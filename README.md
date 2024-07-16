## Acceptance Criteria  


### Description
Implement the profile settings endpoints

### Purpose
Allow users to get and update their profile information

<br></br>
### Get Profile Settings [GET] `api/user/:id`

1.  Authentication

    - Given a request with valid Authentication token that matches the requested data, the system should return said data
    - Given invalid token, the system should return a 401 Unuthorised status.
2.  Retrieval

    - Given a request with a valid id, the details of the user with passed id should be returned
    - Given a request with invalid user id, the system should return a 400 Bad Request status

#### Header
```
{
  "Authorization": "Bearer eyJhbGciOiJIUzI1N...."
}
```

#### Request
```
GET /api/user/2478
```

#### Success Response
```
{
  "message": "user profile retrieved successfully",
  "user": {
    "id": "2478",
    "firstName": "John",
    "lastName": "Doe",
    "email": "john_doe@gg.com",
    "pfp_link": "https://gravitar.com/t2Jci..."
  },
}
```

#### Error Response(invalid token)
```
{
  "message": "could not retrieve user profile",
  "error": "user does not have access to this resource",
  "statusCode": 401,
}
```

#### Error Response(invalid user)
```
{
  "message": "could not retrieve user profile",
  "error": "user does not exist",
  "statusCode": 400,
}
```

<br></br>
### Update Profile Settings [PUT] `/api/user/:id`
1.  Authentication

  - Given a request with valid Authentication token that matches the requested data, the system should update the user profile return the new settings
  - Given invalid token, the system should return a 401 Unuthorised status.
2.  Updating

  - Given a request with a valid id, the details of the user with passed id should be updated and their new profile should be returned by the system
  - Given a request with invalid user id, the system should return a 400 Bad Request status

#### Header
```
{
  "Authorization": "Bearer eyJhbGciOiJIUzI1N...."
}
```

#### Request
```
PUT /api/user/2478
{
  "email": "johnny419@gg.com",
  "pfp_link": "https://gravitar.com/2G3ti..."
}
```

#### Success Response
```
{
  "message": "user profile updated successfully",
  "user": {
    "id": "2478",
    "firstName": "John",
    "lastName": "Doe",
    "email": "johnny419@gg.com",
    "pfp_link": "https://gravitar.com/2G3ti..."
  },
}
```

#### Error Response(invalid token)
```
{
  "message": "could not update user profile",
  "error": "user does not have access to this resource",
  "statusCode": 401,
}
```

#### Error Response(invalid user)
```
{
  "message": "could not update user profile",
  "error": "user does not exist",
  "statusCode": 400,
}
```


<br></br>
### Testing
 1. Unit Tests
    - The system should have unit tests for retrieving user profile, covering scenarios of successful and failed attempts, and invalid token
    - The system should also have unit tests for updating iser profile, covering successful and failed attempts, and invalid token
    - The system should have unit tests to ensure that users cannot retrieve or update data that they do not have access to
