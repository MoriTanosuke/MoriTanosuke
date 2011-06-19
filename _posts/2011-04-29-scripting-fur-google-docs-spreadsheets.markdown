--- 
wordpress_id: 626
layout: post
title: "Scripting f\xC3\xBCr Google Docs Spreadsheets"
wordpress_url: http://blog.kopis.de/?p=626
---
Heute hab ich mein erstes Script für <a href="http://docs.google.com">Google Docs Spreadsheets</a> geschrieben, um amerikanische Zahlen in europäisches Format zu konvertieren. Naja, es ist etwas simpler: Ich ersetze einfach den Punkt als Dezimaltrennzeichen durch ein Komma:

[javascript]
function convertUsToEu() {
  var range = SpreadsheetApp.getActiveRange();
  var maxRows = range.getNumRows() + 1;
  var maxColumns = range.getNumColumns() + 1;
  
  for(var column = 1; column &lt; maxColumns; column++) {
    for(var row = 1; row &lt; maxRows; row++) {
      var cell = range.getCell(row, column);
      var value = cell.getValue();
      value = value.replace('.', ',');
      cell.setValue(value);
    }
  }
}
[/javascript]

Die Verwendung von Javascript ist sehr angenehm, ausserdem ist der Skripteditor von Google sehr praktisch. Es gibt sogar <em>Auto Complete</em>! :-)
