---
category: general
date: 2026-04-01
description: Aktifkan Peringatan Font saat memuat dokumen Word dengan Aspose.Words.
  Pelajari cara menangkap peristiwa substitusi font menggunakan LoadOptions C# dan
  Pengaturan Font.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: id
og_description: Aktifkan Peringatan Font saat memuat dokumen Word dengan Aspose.Words.
  Tutorial ini menunjukkan cara menangkap peristiwa substitusi font di C#.
og_title: Aktifkan Peringatan Font di Aspose.Words – Panduan Lengkap C#
tags:
- Aspose.Words
- C#
- Font Management
title: Aktifkan Peringatan Font di Aspose.Words – Panduan Lengkap C#
url: /id/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan Peringatan Font di Aspose.Words – Panduan Lengkap C# 

Pernah bertanya-tanya mengapa dokumen Word tiba‑tiba terlihat berbeda setelah Anda memuatnya secara programatis? **Enable Font Warnings** dan Anda akan langsung tahu kapan Aspose.Words mengganti font yang hilang dengan font cadangan. Dalam tutorial ini kami akan membahas contoh langsung yang tidak hanya menangkap substitusi tersebut tetapi juga menjelaskan *mengapa* hal itu terjadi.

Kami akan membahas semua yang Anda perlukan untuk memulai: paket NuGet yang diperlukan, konfigurasi `LoadOptions` yang tepat, dan output konsol yang rapi yang memberi tahu Anda font mana yang diganti. Pada akhir tutorial Anda akan memiliki pola yang kuat dan dapat digunakan kembali untuk **C# document processing** yang bekerja dengan versi Aspose.Words mana pun.

## Apa yang Akan Anda Pelajari

- Cara membuat instance `LoadOptions` yang melacak perubahan font.  
- Tujuan dari event `SubstitutionWarning` dan cara menghubungkannya.  
- Contoh kode lengkap yang dapat dijalankan yang mencetak peringatan jelas ke konsol.  
- Tips untuk menangani kasus tepi seperti dokumen yang hanya berisi font standar.  

Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words—hanya pemahaman dasar tentang C# dan .NET.

---

![Diagram mengaktifkan peringatan font](placeholder-image.png "Diagram mengaktifkan peringatan font")

*Teks alternatif: diagram mengaktifkan peringatan font yang menunjukkan alur peristiwa ketika font yang hilang digantikan.*

## Langkah 1: Siapkan LoadOptions dan Aktifkan Peringatan Font

Hal pertama yang Anda butuhkan adalah objek `LoadOptions`. Kontainer ini memberi tahu Aspose.Words bagaimana memperlakukan file yang akan Anda muat. Dengan menetapkan instance `FontSettings` yang baru, Anda membuka pintu ke peristiwa terkait font.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Mengapa ini penting:**  
Jika Anda melewatkan penetapan `FontSettings`, Aspose.Words tetap akan mengganti font yang hilang, tetapi Anda tidak akan menerima pemberitahuan apa pun. Mekanisme peringatan berada di dalam `FontSettings`, sehingga menginisialisasinya *krusial* untuk tujuan kami.

> **Pro tip:** Anda juga dapat mengarahkan `FontSettings` ke folder font khusus menggunakan `SetFontsFolder`. Hal itu mengurangi jumlah peringatan yang akan Anda lihat, karena Aspose.Words dapat menemukan jenis huruf yang hilang.

## Langkah 2: Langganan ke Event SubstitutionWarning (substitusi font)

Sekarang objek `FontSettings` sudah ada, kami mengaitkan ke event `SubstitutionWarning`-nya. Event ini dipicu **setiap kali** Aspose.Words mengganti font yang diminta dengan yang lain.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Mengapa ini penting:**  
Tanpa pendengar ini Anda tidak akan memiliki visibilitas ke proses substitusi. Baris konsol memberi Anda jejak audit cepat, yang sangat berguna selama build otomatis atau saat menghasilkan PDF untuk industri dengan kepatuhan tinggi.

> **Pertanyaan umum:** *Bagaimana jika saya ingin menekan peringatan?*  
> Anda cukup melepaskan handler atau mengatur `FontSettings.SubstitutionWarning += null;`. Namun, mempertahankan peringatan biasanya merupakan jalur paling aman karena substitusi diam dapat menyebabkan gangguan tata letak.

## Langkah 3: Muat Dokumen Anda dengan Opsi yang Dikonfigurasi (C# document processing)

Dengan sistem peringatan siap, memuat dokumen menjadi sederhana. Berikan instance `LoadOptions` ke konstruktor `Document`, dan Aspose.Words akan melakukan sisanya.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Mengapa ini penting:**  
Objek `LoadOptions` adalah jembatan antara file mentah dan infrastruktur peringatan. Jika Anda mengabaikannya, dokumen akan dimuat secara diam-diam, dan semua font yang hilang akan diganti tanpa jejak.

> **Kasus tepi:** Beberapa dokumen menyertakan file font yang tepat yang mereka butuhkan. Dalam skenario tersebut tidak akan muncul peringatan karena Aspose.Words menemukan font yang disematkan. Kode di atas tetap berfungsi; Anda hanya akan melihat output konsol kosong.

## Langkah 4: Verifikasi Output dan Kesalahan Umum

Jalankan program dari command‑prompt atau debugger IDE Anda. Jika dokumen sumber berisi font yang tidak terpasang di mesin (atau tidak tersedia di folder font khusus), Anda akan melihat baris seperti:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Jika tidak ada yang tercetak, maka:

1. Semua font ditemukan, **atau**  
2. Handler `SubstitutionWarning` tidak terpasang dengan benar (periksa kembali Langkah 2).

### Mengapa Substitusi Font Terjadi?

- **Font sistem hilang:** OS tidak memiliki jenis huruf yang diminta.  
- **Format font tidak didukung:** Aspose.Words dapat membaca TrueType dan OpenType, tetapi tidak semua format proprietari.  
- **Pembatasan lisensi:** Beberapa font komersial memblokir penyematan, memaksa penggunaan fallback.

Memahami *mengapa* membantu Anda memutuskan apakah akan menyertakan font yang hilang bersama aplikasi Anda atau menyesuaikan gaya dokumen.

## Bonus: Mengontrol Font Fallback

Jika Anda ingin setiap font yang hilang beralih ke keluarga tertentu (misalnya, “Calibri”), Anda dapat mengatur aturan substitusi global:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Sekarang konsol masih akan memperingatkan Anda, tetapi hasil visual akan konsisten di semua font yang hilang.

---

## Ringkasan

- **Aktifkan Peringatan Font** dengan membuat `LoadOptions` dengan `FontSettings` yang baru.  
- Kaitkan event `SubstitutionWarning` untuk mendapatkan peringatan waktu‑nyata setiap kali font diganti.  
- Muat dokumen Anda menggunakan opsi yang dikonfigurasi, dan opsional menyimpan ke PDF untuk melihat efek visual.  
- Diagnosa mengapa substitusi terjadi dan, jika diperlukan, paksa font fallback tertentu.

Anda baru saja menambahkan jaring pengaman ke alur kerja **Aspose.Words** Anda yang mencegah perubahan tata letak diam-diam. Selanjutnya, Anda mungkin ingin menjelajahi **font settings** seperti `DefaultFontName` atau menyelami opsi **document rendering** untuk menyempurnakan output PDF.

---

### Apa yang Bisa Dicoba Selanjutnya?

- **Jelajahi fitur FontSettings lainnya**: `SetFontsFolder`, `LoadFontSources`, dan `DefaultFontName`.  
- **Gabungkan peringatan dengan kerangka kerja logging** (Serilog, NLog) untuk diagnostik tingkat produksi.  
- **Bereksperimen dengan berbagai format dokumen** (`.doc`, `.rtf`, `.html`) untuk melihat bagaimana masing‑masing menangani font yang hilang.  

Ada pertanyaan atau skenario unik? Tinggalkan komentar di bawah, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}