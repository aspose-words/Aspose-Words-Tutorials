---
category: general
date: 2026-04-24
description: Cara mendeteksi substitusi font yang hilang di Aspose.Words menggunakan
  C#. Panduan ini menunjukkan cara menangani font yang hilang secara andal dengan
  peringatan FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: id
og_description: Cara mendeteksi substitusi font yang hilang di Aspose.Words dengan
  C#. Pelajari cara menangani font yang hilang menggunakan peringatan FontSettings.
og_title: Cara Mendeteksi Substitusi di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Cara Mendeteksi Substitusi di Aspose.Words – Menangani Font yang Hilang
url: /id/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Substitusi di Aspose.Words – Menangani Font yang Hilang

Pernah bertanya-tanya **bagaimana cara mendeteksi substitusi** ketika sebuah dokumen mencoba menggunakan font yang tidak terpasang di server Anda? Ini adalah masalah umum, terutama saat Anda menghasilkan PDF atau file Word dalam pipeline otomatis. Kabar baiknya, Aspose.Words menyediakan hook bawaan untuk mendeteksi situasi tersebut, dan Anda juga dapat **menangani font yang hilang** dengan elegan.

Dalam tutorial ini kami akan membahas contoh dunia nyata yang menunjukkan **bagaimana cara mendeteksi substitusi** melalui event `FontSettings.Warning`, dan kami akan menjelaskan cara **menangani font yang hilang** tanpa mengganggu alur pemrosesan Anda. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan, pemahaman yang jelas mengapa setiap baris penting, serta beberapa tips untuk menghindari jebakan umum.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi di .NET Framework)
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`) – versi 23.11 atau lebih baru
- Dokumen contoh yang merujuk ke font yang tidak terpasang di sistem Anda (misalnya, `MissingFont.docx`)
- Visual Studio, VS Code, atau IDE C# apa pun yang Anda sukai  

Tidak ada konfigurasi tambahan yang diperlukan selain menambahkan paket NuGet.

---

## Cara Mendeteksi Substitusi dengan FontSettings

Inti dari **bagaimana cara mendeteksi substitusi** terletak pada event `FontSettings.Warning`. Ketika Aspose.Words tidak dapat menemukan font yang diminta, ia memunculkan peringatan `WarningType.FontSubstitution`. Dengan berlangganan ke event ini Anda akan menerima notifikasi waktu nyata, lengkap dengan nama font asli dan font yang digunakan sebagai cadangan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Mengapa ini berhasil:**  
- `LoadOptions.FontSettings` memberi tahu Aspose.Words untuk menggunakan objek `FontSettings` yang baru saja Anda buat.  
- Berlangganan ke `Warning` memberi Anda satu tempat untuk memantau *semua* masalah terkait font, bukan hanya font yang hilang.  
- Filter `WarningType.FontSubstitution` memastikan Anda hanya bereaksi pada skenario tepat yang Anda minati – esensi dari **bagaimana cara mendeteksi substitusi**.

### Output yang Diharapkan

Menjalankan kode di atas dengan dokumen yang merujuk ke font yang tidak ada akan mencetak sesuatu seperti:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Jika dokumen hanya menggunakan font yang terpasang, konsol tetap diam – sinyal jelas bahwa **bagaimana cara mendeteksi substitusi** berhasil tanpa alarm palsu.

---

## Menangani Font yang Hilang dengan Elegan

Mendeteksi substitusi hanyalah setengah dari perjuangan; Anda juga memerlukan strategi untuk **menangani font yang hilang** agar output akhir terlihat sesuai harapan. Berikut tiga pendekatan praktis yang dapat Anda gabungkan.

### 1. Sediakan Folder Font Cadangan

Aspose.Words dapat mencari font di direktori tambahan. Dengan mengarahkan ke folder yang berisi font paling umum yang Anda harapkan, Anda mengurangi kemungkinan terjadinya substitusi secara keseluruhan.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Mengapa:** Ketika font asli tidak ada, Aspose.Words kini memiliki serangkaian alternatif yang diketahui, yang sering menghasilkan hasil visual yang lebih dapat diprediksi.

### 2. Ganti Font yang Hilang Secara Programatik

Jika Anda menginginkan kontrol penuh, Anda dapat mengganti font yang hilang dengan font tertentu setelah deteksi.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Mengapa:** Ini memberi tahu engine font mana yang harus dicoba, memungkinkan Anda menegakkan standar merek perusahaan atau aksesibilitas.

### 3. Log dan Abort (Ketika Substitusi Tidak Dapat Diterima)

Kadang-kadang font yang hilang berarti dokumen tidak valid untuk kasus penggunaan Anda (misalnya, formulir hukum). Dalam skenario tersebut Anda dapat melemparkan pengecualian segera setelah substitusi terjadi.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Mengapa:** Kegagalan segera mencegah kesalahan di tahap selanjutnya, seperti tabel yang tidak rata atau tanda tangan yang rusak.

---

## Contoh Lengkap yang Berfungsi – Semua Langkah Digabungkan

Berikut adalah program tunggal yang siap disalin‑tempel yang menunjukkan **bagaimana cara mendeteksi substitusi** *dan* beberapa cara untuk **menangani font yang hilang**. Silakan komentar bagian yang tidak Anda perlukan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Apa yang diharapkan:**  
- Jika `MissingFont.docx` merujuk ke font yang tidak ada di mesin, konsol mencetak peringatan substitusi.  
- `Processed.docx` yang disimpan menggunakan font cadangan yang Anda konfigurasikan (atau default perpustakaan).  
- Tidak ada pengecualian yang tidak ditangani muncul kecuali Anda secara sengaja abort pada substitusi.

---

## Pertanyaan Umum & Kasus Tepi

| Pertanyaan | Jawaban |
|----------|--------|
| *Bagaimana jika dokumen berisi banyak font yang hilang?* | Event peringatan akan dipicu untuk **setiap** substitusi, sehingga Anda akan melihat beberapa baris. Anda dapat menggabungkannya ke dalam daftar untuk laporan ringkasan. |
| *Apakah ini bekerja dengan konversi PDF?* | Tentu saja. `FontSettings` yang sama dihormati ketika Anda memanggil `doc.Save("out.pdf")`. Peringatan substitusi tetap dipicu, memungkinkan Anda memverifikasi kesetiaan visual PDF. |
| *Bisakah saya mendeteksi substitusi setelah dokumen sudah dimuat?* | Tidak secara langsung. Peringatan muncul **selama** proses memuat atau menyimpan. Jika Anda memerlukan analisis setelah pemuatan, tangkap peringatan ke dalam koleksi selama fase pemuatan. |
| *Bagaimana dengan font khusus yang tersemat dalam DOCX?* | Font yang tersemat dianggap ada, sehingga tidak ada substitusi. Jika font tersemat rusak, Aspose.Words tetap memunculkan peringatan, yang dapat Anda tangkap dengan cara yang sama. |
| *Apakah ada dampak pada performa?* | Minimal. Pemeriksaan peringatan ringan; biaya utama adalah memuat dokumen itu sendiri. Menambahkan folder font dapat meningkatkan waktu pencarian sedikit, tetapi hanya pada pemuatan pertama. |

---

## Tips Pro & Jebakan yang Harus Dihindari

- **Tip pro:** Selalu setel `recursive: true` saat mengarahkan ke folder dengan banyak font; jika tidak, sub‑folder akan diabaikan.  
- **Waspada:** Sensitivitas huruf pada Linux. Nama font tidak sensitif huruf pada Windows tetapi sensitif pada Linux, jadi gunakan nama yang tepat atau tambahkan kedua varian.  
- **Ingat:** Jika Anda menjalankan di lingkungan terkontainer, pastikan folder font menjadi bagian dari image atau dipasang pada runtime.  
- **Tip:** Simpan peringatan dalam `List<string>` jika Anda perlu menyajikan ringkasan kepada pengguna akhir atau mencatatnya ke sistem pemantauan.  

---

## Kesimpulan

Kami telah membahas **bagaimana cara mendeteksi substitusi** font yang hilang di Aspose.Words, menunjukkan beberapa cara untuk **menangani font yang hilang**, dan menyediakan contoh lengkap yang dapat dijalankan yang dapat Anda masukkan ke proyek .NET mana pun. Dengan memanfaatkan event `FontSettings.Warning` Anda memperoleh visibilitas waktu nyata terhadap masalah font, dan dengan folder cadangan atau aturan substitusi eksplisit Anda menjaga output tetap terlihat persis seperti yang diharapkan.

Siap untuk langkah selanjutnya? Cobalah memperluas solusi untuk secara otomatis menyematkan font cadangan ke PDF yang dihasilkan, atau hubungkan handler peringatan ke layanan logging terpusat untuk pipeline dokumen berskala besar. Pola yang kami bahas hari ini—deteksi berbasis event, fallback yang elegan, dan penanganan error eksplisit—berlaku pada banyak API Aspose lainnya, sehingga Anda kini siap menghadapi tantangan terkait font di seluruh bidang.

Ada pertanyaan lebih lanjut tentang penanganan font, konversi PDF, atau trik Aspose.Words? Tinggalkan komentar di bawah, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}