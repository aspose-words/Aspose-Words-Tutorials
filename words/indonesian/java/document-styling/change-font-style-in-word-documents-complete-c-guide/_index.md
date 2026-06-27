---
category: general
date: 2026-06-27
description: Ubah gaya font dalam dokumen Word dengan C#. Pelajari cara mengatur berat
  font, mengatur berat tebal, dan menyesuaikan lebar font untuk tipografi yang presisi.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: id
og_description: Ubah gaya font di dokumen Word dengan C#. Temukan cara mengatur ketebalan
  font, mengatur berat tebal, dan menyesuaikan lebar font dalam beberapa langkah mudah.
og_title: Ubah Gaya Font di Dokumen Word – Panduan Lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Ubah Gaya Font dalam Dokumen Word – Panduan Lengkap C#
url: /id/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengubah Gaya Font di Dokumen Word – Panduan Lengkap C#

Pernah perlu **mengubah gaya font** dalam file Word tetapi tidak yakin panggilan API mana yang sebenarnya melakukan hal itu? Anda tidak sendirian—kebanyakan pengembang menemui kendala ini saat pertama kali mencoba mengubah tipografi secara programatis.  

Kabar baiknya, dengan beberapa baris C# Anda dapat **mengatur berat font**, bahkan meningkatkan berat menjadi tebal, dan menyesuaikan lebar setiap glyph. Dalam tutorial ini kami akan membimbing Anda melalui contoh lengkap yang dapat dijalankan dan mengubah file `.docx` dari awal hingga akhir.

## Apa yang Dibahas dalam Panduan Ini

Kami akan memulai dengan memuat dokumen yang sudah ada, lalu membuat objek `FontSettings` yang berisi `FontVariation`. Dari sana kami akan **mengatur berat font**, **mengatur berat tebal**, dan **menyesuaikan lebar font** sebelum akhirnya menerapkan perubahan dan menyimpan hasilnya. Tanpa file konfigurasi eksternal, tanpa string ajaib—hanya C# biasa dan pustaka Aspose.Words. Pada akhir tutorial Anda akan dapat **memodifikasi font di Word** dengan percaya diri, baik Anda membangun mesin pelaporan maupun alat pemformatan massal.

### Prasyarat

- .NET 6.0 atau yang lebih baru (kode juga dapat dikompilasi pada .NET Core)  
- Paket NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Sebuah contoh `input.docx` yang ditempatkan di folder yang dapat Anda referensikan (kami akan menyebutnya `YOUR_DIRECTORY`)  

Jika Anda sudah menyiapkan hal‑hal di atas, mari kita mulai.

---

## Langkah 1: Mengubah Gaya Font – Memuat Dokumen Word

Hal pertama yang harus Anda lakukan adalah membawa file target ke dalam memori. Anggap ini seperti membuka kanvas kosong di mana Anda nanti akan melukis tipografi baru Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Pro tip:** Jika Anda menjalankan ini di server tanpa UI, pastikan lisensi Aspose.Words diatur ke mode percobaan atau Anda telah menerapkan file lisensi yang tepat agar tidak muncul pesan watermark.

---

## Langkah 2: Mengatur Berat Font dan Mengatur Berat Tebal

Setelah dokumen berada di memori, kami membuat kontainer `FontSettings`. Objek ini adalah gerbang ke setiap penyesuaian tingkat font yang dapat Anda lakukan.  

Kelas `FontVariation` memungkinkan Anda menentukan tiga atribut inti:

| Properti | Fungsinya | Rentang tipikal |
|----------|-----------|-----------------|
| `Weight` | Mengontrol seberapa berat glyph terlihat. Nilai **700** adalah “tebal” standar. | 100‑900 |
| `Width`  | Meregangkan atau mengecilkan glyph secara horizontal. **100** berarti lebar normal. | 50‑200 |
| `Slant`  | Menambahkan kemiringan mirip italic. Angka positif memiringkan ke kanan. | -90‑90 |

Di bawah ini kami **mengatur berat font** ke 700 (tebal) dan juga menunjukkan cara meningkatkan nilai tersebut jika font Anda mendukung gaya “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Mengapa ini penting:** Mengatur **set bold weight** secara langsung melalui `SetWeight` menghilangkan kebutuhan akan objek gaya “Bold” terpisah, memberi Anda kontrol pixel‑perfect atas seberapa tebal goresan menjadi.

---

## Langkah 3: Menyesuaikan Lebar Font

Jika Anda pernah perlu membuat font terlihat lebih rapat untuk judul atau lebih luas untuk paragraf, Anda akan senang berada di langkah ini. Properti `Width` melakukan tepat hal itu.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Jebakan umum:** Tidak semua jenis huruf menghormati variasi lebar. Jika Anda tidak melihat perubahan visual, periksa apakah keluarga font yang Anda gunakan mendukung glyph yang terkompresi/terluas.

---

## Langkah 4: Menerapkan Pengaturan Font – Memodifikasi Font di Word

Dengan `FontSettings` yang sudah sepenuhnya dikonfigurasi, langkah terakhir adalah memberi tahu dokumen untuk menggunakannya. Di sinilah kami **memodifikasi font di Word** pada tingkat dokumen, memengaruhi setiap run teks yang mewarisi gaya default.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Jika Anda hanya ingin menargetkan paragraf atau run tertentu, Anda dapat mengambil node tersebut dan mengatur `FontSettings` secara individual. Contoh di atas menunjukkan pendekatan luas, yang cocok untuk skenario pemformatan massal.

---

## Langkah 5: Menyimpan dan Memverifikasi Perubahan

Menyimpan adalah bagian terakhir, namun tentu bukan yang paling tidak penting, dari alur kerja. Setelah file dipersistensikan, Anda dapat membukanya di Microsoft Word untuk melihat gaya baru yang diterapkan.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Hasil yang Diharapkan

- Semua teks tubuh yang sebelumnya menggunakan font default kini muncul **tebal** (weight 700).  
- Jika Anda bereksperimen dengan `SetWidth(80)`, karakter akan tampak sedikit lebih rapat; `SetWidth(120)` akan membuatnya lebih tersebar.  
- Tidak ada konten lain (gambar, tabel, dll.) yang diubah—hanya karakteristik font dari run teks.

Buka `output.docx` di Word, pilih sebuah paragraf, dan periksa dialog **Font**. Anda akan melihat kotak centang **Bold** tercentang dan **Scale** (lebar) mencerminkan nilai yang Anda pilih.

---

## Pertanyaan yang Sering Diajukan & Kasus Khusus

### Bisakah saya mengubah keluarga font sekaligus?

Tentu saja. Setelah Anda mengatur `FontVariation`, Anda juga dapat menetapkan `FontInfo` baru ke `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Bagaimana jika saya hanya ingin **mengatur berat tebal** untuk heading?

Ambil node gaya heading dan terapkan instance `FontSettings` terpisah:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Apakah ini bekerja dengan .NET Core di Linux?

Ya—Aspose.Words bersifat lintas‑platform. Pastikan Anda memiliki pustaka runtime yang sesuai terpasang (`libgdiplus` pada beberapa distribusi) jika berencana merender dokumen ke PDF nantinya.

---

## Kesimpulan

Kami baru saja **mengubah gaya font** dalam dokumen Word dari awal hingga akhir, mencakup cara **mengatur berat font**, **mengatur berat tebal**, dan **menyesuaikan lebar font** menggunakan C#. Contoh lengkap yang dapat dijalankan menunjukkan setiap impor, pembuatan objek, dan pemanggilan metode yang diperlukan, sehingga Anda dapat menyalin‑tempelnya ke proyek Anda sendiri dan melihat tipografi berubah secara instan.

Sekarang setelah Anda tahu cara **memodifikasi font di Word**, Anda dapat menjelajahi topik terkait seperti **menyematkan font khusus**, **menerapkan gradien warna**, atau **membuat tabel dinamis**. Semua itu dibangun di atas fondasi `FontSettings` yang sama yang kami gunakan di sini, jadi Anda sudah selangkah lebih maju.

Punya skenario yang belum tercakup? Tinggalkan komentar, dan kami akan membahasnya bersama. Selamat coding—semoga dokumen Anda selalu terlihat persis seperti yang Anda inginkan!  

![change font style example](placeholder.png){alt="contoh mengubah gaya font"}

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}