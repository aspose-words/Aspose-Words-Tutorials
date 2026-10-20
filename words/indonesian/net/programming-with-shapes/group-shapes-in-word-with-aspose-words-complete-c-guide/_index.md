---
category: general
date: 2026-07-19
description: Kelompokkan bentuk di Word menggunakan Aspose.Words. Pelajari cara menambahkan
  bentuk persegi panjang, mendefinisikan bentuk elips, dan menyisipkan bentuk ke dalam
  dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: id
lastmod: 2026-07-19
og_description: Kelompokkan bentuk di Word dengan Aspose.Words. Kuasai penambahan
  bentuk persegi panjang, mendefinisikan bentuk elips, dan menyisipkan bentuk ke dalam
  dokumen Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Mengelompokkan Bentuk di Word – Tutorial C# Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Mengelompokkan Bentuk di Word dengan Aspose.Words – Panduan Lengkap C#
url: /id/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengelompokkan Bentuk di Word – Panduan Lengkap C#

Pernah bertanya-tanya bagaimana cara **mengelompokkan bentuk di Word** tanpa harus bermain‑main dengan UI? Anda tidak sendirian. Baik Anda membuat kontrak, selebaran, atau diagram secara programatik, kemampuan untuk **menambahkan bentuk persegi panjang**, **mendefinisikan bentuk elips**, dan kemudian **mengelompokkan bentuk di Word** dapat menghemat berjam‑jam pekerjaan manual.

Dalam tutorial ini kita akan membahas contoh dunia nyata menggunakan **Aspose.Words for .NET**. Pada akhir tutorial Anda akan tahu persis cara **menyisipkan bentuk ke Word**, menggabungkannya, dan menghasilkan dokumen yang rapi yang dapat Anda kirim ke klien atau rekan tim.

---

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki hal‑hal berikut:

- **Aspose.Words for .NET** (versi terbaru, misalnya 24.9). Anda dapat mengunduhnya dari NuGet dengan `Install-Package Aspose.Words`.
- Lingkungan pengembangan .NET (Visual Studio 2022 atau VS Code dengan ekstensi C# sudah cukup).
- Familiaritas dasar dengan sintaks C#—tidak perlu hal yang rumit, hanya pernyataan `using` dan pembuatan objek biasa.

Itu saja. Tidak ada pustaka tambahan, tidak ada interop COM, hanya kode terkelola murni.

---

## Cara Mengelompokkan Bentuk di Word Menggunakan Aspose.Words

Berikut adalah langkah‑demi‑langkah yang mencerminkan kode yang sudah Anda miliki. Setiap langkah menjelaskan **mengapa** kita melakukannya, bukan hanya **apa** yang dilakukan baris kode, sehingga Anda dapat menyesuaikan pola ini untuk bentuk apa pun yang Anda inginkan.

### Langkah 1: Siapkan Dokumen dan Builder

Kita mulai dengan membuat `Document` kosong dan `DocumentBuilder`. Builder berfungsi sebagai “pena” yang memungkinkan kita menyisipkan konten di mana saja diperlukan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Mengapa?** Objek `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan API yang nyaman untuk menyisipkan node (seperti bentuk) tanpa harus berurusan langsung dengan pohon node di bawahnya.

### Langkah 2: Tambahkan Bentuk Persegi Panjang (add rectangle shape)

Sekarang kita **menambahkan bentuk persegi panjang** ke dokumen. Kita mengatur ukuran, posisi, dan warna isi agar terlihat menonjol.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Anda dapat mengubah `FillColor` ke warna `System.Drawing.Color` apa pun yang Anda suka. Ini berguna ketika Anda memerlukan bagian‑bagian berwarna dalam sebuah laporan.

### Langkah 3: Definisikan Bentuk Elips (define ellipse shape)

Selanjutnya, kita **mendefinisikan bentuk elips**. Perhatikan `ShapeType` yang berbeda serta offset (`Left = 120`) sehingga elips berada di samping persegi panjang.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Mengapa ini penting:** Dengan memposisikan bentuk secara eksplisit, Anda mengontrol tampilan mereka sebelum digabungkan. Jika Anda mengandalkan tata letak otomatis, pengelompokan bisa terlihat tidak berpusat.

### Langkah 4: (Opsional) Sisipkan Bentuk Individu untuk Pratinjau

Jika Anda ingin melihat setiap bentuk sebelum digabungkan, Anda dapat **menyisipkan bentuk ke Word** secara terpisah. Langkah ini opsional tetapi berguna untuk debugging.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Komentari dua baris ini setelah Anda yakin bentuk‑bentuk sudah terlihat benar; jika tidak, Anda akan mendapatkan visual duplikat setelah pengelompokan.

### Langkah 5: Cara Mengelompokkan Bentuk – Buat GroupShape

Berikut inti tutorial: **cara mengelompokkan bentuk**. Kita membuat `GroupShape`, menempelkan persegi panjang dan elips, serta menentukan bagaimana grup berperilaku dengan teks di sekitarnya.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Penjelasan:** `GroupShape` pada dasarnya adalah kanvas mini yang menampung bentuk‑bentuk lain. Dengan mengatur `WrapType` menjadi `Inline`, seluruh grup bergerak sebagai satu unit ketika Anda menambah atau menghapus teks.

### Langkah 6: Sisipkan Bentuk yang Dikelompokkan ke Dokumen (insert shape into word)

Sekarang kita **menyisipkan bentuk ke Word**—tetapi kali ini yang dimasukkan adalah kontainer yang sudah dikelompokkan, bukan potongan‑potongan terpisah.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Apa yang terjadi di balik layar?** Pemanggilan `InsertNode` menambahkan `GroupShape` ke koleksi node dokumen. Karena grup sudah berisi persegi panjang dan elips, keduanya muncul bersama sebagai satu objek.

### Langkah 7: Simpan Dokumen

Terakhir, tuliskan file ke disk. Anda dapat mengubah jalur sesuai dengan struktur proyek Anda.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Hasil:** Buka `GroupShape.docx` di Microsoft Word dan Anda akan melihat persegi panjang biru muda dan elips koral yang terkunci bersama. Menyeret satu akan memindahkan yang lain—tepat seperti yang dijanjikan oleh “group shapes in word”.

---

## Konfirmasi Visual

Berikut adalah contoh tampilan bentuk yang dikelompokkan di dalam file Word.  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*Alt teks gambar berisi kata kunci utama untuk aksesibilitas dan SEO.*

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan lebih dari dua bentuk?

Cukup terus panggil `groupShape.AppendChild(bentukBaruAnda);` sebelum menyisipkan grup. API tidak membatasi jumlah bentuk anak.

### Bisakah saya memutar atau mengubah ukuran seluruh grup?

Tentu saja. `GroupShape` mewarisi dari `Shape`, sehingga Anda dapat mengatur properti seperti `RotationAngle`, `Width`, atau `Height` pada grup itu sendiri, dan semua bentuk anak akan mengikuti.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Bagaimana cara mengubah warna latar belakang grup?

Gunakan `groupShape.FillColor`. Ini mengisi kotak pembatas tak terlihat; dapat berguna untuk menyorot.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Apakah ini bekerja dengan format Word lama (.doc)?

`Aspose.Words` juga dapat menyimpan ke `.doc`—cukup ganti ekstensi file pada `Save`. Namun, beberapa fitur bentuk lanjutan (seperti pengelompokan) hanya sepenuhnya didukung pada format OOXML `.docx`.

---

## Contoh Lengkap yang Berfungsi

Salin‑tempel blok berikut ke aplikasi konsol baru untuk melihat seluruh proses beraksi. Tidak ada bagian yang terlewat; ini adalah **contoh lengkap yang dapat dijalankan**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Output yang diharapkan:** Saat Anda membuka `GroupShape.docx`, Anda akan melihat satu objek terkelompok yang terdiri dari persegi panjang biru muda dan elips koral muda, terletak bersebelahan dengan sempurna.

---

## Ringkasan

Kami baru saja membahas semua yang Anda perlukan untuk **mengelompokkan bentuk di Word** dengan Aspose.Words:

1. Buat dokumen dan builder.  
2. **Tambahkan bentuk persegi panjang** dan **definisikan bentuk elips** dengan dimensi eksplisit.  
3. (Opsional) **Sisipkan bentuk ke Word** untuk pratinjau cepat.  
4. Gunakan `GroupShape` untuk **cara mengelompokkan bentuk**—tambahkan tiap anak, atur pembungkus, dan sisipkan.  
5. Simpan file dan verifikasi hasilnya.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}