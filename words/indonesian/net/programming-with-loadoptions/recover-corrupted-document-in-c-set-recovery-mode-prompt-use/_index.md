---
category: general
date: 2026-01-11
description: Pulihkan dokumen yang rusak di C# menggunakan Aspose.Words. Pelajari
  cara mengatur mode pemulihan, memuat docx dengan pemulihan, dan memberi peringatan
  kepada pengguna saat terjadi kesalahan dalam beberapa langkah sederhana.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: id
og_description: Pulihkan dokumen yang rusak di C# dengan mengatur mode pemulihan,
  memuat DOCX dengan pemulihan, dan memberi prompt kepada pengguna saat terjadi kesalahan.
  Tutorial lengkap langkah demi langkah.
og_title: Pulihkan Dokumen Rusak di C# – Panduan Cepat
tags:
- Aspose.Words
- C#
- Document Recovery
title: Pulihkan Dokumen Rusak di C# – Atur Mode Pemulihan & Minta Input Pengguna
url: /id/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Memulihkan Dokumen Rusak di C# – Panduan Lengkap

Pernah mencoba membuka file DOCX yang tampak baik di Word tetapi melemparkan pengecualian di kode Anda? Kemungkinan Anda sedang menghadapi skenario **recover corrupted document**. Kabar baiknya, Aspose.Words memberi Anda kontrol detail tentang cara menangani file‑file nakal tersebut—apakah Anda ingin memperbaikinya secara diam‑diam, melemparkan pengecualian, atau menanyakan kepada pengguna apa yang harus dilakukan.

Dalam tutorial ini kami akan membahas semua yang Anda perlukan untuk **recover corrupted document** file, mulai dari menginstal pustaka hingga memilih opsi **set recovery mode** yang tepat, **load docx with recovery**, dan akhirnya **prompt user on error** ketika sesuatu tidak berjalan lancar. Tanpa basa‑basi, hanya contoh lengkap yang dapat dijalankan dan Anda dapat menaruhnya ke proyek .NET mana pun.

> **Pratinjau cepat:** Pada akhir tutorial Anda akan memiliki aplikasi konsol yang memuat `corrupt.docx` yang mungkin rusak, mencatat semua peringatan, dan menanyakan kepada pengguna apakah ingin melanjutkan ketika pemulihan gagal.

---

## Apa yang Anda Butuhkan

- **.NET 6.0** atau yang lebih baru (kode ini juga berfungsi pada .NET Framework 4.6+).  
- **Aspose.Words for .NET** – instal melalui NuGet (`Install-Package Aspose.Words`).  
- Sebuah file **corrupt DOCX** untuk pengujian (Anda dapat sengaja merusak file dengan membukanya di editor heksadesimal atau mengubah ekstensi).  
- IDE pilihan Anda—Visual Studio, Rider, atau bahkan VS Code sudah cukup.

> *Tips pro:* Simpan salinan cadangan file asli. Pemulihan dapat menimpa bagian‑bagian dokumen, dan Anda tidak ingin kehilangan bagian yang masih baik.

---

## Langkah 1 – Instal Aspose.Words dan Tambahkan Namespace

Langkah pertama. Dapatkan pustaka dari NuGet dan masukkan namespace yang diperlukan.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Itu saja yang Anda perlukan untuk sisa panduan. Namespace `Aspose.Words.Loading` berisi kelas `LoadOptions`, yang merupakan kunci untuk **set recovery mode**.

---

## Langkah 2 – Pilih Mode Pemulihan (Primary H2 with Keyword)

### Recover Corrupted Document – Menetapkan Mode Pemulihan yang Tepat

Aspose.Words menawarkan tiga perilaku pemulihan:

| Mode | Apa yang Terjadi | Kapan Digunakan |
|------|------------------|-----------------|
| **PromptUser** | Menampilkan dialog (atau Anda dapat mengimplementasikan prompt sendiri) dan mencoba memperbaiki file. | Ideal untuk alat interaktif di mana pengguna dapat memutuskan. |
| **Silent** | Mencoba memperbaiki secara otomatis, tanpa UI. | Cocok untuk pekerjaan batch atau layanan. |
| **ThrowException** | Menghentikan proses dan melemparkan pengecualian. | Digunakan ketika Anda menginginkan validasi ketat. |

Berikut cara **set recovery mode** ke `PromptUser`. Jika Anda lebih suka penanganan diam, cukup ganti nilai enum.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Mengapa ini penting:** Dengan secara eksplisit **set recovery mode**, Anda memberi tahu Aspose.Words seberapa agresif ia harus bekerja. Defaultnya adalah `PromptUser`, tetapi menjadi eksplisit membuat niat Anda jelas—baik bagi pemelihara di masa depan maupun bagi mesin pencari yang mengindeks kode.

---

## Langkah 3 – Muat DOCX dengan Pemulihan

Sekarang kita akan **load docx with recovery** menggunakan `LoadOptions` yang baru saja dikonfigurasi. Jika file rusak, Aspose.Words akan memperbaikinya atau mengeluarkan peringatan, tergantung pada mode yang dipilih.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Konstruktor `Document` melakukan pekerjaan berat. Pada mode **PromptUser**, Anda akan melihat prompt konsol (atau UI khusus jika Anda menghubungkan ke event `LoadOptions`) yang menanyakan apakah akan melanjutkan. Pada mode **Silent**, metode hanya berusaha sebaik mungkin dan melanjutkan.

---

## Langkah 4 – Periksa Peringatan dan Tanyakan kepada Pengguna

Aspose.Words mencatat semua masalah yang ditemukannya dalam koleksi `Warnings`. Mari iterasi koleksi tersebut dan beri pengguna kesempatan untuk memutuskan langkah selanjutnya.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Potongan kode di atas **prompt user on error** dengan cara yang ramah konsol. Jika Anda membuat aplikasi Windows Forms atau WPF, ganti `Console.ReadLine` dengan `MessageBox` atau dialog khusus.

---

## Langkah 5 – Bekerja dengan Dokumen yang Telah Dipulihkan

Pada titik ini dokumen berada di memori, telah diperbaiki semaksimal mungkin oleh Aspose.Words. Anda kini dapat membaca isinya, menyimpan salinan bersih, atau melakukan manipulasi apa pun yang diperlukan.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Menjalankan program lengkap terhadap file yang rusak akan menghasilkan output konsol serupa dengan ini:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Jika file ternyata baik-baik saja, Anda akan melihat “Document loaded without any warnings.” dan salinan bersih akan identik dengan sumbernya.

---

## Contoh Kerja Lengkap

Berikut seluruh program dalam satu tempat. Salin‑tempel ke proyek konsol baru dan tekan **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Jalankan, rusak sebuah file uji, dan saksikan pemulihan beraksi. 🎉

---

## Kasus Khusus & Variasi

| Skenario | Apa yang Diubah | Mengapa |
|----------|-----------------|---------|
| **Pemrosesan batch** (tanpa interaksi pengguna) | Set `RecoveryMode = RecoveryMode.Silent` dan hapus prompt konsol. | Menjaga alur pipeline tetap otomatis. |
| **Validasi ketat** (gagal cepat) | Gunakan `RecoveryMode.ThrowException`. Bungkus pemanggilan load dalam try/catch dan catat pengecualian. | Menjamin Anda tidak pernah bekerja dengan file yang hanya sebagian diperbaiki. |
| **UI khusus** (WinForms/WPF) | Langganan ke `LoadOptions.LoadingProgress` atau gunakan event `Document.LoadOptions` untuk menampilkan dialog. | Menyediakan pengalaman yang lebih kaya dibandingkan konsol. |
| **Dokumen besar** (kendala memori) | Muat dengan `LoadOptions.LoadFormat = LoadFormat.Docx` dan pertimbangkan `Document.SaveOptions` untuk streaming output. | Mencegah pengecualian OutOfMemory. |

---

## Tips Praktis (Sinyal E‑E‑A‑T)

- **Selalu simpan cadangan** sebelum mencoba pemulihan; proses dapat menimpa bagian file.  
- **Catat peringatan** ke file log untuk analisis nanti; biasanya mereka memberi petunjuk penyebab utama (misalnya bagian yang hilang, XML yang rusak).  
- **Uji dengan berbagai jenis kerusakan** – potong file, rusak tag XML, atau ubah struktur zip untuk melihat perilaku tiap mode.  
- **Perbarui Aspose.Words secara berkala**; versi terbaru meningkatkan algoritma pemulihan dan menambah tipe peringatan baru.  
- **Kombinasikan dengan validasi** – setelah pemulihan, jalankan `document.UpdateFields()` dan `document.Save()` untuk memastikan dokumen berfungsi sepenuhnya.

---

## Kesimpulan

Anda kini tahu cara **recover corrupted document** di C# dengan **set recovery mode**, **load docx with recovery**, dan **prompt user on error** ketika terjadi masalah. Contoh lengkap menunjukkan alur bersih end‑to‑end yang bekerja di aplikasi konsol, layanan, atau proyek UI.

Langkah selanjutnya? Coba ganti prompt konsol dengan dialog modal di aplikasi WinForms, eksperimen dengan mode **Silent** untuk pekerjaan latar belakang, atau integrasikan logika pemulihan ke endpoint upload file ASP.NET sehingga pengguna dapat mengunggah DOCX yang rusak dan menerima versi yang telah diperbaiki secara instan.

Selamat coding, semoga dokumen Anda tetap utuh!  

---

![Contoh pemulihan dokumen rusak](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}