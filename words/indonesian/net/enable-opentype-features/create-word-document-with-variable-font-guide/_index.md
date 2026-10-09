---
category: general
date: 2026-03-19
description: Buat dokumen Word menggunakan Aspose.Words dan font variabel. Pelajari
  cara mengubah ketebalan font, mengatur lebar font, dan mendefinisikan variasi font
  dalam C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: id
og_description: Buat dokumen Word dengan font variabel menggunakan Aspose.Words. Tutorial
  ini menunjukkan cara memuat font, mengubah ketebalan font, mengatur lebar font,
  dan mendefinisikan variasi font.
og_title: Buat Dokumen Word dengan Font Variabel – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Variable Font
title: Buat Dokumen Word dengan Font Variabel – Panduan
url: /id/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word dengan Font Variabel – Panduan

Pernah perlu **membuat dokumen word** yang menggunakan font variabel modern, tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian. Dalam banyak proyek—bayangkan laporan dinamis atau brosur yang konsisten dengan merek—kemampuan untuk **mengubah ketebalan font** secara langsung adalah perubahan yang signifikan.  

Dalam tutorial ini kami akan membahas seluruh proses: mulai dari memuat font variabel ke Aspose.Words, mengatur berat dan lebar font, hingga menyimpan DOCX yang terlihat persis seperti yang Anda rancang. Tanpa referensi yang samar, hanya kode konkret yang dapat Anda masukkan ke proyek C# Anda sekarang.

## Apa yang Akan Anda Pelajari

- Cara **memuat file font variabel** ke Aspose.Words menggunakan `FontSettings`.
- Sintaks untuk **mendefinisikan variasi font** pada sumbu seperti `wght` (berat) dan `wdth` (lebar).
- Cara **mengatur lebar font** dan **mengubah berat font** pada satu `Run`.
- Tips untuk memecahkan masalah umum (glyph yang hilang, jalur folder yang salah, dll.).
- Contoh lengkap yang dapat dijalankan, yang dapat Anda salin‑tempel dan uji secara instan.

> **Prasyarat**: .NET 6+ (atau .NET Framework 4.6+), Aspose.Words untuk .NET yang diinstal via NuGet, dan file font variabel seperti *RobotoFlex.ttf* yang ditempatkan di folder *Fonts* lokal.

---

## Langkah 1 – Muat Font Variabel ke Aspose.Words

Pertama, kita harus memberi tahu Aspose.Words di mana mencari font kustom kami. Kelas `FontSettings` melakukan pekerjaan berat.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Mengapa ini penting**: Tanpa mendaftarkan folder, Aspose.Words akan kembali ke font sistem dan mengabaikan data variasi OpenType yang Anda coba terapkan nanti. Dengan menunjuk ke direktori tertentu, Anda menjamin bahwa *RobotoFlex* (atau font variabel lain) ditemukan setiap kali kode dijalankan.

> **Tips pro**: Atur parameter kedua dari `SetFontsFolder` ke `true` jika Anda ingin Aspose mencari sub‑folder juga. Ini membantu ketika Anda mengatur font berdasarkan gaya atau berat.

---

## Langkah 2 – Buat Dokumen Baru dan Tambahkan Teks Contoh

Sekarang mesin font tahu ke mana harus mencari, kami membuat `Document` kosong dan menyisipkan paragraf dengan `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Apa yang terjadi**: `Run` mewakili potongan teks berurutan dengan format seragam. Dengan membuatnya terlebih dahulu, kami menjaga logika format terisolasi—sempurna untuk kemudian menerapkan sumbu variasi yang berbeda pada run terpisah bila diperlukan.

---

## Langkah 3 – Definisikan Sumbu Variasi yang Diinginkan (Berat & Lebar)

Font variabel mengekspos *sumbu* yang dapat Anda sesuaikan pada waktu berjalan. Dua yang paling umum adalah `wght` (berat font) dan `wdth` (lebar font). Aspose.Words memodelkan ini dengan koleksi `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Mengapa angka-angka ini**: Dalam spesifikasi OpenType, `wght` berkisar dari berat minimum hingga maksimum font (sering 100–900). Nilai **700** menghasilkan tampilan tebal. `wdth` bekerja serupa; **100** berarti lebar default (normal), sementara nilai di bawah 100 memperkecil glyph.

> **Kasus tepi**: Beberapa font variabel tidak mendukung sumbu tertentu. Jika Anda memberikan tag yang tidak didukung, Aspose akan mengabaikannya secara diam-diam. Selalu periksa kembali spesifikasi font (biasanya terdapat di metadata file `.ttf` atau `.otf`).

---

## Langkah 4 – Terapkan Variasi ke Run Menggunakan Nama Font

Sekarang kami mengikat data variasi ke teks sebenarnya. Kelas `FontInfo` menyimpan nama keluarga font dan koleksi sumbu.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Penjelasan**: Dengan mengatur `FontInfo`, kami melewati properti `Font.Name` biasa dan memberikan mesin konfigurasi font yang sepenuhnya memenuhi syarat. Ini satu‑satunya cara untuk memberi tahu Aspose.Words menggunakan font variabel dengan sumbu kustom.

> **Kesalahan umum**: Lupa mencocokkan nama keluarga yang tepat di dalam file font (`RobotoFlex` dalam contoh ini). Kesalahan ketik akan menyebabkan Aspose kembali ke font default, dan variasi Anda akan hilang.

---

## Langkah 5 – Simpan Dokumen dan Verifikasi Hasil

Akhirnya, tulis dokumen ke disk. DOCX yang dihasilkan akan berisi instruksi font‑variabel, yang dapat dirender dengan benar oleh Microsoft Word (2016+).

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Buka file yang dihasilkan di Word, pilih teks, dan lihat dialog **Font**. Anda harus melihat *Roboto Flex* terdaftar, dan teks akan muncul lebih tebal daripada konten sekitarnya—tepat seperti pengaturan `wght = 700` yang kami minta.

> **Tips verifikasi**: Jika teks tampak tidak berubah, periksa kembali bahwa file font benar‑benar mendukung sumbu `wght`. Beberapa font “variabel” hanya mengekspos `ital` (italic) atau `opsz` (ukuran optik).

---

## Opsional: Tambahkan Lebih Banyak Variasi – Mengubah Lebar Secara Dinamis

Jika Anda ingin *mengatur lebar font* secara berbeda untuk paragraf lain, cukup ulangi langkah 3‑4 dengan koleksi `OpenTypeFontVariation` baru.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Sekarang Anda memiliki dua run—satu tebal, satu sedikit lebih lebar—menunjukkan baik **mengubah berat font** maupun **mengatur lebar font** dalam dokumen yang sama.

---

## Contoh Lengkap yang Berfungsi

Salin potongan kode di bawah ini ke aplikasi konsol baru (`Program.cs`) dan jalankan. Pastikan folder `Fonts` berisi `RobotoFlex.ttf` (atau font variabel lain yang Anda pilih).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Output yang diharapkan**: File `VariableFont.docx` di mana frasa “Variable‑weight text” muncul tebal, berkat sumbu `wght = 700`, sambil mempertahankan lebar default.

---

## Pertanyaan yang Sering Diajukan & Kasus Tepi

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika font tidak ditemukan?* | Verifikasi jalur folder, pastikan nama file cocok, dan proses memiliki izin baca. Anda juga dapat memanggil `fontSettings.GetFonts()` untuk menampilkan font yang terdeteksi. |
| *Apakah saya dapat menggabungkan beberapa run dengan variasi berbeda?* | Tentu saja. Setiap `Run` dapat membawa `FontInfo`‑nya sendiri. Cukup ulangi langkah 3‑4 untuk setiap run. |
| *Apakah versi Word yang lebih lama mendukung font variabel?* | Word 2016 (Build 16.0.8001) memperkenalkan dukungan dasar. Jika Anda menargetkan versi yang lebih lama, dokumen akan kembali ke instance statis terdekat dari font tersebut. |
| *Apakah ada batas berapa banyak sumbu yang dapat saya atur?* | Anda dapat mengatur sebanyak apa pun yang didefinisikan font. Tag umum adalah `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Menyediakan tag yang tidak didukung tidak memberikan efek apa pun. |
| *Bagaimana cara men-debug glyph yang hilang?* | Gunakan `FontSettings.GetFontSources()` untuk memeriksa font yang dimuat, dan `FontInfo.HasGlyph(char)` untuk menguji karakter individu. |

---

## Kesimpulan

Dalam beberapa langkah kami telah menunjukkan **cara membuat dokumen word** yang memanfaatkan kekuatan font variabel, memungkinkan Anda **mengubah berat font**, **mengatur lebar font**, **memuat file font variabel**, dan **mendefinisikan sumbu variasi font**—semua dengan Aspose.Words untuk .NET.  

Ide dasarnya sederhana: daftarkan folder font, jelaskan sumbu yang diinginkan, lampirkan ke `Run`, dan simpan. Dari sini Anda dapat memperluas teknik ini ke seluruh bagian, tabel, atau bahkan menghasilkan laporan khusus merek secara programatik.

**Langkah selanjutnya**: coba ganti `RobotoFlex` dengan font variabel lain, bereksperimen dengan sumbu `ital` (italic), atau hasilkan versi PDF dari dokumen yang sama menggunakan Aspose.PDF. Pola yang sama berlaku—muat, definisikan, terapkan, simpan.

Selamat coding, dan nikmati fleksibilitas yang dibawa font variabel ke proyek otomatisasi Word Anda!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}