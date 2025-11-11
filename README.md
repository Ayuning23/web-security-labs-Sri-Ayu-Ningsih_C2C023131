# README.md - Perbedaan Versi Rentan dan Aman

## Deskripsi
Dokumen ini menjelaskan perbedaan antara versi rentan dan versi aman dari sistem login dan upload file pada portal mahasiswa. Tujuannya untuk memahami risiko keamanan seperti **SQL Injection** dan **Broken Access Control** serta cara mitigasinya.

---

## 1. Versi Rentan
Versi rentan menggunakan **input langsung dari pengguna** tanpa validasi atau proteksi. Contohnya:

- **Login:**
  ```php
  $sql = "SELECT id FROM users WHERE username = '$username' AND password = '$password'";
  $result = $db->query($sql);
Versi rentan dari sistem login dan upload file memiliki risiko keamanan serius: pada login, input pengguna langsung dimasukkan ke query SQL sehingga penyerang bisa melakukan SQL Injection, memungkinkan login tanpa password, mencuri data, atau bahkan menghapus data. Sedangkan pada upload file, file disimpan dengan nama asli di folder publik tanpa validasi ekstensi atau ukuran, sehingga file berbahaya dapat diunggah dan diakses sembarangan oleh siapa saja.  

## Versi Rentan
  Versi aman memisahkan struktur SQL dan data, menambahkan kontrol akses, serta melakukan validasi file.
  
    $stmt = $pdo->prepare("SELECT id, password_hash FROM users WHERE username = :u LIMIT 1");
    $stmt->execute([':u' => $_POST['username']]);
    $user = $stmt->fetch();
    
    if ($user && password_verify($_POST['password'], $user['password_hash'])) {
        // login berhasil
    }
Versi aman menggunakan prepared statements untuk memisahkan data input dan perintah SQL, serta menyimpan password dalam bentuk hash, sehingga risiko SQL Injection hilang dan keamanan data pengguna lebih terjaga.
