---
layout: post
category: api
---
  This is an object representing a fulfillment.

Attribute                | Type          | Description
------------------------ | ------------- | ------------
**id**                   | Integer       | A unique identifier for the address       
**order_id**             | Integer       | The company id where the address belongs.
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
      Returns 204 status when the fulfillment gets updated successfully. 
