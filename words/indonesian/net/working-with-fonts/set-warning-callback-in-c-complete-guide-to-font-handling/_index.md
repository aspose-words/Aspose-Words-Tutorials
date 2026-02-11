---
category: general
date: 2026-02-10
description: Atur callback peringatan untuk memantau perubahan font saat Anda mengonfigurasi
  font default dan mengatur font impor default di Aspose.Words. Pelajari solusi langkah
  demi langkah secara lengkap.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: id
og_description: Setel callback peringatan untuk memantau perubahan font saat mengonfigurasi
  font default dan mengatur font impor default. Ikuti tutorial lengkap untuk Aspose.Words.
og_title: Mengatur callback peringatan di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Import
title: Atur callback peringatan di C# – Panduan Lengkap Penanganan Font
url: /id/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set warning callback in C# – Panduan Lengkap Penanganan Font

Pernahkah Anda perlu **set warning callback** saat memuat dokumen Word dan bertanya‑tanya bagaimana cara *configure default font* pada saat yang sama? Anda tidak sendirian. Dalam banyak proyek dunia nyata—seperti generator laporan otomatis atau pipeline konversi dokumen—font yang hilang dapat secara diam‑diam merusak tata letak, dan satu‑satunya cara untuk menangkap masalah tersebut adalah dengan **monitor font changes** melalui sebuah warning callback.

Dalam tutorial ini kita akan berjalan melalui contoh praktis yang menunjukkan cara **set warning callback**, **configure default font**, dan bahkan **set default import font** menggunakan Aspose.Words untuk .NET. Pada akhir tutorial Anda akan memiliki cuplikan kode yang siap dijalankan, memahami mengapa setiap bagian penting, dan tahu cara menyesuaikannya untuk kasus khusus seperti folder font khusus atau substitusi diam‑diam.

---

## Prerequisites

- .NET 6.0 atau lebih baru (kode ini juga bekerja pada .NET Framework 4.6+)  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)  
- Sebuah folder yang berisi fallback font yang ingin Anda gunakan (misalnya, `fonts/Arial.ttf`)  
- Familiaritas dasar dengan aplikasi konsol C#  

Tidak ada pustaka tambahan yang diperlukan.

---

## Step 1: Create LoadOptions and **configure default font**

Hal pertama yang Anda lakukan ketika ingin mengontrol penanganan font adalah membuat instance `LoadOptions`. Objek ini memberi tahu Aspose.Words bagaimana memperlakukan font yang hilang selama proses impor.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Why this matters:**  
Jika dokumen sumber merujuk pada font yang tidak terpasang di server, Aspose.Words akan melihat ke folder yang Anda berikan. Inilah inti dari **set default import font**—Anda secara eksplisit memberi tahu pustaka di mana menemukan pengganti sebelum peringatan apa pun muncul.

---

## Step 2: **Set warning callback** to **monitor font changes**

Aspose.Words menghasilkan `WarningInfoCollection` setiap kali harus mengganti font, di antara hal‑hal lainnya. Dengan melampirkan handler, Anda dapat mencatat atau merespons setiap substitusi.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Why this matters:**  
Hanya **configure default font** tidak cukup jika Anda perlu mengaudit font mana yang sebenarnya diganti. Callback memberikan log waktu nyata, memenuhi kebutuhan **monitor font changes** dan membantu Anda menangkap fallback yang tidak terduga lebih awal dalam pipeline CI.

---

## Step 3: Load the document with the prepared options

Setelah opsi pemuatan selesai disiapkan, Anda dapat dengan aman memuat file `.docx` apa pun. Callback akan otomatis dipicu jika terjadi substitusi.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**What you’ll see:**  
Jika sumber menggunakan font yang tidak ada, konsol akan mencetak sesuatu seperti:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Output tersebut mengonfirmasi bahwa Anda telah berhasil **set warning callback** dan bahwa **default import font** telah diterapkan.

---

## Step 4: (Optional) Fine‑tune font substitution behavior

Kadang‑kadang Anda mungkin ingin mengganti *semua* font yang hilang dengan satu keluarga font saja, terlepas dari permintaan asli. Aspose.Words memungkinkan Anda mengatur *fallback font* secara global.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**When to use this:**  
Jika Anda menghasilkan PDF untuk merek yang hanya mengizinkan sekumpulan font terbatas, ini memastikan konsistensi di setiap dokumen, bahkan jika sumber mencoba menggunakan font yang eksotis.

---

## Step 5: Save or further process the document

Setelah memuat, Anda dapat melanjutkan dengan proses apa pun yang diperlukan—mengedit, mengonversi ke PDF, mengekstrak teks, dll. Berikut contoh singkat menyimpan dokumen sebagai PDF sambil mempertahankan font yang telah diganti.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

PDF yang dihasilkan akan menampilkan fallback font di setiap tempat terjadi substitusi, memberi Anda konfirmasi visual bahwa **set warning callback** berfungsi sebagaimana mestinya.

---

## Common Pitfalls & Pro Tips

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback never fires** | `LoadOptions.WarningCallback` tidak ditetapkan *sebelum* memuat dokumen. | Selalu lampirkan callback **sebelum** memanggil `new Document(...)`. |
| **Wrong font folder** | Kesalahan penulisan path atau izin baca yang hilang. | Pastikan folder ada dan aplikasi memiliki akses `Read`. Gunakan path absolut untuk keandalan. |
| **Multiple substitutions, noisy output** | Dokumen besar dengan banyak font yang hilang. | Filter peringatan dengan `WarningType.FontSubstitution` (seperti yang ditunjukkan) atau tulis ke file log alih‑alih konsol. |
| **Fallback font not applied** | Fallback font tidak terpasang di mesin. | Letakkan file `.ttf`/`.otf` di folder yang Anda berikan ke `SetFontsFolder`. Aspose.Words memuatnya langsung, tanpa instalasi OS. |

**Pro tip:** Saat menjalankan ini di pipeline CI/CD, arahkan output konsol ke artefak build. Dengan begitu Anda memiliki jejak audit setiap substitusi font yang terjadi selama proses build.

---

## Full Working Example (Copy‑Paste Ready)

Berikut adalah program lengkap yang dapat Anda tempel ke proyek Console App baru. Ia mencakup semua langkah, pernyataan `using`, dan komentar yang Anda perlukan.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Expected console output** (asumsi `Times New Roman` tidak ada):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Jalankan program, buka `output.pdf`, dan Anda akan melihat dokumen ditampilkan dengan fallback font di mana pun diperlukan.

---

## Conclusion

Anda kini memiliki pola produksi yang solid untuk **set warning callback** di C#, **configure default font**, **monitor font changes**, dan **set default import font** saat bekerja dengan Aspose.Words. Dengan menempelkan pengumpul peringatan sebelum pemuatan, mengarahkan `FontSettings` ke folder font yang dapat diandalkan, dan secara opsional memaksa fallback global, Anda memperoleh visibilitas dan kontrol penuh atas substitusi font—tepat apa yang dibutuhkan setiap pipeline pemrosesan dokumen yang handal.

Siap ke level berikutnya? Coba gabungkan pendekatan ini dengan:

- **Dynamic font loading** dari basis data (gunakan `FontSettings.SetFontsFolder` pada waktu runtime).  
- **Custom warning handlers** yang menulis ke log terstruktur (JSON atau CSV) untuk analitik.  
- **Parallel document processing** dimana setiap thread memiliki `LoadOptions`‑nya sendiri untuk menghindari konflik.

Silakan bereksperimen, sesuaikan kode dengan arsitektur Anda, dan bagikan temuan di kolom komentar. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}