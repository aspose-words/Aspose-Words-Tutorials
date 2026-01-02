---
category: general
date: 2026-01-02
description: Buat Dokumen Word dengan bentuk persegi panjang, atur warna isi bentuk,
  dan simpan file docx menggunakan Aspose.Words. Pelajari cara membuat persegi panjang
  dengan bayangan dalam hitungan menit.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: id
og_description: Buat Dokumen Word dengan persegi panjang khusus, atur warna isi, tambahkan
  bayangan, dan simpan sebagai DOCX. Kode lengkap dan penjelasan.
og_title: Buat Dokumen Word dengan Bentuk Persegi Panjang – Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Document Generation
title: Buat Dokumen Word dengan Bentuk Persegi Panjang dan Bayangan – Panduan Lengkap
url: /id/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word dengan Bentuk Persegi Panjang dan Bayangan – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **create word document** yang berisi persegi panjang bergaya rapi? Mungkin Anda membutuhkan placeholder untuk logo, banner berwarna, atau sekadar petunjuk visual dalam laporan. Dalam tutorial ini kami akan **add rectangle shape**, memberi warna isi, menerapkan bayangan halus, dan akhirnya **save docx file** – semuanya dengan Aspose.Words untuk .NET.

Anda akan mendapatkan cuplikan C# yang siap dijalankan, penjelasan jelas untuk setiap baris, dan beberapa tip yang dapat Anda gunakan kembali dalam proyek Anda. Tanpa basa‑basi, hanya solusi praktis yang dapat Anda salin‑tempel.

## Apa yang Anda Butuhkan

- .NET 6 atau lebih baru (kode ini juga bekerja pada .NET Framework)  
- Visual Studio 2022 (atau editor apa pun yang Anda suka)  
- **Aspose.Words** paket NuGet (`Install-Package Aspose.Words`)  

Jika Anda sudah memiliki semuanya, bagus – mari kita mulai.

## Langkah 1 – Inisialisasi Dokumen Baru (How to create word document)

Hal pertama yang harus Anda lakukan adalah **create word document** dalam memori. Anggaplah ini seperti membuka kanvas kosong di mana Anda nanti akan menggambar persegi panjang Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Mengapa ini penting:** `Document` mewakili seluruh file DOCX, sementara `DocumentBuilder` adalah pembantu yang memudahkan Anda menyisipkan teks, tabel, gambar, dan bentuk tanpa harus menangani pohon node secara manual.

## Langkah 2 – Sisipkan Bentuk Persegi Panjang (Add rectangle shape)

Sekarang kami akan **add rectangle shape** ke dokumen. Metode `InsertShape` menerima tipe bentuk dan dimensinya dalam poin (1 poin = 1/72 inci).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tip:** Jika Anda pernah perlu membuat geometri berbeda (ellipse, triangle, dll.), cukup ubah `ShapeType.Rectangle` ke nilai enum yang diinginkan.

## Langkah 3 – Konfigurasikan Bayangan (Set shape fill color & shadow)

Bayangan dapat membuat bentuk datar terasa lebih tiga dimensi. Di sini kami mengaktifkan bayangan dan menyesuaikan tampilannya.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Mengapa nilai‑nilai ini?** Radius blur yang sedang dan jarak 5‑point menjaga bayangan tidak menguasai bentuk, sementara 45° meniru sumber cahaya yang datang dari atas‑kiri – konvensi UI yang umum.

## Langkah 4 – Simpan Dokumen (Save docx file)

Akhirnya, kami **save docx file** ke disk. Sesuaikan path dengan lingkungan Anda.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Saat Anda membuka `ShadowDemo.docx` di Word, Anda akan melihat persegi panjang berwarna biru muda dengan bayangan abu‑abu lembut, persis seperti tangkapan layar di bawah.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Image alt text:* **Create Word Document** menampilkan bentuk persegi panjang dengan bayangan.

## Contoh Lengkap, Siap‑Jalankan (How to create rectangle and save)

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin ke aplikasi console:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Hasil yang Diharapkan

- Sebuah file bernama **ShadowDemo.docx** muncul di folder target.  
- Membukanya di Microsoft Word menampilkan satu halaman dengan teks “Shadow Demo” diikuti oleh persegi panjang berwarna biru muda.  
- Persegi panjang tersebut memancarkan bayangan abu‑abu lembut pada sudut 45°, memberikan kesan 3‑D ringan.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan ukuran berbeda?

Cukup ubah argumen `200, 100` di `InsertShape`. Angka‑angka tersebut adalah lebar dan tinggi dalam poin. Untuk membuat kotak, gunakan nilai yang sama.

### Bisakah saya membuat bayangan lebih menonjol?

Tingkatkan `BlurRadius` untuk tepi yang lebih halus, naikkan `Distance` untuk offset yang lebih besar, atau turunkan `Transparency` (misalnya, `0.1`) agar bayangan menjadi lebih gelap.

### Bagaimana cara menambahkan border di sekitar persegi panjang?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Apakah ini kompatibel dengan versi lama Aspose.Words?

Ya. Kelas `ShadowFormat` telah ada sejak rilis awal 2020. Jika Anda menggunakan versi yang sangat lama, Anda mungkin perlu memperbarui untuk mengakses semua properti.

## Tips & Perangkap

- **Pro tip:** Selalu dispose dokumen besar (`doc.Dispose()`) setelah selesai, terutama pada aplikasi web, untuk membebaskan sumber daya native.  
- **Watch out for:** Menggunakan path relatif tanpa izin yang tepat dapat menyebabkan `UnauthorizedAccessException`. Lebih baik gunakan path absolut atau pastikan app pool memiliki akses menulis.  
- **Remember:** Properti `FillColor` menerima `System.Drawing.Color` apa pun. Silakan gunakan `Color.FromArgb(255, 173, 216, 230)` untuk nuansa pastel khusus.

## Langkah Selanjutnya

Sekarang Anda sudah tahu cara **create word document**, **add rectangle shape**, **set shape fill color**, dan **save docx file**, Anda dapat bereksperimen lebih lanjut:

- Sisipkan beberapa bentuk dan atur posisinya dengan `RelativeHorizontalPosition` dan `RelativeVerticalPosition`.  
- Gabungkan persegi panjang dengan teks menggunakan `Shape.TextBox` untuk keterangan.  
- Ekspor dokumen yang sama ke PDF (`doc.Save("output.pdf")`) untuk distribusi.

Jika Anda penasaran tentang grafis yang lebih canggih, lihat dukungan Aspose.Words untuk **WordArt**, **charts**, dan **inline images**. Masing‑masing mengikuti pola yang sama: buat node, konfigurasikan propertinya, dan simpan.

---

### TL;DR

- Gunakan `Document` dan `DocumentBuilder` untuk **create word document**.  
- Panggil `InsertShape(ShapeType.Rectangle, …)` untuk **add rectangle shape**.  
- Atur `FillColor` untuk latar belakang yang diinginkan.  
- Aktifkan `ShadowFormat` dan sesuaikan propertinya untuk tampilan yang halus.  
- Selesaikan dengan `document.Save("yourPath.docx")` untuk **save docx file**.

Selamat coding, dan nikmati membuat file Word Anda terlihat lebih bergaya!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}