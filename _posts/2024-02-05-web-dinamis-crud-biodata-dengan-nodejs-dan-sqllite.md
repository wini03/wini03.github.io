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

Copy code
const express = require('express');
const sqlite3 = require('sqlite3').verbose();
const ejs = require('ejs');
const app = express();
const port = 3000;

app.set('view engine', 'ejs');
app.use(express.urlencoded({ extended: true }));

const db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE IF NOT EXISTS biodata_siswa (id INTEGER PRIMARY KEY, nama TEXT, umur INTEGER, alamat TEXT)");
});

app.get('/', (req, res) => {
  db.all('SELECT * FROM biodata_siswa', (err, rows) => {
    if (err) {
      console.error('Error querying database:', err);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.render('index', { siswa: rows });
  });
});

app.post('/biodata', (req, res) => {
  const { nama, umur, alamat } = req.body;
  const query = 'INSERT INTO biodata_siswa (nama, umur, alamat) VALUES (?, ?, ?)';
  
  db.run(query, [nama, umur, alamat], function(err) {
    if (err) {
      console.error('Error inserting data:', err);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.redirect('/');
  });
});

app.get('/edit/:id', (req, res) => {
  const id = req.params.id;
  db.get('SELECT * FROM biodata_siswa WHERE id = ?', [id], (err, row) => {
    if (err) {
      console.error('Error querying database:', err);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.render('edit', { siswa: row });
  });
});

app.post('/update/:id', (req, res) => {
  const id = req.params.id;
  const { nama, umur, alamat } = req.body;
  const query = 'UPDATE biodata_siswa SET nama=?, umur=?, alamat=? WHERE id=?';
  
  db.run(query, [nama, umur, alamat, id], function(err) {
    if (err) {
      console.error('Error updating data:', err);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.redirect('/');
  });
});

app.get('/delete/:id', (req, res) => {
  const id = req.params.id;
  db.run('DELETE FROM biodata_siswa WHERE id = ?', [id], function(err) {
    if (err) {
      console.error('Error deleting data:', err);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.redirect('/');
  });
});

app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});

# Buat Template EJS:

1. Dalam file views/index.ejs, tambahkan kode untuk menampilkan data siswa dan formulir tambah:
   
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Biodata Siswa</title>
</head>
<body>
  <h1>Data Biodata Siswa</h1>
  <ul>
    <% siswa.forEach((siswa) => { %>
      <li>
        <%= siswa.nama %> - <%= siswa.umur %> tahun - <%= siswa.alamat %>
        <a href="/edit/<%= siswa.id %>">Edit</a>
        <a href="/delete/<%= siswa.id %>">Delete</a>
      </li>
    <% }) %>
  </ul>
  <form action="/biodata" method="post">
    <label for="nama">Nama:</label>
    <input type="text" id="nama" name="nama" required>
    <label for="umur">Umur:</label>
    <input type="number" id="umur" name="umur" required>
    <label for="alamat">Alamat:</label>
    <input type="text" id="alamat" name="alamat" required>
    <button type="submit">Tambah</button>
  </form>
</body>
</html>
      
2.Dalam file views/edit.ejs, tambahkan kode untuk formulir edit:

Copy code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Edit Biodata</title>
</head>
<body>
  <h1>Edit Biodata Siswa</h1>
  <form action="/update/<%= siswa.id %>" method="post">
    <label for="nama">Nama:</label>
    <input type="text" id="nama" name="nama" value="<%= siswa.nama %>" required>
    <label for="umur">Umur:</label>
    <input type="number" id="umur" name="umur" value="<%= siswa.umur %>" required>
    <label for="alamat">Alamat:</label>
    <input type="text" id="alamat" name="alamat" value="<%= siswa.alamat %>" required>
    <button type="submit">Update</button>
  </form>
</body>
</html>

# Jalankan Server:

1.Simpan semua perubahan dan jalankan server dengan perintah node app.js.
2.Buka browser dan akses http://localhost:3000 untuk melihat aplikasi CRUD Biodata Siswa.




