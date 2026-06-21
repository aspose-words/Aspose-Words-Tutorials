---
category: general
date: 2026-06-20
description: Tambahkan bayangan ke bentuk dengan cepat dan pelajari cara mengubah
  transparansi bayangan, menambahkan bayangan bentuk, serta menerapkan bayangan blur
  menggunakan Aspose.Words untuk .NET.
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: id
og_description: Tambahkan bayangan ke bentuk dalam file Word, lihat cara mengubah
  transparansi bayangan, tambahkan bayangan bentuk, dan terapkan bayangan blur dengan
  contoh kode yang jelas.
og_title: Tambahkan Bayangan pada Bentuk – Tutorial C# Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: Tambahkan Bayangan pada Bentuk di Dokumen Word – Panduan Lengkap C#
url: /id/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Bayangan ke Bentuk dalam Dokumen Word – Panduan Lengkap C#

Pernah bertanya-tanya bagaimana **menambahkan bayangan ke bentuk** dalam file Word tanpa harus mengutak‑atik UI? Anda tidak sendirian. Banyak pengembang perlu meningkatkan estetika dokumen secara programatis, dan kabar baiknya adalah Aspose.Words membuatnya sangat mudah.

Dalam tutorial ini kami akan menelusuri langkah‑langkah tepat untuk **menambahkan bayangan ke bentuk**, menunjukkan **cara mengubah transparansi bayangan**, membahas **cara menambahkan bayangan pada bentuk** dalam berbagai skenario, dan bahkan menjelaskan **cara menerapkan bayangan blur** untuk efek kedalaman profesional. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali di proyek .NET mana pun.

## Apa yang Akan Anda Pelajari

- Memuat DOCX, menemukan sebuah bentuk, dan mengonfigurasi properti bayangannya.
- Menyesuaikan opasitas bayangan dengan `Transparency`.
- Menerapkan blur dan offset untuk menciptakan bayangan jatuh yang realistis.
- Menyimpan dokumen yang telah diubah dan memverifikasi hasilnya.
- Tips untuk menangani banyak bentuk, tipe bentuk yang berbeda, dan kasus tepi.

> **Prasyarat:** .NET 6 atau lebih baru, Aspose.Words untuk .NET (paket NuGet `Aspose.Words`), dan pemahaman dasar tentang C#. Tidak diperlukan alat UI.

![add shadow to shape example](image.png){ alt="contoh menambahkan bayangan ke bentuk" }

## Langkah 1: Siapkan Proyek Anda dan Muat Dokumen

Sebelum Anda dapat **menambahkan bayangan ke bentuk**, Anda memerlukan objek dokumen untuk bekerja. Langkah ini sederhana namun penting—tanpa memuat file, tidak ada yang dapat dimodifikasi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*Mengapa ini penting:*  
`Document` adalah titik masuk untuk semua operasi Aspose.Words. Dengan memuat file di awal, Anda memastikan bahwa manipulasi bentuk selanjutnya bekerja pada pohon node yang tepat.

## Langkah 2: Dapatkan Bentuk Target

Sekarang dokumen sudah berada di memori, kita perlu menemukan bentuk yang ingin ditingkatkan. Jika Anda memiliki banyak bentuk, Anda dapat menyesuaikan indeks atau menggunakan selector yang lebih canggih.

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **Tip:** Gunakan `document.GetChild(NodeType.Shape, index, true)` untuk mencari secara rekursif. Jika Anda memerlukan bentuk tertentu berdasarkan nama, periksa `targetShape.Name`.

## Langkah 3: Aktifkan Bayangan dan Atur Warna Dasarnya

Bayangan tidak akan muncul kecuali terlihat dan memiliki warna. Mari beri warna abu‑abu gelap yang halus dan cocok untuk latar belakang terang.

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*Penjelasan:*  
Menetapkan `Visible` ke `true` mengaktifkan efek, sementara `Color.DarkGray` memberikan nada netral yang tidak berbenturan dengan kebanyakan tema dokumen.

## Langkah 4: Cara Mengubah Transparansi Bayangan

Transparansi adalah kunci agar bayangan terasa alami. Nilai `0` berarti sepenuhnya opak; `1` berarti sepenuhnya tidak terlihat. Berikut cara **mengubah transparansi bayangan** menjadi 30 %:

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*Mengapa 0.3?*  
Bayangan dengan transparansi 30 % meniru pencahayaan dunia nyata tanpa mengaburkan tepi bentuk. Anda dapat bereksperimen—`0.5` menghasilkan tampilan yang lebih lembut, sementara `0.1` membuat bayangan lebih menonjol.

## Langkah 5: Cara Menerapkan Bayangan Blur untuk Kedalaman

Bayangan dengan tepi tajam terlihat datar. Menambahkan blur memberikan kedalaman. Di sinilah kami menjawab **cara menerapkan bayangan blur** dalam kode.

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*Apa yang terjadi?*  
`BlurRadius` melunakkan tepi, sementara `OffsetX/Y` memposisikan bayangan seolah sumber cahaya berada di atas‑kiri. Sesuaikan angka‑angka ini agar cocok dengan bahasa desain Anda.

## Langkah 6: Cara Menambahkan Bayangan Bentuk ke Beberapa Bentuk (Opsional)

Jika dokumen Anda berisi beberapa bentuk, Anda mungkin ingin **menambahkan bayangan ke bentuk** pada masing‑masingnya. Loop sederhana dapat menyelesaikannya:

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*Pro tip:*  
Jika Anda hanya ingin memengaruhi persegi panjang, periksa `shape.ShapeType == ShapeType.Rectangle` di dalam loop.

## Langkah 7: Simpan Dokumen yang Telah Dimodifikasi

Semua pekerjaan berat telah selesai—sekarang persistenkan perubahan. Anda dapat menimpa file asli atau menulis ke lokasi baru.

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

Saat Anda membuka `output.docx` di Word, Anda akan melihat persegi panjang (atau bentuk apa pun yang Anda targetkan) menampilkan bayangan halus, semi‑transparan, dan blur.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika bentuk tidak memiliki objek bayangan yang ada?
Aspose.Words secara otomatis membuat objek `Shadow` ketika Anda pertama kali mengakses `targetShape.Shadow`. Tidak diperlukan inisialisasi tambahan.

### Apakah ini bekerja dengan tipe bentuk lain, seperti lingkaran atau gambar?
Tentu saja. API bayangan bersifat agnostik terhadap bentuk. Cukup dapatkan node `Shape` yang sesuai, dan properti yang sama dapat diterapkan.

### Bagaimana cara membuat bayangan tidak terlihat lagi?
Setel `targetShape.Shadow.Visible = false;` atau cukup hilangkan konfigurasi bayangan.

### Kompatibilitas dengan versi .NET yang lebih lama?
Kode ini hanya menggunakan fitur yang tersedia di Aspose.Words 23.x dan .NET Standard 2.0+, sehingga dapat dijalankan pada .NET Framework 4.6.1 dan yang lebih baru.

## Contoh Kerja Lengkap

Berikut program lengkap yang siap dijalankan dan menggabungkan semua langkah:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**Output yang diharapkan:** Buka `output.docx` dan Anda akan melihat persegi panjang asli kini ditampilkan dengan bayangan abu‑abu gelap, 30 % transparan, blur, dan sedikit bergeser ke kanan‑bawah.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **menambahkan bayangan ke bentuk** secara programatis, mulai dari memuat file hingga menyesuaikan transparansi dan blur. Sekarang Anda tahu **cara mengubah transparansi bayangan**, **cara menambahkan bayangan ke bentuk** pada banyak elemen, dan **cara menerapkan bayangan blur** untuk tampilan yang halus.

Siap untuk langkah berikutnya? Cobalah bereksperimen dengan:

- Warna bayangan berbeda (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) untuk efek yang lebih gelap.
- Offset dinamis berdasarkan ukuran bentuk untuk mempertahankan proporsi.
- Menggabungkan bayangan dengan gradien atau refleksi untuk styling tingkat lanjut.

Jangan ragu meninggalkan komentar jika Anda mengalami kendala, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Tutorial Bayangan Bentuk Aspose.Words – Menambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tambahkan Bentuk Grup](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}