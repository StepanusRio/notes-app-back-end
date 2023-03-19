# NOTES APP BACK END
---
-   install dependencis
    -   Nodemon
    -   eslint
    -   @hapi/server

### How to install Dependencis

```
npm i nodemon eslint @hapi/hapi
```

-   Create A Structure Tree Project

```
notes-app-back-end
├── node_modules
├── src
│ ├── handler.js
│ ├── notes.js
│ ├── routes.js
│ └── server.js
├── .eslintrc.json
├── .gitignore
├── package-lock.json
├── package.json
└── README.md
```
### Have a 2 branch
-   main
-   development
---
    Note : Main Branch for production and development for Dev
---
# Project Criteria
    - [x] Web Server Dapat Menyimpan Catatan
    - [x] Web Server Dapat Menampilkan Catatan
    - [x] Web Server Dapat Mengubah Catatan
    - [x] Web Server Dapat Menghapus Catatan

-   First Criteria

There is Structure Object must been save on Server
```
{
 id: string,
 title: string,
 createdAt: string,
 updatedAt: string,
 tags: array of string,
 body: string,
},
```
Examples:
```
{
 id: 'notes-V1StGXR8_Z5jdHi6B-myT',
 title: 'Sejarah JavaScript',
 createdAt: '2020-12-23T23:00:09.686Z',
 updatedAt: '2020-12-23T23:00:09.686Z',
 tags: ['NodeJS', 'JavaScript'],
 body: 'JavaScript pertama kali dikembangkan oleh Brendan Eich dari Netscape di bawah nama Mocha, yang nantinya namanya diganti menjadi LiveScript, dan akhirnya menjadi JavaScript. Navigator sebelumnya telah mendukung Java untuk lebih bisa dimanfaatkan para pemrogram yang non-Java.',
},
```
Routes Path is "/notes" and Method "POST"

Request Body From Client is :
```
{
 "title": "Judul Catatan",
 "tags": ["Tag 1", "Tag 2"],
 "body": "Konten catatan"
}
```
    Notes: for id, createdAt,updateAt must be created at Server Side and Id must Unix
If Response has been success server retrun:    
```
Statuscode:201  |
(Created)       |
=================
Json:
{
  "status": "success",
  "message": "Catatan berhasil ditambahkan",
  "data": {
    "noteId": "V09YExygSUYogwWJ"
  }
}
```
If Response failed server retrun:    
```
Statuscode:500  |
(error)       |
=================
Json:
{
  "status": "error",
  "message": "Catatan gagal untuk ditambahkan"
}
```
-   Seconds Criteria

Routes Path is "/notes" and Method "GET"

Server Response allGetData
```
{
  "status": "success",
  "data": {
    "notes": [
      {
        "id":"notes-V1StGXR8_Z5jdHi6B-myT",
        "title":"Catatan 1",
        "createdAt":"2020-12-23T23:00:09.686Z",
        "updatedAt":"2020-12-23T23:00:09.686Z",
        "tags":[
          "Tag 1",
          "Tag 2"
        ],
        "body":"Isi dari catatan 1"
      },
      {
        "id":"notes-V1StGXR8_98apmLk3mm1",
        "title":"Catatan 2",
        "createdAt":"2020-12-23T23:00:09.686Z",
        "updatedAt":"2020-12-23T23:00:09.686Z",
        "tags":[
          "Tag 1",
          "Tag 2"
        ],
        "body":"Isi dari catatan 2"
      }
    ]
  }
}
```
If No data
```
{
  "status": "success",
  "data": {
    "notes": []
  }
}
```
Get Specific data findDataId Routes '/notes/{id}'
```
StatusCode :200(Ok)
{
  "status": "success",
  "data": {
    "note": {
      "id":"notes-V1StGXR8_Z5jdHi6B-myT",
      "title":"Catatan 1",
      "createdAt":"2020-12-23T23:00:09.686Z",
      "updatedAt":"2020-12-23T23:00:09.686Z",
      "tags":[
        "Tag 1",
        "Tag 2"
      ],
      "body":"Isi dari catatan 1"
    }
  }
}
```
if Cant find Id
```
StatusCode : 404
{
  "status": "fail",
  "message": "Catatan tidak ditemukan"
}
```
-   Thirdth Criteria

Routes Path is "/notes/{id}" and Method "PUT"

Body Request
```
{
  "title":"Judul Catatan Revisi",
  "tags":[
    "Tag 1",
    "Tag 2"
  ],
  "body":"Konten catatan"
}
```

Server Response Success
```
StatusCode: 200(Ok)
{
  "status": "success",
  "message": "Catatan berhasil diperbaharui"
}
```
if Cant find Id
```
StatusCode : 404
{
  "status": "fail",
  "message": "Gagal memperbarui catatan. Id catatan tidak ditemukan"
}
```
-   Fourth Criteria

Routes Path is "/notes/{id}" and Method "DELETE"

Server Response Success
```
StatusCode: 200(Ok)
{
  "status": "success",
  "message": "Catatan berhasil dihapus"
}
```
if Cant find Id
```
StatusCode : 404
{
  "status": "fail",
  "message": "Catatan gagal dihapus. Id catatan tidak ditemukan"
}
```