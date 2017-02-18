# Background
We are creating an SDK for messaging applications that adds a new way to suggest creative contents to users based on various data like location, a user's chat conversation, as well as other contextual or behavioral data. 

An app integrator must first activate our SDK before being able to use our services. Activation allows them to pass initiaization data that we use to generate session data for use on the device. 

# Assignment
Your task is to implement the session activation method. 

- Create a public method that collects data for the app kit. 
- Automatically collect as much information as possible, without requiring the app integrator to specify it
 - Device ID (AAID or app-specified unique ID)
 - Location (lat/long)
 - Device metadata
 - Device type
 - Connection speed
 - Battery level percent charge
 - Device OS and version
 - Screen dimensions
 - Pixel ratio and pixels per inch
- Allow the app integrator to specify:
 - Device ID
 - Location
 - Allowed content formats (a list of any of these these available formats:
    - gif
    - emoji
    - sticker
 - User age
 - User gender
- Allow the app integrator to over-write: 
 - Device ID
 - Location
- POST this information to https://sand-cxp.emogi.com/v1/sessions (it may fail; that's OK)
- Implement a response handler for the following scenarios. (Your handler doesn't actually need to do anything):
 - 200/OK
 - 400/ERROR/INVALID ARGUMENTS
 - 401/ERROR/AUTH FAILED
 - 500/UNEXPECTED SERVER ERROR
 - 503/SERVICE UNAVAILABLE

## Request format
```
{
  "app_id": "1FUUBK",
  "dev_id": "AA7E87A1-8A50-426B-8361-6F74977E8FD0",
  "dev_id_type": "IDFA",
  "ad_fmts": [
    "gif",
    "emo",
    "a-emo",
    "sti",
    "a-sti"
  ],
  "geo": {
    "lat": 40.7506,
    "lng": 73.9935
  },
  "user": {
    "age": "17",
    "gender": "m"
  },
  "dev": {
    "dev_type": "phone",
    "batt": 83,
    "conn": "wifi",
    "os": "",
    "os_ver": "",
    "scr_w": 0,
    "scr_h": 0,
    "pxr": 0,
    "ppi": 0
  }
}
```
## Response format
200/OK response
```
{
  "request_id": "D2DDCE8FDE824E89B2C56E99C04B2DF2",
  "status": "OK", 
  "data": ""
}
```

4xx or 5xx/Error response
```
{
  "error": "Invalid arguments"
} 
```
# Additionally
- We want to be respectful of your time, so please spend no more than 2 hours on this. 
- Provide a list of further work or ehancements

That's it. Have fun :shipit:
