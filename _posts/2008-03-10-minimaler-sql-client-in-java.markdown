--- 
wordpress_id: 180
layout: post
title: Minimaler SQL-Client in Java
wordpress_url: http://blog.kopis.de/?p=180
---

    Ich hab gerade einen kleinen SQL-Client geschrieben, mit dem man einfach SQL-Statements gegen eine Datenbank absetzen kann. Falls jemand auf der Suche ist, bedient euch - einfach auf den Link "<a href="http://kopis.wordpress.com/2008/03/10/minimaler-sql-client-in-java/#more-1324">Den Rest des Beitrags lesen</a>" klicken. :-) Aktuellere Versionen gibt es vielleicht sp&Atilde;&curren;ter unter <a href="http://wikihost.org/wikis/kopis/wiki/prog:simplesqlclient.java">http://wikihost.org/wikis/kopis/wiki/prog:simplesqlclient.java</a>. Dort ist auch der Quelltext besser formatiert, also schaut's einfach mal an.

Wer Verbesserungen hat, der kann sich gern in den Kommentaren zu Wort melden. :-)

&lt;!--more-->
<code> </code>
<div class="CodeRay">
  <div class="code"><pre>package com.basf.migration.region;  import java.sql.Connection;

  import java.sql.DriverManager;

  import java.sql.ResultSet;

  import java.sql.SQLException;

  import java.sql.Statement;

import com.csc.provider.DbmsProviderFactory;

  import com.csc.provider.UnavailableException;

public class SimpleSqlClient {

public SimpleSqlClient(String statement, String driver, String dburl, String username, String password) {

          Connection conn = null;

          try {

              Class.forName(driver);

        conn = DriverManager.getConnection(dburl, username, password);

        execute(conn, statement);

      } catch (SQLException e) {

        // TODO Auto-generated catch block

        e.printStackTrace();

      } catch (ClassNotFoundException e) {

        // TODO Auto-generated catch block

        e.printStackTrace();

      } finally {

        try {

          conn.close();

        } catch (SQLException e) {

          // TODO Auto-generated catch block

          e.printStackTrace();

        } catch(NullPointerException e) {

          // TODO Auto-generated catch block

          e.printStackTrace();

        }

      }

    }

private void execute(Connection conn, String statement) throws SQLException {

      Statement stmt = conn.createStatement();

      boolean executed = stmt.execute(statement);

      ResultSet result = stmt.getResultSet();

      for (int column = 1; column &lt;= result.getMetaData().getColumnCount(); column++) {

        System.out.print(result.getMetaData().getColumnName(column) + &quot;,&quot;);

      }

      System.out.println();

while(result.next()) {

        for (int column = 1; column &lt;= result.getMetaData().getColumnCount(); column++) {

          System.out.print(result.getObject(column) + &quot;,&quot;);

        }

        System.out.println();

      }

    }

public static void main(String[] args) {

      if(args == null || args.length != 5) {

        System.err.println(&quot;Usage:t&quot; + SimpleSqlClient.class + &quot;  SQLSTATEMENT DRIVER_CLASSNAME DB_URL USERNAME PASSWORD&quot;);

        System.exit(-1);

      } else if(args.length == 5) {

        new SimpleSqlClient(args[0], args[1], args[2], args[3], args[4]);

      }

    }

}</pre></div>
</div>
  
