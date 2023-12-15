# REST-API-Documentation

## --- Welcome ---

### GET

#### Request
``` GET http://<IP>/api/ ```

## --- User ---

## Register

### POST

#### Request

```
POST {{base_url}}/api/users/register
Content-Type: application/json

{
    "username" : "string",
    "email" : "string",
    "domicile" :  "string",
    "birthDate" : "date",
    "password" :  "string",
    "confirmPass" : "string"
}
```

#### Response Success

```
{
  message: "Successfully added data!",
  status: 201,
  data: {
    id: "int",
    "username" : "string",
    "email" : "string",
    "domicile" :  "string",
    "birthDate" : "date",
    "password" :  "string",
    "confirmPass" : "string"
  }
}
```

### Response Fail

```
{ 
  error: "Internal Server Error"
}
```

## --- Soal Test ---

### GET

### POST

## --- Hasil Test ---

### GET

#### Request
``` GET http://<IP>/api/result/:userId/test/:testId ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
  "status": 200,
  "data" : [
    {
      "id" : "Integer",
      "soal" : "String",
      "jawaban" : "String",
      "createdAt" : "date",
      "updatedAt" : "date"
    }
  ],
  "recommendation" : "String"
}
```

#### Response Failed

```json
{
  "status" : 404,
  "message" : "Data tidak ditemukan!"
}
```

### DELETE

#### Request
``` DELETE http://<IP>/api/result/:userId/test/:testId```

#### Headers
- Authorization: Token

#### Response Success
```json
{
  "status" : 200,
  "message" : "Data berhasil dihapus!"
}
```

#### Response Failed
```json
{
  "status" : 500,
  "message" : "Terjadi kesalahan server!"
}
```

## --- Favorite ---

### GET

#### Request
``` GET http://<IP>/api/user/:userId/lists ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
  "status" : 200,
  "data" : [
    {
      "id" : "Integer",
      "title" : "String",
      "body" : "String",
      "image": "String"
    }
  ]
}
```

#### Response Failed
```json
{
  "status" : 404,
  "message" : "Data tidak ditemukan!"
}
```

### POST

#### Headers
- Authorization: Token

#### Request
```json 
POST http://<IP>/api/user/:userId/lists 
Content-Type: application/json

{
  "id" : "Integer",
  "title" : "String",
  "body" : "String",
  "image": "String"
}
```

#### Response Success
```json
{
  "status" : 200,
  "message" : "Data berhasil ditambahkan!"
}
```

#### Response Failed
```json
{
  "status" : 500,
  "message" : "Terjadi kesalahan server!"
}
```
