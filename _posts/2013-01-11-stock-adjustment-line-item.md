---
layout: post
category: api
---

This is an object representing a stock adjustment line item.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the stock adjustment line item             
**stock_adjustment_id**        | Integer       |  ID of the parent stock adjustment                           
**variant_id**                 | Integer       |            
**quantity**                   | String        |
**position**                   | Integer       |                               


####   Retrieve a specific stock adjustment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/stock_adjustment_line_items/{STOCK_ADJUSTMENT_LINE_ITEM_ID}*

##### Sample Response

      {
          stock_adjustment_line_item: {
                id: 19522,
                stock_adjustment_id: 3530,
                variant_id: 443492,
                quantity: "-40.0",
                position: 0
          }
      }

####   Create a new stock adjustment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/stock_adjustment_line_item/*

##### Sample Response

      {
          stock_adjustment_line_item: {
                id: 19522,
                stock_adjustment_id: 3530,
                variant_id: 443492,
                quantity: "-40.0",
                position: 0
          }
      }

####   Update a stock adjustment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/stock_adjustment_line_items/{STOCK_ADJUSTMENT_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the stock adjustment line item gets updated successfully. 

####   Delete a stock adjustment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/stock_adjustment_line_items/{STOCK_ADJUSTMENT_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the stock adjustment line item gets deleted successfully. 
