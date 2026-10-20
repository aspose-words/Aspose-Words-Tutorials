---
category: general
date: 2026-08-20
description: Pelajari cara menandatangani dokumen Word dengan tanda tangan digital
  untuk file kontrak. Panduan ini mencakup memuat sertifikat x509 dari PFX dan membuat
  tanda tangan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: id
lastmod: 2026-08-20
og_description: Tandatangani dokumen Word dengan tanda tangan digital untuk file kontrak.
  Ikuti panduan langkah demi langkah ini untuk memuat sertifikat dari PFX dan membuat
  tanda tangan XAdES EPES.
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: Tanda tangani dokumen Word di C# – muat sertifikat X509 dan terapkan tanda
  tangan digital
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to sign word document with a digital signature for contract
    files. This guide covers loading x509 certificate from a PFX and creating the
    signature.
  headline: How to sign word document in C# using an X509 certificate
  type: TechArticle
tags:
- digital signature
- C#
- X509Certificate2
title: Cara menandatangani dokumen Word di C# menggunakan sertifikat X509
url: /id/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menandatangani dokumen Word di C# menggunakan sertifikat X509

Jika Anda perlu **menandatangani dokumen Word** secara programatis, tutorial ini menunjukkan solusi lengkap yang siap dijalankan. Anda akan belajar cara **memuat sertifikat x509** dari file *.pfx*, mengonfigurasi level tanda tangan, dan menghasilkan tanda tangan XML yang sesuai standar yang dapat dilampirkan ke kontrak.  

Langkah-langkah di bawah ini bekerja dengan .NET 6+ dan perpustakaan gratis GroupDocs.Signature untuk .NET, yang mengabstraksi detail XML‑DSig tingkat rendah sambil tetap memberi Anda kontrol penuh atas proses penandatanganan.

## Prasyarat

- .NET 6 SDK atau yang lebih baru terinstal  
- Visual Studio 2022 (atau IDE apa pun yang mendukung .NET)  
- Sertifikat X509 yang valid dalam format **PFX** (`certificate.pfx`) dengan kata sandi yang diketahui  
- Paket NuGet `GroupDocs.Signature` (pasang dengan `dotnet add package GroupDocs.Signature`)  

> **Mengapa prasyarat ini?**  
> Kelas `X509Certificate2` dapat membaca PFX hanya ketika kunci pribadi dapat diekspor, dan GroupDocs.Signature menangani level XAdES EPES yang diperlukan untuk banyak **digital signature for contract** skenario.

## Langkah 1: Muat sertifikat penandatangan (load x509 certificate)

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**Penjelasan**  
`X509Certificate2` membaca **load certificate from pfx** file dan membuat kunci pribadi tersedia untuk penandatanganan. Flag tersebut memastikan kunci disimpan di penyimpanan mesin, yang menghindari masalah izin pada layanan Windows.

**Tips Pro:** Jika Anda menerima `CryptographicException` tentang akses kunci, pastikan akun yang menjalankan kode memiliki izin baca pada file PFX dan kunci ditandai sebagai dapat diekspor.

## Langkah 2: Inisialisasi SignatureHelper dan tetapkan sertifikat

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**Penjelasan**  
`SignatureHelper` adalah pembungkus tipis di atas GroupDocs.Signature yang menyederhanakan alur kerja. Dengan memanggil `SetCertificate`, Anda memberi tahu perpustakaan kunci pribadi mana yang akan digunakan untuk operasi **how to sign document**.

## Langkah 3: Pilih level tanda tangan XAdES (digital signature for contract)

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**Penjelasan**  
XAdES‑EPES (Explicit Policy‑Based Electronic Signature) memenuhi sebagian besar persyaratan hukum untuk **digital signature for contract**. Perpustakaan secara otomatis akan membuat elemen `<QualifyingProperties>` yang diperlukan.

## Langkah 4: Muat dokumen Word yang akan ditandatangani

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**Penjelasan**  
`Document` mewakili file Word dalam memori. Itu dapat berupa file `.docx` apa pun; kode yang sama bekerja untuk PDF atau format OpenXML lainnya jika Anda mengubah ekstensi file.

## Langkah 5: Hasilkan file tanda tangan XML

```csharp
// Destination for the generated XML signature
string signaturePath = @"C:\Contracts\signature.xml";

// Perform the signing operation
signer.SignDocument(document, signaturePath);

// Optional: verify that the file was created
if (System.IO.File.Exists(signaturePath))
{
    Console.WriteLine($"Signature saved to: {signaturePath}");
}
```

**Penjelasan**  
`SignDocument` membuat file XML yang sesuai dengan profil XAdES EPES. `signature.xml` yang dihasilkan dapat dikirim bersama file Word asli atau disematkan nanti menggunakan bagian XML khusus.

**Expected output**

```
Signature saved to: C:\Contracts\signature.xml
```

File XML akan berisi elemen seperti `<Signature>`, `<SignedInfo>`, dan `<X509Data>` yang merujuk pada **load x509 certificate** yang dimuat.

## Contoh lengkap yang dapat dijalankan

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;

class Program
{
    static void Main()
    {
        // 1. Load the signing certificate (load x509 certificate)
        string certPath = @"C:\Certificates\certificate.pfx";
        string certPassword = "yourPassword";
        X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
            X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);

        // 2. Initialize the SignatureHelper and assign the certificate
        SignatureHelper signer = new SignatureHelper();
        signer.SetCertificate(certificate);

        // 3. Set the XAdES signature level (digital signature for contract)
        signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 4. Load the Word document that will be signed
        string docPath = @"C:\Contracts\contract.docx";
        Document document = new Document(docPath);

        // 5. Generate the XML signature file
        string signaturePath = @"C:\Contracts\signature.xml";
        signer.SignDocument(document, signaturePath);

        // Confirmation
        Console.WriteLine(File.Exists(signaturePath)
            ? $"Signature saved to: {signaturePath}"
            : "Failed to create signature file.");
    }
}
```

Simpan file sebagai `Program.cs`, jalankan `dotnet run`, dan Anda akan memperoleh file XML yang ditandatangani siap untuk verifikasi hukum.

## Variasi umum dan kasus tepi

| Scenario | What to change | Why |
|----------|----------------|-----|
| **Menandatangani PDF alih-alih Word** | Ganti `Document` dengan `PdfDocument` dan sesuaikan ekstensi file. | GroupDocs.Signature mendukung banyak format; alur penandatanganan tetap identik. |
| **Menggunakan sertifikat dari Windows Store** | Muat sertifikat melalui `X509Store` alih-alih file PFX. | Berguna ketika kunci pribadi tidak pernah meninggalkan mesin demi alasan kepatuhan. |
| **Menambahkan timestamp** | Panggil `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))`. | Banyak alur kerja kontrak memerlukan timestamp tepercaya untuk membuktikan kapan tanda tangan diterapkan. |
| **Menyematkan tanda tangan ke dalam .docx** | Gunakan `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })`. | Penyematan menyederhanakan distribusi karena hanya satu file yang dibutuhkan. |

## Tips untuk penggunaan produksi

- **Amankan PFX** – simpan di Azure Key Vault atau AWS Secrets Manager alih-alih sistem file.  
- **Validasi rantai sertifikat** sebelum menandatangani untuk memastikan penandatangan dipercaya.  
- **Catat operasi penandatanganan** (sidik jari sertifikat, hash dokumen, timestamp) untuk jejak audit yang diperlukan oleh kebanyakan kebijakan **digital signature for contract**.

## Kesimpulan

Anda sekarang tahu cara **menandatangani dokumen Word** secara programatis, cara **memuat sertifikat x509** dari file PFX, dan cara menghasilkan file **digital signature for contract** yang sesuai standar. Contoh ini mencakup seluruh alur kerja **how to sign document**, dari pemuatan sertifikat hingga pembuatan tanda tangan, dan mencakup variasi umum yang mungkin Anda temui dalam proyek nyata.

**Langkah selanjutnya**

- Jelajahi level tanda tangan lain seperti XAdES‑T atau XAdES‑LT untuk validitas jangka panjang.  
- Coba sematkan tanda tangan XML langsung ke file Word menggunakan opsi `EmbedIntoDocument`.  
- Integrasikan logika verifikasi (`signer.VerifyDocument`) untuk mengonfirmasi tanda tangan pada kontrak yang masuk.

Silakan sesuaikan kode dengan struktur proyek Anda sendiri, dan selamat menandatangani!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Mendeteksi Tanda Tangan Digital pada Dokumen Word](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Mengakses dan Memverifikasi Tanda Tangan di Dokumen Word](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Menandatangani Garis Tanda Tangan yang Ada di Dokumen Word](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}