# Google-Scripts-Move-Rows-Automatically
Using google scripts, move rows from one sheet to another


> This file has been modified from https://www.seerinteractive.com/blog/google-sheets-scripts/ 
> By: Christina Blake
> See Section: Moving rows to a separate tab upon completion



To use this modified script


1. Create a new google spreadsheet


2. Create 3 sheets;

  - Sheet (1) Sheet Name: ToDo (make sure there are no spaces between To and Do. It is all one word ToDo)
  - Sheet (2) Sheet Name: Doing
  - Sheet (3) Sheet Name: Done
  


3. Create the column names in the corresponding column numbers;

  - Column (1) Column Name: Category
  - Column (2) Column Name: Item
  - Column (3) Column Name: Due
  - Column (4) Column Name: Completed
  - Column (5) Column Name: Notes
  - Column (6) Column Name: Link
  - Column (7) Column Name: Reporting Date
  - Column (8) Column Name: Move
  
  
  
4. Select "Tools" from the Menu Bar 

5. Select "Script Editor" from the List

6. Delete everything in code.gs

7. Paste the script

8. Name the script "Move Rows" {you can name this whatever you want}

9. Save the script

10. Run the script

If you do not have any information in the sheets, the script will fail.

Enter data in your sheets, then see if the script moves the data.




Script

function onEdit(e) {
  myFunction2();
}


function myFunction2() {
  // moves rows from one sheet to another when a value is entered in a column

  var sheetNameToWatch = "ToDo";

  var columnNumberToWatch = 8;
  var valueToWatch1 = "Doing";
  var sheetName1ToMoveTheRowTo = "Doing";
    
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = SpreadsheetApp.getActiveSheet();
  var range = sheet.getActiveCell();
  
  if (sheet.getName() == sheetNameToWatch && range.getColumn() == columnNumberToWatch && range.getValue() == valueToWatch1) {

    var targetSheet = ss.getSheetByName(sheetName1ToMoveTheRowTo);
    var targetRange = targetSheet.getRange(targetSheet.getLastRow() + 1, 1);
    sheet.getRange(range.getRow(), 1, 1, sheet.getLastColumn()).moveTo(targetRange);
    sheet.deleteRow(range.getRow());
  }  
 
  var sheetNameToWatch = "ToDo";

  var columnNumberToWatch = 8;
  var valueToWatch2 = "Done";
  var sheetName2ToMoveTheRowTo = "Done";
    
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = SpreadsheetApp.getActiveSheet();
  var range = sheet.getActiveCell();
  
  if (sheet.getName() == sheetNameToWatch && range.getColumn() == columnNumberToWatch && range.getValue() == valueToWatch2) {

  var targetSheet = ss.getSheetByName(sheetName2ToMoveTheRowTo);
  var targetRange = targetSheet.getRange(targetSheet.getLastRow() + 1, 1);
  sheet.getRange(range.getRow(), 1, 1, sheet.getLastColumn()).moveTo(targetRange);
  sheet.deleteRow(range.getRow());
}  
 
  var sheetNameToWatch = "Doing";

  var columnNumberToWatch = 8;
  var valueToWatch2 = "Done";
  var sheetName2ToMoveTheRowTo = "Done";
    
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = SpreadsheetApp.getActiveSheet();
  var range = sheet.getActiveCell();
  
  if (sheet.getName() == sheetNameToWatch && range.getColumn() == columnNumberToWatch && range.getValue() == valueToWatch2) {

    var targetSheet = ss.getSheetByName(sheetName2ToMoveTheRowTo);
    var targetRange = targetSheet.getRange(targetSheet.getLastRow() + 1, 1);
    sheet.getRange(range.getRow(), 1, 1, sheet.getLastColumn()).moveTo(targetRange);
    sheet.deleteRow(range.getRow());
  }}
