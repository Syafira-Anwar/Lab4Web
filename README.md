Menambahkan `float: left` dan `padding: 10px` pada `div`, serta warna latar berbeda untuk tiap class.<img width="181" height="85" alt="image" src="https://github.com/user-attachments/assets/32afd41c-b78f-4d83-9f22-9cfb7b062512" />
Menambahkan `div4` dengan `clear: left` dan `float: none` agar tampil di bawah elemen yang mengambang.<img width="245" height="113" alt="image" src="https://github.com/user-attachments/assets/9cb29d46-14d8-4635-b8f4-8730d614f5d5" /> <img width="386" height="157" alt="image" src="https://github.com/user-attachments/assets/a43012b2-aceb-40b0-b58b-e90b5ea97cdb" />
2.3Header dan reset CSS
Menambahkan reset CSS (`margin: 0; padding: 0`), pengaturan `body`, lebar `#container` 980px yang rata tengah, serta gaya header.
![Header](screenshots/07-header.png)
# Laporan Praktikum 4: CSS Layout

| | |
|---|---|
| **Mata Kuliah** | Pemrograman Web |
| **Nama** | _(isi nama)_ |
| **NIM** | _(isi NIM)_ |
| **Kelas** | _(isi kelas)_ |

## Struktur Folder

```
Lab4Web/
├── lab4_box.html
├── lab4_layout/
│   ├── home.html
│   ├── about.html
│   ├── kontak.html
│   └── style.css
├── screenshots/
└── README.md
```

---

# Bagian 1: Box Element dan CSS Float

File: `lab4_box.html`

## 1.1 Persiapan dokumen HTML

Membuat file `lab4_box.html` berisi struktur dasar HTML5 dengan elemen semantik `<header>` dan judul **Box Element**.

```html
<body>
    <header>
        <h1>Box Element</h1>
    </header>
</body>
```

![Persiapan dokumen HTML](screenshots/01-persiapan.png)

## 1.2 Membuat Box Element

Menambahkan tiga tag `<div>` (`div1`, `div2`, `div3`) di dalam `<section>`. Tanpa `float`, setiap `div` adalah elemen *block*, sehingga tampil menumpuk ke bawah dan memenuhi lebar halaman.

```html
<section>
    <div class="div1">Div 1</div>
    <div class="div2">Div 2</div>
    <div class="div3">Div 3</div>
</section>
```

![Box element tanpa float](screenshots/02-box-element.png)

## 1.3 CSS Float Property

Menambahkan `float: left` pada `div`. Elemen kini "mengambang" ke kiri sehingga ketiga box berjajar ke samping dan lebarnya hanya selebar isinya (ditambah `padding: 10px`).

```css
div {
    float: left;
    padding: 10px;
}
```

![Box element dengan float](screenshots/03-float.png)

## 1.4 Clearfix (Property `clear`)

Menambahkan `div4` setelah `div3`. Agar `div4` tampil **di bawah** elemen yang mengambang, `float` dinonaktifkan (`float: none`) dan `clear: left` ditambahkan.

```css
.div4 {
    background-color: blue;
    clear: left;
    float: none;
}
```

![Hasil clearfix dengan clear: left](screenshots/04-clearfix-left.png)

### Eksperimen nilai `clear`

Semua `div` 1-3 mengambang ke **kiri**, sehingga hasilnya bergantung pada sisi yang di-*clear*.

| Nilai | Hasil yang diamati |
|-------|--------------------|
| `left` | `div4` turun ke bawah `div3` karena sisi kiri dibersihkan dari float. |
| `right` | `div4` **tidak turun**. Float yang ada berada di sisi kiri, bukan kanan, sehingga tidak ada yang dibersihkan. Kotak biru tetap sejajar dengan box lain, dan teks "Div 4" bergeser ke kanan karena menghindari float. |
| `both` | `div4` turun ke bawah `div3`, sama seperti `left`, karena kedua sisi dibersihkan. |

**`clear: right`**

![Eksperimen clear: right](screenshots/05-clear-right.png)

**`clear: both`**

![Eksperimen clear: both](screenshots/06-clear-both.png)

---

# Bagian 2: Layout Web Sederhana

Folder: `lab4_layout/` (berisi `home.html` dan `style.css`)

## 2.1 Persiapan file

Membuat folder `lab4_layout`, lalu `home.html` dan `style.css`. CSS dihubungkan dengan:

```html
<link rel="stylesheet" href="style.css">
```

Seluruh isi halaman dibungkus `<div id="container">`.

## 2.2 Kerangka layout dengan semantic elements

Kerangka dibuat dari elemen semantik HTML5: `<header>`, `<nav>`, `<section id="hero">`, `<section id="wrapper">` (berisi `<section id="main">` dan `<aside id="sidebar">`), dan `<footer>`. Belum ada CSS, jadi tampilannya masih bawaan browser.

![Tampilan kerangka layout](screenshots/07-kerangka.png)

## 2.3 Header dan reset CSS

- `* { margin: 0; padding: 0; }` menghapus margin dan padding bawaan browser.
- `#container` berlebar `980px`, rata tengah (`margin: 0 auto`), dengan bayangan tipis.
- `header` diberi `padding: 20px` dan judul berwarna abu-abu.

![Tampilan header](screenshots/08-header.png)

## 2.4 Navigasi

Link navigasi dibuat `inline-block` dengan latar biru. Class `active` dan efek `:hover` memberi warna biru yang lebih terang.

![Tampilan navigasi](screenshots/09-navigasi.png)

## 2.5 Hero panel

Menambahkan judul, paragraf, dan tombol **Learn more** pada `#hero` dengan latar abu-abu muda.

![Tampilan hero panel](screenshots/10-hero.png)

## 2.6 Layout main dan sidebar

`#main` (640px) dan `#sidebar` (260px) sama-sama diberi `float: left` dan `padding: 20px`, sehingga totalnya `640 + 260 + 80 = 980px` dan keduanya berdampingan. Pada langkah ini belum ada perubahan yang terlihat karena isinya masih kosong. Hasilnya terlihat di langkah berikutnya.

```css
#main    { float: left; width: 640px; padding: 20px; }
#sidebar { float: left; width: 260px; padding: 20px; }
```

## 2.7 Sidebar widget

Menambahkan dua `widget-box` ke dalam `<aside>`: satu berisi daftar link dan satu berisi teks. Sidebar tampil di sisi kanan, sedangkan area main masih kosong.

![Tampilan sidebar widget](screenshots/11-widget.png)

## 2.8 Footer

`clear: both` pada `footer` membuat footer turun ke bawah semua elemen yang mengambang (main dan sidebar), sehingga tidak naik ke samping.

```css
footer {
    clear: both;
    background-color: #1d1d1d;
    padding: 20px;
    color: #eee;
}
```

![Tampilan footer](screenshots/12-footer.png)

## 2.9 Elemen lain pada main content

Menambahkan tiga `.box` bergambar bulat di dalam `.row`. Setiap box berlebar `33.333333%` dan di-*float* ke kiri. `.row:after { clear: both; }` (clearfix) menjaga agar tinggi `.row` tetap mengikuti isinya.

![Tampilan content](screenshots/13-content.png)

## 2.10 Content artikel

Menambahkan dua `<article class="entry">` yang dipisahkan `<hr class="divider">`. Artikel pertama memiliki gambar di kiri, sedangkan artikel kedua di kanan (class `right-img` dengan `float: right`).

![Tampilan halaman home lengkap](screenshots/14-artikel.png)

---


# Kesimpulan

_(Tuliskan 2-3 kalimat tentang apa yang kamu pelajari: box element, `float`, `clear`, dan elemen semantik HTML5.)_
