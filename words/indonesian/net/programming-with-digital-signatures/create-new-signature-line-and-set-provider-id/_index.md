---
title: Buat Baris Tanda Tangan Baru dan Tetapkan ID Penyedia
linktitle: Buat Baris Tanda Tangan Baru dan Tetapkan ID Penyedia
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat baris tanda tangan baru dan mengatur ID penyedia dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah.
weight: 10
url: /id/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Baris Tanda Tangan Baru dan Tetapkan ID Penyedia

## Perkenalan

Hai, para penggemar teknologi! Pernahkah Anda bertanya-tanya bagaimana cara menambahkan baris tanda tangan di dokumen Word Anda secara terprogram? Nah, hari ini kita akan membahasnya menggunakan Aspose.Words untuk .NET. Panduan ini akan memandu Anda melalui setiap langkah, membuatnya semudah membuat baris tanda tangan baru dan mengatur ID penyedia di dokumen Word Anda. Baik Anda mengotomatiskan pemrosesan dokumen atau hanya ingin menyederhanakan alur kerja, tutorial ini akan membantu Anda.

## Prasyarat

Sebelum kita mulai mengotori tangan kita, mari kita pastikan kita sudah punya semua yang kita butuhkan:

1.  Aspose.Words untuk .NET: Jika Anda belum melakukannya, unduh[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan C# lainnya.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework.
4. Sertifikat PFX: Untuk menandatangani dokumen, Anda memerlukan sertifikat PFX. Anda bisa mendapatkannya dari otoritas sertifikat tepercaya.

## Mengimpor Ruang Nama

Hal pertama yang pertama, mari impor namespace yang diperlukan dalam proyek C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Baiklah, mari kita langsung ke intinya. Berikut adalah uraian terperinci dari setiap langkah untuk membuat baris tanda tangan baru dan menetapkan ID penyedia.

## Langkah 1: Buat Dokumen Baru

Untuk memulai, kita perlu membuat dokumen Word baru. Ini akan menjadi kanvas untuk baris tanda tangan kita.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Dalam cuplikan ini, kami menginisialisasi yang baru`Document` dan sebuah`DocumentBuilder` . Itu`DocumentBuilder` membantu kita menambahkan elemen ke dokumen kita.

## Langkah 2: Tentukan Opsi Baris Tanda Tangan

Selanjutnya, kami menentukan opsi untuk baris tanda tangan kami. Ini termasuk nama penanda tangan, jabatan, email, dan detail lainnya.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Pilihan ini mempersonalisasi baris tanda tangan, menjadikannya jelas dan profesional.

## Langkah 3: Masukkan Baris Tanda Tangan

Setelah pilihan kita ditetapkan, kita sekarang dapat menyisipkan baris tanda tangan ke dalam dokumen.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Di sini,`InsertSignatureLine` metode menambahkan baris tanda tangan, dan kami menetapkan ID penyedia yang unik padanya.

## Langkah 4: Simpan Dokumen

Setelah menyisipkan baris tanda tangan, mari simpan dokumennya.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Ini akan menyimpan dokumen Anda dengan baris tanda tangan yang baru ditambahkan.

## Langkah 5: Siapkan Opsi Penandatanganan

Sekarang, kita perlu mengatur opsi untuk menandatangani dokumen. Ini termasuk ID baris tanda tangan, ID penyedia, komentar, dan waktu penandatanganan.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Pilihan ini memastikan dokumen ditandatangani dengan rincian yang benar.

## Langkah 6: Buat Pemegang Sertifikat

Untuk menandatangani dokumen, kita akan menggunakan sertifikat PFX. Mari kita buat pemegang sertifikat untuknya.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Pastikan untuk mengganti`"morzal.pfx"` dengan file sertifikat Anda yang sebenarnya dan`"aw"` dengan kata sandi sertifikat Anda.

## Langkah 7: Tandatangani Dokumen

Terakhir, kami menandatangani dokumen menggunakan utilitas tanda tangan digital.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Ini menandatangani dokumen dan menyimpannya sebagai berkas baru.

## Kesimpulan

Nah, itu dia! Anda telah berhasil membuat baris tanda tangan baru dan menetapkan ID penyedia dalam dokumen Word menggunakan Aspose.Words untuk .NET. Pustaka canggih ini memudahkan pengelolaan dan otomatisasi tugas pemrosesan dokumen. Cobalah dan lihat bagaimana pustaka ini dapat menyederhanakan alur kerja Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan baris tanda tangan?
 Tentu saja! Anda dapat mengubah berbagai opsi di`SignatureLineOptions`untuk memenuhi kebutuhan Anda.

### Bagaimana jika saya tidak memiliki sertifikat PFX?
Anda perlu memperolehnya dari otoritas sertifikat tepercaya. Sertifikat ini penting untuk menandatangani dokumen secara digital.

### Bisakah saya menambahkan beberapa baris tanda tangan ke sebuah dokumen?
Ya, Anda dapat menambahkan baris tanda tangan sebanyak yang diperlukan dengan mengulangi proses penyisipan dengan opsi yang berbeda.

### Apakah Aspose.Words untuk .NET kompatibel dengan .NET Core?
Ya, Aspose.Words untuk .NET mendukung .NET Core, membuatnya serbaguna untuk berbagai lingkungan pengembangan.

### Seberapa amankah tanda tangan digital?
Tanda tangan digital yang dibuat dengan Aspose.Words sangat aman, asalkan Anda menggunakan sertifikat yang valid dan tepercaya.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
