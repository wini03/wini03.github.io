Tentu, berikut adalah langkah-langkah untuk membuat web dinamis biodata siswa dengan Node.js, SQLite, dan operasi CRUD (Create, Read, Update, Delete):

# Persiapkan Environment:

1.Pastikan Node.js dan npm terinstal di sistem kamu.
2.Buat direktori proyek baru dan masuk ke dalamnya melalui terminal.
3.Install modul-modul yang diperlukan:

Copy code

npm init -y

npm install express sqlite3 ejs

# Buat Struktur Proyek:

1.Buat file app.js untuk kode server dan direktori views untuk menyimpan file-template EJS.
2.Buat file views/index.ejs untuk halaman utama.

# Kode Server:

Dalam file app.js, tambahkan kode berikut:

![assets](/assets/Capture2.PNG)
![assets](/assets/Capture3.PNG)
![assets](/assets/Capture4.PNG)


# Buat Template EJS:

1. Dalam file views/index.ejs, tambahkan kode untuk menampilkan data siswa dan formulir tambah:
   
![assets](/assets/Capture5.PNG)
![assets](/assets/Capture6.PNG)

# Jalankan Server:

1.Simpan semua perubahan dan jalankan server dengan perintah node app.js.
2.Buka browser dan akses http://localhost:3000 untuk melihat aplikasi CRUD Biodata Siswa.



# hasil prakteknya






