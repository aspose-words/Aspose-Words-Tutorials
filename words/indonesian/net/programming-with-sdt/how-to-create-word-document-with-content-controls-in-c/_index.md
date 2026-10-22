---
category: general
date: 2026-09-05
description: Buat dokumen Word dengan Aspose.Words, atur teks placeholder, tambahkan
  kontrol, dan simpan dokumen sebagai docx di C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: id
lastmod: 2026-09-05
og_description: Buat dokumen Word menggunakan Aspose.Words untuk .NET, atur teks placeholder,
  tambahkan kontrol, dan simpan dokumen sebagai docx. Ikuti tutorial lengkap ini.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Buat dokumen Word dengan kontrol konten di C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Cara membuat dokumen Word dengan kontrol konten di C#
url: /id/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word dengan kontrol konten di C#

Jika Anda perlu **membuat dokumen Word** yang mencakup kontrol konten terstruktur, panduan ini menunjukkan cara menambahkan tag teks biasa, **mengatur teks placeholder**, dan **menyimpan dokumen sebagai docx** menggunakan Aspose.Words untuk .NET. Contoh ini dapat dijalankan sepenuhnya dan menunjukkan pendekatan yang direkomendasikan untuk pembuatan Word secara programatik.

Anda akan belajar bagaimana:

* Menginisialisasi file Word kosong dengan `Document` dan `DocumentBuilder`.
* **Cara menambahkan kontrol** (sebuah `StructuredDocumentTag`) ke badan dokumen.
* **Cara membuat tag** dengan judul dan placeholder yang memandu pengguna akhir.
* Menyimpan hasil dengan `document.Save`, memastikan file merupakan `.docx` yang valid.

Tutorial ini mengasumsikan Anda memiliki lingkungan pengembangan C# dasar dan lisensi untuk Aspose.Words (evaluasi gratis dapat digunakan untuk tujuan pembelajaran).

---

## Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| .NET 6.0 atau lebih baru | Menyediakan runtime untuk Aspose.Words untuk .NET. |
| Paket NuGet Aspose.Words untuk .NET | Menyediakan kelas `Document`, `DocumentBuilder`, dan `StructuredDocumentTag`. |
| IDE seperti Visual Studio 2022 | Memudahkan menjalankan dan men-debug contoh. |

Instal paket dengan .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Langkah 1: Siapkan proyek untuk **membuat dokumen word**

Buat proyek konsol baru (atau tambahkan kode ke proyek yang sudah ada). Baris pertama menginstansiasi file Word kosong dan `DocumentBuilder` yang memungkinkan Anda menulis konten.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` mewakili struktur file, sementara `DocumentBuilder` melacak titik penyisipan. Pola ini adalah dasar untuk setiap skenario pembuatan Word.

---

## Langkah 2: **Cara menambahkan kontrol** – buat kontrol konten teks biasa (tag)

Sebuah kontrol konten di Word disebut *structured document tag* (SDT). Kode berikut membuat SDT teks biasa, menetapkan judul, dan mendefinisikan placeholder yang muncul saat dokumen dibuka.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Mengapa ini penting:**  
* Properti `Title` berfungsi sebagai pengidentifikasi yang stabil, memungkinkan Anda menemukan atau mengganti kontrol secara programatik nanti.  
* `PlaceholderName` memberikan panduan visual kepada pengguna dokumen tanpa memerlukan kode UI tambahan.

![Buat dokumen Word dengan placeholder kontrol konten](image.png)

*Teks alt gambar: Membuat dokumen Word dengan kontrol konten yang menampilkan teks placeholder.*

---

## Langkah 3: Pindahkan kursor ke dalam kontrol dan tulis teks default

Setelah menyisipkan kontrol, kursor builder masih berada di luar kontrol. Pindahkan kursor ke dalam tag sehingga penulisan selanjutnya menjadi bagian dari konten kontrol.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Jika Anda lebih suka membiarkan kontrol kosong, hapus pemanggilan `Write`. Placeholder tetap terlihat sampai pengguna mengetik nilai.

---

## Langkah 4: **Atur teks placeholder** (pendekatan alternatif)

Kadang-kadang Anda perlu mengubah placeholder setelah tag dibuat. Anda dapat memodifikasi properti `PlaceholderName` secara langsung:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Mengubah placeholder **tidak** memengaruhi konten yang ada, sehingga aman memperbarui petunjuk UI tanpa mengubah data yang dimasukkan pengguna.

---

## Langkah 5: **Simpan dokumen sebagai docx**

Simpan dokumen dalam memori ke file fisik. Metode `Save` secara otomatis menentukan format dari ekstensi file.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Jika Anda memerlukan format lain (misalnya PDF atau HTML), berikan nilai enum `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Langkah 6: Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian menghasilkan program singkat yang mendemonstrasikan **cara membuat tag**, mengatur placeholder-nya, dan **menyimpan dokumen sebagai docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Output yang diharapkan:**  
Menjalankan program membuat `SdtExample.docx` yang berisi satu paragraf dengan kontrol konten teks biasa berjudul *CustomerName*. Kontrol menampilkan “John Doe” sebagai konten awal; jika teks default dihapus, placeholder “Enter name” muncul dalam warna abu‑abu muda saat file dibuka di Microsoft Word.

---

## Variasi umum dan kasus tepi

| Skenario | Penyesuaian yang direkomendasikan |
|----------|-----------------------------------|
| **Beberapa kontrol** | Ulangi langkah 2‑4 untuk setiap bidang, berikan setiap kontrol `Title` yang unik. |
| **Kontrol teks kaya** | Gunakan `SdtType.RichText` alih‑alih `PlainText`. |
| **Bagian berulang** | Pilih `SdtType.RepeatingSection` dan tambahkan kontrol anak di dalam bagian. |
| **Dokumen yang sudah ada** | Muat file yang ada dengan `new Document("template.docx")` dan sisipkan kontrol pada lokasi yang diinginkan. |
| **Placeholder Unicode** | Setel `PlaceholderName` ke string Unicode apa pun; Word akan menampilkannya dengan benar. |
| **Dokumen besar** | Dispose `DocumentBuilder` setelah digunakan untuk membebaskan memori (`builder.Dispose();`). |

**Pro tip:** Ketika Anda perlu mengambil nilai yang dimasukkan pengguna nanti, panggil `StructuredDocumentTag.GetText()` setelah dokumen disimpan dan dibuka kembali. Metode ini mengembalikan teks dalam tanpa placeholder.

**Watch out for:** Menggunakan placeholder yang sama dengan teks default dapat menyebabkan kebingungan, karena Word menyembunyikan placeholder ketika ada teks apa pun. Jaga keduanya tetap berbeda.

---

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word** secara programatik, **menambahkan kontrol**, **membuat tag**, **mengatur teks placeholder**, dan **menyimpan dokumen sebagai docx** menggunakan Aspose.Words untuk .NET. Contoh lengkap dapat disalin ke proyek C# mana pun dan diperluas untuk mendukung tipe kontrol tambahan, bagian berulang, atau integrasi dengan sumber data.

Langkah selanjutnya yang dapat Anda jelajahi meliputi:

* Menambahkan **kontrol konten gambar** (`SdtType.Picture`) untuk menyematkan grafik yang disediakan pengguna.  
* Menggunakan **binding** untuk memetakan SDT ke data XML untuk skenario mail‑merge.  
* Mengonversi DOCX yang dihasilkan ke PDF (`SaveFormat.Pdf`) untuk distribusi.

Bereksperimenlah dengan berbagai tipe tag dan pesan placeholder untuk menyesuaikan alur kerja aplikasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}