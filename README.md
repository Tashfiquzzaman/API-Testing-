# API-Testing
## 🚀 Students_details API Testing Collection
# Content    
- [Introduction](https://github.com/Tashfiquzzaman/API-Testing#introduction)    
- [Requirements](https://github.com/Tashfiquzzaman/API-Testing#requirements)      
- [Assertions Details](https://github.com/Tashfiquzzaman/API-Testing#assertions-details)   
  - [Create User](https://github.com/Tashfiquzzaman/API-Testing#create-user)   
  - [GenerateToken](https://github.com/Tashfiquzzaman/API-Testing#generatetoken)   
  - [Authorized](https://github.com/Tashfiquzzaman/API-Testing#authorized)   
  - [Student List](https://github.com/Tashfiquzzaman/API-Testing#Student-list)   
  - [Update Student Information](https://github.com/Tashfiquzzaman/API-Testing#Update-Student-Information)    
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
#### Create User         
```bash
// set environment UserID
var jsonData = pm.response.json();
pm.environment.set("userID", jsonData.userID);

// environment UserName and actual UserName same or not
pm.test("Test username", function () {
pm.expect(jsonData.username).to.eql(pm.environment.get("userName"));
});

// Expected status code and response status code same or not
pm.test("Status code is 201", function () {
pm.response.to.have.status(201);
});     
```
#### GenerateToken    
```bash   
// set environment token
var jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);


// environment token and actual token same or not
pm.test("Test Token", function () {
    pm.expect(jsonData.token).to.eql(pm.environment.get("token"));
});

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```    
#### Authorized  
```bash
// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

//Actual Authorization true or false
pm.test("Verify the Authorization", function () {
    var jsonData = pm.response.json();
 pm.expect(jsonData).to.be.true;
});
```   
#### Books List     
```bash
const response = pm.response.json();

// set environment isbn

pm.environment.set("isbn1", response.books[0].isbn);
pm.environment.set("isbn2", response.books[1].isbn);
pm.environment.set("isbn3", response.books[2].isbn);
pm.environment.set("forUpdatingOrderLater", response.books[3].isbn);

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});


// environment isbn and actual isbn same or not
pm.test("Test isbn1", function () {
    pm.expect(response.books[0].isbn).to.eql(pm.environment.get("isbn1"))
})
pm.test("Test isbn2", function () {
    pm.expect(response.books[1].isbn).to.eql(pm.environment.get("isbn2"))
})
pm.test("Test isbn3", function () {
    pm.expect(response.books[2].isbn).to.eql(pm.environment.get("isbn3"))
})
pm.test("Test For Updating Order Later", function () {
    pm.expect(response.books[3].isbn).to.eql(pm.environment.get("forUpdatingOrderLater"))
})
```   
#### Ordering Books    
```bash
// Expected status code and response status code same or not
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

// environment isbn and actual isbn same or not

var jsonData = pm.response.json();

pm.test("Test Fist order", function () {
    pm.expect(jsonData.books[0].isbn).to.eql(pm.environment.get("isbn1"))
})
pm.test("Test Second Order", function () {
    pm.expect(jsonData.books[1].isbn).to.eql(pm.environment.get("isbn2"))
})
pm.test("Test Third Order", function () {
    pm.expect(jsonData.books[2].isbn).to.eql(pm.environment.get("isbn3"))
})
```   

#### Order Book Detail     
```bash
// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});


// set environment fist_orderd_book_in_the_list
var jsonData = pm.response.json();
pm.environment.set("fist_orderd_book_in_the_list", jsonData.books[0].isbn);


// environment userID and actual userID same or not
pm.test("Test userID", function () {
    pm.expect(jsonData.userId).to.eql(pm.environment.get("userID"))
})


// environment userName and actual userName same or not

pm.test("Test username", function () {
    pm.expect(jsonData.username).to.eql(pm.environment.get("userName"))
})
```  

#### Book ISBN Detail      
```bash
const jsonData = pm.response.json();

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});


// environment fist_orderd_book_Name and actual fist_orderd_book_Name same or not

pm.test("Test Fist order Book in the list", function () {
    pm.expect(jsonData.isbn).to.eql(pm.environment.get("fist_orderd_book_in_the_list"))
})
```   
#### Edit ISBN   
```bash
const response = pm.response.json();

// Expected status code and response status code same or not
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
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
 
Here in this API new books were orderd list of books were viewed and different tests were performed like GET, POST, PUT,DELETE.

**Summary:** Test Scripts 11 and Total 24 assertions were done. All of them passed with 0 skipped tests. The number of iteration was 1.


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
- newman run “Collection Link” -e “Path”/EnvironmentName.json -r cli,html    
**or**    
- newman run “Collection Link” -e “Path”/EnvironmentName.json -r cli,htmlextra    

