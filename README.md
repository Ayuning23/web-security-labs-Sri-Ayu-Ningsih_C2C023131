##Perbedaan Versi Rentan dan Aman
Repositori ini berisi dua versi kode sumber untuk demonstrasi keamanan perangkat lunak: versi rentan (vulnerable) dan versi aman (secure). Tujuan utama adalah untuk mengedukasi tentang kerentanan umum dalam pengembangan perangkat lunak dan bagaimana cara memperbaikinya.

#Deskripsi Proyek
Proyek ini adalah contoh sederhana aplikasi web yang menerima input dari pengguna dan memprosesnya. Versi rentan mengandung kerentanan keamanan yang dapat dieksploitasi, sedangkan versi aman telah diperbaiki untuk mencegah eksploitasi tersebut.


#Kerentanan Utama
SQL Injection: Input pengguna langsung dimasukkan ke dalam query SQL tanpa sanitasi, memungkinkan injeksi kode berbahaya.

Contoh: Jika pengguna memasukkan ' OR '1'='1, query dapat mengembalikan semua data.
Cross-Site Scripting (XSS): Output pengguna ditampilkan tanpa encoding, memungkinkan injeksi skrip JavaScript.

Contoh: Input seperti <script>alert('Hacked!')</script> akan dieksekusi di browser.
Buffer Overflow (dalam konteks tertentu): Jika ada pemrosesan string tanpa batas, dapat menyebabkan overflow.


#Versi Aman (Secure Version)
Versi ini terletak di direktori secure/. Kode ini telah diperbaiki untuk mengatasi kerentanan di versi rentan.

Perbaikan yang Diterapkan
SQL Injection: Menggunakan parameterized queries atau ORM (seperti SQLAlchemy) untuk mencegah injeksi.

Contoh: Query menggunakan placeholder seperti SELECT * FROM users WHERE username = ? dengan binding parameter.
Cross-Site Scripting (XSS): Output pengguna di-encode menggunakan fungsi seperti html.escape() atau template engine yang aman (misalnya, Jinja2 dengan auto-escaping).

Contoh: Input berbahaya akan ditampilkan sebagai teks biasa, bukan kode eksekusi.
Buffer Overflow: Menambahkan validasi input dan batasan panjang string untuk mencegah overflow.

