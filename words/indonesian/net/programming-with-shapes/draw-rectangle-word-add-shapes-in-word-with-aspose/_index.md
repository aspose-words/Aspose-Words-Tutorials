---
category: general
date: 2026-07-29
description: menggambar kata persegi panjang menggunakan Aspose.Words. Pelajari cara
  menambahkan bentuk persegi panjang, menambahkan bentuk garis, dan mengelola beberapa
  bentuk kata dalam satu dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: id
lastmod: 2026-07-29
og_description: gambar persegi panjang di Word dengan Aspose.Words. Ikuti panduan
  langkah demi langkah ini untuk menambahkan bentuk persegi panjang, menambahkan bentuk
  garis, dan bekerja dengan banyak bentuk di Word dengan mudah.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: gambar persegi panjang di Word – Kuasai Menambahkan Bentuk di Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Menggambar Persegi Panjang di Word – Tambahkan Bentuk di Word dengan Aspose
url: /id/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Panduan Lengkap Menambahkan Bentuk di Word

Pernah bertanya-tanya bagaimana cara **draw rectangle word** dokumen tanpa harus membuka UI setiap kali? Anda tidak sendirian. Banyak pengembang perlu menghasilkan file Word secara dinamis, dan cara termudah adalah membiarkan sebuah library melakukan pekerjaan berat. Dalam tutorial ini kami akan menunjukkan secara tepat **cara menambahkan bentuk**—khususnya sebuah persegi panjang dan sebuah garis—menggunakan Aspose.Words untuk .NET, dan kami akan tetap fokus pada frasa *draw rectangle word* agar Anda tidak tersesat.

Anggap saja ini sebagai studio seni mini yang hidup di dalam kode Anda. Pada akhir tutorial Anda akan dapat **menambahkan bentuk persegi panjang**, **menambahkan bentuk garis**, dan bahkan menggabungkannya menjadi grup **multiple shapes word**. Tanpa UI, tanpa penyesuaian manual, hanya C# yang bersih dan dapat diulang.

## Apa yang Akan Anda Pelajari

- Menyiapkan dokumen Word baru dengan Aspose.Words.  
- Membuat **GroupShape** yang dapat menampung beberapa objek.  
- **Menambahkan bentuk persegi panjang** dan **menambahkan bentuk garis** di dalam grup tersebut.  
- Menyisipkan grup bentuk ke dalam badan dokumen.  
- Menyimpan file dan melihat hasilnya secara langsung.  

Jika Anda sudah nyaman dengan C# dasar dan memiliki salinan Aspose.Words, Anda siap. Tidak ada paket NuGet tambahan selain pustaka inti yang diperlukan.

> **Pro tip:** Aspose.Words bekerja dengan .NET 6, .NET 7, dan .NET Framework 4.6+. Pilih runtime yang sesuai dengan proyek Anda.

![contoh draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – bentuk terkelompok dalam file Word")

## draw rectangle word – Menyiapkan Dokumen

Sebelum kita dapat **draw rectangle word** kita memerlukan kanvas bersih. Kelas `Document` adalah kanvas itu; `DocumentBuilder` adalah kuas kita.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Dua baris di atas memberi kita sebuah `.docx` baru di memori. Tidak ada yang ditulis ke disk terlebih dahulu, yang berarti kita dapat bereksperimen tanpa mengotori sistem file.

## Cara Menambahkan Bentuk – Membuat Kontainer GroupShape

Ketika Anda ingin **multiple shapes word** berperilaku sebagai satu unit—bergerak bersama, berputar bersama—Anda membungkusnya dalam sebuah `GroupShape`. Anggap grup sebagai folder yang menampung bentuk‑bentuk lain.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Mengapa grup? Karena nanti Anda mungkin ingin **menambahkan bentuk persegi panjang** dan **menambahkan bentuk garis**, lalu memindahkannya bersama. Tanpa grup, Anda harus memposisikan setiap bentuk secara terpisah.

## add rectangle shape – Menyisipkan Persegi Panjang ke Dalam Grup

Sekarang kontainer sudah ada, mari **add rectangle shape**. Sebuah persegi panjang adalah `Shape` yang `ShapeType`‑nya adalah `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Perhatikan nilai `Left` dan `Top` relatif terhadap asal grup, bukan halaman. Ini memudahkan penyusunan bentuk secara presisi. Persegi panjang akan muncul di dekat sudut kiri‑atas grup.

## add line shape – Menambahkan Garis ke Grup yang Sama

Sebuah garis hanyalah `Shape` lain, tetapi `ShapeType`‑nya adalah `Line`. Kita akan menempatkannya di bawah persegi panjang.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Karena tinggi garis adalah nol, properti `Top` menentukan posisi vertikal garis. `Width` mengontrol seberapa panjang garis memanjang secara horizontal.

## multiple shapes word – Menyisipkan Grup ke Dalam Badan Dokumen

Kita memiliki grup yang kini memuat **add rectangle shape** dan **add line shape**. Langkah terakhir adalah menaruh seluruh grup ke dalam dokumen.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` menempatkan grup tepat pada posisi di mana `DocumentBuilder` saat ini berada. Jika Anda membutuhkannya pada paragraf tertentu, pindahkan builder dengan `builder.MoveToParagraph(index)` terlebih dahulu.

## Menyimpan Hasil – Melihat Output draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Buka file yang dihasilkan di Microsoft Word dan Anda akan melihat satu grup yang berisi persegi panjang dan garis. Anda dapat mengklik grup, menyeretnya, atau bahkan mengubah ukurannya—semua bentuk bergerak bersama. Itulah kekuatan **multiple shapes word**.

### Output yang Diharapkan

- File `.docx` bernama `GroupShape.docx`.  
- Satu halaman dengan persegi panjang berkelompok (120 × 80 pt) di dekat sudut kiri‑atas.  
- Garis horizontal (panjang 150 pt) yang ditempatkan tepat di bawah persegi panjang.  
- Kedua bentuk dapat dipilih sebagai satu objek tunggal.

Jika Anda double‑click grup, Word akan memungkinkan Anda mengedit setiap bentuk secara terpisah—sempurna untuk penyetelan halus.

## Pertanyaan Umum & Kasus Tepi

**Bagaimana jika saya membutuhkan lebih dari dua bentuk?**  
Terus panggil `group.AppendChild(yourShape)` untuk setiap objek tambahan. Grup dapat menampung sejumlah bentuk apa pun, menjadikannya ideal untuk diagram kompleks.

**Bisakah saya mengubah warna isi persegi panjang?**  
Tentu saja. Setelah membuat persegi panjang, setel `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Ini berlaku untuk semua bentuk yang mendukung pengisian.

**Apakah saya harus menyetel `Height = 0` untuk sebuah garis?**  
Ya, untuk garis horizontal lurus tinggi harus nol. Untuk garis vertikal, setel `Width = 0` dan berikan `Height` nilai positif.

**Apakah ini akan bekerja dengan file .doc (Word 97‑2003)?**  
Aspose.Words dapat menyimpan ke format `.doc` lama, tetapi beberapa fitur bentuk modern mungkin terbatas. Gunakan `.docx` untuk fidelitas penuh.

**Bagaimana cara memutar seluruh grup?**  
Anda dapat menyetel `group.Rotation = 45;` (derajat) sebelum menyisipkannya. Rotasi akan diterapkan ke setiap bentuk anak.

## Ringkasan – Cara Menambahkan Bentuk di Word Secara Programatis

- **draw rectangle word** dimulai dengan membuat `Document` dan `DocumentBuilder`.  
- Bangun sebuah **GroupShape** untuk menampung **multiple shapes word**.  
- **add rectangle shape** dan **add line shape** ditambahkan ke dalam grup.  
- Sisipkan grup ke dalam badan dokumen dengan `builder.InsertNode`.  
- Simpan file dan buka untuk memverifikasi hasil visual.

Itulah seluruh alur kerja, dibungkus dalam satu listing kode yang mudah dibaca.

## Langkah Selanjutnya & Topik Terkait

Sekarang Anda sudah tahu **cara menambahkan bentuk**, pertimbangkan untuk mengeksplorasi:

- **add rectangle shape** dengan sudut melengkung (`ShapeType.Rectangle` + `CornerRadius`).  
- Menata garis dengan pola dash yang berbeda (`line.LineFormat.DashStyle`).  
- Menyisipkan gambar bersamaan dengan bentuk untuk laporan yang lebih kaya.  
- Menggunakan **multiple shapes word** untuk membangun flowchart atau diagram UML sederhana.  

Masing‑masing topik ini dibangun secara natural di atas fondasi yang telah kami jelaskan, dan semuanya mengikuti pola yang sama: membuat bentuk, mengkonfigurasinya, dan mengelompokkannya bila diperlukan.

---

Selamat coding! Jika Anda menemukan kejanggalan atau memiliki kasus penggunaan menarik untuk dibagikan, tinggalkan komentar di bawah. Masukan Anda membantu kita semua menguasai seni **draw rectangle word** dan seterusnya.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}