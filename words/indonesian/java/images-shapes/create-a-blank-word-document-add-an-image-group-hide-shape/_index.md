---
category: general
date: 2026-10-10
description: Buat dokumen Word kosong, sisipkan gambar ke dalam Word, tambahkan grup
  gambar, dan sembunyikan bentuk dalam file yang disimpan. Ikuti panduan langkah demi
  langkah ini.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: id
lastmod: 2026-10-10
og_description: Buat dokumen Word kosong, sisipkan gambar ke dalam Word, tambahkan
  grup gambar, dan sembunyikan bentuk. Panduan ini menunjukkan kode C# lengkap.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Buat dokumen Word kosong, tambahkan grup gambar, sembunyikan bentuk
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Buat dokumen Word kosong, tambahkan grup gambar, sembunyikan bentuk
url: /id/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong, tambahkan grup gambar, sembunyikan bentuk

Jika Anda perlu **membuat dokumen Word kosong** dan kemudian menyembunyikan elemen visual, tutorial ini menunjukkan cara tepatnya. Anda akan belajar cara menyisipkan gambar ke dalam Word, menambahkan grup gambar, dan menyembunyikan bentuk dalam dokumen Word dalam satu rutin C# yang dapat digunakan kembali.

Kami akan menggunakan pustaka Aspose.Words untuk .NET, yang memungkinkan Anda memanipulasi file .docx tanpa harus menginstal Microsoft Word. Pada akhir panduan ini Anda akan memiliki program yang dapat dijalankan yang menghasilkan file Word berisi grup gambar tersembunyi, siap untuk pemrosesan lanjutan atau tampilan bersyarat.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.6+)
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Sebuah folder di disk tempat Anda dapat membaca file gambar dan menulis dokumen output
- Familiaritas dasar dengan C# dan Visual Studio (atau IDE apa pun yang Anda sukai)

## Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah **membuat dokumen Word kosong**. Aspose.Words menyediakan kelas `Document` yang mewakili file Word dalam memori. Membuat instance tanpa argumen memberi Anda dokumen kosong yang siap diisi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* Memulai dengan dokumen kosong memastikan tidak ada format tersembunyi atau bagian yang tersisa yang mengganggu bentuk yang akan Anda tambahkan nanti.

## Sisipkan gambar ke dalam Word menggunakan DocumentBuilder

Selanjutnya, kita **menyisipkan gambar ke dalam Word** dengan terlebih dahulu membuat grup bentuk yang akan menampung gambar. Grup bentuk memungkinkan Anda memperlakukan beberapa objek gambar sebagai satu unit, yang berguna ketika Anda nanti ingin menyembunyikan atau memindahkannya bersama-sama.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Metode `InsertGroupShape` membuat sebuah kontainer kosong. Dimensi diukur dalam poin (1 poin = 1/72 inci). Sesuaikan ukuran agar cocok dengan resolusi gambar yang akan Anda sematkan.

## Tambahkan grup gambar ke dokumen

Sekarang kita **menambahkan grup gambar** dengan memindahkan kursor builder ke dalam grup yang baru dibuat dan menyisipkan gambar. Semua penyisipan berikutnya akan menjadi bagian dari grup.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tip:* Gunakan jalur absolut atau jalur relatif yang di‑escape dengan benar; jika tidak `InsertImage` akan melempar `FileNotFoundException`.

## Sembunyikan bentuk dalam dokumen Word

Akhirnya, kita **menyembunyikan bentuk dalam dokumen Word** dengan mengatur properti `Hidden` grup menjadi `true`. Bentuk tersembunyi tidak ditampilkan saat dokumen dibuka di Word, tetapi tetap ada dalam file dan dapat diungkap secara programatis nanti.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Saat Anda membuka *GroupHidden.docx* di Microsoft Word, Anda akan melihat halaman yang sepenuhnya kosong karena grup gambar tersembunyi. File tersebut masih berisi data gambar, yang dapat Anda tampilkan kembali nanti dengan `group.Hidden = false` jika diperlukan.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke dalam proyek konsol baru:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Output yang diharapkan**

- Sebuah file bernama `GroupHidden.docx` muncul di `YOUR_DIRECTORY`.
- Membuka file di Word menampilkan halaman kosong.
- Gambar tersembunyi dapat ditampilkan kembali dengan mengubah `group.Hidden = false` dan menyimpan ulang.

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|----------------------|
| **Multiple images** | Tambahkan pemanggilan `InsertImage` tambahan setelah `builder.MoveTo(group)`. Semua gambar tetap berada dalam grup yang sama dan berbagi flag tersembunyi. |
| **Different image formats** | Aspose.Words mendukung PNG, JPEG, BMP, GIF, TIFF. Cukup ubah ekstensi file; tidak perlu mengubah kode. |
| **Conditional visibility** | Simpan variabel dokumen khusus (`doc.Variables.Add("ShowImages", "true")`) dan ubah `group.Hidden` berdasarkan nilainya pada saat runtime. |
| **Large documents** | Buat grup pada halaman tertentu (`builder.InsertBreak(BreakType.PageBreak)`) sebelum menyisipkan grup untuk menghindari pergeseran tata letak. |
| **Compatibility with older Word versions** | Simpan sebagai `doc.Save("output.doc", SaveFormat.Doc)` jika Anda membutuhkan format legacy `.doc`; bentuk tersembunyi berperilaku sama. |

**Pro tip:** Selalu set `group.Hidden = true` *setelah* Anda menyisipkan semua elemen anak. Mengubah flag sebelum menambahkan konten dapat menyebabkan beberapa elemen ter‑render secara tidak terduga pada versi Word yang lebih lama.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word kosong**, **menyisipkan gambar ke dalam Word**, **menambahkan grup gambar**, dan **menyembunyikan bentuk dalam dokumen Word** menggunakan Aspose.Words untuk .NET. Contoh lengkap menunjukkan setiap langkah mulai dari menginisialisasi dokumen hingga menyimpan file yang berisi grup gambar tersembunyi.

Selanjutnya, Anda mungkin ingin mengeksplorasi:

- Menambahkan kotak teks atau diagram ke grup yang sama
- Menggunakan `DocumentBuilder.StartBookmark` / `EndBookmark` untuk menandai bagian tersembunyi
- Mengubah visibilitas secara programatis berdasarkan input pengguna atau variabel dokumen

Silakan bereksperimen dengan berbagai bentuk, ukuran, dan aturan visibilitas untuk menyesuaikan skenario otomasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}