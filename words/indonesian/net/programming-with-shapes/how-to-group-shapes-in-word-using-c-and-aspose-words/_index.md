---
category: general
date: 2026-09-30
description: Mengelompokkan bentuk di Word dengan C# – pelajari cara mengelompokkan
  bentuk, menambahkan persegi panjang dan elips, serta menyisipkan bentuk persegi
  panjang ke dokumen Word secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: id
lastmod: 2026-09-30
og_description: Kelompokkan bentuk di Word menggunakan C# dan Aspose.Words. Ikuti
  panduan lengkap ini untuk menambahkan persegi panjang, menambahkan elips, dan pelajari
  cara mengelompokkan bentuk secara efisien.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Mengelompokkan bentuk di Word dengan C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara mengelompokkan bentuk di Word menggunakan C# dan Aspose.Words
url: /id/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word menggunakan C# dan Aspose.Words

Jika Anda perlu **mengelompokkan bentuk di Word** secara programatis, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan melihat cara menambahkan persegi panjang, menambahkan elips, dan kemudian menggabungkannya menjadi satu bentuk grup menggunakan pustaka Aspose.Words untuk .NET.

Bekerja dengan bentuk adalah kebutuhan umum saat menghasilkan laporan, kontrak, atau materi pemasaran secara otomatis. Pada akhir tutorial ini Anda akan memiliki metode C# yang dapat digunakan kembali yang memuat file DOCX, menyisipkan persegi panjang dan elips, mengelompokkannya, dan menyimpan hasilnya—semua tanpa membuka Word secara manual.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Lingkungan pengembangan seperti Visual Studio 2022 (edisi Community sudah cukup)  
* Lisensi Aspose.Words untuk .NET atau salinan evaluasi gratis (API berfungsi tanpa lisensi tetapi menambahkan watermark)  

Anda juga memerlukan dokumen Word sumber (`input.docx`) dalam folder yang dapat direferensikan dari kode. Dokumen dapat kosong; tutorial ini berfokus pada penanganan bentuk.

## Langkah 1: Buat proyek konsol baru dan tambahkan Aspose.Words

Buka terminal atau command prompt Visual Studio dan jalankan:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Perintah ini membuat aplikasi konsol baru bernama **WordShapeDemo** dan menambahkan paket NuGet `Aspose.Words`, yang berisi kelas `Document` dan `DocumentBuilder` yang digunakan untuk memanipulasi file Word.

## Langkah 2: Muat atau buat dokumen

Operasi pertama saat bekerja dengan **bentuk grup di Word** adalah memperoleh objek `Document`. Anda dapat memuat file DOCX yang sudah ada atau memulai dari dokumen kosong.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Kelas `Document` mewakili seluruh file Word. Memuat file memberi Anda kanvas siap untuk menyisipkan bentuk.

## Langkah 3: Mulai bentuk grup

*Group shape* memungkinkan Anda memperlakukan beberapa bentuk independen sebagai satu unit—sempurna untuk memindahkan atau mengubah ukuran mereka secara bersamaan. Untuk memulai grup, panggil `StartGroupShape()` pada `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Memanggil `StartGroupShape` memberi tahu Aspose.Words bahwa setiap penyisipan bentuk berikutnya termasuk dalam grup logis yang sama sampai Anda memanggil `EndGroupShape`.

## Langkah 4: Cara menambahkan bentuk persegi panjang di Word

Setelah grup terbuka, sisipkan persegi panjang. Metode `InsertShape` menerima enum `ShapeType`, diikuti oleh lebar dan tinggi (dalam poin).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Persegi panjang menjadi anggota pertama dalam grup. Anda dapat menyesuaikan isian, garis tepi, atau teksnya nanti jika diperlukan.

## Langkah 5: Cara menambahkan bentuk elips di Word

Selanjutnya, tambahkan elips (lingkaran ketika lebar sama dengan tinggi). Ini menunjukkan **cara menambahkan elips** menggunakan builder yang sama.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Kedua bentuk kini berbagi ruang koordinat yang sama di dalam grup, memudahkan penyelarasan visual.

## Langkah 6: Tutup definisi bentuk grup

Setelah Anda menambahkan semua anggota yang diinginkan, tutup grup. Ini menyelesaikan kumpulan bentuk sehingga Word memperlakukannya sebagai satu objek.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Pada titik ini dokumen berisi satu bentuk grup yang terdiri dari persegi panjang dan elips.

## Langkah 7: Simpan dokumen yang telah dimodifikasi

Terakhir, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Menjalankan program menghasilkan `output.docx`. Buka file tersebut di Microsoft Word, pilih bentuknya, dan Anda akan melihat bahwa persegi panjang serta elips bergerak bersama—bukti bahwa operasi **mengelompokkan bentuk di Word** berhasil.

### Hasil yang diharapkan

* File Word berisi satu objek grup.  
* Memilih grup memungkinkan Anda menyeret, mengubah ukuran, atau memutar kedua persegi panjang dan elips secara bersamaan.  
* Tidak diperlukan interaksi manual dengan Word; semuanya dilakukan melalui kode C#.

![Bentuk grup dalam dokumen Word](grouped-shapes.png "Tangkapan layar dokumen Word yang menampilkan bentuk persegi panjang dan elips yang dikelompokkan")

*Teks alt gambar: “Tangkapan layar dokumen Word yang menampilkan bentuk persegi panjang dan elips yang dikelompokkan”* (memenuhi persyaratan teks alt gambar).

## Mengapa mengelompokkan bentuk penting

Mengelompokkan bentuk lebih dari sekadar kenyamanan visual. Ini memungkinkan Anda untuk:

* **Mempertahankan konsistensi tata letak** – memindahkan grup menjaga posisi relatif tetap utuh.  
* **Menerapkan transformasi sekali saja** – memutar atau menskalakan seluruh grup alih-alih tiap bentuk secara terpisah.  
* **Menyederhanakan pemrosesan lanjutan** – ketika alat lain membaca DOCX, mereka melihat satu bentuk komposit, mengurangi kompleksitas.

Jika Anda pernah perlu menambahkan lebih banyak bentuk (misalnya garis atau kotak teks) ke unit logis yang sama, Anda hanya perlu memanggil `InsertShape` lagi sebelum `EndGroupShape`.

## Variasi umum dan kasus tepi

| Situasi | Cara menanganinya |
|-----------|-----------------|
| **Unit berbeda** – Anda memiliki ukuran dalam sentimeter | Konversi sentimeter ke poin (`1 cm ≈ 28.35 pt`) sebelum memanggil `InsertShape`. |
| **Menambahkan label teks** – Anda ingin keterangan di dalam grup | Sisipkan `ShapeType.TextBox` setelah persegi panjang dan elips, lalu atur properti `Text`. |
| **Menerapkan warna isi** – Anda membutuhkan persegi panjang biru | Setelah `InsertShape`, dapatkan bentuk terakhir melalui `builder.CurrentParagraph.Runs[0].Font` dan set `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Menggunakan format dokumen berbeda** – Anda menargetkan `.doc` alih-alih `.docx` | Kode yang sama tetap berfungsi; cukup ubah ekstensi file saat memanggil `Save`. Aspose.Words secara otomatis menangani formatnya. |

## Tips profesional

* **Gunakan kembali builder** – Anda dapat memulai dan mengakhiri beberapa grup dalam dokumen yang sama; cukup panggil `StartGroupShape` lagi setelah `EndGroupShape`.  
* **Kinerja** – menyisipkan bentuk secara batch di dalam satu blok `StartGroupShape/EndGroupShape` lebih cepat daripada menyisipkan bentuk satu per satu di luar grup.  
* **Lisensi** – lisensi evaluasi menambahkan watermark pada halaman pertama. Pasang lisensi yang tepat untuk menghilangkannya di lingkungan produksi.

## Kesimpulan

Anda kini tahu cara **mengelompokkan bentuk di Word** dengan C#, cara **menambahkan persegi panjang**, cara **menambahkan elips**, dan cara **menyisipkan bentuk persegi panjang** ke dokumen Word menggunakan Aspose.Words. Contoh lengkap yang dapat dijalankan memperlihatkan setiap langkah mulai dari penyiapan proyek hingga menyimpan file akhir.

Dari sini Anda dapat menjelajahi tipe bentuk tambahan, menerapkan styling, atau menggabungkan bentuk grup dengan tabel dan gambar untuk membuat dokumen yang canggih dan dihasilkan secara programatis.

---

**Langkah selanjutnya**

* Pelajari cara **memutar bentuk grup**: gunakan `Shape.RotationAngle` setelah grup ditutup.  
* Jelajahi **kustomisasi isi dan garis tepi** untuk persegi panjang dan elips.  
* Integrasikan logika ini ke dalam API ASP.NET Core untuk menghasilkan laporan sesuai permintaan.  

Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}