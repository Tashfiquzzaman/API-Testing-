# API-Testing
## 🚀 Students_details API Testing Collection
# Content    
- [Introduction](https://github.com/Tashfiquzzaman/API-Testing#Introduction)    
- [Requirements](https://github.com/Tashfiquzzaman/API-Testing#requirements)      
- [Assertions Details](https://github.com/Tashfiquzzaman/API-Testing#assertions-details)   
  - [Create A Student](https://github.com/Tashfiquzzaman/API-Testing#Create-A-Student)   
  - [TokenGenerate](https://github.com/Tashfiquzzaman/API-Testing#TokenGenerate)   
  - [Authorized](https://github.com/Tashfiquzzaman/API-Testing#Authorized)   
  - [Student info Validation](https://github.com/Tashfiquzzaman/API-Testing#Student-info-Validation)   
  - [Technical_Skills Add ](https://github.com/Tashfiquzzaman/API-Testing#Technical-Skills-Add )    
  - [Student Final Information](https://github.comTashfiquzzaman/API-Testing#Student-Final-Information)      
  - [Summary](https://github.com/Tashfiquzzaman/API-Testing#summery)    

# Introduction
This document explains how to run an API test with Postman against a Swagger UI site.    

# Requirements  
**Java**  
https://www.oracle.com/java/technologies/downloads/   
**Postman**   
https://www.postman.com/   
**Node JS**   
https://nodejs.org/en/    

# Assertions Details    
#### Create A Student        
```bash
// set Student FirstName
var first_name=pm.environment.replaceIn("{{$randomFirstName}}")
pm.environment.set("Student_fname",first_name)
// set Student MidtName
var middle_name=pm.environment.replaceIn("{{$randomNamePrefix}}")
pm.environment.set("Student_Mname",middle_name)
// set Student LAstName
var last_name=pm.environment.replaceIn("{{$randomLastName}}")
pm.environment.set("Student_lname",last_name)

// set Student Student_House_No
var House_Number=pm.environment.replaceIn("{{$randomStreetAddress}}")
pm.environment.set("Student_House_No",House_Number)

set Student Student_City_Name
var City=pm.environment.replaceIn("{{$randomCity}}")
pm.environment.set("Student_City_Name",City)

set Student Student_Country_Name
var Country=pm.environment.replaceIn("{{$randomCountry}}")
pm.environment.set("Student_Country_Name",Country)

var Mobile=pm.environment.replaceIn("{{$randomPhoneNumber}}")
pm.environment.set("Student_Mobile_Number",Mobile)


var CurrentAddress=pm.environment.replaceIn("{{$randomStreetAddress}}")
pm.environment.set("Student_Current_Address",CurrentAddress)

const moment=require ('moment')
const today=moment()
pm.environment.set("Student_DOB",today.format("YYYY-MM-DD"))
});
```  
#### TokenGenerate 
```bash   
// set environment token
var jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);
```    
#### Authorized  
```bash
// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

```   
#### Student info Validation     
```bash

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```   
#### Technical_Skills Add    
```bash
// set Student _Technical_Skills 
 var language1=pm.environment.replaceIn("{{$randomCity}}")
pm.environment.set("language_1",language1)

var language2=pm.environment.replaceIn("{{$randomStreetName}}")
pm.environment.set("language_2",language2)

var yearexp=pm.environment.replaceIn("{{$randomInt}}")
pm.environment.set("YrarExp",yearexp)

var lastused=pm.environment.replaceIn("{{$randomCreditCardMask}}")
pm.environment.set("Lastused",lastused)

var status=pm.environment.replaceIn("{{$randomBoolean}}")
pm.environment.set("status",status)


```
#### Delete User   

```bash
// Expected status code and response status code same or not

pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});
```
# Summery    
I have Completed an API test of the Student Information Site.   
https://thetestingworldapi.com/swagger/#/     
<p align="center">
  <img src="https://github.com/Tashfiquzzaman/API-Testing-/blob/78bf08dbda7dcb096d6a50edbb8becd8eb7020f9/Report/Capture.JPG" />
</p>
 
Here in this API, the Student_Information list was viewed and different tests were performed like GET, POST, PUT, DELETE.

**Summary:** Test Scripts 5 and a Total 20 assertions were done. All of them passed with 0 skipped tests. The number of iterations was 1.


# Create Test Suites   

### Using Newman   


  Newman is a command-line Collection Runner for Postman. It enables you to run and test a Postman Collection directly from the command line.
#### Install Command    
```bash
npm install -g newman    
```
#### Run Command    
- newman run “Path/CollectionName.json” -e Path/EnvironmentName.json
- newman run “Collection Link” -e “Path”/EnvironmentName.json    

#### Create HTML Report  
 
#### Install Command      
```bash
npm install -g newman-reporter-html
```
**or**   
```bash
npm install -g newman-reporter-htmlextra    
```
#### Run Command      
- newman run “Collection Name” -e “Path”/EnvironmentName.json -r cli,html    
**or**    
- newman run “Collection Name” -e “Path”/EnvironmentName.json -r cli,htmlextra    

