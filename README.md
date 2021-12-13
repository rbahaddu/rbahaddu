
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
