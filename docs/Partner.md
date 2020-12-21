# Application creation API
```shell
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'X-Api-Key: f3a25750-1e7f-4c34-84ae-c8ca92f1d211'
 'https://lkext.lendingkart.com/v2/partner/leads/create-application'
```

This api creates an application in lendingkart system and returns a leadId along with an applicationId on SUCCESS.

### HTTP Request

`POST https://lkext.lendingkart.com/v2/partner/leads/create-application`



> Output response:

```json
{
  "leadId": "341134",
  "applicationId": null,
  "message": "Application or lead already exist with us",
  "errorMessageList": null,
  "uniqueId": "string",
  "loanDeliveryMethod": null
}
```
### Query Parameters

No query parameter

### Sample Request body

```json
{
  "firstName": "Bala",
  "lastName": "Ganesh",
  "email": "Bala.Ganeshtest1@example.com",
  "mobile": "6666698762",
  "businessRevenue": 5000000,
  "businessAge": 24,
  "registeredAs": "Proprietorship",
  "personalDob": "1990-05-21",
  "personalPAN": "ARTPA1156H",
  "gender": "MALE",
  "cibilConsentForLK": true,
  "mobileNoVerified": true,
  "personalAddress": {
    "ownership": "string",
    "address": "4/5, Race Course Road",
    "city": "Coimbatore",
    "state": "TamilNadu",
    "pincode": "641041"
  },
  "businessRunBy": "Self",
  "loanAmount": 100000,
  "typeOfLoan": "INSTANT",
  "companyName": "Sakthi Enterprises",
  "businessAddress": {
    "ownership": "string",
    "address": "4/5, Race Course Road",
    "city": "Coimbatore",
    "state": "TamilNadu",
    "pincode": "641041"
  },
  "loanNeedTime": "After 2 weeks",
  "uniqueId": "string",
  "otherFields": {}
}

## Response Body
Field | Description | Data Type
------| -----------|---------
 leadId | This is unique leadId | String
 application ID | This is application id | String
 message | This is message returned | String
 loanDeliveryMethod | This is delivery method of you application | String
 leadId | This is unique leadId | String

<aside class="success">
Succesful api call would give you 200
</aside>

[To try this Api please click this](https://lkext.lendingkart.com/apidoc/home.html#!/Partner_Controller/leadApplicationCreationUsingPOST)

# Document upload API
```shell
curl -X POST --header 'Content-Type: multipart/form-data' --header 'Accept: */*' --header 'X-Api-Key: f3a25750-1e7f-4c34-84ae-c8ca92f1d211' {"type":"formData"}
 'https://lkext.lendingkart.com/v2/partner/leads/documents'
```

This API enables document upload functionality for partners.

### HTTP Request

`POST https://lkext.lendingkart.com/v2/partner/leads/documents`


```json

```
### Query Parameters

|Parameter|Description|Data Type|Required|
|---------|-----------|---------|--------|
|applicationId|This is application id|String|true|
|documentType|This is document type| String |true|
|bankName|This is bank name|String|false|
|bankAccountNo|This is bankAccountNo|String|false|


<aside class="success">
Succesful api call would give you 200
</aside>

[To try this Api please click this](https://lkext.lendingkart.com/apidoc/home.html#!/Partner_Controller/uploadDocumentsUsingPOST)

#Document Status API

```shell
curl -X GET --header 'Accept: application/json' --header 'X-Api-Key: f3a25750-1e7f-4c34-84ae-c8ca92f1d211'
'https://lkext.lendingkart.com/v2/partner/leads/document-status?applicationId=LAI-110081529&context=PRE_TERMS'
```
> Output response:

```json
[
  {
    "documentType": "string",
    "documents": [
      {
        "documentTag": "string",
        "latestVerificationDate": "2020-12-13T14:33:39.948Z",
        "pendencyDetails": [
          {
            "autoGenText": "string",
            "comments": "string",
            "uuid": "string",
            "verificationDate": "2020-12-13T14:33:39.948Z",
            "verificationStatus": "PENDING"
          }
        ]
      }
    ],
    "latestVerificationStatus": "PENDING"
  }
]
```
This API will provide document status and any document pendencies raised for an application

### HTTP Request

`GET https://lkext.lendingkart.com/v2/partner/leads/document-status`

### Query Parameters

|Parameter|Description|Data Type|Required|
|---------|-----------|---------|--------|
|applicationId|This is application id|String|true|
|context|This is pre-term,posterm,all|String|true|

<aside class="warning">
This api do not contain request body
</aside>

##Response Body

Field | Description | Data Type
------| -----------|---------
 leadId | This is unique leadId | String
 application ID | This is application id | String
 message | This is message returned | String
 loanDeliveryMethod | This is delivery method of you application | String
 leadId | This is unique leadId | String

<aside class="success">
Succesful api call would give you 200
</aside>

[To try this Api please click this](https://lkext.lendingkart.com/apidoc/home.html#!/Partner_Controller/getDocumentPendenciesUsingGET)

#disbursal data API

```shell
curl -X GET --header 'Accept: application/json' --header 'X-Api-Key: f3a25750-1e7f-4c34-84ae-c8ca92f1d211'
 'https://lkext.lendingkart.com/v2/partner/leads/disbursal-data/LAI-110081529'
```
> Output response:

```json
{
  "disbursalDate": "2018-03-21T18:30:00.000Z",
  "emiDetails": {
    "emiAmount": 0,
    "emiEndDate": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
    "emisRemaining": 0,
    "latestEmiDelay": 0,
    "maxDelay": 0,
    "nextDueDate": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
    "totalEmis": 0
  },
  "interestRate": 36,
  "interestType": "Fixed",
  "loanAmount": 500010,
  "loanBankAccountDetails": {
    "accountHolderName": "Bala",
    "accountNumber": "88888888888",
    "accountType": "Savings account",
    "bankName": "AXIS BANK",
    "branchName": "Koramangala"
  },
  "loanDisbursalAmount": 500000,
  "loanId": "LAI-110081529"
}
```
This API provides the details related to disbursal of a loan.

### HTTP Request

`GET https://lkext.lendingkart.com/v2/partner/leads/disbursal-data/<your applicationId>`

### Query Parameters
No query parameters

<aside class="warning">
This api do not contain request body
</aside>

##Response Body

Field | Description | Data Type
------| -----------|---------
 leadId | This is unique leadId | String
 application ID | This is application id | String
 message | This is message returned | String
 loanDeliveryMethod | This is delivery method of you application | String
 leadId | This is unique leadId | String

<aside class="success">
Succesful api call would give you 200
</aside>

[To try this Api please click this](https://lkext.lendingkart.com/apidoc/home.html#!/Partner_Controller/getDocumentPendenciesUsingGET)