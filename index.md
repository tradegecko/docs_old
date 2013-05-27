## TradeGecko API
***

### API Endpoint
    https://api.tradegecko.com/

### Versioning
    Header: <Accept: application/vnd.tradegecko.v1+json>

## Creating an application
***

  In order to use the TradeGecko API, you must first have a TradeGecko 
  account, you can register a new application at http://go.tradegecko.com/oauth/applications. 
  After successfully creating a new application, you will be given a set of 2
  unique keys: 

  - APPLICATION ID
  - APPLICATION SECRET
  
  These keys are needed in order to obtain an access token to make the API calls.

  TradeGecko is based on [version 22 of the OAuth 2.0 specification](http://tools.ietf.org/html/draft-ietf-oauth-v2-22).

  If you are already familiar with OAuth, then all you really need to know
  about are the two authentication endpoints. The authorization endpoint
  and the token request endpoint.

  These endpoints are:

  - **https://api.tradegecko.com/oauth/authorize**
  - **https://api.tradegecko.com/oauth/token**

## Getting an Authorization Code
***

   An authorization code is the key used to retrieve the access token. 
   In order to acquire an authorization code, you need to send your user
   to the authorization endpoint.

  `https://api.tradegecko.com/oauth/authorize?response_type=code&client_id=<CLIENT_ID>&redirect_uri=<REDIRECT_URI>`

  `CLIENT_ID` should be set to your application ID. `response_type` should 
  always be set to “code”. `REDIRECT_URI` should be set to the URL where 
  the user will be redirected back to after the request is authorized.

  Once the user has successfully authorized the application, she will be redirected to
  the `redirect_uri` with the authorization code as a query parameter.

  e.g. `https://my.application.com/auth/app/callback?code=12bc6909c57aaa930`

## Requesting an access token
***

   The access token is a unique key used to make requests to the API. In
   order to get an access token, user must make a POST request to 
   `https://api.tradegecko.com/oauth/token` with the `client_id`,
   `client_secret`, `redirect_uri`, `code` and `grant_type` as parameters.
   `code` must match the authorization code returned by the
   authorization endpoint and `grant_type` must be set to
   `authorization_code`

##### Sample request (cURL)

      curl -H "Content-type: application/json" -X POST http://api.tradegecko.com/oauth/token 
      -d '{"client_id": "d38abea2ef61c916a1e131de9fd04146579578f",
      "client_secret":"2kj2kd07e197f9942ca1876d759e9e9c45bdcdc",
      "redirect_uri": "https://my.application.com/auth/app/callback", 
      "code": "c3d11b23992f53d748c7b25148da1ac4d838919",
      "grant_type": "authorization_code"}'

##### Sample response

      {
        "access_token": "57ed301af04bf35b40f255feb5ef469ab2f046aff14",
        "expires_in": 7200,
        "refresh_token": "026b343de07818b3ffebfb3001eff9a00aea43da0 ",
        "scope": "public",
        "token_type": "bearer"
      }


## Making an API Call
***

   The TradeGecko API is entirely JSON based. In order to make an authenticated call
   to the API, you must include your access token with the call.
   OAuth2 uses a BEARER token that is passed along in an Authorization
   header.

##### Sample request (cURL)

      curl -H "Authorization: Bearer <ACCESS_TOKEN>" http://api.tradegecko.com/accounts

## Pagination
***

   The TradeGecko API enables pagination by allowing users to include 'limit'
   and 'page' parameters on GET requests to index pages. The default
   limit is 100 items.

##### Sample request (cURL)

      curl -H "Authorization: Bearer <ACCESS_TOKEN>" http://api.tradegecko.com/users?limit=20&page=1

## Filters
***

   The API also allows filtering of records by passing query parameters.
   These are the filters currently allowed by the API (where relevant):

   - ids
   - company_id
   - order_id
   - purchase_order_id
   - stock_adjustment_id
   - status
   - since

##### Sample request (cURL)

      curl -H "Authorization: Bearer <ACCESS_TOKEN>" http://api.tradegecko.com/users?ids[]=1&ids[]=2
      curl -H "Authorization: Bearer <ACCESS_TOKEN>" http://api.tradegecko.com/addresses?company_id=1

## Address
***

  This is an object representing an address of a company. A company can
  have multiple addresses but an address object belongs to only one
  company.


Attribute                | Type          | Description
------------------------ | ------------- | ------------
**id**                   | Integer       |  A unique identifier for the address
**company_id**           | Integer       |  The company id where the address belongs.
**city**                 | String        |  The primary country where company is located
**country**              | String        |  
**label**                | String        |
**state**                | String        |
**address1**             | String        |
**address2**             | String        |
**suburb**               | String        |
**zip_code**             | String        |
**phone_number**         | String        |
**email**                | String        |
  
#### Retrieve list of addresses
Retrieves list of addresses for all companies or addresses for a
certain company.

###### Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/addresses/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/addresses/

##### Sample Response

      {
        "addresses": [
            {
                "address1": "14 York St",
                "address2": null,
                "city": "Auckland",
                "company_id": 3,
                "country": "NZ",
                "email": null,
                "id": 3,
                "label": "Shipping",
                "phone_number": null,
                "state": "",
                "suburb": "Parnell",
                "zip_code": "123456"
            },
            {
                "address1": "7 Silk Road",
                "address2": null,
                "city": "Auckland",
                "company_id": 2,
                "country": "NZL",
                "email": null,
                "id": 42,
                "label": "Billing",
                "phone_number": null,
                "state": "",
                "suburb": "hernebay",
                "zip_code": "1022"
            },
      }

####   Retrieve a particular address

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/addresses/{ADDRESS_ID}/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/addresses/1

##### Sample Response

      {
          "address": {
              "address1": "14a York St",
              "address2": null,
              "city": "Auckland",
              "company_id": 3,
              "country": "NZ",
              "email": null,
              "id": 3,
              "label": "Shipping",
              "phone_number": null,
              "state": "",
              "suburb": "Parnell",
              "zip_code": "123456"
          }
      }

####   Create a new address

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/addresses/*

######     Arguments:
      address:
        company_id:   required
        label:        required
        address1:     required      
        address2:     optional
        city:         optional
        country:      optional
        zip_code:     optional
        suburb:       optional
        state:        optional
        phone_number: optional
        email:        optional

##### Sample Request

      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/addresses/ -d '{"address":{"company_id": 1, "label": "Main Office", 
      "address1": "12 Park Ave"}}'

##### Sample Response

      {
          "address": {
              "address1": "14a York St",
              "address2": null,
              "city": "Auckland",
              "company_id": 3,
              "country": "NZ",
              "email": null,
              "id": 3,
              "label": "Shipping",
              "phone_number": null,
              "state": "",
              "suburb": "Parnell",
              "zip_code": "123456"
          }
      }

####   Update an address

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/addresses/{ADDRESS_ID}/*

###### Arguments:
      address:
        label:        optional
        address1:     optional      
        address2:     optional
        city:         optional
        country:      optional
        zip_code:     optional
        suburb:       optional
        state:        optional
        phone_number: optional
        email:        optional

##### Sample Request

      curl -X PUT -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/addresses/1 -d '{"address":{"city": "Singapore", "country": "SG"}}'

###### Return:
      Returns 204 status when the address gets updated successfully. 

####   Delete an address  

######     Request:

Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/addresses/{ADDRESS_ID}/*

##### Sample Request

      curl -X DELETE -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/addresses/1

###### Return:
      Returns 204 status when the address gets deleted successfully. 

## Company
***
This is an object representing a company.

Attribute                      | Type          | Description
------------------------------ | ------------- | ------------
**id**                         | Integer       |  A unique identifier for the company
**name**                       | String        |  The name of the company
**description**                | String        |  A brief description of the company
**phone_number**               | String        |  The phone number of the company
**status**                     | String        |  Tells whether the company is 'active' or 'archived'
**email**                      | String        |  Primary email of the company
**website**                    | String        |
**company_type**               | String        |  Can be 'business', 'vendor' or 'consumer'
**company_code**               | String        |
**fax**                        | String        |
**default_tax_rate**           | Float         |
**default_discount_rate**      | Float         |
**address_ids**                | Array         |
**contact_ids**                | Array         |
**note_ids**                   | Array         |

####  Retrieve list of companies
Retrieve a list of all companies with 'active' status.

###### Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/companies/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/companies/

##### Sample response

      {
          "companies": [
              {
                  "address_ids": [ 1, 2 ],
                  "company_code": "XYZ",
                  "company_type": "vendor",
                  "contact_ids": [ 33, 35 ],
                  "default_discount_rate": null,
                  "default_tax_rate": null,
                  "description": null,
                  "email": "xyz@xyzshirts.sg",
                  "fax": null,
                  "id": 369,
                  "name": "XYZ Shirts Pte Ltd",
                  "note_ids": [ 6 ],
                  "phone_number": "+65 8111 1111",
                  "status": "active",
                  "website": "http://www.xyzshirts.sg"
              },
              {
                  "address_ids": [ 376 ],
                  "company_code": "BOT",
                  "company_type": "business",
                  "contact_ids": [ 366 ],
                  "default_discount_rate": null,
                  "default_tax_rate": null,
                  "description": null,
                  "email": "info@theboutique.sg",
                  "fax": null,
                  "id": 423,
                  "name": "The Boutique",
                  "note_ids": [],
                  "phone_number": "+65 7777 7777",
                  "status": "active",
                  "website": "http://www.theboutique.sg"
              }
      }

####   Retrieve a specific company

###### Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/companies/{COMPANY_ID}/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/companies/1

##### Sample response

      {
          "company": {
              "address_ids": [ 326, 327 ],
              "company_code": "XYZ",
              "company_type": "vendor",
              "contact_ids": [ 335, 334 ],
              "default_discount_rate": null,
              "default_tax_rate": null,
              "description": null,
              "email": "xyz@xyzshirts.sg",
              "fax": null,
              "id": 369,
              "name": "XYZ Shirts Pte Ltd",
              "note_ids": [ 6 ],
              "phone_number": "+65 8111 1111",
              "status": "active",
              "website": "http://www.xyzshirts.sg"
          }
      }

####   Create a new company

###### Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/companies/*

######     Arguments:
      company:
        name:                   required
        email:                  optional
        phone_number:           optional
        website:                optional
        company_type:           optional
        online_id:              optional
        company_code:           optional
        fax:                    optional
        default_tax_rate:       optional
        default_discount_rate:  optional

##### Sample Request

      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/companies/ -d '{"company":{"name":"Tradegecko Pte Ltd.",
      "email": "info@tradegecko.com"}}'

##### Sample response

      {
          "company": {
              "address_ids": [ 326, 327 ],
              "company_code": "XYZ",
              "company_type": "vendor",
              "contact_ids": [ 335, 334 ],
              "default_discount_rate": null,
              "default_tax_rate": null,
              "description": null,
              "email": "xyz@xyzshirts.sg",
              "fax": null,
              "id": 369,
              "name": "XYZ Shirts Pte Ltd",
              "note_ids": [ 6 ],
              "phone_number": "+65 8111 1111",
              "status": "active",
              "website": "http://www.xyzshirts.sg"
          }
      }

####   Update a company

###### Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/companies/{COMPANY_ID}/*

######     Arguments:
      company:
        name:                   optional
        email:                  optional
        phone_number:           optional
        website:                optional
        company_type:           optional
        online_id:              optional
        company_code:           optional
        fax:                    optional
        default_tax_rate:       optional
        default_discount_rate:  optional

##### Sample Request

      curl -X PUT -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/companies/ -d '{"company":{"website": "http://tradegecko.com"}}'

###### Return:
      Returns 204 status when the company gets updated successfully. 

####   Delete a company

###### Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/companies/{COMPANY_ID}/*

##### Sample Request

      curl -X DELETE -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/companies/1

###### Return:
      Returns 204 status when the company gets deleted successfully. 


## Contact
***

  This is an object representing a contact.

Attribute                | Type          | Description
------------------------ | ------------- | ------------
**id**                   | Integer       |  A unique identifier for the address
**company_id**           | Integer       |  The company id where the address belongs.
**first_name**           | String        |  
**last_name**            | String        |  
**email**                | String        |
**location**             | String        |
**mobile**               | String        |
**phone**                | String        |
**fax**                  | String        |
**notes**                | String        |
**position**             | String        |

####   Retrieve list of contacts

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/contacts/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/contacts

##### Sample response

      {
          "contacts": [
              {
                  "company_id": 1,
                  "email": "john@myweb.sg",
                  "fax": null,
                  "first_name": "John",
                  "id": 335,
                  "last_name": "Doe",
                  "location": "Warehouse",
                  "mobile": "+65 9000 0000",
                  "notes": "",
                  "phone": "+65 8222 2222",
                  "position": "Warehouse Stock Coordinator"
              },
              {
                  "company_id": 1,
                  "email": "tom@myweb.sg",
                  "fax": null,
                  "first_name": "Tom",
                  "id": 334,
                  "last_name": "Smith",
                  "location": "Office",
                  "mobile": "+65 9999 0000",
                  "notes": "",
                  "phone": "+65 8111 1111",
                  "position": "Sales Manager"
              },
      }

####   Retrieve a specific contact

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/contacts/{CONTACT_ID}/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/contacts/1

##### Sample response

      {
          "contact": {
              "company_id": 31,
              "email": "john@mywebsite.sg",
              "fax": null,
              "first_name": "John",
              "id": 3,
              "last_name": "Doe",
              "location": "Warehouse",
              "mobile": "+65 9000 0000",
              "notes": "",
              "phone": "+65 8222 2222",
              "position": "Warehouse Stock Coordinator"
          }
      }

####   Create a new contact

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**    | *https://api.tradegecko.com/contacts/*

###### Arguments
      contact:
        company_id: required
        first_name: required
        last_name:  required
        email:      optional
        location:   optional
        mobile:     optional
        phone:      optional
        position:   optional
        notes:      optional
        fax:        optional

##### Sample Request

      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/contacts/ -d '{"contact":{"company_id": 1, first_name: "John",
      "last_name": "Gecko"}}'

##### Sample response

      {
          "contact": {
              "company_id": 31,
              "email": "john@mywebsite.sg",
              "fax": null,
              "first_name": "John",
              "id": 3,
              "last_name": "Doe",
              "location": "Warehouse",
              "mobile": "+65 9000 0000",
              "notes": "",
              "phone": "+65 8222 2222",
              "position": "Warehouse Stock Coordinator"
          }
      }

####   Update a contact

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/contacts/{CONTACT_ID}/*

###### Arguments
      contact:
        first_name: optional
        last_name:  optional
        email:      optional
        location:   optional
        mobile:     optional
        phone:      optional
        position:   optional
        notes:      optional
        fax:        optional

##### Sample Request

      curl -X PUT -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/contacts/1 -d '{"contact": { email: "john@mywebsite.sg",
      "mobile": "+65 1234 456"}}'


###### Return:
      Returns 204 status when the contact gets updated successfully. 

####   Delete a contact

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/contacts/{CONTACT_ID}/*

##### Sample Request

      curl -X DELETE -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/contacts/1 

###### Return:
      Returns 204 status when the contact gets deleted successfully. 


## Fulfillments
***
  This is an object representing a fulfillment.

Attribute                | Type          | Description
------------------------ | ------------- | ------------
**id**                   | Integer       |  A unique identifier for the address
**order_id**             | Integer       |  The company id where the address belongs.
**status**               | String        |  
**shiped_at**            | String        |  
**received_at**          | String        |
**delivery_type**        | String        | Could be 'Courier' or 'Pickup'
**tracking_number**      | String        |
**tracking_message**     | String        |
**created_at**           | String        |
**updated_at**           | String        |
**order_line_item_ids**  | Array         |

####   Retrieve list of fulfillments

###### Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/fulfillments/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/fulfillments

##### Sample response

      {
            "fulfillments": [
              {
                  "created_at": "2013-01-18T03:09:36Z",
                  "delivery_type": "Courier",
                  "id": 350,
                  "order_id": 101,
                  "order_line_item_ids": [ 303, 304, 302 ],
                  "received_at": null,
                  "shipped_at": "2013-01-09T00:00:00Z",
                  "status": null,
                  "tracking_message": null,
                  "tracking_number": "65656",
                  "updated_at": "2013-01-18T03:09:36Z"
              },
              {
                  "created_at": "2013-01-18T03:09:35Z",
                  "delivery_type": "Pickup",
                  "id": 339,
                  "order_id": 33,
                  "order_line_item_ids": [ 46 ],
                  "received_at": "2012-12-04T00:00:00Z",
                  "shipped_at": "2012-12-06T03:06:32Z",
                  "status": null,
                  "tracking_message": null,
                  "tracking_number": null,
                  "updated_at": "2013-01-18T03:09:35Z"
              }
          ]
      }

####  Retrieve a specific fulfillment item

###### Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/fulfillments/{FULFILLMENT_ID}*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/fulfillments/1

##### Sample response

      {
          "fulfillment": {
                "created_at": "2013-01-18T03:09:35Z",
                "delivery_type": "Pickup",
                "id": 1,
                "order_id": 33,
                "order_line_item_ids": [ 46 ],
                "received_at": "2012-12-04T00:00:00Z",
                "shipped_at": "2012-12-06T03:06:32Z",
                "status": null,
                "tracking_message": null,
                "tracking_number": null,
                "updated_at": "2013-01-18T03:09:35Z"
            }
      }

#### Create a new fulfillment

Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/fulfillments/*


######     Arguments:
      order_id: required
                Unique identifier for the order to be fulfilled
      order_line_items: required
                        An array of order line item ids to be fulfilled

##### Sample Request

      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/fulfillments/ -d '{"fulfillment": {"order_id": 18,
      "order_line_items": [{"id":28}, {"id":29}] }}'

##### Sample response

      {
        order_line_items:[
          {
            id: 1,
            order_id: 1,
            variant_id:3,
            fulfillment_id:1,
            discount: nil,
            quantity:"1.0",
            price:"123.0",
            tax_rate:"12.0",
            freeform:false,
            label: nil,
            position:0,
            image_url: nil
          }],
        fulfillment: {
          "id":1,
          "order_id":1,
          "status":nil,
          "shipped_at":"2013-05-20T02:20:34Z",
          "received_at":"2013-05-20T02:20:29Z",
          "delivery_type":"Pickup",
          "tracking_number":nil,
          "tracking_message":nil,
          "created_at":"2013-05-20T02:20:34Z",
          "updated_at":"2013-05-20T02:20:34Z",
          "order_line_item_ids":[1]
        }
      }

#### Update a fulfillment
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/fulfillments/{FULFILLMENT_ID}*

###### Arguments

      fulfillments:
        cc_tracking_email:   optional
        delivery_type:       optional
        received_at:         optional
        send_tracking_email: optional
        shipped_at:          optional
        tracking_message:    optional
        tracking_number:     optional

##### Sample Request

      curl -X PUT -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/fulfillments/1 -d '{"fulfillment": {"delivery_type": "Pickup", 
      "shipped_at": "Thu, 23 May 2013 00:00:00 GMT", "received_at": "Thu, 23 May 2013 00:00:00 GMT"}}

###### Return:
      Returns 204 status when the contact gets updated successfully. 

## Locations
***

####   Retrieve list of locations

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/locations/*

##### Sample Response

      {
          "locations": [
              {
                  "account_id": 4,
                  "address1": "888 Orchard Road",
                  "address2": "#08-88",
                  "city": "Singapore",
                  "country": "Singapore",
                  "id": 159,
                  "label": "Head Office",
                  "state": "SG",
                  "status": "active",
                  "suburb": "Singapore",
                  "zip_code": "888888"
              },
              {
                  "account_id": 4,
                  "address1": "999 Beach Road",
                  "address2": "",
                  "city": "Singapore",
                  "country": "Singapore",
                  "id": 160,
                  "label": "Warehouse",
                  "state": "SG",
                  "status": "active",
                  "suburb": "Singapore",
                  "zip_code": "999999"
              }
          ]
      }

####   Retrieve a specific location

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/locations/{LOCATION_ID}*

##### Sample Response

      {
          "location": {
              "account_id": 4,
              "address1": "999 Beach Road",
              "address2": "",
              "city": "Singapore",
              "country": "Singapore",
              "id": 160,
              "label": "Warehouse",
              "state": "SG",
              "status": "active",
              "suburb": "Singapore",
              "zip_code": "999999"
          }
      }

####   Create a new location

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**    | *https://api.tradegecko.com/locations/*

######     Arguments:
      label: required

##### Sample Response

      {
          "location": {
              "account_id": 4,
              "address1": "999 Beach Road",
              "address2": "",
              "city": "Singapore",
              "country": "Singapore",
              "id": 160,
              "label": "Warehouse",
              "state": "SG",
              "status": "active",
              "suburb": "Singapore",
              "zip_code": "999999"
          }
      }

####   Update a location

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/locations/{LOCATION_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a location

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/locations/{LOCATION_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Notes
***
  
####   Retrieve list of notes

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/notes/*

##### Sample Response

      {
          "notes": [
              {
                  "body": "Dropped stock off they loved it",
                  "company_id": 105,
                  "created_at": "2013-02-21T20:44:09Z",
                  "id": 42,
                  "updated_at": "2013-02-21T20:44:09Z",
                  "user_id": 26
              },
              {
                  "body": "This is a test note. Yay!  (if it works)",
                  "company_id": 105,
                  "created_at": "2012-12-11T13:55:12Z",
                  "id": 1,
                  "updated_at": "2012-12-11T13:55:12Z",
                  "user_id": 26
              }
          ]
      }

####   Retrieve a specific note

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/notes/{NOTE_ID}*

##### Sample Response

      {
          "note": {
              "body": "This is a test note. Yay!  (if it works)",
              "company_id": 105,
              "created_at": "2012-12-11T13:55:12Z",
              "id": 1,
              "updated_at": "2012-12-11T13:55:12Z",
              "user_id": 26
          }
      }

####   Create a new note

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**    | *https://api.tradegecko.com/notes/*

######     Arguments:
      company_id: required
                  The id of the company where the address is to be
                  added.

##### Sample Response

      {
          "note": {
              "body": "This is a test note. Yay!  (if it works)",
              "company_id": 105,
              "created_at": "2012-12-11T13:55:12Z",
              "id": 1,
              "updated_at": "2012-12-11T13:55:12Z",
              "user_id": 26
          }
      }

####   Update a note

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/notes/{NOTE_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a note

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE**    | *https://api.tradegecko.com/notes/{NOTE_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Order Line Items
***

####   Retrieve list of order line items

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/order_line_items/*

##### Sample Response

      {
          "order_line_items": [
              {
                  "discount": null,
                  "freeform": null,
                  "fulfillment_id": 717,
                  "id": 320,
                  "image_url": null,
                  "label": null,
                  "order_id": 99,
                  "position": null,
                  "price": "10.0",
                  "quantity": "1.0",
                  "tax_rate": "15.0",
                  "variant_id": 1018
              },
              {
                  "discount": null,
                  "freeform": null,
                  "fulfillment_id": 717,
                  "id": 319,
                  "image_url": "https://images.com/thumbnail.jpeg",
                  "label": null,
                  "order_id": 99,
                  "position": null,
                  "price": "24.0",
                  "quantity": "3.0",
                  "tax_rate": "15.0",
                  "variant_id": 1026
              }
          ]
      }

####   Retrieve a specific order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

##### Sample Response

      {
          "order_line_item": {
              "discount": null,
              "freeform": null,
              "fulfillment_id": 717,
              "id": 319,
              "image_url": "https://images.com/thumbnail.jpeg",
              "label": null,
              "order_id": 99,
              "position": null,
              "price": "24.0",
              "quantity": "3.0",
              "tax_rate": "15.0",
              "variant_id": 1026
          }
      }

####   Create a new order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/order_line_items/*

##### Sample Response

      {
          "order_line_item": {
              "discount": null,
              "freeform": null,
              "fulfillment_id": 717,
              "id": 319,
              "image_url": "https://images.com/thumbnail.jpeg",
              "label": null,
              "order_id": 99,
              "position": null,
              "price": "24.0",
              "quantity": "3.0",
              "tax_rate": "15.0",
              "variant_id": 1026
          }
      }

####   Update an order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete an order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Orders
***

####   Retrieve list of orders

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/orders/*

##### Sample Response

      {
          "orders": [
             {
                "assignee_id": null,
                "billing_address_id": 102,
                "cached_total": "74.75",
                "company_id": 104,
                "created_at": "2013-03-24T05:07:21Z",
                "default_price_type": null,
                "due_at": "2013-04-07",
                "email": "user@my.application.com",
                "fulfillment_ids": [ 4 ],
                "fulfillment_status": "shipped",
                "id": 5,
                "invoice_number": "INV0032",
                "issued_at": "2013-03-24",
                "notes": null,
                "order_line_item_ids": [ 11515 ],
                "order_number": "SO02000",
                "payment_status": "unpaid",
                "phone_number": "6543 5432",
                "reference_number": null,
                "shipping_address_id": 102,
                "shopify": null,
                "status": "fulfilled",
                "stock_location_id": 159,
                "tax_label": "GST",
                "tax_override": null,
                "tax_type": "exclusive",
                "tracking_number": null,
                "updated_at": "2013-03-24T05:07:46Z",
                "user_id": 13,
                "xero": null
             }
          ]
      }

####   Retrieve a specific order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/orders/{ORDER_ID}*

##### Sample Response

      {
          "order": {
              "assignee_id": null,
              "billing_address_id": 102,
              "cached_total": "74.75",
              "company_id": 104,
              "created_at": "2013-03-24T05:07:21Z",
              "default_price_type": null,
              "due_at": "2013-04-07",
              "email": "user@my.application.com",
              "fulfillment_ids": [ 4 ],
              "fulfillment_status": "shipped",
              "id": 5,
              "invoice_number": "INV0032",
              "issued_at": "2013-03-24",
              "notes": null,
              "order_line_item_ids": [ 11515 ],
              "order_number": "SO02000",
              "payment_status": "unpaid",
              "phone_number": "6543 5432",
              "reference_number": null,
              "shipping_address_id": 102,
              "shopify": null,
              "status": "fulfilled",
              "stock_location_id": 159,
              "tax_label": "GST",
              "tax_override": null,
              "tax_type": "exclusive",
              "tracking_number": null,
              "updated_at": "2013-03-24T05:07:46Z",
              "user_id": 13,
              "xero": null
          }
      }

####   Create a new order

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/orders/{ORDER_ID}*

##### Sample Response

      {
          "order": {
              "assignee_id": null,
              "billing_address_id": 102,
              "cached_total": "74.75",
              "company_id": 104,
              "created_at": "2013-03-24T05:07:21Z",
              "default_price_type": null,
              "due_at": "2013-04-07",
              "email": "user@my.application.com",
              "fulfillment_ids": [ 4 ],
              "fulfillment_status": "shipped",
              "id": 5,
              "invoice_number": "INV0032",
              "issued_at": "2013-03-24",
              "notes": null,
              "order_line_item_ids": [ 11515 ],
              "order_number": "SO02000",
              "payment_status": "unpaid",
              "phone_number": "6543 5432",
              "reference_number": null,
              "shipping_address_id": 102,
              "shopify": null,
              "status": "fulfilled",
              "stock_location_id": 159,
              "tax_label": "GST",
              "tax_override": null,
              "tax_type": "exclusive",
              "tracking_number": null,
              "updated_at": "2013-03-24T05:07:46Z",
              "user_id": 13,
              "xero": null
          }
      }

####   Update an order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/orders/{ORDER_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Photos
***

####   Retrieve list of variant images

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/images/*

##### Sample Response

      {
          "images": [
              {
                  "base_path": "https://images.com/variant_image/image/1",
                  "file_name": "0icff-04.jpg",
                  "id": 1,
                  "name": "p16t7iul8c1qjg11561v3d14mm1grm5.jpg",
                  "position": null,
                  "uploader_id": null,
                  "variant_id": 2,
                  "versions": [
                      "thumbnail"
                  ]
              },
              {
                  "base_path": "https://images.com/variant_image/image/1",
                  "file_name": "alexchloe01.jpg",
                  "id": 2,
                  "name": "p16t7jbnv81kfr1egp1pd51o9f19ig5.jpg",
                  "position": null,
                  "uploader_id": null,
                  "variant_id": 2,
                  "versions": [
                      "thumbnail"
                  ]
              }
          ]
      }

####  Add a new variant image

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/images/*

##### Sample Response

      {
          "image": {
                  "base_path": "https://images.com/variant_image/image/1",
                  "file_name": "0icff-04.jpg",
                  "id": 1,
                  "name": "p16t7iul8c1qjg11561v3d14mm1grm5.jpg",
                  "position": null,
                  "uploader_id": null,
                  "variant_id": 2,
                  "versions": [ "thumbnail" ]
          }
      }

####   Delete a variant image

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/images/{IMAGE_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Procurements
***

####   Retrieve list of procurements

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/procurements/*

##### Sample Response

      {
          "procurements": [
              {
                  "created_at": "2013-02-21T23:17:19Z",
                  "id": 51,
                  "purchase_order_id": 127,
                  "purchase_order_line_item_ids": [
                      172
                  ],
                  "received_at": "2013-02-21T23:16:56Z",
                  "updated_at": "2013-02-21T23:17:19Z"
              },
              {
                  "created_at": "2013-01-25T10:43:16Z",
                  "id": 18,
                  "purchase_order_id": 127,
                  "purchase_order_line_item_ids": [
                      175
                  ],
                  "received_at": "2013-01-25T10:43:13Z",
                  "updated_at": "2013-01-25T10:43:16Z"
              }
          ],
          "purchase_order_line_items": [
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 172,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 0,
                  "price": null,
                  "procurement_id": 51,
                  "purchase_order_id": 127,
                  "quantity": "11.0",
                  "tax_rate": "15.0",
                  "variant_id": 13410
              },
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 175,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 1,
                  "price": null,
                  "procurement_id": 18,
                  "purchase_order_id": 127,
                  "quantity": "20.0",
                  "tax_rate": "15.0",
                  "variant_id": 1996
              }
          ]
      }

####   Retrieve a specific procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/procurements/{PROCUREMENT_ID}*

##### Sample Response

      {
          "procurement": {
              "created_at": "2013-02-21T23:17:19Z",
              "id": 51,
              "purchase_order_id": 127,
              "purchase_order_line_item_ids": [
                  172
              ],
              "received_at": "2013-02-21T23:16:56Z",
              "updated_at": "2013-02-21T23:17:19Z"
          },
          "purchase_order_line_items": [
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 172,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 0,
                  "price": null,
                  "procurement_id": 51,
                  "purchase_order_id": 127,
                  "quantity": "11.0",
                  "tax_rate": "15.0",
                  "variant_id": 13410
              }
          ]
      }

####   Create a new procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/procurements/*

####   Update a procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/procurements/{PROCUREMENT_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Products
***

####   Retrieve list of products 

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/products/*

##### Sample Response

      {
          "products": [
              {
                  "created_at": "2013-04-18T04:40:00Z",
                  "description": "An awesome product",
                  "id": 2,
                  "image_url": null,
                  "name": "BUTTERFLY TEE",
                  "opt1": "Color",
                  "opt2": "Size",
                  "opt3": null,
                  "product_type": "T-Shirt",
                  "search_cache": "DCP022-S Small DCP022-M Medium DCP022-L Large DCP022-XL X-Large",
                  "status": "active",
                  "tag_string": "T-Shirts,Winter 2012",
                  "updated_at": "2013-04-18T04:40:00Z",
                  "variant_ids": [ 1, 2, 3, 4 ],
                  "vendor": "Dead Castle Project"
              },
              {
                  "created_at": "2013-04-18T04:39:59Z",
                  "description": "A description of the product",
                  "id": 21823,
                  "image_url": "https://images.com/thumbnail_img.jpg",
                  "name": "ALMOST FAMOUS TEE",
                  "opt1": "Color",
                  "opt2": "Size",
                  "opt3": null,
                  "product_type": "T-Shirt",
                  "search_cache": "DCP021-S Small DCP021-M Medium DCP021-L Large DCP021-XL X-Large",
                  "status": "active",
                  "tag_string": "T-Shirts,Winter 2012",
                  "updated_at": "2013-04-18T04:39:59Z",
                  "variant_ids": [ 5, 6, 7, 8 ],
                  "vendor": "Dead Castle Project"
              }
          ]
      }

####   Retrieve a specific product

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/products/{PRODUCT_ID}*

##### Sample Response

      {
          "product": {
              "created_at": "2013-04-18T04:40:00Z",
              "description": "An awesome product",
              "id": 2,
              "image_url": null,
              "name": "BUTTERFLY TEE",
              "opt1": "Color",
              "opt2": "Size",
              "opt3": null,
              "product_type": "T-Shirt",
              "search_cache": "DCP022-S Small DCP022-M Medium DCP022-L Large DCP022-XL X-Large",
              "status": "active",
              "tag_string": "T-Shirts,Winter 2012",
              "updated_at": "2013-04-18T04:40:00Z",
              "variant_ids": [ 1, 2, 3, 4 ],
              "vendor": "Dead Castle Project"
          }
      }


####   Create a new product

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/products/*

##### Sample Response

      {
          "product": {
              "created_at": "2013-04-18T04:40:00Z",
              "description": "An awesome product",
              "id": 2,
              "image_url": null,
              "name": "BUTTERFLY TEE",
              "opt1": "Color",
              "opt2": "Size",
              "opt3": null,
              "product_type": "T-Shirt",
              "search_cache": "DCP022-S Small DCP022-M Medium DCP022-L Large DCP022-XL X-Large",
              "status": "active",
              "tag_string": "T-Shirts,Winter 2012",
              "updated_at": "2013-04-18T04:40:00Z",
              "variant_ids": [ 1, 2, 3, 4 ],
              "vendor": "Dead Castle Project"
          }
      }

####   Update a product

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/products/{PRODUCT_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a product

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/products/{PRODUCT_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Purchase Orders
***

####   Retrieve list of purchase orders 

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/purchase_orders/*

##### Sample Response

      {
          "purchase_orders": [
              {
                  "billing_address_id": 153,
                  "company_id": 128,
                  "created_at": "2013-05-08T05:45:57Z",
                  "due_at": "2013-05-22",
                  "email": "carlos@carlsbikes.com",
                  "id": 466,
                  "notes": null,
                  "order_number": "PO0084",
                  "procurement_ids": [],
                  "procurement_status": "unprocured",
                  "purchase_order_line_item_ids": [
                      1928
                  ],
                  "reference_number": null,
                  "status": "active",
                  "stock_location_id": 159,
                  "tax_type": "inclusive",
                  "updated_at": "2013-05-08T05:46:34Z",
                  "vendor_address_id": 188,
                  "xero": "f74d194f-3a96-47de-b783-77114d26d7e9"
              },
              {
                  "billing_address_id": 18,
                  "company_id": 128,
                  "created_at": "2012-11-01T02:09:32Z",
                  "due_at": null,
                  "email": "",
                  "id": 5,
                  "notes": "Thanks Carl for your awesome bike parts",
                  "order_number": "PO0005",
                  "procurement_ids": [],
                  "procurement_status": "unprocured",
                  "purchase_order_line_item_ids": [
                      4,
                      2,
                      3
                  ],
                  "reference_number": "TR00345",
                  "status": "received",
                  "stock_location_id": 18,
                  "tax_type": null,
                  "updated_at": "2013-05-08T03:10:15Z",
                  "vendor_address_id": 188,
                  "xero": null
              },
          ]
      }

####   Retrieve a specific purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/purchase_orders/{PURCHASE_ORDER_ID}*

##### Sample response

      {
          "purchase_order": {
              "billing_address_id": 153,
              "company_id": 103,
              "created_at": "2013-04-30T07:07:13Z",
              "due_at": "2013-05-14",
              "email": "office@mikesbikes.com",
              "id": 412,
              "notes": null,
              "order_number": "PO0082",
              "procurement_ids": [ 249 ],
              "procurement_status": "partial",
              "purchase_order_line_item_ids": [ 1674, 1672, 1671, 1673 ],
              "reference_number": null,
              "status": "active",
              "stock_location_id": 160,
              "tax_type": "inclusive",
              "updated_at": "2013-05-08T03:10:25Z",
              "vendor_address_id": 101,
              "xero": "b5a6d858-3e99-4df5-91e4-e8a01b35828a"
          }
      }

####   Create a new purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/purchase_orders/*

##### Sample Response

      {
          "purchase_order": {
              "billing_address_id": 153,
              "company_id": 103,
              "created_at": "2013-04-30T07:07:13Z",
              "due_at": "2013-05-14",
              "email": "office@mikesbikes.com",
              "id": 412,
              "notes": null,
              "order_number": "PO0082",
              "procurement_ids": [ 249 ],
              "procurement_status": "partial",
              "purchase_order_line_item_ids": [ 1674, 1672, 1671, 1673 ],
              "reference_number": null,
              "status": "active",
              "stock_location_id": 160,
              "tax_type": "inclusive",
              "updated_at": "2013-05-08T03:10:25Z",
              "vendor_address_id": 101,
              "xero": "b5a6d858-3e99-4df5-91e4-e8a01b35828a"
          }
      }

####   Update a purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/purchase_orders/{PURCHASE_ORDER_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/purchase_orders/{PURCHASE_ORDER_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

## Stock Adjustments
***

####   Retrieve list of stock adjustments

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/stock_adjustments/*

##### Sample Response

      {
          "stock_adjustment_line_items": [
              {
                  "id": 76,
                  "position": 0,
                  "quantity": "-1.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 54725
              }
          ],
          "stock_adjustments": [
              {
                  "adjustment_number": "SA0001",
                  "id": 40,
                  "notes": null,
                  "reason": "damaged",
                  "stock_adjustment_line_item_ids": [
                      76
                  ],
                  "stock_location_id": 159,
                  "updated_at": "2013-05-22T00:22:26Z"
              }
          ]
      }

####   Create a new stock adjustment

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/stock_adjustments/*

##### Sample Response

      {
          "stock_adjustment_line_items": [
              {
                  "id": 76,
                  "position": 0,
                  "quantity": "-1.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 54725
              }
          ],
          "stock_adjustments": {
              "adjustment_number": "SA0001",
              "id": 40,
              "notes": null,
              "reason": "damaged",
              "stock_adjustment_line_item_ids": [
                  76
              ],
              "stock_location_id": 159,
              "updated_at": "2013-05-22T00:22:26Z"
          }
      }

## Users
***

####   Retrieve list of users

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/users/*

##### Sample Response

      {
          "users": [
              {
                  "account_id": 4,
                  "avatar_url": "/assets/avatars/avatar3.png",
                  "email": "user@tradegecko.com",
                  "first_name": "Steve",
                  "id": 1339,
                  "last_name": "Lawrence",
                  "last_sign_in_at": "2013-05-21T06:49:24Z",
                  "location": null,
                  "mobile_phone": null,
                  "phone_number": null,
                  "position": null,
                  "roles": [ "user" ],
                  "status": "active"
              },
              {
                  "account_id": 4,
                  "avatar_url": "https://images.com/image.jpg",
                  "email": "admin@tradegecko.com",
                  "first_name": "John",
                  "id": 27,
                  "last_name": "Smith",
                  "last_sign_in_at": "2013-05-21T09:06:53Z",
                  "location": null,
                  "mobile_phone": null,
                  "phone_number": null,
                  "position": null,
                  "roles": [ "user", "admin" ],
                  "status": "active"
              }
          ]
      }

####   Retrieve a specific user

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/users/{USER_ID}*

##### Sample Response

      {
          "user": {
              "account_id": 4,
              "avatar_url": "/assets/avatars/avatar3.png",
              "email": "user@tradegecko.com",
              "first_name": "Steve",
              "id": 1339,
              "last_name": "Lawrence",
              "last_sign_in_at": "2013-05-21T06:49:24Z",
              "location": null,
              "mobile_phone": null,
              "phone_number": null,
              "position": null,
              "roles": [ "user" ],
              "status": "active"
          }
      }


####   Retrieve current_user

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/users/current*

##### Sample Response

      {
          "user": {
              "account_id": 4,
              "avatar_url": "/assets/avatars/avatar3.png",
              "email": "user@tradegecko.com",
              "first_name": "Steve",
              "id": 1339,
              "last_name": "Lawrence",
              "last_sign_in_at": "2013-05-21T06:49:24Z",
              "location": null,
              "mobile_phone": null,
              "phone_number": null,
              "position": null,
              "roles": [ "user" ],
              "status": "active"
          }
      }

####   Update a user

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/users/{USER_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a user

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE**    | *https://api.tradegecko.com/users/{USER_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Add an avatar

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**    | *https://api.tradegecko.com/users/{USER_ID}/avatar*

## Variants
***

####   Retrieve list of variants

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/variants/*

##### Smple Response

      {
          "images": [
              {
                  "base_path": "https://images.com/image/52290",
                  "file_name": "ywgNWV3fD1_img.jpg",
                  "id": 52290,
                  "name": "img.jpg",
                  "position": 1,
                  "uploader_id": 13,
                  "variant_id": 54721,
                  "versions": [ "thumbnail" ]
              },
              {
                  "base_path": "https://images.com/image/52291",
                  "file_name": "U0nUt8CeW_img.jpg",
                  "id": 52291,
                  "name": "img.jpg",
                  "position": 2,
                  "uploader_id": 13,
                  "variant_id": 54721,
                  "versions": [ "thumbnail" ]
              },
          ],
          "variants": [
              {
                  "cost_price": "16.0",
                  "description": null,
                  "id": 54725,
                  "image_ids": [],
                  "is_online": false,
                  "keep_selling": false,
                  "last_cost_price": null,
                  "manage_stock": true,
                  "max_online": null,
                  "moving_average_cost": "0",
                  "name": "Small",
                  "online_id": null,
                  "opt1": "White",
                  "opt2": "Small",
                  "opt3": null,
                  "position": 1,
                  "product_id": 21824,
                  "reorder_point": null,
                  "retail_price": "90.0",
                  "sku": "DCP022-S",
                  "status": "active",
                  "stock_levels": {
                      "159": "-91.0"
                  },
                  "stock_on_hand": "-91.0",
                  "taxable": true,
                  "upc": null,
                  "vendor_code": null,
                  "wholesale_price": "22.5"
              }
          ]
      }

####   Retrieve a specific variant

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/variants/{VARIANT_ID}*

##### Sample Response

      {
          "images": [],
          "variant": {
              "cost_price": "15.0",
              "description": null,
              "id": 54725,
              "image_ids": [],
              "is_online": false,
              "keep_selling": false,
              "last_cost_price": null,
              "manage_stock": true,
              "max_online": null,
              "moving_average_cost": "0",
              "name": "Small",
              "online_id": null,
              "opt1": "White",
              "opt2": "Small",
              "opt3": null,
              "position": 1,
              "product_id": 21824,
              "reorder_point": null,
              "retail_price": "90.0",
              "sku": "DCP022-S",
              "status": "active",
              "stock_levels": {
                  "159": "-91.0"
              },
              "stock_on_hand": "-91.0",
              "taxable": true,
              "upc": null,
              "vendor_code": null,
              "wholesale_price": "22.5"
          }
      }

####   Create a new variant

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/variants/*

##### Sample Response

      {
          "images": [],
          "variant": {
              "cost_price": "15.0",
              "description": null,
              "id": 54725,
              "image_ids": [],
              "is_online": false,
              "keep_selling": false,
              "last_cost_price": null,
              "manage_stock": true,
              "max_online": null,
              "moving_average_cost": "0",
              "name": "Small",
              "online_id": null,
              "opt1": "White",
              "opt2": "Small",
              "opt3": null,
              "position": 1,
              "product_id": 21824,
              "reorder_point": null,
              "retail_price": "90.0",
              "sku": "DCP022-S",
              "status": "active",
              "stock_levels": {
                  "159": "-91.0"
              },
              "stock_on_hand": "-91.0",
              "taxable": true,
              "upc": null,
              "vendor_code": null,
              "wholesale_price": "22.5"
          }
      }


####   Update a variant

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/variants/{VARIANT_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

####   Delete a variant

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/variants/{VARIANT_ID}*

###### Return:
      Returns 204 status when the account gets updated successfully. 

