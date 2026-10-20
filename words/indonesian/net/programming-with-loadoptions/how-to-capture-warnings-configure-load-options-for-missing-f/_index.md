---
category: general
date: 2026-03-30
description: cara menangkap peringatan saat memuat file DOCX – pelajari cara mendeteksi
  font yang hilang, mengonfigurasi pengaturan font, dan mengatur opsi pemuatan di
  C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: id
og_description: cara menangkap peringatan saat memuat file DOCX – panduan langkah
  demi langkah untuk mendeteksi font yang hilang dan mengatur pengaturan font di C#
og_title: cara menangkap peringatan – mengonfigurasi opsi muat untuk font yang hilang
tags:
- Aspose.Words
- C#
- Font management
title: cara menangkap peringatan – mengonfigurasi opsi pemuatan untuk font yang hilang
url: /id/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menangkap peringatan – mengonfigurasi opsi muat untuk font yang hilang

Pernah bertanya‑tanya **bagaimana cara menangkap peringatan** yang muncul ketika sebuah dokumen mencoba menggunakan font yang tidak terpasang di sistem Anda? Ini adalah situasi yang sering membuat bingung banyak pengembang yang bekerja dengan pustaka pengolah kata, terutama ketika Anda perlu **mendeteksi font yang hilang** sebelum mereka merusak alur ekspor PDF Anda.  

Dalam tutorial ini kami akan menunjukkan solusi praktis yang siap dijalankan, yang **mengonfigurasi pengaturan font**, **menetapkan opsi muat**, dan mencetak setiap peringatan substitusi ke konsol. Pada akhir tutorial Anda akan tahu persis **cara menangani font yang hilang** dengan cara yang membuat aplikasi Anda tetap kuat dan pengguna Anda puas.

## Apa yang Akan Anda Pelajari

- Cara **menetapkan opsi muat** sehingga pustaka melaporkan masalah font alih‑alih menggantinya secara diam‑diam.
- Langkah‑langkah tepat untuk **mengonfigurasi pengaturan font** demi menangkap peringatan.
- Cara **mendeteksi font yang hilang** secara programatik dan meresponsnya.
- Contoh lengkap C# yang dapat disalin‑tempel dan bekerja dengan Aspose.Words for .NET versi terbaru (v24.10 pada saat penulisan).
- Tips memperluas solusi untuk mencatat peringatan, menggunakan font khusus sebagai fallback, atau menghentikan proses ketika font kritis tidak ada.

> **Prasyarat:** Anda harus memasang paket NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`). Tidak ada ketergantungan eksternal lain yang diperlukan.

---

## Langkah 1: Impor Namespace dan Siapkan Proyek

Pertama, tambahkan arahan `using` yang penting. Ini bukan sekadar boilerplate; ia memberi tahu kompiler di mana `LoadOptions`, `FontSettings`, dan `Document` berada.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Tip pro:** Jika Anda menggunakan .NET 6+ Anda dapat mengaktifkan pernyataan *global using* untuk menghindari pengulangan baris‑baris ini di setiap file.

---

## Langkah 2: Tetapkan Opsi Muat dan Aktifkan Peringatan Substitusi Font

Inti dari **cara menangkap peringatan** terletak pada objek `LoadOptions`. Dengan membuat instance `FontSettings` baru dan melampirkan event handler ke `SubstitutionWarning`, Anda memberi tahu pustaka untuk memberi tahu setiap kali tidak dapat menemukan font yang diminta.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Mengapa ini penting:** Tanpa berlangganan event, Aspose.Words secara diam‑diam beralih ke font default, dan Anda tidak pernah tahu glyph mana yang diganti. Dengan mendengarkan `SubstitutionWarning`, Anda mendapatkan jejak audit lengkap—krusial untuk lingkungan yang menuntut kepatuhan.

---

## Langkah 3: Muat Dokumen Menggunakan Opsi yang Telah Dikonfigurasi

Setelah peringatan terpasang, muat DOCX Anda (atau format lain yang didukung) dengan `loadOptions` yang baru saja Anda siapkan. Konstruktor `Document` akan memicu logika pemeriksaan font secara langsung.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Jika file tersebut merujuk, misalnya, pada *“Comic Sans MS”* pada mesin yang hanya memiliki *“Arial”*, Anda akan melihat sesuatu seperti:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Baris itu dicetak langsung ke konsol karena handler yang kami lampirkan sebelumnya.

---

## Langkah 4: Verifikasi dan Tanggapi Peringatan yang Ditangkap

Menangkap peringatan hanyalah setengah dari perjuangan; Anda biasanya harus memutuskan apa yang harus dilakukan selanjutnya. Di bawah ini ada pola cepat yang menyimpan peringatan dalam sebuah list untuk analisis selanjutnya—sempurna jika Anda ingin mencatatnya ke file atau menghentikan impor ketika font kritis tidak ada.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Penanganan kasus tepi:**  
- **Beberapa font yang hilang:** List akan berisi satu entri per substitusi, sehingga Anda dapat mengiterasi dan membuat laporan terperinci.  
- **Font fallback khusus:** Jika Anda memiliki file font sendiri, tambahkan ke `FontSettings` sebelum memuat: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Peringatan kemudian akan menampilkan fallback khusus alih‑alih default sistem.  

---

## Langkah 5: Contoh Lengkap yang Siap Disalin‑Tempel

Menggabungkan semuanya, berikut adalah aplikasi konsol mandiri yang dapat Anda kompilasi dan jalankan sekarang.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Output konsol yang diharapkan** (ketika DOCX merujuk pada font yang hilang):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Jika font *kritis* seperti “Times New Roman” tidak ada, Anda akan melihat pesan abort sebagai gantinya.

---

## Pertanyaan Umum & Hal‑hal yang Perlu Diwaspadai

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya harus memanggil `SetFontsFolder` untuk menangkap peringatan?** | Tidak. Event peringatan berfungsi dengan font sistem default. Gunakan `SetFontsFolder` hanya bila Anda ingin menyediakan font fallback tambahan. |
| **Apakah ini akan bekerja di .NET Core / .NET 5+?** | Tentu saja. Aspose.Words 24.10 mendukung semua runtime .NET modern. Pastikan paket NuGet cocok dengan target framework Anda. |
| **Bagaimana jika saya ingin mencatat peringatan ke file alih‑alih konsol?** | Ganti `Console.WriteLine(msg);` dengan pemanggilan framework logging apa pun, misalnya `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Bisakah saya menekan peringatan untuk font tertentu?** | Ya. Di dalam event handler Anda dapat memfilter: `if (e.FontName == "SomeFont") return;`. Ini memberi kontrol yang sangat detail. |
| **Apakah ada cara menjadikan font yang hilang sebagai error?** | Lemparkan exception secara manual di dalam handler ketika kondisi terpenuhi, atau setel flag dan abort setelah konstruksi `Document` seperti yang ditunjukkan pada contoh. |

---

## Kesimpulan

Anda kini memiliki pola siap produksi untuk **cara menangkap peringatan** yang terjadi saat memuat dokumen dengan font yang hilang. Dengan **mendeteksi font yang hilang**, **mengonfigurasi pengaturan font**, dan **menetapkan opsi muat** secara tepat, Anda memperoleh visibilitas penuh atas peristiwa substitusi font dan dapat memutuskan apakah akan mencatat, menggunakan fallback, atau menghentikan proses.  

Langkah selanjutnya adalah mengintegrasikan logika ini ke dalam alur konversi PDF Anda, menambahkan font fallback khusus, atau mengirim daftar peringatan ke sistem pemantauan. Pendekatan ini dapat diskalakan dari utilitas kecil hingga layanan pemrosesan dokumen tingkat perusahaan.

---

### Bacaan Lanjutan & Langkah Berikutnya

- **Jelajahi lebih banyak fitur FontSettings** – menyematkan font khusus, mengontrol urutan fallback, dan pertimbangan lisensi.  
- **Kombinasikan dengan konversi PDF** – setelah menangkap peringatan, panggil `doc.Save("output.pdf");` dan pastikan PDF menggunakan font yang diharapkan.  
- **Otomatisasi pengujian** – tulis unit test yang memuat dokumen dengan font yang diketahui hilang dan pastikan daftar peringatan berisi pesan yang diharapkan.  

Jika Anda menemukan kendala atau memiliki ide untuk perbaikan, silakan tinggalkan komentar. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}