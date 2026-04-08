---
category: general
date: 2026-01-05
description: Cara menangkap font dengan cepat dan menangani font yang hilang menggunakan
  Aspose.Words. Pelajari solusi langkah demi langkah dengan kode C# lengkap.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: id
og_description: Cara menangkap font di Aspose.Words dan menangani font yang hilang.
  Ikuti panduan terperinci ini untuk implementasi C# yang dapat diandalkan.
og_title: Cara Menangkap Font di Aspose.Words – Tutorial Lengkap
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Menangkap Font di Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Font di Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya **bagaimana cara menangkap font** saat memuat dokumen Word dengan Aspose.Words? Anda tidak sendirian. Font yang hilang dapat menyebabkan gangguan tata letak yang halus, dan tanpa peringatan yang tepat Anda mungkin tidak menyadarinya sampai PDF akhir terlihat tidak tepat. Dalam tutorial ini kami akan menunjukkan secara tepat cara **menangkap font** **dan** menangani font yang hilang sehingga output Anda tetap pixel‑perfect.

Kami akan membahas skenario dunia nyata, menyiapkan callback peringatan, dan memberikan contoh C# yang siap dijalankan. Pada akhir tutorial Anda akan mengerti mengapa hal ini penting, cara mengimplementasikannya, dan hal‑hal yang perlu diwaspadai ketika font menghilang dari lingkungan Anda.

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi **LoadOptions** untuk mendengarkan peringatan terkait font.  
- Peran **IWarningCallback** dan **WarningInfo** dalam Aspose.Words.  
- Tips praktis untuk memecahkan masalah dan mencatat font yang hilang.  
- Contoh kode lengkap, mandiri, yang dapat Anda tempelkan ke Visual Studio dan jalankan seketika.

**Prasyarat:** .NET 6+ (atau .NET Framework 4.7.2+), Aspose.Words untuk .NET terpasang via NuGet, dan pemahaman dasar tentang C#. Tidak diperlukan pustaka lain.

---

## Langkah 1: Siapkan Load Options untuk Menangkap Font

Hal pertama yang kita butuhkan adalah instance **LoadOptions**. Objek ini memberi tahu Aspose.Words bagaimana berperilaku saat membaca dokumen. Dengan menetapkan **IWarningCallback** kustom, kita dapat menyela setiap peringatan substitusi font yang terjadi selama proses pemuatan.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Mengapa ini penting:**  
Aspose.Words secara diam-diam mengganti font yang hilang dengan font default kecuali Anda memintanya untuk memberi tahu. Dengan menambahkan callback, kita **menangkap informasi font** tepat pada saat pemuatan, memberi kesempatan untuk mencatat, mengganti, atau bahkan membatalkan operasi.

> **Pro tip:** Simpan `loadOptions` sebagai variabel yang dapat dipakai ulang jika Anda memproses banyak dokumen dalam satu batch. Ini menghindari pembuatan kembali callback yang sama berulang‑ulang.

---

## Langkah 2: Muat Dokumen dengan Opsi yang Telah Dikonfigurasi

Setelah callback siap, kita muat dokumen. Konstruktor **Document** menerima jalur file dan **LoadOptions** yang baru saja kita atur.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Jika ada font yang hilang, Aspose.Words akan memicu peringatan yang akan diterima oleh `FontWarningCollector` kami. Dokumen tetap akan dimuat, tetapi Anda akan memiliki catatan jelas tentang font mana yang disubstitusi.

---

## Langkah 3: Implementasikan FontWarningCollector – Tangani Font yang Hilang

Inti dari **cara menangkap font** terletak pada kelas `FontWarningCollector`. Kelas ini mengimplementasikan `IWarningCallback` dan menyaring hanya peristiwa `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Penjelasan:**  
- `info.Type` memberi tahu kategori peringatan. Dengan memeriksa `FontSubstitution` kita **menangani font yang hilang** tanpa memenuhi output dengan pesan tidak relevan (misalnya fitur yang sudah usang).  
- `info.Description` berisi pesan yang dapat dibaca manusia seperti “Font 'Comic Sans MS' was substituted with 'Arial'.” Ini adalah data yang tepat untuk mengaudit inventaris font Anda.

> **Waspada:** Jika Anda perlu menghentikan pemrosesan ketika font penting hilang, lemparkan pengecualian di dalam blok `if` alih‑alih hanya mencetak.

---

## Langkah 4: Verifikasi Output – Apa yang Diharapkan

Jalankan program dari konsol atau IDE Anda. Untuk setiap font yang hilang, Anda akan melihat baris seperti:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Jika semua font tersedia, callback tetap diam dan dokumen dimuat tanpa masalah. Anda kini dapat melanjutkan dengan menyimpan, mengonversi, atau mencetak dokumen dengan yakin bahwa Anda telah **menangkap informasi font**.

---

## Langkah 5: Contoh Lengkap yang Berfungsi (Semua Bagian Bersatu)

Berikut adalah program lengkap yang siap disalin‑tempel. Program ini mencakup direktif `using`, implementasi callback, dan demonstrasi singkat menyimpan dokumen yang dimuat sebagai PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Menjalankan kode:**  
1. Buat proyek konsol baru (`dotnet new console -n FontCaptureDemo`).  
2. Tambahkan paket Aspose.Words (`dotnet add package Aspose.Words`).  
3. Ganti `Program.cs` yang dihasilkan dengan cuplikan di atas.  
4. Letakkan file DOCX yang sengaja merujuk pada font yang tidak Anda miliki (misalnya “Papyrus”).  
5. Jalankan (`dotnet run`). Amati konsol untuk pesan substitusi, lalu buka `output.pdf` untuk memverifikasi tata letaknya.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan daftar font yang hilang nanti?

Simpan pesan‑pesan tersebut dalam `List<string>` di dalam `FontWarningCollector` dan expose melalui properti. Dengan cara ini Anda dapat menuliskan daftar ke file log setelah memproses banyak dokumen.

### Apakah ini bekerja dengan file yang terenkripsi atau dilindungi password?

Ya, tetapi Anda juga harus menyediakan password melalui `LoadOptions.Password`. Callback peringatan berfungsi sama setelah dokumen didekripsi.

### Bisakah saya mengganti font yang hilang dengan fallback khusus?

Tentu saja. Di dalam metode `Warning` Anda dapat memanggil `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Ini memastikan substitusi bersifat deterministik.

### Apakah ini memengaruhi performa?

Overheadnya minimal—pada dasarnya satu pemanggilan metode per peringatan. Dalam batch ribuan dokumen dampaknya dapat diabaikan dibandingkan biaya I/O saat memuat tiap file.

---

## Kesimpulan

Kami telah membahas **cara menangkap font** di Aspose.Words, menunjukkan **cara menangani font yang hilang** dengan callback peringatan yang bersih, dan menyediakan contoh lengkap yang dapat dijalankan. Dengan menyematkan pola ini ke dalam pipeline pemrosesan dokumen Anda, Anda tidak akan lagi terkejut oleh substitusi font yang diam-diam.

Siap untuk langkah selanjutnya? Cobalah memperluas collector untuk menulis log JSON, mengintegrasikan dengan dasbor pemantauan, atau secara otomatis menyematkan font yang hilang ke dalam PDF output. Kemungkinannya tak terbatas, dan kini Anda memiliki fondasi yang kuat.

Selamat coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}