---
category: general
date: 2026-01-03
description: Cara mendeteksi font di Aspose.Words dan menangani peringatan menggunakan
  pengaturan font Aspose – panduan langkah demi langkah untuk pengembang.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: id
og_description: Cara mendeteksi font di Aspose.Words dan mengonfigurasi peringatan
  dengan pengaturan font Aspose. Pelajari alur kerja lengkap dalam hitungan menit.
og_title: Cara Mendeteksi Font di Aspose.Words – Menangani Peringatan
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Mendeteksi Font di Aspose.Words – Menangani Peringatan & Pengaturan
url: /id/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font di Aspose.Words – Menangani Peringatan & Pengaturan

Pernah bertanya‑tanya **bagaimana cara mendeteksi font** dalam dokumen Word sebelum masuk produksi? Anda tidak sendirian. Font yang hilang dapat menyebabkan kekacauan tata letak, dan tanpa peringatan yang tepat Anda mungkin mengirim PDF atau DOCX yang rusak tanpa menyadarinya.  

Dalam tutorial ini kami akan menunjukkan **cara mendeteksi font** menggunakan Aspose.Words, memperlihatkan **cara menangani peringatan**, dan menyesuaikan **pengaturan font Aspose** sehingga Anda dapat **mengonfigurasi peringatan** persis seperti yang Anda butuhkan. Pada akhir tutorial Anda akan memiliki potongan kode yang siap dijalankan yang mencetak setiap substitusi yang dilakukan Aspose, dan Anda akan tahu cara menyesuaikannya untuk proyek Anda sendiri.

## Prasyarat

- .NET 6+ (atau .NET Framework 4.6+).  
- Aspose.Words untuk .NET terpasang via NuGet (`Install-Package Aspose.Words`).  
- Sebuah file Word yang sengaja merujuk ke font yang tidak ada (misalnya *DocumentWithMissingFonts.docx*).  

Jika Anda sudah memiliki semua itu, bagus—mari kita mulai.

![tangkapan layar cara mendeteksi font](https://example.com/detect-fonts.png "contoh output cara mendeteksi font")

## Cara Mendeteksi Font dengan Aspose.Words

Langkah pertama adalah memberi tahu Aspose.Words bahwa Anda peduli dengan peristiwa substitusi font. Hal ini dilakukan dengan menyediakan callback peringatan khusus melalui **pengaturan font Aspose**. Callback menerima objek `WarningInfo` untuk setiap substitusi, memungkinkan Anda **mendeteksi font** pada waktu berjalan.

### Langkah 1: Buat Kelas Callback Peringatan

Implementasikan antarmuka `IWarningCallback`. Di dalam metode `Warning`, saring untuk `WarningType.FontSubstitution` dan catat detailnya.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Tips pro:** String `info.Description` berisi nama font yang hilang serta font pengganti yang dipilih Aspose. Anda dapat mem‑parsenya jika memerlukan laporan terstruktur.

### Langkah 2: Konfigurasikan LoadOptions dengan Pengaturan Font Aspose

Buat instance `LoadOptions`, lampirkan objek `FontSettings` baru, dan arahkan `WarningCallback` ke handler yang baru saja Anda buat. Ini memberi tahu Aspose **bagaimana mengonfigurasi peringatan**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Jika Anda memiliki folder font pribadi, Anda dapat menambahkannya seperti:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Baris itu menunjukkan sudut lain dari **pengaturan font Aspose**—Anda mengontrol tepat di mana Aspose mencari font sebelum memutuskan untuk melakukan substitusi.

### Langkah 3: Muat Dokumen dan Aktifkan Callback

Sekarang muat dokumen target dengan `loadOptions`. Saat Aspose mem‑parsing file, setiap font yang hilang akan memicu handler peringatan, secara efektif **mendeteksi font** secara langsung.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Saat Anda menjalankan program, output yang muncul akan mirip dengan:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Langkah 4: (Opsional) Kumpulkan Peringatan untuk Penggunaan Selanjutnya

Jika Anda perlu menyimpan data substitusi untuk laporan, ubah handler agar mengakumulasi pesan dalam sebuah list.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Nanti Anda dapat menulis `handler.Substitutions` ke file JSON, mengirimnya ke layanan logging, atau menampilkannya di UI.

### Langkah 5: Verifikasi Hasil Secara Programatis

Kadang‑kadang Anda ingin memastikan bahwa *tidak ada* substitusi yang terjadi (misalnya dalam build CI). Berikut pemeriksaan singkatnya:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Potongan kode itu memperlihatkan **cara menangani peringatan** secara deterministik, memberi Anda kontrol penuh atas pipeline build.

## Pertanyaan yang Sering Diajukan (dan Kasus Edge)

**Bagaimana jika saya perlu mengabaikan substitusi tertentu?**  
Anda dapat menambahkan logika kondisional di dalam `Warning` dan cukup mengembalikan tanpa mencatat untuk font yang Anda anggap dapat diterima.

**Bisakah saya menonaktifkan semua peringatan dan hanya mendapatkan hasil boolean?**  
Ya—setel `loadOptions.WarningCallback = null` lalu periksa `doc.FontInfo` setelah pemuatan (meskipun Anda akan kehilangan log detail).

**Apakah ini bekerja dengan konversi PDF?**  
Tentu saja. Mekanisme peringatan yang sama dipicu ketika Anda memanggil `doc.Save("out.pdf")`. Callback akan menangkap setiap pertukaran font yang dilakukan selama langkah konversi.

**Apakah ada dampak performa?**  
Overheadnya minimal—hanya beberapa pemanggilan metode tambahan per font yang hilang. Untuk batch besar, Anda mungkin ingin menyimpan hasilnya dalam cache.

## Ringkasan: Apa yang Telah Kita Bahas

- **Cara mendeteksi font** dengan mengimplementasikan `IWarningCallback` khusus.  
- **Cara menangani peringatan** melalui `LoadOptions.WarningCallback`.  
- Menyesuaikan **pengaturan font Aspose** (menambahkan folder font khusus, mengaktifkan/menonaktifkan peringatan).  
- **Cara mengonfigurasi peringatan** untuk output konsol langsung maupun analisis selanjutnya.  

Dengan semua komponen ini, Anda dapat memproses dokumen Word dengan percaya diri, memastikan bahwa font yang hilang terdeteksi, dan menjaga konsistensi output di semua lingkungan.

## Langkah Selanjutnya

- Jelajahi `FontSettings.SubstitutionSettings` untuk kontrol yang lebih granular (misalnya memetakan font yang hilang ke substitusi tertentu).  
- Gabungkan pendekatan ini dengan Aspose.PDF untuk menghasilkan PDF yang mempertahankan tipografi tepat.  
- Otomatiskan pemeriksaan peringatan dalam pipeline CI/CD untuk memblokir rilis yang mengandung masalah font—sangat cocok bagi tim yang **menangani peringatan** sebagai bagian dari quality gate.

Ada pertanyaan lebih lanjut tentang **pengaturan font Aspose** atau butuh bantuan mengintegrasikan ini ke layanan yang lebih besar? Tinggalkan komentar di bawah, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}