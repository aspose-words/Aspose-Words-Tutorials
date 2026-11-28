---
category: general
date: 2026-04-04
description: Pulihkan file Word yang rusak menggunakan Aspose.Words di C#. Pelajari
  cara menampilkan mode pemulihan dan menangani kesalahan file secara efisien.
draft: false
keywords:
- recover corrupted word file
- display recovery mode
language: id
og_description: Pulihkan file Word yang rusak dan tampilkan mode pemulihan dengan
  Aspose.Words. Panduan lengkap langkah demi langkah untuk pengembang C#.
og_title: Pulihkan File Word yang Rusak – Tampilkan Mode Pemulihan di C#
tags:
- Aspose.Words
- C#
- Document Recovery
title: Pulihkan File Word yang Rusak dan Tampilkan Mode Pemulihan di C#
url: /id/net/programming-with-loadoptions/recover-corrupted-word-file-and-display-recovery-mode-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pulihkan File Word yang Rusak – Panduan Lengkap untuk Menampilkan Mode Pemulihan di C#

Pernahkah Anda mencoba membuka dokumen Word yang terlihat baik di Explorer tetapi menghasilkan error saat Anda memuatnya dalam kode? Itu adalah skenario klasik *recover corrupted word file*. Dalam tutorial ini kami akan menunjukkan cara tepat untuk memulihkan file Word yang rusak **dan** menampilkan mode pemulihan yang dipilih menggunakan Aspose.Words untuk .NET.

Kami akan membahas semua yang Anda butuhkan—menginstal pustaka, mengonfigurasi `LoadOptions`, menangani kasus tepi, dan mencetak mode pemulihan ke konsol. Pada akhir tutorial, Anda akan memiliki potongan kode yang solid dan siap produksi yang dapat langsung Anda masukkan ke dalam proyek Anda.

## Apa yang Akan Anda Pelajari

- Cara mengatur `LoadOptions` Aspose.Words untuk mengontrol penanganan kerusakan.  
- Mengapa `RecoveryMode.Strict` adalah default paling aman untuk kasus penggunaan *recover corrupted word file*.  
- Kode tepat yang diperlukan untuk **menampilkan mode pemulihan** setelah memuat.  
- Jebakan umum (mis., file tidak ada, kerusakan yang tidak didukung) dan cara menghindarinya.  

**Prasyarat:** .NET 6+ (atau .NET Framework 4.6+), salinan berlisensi atau evaluasi Aspose.Words, dan pemahaman dasar tentang C#. Tidak ada dependensi lain.

---

## Langkah 1: Instal Aspose.Words untuk .NET

Langkah pertama—dapatkan paket NuGet. Buka terminal di folder proyek Anda dan jalankan:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda berada di proyek lama yang masih menggunakan `packages.config`, jalankan `Install-Package Aspose.Words` di Package Manager Console sebagai gantinya.

Paket ini menyertakan semua yang Anda butuhkan: kelas `Document`, `LoadOptions`, dan enum `RecoveryMode`.

## Langkah 2: Konfigurasikan LoadOptions untuk Memulihkan File Word yang Rusak

Sekarang kami memberi tahu Aspose.Words seberapa agresif ia harus mencoba memperbaiki file yang rusak. Enum `RecoveryMode` memiliki tiga nilai:

| Value | Perilaku |
|-------|------------|
| **Strict** | Membatalkan pada korupsi parah. |
| **Relaxed** | Mencoba memperbaiki masalah kecil. |
| **NoRecovery** | Memuat tanpa upaya pemulihan apapun. |

Untuk sebagian besar skenario produksi, Anda akan menginginkan **Strict**—ini mencegah pemuatan diam-diam dokumen yang rusak yang dapat menyebabkan kesalahan di kemudian hari.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 2: Define recovery behaviour for a potentially damaged file.
var loadOptions = new LoadOptions
{
    // Abort loading if the corruption is severe (alternatives: Relaxed, NoRecovery).
    RecoveryMode = RecoveryMode.Strict
};
```

> **Mengapa ini penting:** Menggunakan `Strict` memastikan Anda *benar‑benar* mengetahui kapan sebuah file tidak dapat diselamatkan, alih‑alih menebak nanti ketika dokumen ditampilkan secara tidak benar.

## Langkah 3: Muat Dokumen dengan Opsi yang Dikonfigurasi

Dengan `loadOptions` siap, kita dapat mencoba membuka file. Jika file utuh, semuanya berjalan lancar; jika rusak, sebuah pengecualian akan dilempar (yang akan kami tangkap nanti).

```csharp
// Step 3: Load the document using the configured recovery options.
string filePath = @"C:\Docs\PotentiallyCorrupt.docx";
Document document = null;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"⚠️ Failed to load document: {ex.Message}");
    // You might log the error or attempt a fallback strategy here.
}
```

> **Kasus tepi:** Jika file tidak ada, `FileNotFoundException` akan muncul. Selalu validasi jalur sebelum memanggil `new Document`.

## Langkah 4: Verifikasi Keberhasilan Muat dan **Menampilkan Mode Pemulihan**

Dengan asumsi tidak ada pengecualian, objek dokumen siap. Mari pastikan muatan berhasil dan cetak mode pemulihan yang kami gunakan. Ini memenuhi persyaratan *display recovery mode*.

```csharp
// Step 4: Confirm that the document was loaded and show the recovery mode.
if (document != null)
{
    Console.WriteLine($"✅ Document loaded successfully.");
    Console.WriteLine($"RecoveryMode = {loadOptions.RecoveryMode}");
}
else
{
    Console.WriteLine("❌ Document could not be loaded.");
}
```

Output konsol tipikal terlihat seperti:

```
✅ Document loaded successfully.
RecoveryMode = Strict
```

Jika Anda mengubah `RecoveryMode` menjadi `Relaxed`, output akan mencerminkan perubahan tersebut—berguna untuk debugging atau strategi pemulihan yang lebih permisif.

## Langkah 5: Opsional – Menangani Skenario Kerusakan Spesifik

Terkadang Anda mungkin ingin **recover corrupted word file** bahkan ketika kerusakan hanya ringan, tanpa menghentikan seluruh operasi. Berikut penyesuaian cepat:

```csharp
// Switch to a more forgiving mode if you need to salvage partially damaged docs.
loadOptions.RecoveryMode = RecoveryMode.Relaxed;

try
{
    document = new Document(filePath, loadOptions);
    Console.WriteLine($"Loaded with Relaxed mode. RecoveryMode = {loadOptions.RecoveryMode}");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed even with Relaxed mode: {ex.Message}");
}
```

> **Kapan menggunakan Relaxed:** Jika Anda memproses unggahan massal dan dapat mentolerir gangguan format minor, `Relaxed` dapat menghemat waktu Anda. Hanya ingat untuk memvalidasi dokumen akhir sebelum dipublikasikan.

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut program siap salin‑tempel yang menunjukkan cara **recover corrupted word file** dan **menampilkan mode pemulihan**:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Define recovery behaviour.
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Strict // Change to Relaxed if needed.
        };

        // 2️⃣ Path to the possibly damaged document.
        string filePath = @"C:\Docs\PotentiallyCorrupt.docx";

        // 3️⃣ Attempt to load the document.
        Document document = null;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"⚠️ Error loading document: {ex.Message}");
            // Early exit if loading fails.
            return;
        }

        // 4️⃣ Verify and **display recovery mode**.
        if (document != null)
        {
            Console.WriteLine($"✅ Document loaded with RecoveryMode = {loadOptions.RecoveryMode}");
        }
        else
        {
            Console.WriteLine("❌ Document could not be loaded.");
        }

        // 5️⃣ (Optional) Do something with the document, e.g., save as PDF.
        // document.Save("Recovered.pdf");
    }
}
```

Jalankan program, dan Anda akan melihat apakah file berhasil melewati pemeriksaan ketat dan mode mana yang diterapkan.

---

## Pertanyaan Umum & Tips

- **Bagaimana jika file terenkripsi?**  
  Aspose.Words dapat membuka file yang dilindungi kata sandi, tetapi Anda harus menyediakan kata sandi melalui `LoadOptions.Password`. Mode pemulihan tetap berlaku setelah dekripsi.

- **Bisakah saya mencatat detail kerusakan yang tepat?**  
  Atur `loadOptions.LoadFormat = LoadFormat.Docx` dan aktifkan `Document.CompatibilityOptions` untuk mendapatkan diagnostik yang lebih terperinci.

- **Apakah `Strict` adalah default?**  
  Tidak—jika Anda tidak menyertakan `RecoveryMode`, Aspose.Words default ke `Relaxed`. Menetapkan `Strict` secara eksplisit adalah cara paling aman untuk *recover corrupted word file* hanya ketika Anda yakin file bersih.

- **Dampak kinerja?**  
  Proses pemulihan menambahkan overhead kecil (biasanya < 5 ms untuk DOCX 1 MB tipikal). Untuk pekerjaan batch besar, pertimbangkan memparalelkan muatan.

## Kesimpulan

Anda sekarang tahu cara **recover corrupted word file** dengan Aspose.Words, mengonfigurasi `RecoveryMode` yang tepat, dan **menampilkan mode pemulihan** untuk memverifikasi strategi Anda. Pendekatan ini memberi Anda kontrol penuh atas penanganan error, memastikan aplikasi Anda mendapatkan dokumen bersih atau gagal cepat dengan pesan yang jelas.

Langkah selanjutnya? Coba ganti `RecoveryMode.Strict` dengan `Relaxed` dan amati bagaimana perpustakaan mencoba memperbaiki masalah kecil. Anda juga dapat menjelajahi penyimpanan dokumen yang dipulihkan dalam format lain (PDF, HTML) untuk memastikan konten berhasil melewati proses pemulihan.

Selamat coding, dan ingat—ketika menangani file yang rusak, menjadi eksplisit tentang perilaku pemulihan menyelamatkan Anda dari banyak bug tersembunyi di kemudian hari. Jangan ragu meninggalkan komentar jika Anda mengalami kendala atau memiliki solusi cerdas untuk dibagikan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}