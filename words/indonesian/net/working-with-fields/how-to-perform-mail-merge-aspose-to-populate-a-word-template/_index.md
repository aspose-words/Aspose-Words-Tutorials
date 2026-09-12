---
category: general
date: 2026-09-11
description: Mail merge Aspose memungkinkan Anda memuat templat Word dan mengisi templat
  Word dengan data, mengotomatiskan pembuatan dokumen untuk membuat surat yang dipersonalisasi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: id
lastmod: 2026-09-11
og_description: Mail merge Aspose memungkinkan Anda memuat templat Word dan mengisi
  templat tersebut, menyederhanakan pembuatan dokumen sehingga Anda dapat membuat
  surat pribadi dengan cepat.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge Aspose: mengisi template Word dalam hitungan menit'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Cara melakukan mail merge dengan Aspose untuk mengisi template Word
url: /id/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara melakukan mail merge aspose untuk mengisi template Word

Jika Anda perlu **mail merge aspose** untuk menghasilkan sekumpulan surat yang dipersonalisasi, panduan ini menunjukkan secara tepat cara memuat template Word, mengisinya dengan data, dan mengotomatisasi pembuatan dokumen dalam beberapa baris C#. Baik Anda membangun sistem pengiriman surat atau alat pelaporan, contoh lengkap di bawah ini memungkinkan Anda membuat surat yang dipersonalisasi tanpa menulis logika merge manual.

Anda akan belajar cara **load word template**, menggunakan kelas `MailMerger` low‑code, dan **populate word template** dengan sumber data anonim. Pada akhir tutorial Anda akan memiliki aplikasi console siap‑jalankan yang menghasilkan dokumen Word yang sudah digabungkan, yang dapat Anda kirim email, cetak, atau arsipkan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terinstal  
* Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi gratis)  
* Paket NuGet `Aspose.Words` (versi 23.10 atau lebih baru) terpasang di proyek Anda  
* File Word (`MailMergeTemplate.docx`) yang berisi placeholder MERGEFIELD seperti **«Name»** dan **«Age»**  

Anda dapat membuat template tersebut di Microsoft Word dengan menyisipkan *Insert → Quick Parts → Field → MergeField* dan memberi nama field persis seperti nama properti di sumber data Anda.

## Langkah 1 – Siapkan sumber data untuk mail merge

Merge low‑code bekerja dengan koleksi enumerable apa pun. Pada contoh ini kami menggunakan array objek anonim, tetapi Anda juga dapat memberikan `DataTable`, daftar POCO, atau data yang dibaca dari basis data.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Mengapa ini penting:**  
Setiap nama properti objek (`Name`, `Age`) harus cocok dengan MERGEFIELD di template. Kelas `MailMerger` secara otomatis memetakan properti ke field, menghilangkan kebutuhan akan event `FieldMerging` manual.

## Langkah 2 – Muat template Word yang berisi MERGEFIELD

Memuat template sangat mudah dengan kelas `Document`. Path dapat berupa absolut atau relatif terhadap direktori kerja executable.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Tips pro:**  
Jika Anda menjalankan kode dari Visual Studio, atur *Copy to Output Directory* untuk file template menjadi **Copy always**. Ini memastikan file tersedia saat binary yang telah dikompilasi dijalankan.

## Langkah 3 – Buat instance MailMerger yang terikat pada template

Kelas `MailMerger` berada di namespace `Aspose.Words.LowCode` dan menyediakan satu metode `Execute` yang menerima sumber data.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Mengapa menggunakan MailMerger?**  
`MailMerger` menyederhanakan pemanggilan boilerplate `MailMerge.Execute`, menangani deteksi field, binding data, dan cloning dokumen secara internal. Ini membuat kode ideal untuk skenario **automate document generation** di mana Anda menginginkan solusi low‑code yang bersih.

## Langkah 4 – Jalankan low‑code merge dengan data yang telah disiapkan

Memanggil `Execute` mengembalikan sebuah `Document` baru yang berisi


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Rename Word Merge Fields with Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}