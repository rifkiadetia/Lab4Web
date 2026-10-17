# Lab4Web - Praktikum 4: CSS Layout

Mata Kuliah: Pemrograman Web
Nama:Rifki Ade Tia
NIM:312510334
Kelas:I253C

---

## Tujuan Praktikum

1. Memahami struktur dasar pembuatan layout.
2. Memahami konsep box element.
3. Memahami CSS Floating.
4. Memahami HTML 5 Semantic Elements.
5. Membuat layout web sederhana.

## Struktur Folder

```
Lab4Web/
├── lab4_box/
│   └── lab4_box.html
├── lab4_layout/
│   ├── home.html
│   ├── about.html
│   ├── kontak.html
│   └── style.css
├── screenshots/
└── README.md
```

> Catatan: semua screenshot disimpan di folder `screenshots/`. Ganti nama file pada tautan gambar di bawah sesuai screenshot masing-masing.

---

# Bagian A: Box Element dan CSS Float (`lab4_box.html`)

## A.1 Persiapan Dokumen HTML

Membuat file `lab4_box.html` berisi kerangka dasar HTML5 dengan elemen semantik `<header>` yang memuat judul `<h1>Box Element</h1>`.

## A.2 Membuat Box Element

Menambahkan `<section>` berisi tiga `<div>` dengan class `div1`, `div2`, dan `div3`. Setiap `<div>` adalah sebuah **box**. Tanpa CSS tambahan, `<div>` bersifat *block* sehingga tersusun menumpuk ke bawah dan memenuhi lebar halaman.

```html
<section>
    <div class="div1">Div 1</div>
    <div class="div2">Div 2</div>
    <div class="div3">Div 3</div>
</section>
```

## A.3 CSS Float Property

Menambahkan CSS pada `<head>`:

```css
div {
    float: left;
    padding: 10px;
}
.div1 { background: red; }
.div2 { background: yellow; }
.div3 { background: green; }
```

**Penjelasan:**
- `float: left` membuat elemen "mengambang" ke kiri, sehingga elemen berikutnya naik berdampingan di sebelahnya.
- `padding: 10px` memberi ruang di dalam box.
- Class `div1`, `div2`, `div3` memberi warna latar merah, kuning, dan hijau.

**Hasil:** ketiga div tampil berjajar ke samping dan lebarnya menyesuaikan isi.

## A.4 Mengatur Clearfix

Menambahkan `<div class="div4">Div 4</div>` setelah `div3`, lalu CSS:

```css
.div4 {
    background-color: blue;
    clear: left;
    float: none;
}
```

**Penjelasan:**
- `clear` mengatur sisi mana yang tidak boleh berdekatan dengan elemen float.
- `clear: left` memaksa Div 4 turun ke bawah elemen yang float ke kiri.
- `float: none` membuat Div 4 kembali normal (block) sehingga memanjang selebar halaman.

**Eksperimen nilai `clear`:**

| Nilai | Efek |
|---|---|
| `left` | Turun di bawah elemen float kiri |
| `right` | Tidak berefek di sini, karena tidak ada elemen float kanan |
| `both` | Turun di bawah elemen float kiri maupun kanan |

---

# Bagian B: Membuat Layout Sederhana (`lab4_layout`)

Layout yang dibuat terdiri dari header, navigasi, hero panel, area main dan sidebar, serta footer.

## B.1 Persiapan File

Membuat folder `lab4_layout` berisi `home.html` dan `style.css`. File CSS dihubungkan ke HTML melalui:

```html
<link rel="stylesheet" href="style.css">
```

Di dalam `<body>` dibuat pembungkus `<div id="container">`.

## B.2 Kerangka Layout dengan Semantic Elements

Di dalam `#container` dibuat kerangka memakai elemen semantik HTML5:

```html
<header>
    <h1>Layout Sederhana</h1>
</header>
<nav>
    <a href="home.html" class="active">Home</a>
    <a href="artikel.html">Artikel</a>
    <a href="about.html">About</a>
    <a href="kontak.html">Kontak</a>
</nav>
<section id="hero"></section>
<section id="wrapper">
    <section id="main"></section>
    <aside id="sidebar"></aside>
</section>
<footer>
    <p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>
```

| Elemen | Fungsi |
|---|---|
| `<header>` | Kepala halaman / judul situs |
| `<nav>` | Kumpulan link navigasi |
| `<section>` | Bagian dalam dokumen (hero, wrapper, main) |
| `<aside>` | Konten pendamping (sidebar) |
| `<footer>` | Kaki halaman |

## B.3 CSS Dasar dan Header

Pada `style.css` ditambahkan:

- `@import` Google Font **Open Sans**.
- **Reset CSS** (`* { margin: 0; padding: 0; }`) untuk menghilangkan jarak bawaan browser.
- `body`: pengaturan font, ukuran, dan warna teks.
- `#container`: `width: 980px`, `margin: 0 auto` (posisi di tengah), dan `box-shadow` untuk bayangan.
- `header` dan `header h1`: padding, margin, dan warna judul.

## B.4 Membuat Navigasi

```css
nav { display: block; background-color: #1f5faa; }
nav a { padding: 15px 30px; display: inline-block; color: #ffffff;
        font-size: 14px; text-decoration: none; font-weight: bold; }
nav a.active, nav a:hover { background-color: #2b83ea; }
```

**Penjelasan:**
- `nav` menjadi bar biru selebar container.
- `nav a` dengan `display: inline-block` membuat link berjajar ke samping namun tetap bisa diberi padding atas-bawah.
- `a.active` menandai halaman aktif, `a:hover` memberi efek saat kursor diarahkan.

## B.5 Membuat Hero Panel

**HTML:** mengisi `<section id="hero">` dengan `<h1>`, `<p>`, dan link tombol "Learn more".

**CSS:**

```css
#hero { background-color: #e4e4e5; padding: 50px 20px; margin-bottom: 20px; }
#hero h1 { margin-bottom: 20px; font-size: 35px; }
#hero p { margin-bottom: 20px; font-size: 18px; line-height: 25px; }
```

**Penjelasan:** hero panel adalah kotak abu-abu besar di bawah menu yang berfungsi sebagai sorotan utama halaman.

## B.6 Mengatur Layout Main dan Sidebar dengan Float

```css
#wrapper { margin: 0; }
#main    { float: left; width: 640px; padding: 20px; }
#sidebar { float: left; width: 260px; padding: 20px; }
```

**Penjelasan:**
- `#main` dan `#sidebar` sama-sama `float: left` sehingga tersusun berdampingan.
- Perhitungan lebar: 640 + 40 (padding main) + 260 + 40 (padding sidebar) = **980px**, sama dengan lebar `#container`. Jika lebih, sidebar akan turun ke bawah.

## B.7 Membuat Sidebar Widget

**HTML:** `<aside id="sidebar">` diisi dua `<div class="widget-box">`: widget pertama berisi daftar 5 link, widget kedua berisi teks.

**CSS:** `.widget-box`, `.widget-box .title`, `.widget-box ul`, `.widget-box li`, `.widget-box li a`, `.widget-box li:hover a`, dan `.widget-box p`.

**Penjelasan:**
- `.title` berlatar biru dengan teks putih sebagai judul widget.
- `list-style-type: none` menghilangkan bullet.
- `li a` dengan `display: block` membuat seluruh baris dapat diklik.
- `li:hover a` memberi efek abu-abu saat hover.

## B.8 Mengatur Footer

```css
footer { clear: both; background-color: #1d1d1d; padding: 20px; color: #eee; }
```

**Penjelasan:** `clear: both` memaksa footer berada di bawah semua elemen float (main dan sidebar). Tanpa ini footer akan naik dan menempel di samping.

## B.9 Menambahkan Elemen pada Main Content (3 Kolom)

**HTML:** `<section id="main">` diisi `<div class="row">` berisi tiga `<div class="box">`. Tiap box memuat gambar bulat, `<h3>`, `<p>`, dan tombol "View detail".

**CSS penting:**

```css
.box { display: block; float: left; width: 33.333333%;
       box-sizing: border-box; padding: 0 10px; text-align: center; }
.image-circle { border-radius: 50%; }
.row { margin: 0 -10px; box-sizing: border-box; }
.row:after, .row:before, .entry:after, .entry:before { content: ''; display: table; }
.row:after, .entry:after { clear: both; }
```

**Penjelasan:**
- `float: left` dengan `width: 33.333333%` membuat tiga kolom sama lebar.
- `box-sizing: border-box` membuat padding termasuk dalam lebar, sehingga tiga kolom tidak melebihi 100%.
- `border-radius: 50%` mengubah gambar persegi menjadi lingkaran.
- **Clearfix** (`:after` dengan `clear: both`) membuat `.row` dan `.entry` membungkus anak yang float, sehingga tinggi parent tidak menjadi 0.
- Perbaikan dari modul: selector `box img` ditulis `.box img` (menggunakan titik karena class).

## B.10 Menambahkan Content Artikel

**HTML:** setelah `.row` di dalam `#main` ditambahkan dua pasang `<hr class="divider">` dan `<article class="entry">`. Artikel pertama berisi gambar di kiri, artikel kedua memakai `class="right-img"` sehingga gambar di kanan.

**CSS:**

```css
.divider { border: 0; border-top: 1px solid #eeeeee; margin: 40px 0; }
.entry { margin: 15px 0; }
.entry h2 { margin-bottom: 20px; }
.entry p { line-height: 25px; }
.entry img { float: left; border-radius: 5px; margin-right: 15px; }
.entry .right-img { float: right; }
```

**Penjelasan:**
- `.divider` adalah garis pemisah antar bagian.
- `.entry img` dengan `float: left` membuat teks mengalir di sebelah kanan gambar.
- `.entry .right-img` menimpa menjadi `float: right` sehingga gambar pindah ke kanan.
---

# Bagian C: Pertanyaan dan Tugas

## C.1 Layout Menu About (`about.html`)

Membuat halaman `about.html` dengan struktur layout yang sama (header, nav, footer) dan isi single layout berupa deskripsi diri dan portfolio. Menu **About** diberi `class="active"`.

## C.2 Layout Menu Contact (`kontak.html`)

Membuat halaman `kontak.html` dengan struktur layout yang sama dan isi berupa form: nama, email, dan pesan (message), serta tombol kirim. Menu **Kontak** diberi `class="active"`.
---

## Kesimpulan

- Setiap elemen HTML pada dasarnya adalah **box** yang terdiri dari margin, border, padding, dan content.
- Properti `float` dan `clear` memungkinkan elemen disusun berdampingan dan dikontrol posisinya.
- Elemen semantik HTML5 (`header`, `nav`, `section`, `aside`, `footer`, `article`) membuat struktur halaman lebih jelas dan mudah dipahami.
- Layout web sederhana dapat dibangun dengan kombinasi semantic elements, box model, dan CSS float.
