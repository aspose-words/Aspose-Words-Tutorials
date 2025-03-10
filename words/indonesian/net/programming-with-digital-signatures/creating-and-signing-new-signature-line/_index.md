---
title: Membuat dan Menandatangani Baris Tanda Tangan Baru
linktitle: Membuat dan Menandatangani Baris Tanda Tangan Baru
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat dan menandatangani baris tanda tangan secara digital dalam dokumen Word menggunakan Aspose.Words for .NET dengan tutorial langkah demi langkah ini. Sempurna untuk otomatisasi dokumen.
weight: 10
url: /id/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dan Menandatangani Baris Tanda Tangan Baru

## Perkenalan

Hai! Jadi, Anda punya dokumen Word dan perlu menambahkan baris tanda tangan lalu menandatanganinya secara digital. Kedengarannya sulit? Sama sekali tidak! Berkat Aspose.Words untuk .NET, Anda dapat melakukannya dengan mudah hanya dengan beberapa baris kode. Dalam tutorial ini, kami akan memandu Anda melalui seluruh proses mulai dari menyiapkan lingkungan hingga menyimpan dokumen dengan tanda tangan baru yang mengilap. Siap? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang Anda butuhkan:
1.  Aspose.Words untuk .NET - Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan .NET - Visual Studio sangat direkomendasikan.
3. Dokumen untuk Ditandatangani - Buat dokumen Word sederhana atau gunakan dokumen Word yang sudah ada.
4.  File Sertifikat - Ini diperlukan untuk tanda tangan digital. Anda dapat menggunakan`.pfx` mengajukan.
5. Gambar untuk Baris Tanda Tangan - Opsional, file gambar untuk tanda tangan.

## Mengimpor Ruang Nama

Pertama, kita perlu mengimpor namespace yang diperlukan. Langkah ini penting karena menyiapkan lingkungan untuk menggunakan fungsi Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Langkah 1: Menyiapkan Direktori Dokumen

Setiap proyek memerlukan awal yang baik. Mari kita atur jalur ke direktori dokumen Anda. Di sinilah dokumen Anda akan disimpan dan diambil.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Membuat Dokumen Baru

Sekarang, mari kita buat dokumen Word baru menggunakan Aspose.Words. Ini akan menjadi kanvas tempat kita menambahkan baris tanda tangan.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Memasukkan Baris Tanda Tangan

 Di sinilah keajaiban terjadi. Kami memasukkan baris tanda tangan ke dalam dokumen kami menggunakan`DocumentBuilder` kelas.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Langkah 4: Menyimpan Dokumen dengan Baris Tanda Tangan

Setelah baris tanda tangan sudah ada, kita perlu menyimpan dokumen. Ini adalah langkah perantara sebelum kita melanjutkan untuk menandatanganinya.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Langkah 5: Menyiapkan Opsi Penandatanganan

Sekarang, mari kita atur opsi untuk menandatangani dokumen. Ini termasuk menentukan ID baris tanda tangan dan gambar yang akan digunakan.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Langkah 6: Memuat Sertifikat

Tanda tangan digital memerlukan sertifikat. Di sini, kami memuat berkas sertifikat yang akan digunakan untuk menandatangani dokumen.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Langkah 7: Menandatangani Dokumen

 Ini adalah langkah terakhir. Kami menggunakan`DigitalSignatureUtil`kelas untuk menandatangani dokumen. Dokumen yang ditandatangani disimpan dengan nama baru.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Kesimpulan

Nah, itu dia! Dengan langkah-langkah ini, Anda telah berhasil membuat dokumen Word baru, menambahkan baris tanda tangan, dan menandatanganinya secara digital menggunakan Aspose.Words untuk .NET. Ini adalah alat canggih yang memudahkan otomatisasi dokumen. Baik Anda berurusan dengan kontrak, perjanjian, atau dokumen formal apa pun, metode ini memastikan dokumen tersebut ditandatangani dan diautentikasi dengan aman.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan format gambar lain untuk baris tanda tangan?
Ya, Anda dapat menggunakan berbagai format gambar seperti PNG, JPG, BMP, dll.

###  Apakah perlu menggunakan`.pfx` file for the certificate?
 Ya, sebuah`.pfx` file adalah format umum untuk menyimpan informasi kriptografi termasuk sertifikat dan kunci pribadi.

### Bisakah saya menambahkan beberapa baris tanda tangan dalam satu dokumen?
Tentu saja! Anda dapat menyisipkan beberapa baris tanda tangan dengan mengulangi langkah penyisipan untuk setiap tanda tangan.

### Bagaimana jika saya tidak memiliki sertifikat digital?
Anda perlu memperoleh sertifikat digital dari otoritas sertifikat tepercaya atau membuatnya menggunakan alat seperti OpenSSL.

### Bagaimana cara memverifikasi tanda tangan digital dalam dokumen?
Anda dapat membuka dokumen yang ditandatangani di Word dan masuk ke detail tanda tangan untuk memverifikasi keaslian dan integritas tanda tangan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
