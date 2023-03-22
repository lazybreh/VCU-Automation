
function doGet(e) {
  var htmlOutput =  HtmlService.createTemplateFromFile('FilterHeaders');
  htmlOutput.Course = '';
  htmlOutput.ProfessorName = '';
  return htmlOutput.evaluate();
}



function doPost(e) {
  Logger.log(JSON.stringify(e));

  var htmlOutput =  HtmlService.createTemplateFromFile('FilterHeaders');
  htmlOutput.Course =  e.parameter.Course;
  htmlOutput.ProfessorName =  e.parameter.ProfessorName;
  return htmlOutput.evaluate();     

}

function getSheetData()  { 
  var ss= SpreadsheetApp.getActiveSpreadsheet();
  var dataSheet = ss.getSheetByName('Display Website Data Table'); 
  var dataRange = dataSheet.getDataRange();
  var dataValues = dataRange.getValues();  
  return dataValues;
}
function Var_getSheetData(){ 
  var ss= SpreadsheetApp.getActiveSpreadsheet();
  var dataSheet = ss.getSheetByName('Database Website Data Table'); 
  var dataRange = dataSheet.getDataRange();
  var dataValues = dataRange.getValues();  
  return dataValues;
}

function getUrl() {
 var url = ScriptApp.getService().getUrl();
 return url;
}

function updateIsApproved(value,index){
  var ss= SpreadsheetApp.openById("1-ydWd_EcuYGl-sAItkhygiSa1LNsBarbs1Mi4F4IKTQ").getSheetByName('Database Website Data Table');
  Logger.log(index);  
  ss.getRange("G" + (index + 1)).setValue(false);
  ss.getRange("G" + (index + 1)).setValue(value);

}
function updateProfessorAssigned(value,index){
  var ss= SpreadsheetApp.openById("1-ydWd_EcuYGl-sAItkhygiSa1LNsBarbs1Mi4F4IKTQ").getSheetByName('Database Website Data Table');
  Logger.log(index);  
  ss.getRange("F" + (index + 1)).setValue("");
ss.getRange("F" + (index + 1)).setValue(value);
}

function getSheetDataProfessorAssigned()  { 
 var sheet = SpreadsheetApp.openById("1-ydWd_EcuYGl-sAItkhygiSa1LNsBarbs1Mi4F4IKTQ").getSheetByName("Database Website Data Table");
  var x = new Array();
  for (let i = 0; i < sheet.getLastRow(); i++) {
  Logger.log(i);
  x[i]=sheet.getRange("F"+ (i+2)).getValue();
}
return x;
}

function getSheetDataApprovedTrueorFalse()  { 
 var sheet = SpreadsheetApp.openById("1-ydWd_EcuYGl-sAItkhygiSa1LNsBarbs1Mi4F4IKTQ").getSheetByName("Database Website Data Table");
  var y = new Array();
  for (let i = 0; i < sheet.getLastRow(); i++) {
  Logger.log(i);
  y[i]=sheet.getRange("G"+ (i+2)).getValue();
}
return y;
}

function getSheetDataID(){
  var sheet = SpreadsheetApp.openById("1-ydWd_EcuYGl-sAItkhygiSa1LNsBarbs1Mi4F4IKTQ").getSheetByName("Form Responses 1");
  var z = new Array();
  for (let i = 0; i < sheet.getLastRow(); i++) {
  Logger.log(i);
  z[i]=sheet.getRange("F"+ (i+2)).getValue();
}
return z;
}



