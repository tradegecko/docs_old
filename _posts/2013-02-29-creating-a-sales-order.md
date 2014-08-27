---
layout: developer
category: developer
---
### Integrating with an e-commerce store

1. Create the Order

`POST /orders`

{% highlight json %}
{
  "order": {
    "company_id": 123,
    "shipping_address_id": 1001,
    "billing_address_id": 1001,
    "assignee_id": 1002,
    "currency_id": 124,
    "email": "hello@example.com",
    "status": "active",
    "tax_type": "inclusive",
    "issued_at": "21-02-2014",
    "source_url": "my-shop.example.com/orders/12345",
    "order_line_items": [
      { "variant_id": 14, "quantity": 1, "price": "12.40", "tax_type_id": 1 }
      { "variant_id": 15, "quantity": 2, "price": "40.90", "tax_type_id": 2 }
    ]
  }
}
{% endhighlight %}

2. Finalize the Order

`PUT /orders/[:order_id]`

{% highlight json %}
{
  "order": {
    "status": "finalized",
    "payment_status": "paid"
  }
}
{% endhighlight %}

3. Create a Package for Shipping

`POST /fulfillments/`

{% highlight json %}
{
  "fulfillment": {
    "order_id": 123,
    "shipping_address_id": 1001,
    "billing_address_id": 1001,
    "delivery_type": "Courier",
    "tracking_number": "ABC1234",
    "packed_at": "21-02-2014",
    "fulfillment_line_items": [
      { "order_line_item_id": 14, "quantity": 1 }
      { "order_line_item_id": 15, "quantity": 2 }
    ]
  }
}
{% endhighlight %}

4. Ship the package

`PUT /fulfillments/[:fulfillment_id]`

{% highlight json %}
{
  "fulfillment": {
    "status": "shipped"
  }
}
{% endhighlight %}

5. TradeGecko will automatically manage the Order's fulfillment and packed statuses
during the fulfillment processes
