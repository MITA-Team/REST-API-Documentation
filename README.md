# REST-API-Documentation

## --- User ---

### GET

### GET by ID

### POST

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
  "status" : 500,
  "message" : "Terjadi kesalahan server!"
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
  "status" : 200,
  "message" : "Data berhasil dihapus!"
}
```