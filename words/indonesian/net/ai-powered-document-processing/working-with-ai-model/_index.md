---
title: Bekerja dengan Model AI
linktitle: Bekerja dengan Model AI
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menggunakan Aspose.Words untuk .NET guna meringkas dokumen dengan AI. Langkah mudah untuk meningkatkan manajemen dokumen.
weight: 10
url: /id/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bekerja dengan Model AI

## Perkenalan

Selamat datang di dunia Aspose.Words yang memikat untuk .NET! Jika Anda pernah ingin membawa manajemen dokumen ke tingkat berikutnya, Anda berada di tempat yang tepat. Bayangkan memiliki kemampuan untuk meringkas dokumen besar secara otomatis hanya dengan beberapa baris kode. Kedengarannya menakjubkan, bukan? Dalam panduan ini, kita akan menyelami lebih dalam penggunaan Aspose.Words untuk membuat ringkasan dokumen menggunakan model bahasa AI yang canggih seperti GPT OpenAI. Baik Anda seorang pengembang yang ingin meningkatkan aplikasi Anda atau penggemar teknologi yang ingin mempelajari sesuatu yang baru, tutorial ini akan membantu Anda.

## Prasyarat

Sebelum kita mulai membuat kode, ada beberapa hal penting yang perlu Anda siapkan:

1. Visual Studio Terpasang: Pastikan Anda telah memasang Visual Studio di komputer Anda. Anda dapat mengunduhnya secara gratis jika belum memilikinya.
  
2. .NET Framework: Pastikan Anda menggunakan versi .NET Framework yang kompatibel untuk Aspose.Words. Versi ini mendukung .NET Framework dan .NET Core.

3.  Aspose.Words untuk .NET: Anda perlu mengunduh dan menginstal Aspose.Words. Anda dapat mengunduh versi terbaru[Di Sini](https://releases.aspose.com/words/net/).

4. Kunci API untuk Model AI: Untuk memanfaatkan ringkasan AI, Anda memerlukan akses ke model AI. Dapatkan kunci API Anda dari platform seperti OpenAI atau Google.

5. Pengetahuan Dasar C#: Pemahaman mendasar tentang pemrograman C# diperlukan untuk memanfaatkan tutorial ini sebaik-baiknya.

Sudah punya semuanya? Keren! Mari kita masuk ke bagian yang menyenangkan - mengimpor paket yang kita butuhkan.

## Paket Impor

Untuk memanfaatkan kekuatan Aspose.Words dan bekerja dengan model AI, kami mulai dengan mengimpor paket yang diperlukan. Berikut cara melakukannya:

### Buat Proyek Baru

Pertama, jalankan Visual Studio dan buat proyek Aplikasi Konsol baru.

1. Buka Visual Studio.
2. Klik “Buat proyek baru.”
3. Pilih “Aplikasi Konsol (.NET Framework)” atau “Aplikasi Konsol (.NET Core)” berdasarkan pengaturan Anda.
4. Beri nama proyek Anda dan tentukan lokasinya.

### Instal Aspose.Words dan Paket Model AI

Untuk menggunakan Aspose.Words, Anda perlu menginstal paket melalui NuGet.

1. Klik kanan pada proyek Anda di Solution Explorer dan pilih “Kelola Paket NuGet.”
2. Cari “Aspose.Words” dan klik “Instal.”
3. Jika Anda menggunakan paket model AI tertentu (seperti OpenAI), pastikan juga paket tersebut terinstal.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Selamat! Setelah paketnya siap, mari kita bahas lebih lanjut implementasinya.

## Langkah 1: Siapkan Direktori Dokumen Anda

Dalam kode kita, kita akan menentukan direktori untuk mengelola tempat penyimpanan dokumen kita dan tempat keluaran kita akan ditempatkan. 

```csharp
// Direktori Dokumen Anda
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Direktori ArtifactsDir Anda
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Di sini, ganti`YOUR_DOCUMENT_DIRECTORY` dengan lokasi tempat dokumen Anda disimpan dan`YOUR_ARTIFACTS_DIRECTORY` di mana Anda ingin menyimpan berkas yang diringkas.

## Langkah 2: Muat Dokumen

Selanjutnya, kita akan memuat dokumen yang ingin kita rangkum ke dalam program kita. Semudah itu! Begini caranya:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Sesuaikan nama berkas dengan nama yang telah Anda simpan. Contoh ini mengasumsikan Anda memiliki dua dokumen bernama “Big document.docx” dan “Document.docx.”

## Langkah 3: Inisialisasi Model AI

Langkah selanjutnya adalah membuat koneksi dengan model AI. Di sinilah kunci API yang Anda dapatkan sebelumnya berperan.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Pastikan kunci API Anda disimpan sebagai variabel lingkungan. Ini seperti menjaga saus rahasia Anda tetap aman!

## Langkah 4: Buat Ringkasan untuk Dokumen Pertama

Sekarang, mari kita buat ringkasan untuk dokumen pertama kita. Kita akan menetapkan parameter untuk menentukan panjang ringkasan juga.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Cuplikan ini meringkas dokumen pertama dan menyimpan output dalam direktori artifak yang Anda tentukan. Jangan ragu untuk mengubah panjang ringkasan sesuai keinginan Anda!

## Langkah 5: Hasilkan Ringkasan untuk Beberapa Dokumen

Merasa berani? Anda juga dapat meringkas beberapa dokumen sekaligus! Berikut cara melakukannya:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Seperti itu, Anda meringkas dua dokumen secara bersamaan! Bicara soal efisiensi, bukan?

## Kesimpulan

Nah, itu dia! Dengan mengikuti panduan ini, Anda telah menguasai seni meringkas dokumen menggunakan Aspose.Words untuk .NET dan model AI yang canggih. Ini adalah fitur menarik yang dapat menghemat banyak waktu Anda, baik untuk penggunaan pribadi maupun integrasi ke dalam aplikasi profesional. Sekarang, manfaatkan kekuatan otomatisasi, dan lihat produktivitas Anda meningkat!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memodifikasi, mengonversi, dan merender dokumen Word secara terprogram.

### Bagaimana cara mendapatkan kunci API untuk model AI?
Anda dapat memperoleh kunci API dari penyedia AI seperti OpenAI atau Google. Pastikan untuk membuat akun dan mengikuti petunjuk mereka untuk membuat kunci Anda.

### Dapatkah saya menggunakan Aspose.Words untuk format file lain?
Ya! Aspose.Words mendukung berbagai format file, termasuk DOCX, RTF, dan HTML, yang menyediakan kemampuan lebih dari sekadar dokumen teks.

### Apakah ada versi gratis Aspose.Words?
Aspose menawarkan uji coba gratis, yang memungkinkan Anda menguji fitur-fiturnya. Anda dapat mengunduhnya dari situs mereka.

### Di mana saya dapat menemukan lebih banyak sumber daya untuk Aspose.Words?
 Anda dapat memeriksa dokumentasinya[Di Sini](https://reference.aspose.com/words/net/) untuk panduan dan wawasan yang komprehensif.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
