---
category: general
date: 2026-05-23
description: atur callback peringatan aspose untuk menangkap peringatan substitusi
  font di Aspose.Words. Pelajari LoadOptions, FontSettings, dan implementasi IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: id
og_description: Atur callback peringatan Aspose untuk memantau substitusi font di
  Aspose.Words. Tutorial ini menunjukkan penggunaan LoadOptions, FontSettings, dan
  implementasi handler peringatan.
og_title: Mengatur Callback Peringatan Aspose – Panduan Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Set Warning Callback Aspose – Panduan Lengkap Memuat Dokumen Word
url: /id/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Panduan Lengkap Memuat Dokumen Word

Pernah bertanya-tanya bagaimana cara **set warning callback aspose** sehingga Anda tidak pernah melewatkan peringatan substitusi font lagi? Anda tidak sendirian. Ketika sebuah DOCX merujuk ke font yang tidak terpasang, Aspose.Words secara diam-diam menggantinya, dan tanpa callback yang tepat Anda mungkin tidak pernah menyadari ada perubahan.

Dalam tutorial ini kami akan menelusuri contoh lengkap yang dapat dijalankan yang menunjukkan secara tepat cara menangkap peringatan tersebut. Pada akhir tutorial Anda akan memahami **Aspose.Words LoadOptions**, cara mengonfigurasi **FontSettings**, dan mengapa mengimplementasikan **IWarningCallback** adalah cara paling bersih untuk tetap terinformasi. Tanpa basa‑basi—hanya kode yang dapat Anda masukkan ke proyek .NET hari ini.

## Apa yang Akan Anda Pelajari

- Cara **set warning callback aspose** pada instance `LoadOptions`.  
- Peran **Aspose.Words LoadOptions** saat membuka dokumen.  
- Mengonfigurasi penanganan **Aspose fonts substitution** dengan `FontSettings`.  
- Menulis implementasi **IWarningCallback** kustom untuk mencatat masalah font.  
- Memuat dokumen secara aman dengan praktik terbaik **Aspose document loading**.

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja pada .NET Framework 4.5+).  
- Lisensi Aspose.Words untuk .NET yang valid atau kunci percobaan.  
- Visual Studio, Rider, atau editor C# apa pun yang Anda sukai.  
- Contoh DOCX (`fontTest.docx`) yang merujuk ke font yang hilang (opsional tetapi membantu).

> **Pro tip:** Jika Anda tidak memiliki DOCX dengan font yang hilang, cukup ubah nama font dalam gaya dokumen dan perhatikan peringatan muncul.

---

## Cara set warning callback aspose untuk memuat dokumen

Berikut adalah program lengkap yang berdiri sendiri. Simpan sebagai `Program.cs`, pulihkan paket NuGet, dan jalankan. Konsol akan mencetak setiap peringatan substitusi font yang dihasilkan Aspose.Words saat memuat file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Output konsol yang diharapkan

Jika `fontTest.docx` merujuk ke font yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Jika semua font tersedia, satu‑satunya baris yang dicetak adalah *Document loaded successfully*—tanpa peringatan, tanpa kebisingan.

![contoh set warning callback aspose](image.png "contoh set warning callback aspose")

---

## Memahami LoadOptions di Aspose.Words

`LoadOptions` adalah gerbang ke setiap penyesuaian yang dapat Anda lakukan **aspose document loading**. Ini memungkinkan Anda:

1. **Menentukan `FontSettings` kustom** – berguna ketika aplikasi Anda menyertakan font sendiri.  
2. **Menyematkan callback peringatan** – tepat seperti yang kami lakukan untuk menangkap substitusi font.  
3. Mengontrol deteksi format dokumen, penanganan kata sandi, dan lainnya.

Karena `LoadOptions` diteruskan ke konstruktor `Document`, pengaturan diterapkan **sekali**, tepat pada saat file diparsing. Itulah mengapa kami dapat menjamin handler peringatan kami akan melihat setiap substitusi sebelum dokumen dibangun di memori.

### Kapan menggunakan LoadOptions kustom

- **Pemrosesan batch** banyak file di mana Anda menginginkan strategi pencatatan yang seragam.  
- **Layanan cloud** yang perlu melaporkan font yang hilang kembali ke pemanggil.  
- **Pipeline pengujian** yang memverifikasi dokumen mematuhi kebijakan font perusahaan.

---

## Mengonfigurasi FontSettings untuk Aspose fonts substitution

Objek `FontSettings` mengontrol cara Aspose.Words menyelesaikan font. Secara default ia mencari di folder font sistem, kemudian beralih ke substitusi bawaan. Anda dapat menyesuaikan perilaku ini:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Baris‑baris ini opsional untuk skenario “set warning callback aspose” dasar, tetapi mereka menggambarkan bagaimana Anda dapat **mengurangi** jumlah peringatan substitusi dengan menyediakan font yang tepat sebelumnya.

---

## Mengimplementasikan IWarningCallback untuk peringatan substitusi font

Antarmuka `IWarningCallback` sangat kecil—hanya satu metode `Warning`. Namun ia memberi Anda **kendali penuh** atas cara peringatan ditangani:

- **Mencatat ke file** alih‑alih ke konsol.  
- **Mengumpulkan peringatan** dalam daftar untuk analisis selanjutnya.  
- **Melemparkan pengecualian** untuk peringatan kritis (misalnya, ketika font yang diperlukan hilang).

Berikut contoh singkat yang menyimpan peringatan dalam `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Anda kemudian dapat memeriksa `handler.Messages` setelah memuat dokumen untuk memutuskan apakah proses harus dihentikan.

---

## Memuat dokumen dengan penanganan peringatan kustom (alur lengkap)

Menggabungkan semuanya, pola akhir yang kemungkinan besar akan Anda gunakan terlihat seperti ini:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Potongan kode ini mendemonstrasikan alur **aspose document loading** yang akan Anda pakai di produksi: konfigurasi, muat, lalu reaksi. Pola ini skala dengan baik baik Anda memproses satu file maupun ribuan file secara berulang.

---

## Pertanyaan Umum & Kasus Edge

**Bagaimana jika dokumen dilindungi kata sandi?**  
Tambahkan `Password = "secret"` pada inisialisasi `LoadOptions`. Callback peringatan tetap berfungsi setelah file didekripsi.

**Apakah callback akan dipicu untuk tipe peringatan lain?**  
Ya—`WarningInfo.Type` dapat berupa `DocumentStructure`, `UnsupportedFileFormat`, dll. Pada contoh kami kami menyaring `FontSubstitution`, tetapi Anda dapat mencatat semuanya dengan menghapus pengecekan `if`.

**Apakah ini memengaruhi performa?**  
Sangat sedikit. Callback hanya dipanggil ketika peringatan terjadi, yang jauh lebih jarang dibandingkan langkah parsing normal.

**Bisakah saya menonaktifkan substitusi font sepenuhnya?**  
Anda dapat mengatur `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` tetapi Aspose.Words akan melempar pengecualian untuk font yang hilang alih‑alih menggantinya.

---

## Kesimpulan

Anda kini tahu persis cara **set warning callback aspose** untuk memantau peristiwa substitusi font selama pemrosesan **Aspose.Words LoadOptions**. Dengan mengonfigurasi `FontSettings`, mengimplementasikan `IWarningCallback` ringan, dan memuat dokumen dengan opsi tersebut, Anda mendapatkan visibilitas penuh atas setiap perubahan font yang dilakukan Aspose di balik layar.

Dari sini Anda dapat:

- Memperluas handler peringatan untuk menulis ke layanan pencatatan terpusat.  
- Menggabungkan callback dengan strategi fallback font kustom.  
- Menggunakan pola ini saat membangun API cloud yang memvalidasi dokumen yang diunggah klien.

Cobalah dengan file DOCX Anda sendiri, sesuaikan `FontSettings`, dan saksikan konsol memberi tahu Anda font apa saja yang diganti. Selamat coding, semoga dokumen Anda selalu tampil sesuai harapan!

## Tutorial Terkait

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}