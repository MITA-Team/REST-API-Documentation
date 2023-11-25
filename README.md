# REST-API-Documentation

## User

### GET

### GET by ID

### POST

## Soal Test

### GET

### POST

## Hasil Test

### GET

#### Request
``` GET http://<IP>/test/result ```

#### Response
```
{
  "status": 200,
  "data" : [
    {
      "id" : "Integer",    ,
      "soal" : "String",
      "jawaban" : "String",
      "createdAt": "date",
      "updatedAt": "date"
    }
  ]
}

```

### POST

## Favorite

### GET

### POST
