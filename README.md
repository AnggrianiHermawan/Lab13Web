# Manajemen Artikel – Fullstack SPA (CI4 + Vue 3)  
Praktikum Pemrograman Web 2 

Nama  : Anggriani Hermawan
NIM   : 312410175 
Kelas : I241B  
Dosen : Agung Nugroho, S.Kom., M.Kom.  

---
# Laporan Praktikum Pemrograman Web 2  
### Framework CodeIgniter 4 – Praktikum 1 sampai 10

Repositori ini berisi hasil praktikum mata kuliah Pemrograman Web 2 dengan studi kasus aplikasi **Blog Sederhana** menggunakan framework CodeIgniter 4 pada project `lab11_ci/ci4`.  
Setiap praktikum dikerjakan sesuai langkah pada modul, disertai penjelasan singkat dan screenshot perubahan yang dilakukan. [file:4][file:2][file:3]

---

## Praktikum 1 – Instalasi CI4 & Konfigurasi Dasar

**Tujuan:**  
Memahami konsep dasar framework, MVC, struktur direktori CodeIgniter 4, serta konfigurasi environment dan layout dasar. [file:4]

**Langkah-langkah yang dilakukan:**

1. Mengaktifkan ekstensi PHP di XAMPP  
   - Mengedit `C:\xampp\php\php.ini` untuk mengaktifkan ekstensi yang dibutuhkan (`mysqli`, `intl`, dll).  
   - Restart Apache dan MySQL dari XAMPP Control Panel.  

2. Instalasi CodeIgniter 4 secara manual  
   - Ekstrak CI4 ke `C:\xampp\htdocs\lab11_ci\ci4`.  
   - Mengakses `http://localhost/lab11_ci/ci4/public/` untuk memastikan CI4 tampil.  

3. Konfigurasi environment  
   - Mengubah nama file `env` menjadi `.env`.  
   - Mengatur `CI_ENVIRONMENT = development` agar error detail muncul saat debug. [file:4]

4. Konfigurasi `.env` dan baseURL  
   - Menambahkan konfigurasi koneksi database ke `lab11_ci`.  
   - Mengatur `app.baseURL = 'http://localhost/lab11_ci/ci4/public/'`.  

5. Memahami struktur direktori CI4  
   - Mempelajari fungsi folder `app`, `public`, `system`, `writable`, dan file `spark`.

6. Membuat routing, controller, dan view sederhana  
   - Menambahkan route untuk `home`, `about`, `contact` di `app/Config/Routes.php`.  
   - Membuat controller `Home` dan `Page` di `app/Controllers`.  
   - Membuat view sederhana di `app/Views` untuk menampilkan teks.  

7. Membuat layout dan template  
   - Menambahkan file `style.css` di folder `public`.  
   - Membuat `app/Views/template/header.php` dan `footer.php` sebagai layout utama.  
   - Mengubah view agar menggunakan `header` dan `footer` template.  
<img width="1920" height="930" alt="Cuplikan layar 2026-03-02 143214" src="https://github.com/user-attachments/assets/0fd01b85-813f-40ee-b158-764a5d43ce6e" />


---

## Praktikum 2 – CRUD Artikel (Model, Controller, View)

**Tujuan:**  
Memahami konsep Model dan CRUD (Create, Read, Update, Delete) pada tabel `artikel`. [file:2]

**Langkah-langkah yang dilakukan:**

1. Membuat database dan tabel `artikel`  
   - Menggunakan database `lab11_ci`.  
   - Membuat tabel `artikel` dengan field: `id`, `judul`, `isi`, `slug`, `gambar`, `status` dan timestamp.  
<img width="622" height="83" alt="image" src="https://github.com/user-attachments/assets/b42bde17-93bf-4e2f-99f2-b5634e6ae339" />


2. Membuat `ArtikelModel`  
   - File: `app/Models/ArtikelModel.php`.  
   - Menentukan `$table = 'artikel'`, `$primaryKey = 'id'`, dan `$allowedFields` sesuai kolom tabel.

3. Membuat controller `Artikel`  
   - File: `app/Controllers/Artikel.php`.  
   - Method `index()` untuk menampilkan daftar artikel.  
   - Method `view($slug)` untuk menampilkan detail artikel berdasarkan slug.  


4. Membuat view `artikel/index.php` dan `artikeldetail.php`  
   - Menampilkan judul, potongan isi, gambar, dan link ke detail.  
   - Menggunakan layout template header/footer dari praktikum 1. 

5. Membuat menu admin artikel  
   - Method `adminIndex()` untuk daftar artikel di halaman admin.  
   - View `artikel/admin_index.php` untuk menampilkan tabel artikel dengan tombol `Edit` dan `Delete`. 

6. Implementasi tambah, ubah, dan hapus artikel  
   - Method `add()`, `edit($id)`, dan `delete($id)` di controller `Artikel`.  
   - View `artikelform_add.php` dan `artikelform_edit.php` untuk form input.
  <img width="1920" height="930" alt="Cuplikan layar 2026-04-02 155700" src="https://github.com/user-attachments/assets/44726a64-6028-446c-ba24-bd15c5446e8d" />
  <img width="1920" height="923" alt="Cuplikan layar 2026-04-04 174132" src="https://github.com/user-attachments/assets/7be7d62b-e800-41b9-912f-90bdb4deea85" />


---

## Praktikum 3 – Penyempurnaan Tampilan & Routing

**Tujuan:**  
Menyempurnakan struktur tampilan front-end dan admin, serta pengaturan routing yang lebih rapi.

**Langkah-langkah yang dilakukan:**

1. Menyusun ulang layout front dan admin  
   - Menambahkan template khusus admin (`template/admin_header.php`, `template/admin_footer.php`).  
   - Memisahkan tampilan front (user) dan admin.  

2. Menyesuaikan routing untuk artikel dan halaman lain  
   - Menambah route `artikel` dan `artikel/(:any)` untuk detail.  
   - Menambah group route `admin` untuk halaman admin artikel.

3. Pengujian menu front dan admin  
   - Mengakses `Home`, `Artikel`, `About`, `Contact` di front.  
   - Mengakses `/admin/artikel` untuk halaman admin.  

---

## Praktikum 4 – Modul Login (Auth & Filter)

**Tujuan:**  
Membuat modul login sederhana dengan auth dan filter untuk membatasi akses ke halaman admin. 

<img width="960" height="462" alt="Cuplikan layar 2026-06-24 202606" src="https://github.com/user-attachments/assets/8dfa3369-37f5-42ad-bf4d-fb017ea055b4" />

**Langkah-langkah yang dilakukan:**

1. Membuat tabel `user` di database `lab11_ci`  
   - Field: `id`, `username`, `useremail`, `userpassword`.  
   - Menambahkan index unik pada `useremail`.  
<img width="479" height="54" alt="image" src="https://github.com/user-attachments/assets/868eec1f-9dcb-4ac0-80ed-0c222bb0388b" />

2. Membuat `UserModel`  
   - File: `app/Models/UserModel.php`.  
   - Mengatur `$table = 'user'`, `$primaryKey = 'id'`, dan `$allowedFields` (`username`, `useremail`, `userpassword`). [file:3]

3. Membuat seeder `UserSeeder`  
   - File: `app/Database/Seeds/UserSeeder.php`.  
   - Menambahkan data user admin (`admin@example.com`) dengan password yang di-hash (`password_hash('admin123', PASSWORD_DEFAULT)`).  
   - Menjalankan seeder: `php spark db:seed UserSeeder`.  
 
4. Membuat controller `User`  
   - Method `login()` untuk proses login (cek email, verifikasi password, set session).  
   - Method `logout()` untuk menghapus session dan redirect ke halaman login. 

5. Membuat view `user/login.php`  
   - Form login dengan input email dan password.  
   - Menampilkan pesan error menggunakan `flashdata` jika login gagal.  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f72c9e0e-3089-43b3-bc20-c7546fdf9784" />


6. Membuat filter `Auth`  
   - File: `app/Filters/Auth.php`.  
   - Mengecek session `logged_in`. Jika belum login, redirect ke `/user/login`. 

7. Konfigurasi filter dan routes  
   - Menambahkan filter `auth` di `app/Config/Filters.php`.  
   - Menggunakan filter `auth` untuk group route `admin`.  

---

## Praktikum 5 – Upload Gambar Artikel

**Tujuan:**  
Menambahkan fitur upload gambar untuk artikel dan menyimpan file di folder `public/gambar`. 

**Langkah-langkah yang dilakukan:**

1. Menyiapkan folder upload  
   - Membuat folder `public/gambar` untuk menyimpan file gambar artikel.

2. Menambahkan field `gambar` di model dan form  
   - Memastikan `ArtikelModel` menyertakan field `gambar` di `$allowedFields`.  
   - Mengubah view form tambah/edit artikel supaya memiliki input type `file` (`<input type="file" name="gambar">`). 

3. Mengubah controller `Artikel` untuk menangani upload  
   - Pada method `add()` dan `edit()`, memproses file upload menggunakan `$this->request->getFile('gambar')`.  
   - Menyimpan nama file gambar ke database dan memindahkan file ke folder `public/gambar`.  

---

## Praktikum 6 – Relasi Artikel dan Kategori (Query Builder)

**Tujuan:**  
Menerapkan relasi **One-to-Many** antara tabel `kategori` dan `artikel`, serta menggunakan Query Builder untuk join data. [file:5]

**Langkah-langkah yang dilakukan:**

1. Membuat tabel `kategori`  
   - Field: `idkategori`, `namakategori`, `slugkategori`.  
   - Menggunakan database `lab11_ci`.  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8ee28035-3c3b-4136-afa0-50735bbd5e60" />


2. Menambah foreign key di tabel `artikel`  
   - Menambahkan field `idkategori` pada tabel `artikel`.  
   - Menambahkan constraint `FOREIGN KEY (idkategori) REFERENCES kategori(idkategori)`.  

3. Membuat `KategoriModel`  
   - File: `app/Models/KategoriModel.php`.  
   - Menentukan `$table = 'kategori'`, `$primaryKey = 'idkategori'`, dan `$allowedFields` (`namakategori`, `slugkategori`). 

4. Memodifikasi `ArtikelModel` untuk join kategori  
   - Menambahkan method `getArtikelDenganKategori()` yang menggunakan Query Builder untuk join `artikel` dan `kategori`.

5. Memodifikasi controller `Artikel`  
   - Method `index()` dan `adminIndex()` menggunakan data join untuk menampilkan nama kategori.  
   - Menambahkan filter pencarian judul dan filter kategori di admin. 

6. Memodifikasi view index dan admin  
   - Menampilkan nama kategori pada daftar artikel.  
   - Menambahkan dropdown kategori di form tambah/edit artikel dan di filter admin.
     
---

## Praktikum 7–8 – Pagination dan Search

**Tujuan:**  
Menambah fitur pencarian dan pagination untuk daftar artikel di halaman admin dan front-end.

**Langkah-langkah yang dilakukan:**

1. Menambahkan pencarian judul artikel  
   - Di controller `Artikel`, menambahkan parameter `q` dari request untuk keyword pencarian.  
   - Menggunakan `like()` pada Query Builder jika keyword diisi.

2. Menambahkan filter kategori di admin  
   - Mengambil `kategoriid` dari request dan menerapkan `where('artikel.idkategori', $kategoriid)` jika dipilih. 

3. Menambahkan pagination  
   - Menggunakan `paginate(10)` di model untuk membatasi jumlah artikel per halaman.  
   - Menampilkan link pagination menggunakan `$pager->links()` di view admin. 

4. Menyesuaikan tampilan  
   - Menambahkan form pencarian dan filter kategori di `artikel/admin_index.php`.  
   - Menampilkan hasil pencarian dan pagination di halaman admin.  

---

## Praktikum 9 – AJAX Pagination dan Search

**Tujuan:**  
Mengimplementasikan pagination dan search menggunakan AJAX untuk meningkatkan user experience pada halaman admin artikel. 

**Langkah-langkah yang dilakukan:**

1. Menyiapkan endpoint AJAX di controller `Artikel`  
   - Memodifikasi `adminIndex()` untuk mengembalikan partial view atau JSON jika request adalah AJAX (`$this->request->isAJAX()`).

2. Menambahkan script jQuery di view admin  
   - Menangani event submit form pencarian dan klik link pagination.  
   - Mengirim request AJAX ke endpoint admin artikel dan mengupdate isi tabel secara dinamis.

3. Menguji AJAX search dan pagination  
   - Mengakses `/admin/artikel`.  
   - Melakukan pencarian artikel dan berpindah halaman tanpa reload penuh.  

---

## Praktikum 10 – Komponen & Penyempurnaan Blog

**Tujuan:**  
Menambahkan komponen seperti **artikel terkini** menggunakan Cell, serta menyempurnakan tampilan blog.
  <img width="1920" height="919" alt="Cuplikan layar 2026-04-02 163621" src="https://github.com/user-attachments/assets/d4e03cdc-e858-4c99-9043-f5b66b97f101" />

**Langkah-langkah yang dilakukan:**

1. Membuat Cell `ArtikelTerkini`  
   - File: `app/Cells/ArtikelTerkini.php`.  
   - Meng-extend `CodeIgniter\View\Cells\Cell` dan menambahkan method `render(): string` untuk mengambil 5 artikel terbaru dan me-render view `components/artikel_terkini`. 
2. Membuat view komponen artikel terkini  
   - File: `app/Views/components/artikel_terkini.php`.  
   - Menampilkan daftar judul artikel terkini dengan link ke detail.

3. Menyisipkan Cell di layout  
   - Menggunakan `view_cell('App\Cells\ArtikelTerkini::render')` di layout front (misalnya di sidebar atau bawah konten).

4. Penyempurnaan tampilan dan navigasi  
   - Menyesuaikan menu utama: `Home`, `Artikel`, `About`, `Contact`.  
   - Menambahkan link ke halaman admin artikel dan halaman login.  

---
## Modul 11: Frontend API Menggunakan VueJS 3
Tujuan: Memahami dasar-dasar VueJS dan cara mengkonsumsi RESTful API untuk menampilkan antarmuka yang reaktif.
Langkah-langkah:
- Melakukan inisialisasi VueJS 3 dan Axios melalui CDN pada file index.html.
- Membangun antarmuka utama (UI) yang reaktif menggunakan directives Vue seperti v-for, v-model, dan v-if.
- Mengimplementasikan fungsi CRUD (Create, Read, Update, Delete) secara asinkron (AJAX) menggunakan library Axios untuk menembak endpoint API dari CodeIgniter 4.
- Merancang tampilan Modal untuk menampung formulir penambahan dan pengubahan data artikel tanpa perlu memuat ulang halaman.

## Modul 12: VueJS Komponen dan Routing (SPA)
Tujuan: Membangun Single Page Application (SPA) seutuhnya dengan memecah antarmuka menjadi komponen-komponen modular.
Langkah-langkah:
- Memecah blok kode antarmuka menjadi komponen mandiri (seperti Komponen Home dan Artikel) agar lebih terstruktur (reusable).
- Mengimplementasikan Vue Router untuk mengatur navigasi Client-Side Routing, sehingga perpindahan antar menu terjadi instan tanpa hard-reload dari browser.
- (Tugas Praktikum): Menambahkan rute baru /about yang memuat komponen profil mahasiswa (berisi Nama, NIM, Kelas, dan Foto) dan menautkannya ke navigasi utama.

## Modul 13: VueJS Autentikasi dan Navigation Guards
Tujuan: Mengamankan antarmuka Frontend (Client-Side Security) dengan membatasi akses pada rute tertentu.
Langkah-langkah & Analisis:
- Membangun modul autentikasi pada API backend CI4 dan form Login pada komponen VueJS. Menggunakan Axios POST untuk mengirim kredensial login ke server secara aman di latar belakang, dan menyimpan status login ke localStorage jika validasi berhasil.
- Mengimplementasikan Vue Router Navigation Guards (router.beforeEach).

(Tugas Praktikum & Analisis): Fungsi router.beforeEach bertindak sebagai pos pemeriksaan sebelum pengguna memasuki suatu halaman rute. Kami menyematkan metadata requiresAuth: true pada rute /artikel dan /about. Jika status sesi pengguna belum login, Navigation Guards akan secara otomatis memblokir akses dan melempar (redirect) pengguna kembali ke halaman form Login.


## Modul 14: Keamanan API, Token & Axios Interceptors
Tujuan: Mengamankan lalu lintas data (endpoint API) di sisi server (Server-Side Security) dari akses pihak ketiga (misalnya via Postman).
Langkah-langkah & Analisis Perbandingan:
- Melakukan modifikasi pada backend CI4 untuk men- generate dan memvalidasi Token Bearer saat user login.
- Menerapkan CI4 Filters pada endpoint CRUD API untuk memastikan hanya request ber-token valid yang dilayani.
- Menerapkan Axios Interceptors di sisi VueJS. Fungsi ini berguna untuk menyusupkan secara otomatis parameter header Authorization: Bearer <token> pada setiap request yang keluar, sehingga kita tidak perlu menuliskan header berulang kali di setiap fungsi CRUD.

(Kesimpulan Tugas): Terdapat perbedaan fundamental antara pengaman sisi klien dan server. Vue Router Navigation Guards murni UI/UX Security (hanya mencegah user awam mengklik dan membuka halaman rute melalui browser). Namun, hacker masih bisa mengambil/merusak data langsung melalui URL API via Postman. Di sinilah CI4 Filters + Token (Server-side) bekerja; sistem ini adalah pengaman inti yang akan menolak mutlak (Error 401 Unauthorized) segala bentuk request ilegal, baik dari browser maupun tools API tester yang tidak membawa token valid.

<img width="122" height="38" alt="image" src="https://github.com/user-attachments/assets/2850d48a-6d33-4ec7-ad9d-b81dc33f5e2d" />

## Penutup

Seluruh praktikum 1 sampai 10 telah diimplementasikan dalam satu project CodeIgniter 4 (`lab11_ci/ci4`) dengan studi kasus blog sederhana:  

- Instalasi dan konfigurasi dasar CI4.  
- CRUD artikel beserta upload gambar.  
- Modul login dengan auth filter.  
- Relasi artikel–kategori dan Query Builder.  
- Pagination, search, dan AJAX untuk admin artikel.  
- Komponen artikel terkini menggunakan Cell. 

