---
category: general
date: 2026-02-26
description: Tangani font yang hilang dalam C# menggunakan Aspose.Words. Pelajari
  cara menangkap peringatan substitusi font, mengimplementasikan IWarningCallback,
  dan menjaga tampilan dokumen Anda tetap tepat.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: id
og_description: Tangani font yang hilang di C# dengan cepat. Panduan ini menunjukkan
  cara menangkap peringatan substitusi font dengan Aspose.Words, mengimplementasikan
  IWarningCallback, dan memverifikasi hasil.
og_title: Menangani Font yang Hilang di C# – Tutorial Aspose.Words Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Document Processing
title: Menangani Font yang Hilang di C# dengan Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangani Font yang Hilang di C# dengan Aspose.Words – Panduan Lengkap

Pernah perlu **menangani font yang hilang** saat memuat dokumen Word di C# dan bertanya-tanya mengapa hasilnya terlihat aneh? Anda tidak sendirian. Ketika file sumber merujuk ke font yang tidak terpasang di mesin, Aspose.Words secara diam-diam menggantinya dengan yang lain, yang dapat merusak tata letak atau merek Anda.  

Berita baik? Dengan menyiapkan **warning callback**, Anda dapat menangkap setiap peristiwa substitusi font, mencatatnya, dan memutuskan apakah akan menyediakan pengganti. Dalam tutorial ini kami akan membimbing Anda melalui seluruh proses—dari menyiapkan proyek hingga memverifikasi output konsol—sehingga Anda tidak akan lagi terkejut oleh font yang tidak terlihat.

> **Apa yang akan Anda dapatkan**: A ready‑to‑run C# console app that reports each missing font, explains why the warning occurs, and shows you how to extend the handler for custom logic.

---

## Prasyarat

- .NET 6.0 atau yang lebih baru (kode ini bekerja pada .NET Core dan .NET Framework)
- Visual Studio 2022 (atau IDE C# apa pun yang Anda sukai)
- Sebuah **lisensi** untuk Aspose.Words for .NET (versi percobaan gratis dapat digunakan untuk pengujian)
- Dokumen Word yang merujuk ke font yang tidak terpasang di sistem Anda (misalnya *Comic Sans MS* pada mesin Linux)

Jika Anda sudah memiliki semua itu, mari kita mulai.

---

## Langkah 1: Buat Proyek Konsol Baru dan Tambahkan Aspose.Words

Untuk menjaga semuanya tetap rapi, mulailah dengan proyek konsol baru.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Tips pro**: Gunakan flag `--framework net6.0` jika Anda ingin menargetkan runtime tertentu.

Ini akan mengunduh paket NuGet Aspose.Words terbaru, yang berisi tipe `LoadOptions` dan `IWarningCallback` yang kami perlukan.

---

## Langkah 2: Implementasikan Warning Handler (IWarningCallback)

Aspose.Words menghasilkan objek `WarningInfo` untuk setiap masalah non‑kritikal yang ditemuinya saat memuat dokumen. Dengan mengimplementasikan `IWarningCallback`, Anda memutuskan apa yang harus dilakukan dengan peringatan tersebut.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Mengapa ini penting**: Tanpa handler, peringatan substitusi font diabaikan secara diam-diam. Dengan mencetaknya, Anda langsung melihat font mana yang hilang dan apa yang digunakan Aspose.Words sebagai gantinya.

---

## Langkah 3: Konfigurasikan LoadOptions dengan Warning Callback

Sekarang kita menghubungkan handler ke proses pemuatan dokumen. `LoadOptions` memungkinkan Anda menyisipkan callback sebelum file diparsing.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Catatan**: Ganti `YOUR_DIRECTORY` dengan folder sebenarnya yang berisi file `.docx` percobaan Anda. Instance `LoadOptions` harus diberikan ke konstruktor `Document`; jika tidak, perilaku default yang diam akan berlaku.

---

## Langkah 4: Jalankan Aplikasi dan Verifikasi Output

Compile and run:

```bash
dotnet run
```

Jika dokumen merujuk ke font yang tidak ada di mesin Anda (misalnya, *Papyrus*), Anda akan melihat sesuatu seperti:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Baris tunggal itu memberi tahu Anda secara tepat font mana yang hilang dan fallback mana yang dipilih Aspose.Words. Anda sekarang dapat memutuskan untuk menyematkan font yang hilang, mengubah dokumen sumber, atau menerima substitusi tersebut.

---

## Langkah 5: Lanjutan – Kumpulkan Peringatan untuk Penggunaan Selanjutnya

Kadang-kadang Anda ingin menyimpan peringatan alih-alih mencetaknya langsung. Di bawah ini ada penyesuaian cepat pada handler yang mengumpulkan pesan dalam sebuah daftar.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

And update `Main` accordingly:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Sekarang Anda memiliki daftar yang dapat digunakan kembali yang dapat Anda tulis ke file log, kirim ke layanan pemantauan, atau tampilkan di UI.

---

## Langkah 6: Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Tidak ada peringatan muncul** | Callback tidak terpasang, atau dokumen dimuat tanpa `LoadOptions`. | Pastikan `LoadOptions.WarningCallback` diatur **sebelum** memanggil konstruktor `Document`. |
| **Nama font salah dalam pesan** | Beberapa font disematkan dalam dokumen; Aspose.Words melaporkan nama *asli*, bukan yang disematkan. | Verifikasi referensi font pada file sumber; menyematkan font menghilangkan peringatan sepenuhnya. |
| **Dampak kinerja** | Mengumpulkan peringatan untuk ribuan dokumen dapat menambah beban. | Gunakan `Console.WriteLine` sederhana untuk debugging cepat; beralih ke pengumpul hanya ketika Anda membutuhkan data tersebut. |

---

## Ringkasan Visual

![Ilustrasi menangani font yang hilang menunjukkan alur warning callback](/images/handle-missing-fonts.png "Diagram penanganan font yang hilang dengan Aspose.Words")

*Diagram (teks alt mencakup kata kunci utama) memvisualisasikan bagaimana warning callback menyela peristiwa substitusi font selama pemuatan dokumen.*

---

## Kesimpulan

Anda kini tahu **cara menangani font yang hilang** di C# menggunakan Aspose.Words. Dengan menyiapkan `IWarningCallback` ke dalam `LoadOptions`, Anda mendapatkan visibilitas penuh pada setiap peristiwa substitusi font, dapat mencatat atau menindaklanjutinya, dan pada akhirnya memastikan dokumen yang dihasilkan mempertahankan tampilan dan nuansa yang diinginkan.

> **Ringkasan cepat**:  
> 1. Tambahkan Aspose.Words ke aplikasi konsol.  
> 2. Implementasikan `FontWarningHandler` (atau pengumpul).  
> 3. Berikan melalui `LoadOptions` saat memuat dokumen.  
> 4. Verifikasi output konsol atau peringatan yang disimpan.  

Dari sini Anda dapat mengeksplorasi **menyematkan font yang hilang** (`FontSettings.SubstitutionSettings`) atau **mengunduhnya secara otomatis dari server font perusahaan**—kedua-duanya merupakan ekstensi alami dari pola yang baru saja kami bangun.

Ada pertanyaan lebih lanjut tentang **peringatan font Aspose.Words**, **C# LoadOptions**, atau **pemuat dokumen dengan font yang hilang**? Tinggalkan komentar, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}