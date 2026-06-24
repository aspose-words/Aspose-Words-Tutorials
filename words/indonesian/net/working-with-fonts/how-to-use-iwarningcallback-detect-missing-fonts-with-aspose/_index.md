---
category: general
date: 2026-06-24
description: Cara menggunakan IWarningCallback untuk mendeteksi font yang hilang dalam
  dokumen Aspose.Words. Pelajari contoh lengkap yang dapat dijalankan dan praktik
  terbaik.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: id
og_description: Cara menggunakan IWarningCallback untuk mendeteksi font yang hilang
  di Aspose.Words. Ikuti panduan langkah demi langkah untuk solusi lengkap yang siap
  produksi.
og_title: Cara Menggunakan IWarningCallback – Deteksi Font yang Hilang
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Menggunakan IWarningCallback – Mendeteksi Font yang Hilang dengan Aspose.Words
url: /id/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan IWarningCallback – Mendeteksi Font yang Hilang dengan Aspose.Words

Cara menggunakan **IWarningCallback** sangat penting ketika Anda bekerja dengan Aspose.Words dan perlu **mendeteksi font yang hilang** dalam file DOCX. Pada panduan ini kami akan menelusuri contoh lengkap yang dapat disalin‑tempel yang menunjukkan secara tepat cara menggunakan IWarningCallback untuk menangkap peringatan substitusi font, mengapa hal ini penting, dan apa yang harus dilakukan setelah Anda menanganinya.

Jika Anda pernah membuka dokumen dan melihat teks yang berantakan karena font khusus tidak terpasang, Anda pasti tahu rasa frustrasinya. Pada akhir tutorial ini Anda akan memiliki cara yang dapat diandalkan untuk menampilkan masalah tersebut secara programatis, mencatatnya, atau bahkan menerapkan font cadangan secara otomatis.

## Apa yang Akan Anda Pelajari

- Tujuan **IWarningCallback** dan kapan harus menggunakannya.  
- Cara mengimplementasikan kolektor peringatan khusus yang mengisolasi peristiwa **detect missing fonts**.  
- Menyambungkan kolektor ke **LoadOptions** sehingga setiap pemuatan dokumen dipantau.  
- Memverifikasi output dan menangani kasus tepi (banyak font yang hilang, peringatan diam, dll.).  

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi pada .NET Framework 4.6+).  
- Aspose.Words for .NET terpasang melalui NuGet (`Install-Package Aspose.Words`).  
- File DOCX yang merujuk pada font yang tidak ada di mesin (misalnya `DocumentWithMissingFont.docx`).  

Tidak ada pustaka tambahan yang diperlukan—semuanya berada di dalam Aspose.Words.

---

## Cara Menggunakan IWarningCallback untuk Mendeteksi Font yang Hilang di Aspose.Words

Berikut adalah **program lengkap yang dapat dijalankan**. Salin ke proyek konsol baru, sesuaikan jalur file, dan jalankan. Anda akan melihat output konsol untuk setiap peringatan font yang hilang.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Output yang Diharapkan

Jika `DocumentWithMissingFont.docx` merujuk pada font bernama *“MyFancyFont”* yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Setiap baris yang diawali dengan **[Missing Font]** dihasilkan oleh implementasi **IWarningCallback** kami, membuktikan bahwa kami berhasil **detect missing fonts**.

---

## Langkah 1: Implementasikan Interface IWarningCallback

Mengapa kita memerlukan kelas khusus? Aspose.Words menghasilkan **peringatan** untuk berbagai alasan—masalah format file, fitur yang sudah usang, dan, yang paling penting bagi kita, substitusi font. Dengan mengimplementasikan `IWarningCallback`, kita mendapatkan hook yang menerima setiap peringatan saat terjadi. Menyaring `WarningType.FontSubstitution` mengisolasi skenario khusus di mana sebuah font tidak tersedia.

**Tips pro:** Jika Anda perlu menangkap *semua* peringatan untuk diagnostik, cukup hapus pengecekan `if` dan catat setiap `info.Type`.

---

## Langkah 2: Sambungkan Callback ke LoadOptions

`LoadOptions` adalah gerbang yang memberi tahu Aspose.Words bagaimana memperlakukan dokumen yang masuk. Menetapkan `WarningCallback` ke instance kolektor kami memastikan callback aktif selama seluruh operasi pemuatan. Anda dapat menggunakan kembali objek `LoadOptions` yang sama untuk beberapa dokumen, yang sangat berguna dalam pipeline pemrosesan batch.

**Pertanyaan umum:** *Bagaimana jika saya memuat dokumen tanpa menentukan LoadOptions?*  
Jawaban: Aspose.Words tetap akan menghasilkan peringatan secara internal, tetapi tanpa callback peringatan tersebut dibuang secara diam‑diam, dan Anda kehilangan kesempatan untuk **detect missing fonts**.

---

## Langkah 3: Muat Dokumen dan Tangkap Peringatan Font yang Hilang

Konstruktor `Document` yang menerima jalur file dan `LoadOptions` melakukan pekerjaan berat. Saat file diurai, setiap font yang hilang memicu metode `FontWarningCollector.Warning` kami. Output konsol membuktikan mekanisme ini berfungsi.

**Kasus tepi:** Sebuah dokumen dapat merujuk pada beberapa font yang tidak ada. Callback dipanggil sekali per font yang hilang, sehingga Anda akan melihat beberapa baris—sempurna untuk membangun laporan komprehensif.

---

## Mengapa Menggunakan IWarningCallback Daripada Pemeriksaan Font Manual?

Anda bisa memindai properti `Run.Font` dokumen secara manual setelah dimuat, tetapi itu mengharuskan dokumen berhasil dimuat terlebih dahulu—sesuatu yang gagal jika font benar‑benar tidak tersedia. Sistem peringatan bekerja **sebelum** substitusi apa pun terjadi, memberi Anda gambaran yang akurat tentang apa yang hilang.

Selain itu, callback dijalankan **sebagai bagian dari pipeline pemuatan**, artinya Anda dapat menghentikan proses lebih awal, mengganti font secara dinamis, atau mencatat diagnostik terperinci tanpa harus melakukan pass tambahan pada pohon dokumen.

---

## Menangani Banyak Font yang Hilang dengan Elegan

Jika Anda memperkirakan banyak font yang hilang, pertimbangkan untuk mengumpulkannya ke dalam koleksi:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Setelah pemuatan selesai, Anda dapat mengiterasi `MissingFonts` dan, misalnya, menuliskannya ke file CSV untuk tim desain.

---

## Bonus: Mencatat Peringatan ke File

Output konsol cukup untuk demo, tetapi kode produksi biasanya mencatat ke penyimpanan yang persisten. Ganti pemanggilan `Console.WriteLine` dengan sesuatu seperti:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Sekarang Anda memiliki jejak audit yang dapat ditinjau nanti, memenuhi persyaratan kepatuhan.

---

## Kesimpulan

Kami telah membahas **cara menggunakan IWarningCallback** untuk **detect missing fonts** di Aspose.Words, mulai dari mengimplementasikan callback hingga menyambungkannya ke `LoadOptions` dan menangani peringatan yang dihasilkan. Pendekatan ini memberi Anda wawasan waktu nyata tentang masalah terkait font, memungkinkan Anda mencatat, mengganti, atau memberi peringatan kepada pengguna sebelum dokumen dirender.

Langkah selanjutnya yang dapat Anda jelajahi:

- **Font cadangan:** secara programatis menetapkan font default ketika terjadi substitusi.  
- **Pemrosesan batch:** loop melalui folder berisi dokumen, menggunakan kembali `AggregatingFontCollector` yang sama.  
- **Umpan balik pengguna:** menampilkan peringatan font yang hilang di UI alih‑alih konsol.

Cobalah di proyek Anda—tidak ada lagi teks berantakan yang misterius, hanya diagnostik yang jelas dan dapat ditindaklanjuti. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Memuat DOCX dan Mendeteksi Font yang Hilang – Panduan C# Lengkap](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Cara Mendeteksi Font di Aspose.Words – Menangani Peringatan & Pengaturan](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}