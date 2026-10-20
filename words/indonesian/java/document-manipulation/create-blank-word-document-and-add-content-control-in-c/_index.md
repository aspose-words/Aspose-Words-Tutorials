---
category: general
date: 2026-10-20
description: Buat dokumen Word kosong menggunakan Aspose.Words dan pelajari cara menggunakan
  tag, menambahkan kontrol konten, mengatur placeholder, serta menyimpan dokumen Word
  dalam format docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to use tags
- add content control
- how to set placeholder
- save word document docx
language: id
lastmod: 2026-10-20
og_description: Buat dokumen Word kosong dengan Aspose.Words. Tutorial ini menjelaskan
  cara menggunakan tag, menambahkan kontrol konten, mengatur placeholder, dan menyimpan
  dokumen Word dalam format docx.
og_image_alt: Screenshot of a blank Word document containing a content control placeholder
og_title: Buat dokumen Word kosong dan tambahkan kontrol konten – panduan C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create blank Word document using Aspose.Words and learn how to use
    tags, add content control, set placeholder, and save Word document docx.
  headline: Create blank Word document and add content control in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word kosong dan tambahkan kontrol konten dalam C#
url: /id/java/document-manipulation/create-blank-word-document-and-add-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan kontrol konten di C#

Jika Anda perlu **membuat dokumen Word kosong** secara programatis, panduan ini akan memandu Anda melalui proses lengkap dengan Aspose.Words untuk .NET. Anda akan melihat **cara menggunakan tag**, menambahkan **kontrol konten**, mengatur **placeholder**, dan akhirnya **menyimpan dokumen Word docx** ke disk.

Tutorial ini mencakup semua yang perlu Anda ketahui untuk menghasilkan templat yang dapat digunakan kembali dan dapat diisi nanti oleh pengguna atau sistem lain. Pada akhir tutorial Anda akan memiliki file .docx yang berisi Structured Document Tag (SDT) teks polos yang siap untuk entri data.

## Prasyarat

* .NET 6.0 atau yang lebih baru terinstal.
* Visual Studio 2022 (atau IDE C# apa pun yang Anda sukai).
* Paket NuGet Aspose.Words untuk .NET (`Aspose.Words`) ditambahkan ke proyek Anda.
* Familiaritas dasar dengan sintaks C#.

Item-item ini memastikan kode berjalan tanpa konfigurasi tambahan.

## Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`, yang mewakili file Word kosong, dan `DocumentBuilder` yang memungkinkan Anda mengedit isinya.

```csharp
// Step 1: Initialise a new blank document and a builder to edit it
Document doc = new Document();               // Represents an empty .docx file
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` dimulai dalam keadaan kosong, sehingga Anda secara efektif **membuat dokumen Word kosong**. `DocumentBuilder` menyediakan metode untuk menyisipkan teks, tabel, dan, yang penting untuk tutorial ini, Structured Document Tags (SDT).

## Cara menggunakan tag: sisipkan Structured Document Tag teks polos

Structured Document Tags adalah fitur Word dasar yang dikenal sebagai *content controls*. Untuk mendemonstrasikan **cara menggunakan tag**, kami menyisipkan SDT teks polos dan memberikan identifier.

```csharp
// Step 2: Insert a plain‑text Structured Document Tag (SDT) with an ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "TagId");
```

Metode `InsertStructuredDocumentTag` membuat kontrol dan menempatkan kursor di dalamnya, siap untuk konfigurasi lebih lanjut.

## Tambahkan kontrol konten: atur judul dan placeholder

Kontrol konten menjadi berguna ketika Anda menyediakan metadata yang ramah pengguna. Di sini kami **menambahkan kontrol konten** dengan detail seperti judul dan placeholder yang muncul sebagai teks petunjuk abu-abu di dalam tag.

```csharp
// Step 3: Set user‑friendly metadata for the SDT
sdt.Title = "CustomerName";                 // Visible name in the Word UI
sdt.PlaceholderName = "Enter name";         // Placeholder text shown to the user
```

Mengatur `Title` membantu pengguna memahami tujuan kontrol, sementara `PlaceholderName` menerapkan persyaratan **cara mengatur placeholder**.

## Sisipkan konten aktual yang akan muncul di dalam SDT

Sekarang kami menulis konten default yang akan ditampilkan saat dokumen dibuka. Dalam banyak skenario Anda mungkin membiarkannya kosong, tetapi menambahkan nilai contoh memperjelas perilaku kontrol.

```csharp
// Step 4: Add the actual content that will appear inside the SDT
builder.Write("John Doe");
```

Pemanggilan `Write` menempatkan teks di dalam SDT yang telah dibuat sebelumnya, sehingga placeholder digantikan oleh nilai yang diberikan.

## Simpan dokumen Word docx ke file

Langkah terakhir adalah menyimpan dokumen ke disk. Ini memenuhi bagian **menyimpan dokumen Word docx** dalam tutorial.

```csharp
// Step 5: Save the document to a file
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "SDT.docx");
doc.Save(outputPath);
```

Setelah dijalankan, Anda akan menemukan `SDT.docx` di desktop Anda. Membuka file tersebut di Microsoft Word menampilkan kontrol konten teks polos dengan judul *CustomerName* serta placeholder “Enter name” (terlihat ketika kontrol kosong) dan teks “John Doe”.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan sebagai aplikasi konsol.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialise a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text Structured Document Tag (SDT) with an ID
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, "TagId");

        // Set user‑friendly metadata for the SDT
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Add the actual content that will appear inside the SDT
        builder.Write("John Doe");

        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "SDT.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

**Output yang diharapkan**

```
Document saved to: C:\Users\<YourUser>\Desktop\SDT.docx
```

Saat Anda membuka `SDT.docx` Anda akan melihat satu paragraf yang berisi teks “John Doe” di dalam kontrol konten berlabel *CustomerName*. Jika Anda menghapus “John Doe”, placeholder “Enter name” muncul dalam warna abu-abu, menunjukkan bahwa logika **cara mengatur placeholder** berfungsi.

## Variasi umum dan kasus tepi

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Beberapa kontrol konten** | Panggil `InsertStructuredDocumentTag` berulang kali dengan ID dan judul yang berbeda. | Memungkinkan Anda membangun templat kompleks dengan banyak bidang yang dapat diisi. |
| **Kontrol konten teks kaya** | Gunakan `StructuredDocumentTagType.RichText` alih-alih `PlainText`. | Mengaktifkan teks tebal, miring, atau gambar tersemat di dalam kontrol. |
| **Bagian berulang** | Gunakan `StructuredDocumentTagType.RepeatingSection`. | Berguna untuk tabel di mana baris ditambahkan secara dinamis. |
| **Menyimpan ke stream** | Ganti `doc.Save(outputPath)` dengan `doc.Save(stream, SaveFormat.Docx)`. | Memungkinkan Anda mengirim file melalui HTTP atau menyimpannya di basis data. |
| **Kompatibilitas dengan versi Word lama** | Simpan dengan `doc.Save(outputPath, SaveFormat.Doc)`. | Menghasilkan file `.doc` untuk kompatibilitas Word 2003/2007. |

Variasi ini menggambarkan bagaimana Anda dapat memperluas pola **menambahkan kontrol konten** dasar untuk memenuhi kebutuhan yang lebih canggih.

## Tips dan praktik terbaik

* **Pro tip:** Tetapkan ID yang bermakna (`TagId`) yang sesuai dengan model data yang akan Anda hubungkan nanti. Ini membuat pembaruan programatis menjadi sederhana.
* **Watch out for:** lupa mengatur `PlaceholderName` ketika kontrol harus membimbing pengguna; placeholder secara default kosong, yang dapat membingungkan.
* **Performance note:** Membuat banyak SDT dalam satu dokumen tidak mahal, tetapi jika Anda menghasilkan ribuan kontrol pertimbangkan untuk menggunakan kembali satu instance `DocumentBuilder` seperti yang ditunjukkan.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **cara menggunakan tag**, **menambahkan kontrol konten**, **cara mengatur placeholder**, dan **menyimpan dokumen Word docx** menggunakan Aspose.Words untuk .NET. Contoh lengkap menunjukkan templat praktis yang dapat diintegrasikan ke dalam pipeline pembuatan dokumen yang lebih besar.

Langkah selanjutnya mungkin meliputi:

* Menjelajahi **menambahkan kontrol konten** untuk tabel dan gambar.
* Mengotomatiskan pengisian placeholder dari basis data.
* Mengonversi `.docx` yang dihasilkan ke PDF atau HTML untuk pengiriman web.

Jangan ragu untuk bereksperimen dengan berbagai jenis tag dan teks placeholder untuk menyesuaikan dokumen dengan kebutuhan aplikasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara Menambahkan Kontrol Konten dan Membuat Dokumen Word dengan Aspose – Lengkap](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)
- [Buat dokumen Word secara programatis – tambahkan kontrol konten dan placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}