---
category: general
date: 2026-09-05
description: Pelajari cara menandatangani Word dengan sertifikat di C# menggunakan
  Aspose.Words. Panduan langkah demi langkah ini mencakup penandatanganan XAdES‑EPES
  dengan sertifikat PFX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word with certificate
- XAdES EPES signing
- Aspose.Words digital signature
- C# sign Word document
- digital signature with certificate
- XadesSignatureOptions
language: id
lastmod: 2026-09-05
og_description: Tandatangani Word dengan sertifikat menggunakan Aspose.Words di C#.
  Ikuti contoh lengkap ini untuk membuat tanda tangan XAdES‑EPES dengan file PFX Anda.
og_image_alt: Screenshot showing a Word document that has been signed with a certificate
og_title: Menandatangani Word dengan sertifikat di C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to sign Word with certificate in C# using Aspose.Words. This
    step‑by‑step guide covers XAdES‑EPES signing with a PFX certificate.
  headline: How to sign Word with certificate using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- digital signature
- XAdES
- certificate
title: Cara menandatangani Word dengan sertifikat menggunakan Aspose.Words di C#
url: /id/net/programming-with-digital-signatures/how-to-sign-word-with-certificate-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menandatangani Word dengan sertifikat menggunakan Aspose.Words di C#

Jika Anda perlu **menandatangani Word dengan sertifikat** dalam aplikasi .NET, panduan ini menunjukkan solusi lengkap yang siap dijalankan. Pada akhir tutorial Anda akan memiliki file .docx yang ditandatangani yang mematuhi standar XAdES‑EPES (Explicit Policy‑based Electronic Signature).

Menandatangani dokumen Word secara programatik menghilangkan langkah manual membuka file di Microsoft Word dan menerapkan tanda tangan. Anda akan belajar cara memuat dokumen yang belum ditandatangani, mengonfigurasi opsi XAdES‑EPES, menerapkan tanda tangan digital dengan sertifikat PFX, dan menyimpan hasil yang ditandatangani—semua dengan Aspose.Words untuk .NET.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Lisensi Aspose.Words untuk .NET (atau kunci evaluasi sementara)  
* File sertifikat PFX (`.pfx`) yang mencakup kunci pribadi dan kata sandi  
* Visual Studio 2022 atau IDE kompatibel C# apa pun  

Item-item ini adalah satu‑satunya dependensi eksternal; kode di bawah ini dapat langsung dijalankan begitu semuanya tersedia.

## Langkah 1: Muat dokumen Word yang belum ditandatangani

Operasi pertama adalah membaca file `.docx` sumber yang ingin Anda tandatangani. Memuat dokumen membuat representasi dalam memori yang dapat dimanipulasi oleh Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Signing;

// Replace with the actual path to your unsigned document
string sourcePath = @"C:\Docs\Unsigned.docx";

Document document = new Document(sourcePath);
```

*Mengapa langkah ini penting*: Kelas `Document` adalah titik masuk untuk semua fitur pengolahan Word di Aspose.Words. Tanpa memuat file, tidak ada yang dapat ditandatangani.

## Langkah 2: Konfigurasikan opsi tanda tangan XAdES‑EPES

XAdES‑EPES menambahkan referensi kebijakan eksplisit ke tanda tangan, yang diperlukan untuk banyak skenario kepatuhan (mis., EU eIDAS). Objek `XadesSignatureOptions` memungkinkan Anda menentukan pengidentifikasi kebijakan, hash-nya, dan algoritma hash.

```csharp
// Create XAdES‑EPES options
XadesSignatureOptions xadesOptions = new XadesSignatureOptions
{
    SignaturePolicyInfo = new XadesSignaturePolicyInfo
    {
        Identifier = "YourPolicyIdentifier",          // Unique policy ID
        Hash = "ABCD1234...",                         // Base‑64 encoded hash of the policy document
        HashAlgorithm = XadesHashAlgorithm.Sha256   // Strong hash algorithm
    },
    IsEpesEnabled = true // Turn on EPES support
};
```

*Mengapa langkah ini penting*: Menetapkan `IsEpesEnabled` ke `true` memberi tahu Aspose.Words untuk menyematkan referensi kebijakan, mengubah tanda tangan XAdES biasa menjadi yang mematuhi EPES. Ini memenuhi kebutuhan auditor yang mengharuskan kebijakan penandatanganan terdokumentasi.

## Langkah 3: Terapkan tanda tangan digital dengan sertifikat Anda

Sekarang Anda melampirkan sertifikat (`.pfx`) dan memanggil metode `DigitalSignature.Sign`. Kata sandi melindungi kunci pribadi di dalam file PFX.

```csharp
// Path to your certificate and its password
string certPath = @"C:\Certificates\mycert.pfx";
string certPassword = "yourPassword";

// Apply the signature
document.DigitalSignature.Sign(certPath, certPassword, xadesOptions);
```

*Mengapa langkah ini penting*: Metode `Sign` melakukan operasi kriptografi: ia menghitung hash dokumen, membuat struktur XML‑DSig, dan menyematkan bagian tanda tangan ke dalam file Word. Menggunakan sertifikat memastikan non‑repudiation dan verifikasi integritas oleh viewer yang kompatibel dengan Office.

### Tips Pro

Jika aplikasi Anda berjalan di server tanpa UI, simpan sertifikat di vault yang aman (Azure Key Vault, AWS Secrets Manager) dan muat ke dalam objek `X509Certificate2`, kemudian berikan objek sertifikat tersebut ke `Sign` alih-alih jalur file.

## Langkah 4: Simpan dokumen yang ditandatangani

Akhirnya, tulis dokumen yang ditandatangani ke disk. Anda dapat menimpa file asli atau membuat file baru; contoh di bawah membuat file baru untuk menjaga versi yang belum ditandatangani tetap utuh.

```csharp
// Destination path for the signed file
string signedPath = @"C:\Docs\SignedXadesEpes.docx";

document.Save(signedPath);
```

*Mengapa langkah ini penting*: Menyimpan mempertahankan XML tanda tangan di dalam paket Word. Membuka `SignedXadesEpes.docx` di Microsoft Word akan menampilkan badge “Signed”, dan detail tanda tangan dapat diperiksa melalui panel **File → Info → View Signatures**.

## Contoh lengkap yang berfungsi

Menggabungkan semua bagian, berikut adalah aplikasi konsol mandiri yang dapat Anda salin, tempel, dan jalankan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Signing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the unsigned document
        string sourcePath = @"C:\Docs\Unsigned.docx";
        Document doc = new Document(sourcePath);

        // 2️⃣ Set up XAdES‑EPES options
        XadesSignatureOptions xadesOptions = new XadesSignatureOptions
        {
            SignaturePolicyInfo = new XadesSignaturePolicyInfo
            {
                Identifier = "YourPolicyIdentifier",
                Hash = "ABCD1234...", // Replace with actual Base‑64 hash
                HashAlgorithm = XadesHashAlgorithm.Sha256
            },
            IsEpesEnabled = true
        };

        // 3️⃣ Apply the signature using a PFX certificate
        string certPath = @"C:\Certificates\mycert.pfx";
        string certPassword = "yourPassword";
        doc.DigitalSignature.Sign(certPath, certPassword, xadesOptions);

        // 4️⃣ Save the signed document
        string signedPath = @"C:\Docs\SignedXadesEpes.docx";
        doc.Save(signedPath);

        Console.WriteLine("Document signed successfully: " + signedPath);
    }
}
```

**Output yang diharapkan**: Konsol mencetak `Document signed successfully: C:\Docs\SignedXadesEpes.docx`. Membuka file yang disimpan di Word menampilkan tanda tangan digital yang valid dan mematuhi XAdES‑EPES.

## Pertanyaan umum & kasus tepi

| Question | Answer |
|----------|--------|
| *Apakah saya dapat menandatangani dokumen yang sudah berisi tanda tangan?* | Ya. Aspose.Words mendukung banyak tanda tangan. Panggil `Sign` lagi dengan instance `XadesSignatureOptions` baru. |
| *Bagaimana jika saya membutuhkan algoritma hash yang berbeda?* | Setel `HashAlgorithm` ke `XadesHashAlgorithm.Sha1`, `Sha384`, atau `Sha512` sesuai kebutuhan kebijakan Anda. |
| *Bagaimana cara memverifikasi tanda tangan secara programatik?* | Gunakan `DigitalSignatureUtil.Verify` atau API `SignatureCollection` untuk menelusuri dan memvalidasi tanda tangan. |
| *Apakah XAdES‑EPES didukung di .NET Core?* | Didukung sepenuhnya mulai Aspose.Words 22.9 ke atas pada .NET 5/6/7. |
| *Bagaimana jika sertifikat disimpan di Windows certificate store?* | Muat dengan `new X509Certificate2(StoreName.My, StoreLocation.CurrentUser, certThumbprint)` dan berikan objek `X509Certificate2` ke `Sign`. |

## Kesimpulan

Anda kini tahu cara **menandatangani Word dengan sertifikat** menggunakan Aspose.Words di C#. Tutorial ini mencakup memuat dokumen, mengonfigurasi opsi XAdES‑EPES, menerapkan tanda tangan digital dengan sertifikat PFX, dan menyimpan file yang ditandatangani. Contoh end‑to‑end ini memenuhi persyaratan kepatuhan dan dapat diintegrasikan ke dalam pipeline pembuatan dokumen otomatis apa pun.

### Langkah selanjutnya

* Jelajahi lebih lanjut **penandatanganan XAdES EPES** dengan menambahkan server timestamp (`XadesTimestampOptions`).  
* Gabungkan pendekatan ini dengan **Aspose.PDF** untuk mengonversi file Word yang ditandatangani menjadi PDF yang ditandatangani.  
* Pelajari cara **memvalidasi digital**

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Memuat Dokumen Word Menggunakan Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Menambahkan Watermark Teks pada Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-watermark/add-text-watermark/)
- [mengonversi word ke pdf di C# menggunakan Aspose.Words – Panduan](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}