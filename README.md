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

#### Request
``` GET http://<IP>/api/user/{id} ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Data pengguna berhasil ditemukan",
“data” : {
"email" : "fidelaCarissa@gmail.com", 
"username" : "fidela carissa"
}
}
```

#### Response Failed
```json
{
"status" : 400,
"message" : "Data pengguna tidak ditemukan"
}
```

### 3. Menampilkan soal by ID

#### Request
``` GET http://<IP>/api/soal/{id} ```

#### Response Success
```json
{
"status" : 200,
"message" : "Soal ditemukan"
"data" : {
"id" : 1,
"soal" : "Anak melamun atau pandangan kosong?",
“kategori” : “speech”,
"jawaban" : [
Always, 
Usually, 
Sometimes,
Rarely & Never ]
}
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Soal tidak ditemukan"
}
```

### 4. Menampilkan semua soal

#### Request
``` GET http://<IP>/api/soal ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
  "status": 200,
  "message": "Data soal ditemukan",
  "data": [
    {
      "id": 1,
      "soal": "Anak melamun atau pandangan kosong?",
      "kategori": "social",
      "jawaban": ["Always", "Usually", "Sometimes", "Rarely", "Never"]
    },
    {
      "id": 2,
      "soal": "Anak menengok ketika namanya dipanggil?",
      "kategori": "speech",
      "jawaban": ["Always", "Usually", "Sometimes", "Rarely", "Never"]
    }
  ]
}
```

#### Response Failed
```json
{
"status" : 500,
"message" : "Terjadi error selama menampilkan data, coba lagi nanti"
}
```

### 5. Menampilkan terapi by ID

#### Request
``` GET http://<IP>/api/terapi/{id} ```

#### Response Success
```json
{
"status" : 200,
"message" : "Data terapi ditemukan"
"data" : {
"id" : 1,
"kategori" : "speech"
"terapi" : "Menirukan suara hewan",
"deskripsi" : "Ayah atau Ibu atau orang yang bertanggungjawab lainnya dapat memberikan anak mainan yang berupa hewan"
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Data terapi dengan id ${idterapi} tidak ditemukan"
}
```

### 6. Menampilkan semua terapi

#### Request
``` GET http://<IP>/api/terapi ```

#### Response Success
```json
{
  "status": 200,
  "message": "Data terapi ditemukan",
  "data": [
    {
      "id": 1,
      "kategori": "speech",
      "terapi": "Menirukan suara hewan",
      "deskripsi": "Ayah atau Ibu atau orang yang bertanggungjawab lainnya dapat memberikan anak mainan yang berupa hewan"
    },
    {
      "id": 2,
      "kategori": "sensory",
      "terapi": "Wilbarger Brushing Protocol",
      "deskripsi": "Saat akan melakukan terapi, berikan anak pakaian yang tipis lalu tes kuas pada kulit orang tua dan pastikan tidak menimbulkan rasa gatal"
    }
  ]
}
```

#### Response Failed
```json
{
"status" : 500,
"message" : "Terjadi error selama menampilkan data, coba lagi nanti"
}
```

### 7. Menampilkan hasil by ID

#### Request
``` GET http://<IP>/api/hasil_soal/{id} ```

#### Response Success
```json
{
  "status": 200,
  "message": "Data hasil ditemukan",
  "data": {
    "id": 1,
    "hasil": [
      {
        "id": 1,
        "soal": "Anak melamun atau pandangan kosong?",
        "kategori": "social",
        "jawaban": "usually"
      },
      {
        "id": 2,
        "soal": "Anak menengok ketika namanya dipanggil?",
        "kategori": "speech",
        "jawaban": "always"
      }
    ]
  }
}
```

#### Response Failed
```json
{
"status" : 400,
"message" : " Data hasil tidak ditemukan"
}
```


## --- POST ---
### 1. Sign up user

#### Request
``` POST http://<IP>/api/signup ```
```json
{
"email" : "fidelaCarissa@gmail.com", 
"username" : "fidela carissa",
"password" : "mita123",
"konfirmasi_pass" : "mita123"
}
```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 201,
"message" : "Akun berhasil dibuat",
"data" : {
"token"  : "1gfshtdsgh"
}
}
```

#### Response Failed
```json
// validasi kelengkapan data 
{
"status" : 400,
"message" : "Lengkapi semua data yang diperlukan"
}

// exist email/username
{
"status" : 400,
"message" : "Email atau username sudah digunakan"
}

// checking password
// pass length
{
"status" : 400,
"message" : "Panjang password harus minimal 8 karakter"
}
//pass komposisi angka dan huruf
{
"status" : 400,
"message" : "Password harus mengandung setidaknya satu huruf dan satu angka"
}
```

### 2. Login user

#### Request
``` POST http://<IP>/api/login ```
```json
{
"identifier" : "fidelaCarissa@gmail.com", // atau "fidela carissa"
"password" : "mita123"
}
```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Berhasil login"
}
```

#### Response Failed
```json
{ 
"status" : 401,
"message" : " Email/username atau password tidak valid"
}

//catch (error)
{ 
"status" : 500,
"message" : "Terjadi error selama login, coba lagi nanti"
}

//verity token
{
"status" : 401,
"message" : "Token tidak valid"
}

// if(!token)
{
"status" : 403,
"message" : "Token tidak disediakan"
}
```

### 3. Forget & reset password user

#### Request
``` POST http://<IP>/api/forgot-password ```

#### Response Success
```json
{
"status" : 200,
"message" : "Email untuk mengatur ulang password berhasil dikirim"
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Email/username tidak ditemukan"
}
```

#### Request
``` POST http://<IP>/api/reset-password ```
#### Response Success
```json
{
"status" : 200,
"message" : "Password berhasil direset"
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Email/username tidak ditemukan"
}
```

### 4. Logout user

#### Request
``` POST http://<IP>/api/logout ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Logout berhasil"
}
```

#### Response Failed
```json
{
"status" : 500,
"message" : "Logout gagal"
}
```

### 5. Menambahkan data anak

#### Request
``` POST http://<IP>/api/child ```
```json
{
"nama" : "kayla pacifica", 
"tanggal_lahir" : "2030-11-09",
"umur" : "2",
"domisili" : "surabaya"
}
```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 201,
"message" : "Data anak berhasil ditambahkan"
}
```

#### Response Failed
```json
//validasi kelengkapan data
{
"status" : 400,
"message" : "Lengkapi semua data yang diperlukan"
}
```

### 6. Menambahkan data hasil_soal

#### Request
``` POST http://<IP>/api/hasil_soal ```

#### Response Success
```json
{
"status" : 200,
"message" : "Semua soal telah terjawab"
}
```

#### Response Failed
```json
{
"status" : 400,
"message" : "Jawaban soal tidak lengkap"
}
```


## --- PATCH ---
### 1. Update data anak by ID

#### Request
``` PATCH http://<IP>/api/child/{id} ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Data anak dengan id '${childId} berhasil diperbarui”
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Data anak tidak ditemukan"
}
```

## --- PUT ---

## --- DELETE ---
### 1. Menghapus data anak by ID dan nama

#### Request
``` DELETE http://<IP>/api/child/{id}/{nama} ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Data anak dengan id ${childId} dan nama ${childnama} berhasil dihapus"
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Data anak tidak ditemukan "
}
```

### 2. Menghapus data user by ID

#### Request
``` DELETE http://<IP>/api/user/{id} ```

#### Headers
- Authorization: Token

#### Response Success
```json
{
"status" : 200,
"message" : "Data pengguna berhasil dihapus'
}
```

#### Response Failed
```json
{
"status" : 404,
"message" : "Data pengguna tidak ditemukan "
}
// error app.use((err, req, res, next) => {} )
{
"status" : 500,
"message" : "Terjadi kesalahan dalam server"
}
```




