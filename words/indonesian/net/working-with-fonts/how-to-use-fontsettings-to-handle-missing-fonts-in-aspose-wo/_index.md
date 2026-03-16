---
category: general
date: 2026-03-16
description: Pelajari cara menggunakan FontSettings di Aspose.Words untuk menangani
  font yang hilang dengan elegan—kode lengkap, penanganan acara, dan tips praktik
  terbaik.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: id
og_description: Cara menggunakan FontSettings di Aspose.Words untuk menangani font
  yang hilang—panduan langkah demi langkah dengan contoh lengkap C# dan tips praktis.
og_title: Cara Menggunakan FontSettings untuk Menangani Font yang Hilang di Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Cara Menggunakan FontSettings untuk Menangani Font yang Hilang di Aspose.Words
url: /id/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

"SubstitutionWarning", "LoadOptions", "Document", "C#", etc.

Also keep code block placeholders unchanged.

Now write final.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan FontSettings untuk Menangani Font yang Hilang di Aspose.Words

Pernah bertanya‑tanya **cara menggunakan FontSettings** ketika dokumen Word Anda merujuk pada font yang tidak terpasang di server? Anda tidak sendirian. Font yang hilang dapat menyebabkan fallback yang jelek atau bahkan melempar pengecualian, dan kebanyakan pengembang hanya mengabaikan masalah ini sampai muncul di produksi.  

Dalam tutorial ini kami akan menunjukkan secara tepat **cara menggunakan FontSettings** untuk **menangani font yang hilang** di Aspose.Words, menangkap peringatan detail, dan menjaga rendering dokumen tetap dapat diprediksi. Pada akhir tutorial Anda akan memiliki contoh C# yang siap dijalankan, memahami mengapa setiap baris penting, dan mengetahui cara menyesuaikan solusi untuk proyek yang lebih besar.

## Apa yang Dibahas dalam Panduan Ini

- Menyiapkan **FontSettings** dan berlangganan ke event `SubstitutionWarning`.  
- Menempelkan pengaturan ke `LoadOptions` sehingga dihormati saat memuat dokumen.  
- Menjalankan dokumen uji yang sengaja tidak memiliki font dan membaca output konsol.  
- Tips untuk logging, menonaktifkan substitusi otomatis, dan menangani kasus tepi seperti banyak font yang hilang.  

Tidak diperlukan dokumentasi eksternal—semua yang Anda butuhkan ada di sini.

## Prasyarat

- .NET 6+ (atau .NET Framework 4.6.2+).  
- Aspose.Words untuk .NET 23.9 atau yang lebih baru (API yang kami gunakan stabil di versi terbaru).  
- File `.docx` sederhana yang merujuk pada font yang Anda tahu tidak terpasang (misalnya *Comic Sans MS* pada kontainer Linux).  

Itu saja—tidak ada paket NuGet tambahan selain Aspose.Words.

## Mengapa Menangani Font yang Hilang Penting

Ketika sebuah dokumen merujuk pada font yang tidak dapat ditemukan oleh runtime, Aspose.Words secara otomatis menggantinya dengan yang paling mendekati. Substitusi tersebut sering kali dapat diterima, tetapi kadang Anda perlu **mencatat** font mana yang hilang (untuk kepatuhan) atau **mencegah** substitusi sama sekali (misalnya untuk PDF dengan merek khusus). Dengan memanfaatkan `FontSettings.SubstitutionWarning`, Anda mendapatkan visibilitas dan kontrol penuh.

## Langkah 1: Buat FontSettings dan Langganan ke Event Substitution‑Warning

Hal pertama yang Anda lakukan adalah menginstansiasi `FontSettings`. Objek ini menyimpan semua konfigurasi terkait font untuk perpustakaan. Bagian pentingnya adalah menghubungkan event `SubstitutionWarning`, yang dipicu **setiap kali** Aspose.Words tidak dapat menemukan font yang diminta.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Mengapa ini penting:**  
- **Visibilitas:** Anda langsung tahu font mana yang tidak ada.  
- **Auditabilitas:** Konsol (atau logger) dapat dialihkan ke file untuk laporan kepatuhan.  
- **Kontrol:** Nanti Anda dapat memutuskan untuk mengganti substitusi dengan font khusus milik Anda.

> **Pro tip:** Jika Anda lebih suka kerangka kerja logging (Serilog, NLog, dll.), ganti pemanggilan `Console.WriteLine` dengan `logger.Information(...)`.

## Langkah 2: Tempelkan FontSettings ke LoadOptions

`LoadOptions` adalah sarana yang memberi tahu Aspose.Words bagaimana memperlakukan file selama fase pemuatan. Dengan menetapkan objek `FontSettings`, Anda memastikan handler peringatan aktif *sebelum* konten apa pun diparsing.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Mengapa ini penting:**  
- Jika Anda memuat dokumen tanpa menyertakan `LoadOptions`, penanganan font default akan berjalan dan Anda akan kehilangan peringatan.  
- Pendekatan ini juga memungkinkan Anda menyesuaikan perilaku pemuatan lain (misalnya proteksi kata sandi) dalam objek yang sama.

## Langkah 3: Muat Dokumen dengan Opsi yang Dikonfigurasi

Sekarang kita akhirnya membaca file Word. Path dapat berupa absolut atau relatif; Aspose.Words akan menghormati `LoadOptions` yang baru saja kita siapkan.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Jika dokumen berisi font yang tidak terpasang, event `SubstitutionWarning` akan dipicu, dan Anda akan melihat output serupa dengan contoh di bawah.

### Output Konsol yang Diharapkan

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Substitusi yang tepat mungkin berbeda tergantung pada rantai fallback font sistem operasi, tetapi **nama font yang hilang** akan selalu dilaporkan.

## Langkah 4: Verifikasi Hasil (Rendering Opsional)

Seringkali Anda ingin memastikan dokumen tetap terlihat baik setelah substitusi. Cara cepatnya adalah menyimpannya sebagai PDF dan membuka hasilnya.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Jika Anda perlu **mencegah** substitusi sama sekali, setel `FontSettings.SubstitutionSettings.TableSubstitution = false` sebelum memuat. Maka Aspose.Words akan melempar pengecualian untuk font yang hilang, yang dapat Anda tangkap dan tangani.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Contoh Kerja Lengkap

Berikut adalah program lengkap yang siap dijalankan. Tempelkan ke aplikasi konsol, sesuaikan path file, dan tekan **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Apa yang Diharapkan

- Konsol mencetak setiap font yang hilang beserta substitusi yang dipilih.  
- PDF yang dihasilkan (jika Anda menyimpan secara opsional) menampilkan dokumen menggunakan font fallback, memastikan integritas tata letak.

## Pertanyaan Umum & Kasus Tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika beberapa font hilang?** | Event dipicu sekali per font yang hilang, sehingga Anda akan mendapatkan baris log terpisah untuk masing‑masing. |
| **Bisakah saya mengganti fallback dengan font khusus?** | Ya. Di dalam handler event Anda dapat memanggil `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Apakah peringatan muncul untuk font yang ter‑embed tetapi gagal dimuat?** | Tentu saja—baik font eksternal maupun yang ter‑embed, permukaan peringatannya sama. |
| **Apakah saya perlu membuang (dispose) `Document`?** | `Document` mengimplementasikan `IDisposable`. Bungkus penggunaannya dalam blok `using` jika Anda memuat banyak file dalam loop. |
| **Apakah ini bekerja di kontainer Linux?** | Selama Aspose.Words dapat menemukan font sistem (misalnya via `fontconfig`), mekanisme event yang sama berfungsi. |

## Praktik Terbaik & Pro Tips

- **Sentralisasi logging:** Buat metode bantu yang menulis ke konsol sekaligus ke file log persisten.  
- **Pemrosesan batch:** Saat mengonversi puluhan dokumen, gunakan satu instance `FontSettings` untuk menghindari berlangganan event berulang‑ulang.  
- **Kinerja:** Peringatan substitusi menambah overhead yang dapat diabaikan, tetapi jika Anda memproses ribuan file, pertimbangkan menonaktifkannya setelah Anda memverifikasi set font.  
- **Keamanan versi:** API `SubstitutionWarning` telah stabil sejak Aspose.Words 16.0, jadi Anda dapat mengandalkannya untuk upgrade di masa depan.

## Kesimpulan

Kami telah membahas **cara menggunakan FontSettings** di Aspose.Words untuk **menangani font yang hilang** secara elegan. Dengan membuat objek `FontSettings`, berlangganan ke `SubstitutionWarning`, dan memuat dokumen melalui `LoadOptions`, Anda memperoleh visibilitas penuh atas masalah font dan dapat memutuskan apakah akan mencatat, mengganti, atau menghentikan proses ketika font tidak tersedia.  

Dari output konsol sederhana hingga logika substitusi khusus, pola ini dapat diskalakan ke pipeline dokumen batch besar, memastikan output Anda tetap konsisten dan dapat diaudit.

**Langkah selanjutnya:**  

- Jelajahi **substitusi font khusus** dengan menetapkan `e.SubstitutedFont` di dalam event.  
- Gabungkan pendekatan ini dengan **rendering dokumen ke gambar** untuk pembuatan thumbnail.  
- Lihat **Aspose.PDF** jika Anda perlu menyematkan font yang telah disubstitusi langsung ke PDF akhir untuk portabilitas penuh.

Selamat coding, semoga dokumen Anda tidak lagi menderita font yang hilang!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}