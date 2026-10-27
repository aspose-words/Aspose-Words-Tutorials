---
category: general
date: 2026-09-21
description: Buat dokumen Word kosong dengan elips tersembunyi menggunakan C#. Pelajari
  cara menyembunyikan bentuk di Word dan menghasilkan bentuk tersembunyi secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word kosong dengan elips tersembunyi menggunakan C#.
  Panduan ini menunjukkan cara menyembunyikan bentuk di Word dan membuat bentuk tersembunyi
  secara programatis.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Buat dokumen Word kosong dengan bentuk elips tersembunyi di C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat dokumen Word kosong dan menambahkan bentuk elips tersembunyi dalam
  C#
url: /id/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan menambahkan bentuk elips tersembunyi di C#

Jika Anda perlu **membuat dokumen Word kosong** yang berisi grafik tak terlihat, panduan ini menunjukkan cara melakukannya secara tepat. Pada akhir tutorial Anda akan memiliki file .docx yang tampak kosong namun sebenarnya menyimpan bentuk elips yang disembunyikan dari tata letak.

Kami akan menggunakan Aspose.Words untuk .NET untuk membangun dokumen, menyisipkan elips, menyembunyikannya, dan menyimpan file. Langkah‑langkahnya juga mencakup **cara membuat objek elips**, cara **menyembunyikan shape di Word**, dan cara **membuat shape tersembunyi** yang berfungsi dengan proyek .NET apa pun.

## Prasyarat

Sebelum Anda mulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Visual Studio 2022 (atau editor C# apa saja)  
* Lisensi Aspose.Words untuk .NET atau salinan evaluasi gratis  
* Familiaritas dasar dengan sintaks C#  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Membuat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menghasilkan file Word kosong. Ini memberi kita kanvas bersih di mana nanti kita dapat menyisipkan grafik tersembunyi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Mengapa kita memulai dengan dokumen kosong** – Memulai dari file kosong menjamin tidak ada konten yang tidak diinginkan mengganggu shape tersembunyi. Hal ini juga menjaga ukuran file tetap minimal, yang berguna ketika dokumen nanti digunakan sebagai templat.

## Cara membuat elips di dalam dokumen kosong

Selanjutnya kita memerlukan `DocumentBuilder` untuk menambahkan konten. Builder memungkinkan kita menempatkan shape secara tepat di lokasi yang diinginkan.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Penjelasan** – `ShapeType.Ellipse` memberi tahu Aspose.Words untuk menggambar sebuah bentuk mirip lingkaran. Lebar dan tinggi diukur dalam poin (1 pt ≈ 1/72 inci). Anda dapat menyesuaikan nilai‑nilai ini sesuai kebutuhan desain Anda.

## Menyembunyikan shape di Word agar tidak muncul di tata letak

Shape yang disembunyikan tetap berada di XML dokumen, yang dapat berguna untuk metadata, pemformatan bersyarat, atau modifikasi programatik di kemudian hari. Untuk menyembunyikannya, kita mengatur properti `Hidden` menjadi `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Mengapa menyembunyikan shape** – Shape tersembunyi diabaikan oleh mesin tata letak, sehingga halaman terlihat benar‑benar kosong. Namun, data shape tetap ada, yang dapat berguna untuk menyimpan penanda, bookmark, atau XML khusus yang dapat dibaca proses hilir.

## Menyimpan dokumen dengan shape tersembunyi

Akhirnya kita menulis file ke disk. `.docx` yang disimpan akan terbuka di Microsoft Word tanpa konten yang terlihat, namun elips tersembunyi tetap ada.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verifikasi** – Buka file yang dihasilkan di Word, kemudian tekan `Alt+F9` untuk menampilkan kode bidang dan `Ctrl+A` → `Ctrl+Shift+F9` untuk melihat objek tersembunyi. Anda akan melihat elips di XML dokumen (`word/document.xml`) tetapi tidak ada apa‑apa di halaman.

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke proyek konsol baru. Program ini mencakup semua direktif `using` dan metode `Main` sehingga dapat dijalankan tanpa scaffolding tambahan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Output yang diharapkan** – Saat Anda menjalankan program, konsol mencetak jalur file, dan file Word yang dihasilkan tidak berisi objek yang terlihat. Jika Anda memeriksa dokumen dengan alat zip (`.docx` adalah arsip zip), Anda akan menemukan elemen `<w:pict>` yang mendeskripsikan elips di dalam `word/document.xml`.

---

## Variasi umum dan kasus tepi

| Skenario | Apa yang diubah | Mengapa penting |
|----------|----------------|----------------|
| **Shape berbeda** | Ganti `ShapeType.Ellipse` dengan `ShapeType.Rectangle`, `ShapeType.Line`, dll. | Memungkinkan Anda menyembunyikan grafik lain sambil mempertahankan alur kerja yang sama. |
| **Beberapa shape tersembunyi** | Panggil `InsertShape` beberapa kali dan set `Hidden = true` pada masing‑masing. | Berguna untuk menyematkan kumpulan penanda atau placeholder. |
| **Visibilitas bersyarat** | Gunakan `shape.Visible = false` bersama `shape.Hidden = true` untuk keamanan ekstra. | Beberapa versi Word lama memperlakukan `Visible` secara berbeda; mengatur keduanya menutupi semua kasus. |
| **Menyimpan ke stream** | Ganti `doc.Save(path)` dengan `doc.Save(stream, SaveFormat.Docx)`. | Memungkinkan pengiriman dokumen langsung lewat HTTP atau penyimpanan di basis data. |
| **Menerapkan gaya** | Setelah penyisipan, ubah `ellipse.FillColor`, `ellipse.LineWeight`, dll. sebelum disembunyikan. | Gaya shape tetap ada di XML, yang dapat berguna untuk menampilkan kembali nanti. |

**Tips pro:** Selalu uji shape tersembunyi pada versi Word target (misalnya Word 2019, Word 365) karena terkadang ada keanehan rendering ketika objek tersembunyi berinteraksi dengan tata letak halaman yang kompleks.

---

## Pertanyaan yang sering diajukan

**T: Apakah menyembunyikan shape memengaruhi ukuran dokumen?**  
J: XML shape menambah beberapa ratus byte, yang dapat diabaikan untuk kebanyakan kasus penggunaan. File tetap pada dasarnya berukuran sama seperti dokumen yang benar‑benar kosong.

**T: Bisakah saya menampilkan kembali shape secara programatik?**  
J: Ya. Muat dokumen, temukan shape (`doc.GetChildNodes(NodeType.Shape, true)`), dan set `shape.Hidden = false`.

**T: Apakah shape tersembunyi akan muncul saat mencetak?**  
J: Tidak. Objek tersembunyi dikecualikan dari tata letak cetak, sehingga halaman yang tercetak tetap kosong.

**T: Apakah pendekatan ini hanya kompatibel dengan Office Open XML (OOXML)?**  
J: Properti `Hidden` merupakan bagian dari spesifikasi OOXML, sehingga setiap pengolah kata yang sepenuhnya mengimplementasikan OOXML (Word, LibreOffice, Google Docs) akan menghormati flag tersembunyi tersebut.

---

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **membuat elips**, **menyembunyikan shape di Word**, dan **membuat shape tersembunyi** menggunakan Aspose.Words untuk .NET. Tutorial ini mencakup seluruh siklus hidup—dari inisialisasi file kosong hingga penyisipan, penyembunyian, dan penyimpanan shape—serta langkah verifikasi dan variasi umum.

Selanjutnya, Anda dapat mengeksplorasi:

* Menambahkan kotak teks tersembunyi untuk metadata (teknik `hide shape in word` diterapkan pada teks)  
* Menggunakan bagian XML khusus untuk menyimpan data terstruktur bersamaan dengan shape tersembunyi  
* Mengonversi dokumen dengan shape tersembunyi ke PDF sambil mempertahankan elemen tersembunyi  

Bereksperimenlah dengan berbagai shape dan pengaturan visibilitas untuk melihat bagaimana konten tersembunyi dapat berfungsi sebagai penyimpanan data ringan di dalam file Word.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}