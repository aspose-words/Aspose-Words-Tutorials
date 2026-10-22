---
category: general
date: 2026-07-23
description: Buat dokumen Word kosong dan tambahkan bentuk persegi panjang di C#.
  Pelajari cara menyisipkan bentuk dan mengelompokkan bentuk di Word menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: id
lastmod: 2026-07-23
og_description: Buat dokumen Word kosong di C# dan pelajari cara menyisipkan bentuk,
  menambahkan bentuk persegi panjang, serta mengelompokkan bentuk Word dengan Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Buat dokumen Word kosong dengan persegi panjang yang dikelompokkan – tutorial
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word kosong dengan persegi panjang yang dikelompokkan – Panduan
  C#
url: /id/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan persegi panjang yang dikelompokkan – Panduan C#

Pernahkah Anda perlu **create blank word document** yang sudah berisi sekumpulan bentuk, tetapi tidak yakin bagaimana cara mengelompokkannya dengan rapi? Anda bukan satu-satunya. Dalam banyak skenario pelaporan atau pembuatan templat, Anda menginginkan kanvas bersih dengan beberapa persegi panjang yang berfungsi sebagai placeholder, dan Anda ingin mereka bergerak bersama sebagai satu unit.

Dalam tutorial ini kami akan memandu Anda melalui langkah‑langkah tepat untuk **create blank word document**, **add rectangle shape**, dan kemudian **group shapes word** menggunakan library Aspose.Words. Pada akhir tutorial Anda akan memiliki file `.docx` siap pakai di mana dua persegi panjang menjadi bagian dari satu grup, sehingga setiap pemindahan atau pengubahan ukuran selanjutnya memengaruhi keduanya sekaligus.  

Kami juga akan menjawab pertanyaan umum “**how to insert shapes**” dan “**how to group shapes**” yang sering muncul di forum dan Stack Overflow. Tidak diperlukan dokumen eksternal—semua yang Anda butuhkan ada di sini.

---

## Prasyarat

- .NET 6 atau lebih baru (kode ini juga dapat dikompilasi dengan .NET Core)  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)  
- Pemahaman dasar tentang sintaks C# (jika Anda sudah menulis “Hello World”, Anda sudah siap)  

Jika Anda belum menginstal Aspose.Words, jalankan:

```bash
dotnet add package Aspose.Words
```

Itu saja—tidak ada DLL tambahan, tidak ada interop COM, hanya referensi NuGet yang bersih.

---

## Langkah 1: Create blank word document dan inisialisasi builder

Hal pertama yang kami lakukan adalah membuat objek `Document` kosong. Anggaplah itu sebagai selembar kertas baru. Kemudian kami melampirkan `DocumentBuilder`, yang merupakan alat praktis yang disediakan Aspose untuk menyisipkan konten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa ini penting:** Tanpa `DocumentBuilder` Anda harus memanipulasi pohon node tingkat rendah secara manual, yang rawan kesalahan. Builder menyederhanakan kerumitan XML dari file `.docx`.

---

## Langkah 2: How to insert shapes – tambahkan kontainer grup terlebih dahulu

Aspose memungkinkan Anda menyisipkan *group shape* yang kemudian dapat menampung bentuk lain. Ini adalah dasar untuk **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Tips pro:** Grup itu sendiri tidak terlihat sampai Anda menambahkan child shape, jadi Anda tidak akan melihat artefak apa pun dalam dokumen yang dihasilkan sampai langkah berikutnya.

---

## Langkah 3: Add rectangle shape – objek yang sebenarnya terlihat

Sekarang kami akan **add rectangle shape** dua kali, masing‑masing dengan ukuran sendiri. Metode `InsertShape` menerima `ShapeType` dan dimensi dalam poin (1 pt ≈ 1/72 inci).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Mengapa persegi panjang?** Mereka adalah bentuk geometris paling sederhana, sempurna untuk placeholder, tiruan UI seperti tombol, atau elemen grafis sederhana.

---

## Langkah 4: How to group shapes – lampirkan persegi panjang ke grup

Setelah persegi panjang dibuat, kami sekarang **how to group shapes** dengan menambahkan mereka sebagai child dari group shape yang telah kami sisipkan sebelumnya.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Apa yang terjadi di balik layar?** Group shape menjadi node induk dalam pohon XML dokumen. Memindahkan grup memindahkan kedua persegi panjang bersama-sama, mempertahankan posisi relatif mereka.

---

## Langkah 5: Save the document – Anda kini memiliki file Word dengan grouped‑shape

Akhirnya, kami menyimpan dokumen ke disk. Ubah path ke lokasi yang ada di mesin Anda.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Itulah seluruh program. Jalankan, buka `GroupShape.docx`, dan Anda akan melihat dua persegi panjang berdiri bersama. Jika Anda memilih satu, seluruh grup akan disorot—tepat seperti yang **group shapes word** lakukan.

---

## Kode sumber lengkap di satu tempat

Untuk kemudahan, berikut contoh lengkap yang siap disalin‑tempel:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Output yang diharapkan:** Membuka `GroupShape.docx` menampilkan halaman kosong dengan dua persegi panjang yang dikelompokkan bersama. Memilih satu persegi panjang secara otomatis memilih yang lain, mengonfirmasi bahwa pengelompokan berhasil.

---

## Pertanyaan umum & penanganan kasus‑tepi

### Bagaimana jika saya membutuhkan lebih dari dua bentuk?

Terus panggil `builder.InsertShape(...)` dan `group.AppendChild(...)` untuk setiap bentuk baru. Grup dapat menampung sejumlah child berapa pun.

### Bisakah saya mengatur warna isi atau border pada persegi panjang?

Tentu saja. Setelah membuat persegi panjang, Anda dapat menyesuaikan `FillColor`, `OutlineColor`, dan `LineWidth`-nya:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Bagaimana cara memindahkan seluruh grup setelah dibuat?

Gunakan properti `Left` dan `Top` pada grup, diukur dalam poin:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Bagaimana dengan skala grup?

Setel `group.Width` dan `group.Height` atau gunakan `group.ScaleX` / `group.ScaleY`. Persegi panjang child mempertahankan proporsinya relatif terhadap grup.

### Apakah ini bekerja dengan file .doc lama?

Aspose.Words mengabstraksi format file, sehingga kode yang sama bekerja untuk `.doc` dan `.docx`. Satu‑satunya keterbatasan adalah beberapa fitur shape terbaru mungkin akan diturunkan ketika menyimpan ke format biner lama.

---

## Tips pro untuk kode siap produksi

- **Dispose of resources** – Bungkus `Document` dalam blok `using` jika Anda menangani file besar untuk membebaskan memori dengan cepat.  
- **Error handling** – Tangkap `Aspose.Words.Fonts.FontSettingsException` jika Anda berencana menyematkan font khusus.  
- **Performance** – Saat menyisipkan banyak shape, nonaktifkan pembaruan layout sementara dengan `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` dan aktifkan kembali setelahnya.

---

## Kesimpulan

Anda kini tahu **how to create blank word document**, **add rectangle shape**, dan **group shapes word** menggunakan Aspose.Words dalam C#. Contoh ini mencakup langkah penting “**how to insert shapes**” dan “**how to group shapes**”, menjelaskan mengapa setiap baris ada, serta menyentuh kustomisasi, kasus‑tepi, dan praktik terbaik.

Selanjutnya, Anda mungkin ingin menjelajahi **how to insert images**, **add text inside grouped shapes**, atau **export the document to PDF**—semua mengikuti pola yang sama menggunakan `DocumentBuilder` dan manipulasi shape. Terus bereksperimen; API Aspose cukup kaya untuk menangani hampir semua skenario otomatisasi Word yang dapat Anda bayangkan.

Selamat coding, dan jangan ragu meninggalkan komentar jika Anda mengalami kendala!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}