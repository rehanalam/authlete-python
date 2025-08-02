# UserSDK
(*user*)

## Overview

Operations about user

### Available Operations

* [create_user](#create_user) - Create user
* [create_users_with_list_input](#create_users_with_list_input) - Creates list of users with given input array
* [login_user](#login_user) - Logs user into the system
* [logout_user](#logout_user) - Logs out current logged in user session
* [get_user_by_name](#get_user_by_name) - Get user by user name
* [update_user](#update_user) - Update user
* [delete_user](#delete_user) - Delete user

## create_user

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="python" operationID="createUser" method="post" path="/user" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.user.create_user(request={
        "id": 10,
        "username": "theUser",
        "first_name": "John",
        "last_name": "James",
        "email": "john@email.com",
        "password": "12345",
        "phone": "12345",
        "user_status": 1,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [models.User](../../models/user.md)                                 | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## create_users_with_list_input

Creates list of users with given input array

### Example Usage

<!-- UsageSnippet language="python" operationID="createUsersWithListInput" method="post" path="/user/createWithList" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.user.create_users_with_list_input(request=[
        {
            "id": 10,
            "username": "theUser",
            "first_name": "John",
            "last_name": "James",
            "email": "john@email.com",
            "password": "12345",
            "phone": "12345",
            "user_status": 1,
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [List[models.User]](../../models/.md)                               | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## login_user

Logs user into the system

### Example Usage

<!-- UsageSnippet language="python" operationID="loginUser" method="get" path="/user/login" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.user.login_user()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The user name for login                                             |
| `password`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The password for login in clear text                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.LoginUserResponse](../../models/loginuserresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## logout_user

Logs out current logged in user session

### Example Usage

<!-- UsageSnippet language="python" operationID="logoutUser" method="get" path="/user/logout" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    a_client.user.logout_user()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## get_user_by_name

Get user by user name

### Example Usage

<!-- UsageSnippet language="python" operationID="getUserByName" method="get" path="/user/{username}" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.user.get_user_by_name(username="Edyth10")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *str*                                                               | :heavy_check_mark:                                                  | The name that needs to be fetched. Use user1 for testing.           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |

## update_user

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateUser" method="put" path="/user/{username}" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    a_client.user.update_user(username_param="<value>", id=10, username="theUser", first_name="John", last_name="James", email="john@email.com", password="12345", phone="12345", user_status=1)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username_param`                                                    | *str*                                                               | :heavy_check_mark:                                                  | name that needs to be updated                                       |                                                                     |
| `id`                                                                | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 10                                                                  |
| `username`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | theUser                                                             |
| `first_name`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | John                                                                |
| `last_name`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | James                                                               |
| `email`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | john@email.com                                                      |
| `password`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 12345                                                               |
| `phone`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 12345                                                               |
| `user_status`                                                       | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | User Status                                                         | 1                                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## delete_user

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteUser" method="delete" path="/user/{username}" -->
```python
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.user.delete_user(username="Rita_Schuppe")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `username`                                                          | *str*                                                               | :heavy_check_mark:                                                  | The name that needs to be deleted                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.User](../../models/user.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.APIErrorInvalidInput | 400                         | application/json            |
| errors.APIErrorUnauthorized | 401                         | application/json            |
| errors.APIErrorNotFound     | 404                         | application/json            |
| errors.APIError             | 4XX, 5XX                    | \*/\*                       |