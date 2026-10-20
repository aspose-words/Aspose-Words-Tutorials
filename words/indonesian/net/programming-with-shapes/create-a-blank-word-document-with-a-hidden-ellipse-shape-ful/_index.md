---
category: general
date: 2026-07-29
description: Buat dokumen Word kosong dan pelajari cara menyembunyikan bentuk, membuat
  objek tersembunyi, serta membuat bentuk elips menggunakan Aspose.Words dalam C#.
  Kode langkah demi langkah disertakan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: id
lastmod: 2026-07-29
og_description: Buat dokumen Word kosong dan sembunyikan bentuk secara instan. Pelajari
  cara membuat objek tersembunyi dan menggambar bentuk elips menggunakan Aspose.Words
  dalam C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Buat Dokumen Word Kosong dengan Bentuk Elips Tersembunyi – Tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Buat Dokumen Word Kosong dengan Bentuk Elips Tersembunyi – Panduan Lengkap
  C#
url: /id/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word Kosong dengan Bentuk Elips Tersembunyi – Panduan Lengkap C#

Pernahkah Anda perlu membuat **dokumen word kosong** lalu menyembunyikan sebuah bentuk di dalamnya? Mungkin Anda sedang menghasilkan templat di mana beberapa penanda harus tetap tidak terlihat sampai langkah selanjutnya. Dalam tutorial ini kami akan membahas **cara menyembunyikan bentuk**, cara **membuat objek tersembunyi**, dan bahkan cara **membuat bentuk elips** menggunakan Aspose.Words untuk .NET. Pada akhir tutorial Anda akan memiliki potongan kode C# yang siap dijalankan dan menghasilkan file DOCX yang berisi elips tak terlihat.

## Apa yang Akan Anda Pelajari

- Menginisialisasi dokumen Word kosong baru dengan Aspose.Words.  
- Membuat bentuk elips, mengatur dimensinya, dan menempatkannya pada halaman.  
- Menandai bentuk sebagai tersembunyi sehingga tidak pernah muncul di layar atau saat dicetak.  
- Menyimpan hasil ke disk dan memverifikasi bahwa objek tersembunyi benar‑benar tidak terlihat.  

Tidak diperlukan pustaka eksternal selain Aspose.Words, dan kode ini bekerja dengan versi 24.10 atau yang lebih baru (properti `Hidden` diperkenalkan pada rilis tersebut). Mari kita mulai.

![Diagram elips tersembunyi di dalam dokumen Word kosong](https://example.com/hidden-ellipse.png "Bentuk elips tersembunyi yang disisipkan ke dalam dokumen Word kosong")

## Buat Dokumen Word Kosong dan Sisipkan Bentuk Elips Tersembunyi

Langkah pertama adalah membuat dokumen baru yang benar‑benar kosong. Anggap `Document` sebagai kanvas kosong; `DocumentBuilder` adalah kuas Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Mengapa memulai dengan dokumen kosong?**  
> Kanvas bersih menjamin tidak ada konten yang sudah ada mengganggu bentuk tersembunyi yang akan Anda tambahkan. Ini juga membuat contoh lebih mudah disalin‑tempel ke proyek mana pun.

## Cara Menyembunyikan Bentuk: Mengatur Properti Hidden

Aspose.Words 24.10 memperkenalkan flag `Hidden` pada `Shape`. Ketika diatur ke `true`, Word memperlakukan bentuk seperti komentar—sepenuhnya tidak terlihat di UI dan saat dicetak.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Tips pro:** Jika Anda kemudian perlu menampilkan kembali bentuk secara programatis, cukup ubah `ellipseShape.Hidden = false;` dan simpan ulang dokumen.

## Buat Objek Tersembunyi: Menyisipkan Bentuk ke Dokumen

Setelah elips dipersiapkan dan disembunyikan, kami menyisipkannya pada lokasi kursor builder saat ini. Posisi builder secara default berada di awal paragraf pertama, yang sempurna untuk dokumen kosong.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Bagaimana jika Anda memerlukan bentuk pada halaman tertentu?**  
> Pindahkan builder ke halaman yang diinginkan terlebih dahulu (`builder.MoveToDocumentEnd();` atau `builder.MoveToPage(pageNumber);`) sebelum memanggil `InsertNode`.

## Simpan Dokumen yang Memuat Bentuk Tersembunyi

Akhirnya, tulis file ke disk. Outputnya akan berupa DOCX standar yang dapat dibuka oleh program pengolah kata apa pun—kecuali elips akan tetap tidak terlihat.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Output yang diharapkan:** Buka `HiddenShape.docx` di Microsoft Word. Anda tidak akan melihat grafik apa pun, tetapi ukuran file akan sedikit lebih besar daripada dokumen yang benar‑benar kosong karena elips tersembunyi disimpan dalam XML.

## Verifikasi Elips Tersembunyi Secara Programatis (Opsional)

Jika Anda ingin memastikan bahwa bentuk memang tersembunyi, Anda dapat memuat file yang disimpan dan memeriksa properti `Hidden` pada bentuk:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Menjalankan potongan kode ini mencetak `True`, mengonfirmasi bahwa objek tersembunyi bertahan melalui siklus simpan‑muat.

## Kasus Pinggir dan Pertanyaan Umum

### Bagaimana jika versi Word target tidak mendukung bentuk tersembunyi?

Flag `Hidden` merupakan bagian dari spesifikasi Office Open XML dan dihormati oleh Word 2007+ serta LibreOffice. Format lama (misalnya `.doc`) mengabaikan flag ini, jadi selalu simpan sebagai `.docx` ketika Anda memerlukan penyembunyian yang dapat diandalkan.

### Bisakah saya menyembunyikan tipe objek lain (gambar, tabel)?

Ya. Setiap node yang diturunkan dari `Shape`—termasuk gambar, kotak teks, dan bahkan SmartArt—memiliki properti `Hidden`. Cukup atur ke `true` sebelum penyisipan.

### Apakah menyembunyikan bentuk memengaruhi kinerja dokumen?

Sangat sedikit. Bentuk disimpan sebagai markup XML, dan Word melewatkan rendering objek tersembunyi selama layout. Jika Anda menyematkan banyak objek tersembunyi, ukuran file akan bertambah, tetapi rendering tetap cepat.

### Bagaimana ini berbeda dari menggunakan bookmark atau komentar sebagai penanda?

Bookmark memang tidak terlihat secara default, tetapi mereka dirancang untuk navigasi, bukan sebagai placeholder visual. Komentar muncul di margin. Bentuk tersembunyi memberi Anda objek visual (ukuran, posisi) yang dapat Anda tampilkan atau manipulasi nanti, yang berguna untuk skenario templating.

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap disalin‑tempel. Program ini mencakup semua direktif `using`, pembuatan elips tersembunyi, dan langkah verifikasi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Menjalankan program ini membuat `HiddenEllipse.docx` di folder eksekusi. Buka file tersebut—Anda akan melihat halaman kosong yang tampak normal, namun elips tersembunyi berada di dalamnya secara diam‑diam.

## Ringkasan

Kami telah membahas cara **membuat dokumen word kosong**, **menyembunyikan bentuk**, **membuat objek tersembunyi**, dan **membuat bentuk elips** semuanya dengan beberapa baris C#. Inti pentingnya adalah properti `Hidden` pada `Shape`, yang mengubah elemen visual apa pun menjadi penanda tak terlihat tanpa merusak kompatibilitas Word.

## Apa Selanjutnya?

- **Gaya bentuk tersembunyi** (warna isi, gaya garis) sehingga ketika Anda menampilkannya nanti, tampilannya persis seperti yang diinginkan.  
- **Menggabungkan bentuk tersembunyi dengan bookmark** untuk membangun templat dinamis yang dapat diaktifkan atau dinonaktifkan.  
- **Jelajahi tipe bentuk lain**—persegi panjang, panah, atau bahkan jalur SVG khusus—dengan mengganti `ShapeType.Ellipse`.  

Silakan bereksperimen: ubah ukuran, pindahkan posisi, atau sisipkan beberapa elips tersembunyi. Pola yang sama berlaku untuk bentuk Aspose.Words apa pun yang perlu Anda sembunyikan.

Jika Anda mengalami masalah atau memiliki ide untuk memperluas pola ini, tinggalkan komentar di bawah. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}