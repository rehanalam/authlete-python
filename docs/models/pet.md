# Pet


## Fields

| Field                                                | Type                                                 | Required                                             | Description                                          | Example                                              |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `id`                                                 | *Optional[int]*                                      | :heavy_minus_sign:                                   | N/A                                                  | 10                                                   |
| `name`                                               | *str*                                                | :heavy_check_mark:                                   | N/A                                                  | doggie                                               |
| `category`                                           | [Optional[models.Category]](../models/category.md)   | :heavy_minus_sign:                                   | N/A                                                  |                                                      |
| `photo_urls`                                         | List[*str*]                                          | :heavy_check_mark:                                   | N/A                                                  |                                                      |
| `tags`                                               | List[[models.Tag](../models/tag.md)]                 | :heavy_minus_sign:                                   | N/A                                                  |                                                      |
| `status`                                             | [Optional[models.PetStatus]](../models/petstatus.md) | :heavy_minus_sign:                                   | pet status in the store                              |                                                      |