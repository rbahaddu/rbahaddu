
# Password Hashing Application Project

The password hashing application is designed to hash the password. The application uses the SHA512 hashing algorithm 
to create a base64 encoded password hash. 
## Features

- POST request to/hash
- GET request to/hash
- GET Stats


Application API accepts the 3 requests outlined above
## Installation

Install application on MAC/linux

Prerequisite: Install homebrew and wget for mac

$ wget --no-check-certificate --no-proxy 
‘https://s3.amazonaws.com/qa-broken-hashserve/broken-hashserve.tgz’ 

Set PORT environment variable

$ export PORT=8088 

Execute binaries

./broken-hashserve_darwin

## Running Tests

To run tests, run the following command


  ● Post to the /hash endpoint 
$ curl -X POST -H "application/json" -d '{"password":"angrymonkey"}' http://127.0.0.1:8088/hash 


● Get the base64 encoded password 
$ curl -H "application/json" http://127.0.0.1:8088/hash/1

● Get the stats 
$ curl http://127.0.0.1:8088/stats 

● Shutdown 
$ curl -X POST -d 'shutdown' http://127.0.0.1:8088/hash 
## Demo

Insert gif or link to demo


## Documentation

Software Functional Specification Documentation
The following is the requirement specification that was used in building the password hashing application. It describes what the application should do. 
● When launched, the application should wait for http connections. 
● It should answer on the PORT specified in the PORT environment variable. ● It should support three endpoints: 
○ A POST to /hash should accept a password. It should return a job identifier immediately. It should then wait 5 seconds and compute the password hash. The hashing algorithm should be SHA512. 
○ A GET to /hash should accept a job identifier. It should return the base64 encoded password hash for the corresponding POST request. 
○ A GET to /stats should accept no data. It should return a JSON data structure for the total hash requests since the server started and the average time of a hash request in milliseconds. 
● The software should be able to process multiple connections simultaneously. ● The software should support a graceful shutdown request. Meaning, it should allow any in-flight password hashing to complete, reject any new requests, respond with a 200 and shutdown. 
● No additional password requests should be allowed when shutdown is pending.


