## API Spec

### Create Polling

- endpoint: `api/polling`
- method: `post`
- headers: 
  - accept: `application/json`
  - Authorization: Bearer `$token`
- body:
```json
{
  "question": "string, max:255",
  "options[0]": "string, max:25, required",
  "options[1]": "string, max:25, required",
  "options[2]": "string, max:25, optional",
  "options[3]": "string, max:25, optional",
  "day": "int, min:0, max:7",
  "hour": "int, 24-format, min:0, max:23",
  "minute": "int, min: 5, max: 59"
}
```
- response:
```json
{
  "message": "string",
  "status": "boolean"
}
```

### Get All Polling

- endpoint: `api/polling`
- method: `get`
- headers:
  - accept: `application/json`
  - Authorization: Bearer `$token`
- response:
```json
[
  {
    "id": "int",
    "question": "string",
    "total_voe": "int",
    "due": "datetime",
    "created_at": "datetime"
  },
  {
    "id": "int",
    "question": "string",
    "total_voe": "int",
    "due": "datetime",
    "created_at": "datetime"
  }
]
```

### Get Detail Polling (Portal Admin)

- endpoint: `api/polling/{id}`
- method: `get`
- headers:
  - accept: `application/json`
  - Authorization: Bearer `$token`
- response:
```json
{
  "id": "int",
  "question": "string",
  "options": [
    {
      "key": "string",
      "value": "int",
      "percentage": "int"
    },
    {
      "key": "string",
      "value": "int",
      "percentage": "int"
    }
  ],
  "due": "datetime",
  "total_vote": "int",
  "created_at": "datetime"
}
```

### Get Detail Polling (Penduduk)

- endpoint: `api/polling/{param}`
- method: `get`
- headers:
  - accept: `application/json`
- response:
```json
{
  "id": "int",
  "question": "string",
  "options": [
    {
      "key": "string"
    },
    {
      "key": "string"
    }
  ],
  "due": "datetime",
  "total_vote": "int",
  "created_at": "datetime"
}
```

### Vote

- endpoint: `api/polling/{param}`
- method: `post`
- headers:
  - accept: `application/json`
- body:
```json
{
  "choice": "string"
}
```