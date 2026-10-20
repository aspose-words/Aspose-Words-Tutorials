---
category: general
date: 2026-04-04
description: Buat bentuk persegi panjang di C# dengan Aspose.Words dan pelajari cara
  menambahkan bayangan, menerapkan blur pada bayangan, serta membuat bayangan menjadi
  transparan – panduan langkah demi langkah.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: id
og_description: Buat bentuk persegi panjang di C# dengan Aspose.Words. Pelajari cara
  menambahkan bayangan, menerapkan blur pada bayangan, dan membuat bayangan menjadi
  transparan dalam tutorial singkat.
og_title: Buat bentuk persegi panjang dan cara menambahkan bayangan di C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat bentuk persegi panjang dan cara menambahkan bayangan di C#
url: /id/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang dan menambahkan bayangan di C#

Pernah perlu **membuat bentuk persegi panjang** dalam dokumen Word tetapi tidak yakin cara memberi bayangan tipis? Anda tidak sendirian. Dalam banyak skenario pelaporan atau branding, persegi panjang sederhana dengan bayangan semi‑transparan yang lembut dapat membuat tata letak terasa lebih halus tanpa banyak usaha.

Dalam tutorial ini kami akan menjelaskan **cara membuat dokumen** menggunakan Aspose.Words, kemudian menunjukkan **cara menambahkan bayangan**, **menerapkan blur pada bayangan**, dan bahkan **membuat bayangan transparan**. Pada akhir tutorial Anda akan memiliki potongan kode C# yang siap dijalankan dan menghasilkan file *.docx* dengan persegi panjang berbayangan yang bagus—semua dalam beberapa menit.

## Apa yang Anda perlukan

- .NET 6 atau lebih baru (API juga bekerja dengan .NET Framework 4.6+)
- Aspose.Words untuk .NET (versi percobaan gratis cukup untuk contoh ini)
- Editor kode – Visual Studio, VS Code, Rider, atau apa saja yang Anda suka
- Pengetahuan dasar C# – tidak perlu hal yang rumit, cukup kemampuan menjalankan aplikasi console

Jika Anda sudah memiliki semua itu, kita bisa langsung masuk ke solusi.

## Langkah 1 – Cara membuat dokumen dan menginisialisasi kanvas

Hal pertama: Anda memerlukan objek `Document` kosong. Anggap saja ini seperti selembar kertas kosong yang nanti akan diubah Aspose.Words menjadi file Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Mengapa kita menginstansiasi `Document` alih‑alih memuat templat? Memulai dari nol menjamin tidak ada gaya atau bagian tersembunyi yang mengganggu persegi panjang kita. Ini juga membuat ukuran file tetap kecil – kebiasaan yang baik ketika Anda menghasilkan banyak dokumen dalam loop.

## Langkah 2 – Membuat bentuk persegi panjang (inti dari kata kunci utama kami)

Sekarang kita **membuat bentuk persegi panjang**. Kelas `Shape` fleksibel; Anda memberi tahu tipe (Rectangle), ukuran, dan cara pembungkusannya dengan teks di sekitarnya.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Perhatikan penggunaan sintaks inisialisasi objek – singkat dan mengurangi kemungkinan lupa mengatur properti nanti. Persegi panjang akan berada di dalam paragraf pertama, yang akan kita tambahkan pada langkah berikutnya.

## Langkah 3 – Cara menambahkan bayangan dan menyesuaikan tampilannya

Menambahkan bayangan bukan hanya satu baris kode; ada beberapa properti yang dapat diatur. Di sinilah kata kunci sekunder **apply blur to shadow** dan **make shadow transparent** berperan.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Catatan cepat tentang angka: `BlurRadius` sebesar 5 memberikan efek lembut; tingkatkan menjadi 10 untuk tampilan lebih halus, atau turunkan menjadi 2 untuk tepi yang tajam. Nilai `Transparency` berkisar antara 0 (tidak tembus) hingga 1 (tidak terlihat). Sesuaikan sesuai kebutuhan kontras merek Anda.

### Pro tip

Jika Anda membutuhkan bayangan berwarna (misalnya biru korporat), cukup ganti `Color.DarkGray` dengan `Color.FromArgb(80, 0, 120, 215)`. Argumen pertama adalah kanal alfa – pertahankan rendah untuk kesan halus.

## Langkah 4 – Menyisipkan bentuk ke dalam dokumen

Setelah persegi panjang dan bayangannya siap, kita tempatkan ke dalam paragraf pertama dokumen. Langkah ini memastikan bentuk muncul di bagian paling atas file.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Mengapa paragraf pertama? Itu adalah nilai default yang aman dan berfungsi bahkan ketika dokumen benar‑benar kosong. Jika Anda memiliki lokasi spesifik (misalnya setelah heading), Anda dapat menemukan node tersebut dan menyisipkan bentuk di sana.

## Langkah 5 – Menyimpan file dan memverifikasi hasilnya

Akhirnya, kita menyimpan dokumen ke disk. Anda dapat memilih jalur apa saja; pastikan foldernya sudah ada.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Saat Anda membuka *ShadowRectangle.docx* di Microsoft Word, Anda akan melihat persegi panjang 200 × 100 point dengan bayangan berwarna abu‑abu gelap, sedikit blur, transparansi 30 %, dan offset tiga point ke kanan serta ke bawah. Efeknya halus namun menambah kedalaman pada tata letak yang semula datar.

![membuat bentuk persegi panjang dengan bayangan di Aspose.Words](https://example.com/placeholder-image.png "membuat bentuk persegi panjang dengan bayangan di Aspose.Words")

*Teks alt gambar:* **membuat bentuk persegi panjang dengan bayangan di Aspose.Words** – gambar menunjukkan dokumen akhir dengan persegi panjang berbayangan.

## Variasi umum dan kasus tepi

### Mengubah warna bayangan secara dinamis

Jika aplikasi Anda mendukung tema, Anda dapat mengambil warna bayangan dari file konfigurasi:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Membuat bentuk non‑inline

Kadang‑kadang Anda ingin persegi panjang mengambang di atas teks. Ganti `WrapType` menjadi `WrapType.Square` dan atur `RelativeHorizontalPosition` ke `RelativeHorizontalPosition.Margin` untuk kontrol lebih.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Menangani banyak halaman

Jika Anda memerlukan persegi panjang pada setiap halaman, lakukan loop melalui `doc.Sections` dan tambahkan bentuk yang dikloning ke paragraf pertama setiap section. Ingat untuk memanggil `rect.Clone(true)` agar pengaturan bayangan juga diduplikasi.

## Ringkasan – Apa yang telah kami capai

- **Membuat bentuk persegi panjang** menggunakan Aspose.Words
- **Cara menambahkan bayangan** dengan warna, offset, blur, dan transparansi
- Menunjukkan **apply blur to shadow** dan **make shadow transparent**
- Menyimpan file Word yang dapat langsung Anda buka

Semua ini dicapai dengan hanya beberapa baris kode, membuktikan bahwa penyesuaian visual yang canggih tidak selalu memerlukan pustaka grafis berat.

## Apa selanjutnya?

- Bereksperimen dengan `ShapeType` lain (Ellipse, Cloud, dll.) dan lihat bagaimana bayangan berperilaku.
- Gabungkan persegi panjang dengan kotak teks untuk membuat label call‑out.
- Selami **cara membuat dokumen** templat yang sudah berisi placeholder untuk bentuk, lalu isi secara programatis.

Silakan sesuaikan radius blur, warna, atau transparansi hingga bayangan terlihat tepat untuk bahasa desain Anda. API ini bersahabat, dan perubahan terlihat langsung saat Anda menjalankan kembali aplikasi console.

Selamat coding, semoga dokumen Anda selalu memiliki sentuhan kedalaman ekstra!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}