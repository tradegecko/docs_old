---
layout: post
category: api
---

This is an object representing a stock transfer line item.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the stock transfer line item             
**stock_transfer_id**          | Integer       |  ID of the parent stock transfer                           
**variant_id**                 | Integer       |            
**quantity**                   | String        |
**position**                   | Integer       |                               
**image_url**                  | String        |                               


####   Retrieve a specific stock transfer line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/stock_transfer_line_items/{STOCK_TRANSFER_LINE_ITEM_ID}*

##### Sample Response

      {
          stock_transfer_line_item: {
              id: 5306,
              stock_transfer_id: 540,
              variant_id: 431876,
              quantity: "10.0",
              position: 0,
              image_url: null
          }
      }

####   Create a new stock transfer line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/stock_transfer_line_item/*

##### Sample Response

      {
          stock_transfer_line_item: {
              id: 5306,
              stock_transfer_id: 540,
              variant_id: 431876,
              quantity: "10.0",
              position: 0,
              image_url: null
          }
      }

####   Update a stock transfer line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/stock_transfer_line_items/{STOCK_TRANSFER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the stock transfer line item gets updated successfully. 

####   Delete a stock transfer line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/stock_transfer_line_items/{STOCK_TRANSFER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the stock transfer line item gets deleted successfully. 
