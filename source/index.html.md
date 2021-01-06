---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for an API Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Channel Signal API! You can use our API to access Channel Signal API endpoints, which can get information on various reports, products, reviews and scores.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
```

```shell
curl "https://api.channelsignal.com/v1/authorize"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
```

> The above command returns JSON structured like this:

```json
{
  "authorized": true,
  "message": "Your API key is valid and active."
}
```

Channel Signal uses API keys to allow access to the API. You can [request an API key here](mailto:support@channelsignal.com?subject=API Key Request).

The API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`authentication-token: your-api-key`

<aside class="notice">
You must replace <code>your-api-key</code> with your provided API key.
</aside>

# Reports

## Get List of Reports

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.reports.get
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.reports.get()
```

```shell
curl "https://api.channelsignal.com/v1/reports"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let reports = api.reports.get();
```

> The above command returns JSON structured like this:

```json
{
  "total_results": 3,
  "reports": [
    {
      "id": "4333f847-1b1d-4e9a-b2d2-7d8e93ccc0f2",
      "name":  "Brand Report"
    },
    {
      "id": "ed897deb-d67c-450b-bea7-595a774c6a8a",
      "name":  "Monthly Report"
    },
    {
      "id": "eb023b28-425c-491a-b36b-ea9fce27bff4",
      "name":  "Annual Report"
    }
  ]
}
```
This endpoint retrieves a list of available reports.

<aside class="warning">The results returned from this endpoint are the available values that can be used in the next request.</aside>

### HTTP Request

`GET https://api.channelsignal.com/v1/reports`

## Get Report Attributes

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.reports.get(<ID>)
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.reports.get(<ID>)
```

```shell
curl "https://api.channelsignal.com/v1/reports/<ID>"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let reports = api.reports.get(<ID>);
```

> The above command returns JSON structured like this:

```json
{
  "name": "Monthly Report",
  "brands": [
      "Brand 1",
      "Brand 2",
      "Brand 3"
  ],
  "categories": [
      "Category 1",
      "Category 2",
      "Category 3",
      "Category 4",
      "Category 5"
  ],
  "sentiment": [
      "very positive",
      "positive",
      "neutral",
      "negative",
      "very negative"
  ],
  "sources": [
      "Amazon",
      "CVS",
      "Target",
      "Walmart"
  ]
}
```

This endpoint retrieves the available parameter values for a specific report.

<aside class="warning">The results returned from this endpoint are the available values that can be used in the filter parameters for the other endpoints.</aside>

<!--<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>-->

### HTTP Request

`GET https://api.channelsignal.com/v1/reports/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the report to retrieve

# Pricing
## Get List of Products with Price

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.pricing.get
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.pricing.get()
```

```shell
curl "https://api.channelsignal.com/v1/pricing"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let pricing = api.reports.get();
```

> The above command returns JSON structured like this:

```json
{
  "current_page": 1,
  "total_pages": 4,
  "total_results": 100,
  "products": [
    {
      "product_id": "07883fdf-c293-411a-9ce9-8d1912b9f8f6",
      "internal_id": "GS455",
      "product": "Onyx Folding Lamp - Lamps - ACME",
      "brand": "ACME",
      "category": "Lamps",
      "last_updated_date": "2020-07-01",
      "pricing": [
        "Amazon": [
          {
            "avg": "96.49",
            "min": "62.99",
            "max": "129.99",
            "last_updated_date": "2020-10-05"
          },
          "B004RUH9ZS":
          {
            "model": "OFL-2345",
            "upc": "1234657890",
            "image_url": "https://example.com/image.jpg",
            "avg": "97.49",
            "min": "64.99",
            "max": "129.99",
            "colors": [
                "Black",
                "Caribou",
                "Feather",
                "Quartz",
                "White",
                "Wild Grape"
            ],
            "attributes":
            {
              // ... this product's external attributes e.g.,
              "Style ID": "GS455",
              "Materialization": "G4203L1",
              "Materialization Number": "G4203L1020",
              "Season": "2019-2 Fall I",
              "Retail ID": "208660"
            },
            "last_updated_date": "2020-10-05"
          },
          "B00R1FLYK2":
          {
            "model": "OFL-2345",
            "upc": "1234657890",
            "image_url": "https://example.com/image.jpg",
            "price": "74.99",
            "colors": "",
            "attributes":
            {
              // ... this product's external attributes
            },
            "last_updated_date": "2020-09-20"
          },
          "B00T7MMCDU":
          {
            "model": "OFL-2345",
            "upc": "1234657890",
            "image_url": "https://example.com/image.jpg",
            "avg": "88.99",
            "min": "62.99",
            "max": "114.99",
            "colors": "",
            "attributes":
            {
              // ... this product's external attributes
            },
            "last_updated_date": "2020-10-01"
          }
        ],
        "CVS":
        {
          "model": "OFL-2345",
          "upc": "1234657890",
          "image_url": "https://example.com/image.jpg",
          "price": "59.99",
          "colors": "",
          "attributes":
          {
            // ... this product's external attributes
          },
          "last_updated_date": "2020-08-10"
        }
        "Target": 
        {
          "model": "OFL-2345",
          "upc": "1234657890",
          "image_url": "https://example.com/image.jpg",
          "price": "52.99",
          "colors": [
              "Sage Green"
          ],
          "attributes":
          {
            // ... this product's external attributes
          },
          "last_updated_date": "2020-10-01"
        }
        "Walmart":
        {
          "model": "OFL-2345",
          "upc": "1234657890",
          "image_url": "https://example.com/image.jpg",
          "price": "59.99",
          "colors": [
              "Black",
              "Coral Pink",
              "Gold Yellow Microfiber",
              "Grey"
          ],
          "attributes":
          {
            // ... this product's external attributes
          },
          "last_updated_date": "2020-10-01"
        }
      ]
    }
  ]
}
```

This endpoint retrieves a list of products with pricing data from a specified report. Products are available through the API as soon as they appear on the source site. As a result they may not always contain review data. Price contains the most recent known price from each source.

### HTTP Request

`GET https://api.channelsignal.com/v1/pricing`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
report_id | true | | The ID of the report to return product results from.
internal_id | false | | The internal third party ID of the product. Multiple id's should be passed as comma separated string.
last_updated_start_date | false | | Start date when Channel Signal received a changed pricing. In the format YYYY-MM-DD.
last_updated_end_date | false | | End date when Channel Signal received a changed pricing. In the format YYYY-MM-DD.
brands | false | | Brands to return results for. Separate each value by a comma. The default is all brands.
sources | false | | Sources to return results for. Separate each value by a comma. The default is all sources.
page | false | 1 | The starting page offset to return results from.
per_page | false | 25 | The total number of results per page. The maximum value is 100.

<aside class="success">
Remember — The available values to use in the parameters for brands, sources and sentiment come from querying the reports endpoint for a specified report using it's ID.
</aside>

# Products
## Get List of Products

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.products.get
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.products.get()
```

```shell
curl "https://api.channelsignal.com/v1/products"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let products = api.reports.get();
```

> The above command returns JSON structured like this:

```json
{
  "current_page": 1,
  "total_pages": 4,
  "total_results": 100,
  "products": [
    {
      "product_id": "07883fdf-c293-411a-9ce9-8d1912b9f8f6",
      "product": "Onyx Folding Lamp - Lamps - ACME",
      "brand": "ACME",
      "category": "Lamps",
      "last_updated_date": "2020-07-01",
      "review_start_date": "2019-05-01",
      "review_end_date": "2019-07-01",
      "total_positive": 264,
      "positive_percent": "91%",
      "total_non_positive": 27,
      "non_positive_percent": "9%",
      "very_positive": 235,
      "positive": 29,
      "neutral": 7,
      "negative": 4,
      "very_negative": 16,
      "star_average": 4.59,
      "total_reviews": 291
    }
  ]
}
```

This endpoint retrieves a list of products from a specified report that contain reviews. 
### HTTP Request

`GET https://api.channelsignal.com/v1/products`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
report_id | true | | The ID of the report to return product results from.
created_start_date | true | | Start date when Channel Signal received the review. In the format YYYY-MM-DD.
created_end_date | true | | End date when Channel Signal received the review. In the format YYYY-MM-DD.
review_start_date | true | | Start date when the user created the review. In the format YYYY-MM-DD.
review_end_date | true | | End date when the user created the review. In the format YYYY-MM-DD.
brands | false | | Brands to return results for. Separate each value by a comma. The default is all brands.
categories | false | | Categories to return results for. Separate each value by a comma. The default is all categories.
sources | false | | Sources to return results for. Separate each value by a comma. The default is all sources.
sentiment | false | | Sentiment types to return results for. Separate each value by a comma. The default is all sentiment types.
filter_duplicates | false | false | Remove duplicate reviews from different sources.
page | false | 1 | The starting page offset to return results from.
per_page | false | 25 | The total number of results per page. The maximum value is 500.

<aside class="success">
Remember — The available values to use in the parameters for brands, categories, sources and sentiment come from querying the reports endpoint for a specified report using it's ID.
</aside>

# Reviews
## Get List of Reviews

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.reviews.get
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.reviews.get()
```

```shell
curl "https://api.channelsignal.com/v1/reviews"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let reviews = api.reviews.get();
```

> The above command returns JSON structured like this:

```json
{
  "current_page": 1,
  "total_pages": 4,
  "total_results": 100,
  "reviews": [
    {
        "review_id": 124993721,
        "external_product_id": "7624939",
        "created_date_timestamp": 1556715600,
        "created_date": "2019-05-01 06:00:00",
        "review_date_timestamp": 1556715600,
        "review_date": "2019-05-01 06:00:00",
        "source": "Amazon",
        "product_id": "07883fdf-c293-411a-9ce9-8d1912b9f8f6",
        "product": "Onyx Folding Flamp - Lamps - ACME",
        "brand": "ACME",
        "author": "Maria R.",
        "verified": "yes",
        "rating": "5",
        "rating_text": "very positive",
        "review_title": "Highly Recommended",
        "review": "This is the best lamp ever!!",
        "category": "Lamps",
        "url": "https://www.amazon.com/ACME-Onyx-Folding-Lamp/dp/B00XC5KN64",
        "image_url": "https://cdn.shopify.com/s/files/1/2170/8465/products/ACME-Onyx-Folding-Lamp.jpg?v=1571609581",
        "asin": "B00XC5KN64",
        "price": "39.99",
        "size": "N/A",
        "color": "Black",
        "model": "TT-DL10",
        "upc": "1234567890",
        "review_tags": "folding"
    }
  ]
}

```

This endpoint retrieves a list of reviews from a specified report. The external_product_id is the product ID retrieved from the source.

### HTTP Request

`GET https://api.channelsignal.com/v1/reviews`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
report_id | true | | The ID of the report to return review results from.
created_start_date | true | | Start date when Channel Signal received the review. In the format YYYY-MM-DD.
created_end_date | true | | End date when Channel Signal received the review. In the format YYYY-MM-DD.
review_start_date | true | | Start date when the user created the review. In the format YYYY-MM-DD.
review_end_date | true | | End date when the user created the review. In the format YYYY-MM-DD.
brands | false | | Brands to return results for. Separate each value by a comma. The default is all brands.
categories | false | | Categories to return results for. Separate each value by a comma. The default is all categories.
product_ids | false | | Products to return results for. Separate each value by a comma. The default is all products.
sources | false | | Sources to return results for. Separate each value by a comma. The default is all sources.
sentiment | false | | Sentiment types to return results for. Separate each value by a comma. The default is all sentiment types.
filter_duplicates | false | false | Remove duplicate reviews from different sources.
page | false | 1 | The starting page offset to return results from.
per_page | false | 25 | The total number of results per page. The maximum value is 500.

<aside class="success">
Remember — The available values to use in the parameters for brands, categories, sources and sentiment come from querying the reports endpoint for a specified report using it's ID.
</aside>


# CS Scores
## Get List of Product Scores

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.scores.get
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.scores.get()
```

```shell
curl "https://api.channelsignal.com/v1/scores"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let scores = api.scores.get();
```

> The above command returns JSON structured like this:

```json
{
  "current_page": 1,
  "total_pages": 4,
  "total_results": 1,
  "products": [
    {
      "product_id": "07883fdf-c293-411a-9ce9-8d1912b9f8f6",
      "product": "Onyx Folding Lamp - Lamps - ACME",
      "brand": "ACME",
      "very_positive": 1071,
      "positive": 130,
      "neutral": 54,
      "negative": 35,
      "very_negative": 69,
      "star_average": 4.54,
      "drivers": [
          {
              "name": "Competitive Brand Mentions",
              "star_average": 4.0,
              "total_reviews": 1
          },
          {
              "name": "Pivot Language",
              "star_average": 4.36,
              "total_reviews": 75
          },
          {
              "name": "Price / Value",
              "star_average": 4.33,
              "total_reviews": 129
          },
          {
              "name": "Quality / Satisfaction",
              "star_average": 4.36,
              "total_reviews": 235
          },
          {
              "name": "Reliable / Usage",
              "star_average": 4.53,
              "total_reviews": 173
          },
          {
              "name": "Safety",
              "star_average": 0.0,
              "total_reviews": 0
          }
      ],
      "total_reviews": 1359
    }
  ]
}
```

This endpoint retrieves scores for a list of products for a specified report.

### HTTP Request

`GET https://api.channelsignal.com/v1/scores`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
report_id | true | | The ID of the report to return score results from.
start_date | false | Today's Date - 12 months | Start date in the format YYYY-MM-DD.
end_date | false | Today's Date | End date in the format YYYY-MM-DD.
brands | false | | Brands to return results for. Separate each value by a comma. The default is all brands.
categories | false | | Categories to return results for. Separate each value by a comma. The default is all categories.
sources | false | | Sources to return results for. Separate each value by a comma. The default is all sources.
filter_duplicates | false | false | Remove duplicate reviews from different sources.
page | false | 1 | The starting page offset to return results from.
per_page | false | 25 | The total number of results per page. The maximum value is 500.

<aside class="success">
Remember — The available values to use in the parameters for brands, categories, sources and sentiment come from querying the reports endpoint for a specified report using it's ID.
</aside>

## Get Product Scores

```ruby
require 'channelsignal'

api = ChannelSignal::APIClient.authorize!('your-api-key')
api.scores.get(<ID>)
```

```python
import channelsignal

api = channelsignal.authorize('your-api-key')
api.scores.get(<ID>)
```

```shell
curl "https://api.channelsignal.com/v1/scores/<ID>"
  -H "Authorization: Token token=your-api-key"
```

```javascript
const channelsignal = require('channelsignal');

let api = channelsignal.authorize('your-api-key');
let scores = api.scores.get(<ID>);
```

> The above command returns JSON structured like this:

```json
{
  "product_id": "07883fdf-c293-411a-9ce9-8d1912b9f8f6",
  "product": "Onyx Folding Lamp - Lamps - ACME",
  "brand": "ACME",
  "very_positive": 1071,
  "positive": 130,
  "neutral": 54,
  "negative": 35,
  "very_negative": 69,
  "star_average": 4.54,
  "drivers": [
      {
          "name": "Competitive Brand Mentions",
          "star_average": 4.0,
          "total_reviews": 1
      },
      {
          "name": "Pivot Language",
          "star_average": 4.36,
          "total_reviews": 75
      },
      {
          "name": "Price / Value",
          "star_average": 4.33,
          "total_reviews": 129
      },
      {
          "name": "Quality / Satisfaction",
          "star_average": 4.36,
          "total_reviews": 235
      },
      {
          "name": "Reliable / Usage",
          "star_average": 4.53,
          "total_reviews": 173
      },
      {
          "name": "Safety",
          "star_average": 0.0,
          "total_reviews": 0
      }
  ],
  "total_reviews": 1359
}
```

This endpoint retrieves scores for an individual product.

### HTTP Request

`GET https://api.channelsignal.com/v1/scores/<ID>`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
ID | true | | The ID of the product to retrieve
start_date | false | Today's Date - 12 months | Start date in the format YYYY-MM-DD.
end_date | false | Today's Date | End date in the format YYYY-MM-DD.
sources | false | | Sources to return results for. Separate each value by a comma. The default is all sources.
filter_duplicates | false | false | Remove duplicate reviews from different sources.

# Rate Limits

The API has a rate limit of 5 requests over a 15 second period, which averages to roughly 20 requests/minute. This should be sufficient for most use cases. In the event you are running into any issues with these limits, please [let us know](mailto:support@channelsignal.com?subject=API Rate Limits) and we would be happy to review.
