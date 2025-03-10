---
title: Menandatangani Dokumen Word Terenkripsi
linktitle: Menandatangani Dokumen Word Terenkripsi
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menandatangani dokumen Word yang dienkripsi menggunakan Aspose.Words untuk .NET dengan panduan terperinci dan langkah demi langkah ini. Sempurna untuk pengembang.
weight: 10
url: /id/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menandatangani Dokumen Word Terenkripsi

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara menandatangani dokumen Word yang dienkripsi? Hari ini, kita akan membahas proses ini menggunakan Aspose.Words untuk .NET. Bersiaplah untuk tutorial yang terperinci, menarik, dan menyenangkan!

## Prasyarat

Sebelum menyelami kodenya, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Unduh dan instal dari[Di Sini](https://releases.aspose.com/words/net/).
2. Visual Studio: Pastikan Anda telah menginstalnya.
3. Sertifikat yang Sah: Anda memerlukan file sertifikat .pfx.
4. Pengetahuan Dasar C#: Memahami dasar-dasar akan membuat tutorial ini lebih lancar.

## Mengimpor Ruang Nama

Pertama, mari impor namespace yang diperlukan. Namespace ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dikelola.

## Langkah 1: Menyiapkan Proyek Anda

Pertama-tama, siapkan proyek Visual Studio Anda. Buka Visual Studio dan buat Aplikasi Konsol C# baru. Beri nama yang deskriptif seperti "SignEncryptedWordDoc".

## Langkah 2: Menambahkan Aspose.Words ke Proyek Anda

Selanjutnya, kita perlu menambahkan Aspose.Words ke proyek Anda. Ada beberapa cara untuk melakukannya, tetapi menggunakan NuGet adalah cara yang paling mudah. 

1. Buka Konsol Manajer Paket NuGet dari Alat > Manajer Paket NuGet > Konsol Manajer Paket.
2. Jalankan perintah berikut:

```powershell
Install-Package Aspose.Words
```

## Langkah 3: Mempersiapkan Direktori Dokumen

Anda memerlukan direktori untuk menyimpan dokumen dan sertifikat Word Anda. Mari kita buat satu.

1. Buat direktori di komputer Anda. Untuk memudahkan, sebut saja "DocumentDirectory".
2. Tempatkan dokumen Word Anda (misalnya, "Document.docx") dan sertifikat .pfx Anda (misalnya, "morzal.pfx") di direktori ini.

## Langkah 4: Menulis Kode

 Sekarang, mari selami kodenya. Buka`Program.cs` file dan mulai dengan mengatur jalur ke direktori dokumen Anda dan menginisialisasi`SignOptions` dengan kata sandi dekripsi.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## Langkah 5: Memuat Sertifikat

 Selanjutnya, muat sertifikat Anda menggunakan`CertificateHolder`kelas. Ini akan memerlukan jalur ke file .pfx dan kata sandi sertifikat.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Langkah 6: Menandatangani Dokumen

 Terakhir, gunakan`DigitalSignatureUtil.Sign` metode untuk menandatangani dokumen Word terenkripsi Anda. Metode ini memerlukan berkas masukan, berkas keluaran, pemegang sertifikat, dan opsi tanda tangan.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## Langkah 7: Menjalankan Kode

Simpan berkas Anda dan jalankan proyek. Jika semuanya sudah diatur dengan benar, Anda akan melihat dokumen yang telah ditandatangani di direktori yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menandatangani dokumen Word yang dienkripsi menggunakan Aspose.Words untuk .NET. Dengan pustaka yang canggih ini, penandatanganan digital menjadi mudah, bahkan untuk file yang dienkripsi. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan jenis sertifikat yang berbeda?
Ya, Aspose.Words mendukung berbagai jenis sertifikat, asalkan dalam format yang benar.

### Apakah mungkin untuk menandatangani beberapa dokumen sekaligus?
Tentu saja! Anda dapat menelusuri kumpulan dokumen dan menandatanganinya secara terprogram.

### Bagaimana jika saya lupa kata sandi dekripsi?
Sayangnya, tanpa kata sandi dekripsi, Anda tidak akan dapat menandatangani dokumen tersebut.

### Bisakah saya menambahkan tanda tangan yang terlihat pada dokumen?
Ya, Aspose.Words memungkinkan Anda menambahkan tanda tangan digital yang terlihat juga.

### Apakah ada cara untuk memverifikasi tanda tangan?
 Ya, Anda bisa menggunakan`DigitalSignatureUtil.Verify` metode untuk memverifikasi tanda tangan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
