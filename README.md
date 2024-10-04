| Endpoint  | Method | Description                 | Request Body                                    | Request Header | Response                                      | Accessed By |
|-----------|--------|-----------------------------|-------------------------------------------------|-----------------|-----------------------------------------------|-------------|
| /register | POST   | Create a new user           | ``` {"user": "naruto727@gmail.com", "pwd": "CCT@9870"}``` | None            | ``` {"success": "New user Naruto727@gmail.com created!"}``` | PUBLIC      |
 /auth    | POST   | Authenticate an user   | ``` {"user": "naruto727@gmail.com", "pwd": "CCT@9870"}``` | None            | ``` {"roles": [1987, 1768, 1789, 1545], "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VySW5mbyI6eyJ1c2VybmFtZSI6Im5hcnV0bzcyN0BnbWFpbC5jb20iLCJyb2xlcyI6WzE5ODcsMTc2OCwxNzg5LDE1NDVdfSwiaWF0IjoxNzAzNDk2NjE3LCJleHAiOjE3MDM0OTY5Nzd9._US-rGo65d0bThFnOvDlmflN62S8Xu-kc_ZWg56zYAE"}``` | PUBLIC      |
/refresh | GET    | Generate a new access token and refresh token    | None         | None    | ``` {"roles": [1987, 1768, 1789, 1545], "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VySW5mbyI6eyJ1c2VybmFtZSI6Im5hcnV0bzcyN0BnbWFpbC5jb20iLCJyb2xlcyI6WzE5ODcsMTc2OCwxNzg9LDE1NDVdfSwiaWF0IjoxNzAzNTAyNDk3LCJleHAiOjE3MDM1MDI4NTd9.twc9hSQAIGVcShrtl3B303oJYN8nwACLUMxFHAUYKJg"}``` | ANY USER TYPE  |
/logout | GET    | Logout the user and delete the refresh token from DB    | None         | None    | ``` {"roles": [1987, 1768, 1789, 1545], "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VySW5mbyI6eyJ1c2VybmFtZSI6Im5hcnV0bzcyN0BnbWFpbC5jb20iLCJyb2xlcyI6WzE5ODcsMTc2OCwxNzg9LDE1NDVdfSwiaWF0IjoxNzAzNTAyNDk3LCJleHAiOjE3MDM1MDI4NTd9.twc9hSQAIGVcShrtl3B303oJYN8nwACLUMxFHAUYKJg"}``` | ANY USER TYPE  |
/users   | GET    | Get users list      | None         | Bearer Token    | ``` [ {"roles": {"USER": 1987},"_id": "65892e9a2adc6fe89ba6e85a","username": "savi727@gmail.com","password": "$2b$10$3I3Qg3h9hj3cvQO0k6Qlae49dAaJNq4ZhLtUvbi3v0Lp3WW4B1doa","refreshToken": [], "__v": 0 }, {"roles": {"USER": 1987,"ADMIN": 1789,"SUB_ADMIN": 1768,"SUPER_ADMIN": 1545},"_id": "65893155402805237f1b2e2b","username": "Naruto727@gmail.com","password": "$2b$10$WBabsVtefd6TDj3i8diSNe3n6ZGGeezMDczxJQUcGqiewwVKSsLZq","refreshToken": ["eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Ik5hcnV0bzcyN0BnbWFpbC5jb20iLCJpYXQiOjE3MDM0OTE0ODUsImV4cCI6MTcwMzQ5MTk4NX0.eilOfmF8XXByF6aVcCS_Dw4TooMJ8seaouS_1FaUZHs","eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Ik5hcnV0bzcyN0BnbWFpbC5jb20iLCJpYXQiOjE3MDM0OTQ0MzUsImV4cCI6MTcwMzQ5NDkzNX0.yIpYx2LWMiRRU55_0qXNSDUUK6xnJerrzJ-OiHH6nEw"], "__v": 5 } ]``` | SUPER_ADMIN  |
 /users   | POST   | Create a new user                | ``` {"user": "dustin727@gmail.com", "pwd": "CCT@9870", "roles": {"ADMIN": 1789, "SUB_ADMIN": 1768, "USER": 1987}}``` | Bearer Token    | ``` {"success": "New user dustin727@gmail.com created!"}``` |  SUPER_ADMIN |
 /users   | DELETE | Delete a user | ``` {"id": "6589488e537552f1a1812e44"}```| Bearer Token                | ``` {"acknowledged": true, "deletedCount": 1}``` | SUPER_ADMIN |
 /employees   | GET    | Get employee info | None         | Bearer Token    | ``` {"_id": {"$oid": "65894bbccd92e295bc993e1c"}, "firstname": "savi", "lastname": "singh", "__v": 0}``` | ANY USER TYPE  |
/employees   | POST   | Create an employee    |  ``` {"firstname": "savi", "lastname": "singh"}```| Bearer Token  |  ``` {"firstname": "savi", "lastname": "singh", "_id": "6589672fcd92e295bc993e2c", "__v": 0}``` | SUPER_ADMIN, ADMIN, SUB_ADMIN |
| /employees   | PUT    | Update an employee     |  ```{"id": "6589488e537552f1a1812e44", "firstname": "Savinder", "lastname": "Singh"}``` | Bearer Token | ``` {"_id": "6589488e537552f1a1812e44", "firstname": "Savinder", "lastname": "Singh", "__v": 0}``` | ADMIN, SUPER_ADMIN |
| /employees   | DELETE | Delete an employee     |  ``` {"id": "6589488e537552f1a1812e44"}``` | Bearer Token |  ``` {"acknowledged": true, "deletedCount": 1}``` | SUPER_ADMIN |

