---
category: general
date: 2026-11-15
description: Pelajari cara menyisipkan bentuk dalam dokumen Word dan mengelompokkan
  beberapa bentuk dengan Aspose.Words DocumentBuilder. Termasuk contoh menyisipkan
  bentuk persegi panjang dan contoh menyisipkan beberapa bentuk.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: id
lastmod: 2026-11-15
og_description: Cara menyisipkan bentuk dalam file Word menggunakan Aspose.Words.
  Panduan ini mencakup pengelompokan beberapa bentuk, menyisipkan bentuk persegi panjang,
  dan menambahkan beberapa bentuk secara efisien.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Cara menyisipkan bentuk dan mengelompokkan beberapa bentuk dengan DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Cara menyisipkan shape dan mengelompokkan beberapa shape menggunakan DocumentBuilder
  di C#
url: /id/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan shape dan mengelompokkan beberapa shape menggunakan DocumentBuilder di C#

Jika Anda perlu mengetahui **cara menyisipkan shape** ke dalam dokumen Word dengan Aspose.Words, panduan ini menunjukkan langkah‑langkah tepatnya. Anda juga akan belajar cara **mengelompokkan beberapa shape** sehingga mereka berperilaku sebagai satu objek, dan cara **menyisipkan shape persegi panjang** bersama grafik lainnya.

Automasi dokumen sering memerlukan penambahan beberapa grafik—chart, logo, call‑out—sementara tetap terorganisir. Pada akhir tutorial ini Anda akan dapat **menyisipkan beberapa shape**, menempatkannya di dalam sebuah grup, dan menyimpan tata letak yang bersih serta dapat digunakan kembali.

## Prasyarat

* .NET 6.0 atau yang lebih baru terpasang  
* Visual Studio 2022 (atau IDE C# apa pun)  
* Lisensi Aspose.Words untuk .NET atau kunci evaluasi gratis  
* Familiaritas dasar dengan C# dan kelas Aspose.Words `DocumentBuilder`  

Anda **tidak** memerlukan pustaka pihak ketiga lain; semua yang dibutuhkan sudah menjadi bagian dari Aspose.Words.

## Langkah 1: Instal Aspose.Words melalui NuGet

Buka proyek Anda di Visual Studio dan jalankan perintah berikut di Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Paket ini mencakup kelas `DocumentBuilder`, `Shape`, dan `GroupShape` yang digunakan sepanjang tutorial ini.

## Langkah 2: Buat instance DocumentBuilder – fondasi untuk **cara menyisipkan shape**

Baris kode pertama yang dapat dijalankan adalah membuat `DocumentBuilder`. Objek ini memberi Anda akses langsung ke pohon dokumen, memungkinkan Anda menempatkan shape tepat di lokasi yang diinginkan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Mengapa ini penting*: `DocumentBuilder` mempertahankan kursor (“titik sisipan”). Setiap pemanggilan `Insert...` berikutnya menggunakan kursor tersebut, itulah mengapa kita kemudian memindahkannya ke dalam `GroupShape` untuk menjaga semua shape tetap bersama.

## Langkah 3: **Menyisipkan shape persegi panjang** – grafik pertama yang akan Anda tambahkan

Persegi panjang adalah placeholder umum untuk tabel, gambar, atau call‑out. Gunakan `InsertShape` dengan `ShapeType.Rectangle` dan tentukan lebar serta tinggi dalam poin (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Persegi panjang muncul pada lokasi kursor saat ini. Anda dapat menyesuaikan isinya, gaya garis, atau teksnya nanti jika diperlukan.

## Langkah 4: Sisipkan shape lain – sebuah elips untuk variasi visual

Menambahkan lebih dari satu shape menunjukkan **menyisipkan beberapa shape**. Elips akan berada setelah persegi panjang dalam alur dokumen.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Pada titik ini dokumen berisi dua shape independen. Jika Anda memindahkan kursor atau menambahkan teks, shape tetap berada di tempat mereka disisipkan.

## Langkah 5: **Mengelompokkan beberapa shape** sehingga mereka berfungsi sebagai satu unit

Pengelompokan penting ketika Anda perlu memindahkan, memutar, atau memformat beberapa grafik sekaligus. Kode berikut membuat `GroupShape`, memindahkan kursor builder ke dalamnya, dan kemudian menyisipkan kembali shape yang sama—kali ini mereka menjadi anak dari grup.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Mengapa menggunakan grup?

* **Transformasi satu titik** – memutar atau mengubah ukuran seluruh grup dengan satu panggilan.  
* **Organisasi logis** – pohon dokumen Word mencerminkan pengelompokan, memudahkan penyuntingan selanjutnya.  
* **Tata letak konsisten** – memindahkan grup menjaga posisi relatif anak‑anaknya tetap utuh.

### Menambahkan lebih banyak shape – memperluas **menyisipkan beberapa shape** di dalam grup

Anda dapat terus memanggil `InsertShape` sementara kursor tetap berada di dalam `GroupShape`. Misalnya, untuk menambahkan segitiga:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Setiap pemanggilan menghormati konteks grup, sehingga segitiga secara otomatis menjadi bagian dari set grup yang sama.

## Langkah 6: Simpan dokumen dan verifikasi hasilnya

Setelah semua shape ditempatkan, simpan dokumen ke file `.docx`. Membuka file tersebut di Microsoft Word (atau penampil kompatibel lainnya) harus menampilkan dua shape terpisah diikuti oleh satu set grup yang berisi persegi panjang, elips, dan segitiga yang sama.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Output yang diharapkan

* **Dua shape pertama** – sebuah persegi panjang dan sebuah elips yang ditempatkan secara independen di halaman.  
* **Blok grup** – sebuah persegi panjang, sebuah elips, dan sebuah segitiga yang bergerak bersama ketika Anda mengklik salah satunya di Word.

Anda dapat menguji pengelompokan dengan memilih shape apa pun di dalam grup; Word akan menyorot seluruh koleksi, mengonfirmasi bahwa operasi **mengelompokkan beberapa shape** berhasil.

## Kesalahan umum dan tips profesional

| Masalah | Mengapa terjadi | Solusi |
|-------|----------------|-----|
| Shape muncul di luar halaman yang dimaksud | Kursor builder tidak dipindahkan ke dalam `GroupShape` sebelum menyisipkan. | Selalu panggil `builder.MoveTo(group)` **sebelum** pemanggilan `InsertShape` yang termasuk dalam grup. |
| Grup menghilang setelah disimpan | Grup disisipkan tanpa ditambahkan ke koleksi node dokumen. | Gunakan `builder.InsertNode(group)` segera setelah membuat `GroupShape`. |
| Ukuran tidak terduga karena DPI dokumen | Aspose.Words menggunakan poin; jika Anda berpikir dalam piksel, dimensi dapat tidak cocok. | Konversi piksel ke poin (`points = pixels * 72 / 96`) atau bekerja langsung dalam poin. |
| Shape saling tumpang tindih secara tidak sengaja | Tidak ada penempatan eksplisit yang diatur; Word menempatkannya secara berurutan. | Atur `Shape.Left` dan `Shape.Top` setelah penyisipan untuk mengontrol penempatan yang tepat. |

**Tips profesional:** Setelah mengelompokkan, Anda dapat mengambil koleksi `Shapes` grup (`group.Shapes`) untuk iterasi, mengganti nama, atau menerapkan pemformatan massal.

## Langkah 7: Memperluas contoh – apa selanjutnya?

Sekarang Anda sudah mengetahui **cara menyisipkan shape**, **menyisipkan shape persegi panjang**, dan **mengelompokkan beberapa shape**, Anda dapat menjelajahi:

* **Menganimasikan shape yang dikelompokkan** – atur properti rotasi atau flip pada grup.  
* **Menerapkan gaya** – gunakan `Shape.FillColor`, `Shape.LineFormat`, atau `Shape.TextBox` untuk menambahkan label.  
* **Mengekspor ke PDF** – tata letak grup yang sama akan dirender dengan benar ketika Anda memanggil `doc.Save("output.pdf")`.  

Semua ekstensi ini menggunakan kembali alur kerja `DocumentBuilder` yang sama, menjaga kode Anda tetap bersih dan dapat dipelihara.

## Kesimpulan

Tutorial ini menunjukkan **cara menyisipkan shape** ke dalam dokumen Word dengan Aspose.Words, cara **menyisipkan shape persegi panjang**, dan cara **mengelompokkan beberapa shape** sehingga mereka berperilaku sebagai satu objek. Dengan mengikuti kode langkah demi langkah, Anda dapat dengan andal **menyisipkan beberapa shape**, mengatur mereka ke dalam grup, dan menghasilkan dokumen kelas profesional secara programatis.

Jangan ragu bereksperimen dengan berbagai tipe shape, warna, dan transformasi grup. Saat Anda siap, integrasikan pola ini ke dalam solusi pelaporan atau templating yang lebih besar untuk mengotomatisasi tata letak dokumen yang kompleks. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Cara membuat dan menyisipkan shape elips dan persegi panjang di dalam shape grup dalam dokumen Word menggunakan Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Cara mengelompokkan shape dalam dokumen Word menggunakan Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}