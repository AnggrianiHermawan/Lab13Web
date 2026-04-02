# Gabungan Praktikum 1, 2, 3 & 4 

- **Nama**  : _Anggriani Hermawan_  
- **NIM**   : _312410175_  
- **Kelas** : _I241B_

---

## Praltikum 1 (Pembuatan Website Sederhana Menggunakan Framework CodeIgniter 4)

### 1.1 Tujuan Praktikum
Memahami penggunaan framework CodeIgniter 4
Mampu menjalankan project web di server lokal
Mampu membuat halaman website sederhana
Mampu mengatur struktur folder pada project

### 1.2 Alat dan Bahan

Alat dan bahan yang digunakan:
CodeIgniter 4
Visual Studio Code
XAMPP
Browser (Google Chrome / lainnya)

### 1.3 Langkah-Langkah Praktikum
1. Instalasi CodeIgniter 4
- Download CodeIgniter 4
- Extract ke folder htdocs (XAMPP)
- Jalankan project melalui browser

2. Menjalankan Project

Mengakses project melalui browser:
http://localhost/lab11_ci/ci4/public/
<img width="1920" height="1080" alt="Cuplikan layar 2026-03-02 133248" src="https://github.com/user-attachments/assets/4515cdb9-05c6-4d7f-a8d9-9da9216c1e87" />

4. Membuat Routing & Controller

Buat file:
app/Config/Routes.php
```
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
Buat file baru:
app/Controllers/Page.php
```
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
{
    return view('about', [
        'title' => 'Halaman About',
        'content' => 'Ini adalah halaman About yang menjelaskan isi halaman.'
    ]);
}

    public function contact()
    {
        echo "Ini halaman Contact";
    }

    public function faqs()
    {
        echo "Ini halaman FAQ";
    }
}
```
Buka http://localhost/lab11_ci/ci4/public/about
<img width="1920" height="1080" alt="Cuplikan layar 2026-03-02 135605" src="https://github.com/user-attachments/assets/772043c8-48f2-4190-a14e-2567392bb45b" />

5. Buat Folder Template di Views
kemudian buat file header.php dan footer.php

- Buat header.php
lokasi: app/Views/template/header.php
```
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title><?= $title; ?></title>
 <link rel="stylesheet" href="<?= base_url('style.css'); ?>">
</head>
<body>
 <div id="container">
 <header>
 <h1>Layout Sederhana</h1>
 </header>
 <nav>
 <a href="<?= base_url('/');?>" class="active">Home</a>
 <a href="<?= base_url('/artikel');?>">Artikel</a>
 <a href="<?= base_url('/about');?>">About</a>
 <a href="<?= base_url('/contact');?>">Kontak</a>
 </nav>
 <section id="wrapper">
 <section id="main">
```

- Buat footer.php
lokasi: app/Views/template/footer.php
```
 </section> <!-- end main -->

 <aside id="sidebar">
 <div class="widget-box">
 <h3 class="title">Widget Header</h3>
 <ul>
 <li><a href="#">Widget Link</a></li>
 <li><a href="#">Widget Link</a></li>
 </ul>
 </div>

 <div class="widget-box">
 <h3 class="title">Widget Text</h3>
 <p>Vestibulum lorem elit...</p>
 </div>
 </aside>

 </section> <!-- end wrapper -->

 <footer>
 <p>&copy; 2021 - Universitas Pelita Bangsa</p>
 </footer>

 </div>
</body>
</html>
```

6. Menambahkan style.css
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #f4f4f4;
}

#container {
    width: 980px;
    margin: 20px auto;
    background: #fff;
    box-shadow: 0 0 1em #ccc;
}

header {
    padding: 20px;
    background: #cd4190;
    color: white;
}

nav {
    background: #d060a3;
}

nav a {
    color: #fff;
    text-decoration: none;
    padding: 15px 20px;
    display: inline-block;
}

nav a:hover {
    background: #5c97da;
}

#wrapper {
    display: flex;
}

#main {
    flex: 3;
    padding: 20px;
}

#sidebar {
    flex: 1;
    background: #f0f0f0;
    padding: 20px;
}

.widget-box {
    margin-bottom: 20px;
}

.widget-box .title {
    background: #e34589;
    color: #fff;
    padding: 10px;
}

.widget-box ul {
    list-style: none;
}

.widget-box ul li {
    padding: 5px 0;
}

.widget-box p {
    padding: 10px 0;
}

footer {
    padding: 20px;
    text-align: center;
    background: #79afe6;
    color: white;
}
```
<img width="1920" height="1080" alt="Cuplikan layar 2026-03-02 143214" src="https://github.com/user-attachments/assets/abae289d-7358-4b4f-b4b8-620d5ddfcce4" />

## Praltikum 2 ( Framework Lanjutan (CRUD) )

### 2.1 Membuat database
```
CREATE DATABASE lab_ci4;

USE lab_ci4;

CREATE TABLE artikel (
    id INT AUTO_INCREMENT PRIMARY KEY,
    judul VARCHAR(200),
    isi TEXT,
    gambar VARCHAR(200),
    status TINYINT(1),
    slug VARCHAR(200)
);
```
<img width="103" height="47" alt="image" src="https://github.com/user-attachments/assets/6dd058e0-58c7-4bfe-864a-978fff804df9" />

```
INSERT INTO artikel (judul, isi, slug, status) VALUES
('Belajar CodeIgniter 4', 
'CodeIgniter 4 adalah framework PHP yang digunakan untuk mempermudah proses pembuatan aplikasi web. Dengan menggunakan konsep MVC (Model, View, Controller), developer dapat mengatur struktur program menjadi lebih rapi dan mudah dipelihara.', 
'belajar-codeigniter-4', 1),

('Pengenalan Framework PHP', 
'Framework PHP merupakan kerangka kerja yang membantu programmer dalam membuat aplikasi web dengan lebih cepat. Framework menyediakan berbagai library dan struktur kode sehingga pengembangan aplikasi menjadi lebih efisien.', 
'pengenalan-framework-php', 1);
```
<img width="741" height="64" alt="image" src="https://github.com/user-attachments/assets/ede04d72-d92b-4d88-8fae-901877b6c825" />

### 2.2 Konfigurasi Database (.env)
Edit file .env:
<img width="227" height="68" alt="image" src="https://github.com/user-attachments/assets/8928c20e-8a71-4324-8d2f-4325795cf60f" />

### 2.3 Membuat model
File: app/Models/ArtikelModel.php
```
<?php

namespace App\Models;

use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}
```

### 2.4 Membuat Controller
File: app/Controllers/Artikel.php
```
<?php

namespace App\Controllers;

use App\Models\ArtikelModel;
use CodeIgniter\Exceptions\PageNotFoundException;

class Artikel extends BaseController
{
    // =======================
    // Menampilkan Semua Artikel (Frontend)
    // =======================
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();

        return view('artikel/index', compact('artikel', 'title'));
    }

    // =======================
    // Detail Artikel
    // =======================
    public function view($slug)
    {
        $model = new ArtikelModel();
        $artikel = $model->where(['slug' => $slug])->first();

        if (!$artikel) {
            throw PageNotFoundException::forPageNotFound();
        }

        $title = $artikel['judul'];
        return view('artikel/detail', compact('artikel', 'title'));
    }

    // =======================
    // Admin Index
    // =======================
    public function admin_index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();

        return view('artikel/admin_index', compact('artikel', 'title'));
    }

    // =======================
    // Tambah Artikel
    // =======================
    public function add()
    {
        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);

        $isDataValid = $validation->withRequest($this->request)->run();

        if ($isDataValid) {
            $artikel = new ArtikelModel();
            $artikel->insert([
                'judul' => $this->request->getPost('judul'),
                'isi'   => $this->request->getPost('isi'),
                'slug'  => url_title($this->request->getPost('judul'), '-', true),
                'status' => 1
            ]);

            return redirect()->to('/admin/artikel');
        }

        $title = "Tambah Artikel";
        return view('artikel/form_add', compact('title'));
    }

    // =======================
    // Edit Artikel
    // =======================
    public function edit($id)
    {
        $artikel = new ArtikelModel();

        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);

        $isDataValid = $validation->withRequest($this->request)->run();

        if ($isDataValid) {
            $artikel->update($id, [
                'judul' => $this->request->getPost('judul'),
                'isi'   => $this->request->getPost('isi'),
            ]);

            return redirect()->to('/admin/artikel');
        }

        $data = $artikel->where('id', $id)->first();
        $title = "Edit Artikel";

        return view('artikel/form_edit', compact('title', 'data'));
    }

    // =======================
    // Hapus Artikel
    // =======================
    public function delete($id)
    {
        $artikel = new ArtikelModel();
        $artikel->delete($id);

        return redirect()->to('/admin/artikel');
    }
}
```

### 2.5 Membuat View
```
<?= $this->include('template/admin_header'); ?>

<div class="d-flex justify-content-between align-items-center mb-4">
    <h2><?= $title; ?></h2>
    <a href="<?= base_url('/admin/artikel/add');?>" class="btn btn-primary"> + Tambah Artikel</a>
</div>

<table class="table table-bordered table-striped">
    <thead class="thead-dark">
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
        <?php if($artikel): foreach($artikel as $row): ?>
        <tr>
            <td><?= $row['id']; ?></td>
            <td>
                <b><?= $row['judul']; ?></b>
                <p class="mb-0 text-muted"><small><?= substr($row['isi'], 0, 50); ?>...</small></p>
            </td>
            <td><?= $row['status'] == 1 ? '<span class="badge badge-success">Aktif</span>' : 'Draft'; ?></td>
            <td>
                <a class="btn btn-sm btn-info" href="<?= base_url('/admin/artikel/edit/' . $row['id']);?>">Ubah</a>
                <a class="btn btn-sm btn-danger" onclick="return confirm('Yakin ingin menghapus artikel ini?');" href="<?= base_url('/admin/artikel/delete/' . $row['id']);?>">Hapus</a>
            </td>
        </tr>
        <?php endforeach; else: ?>
        <tr>
            <td colspan="4" class="text-center">Belum ada data artikel.</td>
        </tr>
        <?php endif; ?>
    </tbody>
</table>

<?= $this->include('template/admin_footer'); ?>
```

### 2.6 Membuat Routing
```
<?php

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */
$routes->get('/', 'Home::index');

$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
$routes->get('/artikel', 'Artikel::index');
$routes->get('/artikel/(:any)', 'Artikel::view/$1');

$routes->group('admin', function($routes) {
    $routes->get('artikel', 'Artikel::admin_index');
    $routes->add('artikel/add', 'Artikel::add');
    $routes->add('artikel/edit/(:segment)', 'Artikel::edit/$1');
    $routes->get('artikel/delete/(:segment)', 'Artikel::delete/$1');
});
```

### 2.7 Pengujian CRUD
- Tampilan Daftar Artikel http://localhost:8080/artikel
<img width="1920" height="1080" alt="Cuplikan layar 2026-04-02 155537" src="https://github.com/user-attachments/assets/539199e4-bfa8-4cb4-9df9-b5842591a098" />

- Tampilan Dashboard Admin http://localhost/lab11_ci/ci4/public/admin/artikel
<img width="1920" height="1080" alt="Cuplikan layar 2026-04-02 143219" src="https://github.com/user-attachments/assets/f963752b-9ad6-498d-9723-e2492b579399" />

- Pengujian Tambah Data http://localhost/lab11_ci/ci4/public/admin/artikel/add
<img width="1920" height="1080" alt="Cuplikan layar 2026-04-02 155700" src="https://github.com/user-attachments/assets/a40742c0-a018-4bb3-9e12-7af87eae076c" />

- Pengujian Ubah Data http://localhost/lab11_ci/ci4/public/admin/artikel/edit/1
<img width="1920" height="1080" alt="Cuplikan layar 2026-04-02 155751" src="https://github.com/user-attachments/assets/5d171bde-1e85-4b73-b6f1-13262ef168f0" />

- Pengujian Hapus Data 
<img width="354" height="126" alt="image" src="https://github.com/user-attachments/assets/41f8a43f-221d-4052-83c9-ef06b4113aea" />

## Praltikum 3 (View Layout dan View Cell)

### 3.1 Tambahkan kolom baru bernama created_at dengan tipe data DATETIME atau TIMESTAMP.
```
ALTER TABLE artikel 
ADD created_at DATETIME DEFAULT CURRENT_TIMESTAMP;
```
<img width="89" height="53" alt="image" src="https://github.com/user-attachments/assets/5d32309c-caaf-44d3-89b0-ca226b0480d6" />

### 3.2 Membuat layout utama
- Buat folder app/Views/layout lalu buat file main.php
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title ?? 'My Website' ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
        <header>
            <h1>Layout Sederhana</h1>
        </header>

        <nav>
            <a href="<?= base_url('/');?>">Home</a>
            <a href="<?= base_url('/artikel');?>">Artikel</a>
            <a href="<?= base_url('/about');?>">About</a>
            <a href="<?= base_url('/contact');?>">Kontak</a>
        </nav>

        <section id="wrapper">
            <section id="main">
                <?= $this->renderSection('content') ?>
            </section>

            <aside id="sidebar">
                <?= view_cell('App\\Cells\\ArtikelTerkini::render') ?>

                <div class="widget-box">
                    <h3>Widget</h3>
                    <p>Sidebar tambahan</p>
                </div>
            </aside>
        </section>

        <footer>
            <p>&copy; 2026</p>
        </footer>
    </div>
</body>
</html>
```

- Ubah app/Views/artikel/index.php
```
<?= $this->extend('layout/main'); ?>

<?= $this->section('content'); ?>
    <h1><?= $title; ?></h1>
    <hr>
    
    <?php if($artikel): foreach($artikel as $row): ?>
    <article class="entry">
        <h2>
            <a href="<?= base_url('/artikel/'.$row['slug']);?>"><?= $row['judul']; ?></a>
        </h2>
        <p><?= substr($row['isi'], 0, 200); ?></p>
    </article>
    <hr class="divider" />
    <?php endforeach; else: ?>
    <article class="entry">
        <h2>Belum ada data.</h2>
    </article>
    <?php endif; ?>

<?= $this->endSection(); ?>
```

- Buat view cell
buat folder app/Cells lalu file ArtikelTerkini.php
```
<?php

namespace App\Cells;

use App\Models\ArtikelModel;

class ArtikelTerkini
{
    public function render()
    {
        $model = new ArtikelModel();
        $artikel = $model->orderBy('created_at', 'DESC')
                         ->limit(5)
                         ->findAll();

        return view('components/artikel_terkini', [
            'artikel' => $artikel
        ]);
    }
}
```

- Buat view Components
buat folder app/Views/components lalu buat file artikel_terkini.php
```
<h3>Artikel Terkini</h3>

<ul>
<?php foreach ($artikel as $row): ?>
    <li>
        <a href="<?= base_url('/artikel/' . $row['slug']) ?>">
            <?= $row['judul'] ?>
        </a>
    </li>
<?php endforeach; ?>
</ul>
```

<img width="1920" height="1080" alt="Cuplikan layar 2026-04-02 163621" src="https://github.com/user-attachments/assets/1847c845-b8f1-46a4-a90e-cfddac1fd47d" />
Halaman berhasil menampilkan daftar artikel
Layout (header, navbar, content, sidebar, footer) berhasil dibuat
Sidebar menampilkan artikel terbaru

1. Manfaat utama View Layout

View Layout digunakan untuk:
Menghindari penulisan kode berulang (header, navbar, footer cukup 1x)
Mempermudah pengelolaan tampilan
Membuat struktur halaman lebih rapi dan konsisten
Memisahkan bagian tampilan (content bisa beda, layout tetap sama)

2. Perbedaan View Cell vs View Biasa

View Biasa
Dipanggil dari controller
Menampilkan data utama halaman
Contoh: halaman daftar artikel

View Cell
Dipanggil langsung dari view (tanpa controller)
Biasanya untuk komponen kecil (sidebar, widget, dll)
Bisa ambil data sendiri (pakai model di dalam cell)

Intinya:
View = halaman utama
View Cell = komponen tambahan (modular)

