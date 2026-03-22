---
category: general
date: 2026-03-22
description: Simpan Dokumen Word dan deteksi font yang hilang menggunakan Aspose.Words.
  Pelajari cara melacak font yang hilang dan menangkap kesalahan font di C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: id
og_description: Simpan Dokumen Word dan deteksi font yang hilang di C#. Panduan ini
  menunjukkan cara melacak font yang hilang dan menangkap kesalahan font menggunakan
  callback peringatan.
og_title: Simpan Dokumen Word – Deteksi Font yang Hilang dengan Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Simpan Dokumen Word – Deteksi Font yang Hilang dengan Aspose.Words
url: /id/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Dokumen Word – Deteksi Font yang Hilang dengan Aspose.Words

Pernahkah Anda perlu **save word document** tetapi tidak yakin apakah beberapa font di dalamnya akan bertahan setelah proses penyimpanan? Hal ini terjadi lebih sering daripada yang Anda kira, terutama ketika dokumen berpindah antar mesin dengan perpustakaan font yang berbeda. Kabar baiknya? Aspose.Words menyediakan cara bawaan untuk **detect missing fonts** saat Anda **save word document**, sehingga Anda dapat mencatat, memberi peringatan, atau bahkan menggantinya sebelum file muncul di layar pengguna.

Dalam tutorial ini kami akan membimbing Anda melalui contoh lengkap yang siap dijalankan, yang tidak hanya menyimpan dokumen Word tetapi juga **tracks missing fonts** dan **captures font errors** menggunakan handler peringatan khusus. Pada akhir tutorial Anda akan mengerti mengapa callback peringatan penting, cara menghubungkannya, dan seperti apa output konsol ketika terjadi substitusi. Tanpa tambahan yang tidak perlu—hanya kode yang dapat Anda tempelkan ke proyek .NET Anda sekarang.

> **Prerequisites**  
> • .NET 6 (atau .NET Framework terbaru) terpasang  
> • Visual Studio 2022 atau IDE favorit Anda  
> • Salinan berlisensi **Aspose.Words for .NET** (versi trial gratis cukup untuk pengujian)  

Jika Anda sudah menyiapkan semua itu, mari kita mulai.

---

## Simpan Dokumen Word dan Deteksi Font yang Hilang

Inti idenya sederhana: sebelum Anda memanggil `Document.Save`, tetapkan sebuah objek yang mengimplementasikan `IWarningCallback` ke `Document.WarningCallback`. Aspose.Words akan memanggil objek ini untuk setiap peringatan yang ditemukannya, termasuk peringatan **font substitution** yang muncul ketika dokumen sumber merujuk pada font yang tidak dapat ditemukan oleh sistem Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**What you’ll see:**  
Jika `input.docx` merujuk pada font yang tidak terpasang, konsol akan mencetak sesuatu seperti:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Baris itu memberi tahu Anda secara tepat font mana yang hilang dan apa yang digunakan Aspose.Words sebagai gantinya—sempurna untuk **capturing font errors** sebelum Anda mendistribusikan file.

---

## Lacak Font yang Hilang dengan Callback Peringatan (Langkah‑per‑Langkah)

### 1️⃣ Install Aspose.Words

Buka konsol NuGet proyek Anda dan jalankan:

```bash
dotnet add package Aspose.Words
```

Ini akan mengunduh versi stabil terbaru (saat ini 24.10). Menjaga pustaka tetap terbaru memastikan Anda mendapatkan kemampuan **detect missing fonts** terbaru serta perbaikan bug.

### 2️⃣ Definisikan Warning Handler

Mengapa kita memerlukan kelas terpisah? Mengimplementasikan `IWarningCallback` memungkinkan Anda memusatkan semua logika peringatan di satu tempat. Anda juga dapat mencatat ke file, mengirim telemetry, atau melempar pengecualian jika font yang hilang menjadi kesalahan fatal bagi alur kerja Anda.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** Jika Anda perlu **track missing fonts** di banyak dokumen, simpan pesan‑pesan tersebut dalam `List<string>` di dalam handler dan expose‑kan nanti untuk pelaporan.

### 3️⃣ Muat Dokumen Sumber Anda

Konstruktor `Document` dapat menerima jalur file, stream, atau bahkan byte mentah. Dalam kebanyakan kasus Anda akan menunjuk ke file `.docx` yang diterima dari pengguna atau sistem lain.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Jika file berukuran besar, pertimbangkan menggunakan `LoadOptions` untuk mengaktifkan lazy loading, yang mengurangi tekanan memori.

### 4️⃣ Sambungkan Callback

Tetapkan instance ke `doc.WarningCallback`. Mulai dari titik ini, setiap peringatan (termasuk substitusi font) akan melewati handler Anda.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Simpan Dokumen

Sekarang Anda dapat dengan aman memanggil `Save`. Handler peringatan berjalan **synchronously** selama operasi penyimpanan, sehingga Anda akan melihat outputnya segera.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Jika Anda lebih suka menyimpan ke format lain (PDF, HTML, dll.), mekanisme peringatan yang sama tetap berfungsi—Aspose.Words tetap akan melaporkan font yang hilang sebelum konversi.

---

## Tangkap Kesalahan Font – Kasus Edge Umum

Meskipun alur dasar mencakup sebagian besar skenario, proyek dunia nyata sering menemui beberapa kendala. Berikut beberapa variasi yang mungkin Anda temui dan cara menanganinya.

### Font Hilang di Header/Footer

Header dan footer adalah node terpisah, tetapi sistem peringatan memperlakukan mereka sama seperti teks utama. Tidak diperlukan kode tambahan; callback akan dipicu untuk font tersebut juga. Pastikan Anda memuat dokumen secara penuh (perilaku default melakukannya).

### Beberapa Substitusi dalam Satu Dokumen

Jika sebuah dokumen menggunakan beberapa font yang tidak dikenal, handler akan dipanggil sekali per substitusi. Untuk menghindari konsol yang terlalu penuh, Anda dapat menduplikasi pesan:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Mengubah Peringatan menjadi Pengecualian

Kadang-kadang font yang hilang menjadi hal yang tidak dapat diterima. Lemparkan pengecualian di dalam handler untuk menghentikan proses penyimpanan:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Ingat untuk membungkus `doc.Save` dalam blok `try/catch` agar pengecualian dapat ditangani dengan elegan.

---

## Verifikasi Hasil – Apa yang Diharapkan

Setelah penyimpanan selesai, buka `output.docx` di Microsoft Word (atau penampil kompatibel lainnya). Anda seharusnya melihat tata letak visual yang sama dengan aslinya, tetapi font yang disubstitusi akan muncul sebagai fallback yang Anda lihat di konsol. Untuk memeriksa kembali, Anda dapat:

1. Buka **File → Options → Advanced → Show document content → Use draft quality** – ini memaksa Word menampilkan semua substitusi font yang tersembunyi.  
2. Gunakan dialog **Replace Fonts** Word (`Ctrl+Shift+F`) untuk melihat font mana yang sebenarnya ter-embed.

Jika semuanya cocok, Anda telah berhasil **save word document** sambil **detecting missing fonts** dan **capturing font errors**. 🎉

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut seluruh program yang dapat Anda tempelkan ke proyek Console App baru. Cukup ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya di mesin Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Expected console output** (example):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Itulah seluruh cerita—tanpa langkah tersembunyi, tanpa dokumen eksternal yang harus Anda kejar.

---

## Conclusion

Kami baru saja menunjukkan cara **save word document** sambil secara aktif **detect missing fonts**, **track missing fonts**, dan **capture font errors** menggunakan callback peringatan Aspose.Words. Dengan menambahkan implementasi kecil `IWarningCallback`, Anda mendapatkan visibilitas penuh terhadap substitusi font pada saat penyimpanan, memberi Anda kesempatan untuk mencatat, mengganti, atau menghentikan proses sesuai kebutuhan.

Siap untuk tantangan berikutnya? Cobalah memperluas handler untuk menulis peringatan ke dalam log JSON terstruktur, atau gabungkan dengan Aspose.PDF untuk mengonversi dokumen yang sama sambil mempertahankan informasi font. Anda juga dapat mengeksplorasi penyematan font yang hilang langsung ke dalam file output—Aspose.Words mendukung penyematan font melalui `LoadOptions.FontSettings`.

Coba dulu, sesuaikan kode dengan alur kerja Anda, dan beri tahu kami bagaimana hasilnya. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}