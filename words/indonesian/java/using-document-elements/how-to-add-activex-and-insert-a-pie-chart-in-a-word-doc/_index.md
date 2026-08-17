---
category: general
date: 2026-08-17
description: Cara menambahkan kontrol ActiveX dan menyisipkan diagram lingkaran dalam
  dokumen Word menggunakan Aspose.Words. Memisahkan irisan dan menyimpan sebagai DOCX
  dalam beberapa langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: id
lastmod: 2026-08-17
og_description: Cara menambahkan kontrol ActiveX, menyisipkan diagram pai, memisahkan
  irisan, dan menyimpan sebagai DOCX dengan Aspose.Words – panduan lengkap langkah
  demi langkah.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Cara menambahkan ActiveX dan menyisipkan diagram lingkaran di dokumen Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Cara menambahkan ActiveX dan menyisipkan diagram lingkaran di dokumen Word
url: /id/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan ActiveX dan menyisipkan diagram pai dalam dokumen Word

Jika Anda perlu **menambahkan ActiveX** kontrol dan menyisipkan diagram dalam dokumen Word, tutorial ini menunjukkan solusi lengkap yang dapat dijalankan. Dengan menggunakan Aspose.Words Anda dapat menempatkan ActiveX CommandButton, membuat diagram pai, meletuskan satu irisan untuk penekanan, dan akhirnya **menyimpan sebagai DOCX** hanya dalam beberapa baris C#.

Di bagian-bagian berikut Anda akan melihat setiap impor yang diperlukan, daftar kode lengkap, dan penjelasan mengapa setiap langkah penting. Pada akhir tutorial Anda akan dapat mengintegrasikan kontrol interaktif dan data visual ke dalam file .docx apa pun yang Anda hasilkan secara programatik.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau lebih baru (kode juga bekerja dengan .NET Framework 4.7+)
* Paket Aspose.Words untuk .NET (tersedia via NuGet)
* Lingkungan pengembangan seperti Visual Studio 2022 atau VS Code
* Pemahaman dasar tentang C# dan model objek Word

Tidak ada perpustakaan diagram pihak ketiga tambahan yang diperlukan—Aspose.Words menyediakan pembuatan diagram bawaan.

## Cara menambahkan kontrol ActiveX dengan Aspose.Words

Kontrol ActiveX memungkinkan Anda menyematkan elemen UI interaktif langsung di dalam file Word. Dalam panduan ini kami menambahkan sebuah **CommandButton** yang nantinya dapat dihubungkan ke kode VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Mengapa ini berhasil:**  
`InsertForms2OleControl` membuat kontainer OLE yang dikenali UI Word sebagai kontrol ActiveX. Menetapkan tipe kontrol ke `CommandButton` dan memberi caption membuatnya berperilaku seperti tombol standar ketika pengguna membuka file di Word.

## Sisipkan diagram pai dan letuskan sebuah irisan

Diagram berguna untuk memvisualisasikan data tanpa meninggalkan dokumen. Langkah-langkah berikut mendemonstrasikan **cara menyisipkan diagram** dan khususnya sebuah **diagram pai** yang irisan pertamanya diletuskan.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Mengapa meletuskan irisan:**  
Memanggil `SetExplode(0, true)` memberi tahu Aspose.Words untuk menggeser titik data pertama, menarik perhatian pemirsa ke segmen tersebut. Ini adalah teknik umum dalam presentasi untuk menyoroti nilai kunci.

## Simpan sebagai DOCX

Setelah menambahkan tombol ActiveX dan diagram, simpan dokumen ke disk. Langkah ini mendemonstrasikan **menyimpan sebagai DOCX** menggunakan metode standar.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

File `Output.docx` kini berisi tombol interaktif, diagram pai dengan irisan yang diletuskan, dan dapat dibuka di Microsoft Word tanpa plugin tambahan.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut adalah program mandiri yang dapat Anda salin ke aplikasi konsol dan jalankan segera.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Hasil yang diharapkan:**  
Membuka `Output.docx` di Word menampilkan tombol berlabel *Click Me* dan diagram pai di mana irisan pertama (January) terpisah dari yang lain. Tombol siap untuk penanganan peristiwa VBA, dan diagram dapat diedit menggunakan alat diagram bawaan Word.

## Pertanyaan umum dan kasus tepi

* **Apakah saya dapat menambahkan tipe ActiveX lain?**  
  Ya. Ganti `Forms2OleControlType.CommandButton` dengan nilai apa pun dari enum `Forms2OleControlType` (misalnya `CheckBox`, `OptionButton`). Pola penyisipan yang sama berlaku.

* **Bagaimana jika saya membutuhkan tipe diagram lain?**  
  Gunakan `ChartType.Bar`, `ChartType.Line`, dll., pada pemanggilan `InsertChart`. Langkah **cara menyisipkan diagram** tetap sama; hanya nilai enum yang berubah.

* **Bagaimana mengontrol ukuran irisan yang diletuskan?**  
  Aspose.Words saat ini hanya mendukung flag explode biner (true/false). Untuk kontrol yang lebih halus (misalnya jarak offset) Anda harus mengedit OOXML dasar setelah menyimpan.

* **Apakah dokumen kompatibel dengan versi Word yang lebih lama?**  
  Menyimpan sebagai DOCX memastikan kompatibilitas dengan Word 2007 ke atas. Untuk Word 2003 Anda dapat mengubah menjadi `SaveFormat.Doc` tetapi dukungan ActiveX terbatas pada format tersebut.

* **Apakah saya perlu merujuk `System.Drawing`?**  
  Tidak. Semua objek gambar disediakan oleh Aspose.Words, jadi satu‑satunya paket NuGet yang diperlukan adalah `Aspose.Words`.

## Kesimpulan

Anda kini tahu **cara menambahkan ActiveX**, **menyisipkan diagram pai**, **meletuskan irisan pai**, dan **menyimpan sebagai DOCX** menggunakan Aspose.Words untuk .NET. Contoh lengkap mencakup setiap langkah dari pembuatan dokumen hingga penyimpanan akhir, serta menjelaskan alasan di balik setiap pemanggilan API.

Selanjutnya, Anda dapat menjelajahi:

* Menambahkan makro VBA yang merespon klik CommandButton (**cara menyisipkan diagram** dan mengotomatisasi pembaruan data)
* Menyesuaikan tampilan diagram (warna, label data) agar sesuai dengan identitas perusahaan
* Menyematkan kontrol ActiveX tambahan seperti **ComboBox** atau **ListBox** untuk formulir yang lebih kaya

Silakan bereksperimen dengan kode, ganti data contoh, dan integrasikan solusi ini ke dalam pipeline pembuatan dokumen Anda sendiri. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}