---
layout: post
category: api
---
  This is an object representing a stock transfer.

Attribute                        | Type          | Description
-------------------------------- | ------------- | ------------
**id**                           | Integer       | A unique identifier for the stock transfer
**adjustment_number**            | String        |
**status**                       | String        |
**created_at**                   | String        |
**updated_at**                   | String        |
**transacted_at_at**             | String        |
**notes**                        | String        |
**source_location_id**           | Integer       |
**source_destination_id**        | Integer       |
**cached_quantity**              | String        |
**stock_transfer_line_item_ids** | Array         |

####   Retrieve list of stock transfers

###### Request:
Method     | Request URL
-----------| -------------
**GET**    | *https://api.tradegecko.com/stock_transfers/*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>"
      https://api.tradegecko.com/stock_transfers

##### Sample response

      {
            stock_transfers: [
                  {
                        id: 1,
                        adjustment_number: "ST0001",
                        status: "received",
                        created_at: "2013-05-27T08:51:20Z",
                        updated_at: "2013-05-28T08:20:59Z",
                        transacted_at: "2013-05-28T08:20:59Z",
                        received_at: "2013-05-28T08:20:59Z",
                        notes: null,
                        source_location_id: 18,
                        destination_location_id: 160,
                        cached_quantity: "10.0",
                        stock_transfer_line_item_ids: [ 1 ]
                  },
                  {
                        id: 2,
                        adjustment_number: "ST0002",
                        status: "received",
                        created_at: "2013-05-28T09:30:13Z",
                        updated_at: "2013-05-30T04:37:30Z",
                        transacted_at: "2013-05-30T04:37:30Z",
                        received_at: "2013-05-30T04:37:30Z",
                        notes: null,
                        source_location_id: 159,
                        destination_location_id: 160,
                        cached_quantity: "10.0",
                        stock_transfer_line_item_ids: [ 2 ]
                  }
            ]
      }

####  Retrieve a specific stock transfer item

###### Request:
Method     | Request URL
-----------| -------------
**GET**    | *https://api.tradegecko.com/stock_transfers/{STOCK_TRANSFER_ID}*

##### Sample Request

      curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>"
      https://api.tradegecko.com/stock_transfers/1

##### Sample response

      {
            stock_transfer: {
                id: 1,
                adjustment_number: "ST00019",
                status: "received",
                created_at: "2013-09-26T04:55:22Z",
                updated_at: "2013-09-26T04:57:10Z",
                transacted_at: "2013-09-26T04:57:10Z",
                received_at: "2013-09-26T04:57:10Z",
                notes: null,
                source_location_id: 160,
                destination_location_id: 3723,
                cached_quantity: "10.0",
                stock_transfer_line_item_ids: [ 5306 ]
            }
      }

#### Create a new stock transfer

Method     | Request URL
-----------| -------------
**POST**   | *https://api.tradegecko.com/stock_transfers/*


##### Sample response

      {
            stock_transfer: {
                id: 540,
                adjustment_number: "ST00019",
                status: "received",
                created_at: "2013-09-26T04:55:22Z",
                updated_at: "2013-09-26T04:57:10Z",
                transacted_at: "2013-09-26T04:57:10Z",
                received_at: "2013-09-26T04:57:10Z",
                notes: null,
                source_location_id: 160,
                destination_location_id: 3723,
                cached_quantity: "10.0",
                stock_transfer_line_item_ids: [ 5306 ]
            }
      }

#### Update a stock transfer
Method     | Request URL
-----------| -------------
**PUT**    | *https://api.tradegecko.com/stock_transfers/{STOCK_TRANSFER_ID}*


##### Sample response

      {
            stock_transfer: {
                id: 540,
                adjustment_number: "ST00019",
                status: "received",
                created_at: "2013-09-26T04:55:22Z",
                updated_at: "2013-09-26T04:57:10Z",
                transacted_at: "2013-09-26T04:57:10Z",
                received_at: "2013-09-26T04:57:10Z",
                notes: null,
                source_location_id: 160,
                destination_location_id: 3723,
                cached_quantity: "10.0",
                stock_transfer_line_item_ids: [ 5306 ]
            }
      }


####   Delete a stock transfer

######     Request:
Method     | Request URL
-----------| -------------
**DELETE** | *https://api.tradegecko.com/stock_transfers/{STOCK_TRANSFER_ID}*

###### Return:
      Returns 204 status when the stock transfer gets deleted successfully.
