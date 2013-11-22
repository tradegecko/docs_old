---
layout: post
category: api
---

This is an object representing a purchase order line item.

Attribute                      | Type          | Description                                         
------------------------------ | ------------- | ------------                                        
**id**                         | Integer       |  A unique identifier for the purchase order line item             
**purchase_order_id**          | Integer       |  ID of the parent purchase order                     
**variant_id**                 | Integer       |             
**procurement_id**             | Integer       |  
**quantity**                   | String        |                               
**position**                   | Integer       |                               
**tax_rate**                   | String        |                               
**price**                      | String        |                               
**label**                      | String        |                               
**freeform**                   | Boolean       |                               
**base_price**                 | String        |                               
**extra_cost_value**           | String        |                               
**image_url**                  | String        |                               


####   Retrieve a specific purchase order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/purchase_order_line_items/{PURCHASE_ORDER_LINE_ITEM_ID}*

##### Sample Response

      {
          purchase_order_line_item: {
              id: 6887,
              purchase_order_id: 2017,
              variant_id: 317068,
              procurement_id: 1439,
              quantity: "2.0",
              position: 0,
              tax_rate: "6.0",
              price: "20.0",
              label: null,
              freeform: false,
              base_price: "20.0",
              extra_cost_value: "12.5",
              image_url: null
          }
      }

####   Create a new purchase order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/purchase_order_line_item/*

##### Sample Response

      {
          purchase_order_line_item: {
              id: 6887,
              purchase_order_id: 2017,
              variant_id: 317068,
              procurement_id: 1439,
              quantity: "2.0",
              position: 0,
              tax_rate: "6.0",
              price: "20.0",
              label: null,
              freeform: false,
              base_price: "20.0",
              extra_cost_value: "12.5",
              image_url: null
          }
      }


####   Update a purchase order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/purchase_order_line_items/{PURCHASE_ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the purchase order line item gets updated successfully. 

####   Delete a purchase order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/purchase_order_line_items/{PURCHASE ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the purchase order line item gets deleted successfully. 
