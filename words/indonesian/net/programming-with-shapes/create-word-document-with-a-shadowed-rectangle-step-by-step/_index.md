---
category: general
date: 2026-01-13
description: Buat dokumen Word menggunakan Aspose.Words dan pelajari cara menyisipkan
  bentuk persegi panjang, cara menambahkan bayangan, serta menambahkan bayangan pada
  bentuk di C#. Contoh lengkap disertakan.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: id
og_description: Buat dokumen Word dengan Aspose.Words, lihat cara menyisipkan bentuk
  persegi panjang dan cara menambahkan bayangan. Ikuti contoh lengkap C#.
og_title: Buat Dokumen Word dengan Persegi Panjang Berbayang – Tutorial Lengkap
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat Dokumen Word dengan Persegi Panjang Berbayang – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word dengan Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah

Pernahkah Anda perlu **create word document** yang berisi persegi panjang berbayang yang bagus, tetapi tidak yakin harus mulai dari mana? Anda bukan satu‑satunya—banyak pengembang mengalami hal yang sama saat pertama kali bermain dengan Aspose.Words.  

Dalam tutorial ini kami akan membahas semua yang Anda perlukan untuk **create word document** secara programatis, **insert rectangle shape**, dan menunjukkan **how to add shadow** sehingga bentuknya benar‑benar menonjol. Pada akhir tutorial Anda akan memiliki potongan kode C# yang siap dijalankan dan dapat Anda masukkan ke proyek .NET mana pun.

## Apa yang Akan Anda Pelajari

- Kode tepat untuk **how to insert shape** (sebuah persegi panjang) ke dalam file Word.  
- Properti yang harus Anda sesuaikan untuk **add shape shadow** dan mengontrol tampilannya.  
- Cara menyimpan hasil dan memverifikasi bahwa bayangan terlihat.  
- Beberapa tip praktis dan catatan edge‑case yang menghemat sakit kepala Anda nanti.

Tidak diperlukan dokumentasi eksternal—semuanya ada di sini.

## Prasyarat

Sebelum kami menyelam lebih dalam, pastikan Anda memiliki:

1. **.NET 6.0** (atau versi .NET terbaru) terpasang.  
2. **license** untuk Aspose.Words for .NET, atau Anda dapat menggunakan mode evaluasi gratis untuk pengujian.  
3. Lingkungan pengembangan—Visual Studio 2022 sangat cocok, tetapi editor apa pun yang dapat mengompilasi C# juga dapat digunakan.

Itu saja. Tidak ada paket NuGet tambahan selain `Aspose.Words` yang diperlukan.

## Langkah 1 – Siapkan Proyek dan Referensikan Aspose.Words

Pertama, buat aplikasi console baru dan tambahkan paket Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda menggunakan versi percobaan gratis, ingatlah untuk memanggil `License.SetLicense` dengan file lisensi Anda; jika tidak, perpustakaan akan menambahkan watermark.

## Langkah 2 – Inisialisasi Document Builder

Sekarang kami akan memulai proses **create word document** yang sebenarnya. Kelas `Document` memberi kami kanvas kosong, dan `DocumentBuilder` memungkinkan kami menggambar di atasnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Mengapa kita membutuhkan builder? Ia menyembunyikan detail OpenXML tingkat rendah, sehingga Anda dapat fokus pada *apa* yang Anda inginkan bukan pada *bagaimana* file tersebut terstruktur. Ini adalah inti dari **how to insert shape** dengan cepat.

## Langkah 3 – Sisipkan Bentuk Persegi Panjang

Di sinilah kita benar‑benar **insert rectangle shape**. Persegi panjang akan berukuran 150 × 100 poin (sekitar 2 inci × 1,3 inci).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Metode `InsertShape` mengembalikan objek `Shape`, yang dapat kami sesuaikan lebih lanjut. Pada titik ini, persegi panjang hanyalah kotak putih solid—belum ada bayangan.

## Langkah 4 – Cara Menambahkan Bayangan (Add Shape Shadow)

Menambahkan bayangan ternyata sangat sederhana setelah Anda tahu properti mana yang harus diubah. Objek `ShadowFormat` mengontrol visibilitas, warna, blur, offset, dan ukuran.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Blok tersebut menjawab **how to add shadow** dalam bahasa sederhana: aktifkan, pilih warna, sesuaikan transparansi, offset, blur, dan ukuran. Anda dapat bereksperimen dengan angka-angka ini untuk mendapatkan bayangan tebal atau sangat tipis.

### Variasi Umum

- **Different colours:** Gunakan `Color.Black` untuk bayangan klasik, atau `Color.BlueViolet` untuk efek bergaya.  
- **Zero blur:** Atur `BlurRadius = 0` untuk tepi yang tajam.  
- **Larger offsets:** Tingkatkan `OffsetX`/`OffsetY` untuk memindahkan bayangan lebih jauh dari bentuk.

## Langkah 5 – Simpan Dokumen dan Verifikasi

Akhirnya, tulis dokumen ke disk. File akan menjadi `.docx` standar yang dapat dibuka oleh pengolah kata modern mana pun.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Buka *ShadowRectangle.docx* yang dihasilkan di Microsoft Word. Anda akan melihat persegi panjang dengan bayangan abu‑abu lembut yang di‑offset ke kanan‑bawah—tepat seperti yang ditentukan kode.

> **Expected output:** File Word satu halaman yang berisi persegi panjang 150 × 100 poin dengan bayangan abu‑abu 30 % transparan, di‑offset 5 pt, blur 4 pt, dan berukuran 75 % dari bentuk.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Jalankan program (`dotnet run`) dan Anda akan memiliki file Word baru dengan persegi panjang berbayang yang bagus—sempurna untuk laporan, sertifikat, atau petunjuk visual apa pun yang Anda butuhkan.

## Pertanyaan yang Sering Diajukan (FAQs)

**Q: Bisakah saya menyisipkan bentuk lain (elips, bintang) dan tetap menggunakan kode bayangan yang sama?**  
A: Tentu saja. Metode `InsertShape` menerima nilai enum `ShapeType` apa pun. Setelah Anda memiliki instance `Shape`, properti `ShadowFormat` bekerja sama persis, sehingga **how to add shadow** tidak tergantung pada bentuk.

**Q: Bagaimana jika saya membutuhkan bayangan di kedua sisi bentuk?**  
A: Aspose.Words hanya mendukung satu drop shadow per bentuk. Untuk mensimulasikan efek dua sisi, duplikat bentuk, offset masing‑masing salinan secara berbeda, dan atur `ShadowFormat.Visible` pada salah satu menjadi `false` sementara tetap mempertahankan bayangan pada yang lain.

**Q: Apakah ini bekerja pada .NET Framework 4.8?**  
A: Ya. API bersifat versi‑agnostik; cukup referensikan DLL Aspose.Words yang sesuai untuk kerangka kerja target Anda.

## Tips & Jebakan

- **Don’t forget to set `Visible = true`**—properti bayangan akan diabaikan jika tidak.  
- **Transparency values range from 0.0 (opaque) to 1.0 (fully transparent).** Kesalahan umum adalah menggunakan `30` alih‑alih `0.3`.  
- **Saving to a read‑only folder throws an exception.** Pastikan direktori output dapat ditulisi.

## Langkah Selanjutnya

Sekarang Anda sudah mengetahui **how to insert shape**, **add shape shadow**, dan **create word document** dengan Aspose.Words, Anda mungkin ingin menjelajahi:

- Menambahkan **text inside the rectangle** menggunakan `builder.InsertParagraph()` sebelum menyisipkan bentuk.  
- Menerapkan **gradient fills** atau **patterned borders** untuk gaya visual yang lebih kaya.  
- Mengotomatiskan pembuatan beberapa halaman, masing‑masing dengan bentuk berbayang berbeda, untuk membangun laporan dinamis.

Silakan bereksperimen—mengubah warna, blur, atau ukuran bayangan dapat secara dramatis mengubah tampilan dokumen Anda.

---

*Siap menerapkan ini ke produksi? Ambil kode, sesuaikan parameter, dan saksikan file Word Anda mendapatkan sentuhan profesional dalam hitungan detik.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}