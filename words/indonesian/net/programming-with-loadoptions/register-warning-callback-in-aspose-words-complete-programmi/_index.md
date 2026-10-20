---
category: general
date: 2026-06-27
description: Daftarkan callback peringatan di Aspose.Words untuk menangkap substitusi
  font dan masalah pemuatan. Pelajari penggunaan LoadOptions langkah demi langkah
  dengan Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: id
og_description: Daftarkan callback peringatan di Aspose.Words untuk memantau substitusi
  font dan peringatan pemuatan lainnya. Ikuti tutorial lengkap ini untuk implementasi
  yang kuat.
og_title: Mendaftarkan Callback Peringatan di Aspose.Words – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Mendaftarkan Callback Peringatan di Aspose.Words – Panduan Pemrograman Lengkap
url: /id/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftarkan Callback Peringatan di Aspose.Words – Panduan Pemrograman Lengkap

Pernah bertanya-tanya bagaimana **mendaftarkan callback peringatan di Aspose.Words** sehingga Anda dapat melihat tepat font apa yang diganti saat dokumen dimuat? Anda tidak sendirian. Banyak pengembang mengalami kebuntuan ketika substitusi font yang diam mengacaukan tata letak PDF atau file Word yang dihasilkan.  

Dalam tutorial ini kami akan membimbing Anda melalui solusi praktis yang tidak hanya mendaftarkan callback peringatan di Aspose.Words tetapi juga menjelaskan *mengapa* Anda perlu melakukannya, bagaimana cara kerja callback di balik layar, dan kasus tepi apa yang mungkin Anda temui. Pada akhir tutorial Anda dapat mencatat setiap substitusi font, menangkap peringatan pemuatan lainnya, dan membuat alur pemrosesan dokumen Anda menjadi transparan.

## Apa yang Akan Anda Pelajari

- Menyiapkan **LoadOptions** untuk mengontrol perilaku pemuatan dokumen.  
- Mendaftarkan **callback peringatan** yang dipicu untuk substitusi font dan tipe peringatan lainnya.  
- Memuat DOCX dengan opsi yang telah dikonfigurasi dan menafsirkan output callback.  
- Jebakan umum (font yang hilang, folder font khusus, dan pertimbangan kinerja).  

**Prasyarat:** Visual Studio 2022 (atau IDE C# apa pun), runtime .NET 6+ , dan lisensi Aspose.Words yang aktif (versi percobaan gratis cukup untuk percobaan). Tidak diperlukan paket NuGet tambahan selain `Aspose.Words`.

---

![Diagram yang menggambarkan alur pendaftaran callback peringatan di Aspose.Words dan penanganan peringatan substitusi font](register-warning-callback-aspose-words.png "diagram pendaftaran callback peringatan aspose.words")

## Langkah 1: Buat LoadOptions – Titik Masuk untuk Penanganan Peringatan  

Sebelum callback dapat dipicu, Anda memerlukan instance **LoadOptions**. Anggaplah ini sebagai panel kontrol yang Anda serahkan ke Aspose.Words ketika Anda berkata “muat file ini, tetapi beri tahu saya jika ada yang tidak beres.”  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Mengapa ini penting:** `LoadOptions` memungkinkan Anda menyesuaikan segala hal mulai dari kata sandi enkripsi hingga direktori font. Dengan melampirkan callback peringatan ke objek ini, Anda mengubah proses yang diam menjadi proses yang dapat diamati.

## Langkah 2: Daftarkan Callback Peringatan – Tangkap Substitusi Font  

Sekarang hadir bintang utama: **callback peringatan**. Kami akan mendaftarkan metode anonim (lambda) yang dipanggil Aspose.Words untuk setiap peringatan pemuatan. Di dalam callback kami menyaring `WarningType.FontSubstitution` dan mencetak pesan yang ramah.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Tips pro:** Jika Anda juga ingin mencatat gambar yang hilang atau fitur yang tidak didukung, tambahkan cabang `if` tambahan yang memeriksa `args.WarningType`. Ini menjadikan implementasi **register warning callback in Aspose.Words** Anda sebuah pusat diagnostik pemuatan lengkap.

## Langkah 3: Muat Dokumen Menggunakan LoadOptions yang Dikonfigurasi  

Setelah callback terhubung, langkah selanjutnya cukup memuat dokumen. Berikan instance `loadOptions` ke konstruktor `Document`. Setiap kali Aspose.Words menemukan font yang tidak dapat ditemukan, callback Anda akan dipicu dan menulis ke konsol.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Jalankan program, dan Anda akan melihat output serupa dengan:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Itulah inti dari **register warning callback aspose.words**—pola tiga langkah yang dapat Anda gunakan kembali di proyek mana pun.

## Langkah 4: Memperluas Callback untuk Skenario Dunia Nyata  

### 4.1 Mencatat ke File Alih-alih Konsol  

Di produksi Anda jarang menginginkan spam konsol. Ganti `Console.WriteLine` dengan logger (misalnya, `Serilog`, `NLog`) atau tulis ke file teks:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Menyediakan Direktori Font Kustom  

Jika lingkungan Anda menggunakan font korporat, beri tahu Aspose.Words di mana mencarinya sebelum beralih ke substitusi:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Sekarang callback mungkin dipicu *lebih sedikit*, karena mesin menemukan font yang tepat.

### 4.3 Menangani Peringatan Non‑Font  

Anda dapat memperluas cakupan untuk menangkap semua peringatan pemuatan:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Langkah 5: Menguji Implementasi Anda – Apa yang Diharapkan  

### 5.1 Verifikasi dengan Dokumen yang Memiliki Font Hilang  

Buat DOCX kecil yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya “Comic Sans MS” pada server Linux). Jalankan loader; Anda harus melihat pesan substitusi.  

### 5.2 Ukur Overhead  

Callback menambahkan overhead yang dapat diabaikan—sekitar beberapa mikrodetik per peringatan. Jika Anda memuat ribuan dokumen, Anda dapat mengelompokkan entri log atau menonaktifkan callback untuk run yang tidak kritis.

### 5.3 Kasus Tepi  

- **Beberapa Substitusi untuk Font yang Sama:** Aspose.Words dapat memicu callback berkali‑kali jika font yang sama yang hilang muncul pada halaman yang berbeda. Lakukan deduplikasi di logger Anda bila diperlukan.  
- **Dokumen Enkripsi:** Jika DOCX diproteksi kata sandi, Anda juga harus mengatur `loadOptions.Password`. Callback tetap akan dipicu setelah dekripsi.  
- **Pemuat Asinkron:** API bersifat sinkron, tetapi Anda dapat membungkus panggilan load dalam `Task.Run` untuk pemrosesan latar belakang; callback tetap thread‑safe.

## Jebakan Umum & Cara Menghindarinya  

| Jebakan | Mengapa Terjadi | Solusi |
|---------|----------------|--------|
| **Tidak ada output sama sekali** | Callback tidak ditetapkan *atau* `WarningCallback` ditimpa kemudian. | Pastikan Anda menetapkan callback **sekali** sebelum memuat, dan jangan menetapkan ulang `loadOptions` setelah penetapan. |
| **Exception cast yang salah** | Mencoba meng-cast peringatan yang bukan `FontSubstitutionWarningInfo`. | Selalu periksa `args.WarningType` sebelum melakukan cast. |
| **Penurunan kinerja** | Mencatat secara sinkron ke target I/O yang lambat. | Gunakan kerangka kerja logging asinkron atau buffer penulisan. |
| **Font kustom tidak ditemukan** | Folder font tidak ditambahkan ke `FontSettings`. | Tambahkan `SetFontsFolder` seperti yang ditunjukkan pada Langkah 4.2. |

## Contoh Lengkap yang Siap Pakai – Salin‑dan‑Jalankan  

Berikut adalah program mandiri yang dapat Anda salin ke proyek Console App baru. Program ini menunjukkan alur lengkap dari awal hingga akhir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Output konsol yang diharapkan** (asumsi ada font yang hilang):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Jalankan program, dan Anda akan melihat tepat font apa yang diganti oleh Aspose.Words, memberi Anda visibilitas penuh ke proses pemuatan.

---

## Kesimpulan  

Kami baru saja membahas **cara mendaftarkan callback peringatan di Aspose.Words**, mengapa ini merupakan praktik terbaik untuk alur kerja pemrosesan dokumen apa pun, dan bagaimana memperluas pola ini untuk pencatatan, font kustom, serta penanganan peringatan yang lebih luas. Dengan hanya tiga baris kode, Anda mengubah operasi load yang kotak‑hitam menjadi langkah yang dapat diaudit dan debug—tidak ada lagi perubahan tata letak yang misterius.

Apa selanjutnya? Cobalah menggabungkan callback ini dengan **Aspose.Words SaveOptions** untuk mencatat peringatan selama proses *load* **dan** *save*, atau hubungkan callback ke API web yang memproses unggahan secara real‑time. Anda juga dapat menjelajahi kata kunci sekunder lain yang kami perkenalkan—seperti *loadoptions font substitution warning*—untuk menyempurnakan kinerja atau mengintegrasikan dengan dasbor pemantauan.

Punya pertanyaan atau skenario rumit? Tinggalkan komentar, dan mari kita selesaikan bersama. Selamat coding, semoga PDF Anda selalu menampilkan font yang tepat!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat dengan teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}