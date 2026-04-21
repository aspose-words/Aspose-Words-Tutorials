---
category: general
date: 2026-04-21
description: Buat dokumen Word dengan persegi panjang bergaya dan bayangan. Pelajari
  cara menambahkan bayangan, menyisipkan bentuk persegi panjang, mengatur warna bayangan,
  dan lainnya dalam C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: id
og_description: Buat dokumen Word dan tambahkan bentuk persegi panjang berbayangan
  di C#. Ikuti panduan ini untuk mengatur warna bayangan, blur, dan offset dengan
  mudah.
og_title: Buat Dokumen Word dengan Persegi Panjang Berbayang – Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat Dokumen Word dengan Persegi Panjang Berbayang – Panduan Lengkap
url: /id/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word dengan Persegi Panjang Berbayang – Panduan Lengkap

Pernah membutuhkan untuk **create word document** yang terlihat lebih halus dibandingkan halaman teks biasa? Mungkin Anda sedang membuat templat laporan atau selebaran dan sebuah persegi panjang sederhana dengan bayangan halus akan menyelesaikannya. Dalam tutorial ini kami akan membahas langkah demi langkah—cara menyisipkan bentuk persegi panjang, mengaktifkan bayangan, dan menyesuaikan warnanya, blur, serta offset—semua dengan C# dan Aspose.Words.

Kami juga akan membahas **how to add shadow** dengan cara yang berfungsi baik Anda menargetkan Word 2016, 2019, atau build terbaru Office 365. Pada akhir tutorial Anda akan memiliki file *.docx* siap‑simpan yang menampilkan persegi panjang berbayang dengan baik, dan Anda akan memahami “mengapa” di balik setiap properti yang Anda atur.

## Prasyarat

- .NET 6 (atau versi .NET Framework terbaru apa pun)  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)  
- Familiaritas dasar dengan sintaks C#  
- IDE seperti Visual Studio (tapi editor apa pun juga dapat digunakan)

Tidak diperlukan pustaka tambahan; semua yang lain berada di dalam Aspose.Words.

## Langkah 1 – Inisialisasi Dokumen dan Builder (Create Word Document)

Untuk **create word document** secara programatis Anda memulai dengan kelas `Document`. `DocumentBuilder` adalah kuas Anda; ia memungkinkan Anda menambahkan teks, bentuk, dan elemen lainnya.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting:* Objek `Document` mewakili seluruh file .docx. Tanpa itu Anda tidak memiliki tempat untuk menempelkan persegi panjang atau bayangannya.

## Langkah 2 – Sisipkan Bentuk Persegi Panjang (Insert Rectangle Shape)

Sekarang kita benar‑benarnya **insert rectangle shape**. Metode `InsertShape` menerima enum `ShapeType`, serta lebar dan tinggi dalam satuan poin.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Tips pro:* 1 poin ≈ 1/72 inci, jadi 200 pts kira‑kira 2,78 inci lebar. Sesuaikan angka‑angka ini agar cocok dengan tata letak Anda.

## Langkah 3 – Aktifkan Bayangan (How to Add Shadow)

Bayangan dinonaktifkan secara default. Ubah flag `Visible` untuk mengaktifkannya.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Apa yang terjadi?* Ketika `Visible` bernilai true, Word akan merender drop‑shadow berdasarkan properti lain yang Anda atur selanjutnya.

## Langkah 4 – Sesuaikan Penampilan Bayangan (Set Shadow Color, Blur, Offsets)

Di sinilah Anda **set shadow color**, radius blur, dan offset X/Y. Silakan bereksperimen—nilai yang berbeda memberikan cahaya lembut, bayangan dalam, atau bahkan efek “mengapung”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Mengapa angka‑angka ini?* Blur sebesar 5 pts memberikan tepi yang lembut, sementara offset 4 pts menggeser bayangan ke kanan‑bawah, meniru sumber cahaya dari kiri‑atas. Ubah `Color` menjadi `Color.Black` untuk kontras yang lebih kuat, atau gunakan `Color.FromArgb(128, 0, 0, 0)` untuk hitam semi‑transparan.

### Kasus Tepi & Variasi

- **No blur:** Setel `Blur = 0` untuk bayangan tajam dengan tepi keras.  
- **Negative offsets:** Gunakan `OffsetX = -4` untuk menggeser bayangan ke kiri.  
- **Different shapes:** Properti bayangan yang sama bekerja untuk lingkaran, segitiga, atau bahkan bentuk gambar bebas—cukup ubah `ShapeType` pada Langkah 2.  
- **Compatibility:** Aspose.Words menulis data bayangan dalam format Office Open XML, yang berfungsi di Word 2010‑2021 dan Office 365.

## Langkah 5 – Simpan Dokumen (Create Word Document)

Akhirnya, simpan file ke disk. Anda dapat memilih format apa pun yang didukung (`.docx`, `.pdf`, `.odt`, …) tetapi untuk panduan ini kami akan tetap menggunakan format Word klasik.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Saat Anda membuka **ShadowRectangle.docx** di Microsoft Word, Anda akan melihat persegi panjang abu‑abu dengan bayangan halus yang blur dan offset ke kanan‑bawah—tepat seperti yang kami skrip.

### Output yang Diharapkan

- File *.docx* satu halaman.  
- Persegi panjang 200 pt × 100 pt yang terpusat di lokasi kursor saat `InsertShape` dipanggil.  
- Bayangan abu‑abu yang muncul 4 pts ke kanan dan 4 pts ke bawah, dengan blur 5 pt.

Jika bentuk terlihat tidak terpusat, Anda dapat memindahkan kursor dengan `builder.MoveTo` sebelum menyisipkan, atau menyesuaikan properti `Left` dan `Top` pada bentuk setelah penyisipan.

## Pertanyaan Umum & Pemecahan Masalah

**Q: Bayangan tidak muncul di Word.**  
A: Pastikan `ShadowFormat.Visible` bernilai `true`. Juga pastikan Anda menggunakan versi terbaru Aspose.Words (fitur bayangan ditambahkan pada versi 20.3).  

**Q: Bisakah saya menerapkan gradien pada bayangan?**  
A: Tidak secara langsung melalui `ShadowFormat`. UI Word mendukung bayangan gradien, tetapi skema Open XML (yang diikuti Aspose.Words) hanya menyediakan bayangan berwarna solid. Anda harus mengedit XML dasar secara manual—skenario yang lebih lanjutan.  

**Q: Bagaimana jika saya membutuhkan persegi panjang transparan dengan hanya bayangan?**  
A: Setel `rectangle.FillColor = Color.Transparent;` setelah penyisipan. Bayangan tetap akan dirender karena terpisah dari isi.

## Tips Pro untuk Kode Produksi

- **Reuse the builder:** Jika Anda menambahkan banyak bentuk, gunakan instance `DocumentBuilder` yang sama—membuat yang baru untuk setiap bentuk menambah beban yang tidak perlu.  
- **Batch saves:** Simpan sekali setelah semua modifikasi; I/O yang sering memperlambat pembuatan dokumen besar.  
- **Error handling:** Bungkus seluruh blok dalam `try / catch` dan catat pengecualian `Aspose.Words`; biasanya berisi nomor baris yang membantu jika templat dokumen rusak.

## Langkah Selanjutnya (Topik Terkait)

- **How to add shadow** ke gambar atau kotak teks (penggunaan `ShadowFormat` serupa).  
- **Insert rectangle shape** di dalam sel tabel untuk styling sel khusus.  
- **Create rectangle in Word** menggunakan XML native Word (bagi yang lebih suka Open XML mentah).  
- **Set shadow color** secara dinamis berdasarkan input pengguna atau warna tema.

Bereksperimenlah dengan warna, radius blur, dan offset yang berbeda—mungkin cahaya biru lembut untuk laporan korporat, atau bayangan hitam dalam untuk selebaran dramatis. Kemungkinannya tak terbatas, dan perubahan kode sangat minimal.

---

### Ringkasan Cepat

- Kami **created a word document** dari awal.  
- Kami **inserted a rectangle shape** dan mengaktifkan bayangannya.  
- Kami **set shadow color**, blur, dan offset untuk mencapai tampilan profesional.  
- Kami menyimpan file, siap untuk didistribusikan.

Sekarang Anda memiliki fondasi yang kuat untuk menambahkan sentuhan visual pada proyek otomatisasi Word apa pun. Punya ide lebih? Tinggalkan komentar, dan mari teruskan diskusinya. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}