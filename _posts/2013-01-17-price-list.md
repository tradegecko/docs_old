---
layout: post
category: api
---

This is an object representing a price list.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the price list            
**code**                       | String        |                           
**name**                       | String        |  Name of the price list              
**is_cost**                    | String        |  Price list would be available in creating purchase orders if set to true
**is_default**                 | String        |
**currency_id**                | String        |                 
**currency_symbol**            | String        |                 
**currency_iso**               | String        |                 
**position**                   | Integer       |                 


####   Retrieve list of price lists

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/price_lists/*

##### Sample Response

      {
         price_lists: [
              {
                  id: "buy",
                  code: "BUY",
                  name: "Buy",
                  is_cost: true,
                  is_default: true,
                  currency_id: 4,
                  currency_symbol: "$",
                  currency_iso: "SGD"
              },
              {
                  id: "wholesale",
                  code: "WHOLE",
                  name: "Wholesale",
                  is_cost: false,
                  is_default: true,
                  currency_id: 4,
                  currency_symbol: "$",
                  currency_iso: "SGD"
              },
              {
                  id: "retail",
                  code: "RETAIL",
                  name: "Retail",
                  is_cost: false,
                  is_default: true,
                  currency_id: 4,
                  currency_symbol: "$",
                  currency_iso: "SGD"
              },
              {
                  id: 736,
                  currency_id: 1899,
                  currency_symbol: "€",
                  currency_iso: "EUR",
                  code: "EUR",
                  name: "Buy - EURO",
                  is_cost: true,
                  is_default: null,
                  position: 8
              }
         ]
      }

####   Retrieve a specific price list

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/price_lists/{PRICE_LIST_ID}*

##### Sample Response

      {
          price_list: {
              id: 12,
              code: "AUS",
              name: "AUS",
              is_cost: true,
              is_default: true,
              currency_id: 4,
              currency_symbol: "$",
              currency_iso: "SGD"
          }
      }

####   Create a new price list

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/price_lists/*

##### Sample Response

      {
          price_list: {
              id: 12,
              code: "AUS",
              name: "AUS",
              is_cost: true,
              is_default: true,
              currency_id: 4,
              currency_symbol: "$",
              currency_iso: "SGD"
          }
      }


####   Update a price list

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/price_lists/{PRICE_LIST_ID}*

###### Return:
      Returns 204 status when the price list gets updated successfully. 


####   Delete a price list

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/price_lists/{PRICE_LIST_ID}*

###### Return:
      Returns 204 status when the price list gets deleted successfully. 
