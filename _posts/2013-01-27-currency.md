---
layout: post
category: api
---

This is an object representing a currency.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the currency            
**iso**                        | String        |  Three-character currency code                            
**name**                       | String        |  Name of the currency               
**rate**                       | String        |  Exchange rate based on account's base currency    
**symbol**                     | String        |  Currency symbol
**separator**                  | String        |                 
**delimiter**                  | String        | 
**precision**                  | Integer       |                   
**format**                     | String        |                                                     


####   Retrieve list of currencies

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/currencies/*

##### Sample Response

      {
         currencies: [
              {
                  id: 1909,
                  iso: "MYR",
                  name: "Ringgit",
                  rate: "2.54317",
                  symbol: "RM",
                  separator: ".",
                  delimiter: ",",
                  precision: 2,
                  format: "%u%n"
              },
              {
                  id: 3056,
                  iso: "NZD",
                  name: "New Zealand",
                  rate: "0.95177",
                  symbol: "$",
                  separator: ".",
                  delimiter: ",",
                  precision: 2,
                  format: "%u%n"
              },
              {
                  id: 2007,
                  iso: "AUD",
                  name: "Australian Dollar",
                  rate: "0.85412",
                  symbol: "$",
                  separator: ".",
                  delimiter: ",",
                  precision: 2,
                  format: "%u%n"
              }
         ]
      }

####   Retrieve a specific currency

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/currencies/{CURRENCY_ID}*

##### Sample Response

      {
          currency: {
              id: 3056,
              iso: "NZD",
              name: "New Zealand",
              rate: "0.95177",
              symbol: "$",
              separator: ".",
              delimiter: ",",
              precision: 2,
              format: "%u%n"
          }
      }

####   Create a new currency

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/currencies/*

##### Sample Response

      {
          currency: {
              id: 3056,
              iso: "NZD",
              name: "New Zealand",
              rate: "0.95177",
              symbol: "$",
              separator: ".",
              delimiter: ",",
              precision: 2,
              format: "%u%n"
          }
      }


####   Update a currency

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/currencies/{CURRENCY_ID}*

###### Return:
      Returns 204 status when the currency gets updated successfully. 
