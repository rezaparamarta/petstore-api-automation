# PetStore API Automation Test

Repository ini berisi **API Automation Test** untuk **Swagger PetStore API** menggunakan **Postman** dan **Newman** sebagai command-line runner.

Test mencakup:
- Positive Case
- Negative Case
- Edge Case
- Assertion status code & response body
- Request chaining menggunakan environment variable
- HTML & XML report generation

---
## Requirements
Pastikan environment berikut sudah ter-install sebelum menjalankan test:
### Tools
- **Git**
- **Node.js** ≥ v16 (disarankan LTS)
- **npm** ≥ v8
- **Postman Desktop**
- **Newman** ≥ v5.x
- **Newman HTML Extra Reporter**
- **Newman JUnit Reporter**

### Contoh Versi
- Node.js v18.x
- Newman v5.x

---
## Project Structure
petstore-api-automation/
│
├── petStoreCollection.json # Postman Collection
├── petStore_env.json # Postman Environment
└── README.md
---
## ⬇️ Clone Repository
Clone repository ini ke local machine:
```bat
git clone https://github.com/rezaparamarta/petstore-api-automation.git
Masuk ke folder project:
cd petstore-api-automation
```
---
## 📦 Instalasi
Install Newman & Reporter:
Jalankan perintah berikut satu kali saja:
```bat
npm install -g newman
```
Install Newman HTML Extra Reporter & JUnit Reporter:
```bat
npm install -g newman-reporter-htmlextra
```
```bat
npm install -g newman-reporter-junitfull

```
Verifikasi instalasi:
```bat
newman -v

```
---
## 🚀 Test
Run Test
```bat
newman run petStore-collection.json ^
-e petStore-env.json ^
-r cli,htmlextra ^  
--reporter-htmlextra-export reports\report.html
```

```bat
newman run petStore-collection.json ^
-e petStore-env.json ^
-r cli,htmlextra ^
--reporter-htmlextra-export reports\report.html
newman run petStoreCollection.json ^
-e petStore_env.json ^
-r junitfull ^
--reporter-junitfull-export reports\report.xml
```

Report Output
Setelah test dijalankan:
HTML Report → reports/report.html
XML Report → reports/report.xml
HTML report dapat dibuka langsung di browser.
XML report dapat digunakan untuk CI/CD atau Test Management Tool.

Test Coverage
✅ Positive Case
```
Create new pet
Get pet by valid ID
Update existing pet
Find pets by valid status
Create user
Get user by valid username
Delete pet by valid ID
```
❌ Negative Case
```
Get pet with non-existent ID
Delete pet with non-existent ID
Create pet with missing required field
Update pet with invalid data type
Find pets with invalid status
Get non-existent user
Delete non-existent user
```
⚠️ Edge Case
```
Create pet with negative category and tag ID
```

---
## 📝 Assertion
🔗 Request Chaining Flow
```
Automation ini menggunakan request chaining, antara lain:
Create Pet
Menyimpan petId ke environment
Get / Update / Delete Pet
Menggunakan petId dari environment
Create User
Menyimpan username
Get / Delete User
Menggunakan username dari environment
Chaining dikelola melalui Postman Environment Variables.
```

👤 Author

Reza Paramarta
PetStore API Automation Test