FORMAT: 1A
HOST: http://hub.wattbike.com/

# Wattbike

This API provides access to the **Wattbike** service. You can manage accounts and user sessions. Gets workouts and categories.

## Status API [/api/ranking]

### Get the status API  [GET]
+ Request (application/json)

    + Headers
            
            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

+ Response 200 (application/json)
            
            {
                "status": "live"
            }

## Account Registration [/api/ranking/users]

### Update account password [PUT]

You may update password using this action. It takes a JSON
object containing an account email address and a new password. 
- If the new password is less than 6 characters, service returns error with status code 400.
- If the new password is more than 6 characters, service returns JSON object with user id and authantication token.

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

    + Body

            {
                "emailAddress": "{dynamicEmail}",
                "password": "dd"
            }
   
+ Response 400 (application/json)

        {
            "error": "Password too short - minimum 6 characters"
        }

+ Response 200 (application/json)

        {
            "authenticationToken": "044548a18337899b8dac630fe9d5f2bb",
            "userId": "648563f5968a2586"
        }

### Account sign-in [POST]

You may sign-in in the application using this action. 
It takes a JSON object containing an account email address and an account password

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

    + Body

            {
                "emailAddress": "andymccorkell@gmail.com",
                "password": "hQeqLhnM22"
            }

+ Response 200 (application/json)

        {
            "authenticationToken": "f89f3332a012b1beb4e66d5f783a04e8",
            "userId": "92855eb01cdd9fa1"
        }
   
## Token Verification [/api/ranking/auths]

### Send token verification [POST]

You may send token verification using this action. It takes a JSON
object containing a token. If this is a valid token, 
service return user account releated to this token and the same token.

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

    + Body

            {
                 "authenticationToken": "f89f3332a012b1beb4e66d5f783a04e8"
            }
            
+ Response 200 (application/json)

        {
            "account": "andymccorkell@gmail.com",
            "authenticationToken": "f89f3332a012b1beb4e66d5f783a04e8"
        }
        

## Session Put [/api/ranking/sessions]

### Update user session [PUT]
Every user in **Wattbike** has an individual training session. 
You can update user session using this action. It takes a JSON
object containing an account information (email) and training session information, such as data of labs.
That service returns user session id, link to the session and username.

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

    + Body

            {
                "dataVersion": 1.2,
                "serialNumber": 25010062,
                "firmwareVersion": 1.22,
                "deviceUserAgent": "Apple-iPhone/501.347",
                "commId": 1,
                "startDate": "{dateTime}",
                "account": "wattbike:andymccorkell@gmail.com",
                "title": "A custom title string",
                "weight": 96.0,
                "maximumHeartRate": 180.0,
                "maximumMinutePower": 123,
                "latLong": "xxxxxxxx",
                "altitude": "xxxxxxxx",
                 "laps":[
                  {
                   "lap":1,
                   "data":[
                          {{rows}}
                          ]
                  },
                  {
                   "lap": 2,
                   "data": [
                                {{rows}}
                           ]
                  },
                  {
                   "lap": 3,
                   "data": [
                                {{rows}}
                           ]
                  }
                 ]
            }
            
+ Response 200 (application/json)

        {
            "sessionId": "5fda18d98a5c66ab41f34da47daaef33",
            "sessionLink": "http://hub.wattbike.com/andymccorkell/session/5fda18d98a5c66ab41f34da47daaef33",
            "username": "andymccorkell"
        }

## Session Process Status [/api/ranking/status]

### Get the session status [POST]

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json

    + Body

            {
                "sessionId": "b9aab02edb52ebb7639f0189ca1faa30"
            }
            
+ Response 200 (application/json)

        {
            "statusId": "3",
            "statusDescription": "Processing Complete"
        }

## Firmware [/api/ranking/firmware]

### Get the new version of device firmware [GET]

You can get the new version of device software using this action.

+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json
            
+ Response 200 (application/json)

        {
            "firmwareVersion": "1.23.00",
            "firmwareReleaseDate": "2015-08-10",
            "firmwareLink": "http://wattbike.com/assets/software/Wattbike-ModelB-firmware-V12300-20150810.bin"
        }

## Users get [/api/ranking/users/id/{userid}]

### Get the user information [GET]

You can get the user information using this action. 
You must sets the user id in Parameters. 
This example uses a user with id 92855eb01cdd9fa1.

+ Parameters
      + userid (number, optional)  ... ID of our User.
      
         + Default: 92855eb01cdd9fa1
      
+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json
            
+ Response 200 (application/json)

        {
            "id": "92855eb01cdd9fa1",
            "username": "andymccorkell",
            "firstName": "Andy",
            "surname": "McCorkell",
            "displayName": "Andy M",
            "gender": "m",
            "dob": "362185200",
            "country": "GB",
            "profileImage": "http://hub.wattbike.com/files/thumb/1_5Ypgfl4N0CayFTwt.jpg",
            "joined": "2014-04-01 10:43:56",
            "group": "1",
            "mmp": 234,
            "mhr": 112,
            "ftp": 201,
            "weight": 100,
            "wbMonitors": [
                "00000000",
                "00000000",
                "00000000",
                "00000000"
            ],
            "hrMonitors": [
                "00000000",
                "00000000",
                "00000000",
                "00000000"
            ],
            "settings": {
                "distance": "km",
                "workoutType": "ftp"
            }
        }

## Workouts List [/api/ranking/workouts]

### List all Workouts  [GET]
You can get all workouts using this action. 
This service return JSON array of workouts.
      
+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json
            
+ Response 200 (application/json)

        {
            "workouts": [
                {
                    "id": "75255ed6a3da4db4",
                    "authorDisplayName": "Andy M",
                    "authorId": "92855eb01cdd9fa1",
                    "title": "Workout Demo",
                    "intro": "A short, simple workout to show the training features of the Wattbike app",
                    "notes": "<p>Nullam id dolor id nibh ultricies vehicula ut id elit. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Lorem <em>ipsum dolor sit amet</em>, consectetur adipiscing elit. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Donec id elit non mi porta gravida at eget metus.\r</p>\n<p>\rDuis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vestibulum id ligula porta felis euismod semper. <a href=\"#\">Aenean lacinia bibendum</a> nulla sed consectetur. Maecenas sed diam eget risus varius blandit sit amet non magna. Cras mattis consectetur purus sit amet fermentum. Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n</p>",
                    "timeTotal": 300,
                    "metric": "mmp",
                    "image": "http://hub.wattbike.com/link/to/media.jpg",
                    "video": "http://youtube/link",
                    "furtherReading": "http://hub.wattbike.com/link/to/page",
                    "mainCategory": "13955eceaf66522b",
                    "categories": [
                        "13955eceaf66522b",
                        "97355ed6901db209"
                    ],
                    "test": false
                },
                {
                    "id": "88655ed6a4dd8f82",
                    "authorDisplayName": "Andy M",
                    "authorId": "92855eb01cdd9fa1",
                    "title": "Second Workout Demo",
                    "intro": "Another short, simple workout to show the training features of the Wattbike app",
                    "notes": "<p>Nullam id dolor id nibh ultricies vehicula ut id elit. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Lorem <em>ipsum dolor sit amet</em>, consectetur adipiscing elit. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Donec id elit non mi porta gravida at eget metus.\r</p>\n<p>\rDuis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vestibulum id ligula porta felis euismod semper. <a href=\"#\">Aenean lacinia bibendum</a> nulla sed consectetur. Maecenas sed diam eget risus varius blandit sit amet non magna. Cras mattis consectetur purus sit amet fermentum. Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n</p>",
                    "timeTotal": 300,
                    "metric": "mmp",
                    "image": "http://hub.wattbike.com/link/to/media.jpg",
                    "video": "http://youtube/link",
                    "furtherReading": "http://hub.wattbike.com/link/to/page",
                    "mainCategory": "13955eceaf66522b",
                    "categories": [
                        "13955eceaf66522b",
                        "97355ed6901db209",
                        "97355ed6901db209"
                    ],
                    "test": false
                },
                {
                    "id": "655ed688a8f824dd",
                    "authorDisplayName": "Andy M",
                    "authorId": "92855eb01cdd9fa1",
                    "title": "3 Minute Test",
                    "intro": "A test, Test",
                    "notes": "<p>Nullam id dolor id nibh ultricies vehicula ut id elit. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Lorem <em>ipsum dolor sit amet</em>, consectetur adipiscing elit. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Donec id elit non mi porta gravida at eget metus.\r</p>\n<p>\rDuis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vestibulum id ligula porta felis euismod semper. <a href=\"#\">Aenean lacinia bibendum</a> nulla sed consectetur. Maecenas sed diam eget risus varius blandit sit amet non magna. Cras mattis consectetur purus sit amet fermentum. Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n</p>",
                    "timeTotal": 180,
                    "metric": "mmp",
                    "image": "http://hub.wattbike.com/link/to/media.jpg",
                    "video": "http://youtube/link",
                    "furtherReading": "http://hub.wattbike.com/link/to/page",
                    "mainCategory": "13955eceaf66522b",
                    "categories": [
                        "13955eceaf66522b",
                        "97355ed6901db209",
                        "97355ed6901db209",
                        "85355ed6901db8w"
                    ],
                    "test": {
                        "outcomes": "mmp, mhr, vo2max, powerKg, mets"
                }
            }
        ]
        }

## Workouts Get [/api/ranking/workouts/id/{workoutid}]

### Get the workout information [GET]

You can get the workout information using this action.
A workout is comprised of a JSON array of session ‘segments’
with some header information. 
You must set the workout id in Parameters. 
This example uses a workout with id 75255ed6a3da4db4.

+ Parameters
      + workoutid (number, optional)  ... ID of our Workout.
      
         + Default: 75255ed6a3da4db4
      
+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json
            
+ Response 200 (application/json)

        {
            "id": "75255ed6a3da4db4",
            "authorDisplayName": "Andy M",
            "authorId": "92855eb01cdd9fa1",
            "title": "Workout Demo",
            "intro": "A short, simple workout to show the training features of the Wattbike app",
            "notes": "<p>Nullam id dolor id nibh ultricies vehicula ut id elit. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Lorem <em>ipsum dolor sit amet</em>, consectetur adipiscing elit. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Donec id elit non mi porta gravida at eget metus.\r</p>\n<p>\rDuis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vestibulum id ligula porta felis euismod semper. <a href=\"#\">Aenean lacinia bibendum</a> nulla sed consectetur. Maecenas sed diam eget risus varius blandit sit amet non magna. Cras mattis consectetur purus sit amet fermentum. Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n</p>",
            "timeTotal": 300,
            "metric": "mmp",
            "image": "http://hub.wattbike.com/link/to/media.jpg",
            "video": "http://youtube/link",
            "furtherReading": "http://hub.wattbike.com/link/to/page",
            "mainCategory": "13955eceaf66522b",
            "categories": [
                "13955eceaf66522b",
                "97355ed6901db209"
            ],
            "test": false,
            "segments": [
            {
                "duration": 60,
                "start": 30,
                "end": 30,
                "hr": 0,
                "cadence": 90,
                "lap": 0,
                "flashNote": "",
                "flashNoteOffset": 0
            },
            {
                "duration": 60,
                "start": 40,
                "end": 40,
                "hr": 0,
                "cadence": 90,
                "lap": 0,
                "flashNote": "",
                "flashNoteOffset": 0
            },
            {
                "duration": 50,
                "start": 50,
                "end": 50,
                "hr": 0,
                "cadence": 90,
                "lap": 0,
                "flashNote": "Sprint in 10 seconds",
                "flashNoteOffset": 35
            },
            {
                "duration": 10,
                "start": 80,
                "end": 80,
                "hr": 0,
                "cadence": 90,
                "lap": 1,
                "flashNote": "",
                "flashNoteOffset": 0
            },
            {
                "duration": 120,
                "start": 20,
                "end": 20,
                "hr": 0,
                "cadence": 90,
                "lap": 1,
                "flashNote": "Only two minutes to go",
                "flashNoteOffset": 0
            }
        ]
        }
        
## Categories Get [/api/ranking/categories]

### List all Categories  [GET]
You can get all Categories using this action. 
This service return JSON array of categories.
      
+ Request (application/json)

    + Headers

            X-API-KEY : AY7JsQof82R3NTaZu0KSzJJLiR364cSk
            Accept : application/json
            
+ Response 200 (application/json)
        
        {
            "categories": [
                {
                    "id": "13955eceaf66522b",
                    "title": "Power",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "18755eceaf66230a",
                    "type": "workout"
                },
                {
                    "id": "30855eceb03e3459",
                    "title": "Endurance",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "18755eceaf66230a",
                    "type": "workout"
                },
                {
                    "id": "73355eceb0e5b25f",
                    "title": "Leg Speed",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "18755eceaf66230a",
                    "type": "workout"
                },
                {
                    "id": "88555eceb18d817e",
                    "title": "Strength",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "18755eceaf66230a",
                    "type": "workout"
                },
                {
                    "id": "26155eceb21b14ab",
                    "title": "Weightloss",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "22069eceaf66240g",
                    "type": "workout"
                },
                {
                    "id": "97355ed6901db209",
                    "title": "Examples",
                    "description": "Example workouts to illustrate Workout features.",
                    "parent": null,
                    "type": "workout"
                },
                {
                    "id": "85355ed6901db8w",
                    "title": "Tests",
                    "description": "Test description",
                    "parent": null,
                    "type": "workout"
                },
                {
                    "id": "18755eceaf66230a",
                    "title": "Cycling",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": null,
                    "type": "workout"
                },
                {
                    "id": "22069eceaf66240g",
                    "title": "Misc",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": null,
                    "type": "workout"
                },
                {
                    "id": "30845sqiot44209p",
                    "title": "Plan Category 1",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": null,
                    "type": "plan"
                },
                {
                    "id": "30855eceb03e345p",
                    "title": "Plan Category 2",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": null,
                    "type": "plan"
                },
                {
                    "id": "73355eceb0e5b25p",
                    "title": "Plan Category 3",
                    "description": "Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": null,
                    "type": "plan"
                },
                {
                    "id": "72455eceb0e5b25d",
                    "title": "Plan Category 1b",
                    "description": "Has Parent. Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "30845sqiot44209p",
                    "type": "plan"
                },
                {
                    "id": "73795eceb0e5b25q",
                    "title": "Plan Category 1c",
                    "description": "Has Parent. Nulla vitae elit libero, a pharetra augue. Nullam id dolor id nibh ultricies vehicula ut id elit.",
                    "parent": "30845sqiot44209p",
                    "type": "plan"
                }
            ]
        }