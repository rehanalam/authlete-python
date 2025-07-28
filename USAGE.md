<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from authlete import Authlete
import os


with Authlete(
    api_key=os.getenv("AUTHLETE_API_KEY", ""),
) as a_client:

    res = a_client.pet.update_pet(name="doggie", photo_urls=[
        "<value>",
        "<value>",
    ], id=10, category={
        "id": 1,
        "name": "Dogs",
    })

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asychronous requests by importing asyncio.
```python
# Asynchronous Example
import asyncio
from authlete import Authlete
import os

async def main():

    async with Authlete(
        api_key=os.getenv("AUTHLETE_API_KEY", ""),
    ) as a_client:

        res = await a_client.pet.update_pet_async(name="doggie", photo_urls=[
            "<value>",
            "<value>",
        ], id=10, category={
            "id": 1,
            "name": "Dogs",
        })

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->