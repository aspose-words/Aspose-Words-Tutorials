---
category: general
date: 2026-09-08
description: Cara menandatangani dokumen Word menggunakan alur kerja tanda tangan
  digital docx, memuat sertifikat pfx, dan membuat tanda tangan XAdES di C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: id
lastmod: 2026-09-08
og_description: Cara menandatangani dokumen Word menggunakan alur tanda tangan digital
  docx, memuat sertifikat pfx, dan membuat tanda tangan XAdES di C#. Ikuti contoh
  lengkapnya.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Cara menandatangani dokumen Word dengan XAdES EPES di C# – panduan langkah
  demi langkah
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Cara menandatangani dokumen Word dengan XAdES EPES di C#
url: /id/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menandatangani dokumen Word dengan XAdES EPES di C#

Jika Anda perlu **cara menandatangani word** file secara programatik, panduan ini menunjukkan solusi lengkap yang siap produksi. Anda akan belajar cara memuat sertifikat PFX, mengonfigurasi **digital signature docx**, dan membuat tanda tangan XAdES‑EPES yang dapat diverifikasi oleh Microsoft Word dan validator pihak ketiga.

Contoh ini menggunakan pustaka GroupDocs.Signature untuk .NET, tetapi konsepnya berlaku untuk API apa pun yang mendukung XAdES. Pada akhir tutorial Anda akan memiliki file `Signed_XAdES_EPES.docx` yang telah ditandatangani siap didistribusikan.

## Apa yang Anda butuhkan

- .NET 6.0 atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- File sertifikat PFX yang valid (`.pfx`) yang berisi kunci pribadi
- Password untuk file PFX
- Dokumen Word (`.docx`) yang ingin Anda tandatangani
- Paket NuGet **GroupDocs.Signature** (pasang dengan `dotnet add package GroupDocs.Signature`)

## Langkah 1: Pasang paket NuGet yang diperlukan

```bash
dotnet add package GroupDocs.Signature
```

Paket ini menyediakan kelas `Document`, `XadesSignatureOptions`, dan tipe pembantu untuk membuat file **digitally sign word**.

## Langkah 2: Muat dokumen Word yang belum ditandatangani

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Memuat dokumen memberi Anda model objek yang dapat dimanipulasi sebelum menerapkan tanda tangan.

## Langkah 3: Muat sertifikat PFX (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** Jika sertifikat disimpan di Windows certificate store, Anda dapat mengambilnya dengan `X509Store` alih‑alih memuat file. Pendekatan `load pfx certificate` bekerja di semua platform, termasuk kontainer Linux.

## Langkah 4: (Opsional) Tambahkan baris tanda tangan visual

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Jika Anda lebih suka tanda tangan tak terlihat, Anda dapat melewati langkah ini. **digital signature docx** tetap sah secara kriptografis.

## Langkah 5: Konfigurasikan opsi XAdES‑EPES (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

Flag `XadesSignatureType.XAdES_EPES` memberi tahu pustaka untuk menyematkan tanda tangan sesuai profil EPES (Explicit Policy‑based Electronic Signature), yang secara luas diterima oleh regulasi EU e‑IDAS.

## Langkah 6: Terapkan tanda tangan digital

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

Metode `Sign` melakukan semua pekerjaan kriptografi: menghitung hash bagian dokumen, membuat struktur XML‑DSig, dan menyisipkan envelope XAdES ke dalam file Word.

## Langkah 7: Simpan dokumen yang ditandatangani

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Setelah disimpan, buka `Signed_XAdES_EPES.docx` di Microsoft Word. Anda akan melihat baris tanda tangan (jika Anda menambahkannya) dan bilah status **digitally sign word** yang menunjukkan bahwa file telah ditandatangani dan tanda tangan valid.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Output yang diharapkan

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Membuka file di Word menampilkan banner hijau “Signed” dan, jika Anda menambahkan baris visual, baris tanda tangan muncul di lokasi yang Anda tentukan.

## Menangani jebakan umum

| Masalah | Mengapa terjadi | Solusi |
|-------|----------------|-----|
| **Password sertifikat salah** | Konstruktor `X509Certificate2` melempar `CryptographicException`. | Verifikasi password, atau gunakan pengelola rahasia yang aman (Azure Key Vault, AWS Secrets Manager). |
| **Word menampilkan “Signature is invalid”** | Dokumen diubah setelah penandatanganan, atau kebijakan penandatanganan tidak ada. | Pastikan file disimpan **setelah** penandatanganan dan tidak diedit lagi. Sematkan kebijakan XAdES yang tepat jika regulator Anda memerlukannya. |
| **Baris tanda tangan tidak terlihat** | Dokumen menggunakan tata letak bagian yang berbeda. | Tambahkan `SignatureLine` ke paragraf yang tepat atau buat paragraf baru sebelum menambahkannya. |
| **Perlambatan kinerja pada dokumen besar** | Tanda tangan XAdES menghitung hash setiap bagian paket. | Gunakan API streaming (`SignAsync`) atau tingkatkan sumber daya mesin untuk file sangat besar (>50 MB). |

## Memperluas solusi

- **Multiple signers** – panggil `Sign` berulang kali dengan sertifikat berbeda dan atur `SignatureId` untuk membedakan masing‑masing penandatangan.
- **Timestamping** – tambahkan objek `TimestampOptions` ke `XadesSignatureOptions` untuk menyematkan timestamp tepercaya.
- **Custom policies** – sediakan file kebijakan XML melalui `XadesSignatureOptions.PolicyFilePath` untuk kepatuhan terhadap standar tertentu.

## Kesimpulan

Anda kini tahu **cara menandatangani word** dokumen secara programatik, cara **memuat pfx certificate**, dan cara **membuat xades signature** menggunakan GroupDocs.Signature. Tutorial ini mencakup setiap langkah mulai dari memuat dokumen hingga menyimpan output yang ditandatangani, dengan tip praktis untuk kasus tepi umum.  

Selanjutnya, jelajahi topik terkait seperti **digitally sign word** PDF, integrasikan verifikasi **digital signature docx**, atau tambahkan dukungan **timestamp** untuk memenuhi persyaratan kepatuhan lanjutan. Selamat menandatangani!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Deteksi Tanda Tangan Digital pada Dokumen Word](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Menandatangani Garis Tanda Tangan yang Ada di Dokumen Word](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Akses dan Verifikasi Tanda Tangan di Dokumen Word](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}