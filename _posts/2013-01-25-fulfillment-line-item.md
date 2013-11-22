---
layout: post
category: api
---

This is an object representing a fulfillment line item.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the fulfillment line item             
**fulfillment_id**             | Integer       |  ID of the parent fulfillment id                            
**order_line_item_id**         | Integer       |  ID of the parent order line item               
**quantity**                   | String        |  Quantity of stocks fulfilled
**base_price**                 | String        |  Base price of the variant                                


####   Retrieve a specific fulfillment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/fulfillment_line_items/{FULFILLMENT_LINE_ITEM_ID}*

##### Sample Response

      {
          fulfillment_line_item: {
              id: 30630,
              fulfillment_id: 16140,
              order_line_item_id: 64686,
              quantity: "1.0",
              base_price: "24.0"
          }
      }

####   Create a new fulfillment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/fulfillment_line_item/*

##### Sample Response

      {
          fulfillment_line_item: {
              id: 30630,
              fulfillment_id: 16140,
              order_line_item_id: 64686,
              quantity: "1.0",
              base_price: "24.0"
          }
      }


####   Update a fulfillment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/fulfillment_line_items/{FULFILLMENT_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the fulfillment line item gets updated successfully. 

####   Delete a fulfillment line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/fulfillment_line_items/{FULFILLMENT_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the fulfillment line item gets deleted successfully. 
