Contact List
﻿

Contact
POST Add Contact
﻿https://thinking-tester-contact-list.herokuapp.com/contacts

HEADERS
Authorization	Bearer
Body raw (json)

JSON
{
    "firstName": "John",
    "lastName": "Doe",
    "birthdate": "1970-01-01",
    "email": "jdoe@fake.com",
    "phone": "8005555555",
    "street1": "1 Main St.",
    "street2": "Apartment A",
    "city": "Anytown",
    "stateProvince": "KS",
    "postalCode": "12345",
    "country": "USA"
}
﻿
GET Get Contact List
﻿https://thinking-tester-contact-list.herokuapp.com/contacts

HEADERS
Authorization	Bearer
﻿
GET Get Contact
﻿https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿
HEADERS

Authorization	Bearer
﻿
PUT Update Contact
﻿https://thinking-tester-contact-list.herokuapp.com/contacts/﻿
HEADERS

Authorization	Bearer
Body raw (json)

JSON
{
    "firstName": "John",
    "lastName": "Doe",
    "birthdate": "1970-01-01",
    "email": "jdoe@fake.com",
    "phone": "8005555555",
    "street1": "1 Main St.",
    "street2": "Apartment A",
    "city": "Anytown",
    "stateProvince": "KS",
    "postalCode": "12345",
    "country": "USA"
}
﻿
PATCH Update Contact
﻿https://thinking-tester-contact-list.herokuapp.com/contacts/﻿
The PATCH Update Contact operation is not available through the UI.

HEADERS

Authorization	Bearer
Body raw (json)

JSON
{
    "firstName": "Anna"
}
﻿
DELETE Delete Contact
﻿https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿
HEADERS

Authorization	Bearer
﻿

POST
Add Contact - ZJ
https://thinking-tester-contact-list.herokuapp.com/contacts
﻿

Request Headers
Authorization
Body
raw (json)
View More
json
{
    "firstName": "John",
    "lastName": "Doe",
    "birthdate": "1970-01-01",
    "email": "jdoe@fake.com",
    "phone": "8005555555",
    "street1": "1 Main St.",
    "street2": "Apartment A",
    "city": "Anytown",
    "stateProvince": "KS",
    "postalCode": "12345",
    "country": "USA"
}
GET
Get Contact List - ZJ
https://thinking-tester-contact-list.herokuapp.com/contacts
﻿

Request Headers
Authorization
GET
Get Contact - ZJ
https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿

Request Headers
Authorization
PUT
Update Contact - HY
https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿

Request Headers
Authorization
Body
raw (json)
json
{ "firstName": "sw", "lastName": "<sc>" }
PATCH
Update Contact - HY
https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿

Request Headers
Authorization
Body
raw (json)
json
{
    "birthdate": "1970-01-01"
}
DELETE
Delete Contact - HY
https://thinking-tester-contact-list.herokuapp.com/contacts/
﻿

Request Headers
Authorization
User
StartFragmentUser Collection Documentation – API GuideEndFragment

StartFragment

📘 Overview
This Postman collection includes all endpoints related to user management, including registration, login, and updating user information.

﻿
📍 Base URL
Plain Text
https://thinking-tester-contact-list.herokuapp.com
﻿
🔐 Authentication
Type: Bearer Token (JWT)
How to use: After a successful login, copy the token from the response and include it in the Authorization header like so:
Plain Text
makefileCopyEditAuthorization: Bearer <token>
﻿
📂 Endpoints
﻿
📤 Add User
Method: POST
Endpoint: /users
Description: Create a new user account
Body (JSON):
Plain Text
jsonCopyEdit{
  "firstName": "Yousef",
  "lastName": "Sabet",
  "email": "yousef@example.com",
  "password": "YourPassword123"
}
Expected Response: 201 Created with new user info
﻿
🔑 Login User
Method: POST
Endpoint: /users/login
Description: Login with email and password to get a token
Body (JSON):
Plain Text
jsonCopyEdit{
  "email": "yousef@example.com",
  "password": "YourPassword123"
}
Expected Response: 200 OK with token
﻿
🔄 Update User Info
Method: PATCH
Endpoint: /users/me
Description: Update logged-in user’s data
Headers:
Authorization: Bearer
Content-Type: application/json
Body (JSON example):
Plain Text
jsonCopyEdit{
  "firstName": "UpdatedName",
  "lastName": "UpdatedLast",
  "email": "updated@example.com"
}
Expected Response: 200 OK with updated user object
❗ Note:

All fields are optional but must follow validation rules.
Email input is normalized to lowercase automatically.
﻿
🚫 Common Errors
Code	Description
400
Missing required fields / invalid format
401
Unauthorized – invalid or missing token
409
Email already in use
﻿
🧪 Test Notes
Avoid using already registered emails for new users.
Empty request body on PATCH /users/me should return 400 Bad Request.
When updating the email with capital letters, the response will normalize it to lowercase.
Version field (__v) might not increment after update (check bug report).
﻿
✅ Status Codes
Code	Meaning
200
Success
201
Created
400
Bad Request
401
Unauthorized
404
Not Found
409
Conflict (e.g. email in use)
﻿
🧑‍💻 Example Flow
Register a new user via /users
Login with /users/login and get token
Use PATCH /users/me with token to update user info
StartFragment

🚪 Logout User
Method: POST
Endpoint: /users/logout
Description: Logs out the currently authenticated user
Headers:
Authorization: Bearer
Body: No body required
Expected Response: 200 OK
Notes:
This will invalidate the current token.
If token is missing or invalid, returns 401 Unauthorized.
﻿
❌ Delete User Account
Method: DELETE
Endpoint: /users/me
Description: Deletes the logged-in user's account
Headers:
Authorization: Bearer
Body: No body required
Expected Response: 200 OK
Notes:
The user and all their related data will be permanently removed.
Requires a valid token.
﻿
🔄 Reminder: Token Usage
For all protected routes like PATCH, POST /logout, and DELETE /me, include this in your headers:

Plain Text
makefileCopyEditAuthorization: Bearer <your_token>
﻿
StartFragment

Get User Profile
Method: GET
Endpoint: /users/me
Description: Retrieves the profile information of the currently authenticated user
Headers:
Authorization: Bearer
Body: No body required
Expected Response: 200 OK
jsonCopyEdit{ "_id": "608b2db1add2691791c04c89", "firstName": "Test", "lastName": "User", "email": "test@fake.com", "__v": 1}
Notes:
Requires a valid Bearer token.
Returns current user’s full profile info.  
Now your full Postman user guide includes:

Add User
Login
Update user
Logout
Delete user
Get User Profile
﻿

POST
Add User
https://thinking-tester-contact-list.herokuapp.com/users
﻿

Body
raw (json)
json
{
    "firstName": "love4040",
    "lastName": "love",
    "email": "fathi21@axsos.academy",
    "password": "@yoyo60@yoyo8080"
}
GET
Get User Profile
https://thinking-tester-contact-list.herokuapp.com/users/me
﻿

Request Headers
Authorization
PATCH
Update User
https://thinking-tester-contact-list.herokuapp.com/users/me
﻿

Request Headers
Authorization
Body
raw (json)
json
{ 
"firstName": "Tititup4040",
    "lastName": "Tititup",
    "email": "FATHI81@axsos.academy"
    }
POST
Login User HF
https://thinking-tester-contact-list.herokuapp.com/users/login
﻿

Request Headers
Authorization
Body
raw (json)
json
{
    "email":"malak7000@fake.com",
    "password":"@yoyo60@yoyo8080"
}
POST
Logout User HF
https://thinking-tester-contact-list.herokuapp.com/users/logout
﻿

Request Headers
Content-Type
application/json
Authorization
DELETE
Delete User HF
https://thinking-tester-contact-list.herokuapp.com/users/me
﻿

Request Headers
Authorization
Content-Type
application/json
