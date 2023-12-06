# REST-API-Documentation

## --- GET ---
### 1. Menampilkan data anak by ID

#### Request
``` GET http://<IP>/api/child/{id} ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Data anak berhasil ditemukan"
"data" : {
"nama" : "kayla pacifica", 
"tanggal_lahir" : "2030-11-09",
"umur" : "2",
"domisili" : "surabaya",
"keluhan" : "speech",
"Rekomendasi" : ["1","2"] //terapi id
} 
}
```

#### Response Failed
```json
{
"status" : 400,
"message" : "Data anak tidak ditemukan"
}
```

### 2. menampilakan data user by ID


## --- POST ---
## --- PATCH ---
## --- PUT ---
## --- DELETE ---




