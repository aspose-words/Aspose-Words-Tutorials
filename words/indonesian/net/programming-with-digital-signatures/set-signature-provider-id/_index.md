---
title: Mengatur ID Penyedia Tanda Tangan di Dokumen Word
linktitle: Mengatur ID Penyedia Tanda Tangan di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Tetapkan ID Penyedia Tanda Tangan dengan aman di dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan terperinci kami yang terdiri dari 2000 kata untuk menandatangani dokumen Anda secara digital.
weight: 10
url: /id/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur ID Penyedia Tanda Tangan di Dokumen Word

## Perkenalan

Hai! Jadi, Anda memiliki dokumen Word yang luar biasa ini yang memerlukan tanda tangan digital, bukan? Namun, bukan sembarang tanda tangan—Anda perlu menetapkan ID Penyedia Tanda Tangan tertentu. Baik Anda menangani dokumen hukum, kontrak, atau dokumen apa pun, menambahkan tanda tangan digital yang aman sangatlah penting. Dalam tutorial ini, saya akan memandu Anda melalui seluruh proses pengaturan ID Penyedia Tanda Tangan dalam dokumen Word menggunakan Aspose.Words untuk .NET. Siap? Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk Pustaka .NET: Jika Anda belum melakukannya,[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE apa pun yang kompatibel dengan C#.
3. Dokumen Word: Dokumen dengan baris tanda tangan (`Signature line.docx`).
4.  Sertifikat Digital: A`.pfx` file sertifikat (misalnya,`morzal.pfx`).
5. Pengetahuan Dasar C#: Hanya dasar-dasarnya—jangan khawatir, kami di sini untuk membantu!

Sekarang, mari kita mulai aksinya!

## Mengimpor Ruang Nama

Pertama-tama, pastikan Anda menyertakan namespace yang diperlukan dalam proyek Anda. Ini penting untuk mengakses pustaka Aspose.Words dan kelas terkait.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

Baiklah, mari kita uraikan ini menjadi langkah-langkah yang sederhana dan mudah dicerna.

## Langkah 1: Muat Dokumen Word Anda

Langkah pertama adalah memuat dokumen Word yang berisi baris tanda tangan. Dokumen ini akan dimodifikasi untuk menyertakan tanda tangan digital dengan ID Penyedia Tanda Tangan yang ditentukan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Di sini, kami menentukan direktori tempat dokumen Anda berada. Ganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke dokumen Anda.

## Langkah 2: Akses Baris Tanda Tangan

Selanjutnya, kita perlu mengakses baris tanda tangan di dalam dokumen. Baris tanda tangan disematkan sebagai objek bentuk di dokumen Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Baris kode ini mendapatkan bentuk pertama di badan bagian pertama dokumen dan melemparkannya ke`SignatureLine` obyek.

## Langkah 3: Siapkan Opsi Tanda

Sekarang, kita membuat opsi tanda, yang menyertakan ID Penyedia dan ID Baris Tanda Tangan dari baris tanda tangan yang diakses.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Pilihan ini akan digunakan saat menandatangani dokumen untuk memastikan ID Penyedia Tanda Tangan yang benar telah ditetapkan.

## Langkah 4: Muat Sertifikat

 Untuk menandatangani dokumen secara digital, Anda memerlukan sertifikat. Berikut cara memuatnya`.pfx` mengajukan:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Mengganti`"aw"` dengan kata sandi untuk berkas sertifikat Anda jika ada.

## Langkah 5: Tandatangani Dokumen

 Akhirnya, saatnya untuk menandatangani dokumen menggunakan`DigitalSignatureUtil.Sign` metode.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Ini menandatangani dokumen Anda dan menyimpannya sebagai file baru,`Digitally signed.docx`.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menetapkan ID Penyedia Tanda Tangan dalam dokumen Word menggunakan Aspose.Words untuk .NET. Proses ini tidak hanya mengamankan dokumen Anda, tetapi juga memastikan dokumen tersebut mematuhi standar tanda tangan digital. Sekarang, lanjutkan dan cobalah dengan dokumen Anda. Ada pertanyaan? Lihat FAQ di bawah ini atau kunjungi[Forum dukungan Aspose](https://forum.aspose.com/c/words/8).

## Pertanyaan yang Sering Diajukan

### Apa itu ID Penyedia Tanda Tangan?

ID Penyedia Tanda Tangan secara unik mengidentifikasi penyedia tanda tangan digital, memastikan keaslian dan keamanan.

### Bisakah saya menggunakan file .pfx untuk penandatanganan?

Ya, asalkan sertifikat digitalnya valid. Pastikan Anda memiliki kata sandi yang benar jika sertifikat tersebut dilindungi.

### Bagaimana cara mendapatkan file .pfx?

Anda dapat memperoleh file .pfx dari Otoritas Sertifikat (CA) atau membuatnya menggunakan alat seperti OpenSSL.

### Bisakah saya menandatangani beberapa dokumen sekaligus?

Ya, Anda dapat mengulang beberapa dokumen dan menerapkan proses penandatanganan yang sama untuk masing-masing dokumen.

### Bagaimana jika saya tidak memiliki baris tanda tangan di dokumen saya?

Anda harus memasukkan baris tanda tangan terlebih dahulu. Aspose.Words menyediakan metode untuk menambahkan baris tanda tangan secara terprogram.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
