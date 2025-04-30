---
"description": "Tingkatkan pemrosesan dokumen Anda dengan Aspose.Words untuk .NET dan Google AI untuk membuat ringkasan ringkas dengan mudah."
"linktitle": "Bekerja dengan Model AI Google"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Bekerja dengan Model AI Google"
"url": "/id/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bekerja dengan Model AI Google

## Perkenalan

Dalam artikel ini, kita akan membahas cara meringkas dokumen menggunakan Aspose.Words dan model AI Google langkah demi langkah. Baik Anda ingin meringkas laporan yang panjang atau mengekstrak wawasan dari berbagai sumber, kami siap membantu Anda.

## Prasyarat

Sebelum masuk ke bagian praktis, mari pastikan Anda siap untuk meraih kesuksesan. Berikut ini yang Anda perlukan:

1. Pengetahuan Dasar tentang C# dan .NET: Keakraban dengan konsep pemrograman akan membantu Anda memahami contoh dengan lebih baik.
   
2. Pustaka Aspose.Words untuk .NET: Pustaka canggih ini memungkinkan Anda membuat dan memanipulasi dokumen Word dengan mudah. Anda dapat [unduh disini](https://releases.aspose.com/words/net/).

3. Kunci API untuk Model AI Google: Untuk memanfaatkan model AI, Anda memerlukan kunci API untuk autentikasi. Simpan kunci tersebut dengan aman di variabel lingkungan Anda.

4. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan .NET yang berfungsi (Visual Studio atau IDE lainnya).

5. Contoh Dokumen: Anda memerlukan contoh dokumen Word (misalnya, "Dokumen besar.docx", "Dokumen.docx") untuk menguji ringkasan.

Sekarang setelah kita membahas dasar-dasarnya, mari selami kodenya!

## Paket Impor

Untuk bekerja dengan Aspose.Words dan mengintegrasikan model AI Google, Anda perlu mengimpor namespace yang diperlukan. Berikut cara melakukannya:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Sekarang setelah Anda mengimpor paket yang diperlukan, mari kita uraikan proses meringkas dokumen langkah demi langkah.

## Langkah 1: Menyiapkan Direktori Dokumen Anda

Sebelum kita dapat memproses dokumen, kita perlu menentukan di mana file kita berada. Langkah ini penting untuk memastikan bahwa Aspose.Words dapat mengakses dokumen tersebut.

```csharp
// Direktori Dokumen Anda
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Direktori ArtifactsDir Anda
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Mengganti `"YOUR_DOCUMENT_DIRECTORY"` Dan `"YOUR_ARTIFACTS_DIRECTORY"` dengan jalur aktual pada sistem tempat dokumen Anda disimpan. Ini akan berfungsi sebagai dasar untuk membaca dan menyimpan dokumen.

## Langkah 2: Memuat Dokumen

Selanjutnya, kita perlu memuat dokumen yang ingin kita rangkum. Dalam kasus ini, Anda akan memuat dua dokumen yang telah kita tentukan sebelumnya.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

Itu `Document` kelas dari Aspose.Words memungkinkan Anda memuat berkas Word ke dalam memori. Pastikan nama berkas sesuai dengan dokumen sebenarnya di direktori Anda, atau Anda akan mengalami galat berkas tidak ditemukan!

## Langkah 3: Mengambil Kunci API

Untuk memanfaatkan model AI, Anda perlu mengambil Kunci API. Kunci ini berfungsi sebagai akses ke layanan Google AI.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Baris kode ini mengambil kunci API yang telah Anda simpan dalam variabel lingkungan Anda. Sebaiknya jangan masukkan informasi sensitif seperti kunci API ke dalam kode Anda demi alasan keamanan.

## Langkah 4: Membuat Instansi Model AI

Sekarang, saatnya membuat contoh model AI. Di sini Anda dapat memilih model mana yang akan digunakan—dalam contoh ini, kami memilih model GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Baris ini menyiapkan model AI yang akan Anda gunakan untuk meringkas dokumen. Pastikan untuk berkonsultasi [dokumentasi](https://reference.aspose.com/words/net/) untuk mengetahui rincian mengenai berbagai model dan kemampuannya.

## Langkah 5: Merangkum Satu Dokumen

Mari kita fokus pada rangkuman dokumen pertama. Kita dapat memilih untuk mendapatkan rangkuman singkat di sini.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Pada langkah ini, kami menggunakan `Summarize` metode dari instans model AI untuk mendapatkan ringkasan dokumen pertama. Panjang ringkasan ditetapkan menjadi pendek, tetapi Anda dapat menyesuaikannya tergantung pada kebutuhan Anda. Terakhir, dokumen yang diringkas disimpan ke direktori artefak Anda.

## Langkah 6: Merangkum Beberapa Dokumen

Ingin meringkas beberapa dokumen sekaligus? Aspose.Words juga memudahkannya!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Di sini, kami memanggil `Summarize` metode lagi, tetapi kali ini dengan serangkaian dokumen. Ini akan memberi Anda ringkasan panjang yang merangkum esensi kedua berkas. Sama seperti sebelumnya, hasilnya disimpan dalam direktori artefak yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menyiapkan lingkungan untuk meringkas dokumen menggunakan Aspose.Words untuk .NET dan model AI Google. Mulai dari memuat dokumen hingga membuat ringkasan singkat, langkah-langkah ini menyediakan pendekatan yang efisien untuk mengelola teks dalam jumlah besar secara efektif.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words?
Aspose.Words adalah pustaka yang hebat untuk membuat, memodifikasi, dan mengonversi dokumen Word menggunakan .NET.

### Bagaimana cara mendapatkan kunci API untuk Google AI?
Anda biasanya dapat memperoleh kunci API dengan mendaftar ke Google Cloud dan mengaktifkan layanan API yang diperlukan.

### Bisakah saya meringkas beberapa dokumen sekaligus?
Ya! Seperti yang ditunjukkan, Anda dapat meneruskan serangkaian dokumen ke metode ringkasan.

### Jenis ringkasan apa yang dapat saya buat?
Anda dapat memilih ringkasan pendek, sedang, dan panjang berdasarkan kebutuhan Anda.

### Di mana saya dapat menemukan lebih banyak sumber daya Aspose.Words?
Lihat di sini [dokumentasi](https://reference.aspose.com/words/net/) untuk contoh dan panduan lebih lanjut.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}