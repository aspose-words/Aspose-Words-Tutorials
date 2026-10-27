---
category: general
date: 2026-10-26
description: Buat dokumen Word kosong dengan C# dan pelajari cara menyisipkan bentuk
  grup, lalu tambahkan bentuk persegi panjang ke dalam grup. Panduan ini mencakup
  cara mengelompokkan beberapa bentuk langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: id
lastmod: 2026-10-26
og_description: Buat dokumen Word kosong dengan C# dan lihat cara menyisipkan grup,
  kemudian tambahkan bentuk persegi panjang. Kuasai pengelompokan beberapa bentuk
  dengan contoh kode lengkap.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Buat dokumen Word kosong dan grupkan beberapa bentuk – tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat dokumen Word kosong dan mengelompokkan beberapa bentuk
url: /id/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan mengelompokkan beberapa bentuk

Jika Anda perlu **membuat dokumen Word kosong** secara programatis, tutorial ini menunjukkan secara tepat caranya. Anda akan melihat cara menyisipkan bentuk grup, lalu **menambahkan persegi panjang** ke grup tersebut, mencakup alur kerja lengkap dari dokumen kosong hingga gambar yang dikelompokkan.

Bekerja dengan file Word sering berarti mengatur beberapa gambar bersama—bayangkan sebuah diagram yang terdiri dari banyak bentuk. Pada akhir panduan ini Anda akan dapat **mengelompokkan beberapa bentuk**, menyisipkan **bentuk persegi panjang**, dan memahami **cara menyisipkan grup** serta **cara menambahkan persegi panjang** dengan cara yang bersih dan dapat digunakan kembali.

## Apa yang Anda butuhkan

* .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+)
* **Aspose.Words for .NET** paket NuGet (`Install-Package Aspose.Words`)
* Pemahaman dasar tentang C# dan IDE Visual Studio (semua IDE dapat digunakan)

> **Tips profesional:** Aspose.Words berjalan sepenuhnya offline; Anda tidak memerlukan koneksi internet setelah paket diinstal.

## Langkah 1: Membuat dokumen Word kosong

Operasi pertama adalah menginstansiasi objek `Document` yang kosong. Objek ini mewakili **dokumen Word kosong** yang nantinya akan Anda tambahkan bentuk-bentuk.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* Sebuah `Document` tanpa bagian atau paragraf apa pun tetap merupakan file .docx yang valid. Memulai dari lembar kosong menjamin tidak ada format tersembunyi yang mengganggu bentuk yang akan Anda tambahkan nanti.

## Langkah 2: Menyisipkan bentuk grup (cara menyisipkan grup)

Sebuah **bentuk grup** berfungsi seperti wadah yang dapat menampung objek gambar lainnya. Di Aspose.Words Anda membuatnya dengan `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Mengapa menggunakan grup?* Pengelompokan memungkinkan Anda memindahkan, memutar, atau mengubah ukuran beberapa bentuk sebagai satu unit. Ini penting untuk diagram di mana elemen harus tetap sejajar.

## Langkah 3: Menyisipkan bentuk persegi panjang (menyisipkan bentuk persegi panjang)

Sekarang tambahkan persegi panjang ke dokumen. Metode `InsertShape` mengembalikan objek `Shape` yang kemudian dapat Anda lampirkan ke grup.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Mengapa persegi panjang?* Persegi panjang adalah blok bangunan paling umum untuk diagram alur, mock‑up UI, dan grafik placeholder. Dimensi dinyatakan dalam poin (1 pt ≈ 1/72 inci).

## Langkah 4: Menambahkan persegi panjang ke grup (cara menambahkan persegi panjang)

Sebuah bentuk yang dibuat dengan `InsertShape` berada langsung di badan dokumen. Untuk menjadikannya bagian dari grup, panggil `AppendChild` pada `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Apa yang terjadi di balik layar?* `AppendChild` memindahkan node persegi panjang dari cerita utama dokumen ke dalam koleksi internal grup, mempertahankan ukuran dan posisinya relatif terhadap asal grup.

## Langkah 5: Menyimpan dokumen

Akhirnya, tulis file ke disk. Anda dapat membuka `.docx` yang dihasilkan di Microsoft Word untuk melihat persegi panjang yang dikelompokkan.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Kasus khusus:** Jika Anda berniat menambahkan lebih banyak bentuk (mis., lingkaran, garis) ke grup yang sama, ulangi **Langkah 3** dan **Langkah 4** untuk setiap bentuk baru sebelum menyimpan. Grup akan secara otomatis menyesuaikan kotak pembatasnya untuk mencakup semua anak.

## Cara mengelompokkan beberapa bentuk – memperluas contoh

Berikut adalah cuplikan cepat yang menambahkan bentuk kedua (sebuah elips) ke grup yang sama, menunjukkan **mengelompokkan beberapa bentuk** dalam satu dokumen.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Saat Anda membuka `GroupedShapeExample.docx`, Anda akan melihat persegi panjang dan elips bergerak bersama ketika Anda memilih grup di Word.

## Pertanyaan umum dan pemecahan masalah

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya memerlukan lisensi untuk Aspose.Words?** | Evaluasi gratis berfungsi tanpa lisensi, tetapi menambahkan watermark. Untuk produksi, terapkan lisensi untuk menghapus watermark dan membuka kinerja penuh. |
| **Bisakah saya memposisikan bentuk secara tepat?** | Ya. Setelah menyisipkan sebuah bentuk Anda dapat mengatur properti `Shape.Left`, `Shape.Top`, `Shape.Width`, dan `Shape.Height`. |
| **Bagaimana jika persegi panjang menghilang setelah disimpan?** | Pastikan Anda memanggil `group.AppendChild(rectangle)` *setelah* menyisipkan persegi panjang. Menambahkan bentuk ke badan dokumen terlebih dahulu dan kemudian memindahkannya ke dalam grup diperlukan. |
| **Apakah memungkinkan mengelompokkan bentuk di berbagai bagian?** | Tidak. Semua bentuk dalam sebuah grup harus berada dalam cerita (section) yang sama. Buat grup terpisah per bagian jika diperlukan. |

## Ringkasan

Anda sekarang tahu cara **membuat dokumen Word kosong**, **menyisipkan grup**, **menambahkan persegi panjang**, dan **mengelompokkan beberapa bentuk** menggunakan Aspose.Words untuk .NET. Contoh lengkap yang dapat dijalankan di atas dapat disalin ke dalam aplikasi konsol dan dijalankan segera.

## Langkah Selanjutnya

* Bereksperimen dengan ukuran dan warna **menyisipkan bentuk persegi panjang** (`rectangle.FillColor = Color.LightBlue;`).  
* Jelajahi tipe bentuk lain (`ShapeType.Polygon`, `ShapeType.Line`) untuk memperkaya diagram Anda.  
* Pelajari cara mengonversi `.docx` akhir ke PDF (`doc.Save("output.pdf");`) untuk distribusi.  
* Selami **cara menambahkan persegi panjang** ke dokumen yang sudah ada dan sudah berisi teks—gunakan `DocumentBuilder.MoveTo` untuk menempatkan grup di tempat yang Anda butuhkan.

Silakan sesuaikan kode untuk kebutuhan pelaporan atau pembuatan diagram Anda sendiri. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat dokumen Word kosong dan mengelompokkan bentuk di C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Cara mengelompokkan bentuk di Word dan menambahkan bentuk ke dokumen Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word dengan Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}