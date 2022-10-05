# HT2 - Dropbox API Testing With Postman/Newman
## Purpose
This project implements automated tests for the following Dropbox API scenarios:
- Upload File
- Get File Meta Data
- Delete File

### Tools
- Newman v5 by Postman Labs: https://github.com/postmanlabs/newman
- Newman htmlextra reporter: https://github.com/DannyDainton/newman-reporter-htmlextra

## Installation
To install, clone the repository and install all the dependencies:  `npm i`

## Setup
You would need:
- Test Dropbox account
- Authentication token for your test dropbox acount
- Specify token in the project configuration

### Test Dropbox Account
If you don't have a dropbox account to use for testing, create one by the following link: https://www.dropbox.com/register

### Generate Authentication Token 
To obtain an Oauth2.0 token we need to request Dropbox to create an _app_. To do that:
- Go to the [Dropbox App Console](https://www.dropbox.com/developers/apps) and log in to your test account
- Select `Create App` and provide parameters:
	- Scoped access = New
	- Choose the type of access you need = Full Dropbox 
  - Name your app = you can use any unique name here (Dropbox requires that app names should be unique globally)
- Now go to `Generated access token` section and click `Generate`. Copy generated token value.

### Configure Project
Open `globals.js` config file and put generated token to `authToken` value:
```
	"values": [
		{
			"key": "authToken",
			"value": "token here",
			"type": "default",
			"enabled": true
		}
	],
```

## Usage - Running The Test Suite
You can initate a test run from the command line by typing
```
npm run test
```
## Reports
By default this project uses 2 reporters: 
- Newman CLI reporter that provides test run results to console
- Newman HTML reporter that generates html report for each run and saves it to the `newman` directory

## Implemented Tests
This project implements automated tests for the following Dropbox API scenarios:
- Upload File
- Get File Meta Data
- Delete File

### 1. Upload File
API documentation: https://www.dropbox.com/developers/documentation/http/documentation#files-upload

These tests cover a simple file upload scenario.
- Positive cases:
	- TestFile.txt is correctly uploaded to Dropbox using the unique filename (to avoid possible conflicts)
- Negative cases:
	- Request is not authentified
  - Wrong request type (GET isntead of POST)
  - Request has no arguments
  - Request has no mandatory path argument

### 2. Get File Meta Data
API documentation: https://www.dropbox.com/developers/documentation/http/documentation#files-get_metadata

These tests cover a scenario to get file information (meta data):
- Positive cases:
	- Meta data for the recently uploaded file (by the previous test) is correctly obtained and matches expected values
- Negative cases:
	- Request is not authentified
  - Wrong request type (GET isntead of POST)
  - Request has no arguments
  - Request has no mandatory path argument
  - Requested file does not exist

### 3. Delete File
API documentation: https://www.dropbox.com/developers/documentation/http/documentation#files-delete

These tests cover a simple file deletion scenario:
- Positive cases:
	- Recently uploaded file is correctly deleted
- Negative cases:
	- File does not exist
