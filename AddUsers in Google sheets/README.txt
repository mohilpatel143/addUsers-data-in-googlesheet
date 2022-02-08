---> Step:1

open URL : https://docs.google.com/spreadsheets/
and create sheets : Name Age Mobile email

---> Step:2

open URL : https://script.google.com/
and Write this Code :

//-----------------------code start---------------------
// Step-1

var wbook = SpreadsheetApp.openByUrl('https://docs.google.com/spreadsheets/d/107EqJx9z0I-6lrwBd4uiPTVEOvnDZNUnHrQaNIBrV2Q/edit#gid=0'); # your googlesheet url       

var sheet = wbook.getSheetByName('Sheet1'); # sheetname

// Step-2

function doPost(e)
{
  var action = e.parameter.action;

  if(action == 'addUser')
  {
    return addUser(e);
  }
}

// Step-3

function addUser(e)
{
  var user = JSON.parse(e.postData.contents);

  sheet.appendRow([user.name,user.age,user.mobile,user.email]);

  // Step-4
  return ContentService.createTextOutput("Success").setMimeType(ContentService.MimeType.TEXT);
}
//------------------code end-----------------
after write code has been save run & deploy this code
if successfully deploy tha project its can be create link.

---> Stap:3

open postman select POST request and peast the deployment URL and after url wirte ?action=addUser
select body row and texttype JSON
ex:
{
    "name":"ram",
    "age":"26",
    "mobile":"23235965262",
    "email":"ram123@gmail.com"
}

and send this POST request

if your programme can right immplement it can been saw the success message and data can been send in google sheet.




