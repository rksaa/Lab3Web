# Praktikum 3 – CSS Dasar (Pemrograman Web)

| | |
|---|---|
| **Nama** | Riksa Siddiq Alrizki |
| **NIM** | 312510015 |
| **Kelas** | I253A |
| **Program Studi** | Teknik Informatika |
| **Mata Kuliah** | Pemrograman Web |
| **Universitas** | Universitas Pelita Bangsa |

---

## 1. Tujuan Praktikum

1. Memahami cara menerapkan CSS pada halaman HTML (inline, internal, dan eksternal).
2. Memahami penggunaan selector dasar: *element selector*, *ID selector*, dan *class selector*.
3. Mampu mengatur tampilan teks, warna, border, padding, margin, dan navigasi.

## 2. Struktur Folder

```
Lab3Web/
├── index.html
├── style_eksternal.css
└── README.md
```

## 3. Langkah-langkah Pengerjaan

### Langkah 1 – Membuat struktur HTML (`index.html`)

Pertama dibuat kerangka halaman HTML dengan elemen `header`, `nav`, dan `div` ber-ID `intro`. File CSS eksternal dihubungkan melalui tag `<link>` di dalam `<head>`.

```html
<link rel="stylesheet" href="style_eksternal.css" type="text/css">
```

Isi `<body>`:

- `<header>` berisi judul `<h1>CSS Internal dan <i>Inline CSS</i></h1>`.
- `<nav>` berisi tiga tautan: **CSS Dasar**, **CSS Eksternal**, **HTML Dasar**.
- `<div id="intro">` berisi `<h1>Hello World</h1>`, paragraf perkenalan, dan tombol berupa tautan `<a class="button btn-primary">`.

![Kode index.html](screenshoot/01.png)

**Hasil (belum diberi CSS):** halaman tampil dengan gaya bawaan browser. Judul berwarna hitam, menu navigasi hanya berupa tautan biru bergaris bawah, dan semua elemen rata kiri.

![Tampilan tanpa CSS](screenshoot/02.png)

---

### Langkah 2 – Membuat CSS eksternal untuk `body`, `header`, dan `h1` (`style_eksternal.css`)

```css
body {
  font-family: 'Open Sans', sans-serif;
}
header {
  min-height: 80px;
  border-bottom: 1px solid #00e600;
}
h1 {
  font-size: 24px;
  color: #00e600;
  text-align: center;
  padding: 20px 10px;
}
h1 i {
  color: #00e600;
}
```

![Kode CSS untuk body, header, h1](screenshoot/03.png)

**Penjelasan:**

| Selector | Fungsi |
|---|---|
| `body` | Mengatur jenis font seluruh halaman menjadi *Open Sans* (cadangan `sans-serif`). |
| `header` | Memberi tinggi minimal 80px dan garis hijau di bagian bawah. |
| `h1` | Ukuran font 24px, warna hijau `#00e600`, rata tengah, dan jarak dalam (padding) 20px atas-bawah dan 10px kiri-kanan. |
| `h1 i` | *Descendant selector*: hanya mewarnai teks miring (`<i>`) yang berada di dalam `h1`. |

**Hasil:** judul berubah menjadi hijau dan rata tengah, font berganti menjadi sans-serif, serta muncul garis hijau di bawah header.

![Hasil styling header dan h1](screenshoot/04.png)

---

### Langkah 3 – Menata menu navigasi (`nav`)

```css
nav {
  background: #20A759;
  color: #fff;
  padding: 10px;
}
nav a {
  color: #fff;
  text-decoration: none;
  padding: 10px 20px;
}
nav .active,
nav a:hover {
  background: #0B6B3A;
}
```

![Kode CSS nav](screenshoot/05.png)

**Penjelasan:**

- `nav` memberi latar hijau `#20A759`, teks putih, dan padding 10px sehingga menjadi bar menu.
- `nav a` menghilangkan garis bawah tautan (`text-decoration: none`), mengubah warna teks menjadi putih, dan menambah ruang `10px 20px` agar tiap menu terlihat seperti tombol.
- `nav .active, nav a:hover` memberi warna hijau tua `#0B6B3A` pada menu yang berkelas `active` dan pada menu yang sedang disorot kursor (*hover*). Tanda koma membuat dua selector berbagi satu aturan yang sama.

**Hasil:** menu navigasi tampil sebagai bar hijau dengan teks putih.

![Hasil styling nav](screenshoot/06.png)

---

### Langkah 4 – Menambahkan ID Selector dan Class Selector

```css
/* ID Selector */
#intro {
  background: #418fb1;
  border: 1px solid #099249;
  min-height: 100px;
  padding: 10px;
}
#intro h1 {
  text-align: left;
  border: 0;
  color: #fff;
}
/* Class Selector */
.button {
  padding: 15px 20px;
  background: #bebcbd;
  color: #fff;
  display: inline-block;
  margin: 10px;
  text-decoration: none;
}
.btn-primary {
  background: #E42A42;
}
```

![Kode CSS ID dan class selector](screenshoot/07.png)

**Penjelasan:**

| Selector | Jenis | Fungsi |
|---|---|---|
| `#intro` | ID selector | Memberi latar biru `#418fb1`, border hijau, tinggi minimal 100px, dan padding 10px pada `<div id="intro">`. |
| `#intro h1` | ID + elemen | Mengubah judul di dalam `#intro` menjadi rata kiri, tanpa border, dan berwarna putih. Aturan ini menimpa aturan `h1` umum karena lebih spesifik. |
| `.button` | Class selector | Mengubah tautan menjadi tombol: padding 15px 20px, latar abu-abu, teks putih, `inline-block`, margin 10px, tanpa garis bawah. |
| `.btn-primary` | Class selector | Mengganti warna latar tombol menjadi merah `#E42A42`. Karena ditulis setelah `.button`, warna ini yang dipakai. |

Pada HTML, tombol memakai dua class sekaligus: `class="button btn-primary"`.

---

### Langkah 5 – Hasil akhir

Setelah semua aturan CSS diterapkan, halaman tampil dengan header hijau, menu navigasi hijau (menu **CSS Eksternal** tampak lebih gelap saat di-*hover*), area `#intro` berlatar biru, dan tombol **Informasi selengkapnya.** berwarna merah.

![Hasil akhir](screenshoot/08.png)

---

## 4. Perbandingan Tiga Cara Menerapkan CSS

| Jenis | Cara penulisan | Kelebihan | Kekurangan |
|---|---|---|---|
| **Inline** | Atribut `style="..."` pada tag | Cepat untuk perubahan satu elemen | Sulit dikelola, tidak bisa dipakai ulang |
| **Internal** | Tag `<style>` di dalam `<head>` | Berlaku untuk satu halaman | Tidak bisa dibagikan ke halaman lain |
| **Eksternal** | File `.css` terpisah dengan `<link>` | Satu file untuk banyak halaman, rapi | Perlu file tambahan |

Pada praktikum ini CSS yang digunakan adalah **CSS eksternal** (`style_eksternal.css`).

## 5. Perbedaan Selector yang Dipakai

| Selector | Tanda | Contoh | Keterangan |
|---|---|---|---|
| Element | (nama tag) | `h1`, `nav a` | Mengenai semua elemen dengan tag tersebut |
| ID | `#` | `#intro` | Untuk satu elemen unik |
| Class | `.` | `.button` | Bisa dipakai di banyak elemen |
| Descendant | spasi | `h1 i` | Elemen di dalam elemen lain |
| Pseudo-class | `:` | `a:hover` | Kondisi tertentu, misalnya saat kursor di atas elemen |

## 6. Kesimpulan

Melalui praktikum ini dipelajari cara menghubungkan CSS eksternal ke HTML dan menggunakan selector elemen, ID, dan class untuk mengatur warna, font, jarak, border, serta tampilan menu dan tombol. Selector yang lebih spesifik (seperti `#intro h1`) dapat menimpa aturan yang lebih umum (seperti `h1`). Dengan CSS, tampilan halaman yang awalnya polos dapat diubah menjadi lebih rapi dan menarik tanpa mengubah isi HTML.
