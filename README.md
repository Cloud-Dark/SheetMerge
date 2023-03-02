<p align="center"><img src="https://camo.githubusercontent.com/8b3ff7d037bfd150af02ae206242e91dcda05e19435f693f92eef01147b5ad23/68747470733a2f2f696d672e69636f6e73382e636f6d2f637574652d636c69706172742f3531322f676f6f676c652d7368656574732e706e67" width="300" height="320"></p>
<p align="center">

  <a href="https://github.com/WillDev12">
    <img src="https://img.shields.io/github/followers/WillDev12?color=success&label=Follow%20My%20Github&logo=GitHub&style=for-the-badge">
    
  <a href="https://github.com/WillDev12/SheetMerge">
    <img src="https://img.shields.io/github/forks/WillDev12/SheetMerge?style=for-the-badge">
    
  <a href="https://github.com/WillDev12/SheetMerge">
    <img src="https://img.shields.io/github/watchers/WillDev12/SheetMerge?style=for-the-badge">
  
  <a href="https://github.com/WillDev12/SheetMerge">
    <img src="https://img.shields.io/github/stars/WillDev12/SheetMerge?style=for-the-badge">
   
</p>

# SheetMerge

SheetMerge allows you to program multiple Google Sheets at once minus the hassle of defining hundreds of things.

# How to install

Here is a brief tutorial on how to install. If you are interested in how to use, see [here](https://github.com/WillDev12/SheetMerge#how-to-use)

1. Go to Google Sheets

2. Open new Google Script through Extensions

3. Once in the script, click the plus button above "Libraries"

4. Paste the following ID and press look up:

```
17-iwEaZVMqeY7-7jnTyI9lu4ThNP8fpPzf4AEb93IdRkJKvIcJ6S4SO9
```
5. Select a version and apply

# How to use

SheetMerge provides custom commands that let you define what you want to do to another Google Sheet.  In other words, you can edit two at once.

First, you will need a link.  In my case, I will use %link% as a replacement for an actual one.

Here is an example of how to pair a new sheet:

``` javascript
var link = "%link%";

function yourFunction() {

  var active = SheetMerge.getActiveSheet(link);
  Logger.log(active);
  
}
```

If the logger logs the active sheet used in the link, than the program is fully installed.

There are many more things you can do besides this, and [here](https://github.com/WillDev12/SheetMerge#there-is-much-more-than-just-that-so-here-is-a-full-list-of-pre-built-functions-provided) is a full list of all of them

- - -

Here is a script on how to get the properties of a cell:

``` javascript
var link = "%link%";

function getValues() {

  var text = SheetMerge.getValue("A1", link),
      font = SheetMerge.getFontFamily("A1", link),
      size = SheetMerge.getFontSize("A1", link);

  Logger.log(text + ", " + font + ", " + size);

}
```

If you do not already have a sheet to edit, you can easily make one like this:
``` javascript
function createNew() {

  var sheet = SheetMerge.createNew('name'); //upon running, this returns the url of the new sheet for you to edit.

}
```

You can even use the SheetMerge library to edit the sheet remotely!

``` javascript
function changeText() {

  SheetMerge.setCell("A1", "Test text", link);
  Logger.log(SheetMerge.getValue("A1", link));

}
```

- - -

Editing Sheets are easy when it comes to SheetMerge

``` javascript
var link = "%link%";

function editSheets() {

  var name = SheetMerge.getSheetName(link);
  var id = SheetMerge.getSheetId(link);

  //Gets the name and id of the open sheet remotely

  SheetMerge.renameActiveSheet("newName", link);

  //Renames the sheet of your choice

  SheetMerge.insertSheet("sheetName", link);
  SheetMerge.copySheet("newName", link);
  SheetMerge.duplicateActiveSheet(link);

  //Insert and copy sheets

  SheetMerge.deleteActiveSheet(link);
  SheetMerge.deleteSheet("sheetName", link);

  //Delete unnecessary ones

}
```

- - -

Lots of font work is involved, so be warned!

``` javascript
var link = "%link%";

function getFonts() {

  var color = SheetMerge.getFontColor("A1", link),
      size = SheetMerge.getFontSize("A1", link),
      style = SheetMerge.getFontStyle("A1", link),
      weight = SheetMerge.getFontWeight("A1", link),
      family = SheetMerge.getFontFamily("A1", link);

  //Get font properties

  SheetMerge.setFontColor("A1", "#fff", link);
  SheetMerge.setCellFontSize("A1", "10", link);
  SheetMerge.setFontStyle("A1", "italic", link);
  SheetMerge.setFontWeight("A1", "bold", link);
  SheetMerge.setFontFamily("A1", "times new roman", link);

  //Change font properties

}
```

- - -

# There is much more than just that, so here is a full list of pre-built functions provided:

| Property | Type | Description |
| :---    | :----: | :----: |
| getActiveSheet(link) | Sheets | Gets the current sheet of a Spreadsheet |
| getSpreadsheetName(link) | Sheets | Gets the name of a spreadsheet from a link |
| getSpreadsheetID(link) | Sheets | Gets the ID of a sheet from it's link |
| getSheetName(link) | Sheets | Gets the name of the active sheet |
| getURL(id) | Sheets | Gets the url of a Spreadsheet from the ID |
| copySheet(newname, link) | Sheets | Copies a Spreadsheet |

  * Sheets & stuff
      * getActiveSheet(link)
      * getSpreadsheetName(link)
      * getSpreadsheetID(link)
      * getSheetId(link)
      * getSheetName(link)
      * getURL(id)
      * copySheet(newName, link)
      * deleteActiveSheet(link)
      * deleteSheet(sheetName, link)
      * duplicateActiveSheet(link)
      * renameActiveSheet(newName, link)
      * insertSheet(name, link)
  * People
      * getViewers(link)
      * getOwner(link)
  * Cells & editing
      * getA1(range, link)
      * getCellBorder(range, link)
      * getFontColor(range, link)
      * getFontSize(range, link)
      * getCellRow(range, link)
      * getCellColumn(range, link)
      * getValue(range, link)
  * Surroundings
      * getLastColumn(range, link)
      * getLastRow(range, link)
  * Fonts
      * getFontStyle(range, link)
      * getFontFamily(range, link)
      * getFontWeight(range, link)
  * Setting
      * setCell(cell, text, link)
      * setCellBorder(range, top, left, bottom, right, link) // :O
      * setCellFontSize(cell, size, link)
      * setFontColor(range, color, link)
      * setFontStyle(range, style, link)
      * setFontFamily(range, font, link)
      * setFontWeight(range, weight, link)
      * setRowHeight(row, height, link)
      * setColumnWidth(column, width, link)
  * Formulas
      * setFormula(range, formula, link)
      * getFormula(range, link)
  * Deletion
      * clearRange(range, link)
      * deleteRow(rowNum, link)
      * deleteRows(row, howMany, link)
      * deleteColumn(columnNum, link)
      * deleteColumns(column, howMany, link)
  * Misc
      * setTabColor(color, link)

# Source

  You can view my source[^1] [here](https://github.com/WillDev12/SheetMerge/blob/main/library/lib.gs)
  
# Interested in this kind of content?

Check out my [profile](https://github.com/WillDev12) or share it! (This means a lot to me)
```
https://github.com/WillDev12
```
  
[^1]: Copyright © WillDev12 2023
