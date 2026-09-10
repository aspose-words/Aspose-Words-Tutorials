---
category: general
date: 2026-01-10
description: Pelajari cara menggunakan LoadOptions untuk menangani font yang hilang
  di Aspose.Words. Kode langkah demi langkah, tips, dan praktik terbaik untuk memuat
  dokumen secara andal.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: id
og_description: Cara menggunakan LoadOptions untuk menangani font yang hilang di Aspose.Words.
  Dapatkan contoh lengkap yang dapat dijalankan dengan penjelasan dan tips praktis.
og_title: Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- .NET
title: Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap
url: /id/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya **how to use LoadOptions** saat memuat dokumen Word yang mungkin kehilangan beberapa font? Anda bukan satu‑satunya yang menggaruk kepala tentang hal ini. Dalam banyak proyek dunia nyata, dokumen berpindah antar mesin, dan sistem target sering kali tidak memiliki tipe huruf persis yang digunakan penulis. Hasilnya? Substitusi font yang tak terduga yang dapat merusak tata letak, menyembunyikan karakter penting, atau sekadar tampak tidak sesuai merek.  

Untungnya, Aspose.Words memberi kita cara bersih untuk *handle missing fonts* dengan mengekspos objek `LoadOptions` yang memiliki callback peringatan. Dalam tutorial ini Anda akan belajar **how to use LoadOptions** secara tepat untuk menangkap peringatan substitusi font, mencatatnya, dan menjaga pipeline pemrosesan Anda tetap kuat.

Kami akan membahas:

* Menyiapkan kelas callback peringatan  
* Mengonfigurasi `LoadOptions` dengan callback tersebut  
* Memuat dokumen sambil melacak font yang hilang  
* Tips untuk pemecahan masalah dan memperluas solusi  

Tidak perlu dokumentasi eksternal—semua yang Anda butuhkan ada di sini.

---

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki:

* **Aspose.Words for .NET** (versi terbaru per 2026) terpasang via NuGet  
* Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code)  
* Contoh file DOCX yang merujuk pada font yang tidak Anda miliki (kami sebut `input.docx`)  

Itu saja—tidak ada pustaka tambahan yang diperlukan.

---

## Langkah 1 – Definisikan Warning Callback untuk Menangkap Substitusi Font

Potongan pertama dari teka‑teki adalah kelas yang mengimplementasikan `IWarningCallback`. Aspose.Words akan memanggil metode `Warning`‑nya setiap kali menemukan sesuatu yang patut dicatat—seperti font yang hilang.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Mengapa ini penting:**  
Dengan memfilter pada `WarningType.FontSubstitution` kita menghindari kekacauan dari peringatan yang tidak relevan (misalnya fitur yang sudah usang). Callback memberi Anda kontrol penuh—Anda bisa mencatat ke file, melempar pengecualian, atau bahkan mencoba menyematkan font fallback secara programatis.

---

## Langkah 2 – Konfigurasikan LoadOptions dengan Callback

Setelah kita memiliki handler, kita perlu memberi tahu Aspose.Words untuk menggunakannya. Di sinilah **how to use LoadOptions** diterapkan secara praktis.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Tip:** `LoadOptions` menawarkan banyak saklar lain (misalnya `Password`, `LoadFormat`, `Encoding`). Anda dapat menggabungkannya, tetapi untuk menangani font yang hilang, `WarningCallback` adalah bintang utama.

---

## Langkah 3 – Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Dengan `LoadOptions` yang siap, memuat dokumen menjadi sangat mudah. Aspose.Words secara otomatis akan memanggil callback untuk setiap font yang tidak dapat ditemukan.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Output yang diharapkan:**  

Jika `input.docx` menggunakan font bernama *“GothicBold”* yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Baris peringatan muncul **tepat ketika font yang hilang terdeteksi**, memberi Anda umpan balik langsung.

---

## Langkah 4 – (Opsional) Lanjutkan Memproses Dokumen

Biasanya Anda ingin melakukan lebih dari sekadar memuat file. Berikut beberapa tindakan pasca‑muat yang umum dan bekerja mulus dengan pengaturan peringatan kami.

### 4.1 Simpan Dokumen sebagai PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Ganti Font yang Hilang dengan Fallback yang Dikenal

Jika Anda menginginkan fallback tertentu (misalnya *“Calibri”*), Anda dapat menyesuaikan `FontSettings` sebelum menyimpan:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Catat Semua Peringatan ke File

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Potongan kode ini menggambarkan **how to use LoadOptions** di luar kasus dasar, memberi Anda fleksibilitas untuk solusi produksi.

---

## Kesalahan Umum & Cara **Menangani Font yang Hilang** dengan Elegan

| Pitfall | Why it Happens | How to Fix / Mitigate |
|---------|----------------|-----------------------|
| **No callback attached** | Anda lupa mengatur `WarningCallback`. | Selalu buat instance `LoadOptions` dan tetapkan handler Anda sebelum memuat. |
| **Callback only prints, never stores** | Pada layanan web, output console menghilang. | Ganti `Console.WriteLine` dengan logger (Serilog, NLog) atau tulis ke penyimpanan persisten. |
| **Multiple missing fonts, only first reported** | Callback Anda melempar pengecualian pada peringatan pertama. | Buat callback ringan; hindari melempar kecuali memang ingin menghentikan proses. |
| **Substituted font looks wrong** | Substitusi default mungkin memilih font yang secara visual sangat berbeda. | Gunakan `FontSettings.SubstitutionSettings.FontSubstitutionRules` untuk memprioritaskan fallback pilihan Anda. |
| **Performance hit on huge documents** | Callback peringatan dipanggil ribuan kali. | Kumpulkan peringatan dalam daftar dan proses setelah pemuatan, atau filter hanya nama font unik. |

Menyadari skenario‑skenario ini membantu Anda **handle missing fonts** tanpa kejutan.

---

## Contoh Lengkap – Semua Bagian Bersatu

Berikut program lengkap yang siap dijalankan. Salin‑tempel ke proyek konsol, tambahkan paket NuGet Aspose.Words, dan program akan berfungsi langsung.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Menjalankan program ini** akan:

1. Mencetak semua peringatan substitusi font ke console.  
2. Menyimpan tata letak asli sebagai `output.pdf`.  
3. Menyimpan PDF kedua (`output-with-fallback.pdf`) yang memaksa fallback ke *Calibri* atau *Arial*.

---

## Pertanyaan yang Sering Diajukan (FAQs)

**T: Apakah ini bekerja untuk file DOC, RTF, atau HTML?**  
J: Ya. `LoadOptions` bersifat format‑agnostik; selama Anda memberikan jalur file yang benar, callback peringatan akan dipicu untuk font yang hilang pada semua format yang didukung.

**T: Bisakah saya menonaktifkan peringatan sama sekali?**  
J: Anda dapat menetapkan callback kosong (`new IWarningCallback { Warning = _ => {} }`) atau mengatur `LoadOptions.WarningCallback = null`. Namun, kehilangan visibilitas berarti Anda mungkin melewatkan masalah font yang kritis.

**T: Bagaimana jika saya perlu mengganti font yang hilang dengan font yang disematkan?**  
J: Gunakan `FontSettings` untuk menyematkan file font pengganti (`AddFontSource`). Gabungkan dengan aturan substitusi untuk pengalaman yang mulus.

**T: Apakah callback thread‑safe?**  
J: Callback dapat dipanggil dari beberapa thread saat memuat dokumen besar secara paralel. Pastikan sumber daya bersama (misalnya file log) disinkronkan.

---

## Kesimpulan

Kami telah menelusuri **how to use LoadOptions** di Aspose.Words untuk **handle missing fonts** secara elegan. Dengan mendefinisikan `IWarningCallback` khusus, menautkannya ke instance `LoadOptions`, dan memuat dokumen dengan konfigurasi tersebut, Anda memperoleh wawasan waktu nyata tentang setiap peristiwa substitusi font. Dari situ, Anda dapat mencatat, mengganti, atau menyematkan font fallback agar output tetap sesuai harapan.

Ingat, langkah‑langkah kuncinya:

1. Implementasikan warning callback yang fokus pada `WarningType.FontSubstitution`.  
2. Sambungkan callback ke objek `LoadOptions`.  
3. Muat dokumen Anda dengan opsi tersebut.  
4. (Opsional) Terapkan aturan substitusi font tambahan atau pencatatan sesuai kebutuhan.

Silakan bereksperimen—ganti logger console dengan logger terstruktur, tambahkan notifikasi email untuk font yang hilang secara kritis, atau integrasikan pola ini ke dalam pipeline pemrosesan dokumen yang lebih besar. Pendekatan ini skalabel baik untuk satu file maupun ribuan file dalam batch job.

Selamat coding, semoga dokumen Anda selalu tampil dengan tipe huruf yang tepat!  

---

![contoh cara menggunakan loadoptions]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}