# Mailsight.io API Documentation

## Signup
To access the API, you will need an `API-KEY`. To request one, please visit our website [mailsight.io](https://mailsight.io/)

## Authentication
Always add an `x-api-key` in the header of all API requests.

## Resources
### Leads
#### Create a Lead
`POST https://api.mailsight.io/leads`
**Body**
```json
{
	firstName: '', // REQUIRED
	lastName: '', // REQUIRED
	middleName: '', // OPTIONAL
	domain: 'example.com' // REQUIRED
}
```
**Response**
```json
{
	leadId: '629aee1d43ec45b35fab90bc',
}
```

#### Get  Last 25 Leads
`GET https://api.mailsight.io/leads`
**Response**
```json
[
  {
    "firstName": "Jon",
    "lastName": "Doe",
    "middleName": "",
    "domain": "exampleone.com",
    "locale": "",
    "createdAt": "2022-07-26T08:39:28.228Z",
    "user": {
      "name": "Jos",
      "_id": "625saa7dfe22643aaa29828e"
    },
    "pending": true,
    "emails": ["jon@exampleone.ca"]
  },
  {
    "firstName": "Jane",
    "lastName": "Doe",
    "middleName": "",
    "domain": "exampletwo.com",
    "locale": "",
    "createdAt": "2022-07-26T08:39:28.228Z",
    "user": {
      "name": "Jos",
      "_id": "625saa7dfe22643aaa29828e"
    },
    "pending": false,
    "emails": ["janedoe@exampletwo.com", "jane@exampletwo.com"]
  }
]
```
#### Get a Specific Lead Using LeadId
`GET https://api.mailsight.io/leads/<leadId>`
**Response**
```json
{
    "firstName": "Jon",
    "lastName": "Doe",
    "middleName": "",
    "domain": "exampleone.com",
    "locale": "",
    "createdAt": "2022-07-26T08:39:28.228Z",
    "user": {
      "name": "Jos",
      "_id": "625saa7dfe22643aaa29828e"
    },
    "pending": true,
    "emails": ["jon@exampleone.ca"]
}
```
### Validation Requests
`POST https://api.mailsight.io/email-validation`
####  Create Validation Request
**Body**
```json
{
	"email": "emailtobevalidated@domain.com"
}
```
**Response**
```json
{
	"message":  "Email pending validation"
}
```

#### Fetch All Validation Requests
`GET https://api.mailsight.io/email-validate`
**Response**
```json
[
    {
        "email": "emailtobevalidated@domain.com",
        "status": "PENDING",
        "createdAt": "2022-07-31T21:44:58.427Z"
    },
    {
        "email": "emailtobevalidatedtwo@domain.com",
        "status": "VALID",
        "createdAt": "2022-07-31T21:44:58.427Z"
    }
]
```

#### Fetch Specific Validation Request
`GET https://api.mailsight.io/email-validate/<email>`
e.g
`GET https://api.mailsight.io/email-validate/emailtobevalidated@domain.com`
**Response**
```json
{
    "email": "emailtobevalidated@domain.com",
    "status": "PENDING",
    "createdAt": "2022-07-31T21:44:58.427Z"
},
```

