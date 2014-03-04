---
layout: post
category: api
---

This is an object representing a invoice line item.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the invoice line item             
**invoice_id**                 | Integer       |  ID of the parent invoice id                            
**order_line_item_id**         | Integer       |  ID of the parent order line item               
**quantity**                   | String        |  Quantity of stocks invoiced
**position**                   | Integer       |                               


####   Retrieve a specific invoice line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/invoice_line_items/{INVOICE_LINE_ITEM_ID}*

##### Sample Response

      {
          invoice_line_item: {
              id: 30630,
              invoice_id: 16140,
              order_line_item_id: 64686,
              quantity: "1.0",
              position: 1
          }
      }

####   Create a new invoice line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/invoice_line_items/*

##### Sample Response

      {
          invoice_line_item: {
              id: 30630,
              invoice_id: 16140,
              order_line_item_id: 64686,
              quantity: "1.0",
              position: 1
          }
      }


####   Update a invoice line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/invoice_line_items/{INVOICE_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the invoice line item gets updated successfully. 

####   Delete a invoice line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/invoice_line_items/{INVOICE_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the invoice line item gets deleted successfully. 
