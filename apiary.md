FORMAT: 1A
HOST: http://hub.wattbike.com

# Wattbike

This is a simple API. 2

## API status [/api/ranking/]

### Get api status [GET]

+ Response 200 (application/json)
    

        [
            {
                "status": "live"
            }
        ]

##  Update user password [/api/ranking/users]
### Update user password with small pass [PUT]

When you try to user password with string, who is than 6 characters. 
You can revice an error.

+ Request (application/json)

        {
            "emailAddress" : {dynamicEmail},
            "password" : "dd"
        }

+ Response 201 (application/json)

    + Headers

            Location: /questions/2

    + Body

            {
                "error": "Password too short - minimum 6 characters"
            }
