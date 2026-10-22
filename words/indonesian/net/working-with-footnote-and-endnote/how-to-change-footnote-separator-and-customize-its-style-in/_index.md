---
category: general
date: 2026-10-13
description: Cara mengubah pemisah catatan kaki dalam dokumen Word menggunakan Aspose.Words.
  Pelajari cara mengubah warna font dalam dokumen Word secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: id
lastmod: 2026-10-13
og_description: Cara mengubah pemisah catatan kaki dalam dokumen Word dengan Aspose.Words.
  Tutorial ini menunjukkan cara mengubah warna font dalam dokumen Word menggunakan
  C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Cara mengubah pemisah catatan kaki di dokumen Word – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Cara mengubah pemisah catatan kaki dan menyesuaikan gaya dalam dokumen Word
url: /id/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengubah pemisah catatan kaki dan menyesuaikan gayanya dalam dokumen Word

Jika Anda perlu **cara mengubah pemisah catatan kaki** dalam dokumen Word, panduan ini memberi Anda solusi lengkap yang siap dijalankan. Menggunakan Aspose.Words untuk .NET Anda juga dapat **mengubah warna font dalam dokumen Word** pada elemen seperti pemisah catatan kaki dan catatan akhir, sehingga file akhir sesuai dengan merek atau panduan gaya Anda.

Penulis dokumen sering bertanya: *Mengapa pemisah catatan kaki default terlihat polos, dan bagaimana saya dapat membuatnya menonjol?* Jawabannya adalah dengan mengakses langsung objek paragraf pemisah, menyesuaikan properti font mereka, dan menyimpan hasilnya. Tutorial ini memandu Anda melalui setiap langkah, mulai dari memuat file .docx hingga menyimpan output yang telah bergaya.

Anda akan belajar cara:

* Muat file Word yang sudah berisi catatan kaki dan catatan akhir.  
* Temukan paragraf pemisah catatan kaki dan catatan akhir.  
* Ubah warna font setiap pemisah (merah untuk catatan kaki, biru untuk catatan akhir).  
* Simpan dokumen yang telah dimodifikasi tanpa kehilangan konten yang ada.

Tidak diperlukan alat eksternal selain pustaka Aspose.Words dan lingkungan pengembangan .NET.

## Prasyarat

* .NET 6.0 SDK atau lebih baru (kode juga bekerja dengan .NET Framework 4.7+).  
* Visual Studio 2022, Rider, atau editor C# apa pun yang Anda sukai.  
* Paket NuGet Aspose.Words untuk .NET (`Aspose.Words`).  
* File Word contoh (`Footnotes.docx`) yang berisi setidaknya satu catatan kaki dan satu catatan akhir.

> **Pro tip:** Jika Anda belum memiliki file contoh, buat dokumen Word baru, sisipkan catatan kaki (`References → Insert Footnote`) dan catatan akhir (`References → Insert Endnote`). Simpan sebagai `Footnotes.docx` di folder yang dapat Anda referensikan dari kode.

## Cara mengubah pemisah catatan kaki dengan Aspose.Words

Inti dari tugas ini adalah mengambil paragraf khusus yang diekspos oleh Aspose.Words sebagai node *separator*. Node ini berjenis `Paragraph` dan dapat diformat seperti paragraf lainnya.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Mengapa setiap baris penting

* **Memuat dokumen** (`new Document`) memberi Anda representasi dalam memori yang dapat dimanipulasi oleh Aspose.Words.  
* **`GetChild` dengan `ParagraphNodeType.FootnoteSeparator`** mengembalikan paragraf tersembunyi yang digunakan Word untuk menggambar garis yang memisahkan catatan kaki dari teks utama. Metode yang sama bekerja untuk pemisah catatan akhir.  
* **Mengubah `Font.Color`** secara langsung memengaruhi tampilan garis karena Word merender pemisah sebagai paragraf dengan satu karakter “‑”. Menetapkan warna ke `Color.Red` (atau `System.Drawing.Color` apa pun) memperbarui gaya visual.  
* **Menyimpan** menuliskan perubahan kembali ke file .docx yang dapat dibuka oleh prosesor Word apa pun.

### Output yang diharapkan

Saat Anda membuka `FootnoteSeparatorsStyled.docx` di Microsoft Word:

* Garis pemisah catatan kaki muncul **merah**.  
* Garis pemisah catatan akhir muncul **biru**.  

Semua konten catatan kaki dan catatan akhir asli tetap tidak berubah.

## Mengubah warna font dalam dokumen Word menggunakan C#

Operasi yang ditunjukkan di atas adalah kasus khusus dari kemampuan yang lebih luas: **mengubah warna font dalam dokumen Word** secara programatis. Setelah Anda memiliki `Paragraph`, `Run`, atau `Node` apa pun yang berisi teks, Anda dapat menyesuaikan properti `Font.Color`-nya.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Potongan kode ini mengiterasi setiap paragraf, memeriksa apakah menggunakan gaya `Heading 1`, dan mengatur warna fontnya.  
* Anda dapat menyesuaikan kondisi untuk menargetkan catatan kaki, tabel, atau jenis node lainnya.

## Penjabaran langkah‑demi‑langkah

### 1. Instal Aspose.Words

Buka terminal di folder proyek Anda dan jalankan:

```bash
dotnet add package Aspose.Words
```

Paket ini mencakup semua assembly yang diperlukan untuk kode yang ditunjukkan sebelumnya.

### 2. Siapkan file input

Letakkan `Footnotes.docx` di direktori yang diketahui (mis., `C:\Docs`). Pastikan file tersebut berisi setidaknya satu catatan kaki dan satu catatan akhir agar node pemisah ada.

### 3. Tulis program C#

Buat proyek konsol baru (`dotnet new console -n FootnoteStyler`) dan ganti `Program.cs` yang dihasilkan dengan blok kode lengkap dari bagian **Cara mengubah pemisah catatan kaki**. Ingat untuk menyesuaikan jalur file agar sesuai dengan lingkungan Anda.

### 4. Jalankan dan verifikasi

Jalankan program:

```bash
dotnet run
```

Setelah eksekusi selesai, buka `FootnoteSeparatorsStyled.docx`. Anda akan melihat garis pemisah merah dan biru seperti yang dijelaskan.

### 5. Perluas solusi

* **Warna berbeda:** Gunakan nilai `System.Drawing.Color` apa pun, mis., `Color.FromArgb(255, 128, 0)` untuk oranye.  
* **Gaya garis khusus:** Alih-alih mengubah warna, Anda dapat memodifikasi properti `ParagraphFormat` seperti `LineSpacing`, `Shading`, atau bahkan mengganti karakter pemisah.  
* **Banyak dokumen:** Bungkus logika dalam metode yang menerima jalur input dan output, lalu panggil dalam loop untuk pemrosesan batch.

## Kesalahan umum dan cara menghindarinya

| Gejala | Penyebab | Solusi |
|--------|----------|--------|
| `GetChild` returns `null` | Dokumen sumber tidak memiliki pemisah catatan kaki/catatan akhir (mis., tidak ada catatan kaki). | Tambahkan setidaknya satu catatan kaki atau catatan akhir, atau periksa `null` sebelum mengakses `Font`. |
| Color change not visible | Pemisah dirender sebagai garis bukan karakter pada beberapa versi Word. | Set `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` dan `ParagraphFormat.LineSpacing = 1` untuk memaksa karakter terlihat. |
| Runtime exception `FileNotFoundException` | Jalur file tidak benar. | Gunakan jalur absolut atau `Path.Combine` dengan `Environment.CurrentDirectory`. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup penanganan kesalahan dan komentar yang menjelaskan setiap operasi.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Menjalankan program ini menghasilkan file Word di mana garis pemisah catatan kaki berwarna merah dan garis pemisah catatan akhir berwarna biru, memenuhi persyaratan **cara mengubah pemisah catatan kaki** sekaligus menunjukkan **mengubah warna font dalam dokumen word**.

## Kesimpulan

Anda kini tahu **cara mengubah pemisah catatan kaki** dalam dokumen Word menggunakan Aspose.Words untuk .NET dan cara **mengubah warna font dalam dokumen Word** secara programatis. Pendekatannya adalah:

1. Muat dokumen.  
2. Ambil paragraf pemisah tersembunyi.  
3. Atur properti `Font.Color` mereka.  
4. Simpan file yang telah dimodifikasi.

Dari sini Anda dapat menjelajahi styling yang lebih maju—menyesuaikan ketebalan garis, menerapkan font berbeda, atau mengotomatisasi proses pada banyak file. Menguasai teknik ini memberi Anda kontrol detail atas tampilan dokumen Word langsung dari kode C#.

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Dapatkan Pemisah Gaya Paragraf dalam Dokumen Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Tambahkan Nomor Halaman ke Footer Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}