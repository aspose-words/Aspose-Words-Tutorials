---
category: general
date: 2026-08-10
description: Masukkan bentuk persegi panjang di Word menggunakan C#. Pelajari cara
  menyembunyikan bentuk, menyembunyikan bentuk di Word, dan membuat bentuk tersembunyi
  dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: id
lastmod: 2026-08-10
og_description: Masukkan bentuk persegi panjang di Word menggunakan C#. Tutorial ini
  menjelaskan cara menyembunyikan bentuk, menyembunyikan bentuk di Word, dan membuat
  bentuk tersembunyi dengan contoh kode lengkap.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Masukkan bentuk persegi panjang di Word dengan C# – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Menyisipkan bentuk persegi panjang di Word dengan C# – panduan lengkap
url: /id/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyisipkan bentuk persegi panjang di Word dengan C# – panduan lengkap

Jika Anda perlu **menyisipkan bentuk persegi panjang** dalam dokumen Word menggunakan C#, panduan ini menunjukkan langkah‑langkah tepatnya. Anda juga akan belajar **cara menyembunyikan bentuk** agar tidak muncul di file akhir, yang menjawab pertanyaan umum **menyembunyikan bentuk di Word** dan memperlihatkan cara **membuat bentuk tersembunyi** secara programatik.

Tutorial ini mencakup semua hal mulai dari menyiapkan Aspose.Words SDK hingga memverifikasi bahwa bentuk tersebut tersembunyi. Pada akhir artikel Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat ditempatkan di proyek .NET mana pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- .NET 6.0 atau yang lebih baru terpasang (kode juga berfungsi dengan .NET Framework 4.6+)
- Lisensi Aspose.Words for .NET yang valid atau kunci evaluasi sementara
- Visual Studio 2022 (atau IDE apa pun yang mendukung C#)
- Pengetahuan dasar tentang sintaks C# dan Document Object Model (DOM) file Word

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Langkah 1: Buat dokumen kosong baru dan DocumentBuilder

Operasi pertama adalah menginstansiasi objek `Document`. `DocumentBuilder` menyediakan API yang nyaman untuk menyisipkan konten seperti bentuk, paragraf, dan tabel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:** `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menjaga kursor yang melacak di mana elemen berikutnya akan ditempatkan. Menginisialisasi kedua objek merupakan fondasi bagi setiap tugas otomatisasi Word.

## Langkah 2: Sisipkan bentuk persegi panjang

Sekarang Anda menyisipkan persegi panjang. Metode `InsertShape` memerlukan tipe bentuk dan dimensinya dalam poin (1 poin ≈ 1/72 inci). Ukuran **200 × 100 poin** menghasilkan persegi panjang kira‑kira 2,78 × 1,39 inci.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Mengapa ini penting:** Objek `Shape` yang Anda terima dapat dikonfigurasi sepenuhnya—warna, batas, teks, dan visibilitas semuanya dapat diubah sebelum dokumen disimpan.

## Langkah 3: Sembunyikan bentuk

Agar persegi panjang tidak ditampilkan atau dicetak, atur properti `Hidden`‑nya menjadi `true`. Properti ini langsung memetakan ke atribut “Hidden” di Word, yang dihormati Word baik dalam mode tampilan maupun cetak.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Mengapa ini penting:** Menetapkan `Hidden` adalah cara standar untuk **menyembunyikan bentuk di Word** tanpa menghapusnya dari struktur dokumen. Bentuk tetap dapat diakses oleh kode, memungkinkan manipulasi selanjutnya seperti pemformatan bersyarat atau pengaturan visibilitas berbasis data.

## Langkah 4: Simpan dokumen

Terakhir, persistenkan dokumen ke disk. Pilih folder mana saja yang Anda suka; contoh ini menggunakan jalur placeholder yang harus Anda ganti dengan jalur yang sebenarnya.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Mengapa ini penting:** Menyimpan menuntaskan file dan menuliskan flag tersembunyi ke dalam Open XML yang mendasarinya. Saat Anda membuka dokumen di Microsoft Word, persegi panjang akan tidak terlihat, mengonfirmasi bahwa Anda berhasil **membuat bentuk tersembunyi**.

## Langkah 5: Verifikasi bentuk tersembunyi

Buka `HiddenShape.docx` yang dihasilkan di Microsoft Word:

1. Pilih **File → Options → Display** dan pastikan *“Show hidden text”* **tidak dicentang**.  
2. Persegi panjang tidak boleh terlihat di halaman manapun.  
3. Untuk memeriksa kembali, aktifkan *“Show hidden text”*; persegi panjang akan muncul dengan outline titik‑titik samar, membuktikan bahwa bentuk ada tetapi tersembunyi.

Jika persegi panjang masih terlihat, pastikan Anda telah menyimpan file setelah mengatur `Hidden = true` dan bahwa Anda membuka file yang benar.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan langsung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Output yang diharapkan:** Konsol mencetak jalur file dan pengingat singkat. Saat file dibuka di Word, persegi panjang tidak terlihat kecuali teks tersembunyi diaktifkan.

## Pertanyaan umum dan kasus tepi

### Bisakah saya menyembunyikan hanya garis tepi tetapi tetap menampilkan isinya?

Ya. Alih‑alih mengatur `Hidden = true`, Anda dapat mengatur `rectangle.LineFormat.Visible = false` untuk menyembunyikan batas sementara warna isi tetap terlihat. Ini merupakan variasi dari **cara menyembunyikan bentuk** yang mempertahankan sebagian tampilan visual.

### Apakah flag tersembunyi berfungsi di versi Word lama (2003, 2007)?

Atribut tersembunyi merupakan bagian dari spesifikasi Open XML yang diperkenalkan pada Word 2007. Dokumen yang disimpan dalam format biner lama `.doc` tidak akan mempertahankan flag tersebut. Untuk mendukung format legacy, simpan dokumen sebagai `.docx` dan, bila diperlukan, konversi kemudian menggunakan `SaveFormat.Doc` milik Aspose.Words.

### Bagaimana jika saya perlu menyembunyikan beberapa bentuk sekaligus?

Iterasi koleksi `Document.GetChildNodes(NodeType.Shape, true)` dan atur `Hidden = true` pada setiap bentuk yang memenuhi kriteria Anda (misalnya, `ShapeType` tertentu atau nilai `AlternativeText` khusus).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Apakah ada dampak kinerja saat menyembunyikan bentuk?

Flag tersembunyi menambahkan atribut XML yang sangat kecil; tidak memengaruhi kecepatan rendering. Namun, sejumlah besar objek tersembunyi dapat meningkatkan ukuran file secara marginal. Hapus bentuk yang tidak pernah Anda perlukan untuk menjaga dokumen tetap ringan.

## Tips dan praktik terbaik

- **Berikan nama yang bermakna** pada bentuk dengan `rectangle.Name = "MyHiddenRectangle"`; ini membantu ketika Anda nanti mencari bentuk di DOM.
- **Atur `AlternativeText`** ke tag khusus (misalnya, `"HiddenShape"`). Ini memungkinkan Anda menemukan bentuk tanpa bergantung pada indeksnya.
- **Bungkus kode dalam blok try‑catch** untuk menangani kesalahan lisensi atau pengecualian I/O secara elegan.
- **Dispose objek Document** setelah menyimpan jika Anda memproses banyak file dalam loop untuk membebaskan sumber daya tak terkelola: `document.Dispose();`.

## Kesimpulan

Anda kini tahu cara **menyisipkan bentuk persegi panjang** dalam dokumen Word dengan C#, cara **menyembunyikan bentuk di Word**, dan cara **membuat bentuk tersembunyi** yang tetap menjadi bagian dari struktur dokumen namun tidak terlihat oleh pengguna akhir. Contoh lengkap yang dapat dijalankan memperlihatkan seluruh alur kerja, mulai dari pembuatan dokumen hingga verifikasi.

Selanjutnya, Anda dapat mengeksplorasi **cara menyembunyikan bentuk** berdasarkan input pengguna, atau menggabungkan bentuk tersembunyi dengan kontrol konten untuk pembuatan dokumen dinamis. Teknik yang sama juga dapat diterapkan pada tipe bentuk lain seperti elips, panah, atau gambar khusus.

Jangan ragu bereksperimen dengan dimensi, warna, dan pengaturan visibilitas yang berbeda. Jika Anda menemui masalah, tinjau kembali langkah‑langkah di atas atau konsultasikan dokumentasi Aspose.Words untuk detail API yang lebih mendalam. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan langkah‑per‑langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan pada Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}