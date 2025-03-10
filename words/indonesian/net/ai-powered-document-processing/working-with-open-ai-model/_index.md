---
title: Bekerja dengan Model AI Terbuka
linktitle: Bekerja dengan Model AI Terbuka
second_title: API Pemrosesan Dokumen Aspose.Words
description: Dapatkan ringkasan dokumen yang efisien menggunakan Aspose.Words untuk .NET dengan model-model canggih OpenAI. Pelajari panduan lengkap ini sekarang.
weight: 10
url: /id/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bekerja dengan Model AI Terbuka

## Perkenalan

Di dunia digital saat ini, konten adalah raja. Baik Anda seorang pelajar, profesional bisnis, atau penulis yang tekun, kemampuan untuk memanipulasi, meringkas, dan membuat dokumen secara efisien sangatlah berharga. Di sinilah pustaka Aspose.Words untuk .NET berperan, yang memungkinkan Anda mengelola dokumen seperti seorang profesional. Dalam tutorial komprehensif ini, kita akan menyelami cara memanfaatkan Aspose.Words bersama dengan model OpenAI untuk meringkas dokumen secara efektif. Siap untuk membuka potensi pengelolaan dokumen Anda? Mari kita mulai!

## Prasyarat

Sebelum kita mulai dan menyelami kodenya, ada beberapa hal penting yang perlu Anda siapkan:

### Kerangka .NET
Pastikan Anda menjalankan versi .NET framework yang kompatibel dengan Aspose.Words. Secara umum, .NET 5.0 dan yang lebih baru seharusnya berfungsi dengan sempurna.

### Pustaka Aspose.Words untuk .NET
 Anda perlu mengunduh dan memasang pustaka Aspose.Words. Anda dapat mengunduhnya dari[tautan ini](https://releases.aspose.com/words/net/).

### Kunci API OpenAI
Untuk mengintegrasikan model bahasa OpenAI untuk peringkasan dokumen, Anda memerlukan Kunci API. Anda bisa mendapatkannya dengan mendaftar di platform OpenAI dan mengambil kunci dari pengaturan akun Anda.

### IDE untuk Pengembangan
Memiliki Lingkungan Pengembangan Terpadu (IDE) seperti Visual Studio sangat ideal untuk mengembangkan aplikasi .NET.

### Pengetahuan Pemrograman Dasar
Pemahaman dasar tentang C# dan pemrograman berorientasi objek akan membantu Anda memahami konsep tersebut dengan lebih mudah.

## Paket Impor

Setelah semuanya beres, mari impor paket-paket kita. Buka proyek Visual Studio Anda dan tambahkan pustaka yang diperlukan. Berikut cara melakukannya:

### Tambahkan Paket Aspose.Words

Anda dapat menambahkan paket Aspose.Words melalui NuGet Package Manager. Berikut cara melakukannya:
- Buka Alat -> Manajer Paket NuGet -> Kelola Paket NuGet untuk Solusi.
- Cari "Aspose.Words" dan klik Instal.

### Tambahkan Lingkungan Sistem

 Pastikan untuk menyertakan`System`namespace untuk menangani variabel lingkungan:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Tambahkan Aspose.Words

Kemudian, sertakan namespace Aspose.Words dalam file C# Anda:
```csharp
using Aspose.Words;
```

### Tambahkan Pustaka OpenAI

Jika Anda menggunakan pustaka untuk berinteraksi dengan OpenAI (seperti klien REST), pastikan untuk menyertakannya juga. Anda mungkin perlu menambahkannya melalui NuGet dengan cara yang sama seperti kami menambahkan Aspose.Words.

Sekarang setelah kita menyiapkan lingkungan kita dan mengimpor paket yang diperlukan, mari kita uraikan proses peringkasan dokumen langkah demi langkah.

## Langkah 1: Tentukan Direktori Dokumen Anda

Sebelum Anda dapat mulai mengolah dokumen Anda, Anda perlu menyiapkan direktori tempat dokumen dan artefak Anda akan berada:

```csharp
// Direktori Dokumen Anda
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Direktori Artefak Anda
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Hal ini membuat kode Anda lebih mudah dikelola, karena Anda dapat dengan mudah mengubah jalur jika diperlukan.`MyDir` adalah tempat dokumen masukan Anda disimpan, sementara`ArtifactsDir` adalah tempat Anda menyimpan ringkasan yang dibuat.

## Langkah 2: Muat Dokumen Anda

Berikutnya, Anda akan memuat dokumen yang ingin diringkas. Ini mudah dilakukan dengan Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Pastikan nama dokumen Anda sesuai dengan yang ingin Anda gunakan, jika tidak, Anda akan mengalami kesalahan!

## Langkah 3: Dapatkan Kunci API Anda

Setelah dokumen Anda dimuat, saatnya untuk mengambil kunci API OpenAI Anda. Anda akan mengambilnya dari variabel lingkungan untuk menjaganya tetap aman:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Sangat penting untuk mengelola kunci API Anda dengan aman guna menjauhkan pengguna yang tidak berwenang.

## Langkah 4: Buat Instansi Model OpenAI

Setelah kunci API Anda siap, kini Anda dapat membuat contoh model OpenAI. Untuk meringkas dokumen, kami akan menggunakan model Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Langkah ini pada dasarnya menyiapkan kekuatan otak yang dibutuhkan untuk meringkas dokumen Anda, memberi Anda akses ke ringkasan berbasis AI.

## Langkah 5: Ringkaslah Satu Dokumen

Mari kita rangkum dokumen pertama terlebih dahulu. Di sinilah keajaiban terjadi:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Di sini, kami menggunakan`Summarize` metode model.`SummaryLength.Short`parameter menentukan bahwa kita menginginkan ringkasan singkat — sempurna untuk ikhtisar cepat!

## Langkah 6: Ringkas Beberapa Dokumen

Merasa ambisius? Anda dapat meringkas beberapa dokumen sekaligus. Lihat saja betapa mudahnya:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Fitur ini sangat berguna untuk membandingkan beberapa berkas. Mungkin Anda sedang mempersiapkan rapat dan butuh catatan singkat dari beberapa laporan yang panjang. Ini adalah sahabat baru Anda!

## Kesimpulan

Merangkum dokumen dengan Aspose.Words untuk .NET dan OpenAI bukan hanya keterampilan yang bermanfaat; tetapi juga sangat memberdayakan. Dengan mengikuti panduan ini, Anda telah mengubah teks yang panjang dan rumit menjadi ringkasan yang ringkas, sehingga menghemat waktu dan tenaga Anda. Baik Anda ingin memastikan kejelasan bagi klien atau mempersiapkan presentasi penting, kini Anda memiliki alat untuk melakukannya secara efisien.

Jadi, tunggu apa lagi? Telusuri dokumen Anda dengan percaya diri dan biarkan teknologi melakukan pekerjaan beratnya!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?  
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen secara terprogram.

### Apakah saya memerlukan kunci API untuk OpenAI?  
Ya, Anda harus memiliki kunci API OpenAI yang valid untuk mengakses kemampuan ringkasan menggunakan model mereka.

### Bisakah saya meringkas beberapa dokumen sekaligus?  
Tentu saja! Anda dapat meringkas beberapa dokumen dalam satu panggilan, yang ideal untuk laporan yang ekstensif.

### Bagaimana cara menginstal Aspose.Words?  
Anda dapat menginstalnya melalui NuGet Package Manager di Visual Studio dengan mencari "Aspose.Words".

### Apakah ada uji coba gratis untuk Aspose.Words?  
 Ya, Anda dapat mengakses uji coba gratis Aspose.Words melalui[situs web](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
