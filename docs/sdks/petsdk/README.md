# PetSDK
(*pet*)

## Overview

Everything about your Pets

Find out more
<http://swagger.io>

### Available Operations

* [update_pet](#update_pet) - Update an existing pet
* [add_pet](#add_pet) - Add a new pet to the store
* [find_pets_by_status](#find_pets_by_status) - Finds Pets by status
* [find_pets_by_tags](#find_pets_by_tags) - Finds Pets by tags
* [get_pet_by_id](#get_pet_by_id) - Find pet by ID
* [delete_pet](#delete_pet) - Deletes a pet
* [upload_file](#upload_file) - uploads an image

## update_pet

Update an existing pet by Id

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.update_pet(name="doggie", photo_urls=[
        "<value 1>",
    ], id=10, category={
        "id": 1,
        "name": "Dogs",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | doggie                                                              |
| `photo_urls`                                                        | List[*str*]                                                         | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `id`                                                                | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 10                                                                  |
| `category`                                                          | [Optional[models.Category]](../../models/category.md)               | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `tags`                                                              | List[[models.Tag](../../models/tag.md)]                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `status`                                                            | [Optional[models.PetStatus]](../../models/petstatus.md)             | :heavy_minus_sign:                                                  | pet status in the store                                             |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Pet](../../models/pet.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## add_pet

Add a new pet to the store

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.add_pet(name="doggie", photo_urls=[
        "<value 1>",
        "<value 2>",
        "<value 3>",
    ], id=10, category={
        "id": 1,
        "name": "Dogs",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | doggie                                                              |
| `photo_urls`                                                        | List[*str*]                                                         | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `id`                                                                | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 10                                                                  |
| `category`                                                          | [Optional[models.Category]](../../models/category.md)               | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `tags`                                                              | List[[models.Tag](../../models/tag.md)]                             | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `status`                                                            | [Optional[models.PetStatus]](../../models/petstatus.md)             | :heavy_minus_sign:                                                  | pet status in the store                                             |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Pet](../../models/pet.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## find_pets_by_status

Multiple status values can be provided with comma separated strings

### Example Usage

```python
from authlete import Authlete, models
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.find_pets_by_status(status=models.FindPetsByStatusStatus.AVAILABLE)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `status`                                                                          | [Optional[models.FindPetsByStatusStatus]](../../models/findpetsbystatusstatus.md) | :heavy_minus_sign:                                                                | Status values that need to be considered for filter                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[List[models.Pet]](../../models/.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## find_pets_by_tags

Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.find_pets_by_tags()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tags`                                                              | List[*str*]                                                         | :heavy_minus_sign:                                                  | Tags to filter by                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Pet]](../../models/.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## get_pet_by_id

Returns a single pet

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.get_pet_by_id(pet_id=311674)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `pet_id`                                                            | *int*                                                               | :heavy_check_mark:                                                  | ID of pet to return                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Pet](../../models/pet.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## delete_pet

Deletes a pet

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.delete_pet(pet_id=818965)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `pet_id`                                                            | *int*                                                               | :heavy_check_mark:                                                  | Pet id to delete                                                    |
| `api_key`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Pet](../../models/pet.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## upload_file

uploads an image

### Example Usage

```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.upload_file(pet_id=150516)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `pet_id`                                                            | *int*                                                               | :heavy_check_mark:                                                  | ID of pet to update                                                 |
| `additional_metadata`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Additional Metadata                                                 |
| `request_body`                                                      | *Optional[Union[bytes, IO[bytes], io.BufferedReader]]*              | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.APIResponse](../../models/apiresponse.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |