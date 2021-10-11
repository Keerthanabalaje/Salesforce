# APEX PROGRAMMING
[APEX course](https://realmassive.udemy.com/course/introduction-to-apex-programming-language/learn/lecture/3864816#overview"Udemy course")
[Deepika code](https://github.com/deepikakhanna/SalesforceInterviewMyTutorialRack"CODE PRACTISE")
***
## **1 General**
```
String name ='keerthana';
System.debug('Firstname is '+ name);
```
> Firstname is keerthana
```
String name ='keerthana';
name ='Sowmiya';
System.debug('Firstname is '+ name);
```
> Firstname is Sowmiya

```
Integer n1= 100*111 ;
Integer n2= (55/32)*2;
Integer n3= 333;
system.debug('total is '+(n1+n2+n3));
```
> total is 11435
***

## **2 Date time data type**
```
Datetime myMeeting = Datetime.newInstance(2021,06,15,13,59,5);
system.debug('my meeting is on '+ myMeeting);
```
> my meeting is on 2021-06-15 20:59:05  GMT FORMATE
```
Datetime myMeeting = Datetime.newInstance(2021,06,15,13,59,5);
system.debug('my meeting is on '+ myMeeting);
Date mydate = myMeeting.Date();
system.debug('my meetig date is on'+ mydate);
```
> my meetig date is on 2021-06-15 00:00:00**
***
## **3Format function**
```
Datetime myMeeting = Datetime.newInstance(2021,06,15,13,59,5);
string formatdate = myMeeting.format();
system.debug('my formatted one is'+ formatdate);
```
> my formatted one is 6/15/2021, 1:59PM
***
## **While loop**
```
integer i=1;
while(i<=100)
{
    system.debug(i);
    i+=10;
}

```
>1,11,21,31,41,51,61,71,81,91,
***
## **SOQL QUERIES**
```
Account acc = [Select Name from account];
```
```
SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c WHERE Categories__c IN ('Cores')
```
***
## **API CODE**
```
@HttpPost
    global static Id createAccount(String Na, String Ph)
    {
        Account create= new Account (Name=Na,Phone=Ph);
        insert create;
        return create.Id;
    }  
```
***
## **Array to string and with single code**
```
try {
            String categoriesList = '\'' + String.join(categories, '\',\'') + '\'';
            String functionalAreaList = '\'' + String.join(functionalArea, '\',\'') + '\'';
            if(categories.size() > 0 && functionalArea.size() >0){
                String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c WHERE Categories__c IN '+'('+ categoriesList +')'+' AND '+'Functional_Area__c IN '+'('+ functionalAreaList +')';
                List<sObject> query = Database.query(queryString);
                return query;
                }
                else if(categories.size() > 0){
                String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c WHERE Categories__c IN '+'('+ categoriesList +')';
                List<sObject> query = Database.query(queryString);
                return query;
                }
                else if(functionalArea.size() > 0){
                String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c WHERE Functional_Area__c IN '+'('+ functionalAreaList +')';
                List<sObject> query = Database.query(queryString);
                return query;
                }
                else{
                String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c';
                List<sObject> query = Database.query(queryString);
                return query;
                }
```
***
## **The same above using oops concept**
```
try {
            String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c';
            String categoriesList = '\'' + String.join(categories, '\',\'') + '\'';
            String functionalAreaList = '\'' + String.join(functionalArea, '\',\'') + '\'';
            
            if(categories.size() > 0 && functionalArea.size() > 0) {
                queryString += ' WHERE Categories__c IN '+'('+ categoriesList +')'+' AND '+'Functional_Area__c IN '+'('+ functionalAreaList +')';   
            } else if(categories.size() > 0) {
                queryString += ' WHERE Categories__c IN '+'('+ categoriesList +')';
            } else if(functionalArea.size() > 0) {
                queryString += ' WHERE Functional_Area__c IN '+'('+ functionalAreaList +')';
            }
```
***
```
String[] categories= new String[]{'Cores','Blockchain'}; 
String[] functionalArea= new String[]{'Marketing', 'Risk'};
String queryString = 'SELECT Title__c, Badge__c, Created_date__c, Comments__c, Likes__c, Views__c,Categories__c, Functional_Area__c FROM Conversation__c';
String categoriesList = '\'' + String.join(categories, '\',\'') + '\'';
String functionalAreaList = '\'' + String.join(functionalArea, '\',\'') + '\'';        
     if(categories.size() > 0 && functionalArea.size() > 0) {
                queryString += ' WHERE Categories__c IN '+'('+ categoriesList +')'+' AND '+'Functional_Area__c IN '+'('+ functionalAreaList +')';   
     } else if(categories.size() > 0) {
                queryString += ' WHERE Categories__c IN '+'('+ categoriesList +')';
     } else if(functionalArea.size() > 0) {
                queryString += ' WHERE Functional_Area__c IN '+'('+ functionalAreaList +')';
     }
List<sObject> query = Database.query(queryString);
system.debug(query);
```
***