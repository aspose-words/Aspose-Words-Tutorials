---
category: general
date: 2026-02-26
description: Buat bentuk persegi panjang di Word menggunakan Aspose.Words dan pelajari
  cara menambahkan bentuk ke Word, menerapkan bayangan pada bentuk, serta mengatur
  transparansi bentuk dalam hitungan menit.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: id
og_description: Buat bentuk persegi panjang di Word menggunakan Aspose.Words. Pelajari
  cara menambahkan bentuk ke Word, menerapkan bayangan pada bentuk, dan mengatur transparansi
  bentuk dengan cepat.
og_title: Buat Bentuk Persegi Panjang di Word – Panduan Lengkap Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Buat Bentuk Persegi Panjang di Word – Panduan Lengkap Aspose.Words
url: /id/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

"Kasus Pinggir yang Perlu Diperhatikan" maybe.

Translate "Frequently Asked Questions" => "Pertanyaan yang Sering Diajukan".

Translate Q/A.

Make sure to keep markdown formatting.

Let's construct final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Bentuk Persegi Panjang di Word – Panduan Lengkap Aspose.Words

Pernah perlu **membuat bentuk persegi panjang** dalam dokumen Word tetapi tidak tahu harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami hal yang sama saat mengotomatisasi laporan atau faktur. Pada tutorial ini kami akan membimbing Anda melalui contoh lengkap yang siap dijalankan, menunjukkan cara **menambahkan shape ke Word**, menerapkan bayangan halus, dan mengontrol transparansi shape, semuanya dengan Aspose.Words untuk .NET.

Pada akhir panduan Anda akan memiliki file `.docx` yang berisi persegi panjang bersih dengan bayangan yang dipoles—sempurna untuk branding, penekanan, atau sekadar membuat dokumen Anda terlihat lebih profesional. Tidak memerlukan alat eksternal, hanya beberapa baris C#.

## Apa yang Anda Butuhkan

- **Aspose.Words untuk .NET** (versi terbaru per awal 2026). Anda dapat mengunduhnya dari NuGet (`Install-Package Aspose.Words`).
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code dengan ekstensi C#).
- Familiaritas dasar dengan sintaks C#—tidak ada yang rumit, hanya pernyataan `using` biasa dan pembuatan objek.

Jika Anda sudah memiliki semua itu, bagus—mari kita mulai.

## Membuat Bentuk Persegi Panjang – Langkah Inti

Berikut adalah kode sumber lengkap. Salin‑tempel ke proyek konsol baru, tekan **F5**, dan Anda akan melihat `ShadowDemo.docx` muncul di folder yang Anda tentukan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Mengapa Ini Berfungsi

- **`Document`** adalah titik masuk; mewakili seluruh file Word.
- **`Shape`** dengan `ShapeType.Rectangle` memberi tahu Aspose bahwa kita menginginkan objek gambar berbentuk persegi panjang.
- Menetapkan **`Width`** dan **`Height`** memberi shape ukuran yang deterministik; jika tidak, akan menjadi placeholder yang sangat kecil.
- Objek **`Shadow`** memungkinkan kita menyesuaikan setiap aspek visual: blur, jarak, arah, warna, transparansi, dan spread. Inilah inti dari *apply shadow to shape*.
- Akhirnya, **`AppendChild`** menyisipkan shape ke paragraf pertama dokumen, cara paling sederhana untuk *add shape to Word* tanpa harus berurusan dengan tabel atau header.

Saat Anda membuka `ShadowDemo.docx`, Anda akan melihat persegi panjang abu‑abu yang duduk nyaman dalam dokumen, bayangannya miring ke kanan‑bawah dengan sudut 45°. Bayangan tersebut bukan blok padat; radius blur melunakkan tepinya, dan transparansi membuatnya tampak seperti bayangan alami, bukan overlay yang keras.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(Gambar di atas menunjukkan hasil akhir dari potongan kode.)*

## Menambahkan Shape ke Dokumen Word – Opsi Penempatan

Contoh ini menggunakan **paragraf pertama** karena itu cara tercepat untuk melihat sesuatu di layar. Dalam skenario dunia nyata Anda mungkin ingin:

- Menyisipkan shape ke **section** atau **header/footer** tertentu.
- Menempatkannya di dalam **sel tabel** untuk penyelarasan dengan data tabular.
- Membungkusnya dengan opsi **text wrapping** (misalnya, `WrapType.Square`) sehingga teks di sekitarnya mengalir di sekitar persegi panjang.

Berikut variasi singkat yang menempatkan shape ke paragraf baru dengan gaya khusus:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Tips profesional:* Selalu tambahkan shape **setelah** Anda mengonfigurasi propertinya; jika tidak, Anda mungkin perlu memanggil `UpdateLayout` untuk menyegarkan tampilan visual.

## Menerapkan Bayangan ke Shape – Penyetelan Tampilan

Bayangan dapat mengubah estetika dokumen secara dramatis. Kelas `Shadow` menyediakan beberapa properti:

| Properti      | Apa yang Dikontrol                                   | Nilai Tipikal |
|---------------|------------------------------------------------------|---------------|
| `BlurRadius`  | Kelembutan tepi bayangan                             | 2.0 – 10.0    |
| `Distance`    | Seberapa jauh bayangan dipindahkan dari shape        | 1.0 – 8.0     |
| `Direction`   | Sudut dalam derajat (0 = kiri, 90 = atas)            | 0 – 360       |
| `Color`       | Warna bayangan (any `System.Drawing.Color`)         | Gray, Black, Custom |
| `Transparency`| Opasitas (0 = sepenuhnya opaque, 1 = tidak terlihat) | 0.0 – 0.5     |
| `Spread`      | Ekspansi bayangan sebelum blur diterapkan            | 0.0 – 1.0     |

Jika Anda menginginkan **tampilan halus dan profesional**, pertahankan `BlurRadius` sekitar 4‑6 dan `Transparency` mendekati 0.2, seperti pada kode di atas. Untuk **efek dramatis**, naikkan `Distance` ke 6, atur `Direction` ke 135°, dan turunkan `Transparency` menjadi 0.05.

## Mengatur Transparansi Shape dan Spread Bayangan

Transparansi tidak hanya berlaku pada bayangan; Anda juga dapat membuat persegi panjang itu sendiri sebagian tembus pandang:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Menggabungkan isian semi‑transparent dengan bayangan lembut sering menghasilkan nuansa UI modern—bagus untuk dasbor atau mock‑up desain yang disematkan dalam laporan.

### Kasus Pinggir yang Perlu Diperhatikan

1. **Versi Word lama** (sebelum 2007) tidak mendukung beberapa properti bayangan. Jika Anda menargetkan file `.doc`, pertimbangkan menyederhanakan bayangan (misalnya, set `BlurRadius` ke 0).
2. **Layar DPI tinggi** dapat menampilkan bayangan sedikit berbeda. Uji pada lingkungan target jika kesetiaan visual sangat penting.
3. **Shape yang saling tumpang tindih**—Aspose merender bayangan sesuai urutan penambahannya. Sisipkan shape dari belakang ke depan untuk menghindari occlusion yang tidak diinginkan.

## Simpan dan Verifikasi Hasil

Metode `Document.Save` secara otomatis mendeteksi format output dari ekstensi file. Untuk file **`.docx`** Anda mendapatkan format Open XML, yang dipahami oleh kebanyakan pengolah Word modern. Jika Anda memerlukan versi **PDF** dengan gaya visual yang sama, cukup ubah ekstensi:

```csharp
document.Save("ShadowDemo.pdf");
```

Membuka `ShadowDemo.docx` (atau `ShadowDemo.pdf`) seharusnya menampilkan **persegi panjang dengan bayangan** yang bersih, mengonfirmasi bahwa Anda telah berhasil *create rectangle shape* dan *apply shadow to shape* menggunakan Aspose.Words.

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menggunakan shape lain, seperti elips?**  
J: Tentu saja. Ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse` (atau enum `ShapeType` lainnya). Properti bayangan tetap sama.

**T: Bagaimana jika saya ingin persegi panjang dapat diklik?**  
J: Anda dapat menambahkan hyperlink ke shape:

```csharp
rectangleShape.Href = "https://example.com";
```

**T: Apakah ini bekerja pada .NET 6+?**  
J: Ya. Aspose.Words 23.11 dan versi lebih baru sepenuhnya mendukung .NET 6, .NET 7, dan .NET 8. Cukup referensikan paket NuGet yang sesuai.

**T: Bagaimana cara mengubah warna bayangan agar sesuai dengan merek saya?**  
J: Gunakan `System.Drawing.Color` apa pun yang Anda suka:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **membuat bentuk persegi panjang** dalam dokumen Word, **menambahkan shape ke Word**, **menerapkan bayangan ke shape**, dan **mengatur transparansi shape**. Kode lengkap yang dapat dijalankan berada di bagian atas halaman ini, dan penjelasannya memberi Anda kepercayaan untuk menyesuaikan ukuran, warna, dan parameter bayangan untuk proyek apa pun.

Siap untuk langkah selanjutnya? Cobalah bereksperimen dengan:

- Beberapa shape yang ditumpuk bersama untuk efek lencana.
- Penentuan ukuran dinamis berdasarkan konten dokumen (misalnya, menghitung lebar dari kolom tabel).
- Mengekspor dokumen ke PDF atau HTML sambil mempertahankan bayangan.

Jangan ragu meninggalkan komentar jika Anda mengalami kendala, atau bagikan variasi Anda sendiri pada tema “persegi panjang dengan bayangan”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}