---
category: general
date: 2026-02-12
description: Buat penangan peringatan font untuk mendeteksi font yang hilang dan melacak
  font yang hilang di Aspose.Words. Pelajari cara mencatat peringatan secara efisien.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: id
og_description: Buat penangan peringatan font di C# untuk mendeteksi font yang hilang
  dan pelajari cara mencatat peringatan ketika Aspose.Words mengganti font.
og_title: Buat Penangan Peringatan Font – Deteksi Font yang Hilang
tags:
- Aspose.Words
- C#
- Document Processing
title: Buat Penangan Peringatan Font – Deteksi Font yang Hilang di C#
url: /id/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Penangan Peringatan Font – Deteksi Font yang Hilang di C#

Pernah perlu **membuat penangan peringatan font** karena dokumen Word secara diam‑diam mengganti font yang tidak Anda harapkan? Anda tidak sendirian. Ketika Aspose.Words memuat DOCX yang merujuk pada font yang tidak ada di server, ia secara diam‑diam beralih ke font default—menyebabkan tata letak Anda sedikit rusak.  

Dalam tutorial ini kami akan menunjukkan cara **mendeteksi font yang hilang**, **melacak font yang hilang**, dan **cara mencatat peringatan** sehingga Anda dapat melihat substitusi tersebut sebelum menimbulkan masalah. Pada akhir tutorial Anda akan memiliki penangan peringatan yang dapat digunakan kembali yang mencetak setiap peristiwa substitusi font ke konsol (atau logger apa pun yang Anda pilih). Tidak ada misteri, hanya kode yang jelas dan dapat ditindaklanjuti.

## Prasyarat

- .NET 6.0 atau lebih baru (API sama untuk .NET Framework 4.6+)
- Aspose.Words untuk .NET terpasang (`dotnet add package Aspose.Words`)
- File Word yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya `MissingFont.docx`)

Jika Anda sudah memiliki semua itu, bagus—mari kita mulai.

## Langkah 1: Siapkan LoadOptions dengan Callback Peringatan  

Hal pertama yang Anda lakukan ketika ingin **membuat penangan peringatan font** adalah memberi tahu Aspose.Words untuk memicu callback setiap kali menemukan masalah. `LoadOptions` adalah wadah untuk konfigurasi tersebut.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Mengapa ini penting:**  
`LoadOptions` adalah satu‑satunya tempat Anda dapat menyambungkan `IWarningCallback`. Tanpa itu, Aspose.Words akan mencatat peringatan secara internal tetapi Anda tidak akan pernah melihatnya. Dengan menetapkan `FontWarningHandler` kita memperoleh kontrol penuh atas apa yang terjadi ketika font yang hilang disubstitusi.

## Langkah 2: Implementasikan Kelas FontWarningHandler  

Sekarang kita benar‑benar **membuat penangan peringatan font**. Kelas ini mengimplementasikan `IWarningCallback` dan menerima objek `WarningInfo` untuk setiap peringatan yang dihasilkan Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Penjelasan:**  
- `info.Type` memberi tahu kita kategori peringatannya. Kita peduli pada `WarningType.FontSubstitution` karena itulah yang menandakan font yang hilang.  
- `info.Description` berisi pesan yang dapat dibaca manusia seperti *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Dengan menulis ke `Console.WriteLine` kita **mencatat peringatan** secara langsung. Pada aplikasi dunia nyata Anda mungkin menggantinya dengan `ILogger`, penulis file, atau layanan telemetri.

> **Tips pro:** Jika Anda perlu mengumpulkan semua font yang hilang untuk pelaporan nanti, simpan `info.Description` dalam `List<string>` alih‑alih mencetaknya.

## Langkah 3: Muat Dokumen Menggunakan LoadOptions yang Telah Dikonfigurasi  

Dengan callback yang sudah dipasang, memuat dokumen secara otomatis akan memicu penangan kita setiap kali ada font yang hilang.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Apa yang akan Anda lihat:**  
Menjalankan program mencetak sesuatu yang mirip dengan:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Baris itu mengonfirmasi bahwa Anda telah berhasil **mendeteksi font yang hilang** dan kini **melacak font yang hilang** secara real‑time.

## Langkah 4: Verifikasi Penangan Bekerja dengan Berbagai Skenario  

Mudah mengasumsikan penangan hanya bekerja untuk file DOCX, tetapi Aspose.Words mendukung banyak format. Cobalah memuat PDF yang merujuk pada font ter‑embed, atau file `.doc` lama. Callback yang sama dipicu untuk format apa pun yang melewati pipeline resolusi font.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Jika PDF merujuk pada font yang tidak terpasang, Anda akan mendapatkan output konsol yang sama. Ini menunjukkan bahwa solusi **membuat penangan peringatan font** Anda bersifat format‑agnostik.

## Langkah 5: Memperluas Penangan – Mencatat ke File  

Output ke konsol berguna untuk demo, tetapi kode produksi biasanya menulis ke file log. Berikut penyesuaian singkatnya.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Sekarang setiap kali font disubstitusi, pesan akan ditambahkan ke `font-warnings.log`. Ini memenuhi bagian **cara mencatat peringatan** dari brief dan memberi Anda jejak audit yang persisten.

## Langkah 6: Menggabungkan Semua – Contoh Lengkap yang Dapat Dijalan  

Di bawah ini adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Tidak ada bagian yang hilang; cukup ganti jalur file dengan dokumen Anda sendiri.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Hasil yang diharapkan:**  

- Konsol mencetak setiap baris substitusi.  
- `font-warnings.log` kini berisi catatan ber‑timestamp dari setiap peristiwa font yang hilang.  
- File `output.pdf` dibuat menggunakan font yang telah disubstitusi, memastikan konversi berhasil meskipun font asli tidak tersedia.

## Pertanyaan Umum & Kasus Pojok  

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika saya ingin mengabaikan font tertentu?* | Di dalam `Warning`, periksa `info.Description` untuk nama font dan `return;` lebih awal untuk font yang Anda anggap dapat diterima. |
| *Apakah penangan akan dipicu untuk font yang ter‑embed?* | Tidak—font yang ter‑embed selalu tersedia bagi dokumen, sehingga tidak ada peringatan substitusi. |
| *Bisakah saya menangkap tipe peringatan lain (misalnya masalah resolusi gambar)?* | Tentu saja. Hapus guard `if (info.Type == WarningType.FontSubstitution)` atau tambahkan blok `if` tambahan untuk `WarningType.ImageResolution`. |
| *Apakah penangan ini thread‑safe?* | Implementasi default yang ditunjukkan menulis ke file tanpa sinkronisasi. Untuk skenario multi‑thread, bungkus penulisan file dengan `lock` atau gunakan logger yang bersifat concurrent. |

## Langkah Selanjutnya  

Sekarang Anda tahu **cara mencatat peringatan** untuk font yang hilang, Anda mungkin ingin:

- **Mendeteksi font yang hilang** selama proses impor batch dan menghasilkan laporan ringkasan.  
- **Melacak font yang hilang** di banyak dokumen dan mengirimkan peringatan email ketika font tertentu muncul secara sering.  
- **Mengintegrasikan dengan sistem pemantauan** (misalnya Azure Application Insights) untuk menampilkan tren substitusi font dari waktu ke waktu.  

Semua ekstensi ini dibangun di atas fondasi `IWarningCallback` yang telah kita buat.

---

*Selamat coding! Jika Anda menemukan keanehan—mungkin folder font khusus atau share jaringan—tinggalkan komentar di bawah. Komunitas (dan saya) selalu senang membantu Anda menyempurnakan strategi peringatan font Anda.* 

![contoh membuat penangan peringatan font](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}