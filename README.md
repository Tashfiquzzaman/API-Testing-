# API-Testing
## 🚀 Students_details API Testing Collection

# Table of Contents
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Assertions Details](#assertions-details)
  - [Create A Student](#create-a-student)
  - [TokenGenerate](#tokengenerate)
  - [Authorized](#authorized)
  - [Student info Validation](#student-info-validation)
  - [Technical_Skills Add](#technical-skills-add)
  - [Student Final Information](#student-final-information)
  - [Summary](#summary)

# Introduction<a name="introduction"></a>
This document explains how to run an API test with Postman against a Swagger UI site.

# Requirements<a name="requirements"></a>
...
- **Java**: [Download](https://www.oracle.com/java/technologies/downloads/)
- **Postman**: [Download](https://www.postman.com/)
- **Node JS**: [Download](https://nodejs.org/en)
# Assertions Details<a name="assertions-details"></a>

## Create A Student<a name="create-a-student"></a>
...
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
## TokenGenerate<a name="tokengenerate"></a>
...
```bash   
// set environment token
var jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);
```    

## Authorized<a name="authorized"></a>
...
#### Authorized  
```bash
// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
## Student info Validation<a name="student-info-validation"></a>
...
```bash

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
## Technical_Skills Add<a name="technical-skills-add"></a>

#### Technical_Skills Add  
...
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
## Student Final Information<a name="student-final-information"></a>
...
```bash
     var jsondata= pm.response.json()
     pm.test("Status code is 200 OK", function () {
     pm.response.to.have.status(200);
     });

     // Language 1  Value Validation
     pm.test("Language check 1",function(){
        pm.expect(jsondata.data.TechnicalDetails[0].language[0]).to.eql(pm.environment.get("language_1"))
     })
     //// Language 2  Value Validation

     pm.test("Language check 2",function(){
        pm.expect(jsondata.data.TechnicalDetails[0].language[1]).to.eql(pm.environment.get("language_2"))
     })

     //Year of Experience
     pm.test("Year of Experience check",function(){
        pm.expect(jsondata.data.TechnicalDetails[0].yearexp).to.eql(pm.environment.get("YrarExp"))
     })

     // House Number Validation
     pm.test("House Number Validation",function(){
        pm.expect(jsondata.Address).to.eql(pm.environment.get("23023 Asa Spurs"))
     })

     
     // city name validation
     pm.test("Student's City Name Validation",function(){
        pm.expect(jsondata.Address).to.eql(pm.environment.get("Rolfsonstad"))
     })
    
    // Studenr Country name Validation
     pm.test("Studenr Country name Validation",function(){
        pm.expect(jsondata.Address).to.eql(pm.environment.get("Sudan"))
     })

     // Studenr Mobile Number Validation
     pm.test("Studenr Mobile Number Validation",function(){
        pm.expect(jsondata.Address).to.eql(pm.environment.get("337-995-8976"))
        })


        // Studenr Current Address Validation
        pm.test( "Studenr Current Address Validation",function(){
        pm.expect(jsondata.Address).to.eql(pm.environment.get("76034 Zemlak Way"))
        })

#### Delete User   
...
```bash
// Expected status code and response status code same or not

pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});
```
## Summary<a name="summary"></a>
<img src="https://github.com/Tashfiquzzaman/API-Testing-/blob/78bf08dbda7dcb096d6a50edbb8becd8eb7020f9/Report/Capture.JPG" />
</p>
Test Scripts 5 and a Total 20 assertions were done. All of them passed with 0 skipped tests. The number of iterations was 1.

# Create Test Suites   

### Using Newman   
  Newman is a command-line Collection Runner for Postman. It enables you to run and test a Postman Collection directly from the command line.
#### Install Command    
```bash
npm install -g newman    
```
#### Create HTML Report        
#### Run Command      
- newman run “Collection Name”.json -e "EnvironmentName".json -r cli,html    
**or**    
- newman run “Collection Name” -e “EnvironmentName".json -r cli,htmlextra    
