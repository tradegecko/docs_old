---
layout: post
category: api
---
  This is an object representing a fulfillment.

Attribute                      | Type          | Description
------------------------------ | ------------- | ------------
**id**                         | Integer       | A unique identifier for the address       
**order_id**                   | Integer       | The company id where the address belongs.
**status**                     | String        |                                          
**shipped_at**                 | String        |                                         
**received_at**                | String        |                                          
**packed_at**                  | String        |                                          
**delivery_type**              | String        | Could be 'Courier' or 'Pickup'           
**tracking_number**            | String        |                                          
**tracking_url**               | String        |                                          
**tracking_company**           | String        |                                          
**created_at**                 | String        |                                          
**updated_at**                 | String        |                                          
**fulfillment_line_item_ids**  | Array         |                                          
**shipping_address_id**        | Integer       |                                          
**billing_address_id**         | Integer       |                                          
**exchange_rate**              | String        |                                          
**receipt**                    | Hash          |                                          
**xero**                       | String        |                                          
**notes**                      | String        |                                          

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
                      id: 592,
                      order_id: 830,
                      shipping_address_id: 3,
                      billing_address_id: 241,
                      status: "fulfilled",
                      exchange_rate: "1.0",
                      packed_at: "2013-01-18",
                      shipped_at: "2013-01-17T11:50:08Z",
                      received_at: "2013-01-17T00:00:00Z",
                      delivery_type: "Pickup",
                      tracking_number: "1234",
                      notes: "Thank you for your purchase",
                      tracking_url: null,
                      tracking_company: null,
                      receipt: { },
                      updated_at: "2013-10-07T05:03:58Z",
                      xero: null,
                      fulfillment_line_item_ids: [ 1279, 1278 ]
                  },
                  {
                      id: 579,
                      order_id: 751,
                      shipping_address_id: 103,
                      billing_address_id: 103,
                      status: "fulfilled",
                      exchange_rate: "1.0",
                      packed_at: "2013-01-18",
                      shipped_at: "2013-01-08T00:00:00Z",
                      received_at: null,
                      delivery_type: "Courier",
                      tracking_number: "6565",
                      notes: "Thank you for your purchase",
                      tracking_url: null,
                      tracking_company: null,
                      receipt: { },
                      updated_at: "2013-10-07T05:03:58Z",
                      xero: null,
                      fulfillment_line_item_ids: [ 1196, 1195 ]
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
          fulfillment_line_items: [
              {
                  id: 30630,
                  fulfillment_id: 16140,
                  order_line_item_id: 64686,
                  quantity: "1.0",
                  base_price: "24.0"
              }
          ],
          fulfillment: {
              id: 16140,
              order_id: 19513,
              shipping_address_id: null,
              billing_address_id: null,
              status: "fulfilled",
              exchange_rate: "1.0",
              packed_at: "2013-08-05",
              shipped_at: "2013-08-05T07:56:05Z",
              received_at: null,
              delivery_type: "Courier",
              tracking_number: null,
              notes: null,
              tracking_url: null,
              tracking_company: null,
              receipt: { },
              updated_at: "2013-10-07T05:05:58Z",
              xero: "d4656764-8af5-4d49-88cf-6a6a90bd59ef",
              fulfillment_line_item_ids: [ 30630 ]
          }
      }

#### Create a new fulfillment

Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/fulfillments/*


##### Sample response

      {
          fulfillment_line_items: [
              {
                  id: 30630,
                  fulfillment_id: 16140,
                  order_line_item_id: 64686,
                  quantity: "1.0",
                  base_price: "24.0"
              }
          ],
          fulfillment: {
              id: 16140,
              order_id: 19513,
              shipping_address_id: null,
              billing_address_id: null,
              status: "fulfilled",
              exchange_rate: "1.0",
              packed_at: "2013-08-05",
              shipped_at: "2013-08-05T07:56:05Z",
              received_at: null,
              delivery_type: "Courier",
              tracking_number: null,
              notes: null,
              tracking_url: null,
              tracking_company: null,
              receipt: { },
              updated_at: "2013-10-07T05:05:58Z",
              xero: "d4656764-8af5-4d49-88cf-6a6a90bd59ef",
              fulfillment_line_item_ids: [ 30630 ]
          }
      }

#### Update a fulfillment
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/fulfillments/{FULFILLMENT_ID}*


##### Sample response

      {
          fulfillment_line_items: [
              {
                  id: 30630,
                  fulfillment_id: 16140,
                  order_line_item_id: 64686,
                  quantity: "1.0",
                  base_price: "24.0"
              }
          ],
          fulfillment: {
              id: 16140,
              order_id: 19513,
              shipping_address_id: null,
              billing_address_id: null,
              status: "fulfilled",
              exchange_rate: "1.0",
              packed_at: "2013-08-05",
              shipped_at: "2013-08-05T07:56:05Z",
              received_at: null,
              delivery_type: "Courier",
              tracking_number: null,
              notes: null,
              tracking_url: null,
              tracking_company: null,
              receipt: { },
              updated_at: "2013-10-07T05:05:58Z",
              xero: "d4656764-8af5-4d49-88cf-6a6a90bd59ef",
              fulfillment_line_item_ids: [ 30630 ]
          }
      }


####   Delete a fulfillment

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/fulfillments/{FULFILLMENT_ID}*

###### Return:
      Returns 204 status when the fulfillment gets deleted successfully. 
