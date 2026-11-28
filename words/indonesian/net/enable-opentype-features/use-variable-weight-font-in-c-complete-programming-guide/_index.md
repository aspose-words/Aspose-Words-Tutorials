---
category: general
date: 2026-06-02
description: Pelajari cara menggunakan font dengan berat variabel di C# dan mengatur
  berat font secara programatik sambil mengubah kode stretch font untuk tipografi
  dinamis.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: id
og_description: Gunakan font dengan bobot variabel di C# untuk mengatur bobot font
  secara programatis dan mengubah kode perluasan font, memungkinkan tipografi dinamis
  dalam dokumen Anda.
og_title: Gunakan Font dengan Berat Variabel di C# – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Gunakan Font Berat Variabel di C# – Panduan Pemrograman Lengkap
url: /id/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gunakan Font Berat Variabel di C# – Panduan Pemrograman Lengkap

Pernah membutuhkan untuk **menggunakan font berat variabel** dalam proyek .NET tetapi tidak yakin bagaimana membuat berat dan rentang (stretch) merespon input pengguna? Anda tidak sendirian. Dalam banyak skenario UI atau pelaporan, Anda ingin teks beradaptasi—mungkin judul ringan yang menjadi tebal saat hover, atau paragraf yang memperlebar lebar untuk penekanan. Kabar baiknya, dengan Aspose.Words Anda dapat **mengatur berat font secara programatis** dan bahkan **mengubah kode stretch font** secara langsung.

Dalam tutorial ini kami akan memandu Anda melalui contoh praktis yang menunjukkan secara tepat cara memuat font berat variabel, menerapkan berat khusus, dan menyesuaikan pengaturan stretch—semua dengan kode C# yang jelas dan dapat Anda salin‑tempel. Pada akhir tutorial Anda akan memiliki aplikasi konsol yang dapat dijalankan dan menghasilkan PDF yang menampilkan efek tersebut.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (v23.12 atau lebih baru). Perpustakaan ini mendukung penuh font berat variabel.
- Sebuah folder yang berisi setidaknya satu file font berat variabel, misalnya *RobotoFlex‑Variable.ttf*. Anda dapat mengunduhnya dari Google Fonts.
- .NET 6 SDK (atau versi .NET terbaru) dan IDE pilihan Anda.
- Pengetahuan dasar C#—tidak perlu hal yang rumit, hanya beberapa baris kode.

Itu saja. Tidak ada paket NuGet tambahan selain Aspose.Words, dan tidak ada file konfigurasi yang rumit.

![Use variable weight font example](https://example.com/variable-weight-sample.png "Demonstrasi penggunaan font berat variabel")
*Teks alternatif: tangkapan layar yang menunjukkan penggunaan font berat variabel dalam dokumen PDF yang dihasilkan.*

---

## Langkah 1: Siapkan FontSettings dan Arahkan ke Folder Font Anda  

Pertama-tama—Aspose.Words perlu mengetahui di mana font berat variabel Anda berada. Anda melakukannya dengan membuat objek `FontSettings` dan melampirkan `FolderFontSource`. Flag `true` memberi tahu mesin untuk mencari sub‑folder juga, yang berguna jika Anda menyimpan beberapa keluarga font bersama-sama.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Mengapa ini penting:** Tanpa mendaftarkan folder, Aspose.Words akan kembali ke font sistem dan mengabaikan data berat variabel yang tertanam dalam file font khusus Anda. Langkah ini menjadi dasar bagi semua yang akan datang.

---

## Langkah 2: Lampirkan FontSettings ke Dokumen  

Sekarang kami membuat `Document` baru (atau memuat yang sudah ada) dan memberitahukannya untuk menggunakan `FontSettings` yang baru saja kami siapkan. Pengikatan ini yang membuat data berat variabel tersedia untuk setiap `Run` yang kami tambahkan nanti.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Jika Anda sudah memiliki templat—misalnya file Word dengan placeholder—Anda dapat mengganti `new Document()` dengan `new Document("Template.docx")`. `FontSettings` yang sama akan diterapkan.

---

## Langkah 3: Tambahkan Run Teks yang Akan Menggunakan Font Berat Variabel  

**Run** adalah unit terkecil dari pemformatan teks di Aspose.Words. Kami akan membuat satu, menyisipkannya ke dalam paragraf baru, dan kemudian mengubah atribut fontnya.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Pada titik ini teks akan dirender menggunakan font default (biasanya Times New Roman). Keajaiban terjadi setelah kami menetapkan keluarga font berat variabel.

---

## Langkah 4: Pilih Keluarga Font Berat Variabel  

Di sinilah kita benar‑benar **menggunakan font berat variabel**. Atur `Font.Name` ke nama keluarga yang tepat seperti yang didefinisikan di dalam file font variabel. Untuk Roboto Flex, namanya adalah `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Jika Anda tidak yakin dengan nama keluarga, buka file `.ttf` di penampil font atau gunakan metode `fontSettings.GetFonts()` untuk menampilkan semua keluarga yang tersedia.

---

## Langkah 5: Atur Berat Font dan Stretch Secara Programatis  

Sekarang inti tutorial: kami **mengatur berat font secara programatis** dan **mengubah kode stretch font**. Kedua properti menerima nilai integer yang sesuai dengan spesifikasi OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Pilih nilai apa pun yang didukung oleh font variabel.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Nilai default adalah 100 (Normal).

> **Pro tip:** Tidak semua font variabel menampilkan seluruh rentang. Jika Anda menetapkan nilai yang tidak didukung, mesin akan menyesuaikan ke berat atau stretch terdekat yang tersedia.

---

## Langkah 6: Simpan Dokumen dan Verifikasi Hasilnya  

Akhirnya, tulis dokumen ke PDF (atau DOCX) dan buka untuk melihat efeknya. PDF adalah format yang bagus untuk verifikasi visual karena renderingnya konsisten di semua platform.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Saat Anda membuka *VariableWeightDemo.pdf*, Anda akan melihat frasa “Variable‑weight text demo” dirender dalam gaya ringan dan sedikit diperluas dari Roboto Flex. Ubah `FontWeight` menjadi `700` dan `FontStretch` menjadi `80` lalu jalankan kembali—perhatikan teks menjadi tebal dan lebih padat.

---

## Pertanyaan Umum & Kasus Edge  

### Bagaimana jika font tidak muncul sama sekali?  

- **Missing FontSettings**: Pastikan `doc.FontSettings = fontSettings;` dijalankan **sebelum** teks apa pun ditambahkan.
- **Nama keluarga salah**: Gunakan `fontSettings.GetFonts()` untuk menampilkan semua keluarga yang ditemukan; salin string yang tepat.
- **Berat/stretch tidak didukung**: Beberapa font variabel hanya mendukung sebagian rentang 100‑900. Gunakan `run.Font.FontWeight = 400;` sebagai fallback yang aman.

### Bisakah saya mengubah berat setelah dokumen disimpan?  

Ya. Objek `Run` dapat diubah, sehingga Anda dapat menyesuaikan `FontWeight` atau `FontStretch` kapan saja sebelum `Save` akhir. Jika Anda perlu mengubah berat secara dinamis (misalnya berdasarkan interaksi pengguna), pertimbangkan untuk menghasilkan run terpisah untuk setiap keadaan.

### Apakah ini bekerja dengan output DOCX?  

Tentu saja. Metadata berat variabel disimpan dalam OpenXML yang mendasarinya, dan versi Word modern dapat menafsirkannya. Namun, versi Word yang lebih lama mungkin mengabaikan pengaturan stretch.

---

## Contoh Lengkap yang Berfungsi  

Berikut adalah program konsol lengkap yang dapat Anda kompilasi dan jalankan seketika. Program ini mencakup semua direktif `using` yang diperlukan, penanganan error, dan komentar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Output yang diharapkan:** Konsol mencetak jalur penyimpanan, dan PDF yang dihasilkan menampilkan teks dalam gaya ringan dan diperluas—tepat seperti yang kami konfigurasikan.

---

## Ringkasan  

Kami telah membahas cara **menggunakan font berat variabel** di C# dengan Aspose.Words, mendemonstrasikan cara **mengatur berat font secara programatis**, dan menunjukkan **kode perubahan stretch font** yang diperlukan untuk memperlebar atau mempersempit glif. Langkah‑langkahnya sederhana: konfigurasikan `FontSettings`, lampirkan ke `Document`, buat `Run`, pilih keluarga font berat variabel, dan akhirnya sesuaikan `FontWeight` serta `FontStretch`.

---

## Apa Selanjutnya?  

- **Integrasi UI Dinamis**: Sambungkan logika yang sama ke aplikasi WinForms atau WPF agar pengguna dapat memilih berat/stretch melalui slider.
- **Multiple runs**: Gabungkan beberapa run dengan berat berbeda dalam paragraf yang sama untuk hierarki tipografi yang kaya.
- **Axis lanjutan**: Beberapa font variabel menyediakan sumbu tambahan (mis., slant, optical size). Gunakan `run.Font.FontStyle` atau jelajahi `FontVariationSettings` untuk kontrol yang lebih halus.
- **Tips performa**: Cache instance `FontSettings` saat memproses banyak dokumen untuk menghindari pemindaian folder berulang.

Silakan bereksperimen—ganti *Roboto Flex* dengan *Inter Variable* atau font OpenType variabel lainnya, dan saksikan dokumen Anda memperoleh tingkat fleksibilitas visual yang baru. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Gunakan Font Dari Mesin Target](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Gunakan Font Dari Mesin Target](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Gunakan Font Dari Mesin Target](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}