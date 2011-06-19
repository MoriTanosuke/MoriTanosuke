--- 
wordpress_id: 670
layout: post
title: PHP und die Fitbit API
wordpress_url: http://blog.kopis.de/?p=670
---
In den letzten Tagen habe ich meine Homepage unter <a href="http://www.kopis.de">www.kopis.de</a> etwas verändert. Ja gut, ich habe überhaupt erstmal was draufgeschrieben. Im Moment wird dort also eine Art Social Hub angezeigt, in dem ich mehrere Quellen zusammenführe:
<a href="http://blog.kopis.de/wp-content/uploads/2011/05/kopis-socialhub1.png"><img class="aligncenter size-medium wp-image-671" title="kopis-socialhub1" src="http://blog.kopis.de/wp-content/uploads/2011/05/kopis-socialhub1-300x238.png" alt="" width="300" height="238" /></a>

Einige Daten kommen dabei aus der <a href="http://dev.fitbit.com">Fitbit API</a>, die ich diesmal mit <a href="http://de.php.net">PHP</a> angesprochen habe. Das liegt hauptsächlich an den Einschränkungen, die mein Webspace mitbringt. Wie auch immer, die Abfragen habe ich also per PHP und <a href="http://code.google.com/p/oauth-php/">oauth-php</a> erledigt.

Ein paar Probleme hatte ich dabei schon, was hauptsächlich an der schlechten Dokumentation von <em>oauth-php</em> liegt. Für alle, die also einen <a href="http://oauth.org">OAuth</a>-Zugriff auf eine API erledigen wollen, folgt hier ein kleines Beispiel in PHP. ;-)

Bevor man überhaupt irgendwas sinnvolles mit <em>oauth-php</em> erledigen kann, muss man eine Datenbank für die Benutzerinformationen anlegen. Man kann die Daten auch in der Session ablegen, aber wer will das schon. Also legt man eine Datenbank an und führt anschliessend das SQL-Skript <em>library/store/mysql/mysql.sql</em> aus. Damit werden Tabellen angelegt, in die <em>oauth-php</em> Server-Einstellungen und später Tokens für die Benutzer ablegt.

Dann erfolgt die Authentifizierung des Benutzers. Das ist bei OAuth ein zweistufiger Prozess: erst wird mit einem (vorher zu registrierenden) Benutzer und Password ein Request Token erzeugt, danach ein Access Token abgefragt und mit diesem Access Token werden alle weiteren Anfragen <em>unterschrieben</em>.

Die Erzeugung des Request Tokens seht ihr hier:

[php]
&lt;?php
include_once &quot;library/OAuthStore.php&quot;;
include_once &quot;library/OAuthRequester.php&quot;;

define(&quot;FITBIT_CONSUMER_KEY&quot;, &quot;yourkey&quot;);
define(&quot;FITBIT_CONSUMER_SECRET&quot;, &quot;yoursecret&quot;);

define(&quot;FITBIT_OAUTH_HOST&quot;, &quot;http://api.fitbit.com&quot;);
define(&quot;FITBIT_REQUEST_TOKEN_URL&quot;, FITBIT_OAUTH_HOST . &quot;/oauth/request_token&quot;);
define(&quot;FITBIT_AUTHORIZE_URL&quot;, FITBIT_OAUTH_HOST . &quot;/oauth/authorize&quot;);
define(&quot;FITBIT_ACCESS_TOKEN_URL&quot;, FITBIT_OAUTH_HOST . &quot;/oauth/access_token&quot;);
define(&quot;FITBIT_ACTIVITIES_URL&quot;, FITBIT_OAUTH_HOST . &quot;/1/user/-/activities/date/2011-05-13.json&quot;); // not sure about this

define('OAUTH_TMP_DIR', function_exists('sys_get_temp_dir') ? sys_get_temp_dir() : realpath($_ENV[&quot;TMP&quot;]));

//  Init the OAuthStore
$server = array(
	'consumer_key' =&gt; FITBIT_CONSUMER_KEY, 
	'consumer_secret' =&gt; FITBIT_CONSUMER_SECRET,
	'server_uri' =&gt; FITBIT_OAUTH_HOST,
	'request_token_uri' =&gt; FITBIT_REQUEST_TOKEN_URL,
	'authorize_uri' =&gt; FITBIT_AUTHORIZE_URL,
	'access_token_uri' =&gt; FITBIT_ACCESS_TOKEN_URL,
	'signature_methods' =&gt; array('HMAC-SHA1', 'PLAINTEXT'),
);
$user = 1;

// get store
$dboptions = array('server' =&gt; 'localhost', 'username' =&gt; 'username', 'password' =&gt; 'password', 'database' =&gt; 'database');
$store = OAuthStore::instance(&quot;MySQL&quot;, $dboptions);
// write server info to store
$consumer_key = $store-&gt;updateServer($server, $user);
$callback_uri = 'http://www.kopis.de/n/oauth-php/fitbit_cb.php?consumer_key=' . rawurlencode($consumer_key) . '&amp;user=' . intval($user);
$token = OAuthRequester::requestRequestToken($consumer_key, $user, array('oauth_callback' =&gt; $callback_uri));

$uri = $token['authorize_uri'] . '?oauth_token=' . rawurlencode($token['token']) . '&amp;oauth_callback=' . rawurlencode($callback_uri);

header('Location: ' . $uri);
?&gt;
[/php]

Hier wird ein Request Token erzeugt und anschliessend wird man zu einer URL bei Fitbit weitergeleitet, auf der man sich in seinen Fitbit Account einloggen muss und der Anwendung (also von meiner Homepage mit <em>oauth-php</em>) den Zugriff auf den Account erlauben muss.

Der Request gibt gleichzeitig eine Callback URL an Fitbit, die nach erfolgter Authentifizierung wieder bei mir aufgerufen wird. In der PHP-Datei, die hinter der Callback URL liegt, wird anschliessend das Request Token in ein Access Token getauscht:

[php]
&lt;?php
require_once 'library/OAuthRequester.php';

// get store
$dboptions = array('server' =&gt; 'server', 'username' =&gt; 'username', 'password' =&gt; 'password', 'database' =&gt; 'database');
$store = OAuthStore::instance(&quot;MySQL&quot;, $dboptions);

$consumer_key = $_REQUEST['consumer_key'];
$oauth_token = $_REQUEST['oauth_token'];
$oauth_verifier = $_REQUEST['oauth_verifier'];
$user = 1;

OAuthRequester::requestAccessToken($consumer_key, $oauth_token, $user, 'POST', $_REQUEST);

$today = strftime(&quot;%Y-%m-%d&quot;);
$req = new OAuthRequester('http://api.fitbit.com/1/user/-/activities/date/'.$today.'.json', 'GET');
$result = $req-&gt;doRequest($user);
$req = new OAuthRequester('http://api.fitbit.com/1/user/-/foods/log/date/'.$today.'.json', 'GET');
$result2 = $req-&gt;doRequest($user);
$req = new OAuthRequester('http://api.fitbit.com/1/user/-/sleep/timeInBed/date/'.$today.'/today.json', 'GET');
$result3 = $req-&gt;doRequest($user);
$req = new OAuthRequester('http://api.fitbit.com/1/user/-/sleep/awakeningsCount/date/'.$today.'/today.json', 'GET');
$result4 = $req-&gt;doRequest($user);

$activities = json_decode($result['body'], true);
$foods = json_decode($result2['body'], true);
$timeInBed = json_decode($result3['body'], true);
$awakeningsCount = json_decode($result4['body'], true);

// print out few information as json
echo &quot;{'steps':&quot;, $activities['summary']['steps'], &quot;,&quot;,
&quot;'distance':&quot;, $activities['summary']['distances'][0]['distance'], &quot;,&quot;,
&quot;'calories':&quot;, $foods['summary']['calories'], &quot;,&quot;,
&quot;'caloriesOut':&quot;, $activities['summary']['caloriesOut'], &quot;,&quot;,
&quot;'activeScore':&quot;, $activities['summary']['activeScore'], &quot;,&quot;,
&quot;'timeInBed':&quot;, round($timeInBed['sleep-timeInBed'][0]['value'] / 60, 2), &quot;,&quot;,
&quot;'awakeningsCount':&quot;, $awakeningsCount['sleep-awakeningsCount'][0]['value'], &quot;}&quot;;
?&gt;
[/php]

Wer aufmerksam gelesen hat, der wird die Variable <code>$user</code> bemerkt haben, die hart auf <em>1</em> gesetzt ist. Das liegt daran, dass ich wirklich nur einen Benutzer mit der API verwende, nämlich mich selbst. ;-) Für alle ernsthaften Anwendungen wird man diesen Wert auch in der Datenbank ablegen, um verschiedene Request und Access Tokens zu unterstützen.

Nach dem einmal erfolgten Tausch in ein Access Token, hab ich den Aufruf von <code>OAuthRequester::requestAccessToken</code> auskommentiert und die Variablen nicht mehr aus den <code>$_REQUEST</code> gelesen, sondern nur noch aus der Datenbank. Bis das Access Token ungültig wird, kann ich jetzt direkt <em>fitbit_cb.php</em> aufrufen, statt vorher manuell die Authentifizierung zu durchlaufen.

OAuth-Tokens sind oft über einen längeren Zeitraum gültig. Ich weiß gar nicht, ob bei Fitbit das Token überhaupt abläuft. <a href="http://wiki.fitbit.com/display/API/OAuth-Authentication-API">Auch die Doku schweigt sich darüber aus</a>.

Mit diesem kleinen Setup hab ich jetzt Zugriff auf meine Daten bei Fitbit und kann damit allerlei Unsinn anstellen. Wer das Ergebnis bewundern möchte, kann das unter <a href="http://www.kopis.de">www.kopis.de</a> tun.
