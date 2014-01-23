---
layout: post
category: api
---

This is an object representing a payment term.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the payment term            
**name**                       | String        |  Name of the payment term              
**due_in_days**                | Integer       |                 
**status**                     | String        |                 


####   Retrieve list of payment terms

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/payment_terms/*

##### Sample Response

      {
         payment_terms: [
              {
                  id: 12,
                  name: "NET30",
                  due_in_days: 30,
                  status: "active"
              },
              {
                  id: 11,
                  name: "NET10",
                  due_in_days: 10,
                  status: "active"
              },
              {
                  id: 10,
                  name: "Cash on Delivery",
                  due_in_days: 0,
                  status: "active"
              }
         ]
      }

####   Retrieve a specific payment term

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/payment_terms/{PAYMENT_TERM_ID}*

##### Sample Response

      {
          payment_term: {
              id: 12,
              name: "NET30",
              due_in_days: 30,
              status: "active"
          }
      }

####   Create a new payment term

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/payment_terms/*

##### Sample Response

      {
          payment_term: {
              id: 12,
              name: "NET30",
              due_in_days: 30,
              status: "active"
          }
      }


####   Update a payment term

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/payment_terms/{PAYMENT_TERM_ID}*

###### Return:
      Returns 204 status when the payment term gets updated successfully. 

####   Delete a payment term

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE**    | *https://api.tradegecko.com/payment_terms/{PAYMENT_TERM_ID}*

###### Return:
      Returns 204 status when the payment term gets deleted successfully. 
