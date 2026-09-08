---
category: general
date: 2026-09-08
description: Pelajari cara menyisipkan kontrol konten dalam dokumen Word menggunakan
  C# dan Aspose.Words. Termasuk langkah-langkah untuk membuat kontrol konten, mengatur
  placeholder, dan menyimpan file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: id
lastmod: 2026-09-08
og_description: Masukkan kontrol konten dalam file Word menggunakan C# dan Aspose.Words.
  Ikuti panduan ini untuk membuat kontrol konten, mengatur teks placeholder, dan menyimpan
  dokumen.
og_image_alt: Insert content control example in a Word document
og_title: Menyisipkan kontrol konten di Word dengan C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Cara menyisipkan kontrol konten dalam dokumen Word dengan C#
url: /id/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan kontrol konten dalam dokumen Word dengan C#

Jika Anda perlu **menyisipkan kontrol konten** dalam dokumen Word, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Anda juga akan belajar cara **membuat kontrol konten** secara programatik, mengatur teks placeholder, dan menulis file ke disk.

Kontrol konten memungkinkan Anda mendefinisikan wilayah yang dapat diisi, diulang, atau dikunci oleh pengguna. Mereka banyak digunakan untuk templat, formulir, dan laporan dinamis. Langkah‑langkah di bawah ini menggunakan pustaka Aspose.Words untuk .NET, yang bekerja dengan .NET 6+, .NET Framework 4.6+, dan .NET Core.

## Cara menyisipkan kontrol konten dalam dokumen Word

1. **Tambahkan Aspose.Words ke proyek Anda**  
   Buka terminal di folder proyek dan jalankan:

   ```bash
   dotnet add package Aspose.Words
   ```

   Paket ini berisi kelas `Document`, `DocumentBuilder`, dan `StructuredDocumentTag` yang diperlukan untuk kontrol konten.

2. **Buat dokumen kosong baru**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Objek `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan kursor yang nyaman untuk menyisipkan node.

## Membuat kontrol konten dengan Aspose.Words

Kontrol konten direpresentasikan oleh kelas `StructuredDocumentTag` (SDT). Kode berikut membuat kontrol konten **plain‑text** dan memberinya judul yang dapat Anda query nanti.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Mengapa ini penting:*  
- `SdtType.PlainText` memastikan kontrol hanya menerima karakter teks biasa.  
- `MarkupLevel.Block` membuat kontrol berperilaku seperti paragraf penuh, yang ideal untuk bidang formulir.  
- Properti `Title` adalah pengidentifikasi stabil yang dapat Anda gunakan saat mencari atau mengikat data.

## Mengatur placeholder dan teks default

Placeholder membimbing pengguna sebelum mereka mengetik apa pun. Anda juga dapat mengisi kontrol dengan konten default.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

Fragmen XML harus cocok dengan tipe data kontrol. Untuk kontrol plain‑text, elemen `<text>` diperlukan. Jika Anda melewatkan langkah ini, placeholder yang didefinisikan sebelumnya akan ditampilkan sebagai gantinya.

## Menyisipkan kontrol konten pada lokasi yang diinginkan

Kursor `DocumentBuilder` menentukan di mana kontrol muncul. Secara default, kursor berada di awal dokumen.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Jika Anda memerlukan kontrol di dalam tabel, header, atau setelah paragraf yang ada, pindahkan builder terlebih dahulu:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Menyimpan dokumen dengan kontrol konten yang disisipkan

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

File `SDT.docx` kini berisi kontrol konten plain‑text dengan judul **CustomerName**, placeholder “Enter name here”, dan teks default “John Doe”.

![Contoh penyisipan kontrol konten dalam dokumen Word](insert-content-control.png)

*Teks alt gambar:* Contoh penyisipan kontrol konten dalam dokumen Word

### Hasil yang diharapkan

Saat Anda membuka `SDT.docx` di Microsoft Word:

- Placeholder abu‑abu “Enter name here” muncul jika Anda menghapus teks default.  
- Kontrol disorot ketika Anda mengklik di dalamnya, menandakan dapat diedit.  
- Tab **Developer** (jika diaktifkan) menampilkan judul kontrol **CustomerName** di panel Properties.

## Contoh lengkap yang berfungsi

Berikut adalah program tunggal yang berdiri sendiri yang dapat Anda salin, kompilasi, dan jalankan. Program ini mendemonstrasikan setiap langkah mulai dari penyiapan proyek hingga penyimpanan file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Jalankan program dengan `dotnet run`. Setelah eksekusi, buka file yang dihasilkan untuk memverifikasi bahwa kontrol konten muncul seperti yang dijelaskan.

## Tips praktis dan jebakan umum

| Situasi | Pendekatan yang disarankan |
|-----------|----------------------|
| **Beberapa kontrol dengan tipe yang sama** | Beri setiap kontrol `Title` yang unik. Anda dapat mengambil kontrol kemudian dengan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Kontrol tidak terlihat di Word** | Pastikan Anda menyimpan dokumen dengan ekstensi `.docx` dan bahwa versi `Aspose.Words` kompatibel dengan versi Office Anda. |
| **Membutuhkan kontrol rich‑text** | Gunakan `SdtType.RichText` alih‑alih `PlainText`. Fragmen XML kemudian menggunakan elemen `<w:richText>`. |
| **Menempatkan kontrol di dalam sel tabel** | Pindahkan builder ke sel terlebih dahulu: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Kinerja dengan dokumen besar** | Buat `StructuredDocumentTag` sekali dan gunakan kembali jika Anda memerlukan banyak kontrol identik; kloning dengan `sdt.Clone(true)`. |

## Langkah selanjutnya

- **Buat kontrol konten berulang** (`SdtType.RepeatingSection`) untuk tabel yang tumbuh secara dinamis.  
- **Hubungkan kontrol konten ke data XML** menggunakan `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Kunci kontrol** (`sdt.LockContentControl = true`) untuk mencegah penyuntingan pengguna sambil tetap memperbolehkan pembaruan programatik.  

Mengeksplorasi topik‑topik ini akan memperdalam kemampuan Anda dalam membangun templat Word yang kuat dengan Aspose.Words.

---

**Kesimpulan**  
Anda kini tahu cara **menyisipkan kontrol konten** dalam dokumen Word menggunakan C#. Tutorial ini mencakup pembuatan kontrol, pengaturan placeholder dan teks default, penyisipan pada lokasi yang diinginkan, serta penyimpanan file akhir. Dengan fondasi ini Anda dapat membangun formulir canggih, templat mail‑merge, dan laporan otomatis yang memanfaatkan fitur kontrol‑konten native Word.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Atur Gaya Kontrol Konten](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Atur Warna Kontrol Konten](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}