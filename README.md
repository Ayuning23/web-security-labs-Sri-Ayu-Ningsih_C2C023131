# README.md - Sistem Login dan Upload File Aman

## Deskripsi
Proyek ini merupakan implementasi sistem login dan upload file untuk portal mahasiswa dengan fokus pada **keamanan aplikasi web**.  
Tujuannya adalah mencegah serangan seperti **SQL Injection**, **Cross Site Scripting (XSS)**, dan **Broken Access Control**, serta memastikan data dan file mahasiswa tetap aman.

---

## 1. Perbedaan Versi Rentan dan Aman

### 1.1 Versi Rentan
Versi rentan menggunakan **input langsung dari pengguna** tanpa validasi atau parameterisasi.  
Contohnya:

- **Login:**
  ```php
  $sql = "SELECT id FROM users WHERE username = '$username' AND password = '$password'";
  $result = $db->query($sql);
