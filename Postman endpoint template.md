description about  what will do with the endpoint
## Request URL
| path | value | type | description | 
| --- | --- | --- | --- |
| groupid | UUID of the group | integer |

## Body request rule
| properties | rules | needs | type | description |
| --- | --- | --- | --- |  --- |
| image_file | <ul><li>first</li></ul> | required | the file image |


```json
{
    "message": "incorrect request body value",
    "errors": {
        "password": [
            "minimum length is 8 char",
            "must be contain at least a number"
        ],
        "email": [
            "invalid format"
        ]
    }
}
```


