---
"description": "Pelajari cara menambahkan dan menyesuaikan header dan footer dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini memastikan pemformatan dokumen yang profesional."
"linktitle": "Buat Header dan Footer"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Buat Header dan Footer"
"url": "/id/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat Header dan Footer

## Perkenalan

Menambahkan header dan footer ke dokumen Anda dapat meningkatkan profesionalisme dan keterbacaannya. Dengan Aspose.Words untuk .NET, Anda dapat dengan mudah membuat dan menyesuaikan header dan footer untuk dokumen Word Anda. Dalam tutorial ini, kami akan memandu Anda melalui proses ini langkah demi langkah, memastikan Anda dapat menerapkan fitur-fitur ini dengan lancar.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

- Aspose.Words untuk .NET: Unduh dan instal dari [tautan unduhan](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Seperti Visual Studio, untuk menulis dan menjalankan kode Anda.
- Pengetahuan Dasar C#: Pemahaman tentang C# dan kerangka kerja .NET.
- Dokumen Contoh: Dokumen contoh untuk menerapkan header dan footer, atau membuat yang baru seperti yang ditunjukkan dalam tutorial.

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan untuk mengakses kelas dan metode Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Langkah 1: Tentukan Direktori Dokumen

Tentukan direktori tempat dokumen Anda akan disimpan. Ini membantu dalam mengelola jalur secara efektif.

```csharp
// Jalur ke direktori dokumen
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Langkah 2: Buat Dokumen Baru

Buat dokumen baru dan `DocumentBuilder` untuk memfasilitasi penambahan konten.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Konfigurasikan Pengaturan Halaman

Siapkan pengaturan halaman, termasuk apakah halaman pertama akan memiliki header/footer yang berbeda.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Langkah 4: Tambahkan Header ke Halaman Pertama

Pindah ke bagian header untuk halaman pertama dan konfigurasikan teks header.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Langkah 5: Tambahkan Header Utama

Pindah ke bagian header utama dan masukkan gambar dan teks.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Masukkan gambar ke dalam header
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Langkah 6: Tambahkan Footer Utama

Pindah ke bagian footer utama dan buat tabel untuk memformat konten footer.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Tambahkan penomoran halaman
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Langkah 7: Tambahkan Konten dan Hentian Halaman

Pindah ke akhir dokumen, tambahkan jeda halaman, dan buat bagian baru dengan pengaturan halaman yang berbeda.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Langkah 8: Salin Header dan Footer dari Bagian Sebelumnya

Jika Anda ingin menggunakan kembali header dan footer dari bagian sebelumnya, salin dan terapkan modifikasi yang diperlukan.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat menambahkan dan menyesuaikan header dan footer secara efektif di dokumen Word Anda menggunakan Aspose.Words for .NET. Ini akan meningkatkan tampilan dan profesionalisme dokumen Anda, membuatnya lebih mudah dibaca dan menarik.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?

Aspose.Words untuk .NET adalah pustaka yang memungkinkan pengembang untuk membuat, mengedit, dan mengonversi dokumen Word secara terprogram dalam aplikasi .NET.

### Bisakah saya menambahkan gambar ke header atau footer?

Ya, Anda dapat dengan mudah menambahkan gambar ke header atau footer menggunakan `DocumentBuilder.InsertImage` metode.

### Bagaimana cara mengatur header dan footer yang berbeda untuk halaman pertama?

Anda dapat mengatur header dan footer yang berbeda untuk halaman pertama dengan menggunakan `DifferentFirstPageHeaderFooter` milik `PageSetup` kelas.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words?

Anda dapat menemukan dokumentasi lengkap di [Halaman dokumentasi API Aspose.Words](https://reference.aspose.com/words/net/).

### Apakah ada dukungan yang tersedia untuk Aspose.Words?

Ya, Aspose menawarkan dukungan melalui [forum dukungan](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}