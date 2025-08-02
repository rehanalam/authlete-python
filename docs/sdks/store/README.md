# Store
(*store*)

## Overview

Access to Petstore orders

Find out more about our store
<http://swagger.io>

### Available Operations

* [get_inventory](#get_inventory) - Returns pet inventories by status
* [place_order](#place_order) - Place an order for a pet
* [get_order_by_id](#get_order_by_id) - Find purchase order by ID
* [delete_order](#delete_order) - Delete purchase order by ID

## get_inventory

Returns a map of status codes to quantities

### Example Usage

<!-- UsageSnippet language="python" operationID="getInventory" method="get" path="/store/inventory" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.store.get_inventory()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, int]](../../models/.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## place_order

Place a new order in the store

### Example Usage

<!-- UsageSnippet language="python" operationID="placeOrder" method="post" path="/store/order" -->
```python
from authlete import Authlete, models
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.store.place_order(request={
        "id": 10,
        "pet_id": 198772,
        "quantity": 7,
        "status": models.OrderStatus.APPROVED,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.Order](../../models/order.md)                               | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Order](../../models/order.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## get_order_by_id

For valid response try integer IDs with value <= 5 or > 10. Other values will generate exceptions.

### Example Usage

<!-- UsageSnippet language="python" operationID="getOrderById" method="get" path="/store/order/{orderId}" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.store.get_order_by_id(order_id=728529)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `order_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | ID of order that needs to be fetched                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Order](../../models/order.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## delete_order

For valid response try integer IDs with value < 1000. Anything above 1000 or nonintegers will generate API errors

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteOrder" method="delete" path="/store/order/{orderId}" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.store.delete_order(order_id=690575)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `order_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | ID of the order that needs to be deleted                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Order](../../models/order.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |