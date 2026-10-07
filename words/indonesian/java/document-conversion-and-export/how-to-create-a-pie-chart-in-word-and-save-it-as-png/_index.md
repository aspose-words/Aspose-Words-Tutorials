---
category: general
date: 2026-10-07
description: Pelajari cara membuat diagram lingkaran di Word, menambahkan seri data,
  dan menyimpan diagram sebagai PNG menggunakan Java. Ikuti panduan langkah demi langkah
  untuk hasil cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: id
lastmod: 2026-10-07
og_description: 'Buat diagram lingkaran di Word dengan cepat: tutorial ini menunjukkan
  cara menambahkan seri data, menghasilkan diagram, dan menyimpan diagram Word sebagai
  gambar (PNG). Ikuti contoh kode lengkap.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Buat diagram lingkaran di Word dan ekspor sebagai PNG – panduan
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Cara membuat diagram lingkaran di Word dan menyimpannya sebagai PNG
url: /id/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram pai di Word dan menyimpannya sebagai PNG

Jika Anda perlu **membuat diagram pai** di dalam file Microsoft Word, panduan ini menunjukkan secara tepat cara melakukannya dengan Java. Anda juga akan belajar cara **menambahkan seri data** ke diagram dan **menyimpan diagram sebagai PNG** sehingga visual tersebut dapat digunakan kembali di luar Word.

Membuat diagram langsung dalam dokumen menghemat Anda dari mengekspor data ke alat grafis terpisah. Pada akhir tutorial ini Anda akan memiliki file Word yang berfungsi penuh yang berisi diagram pai dan gambar PNG yang cocok di disk.

## Prasyarat

* Java 17 atau yang lebih baru terinstal.
* **GroupDocs.Viewer for Java** (atau perpustakaan kompatibel yang menyediakan kelas `Document`, `Chart`, `ChartType`, dan `ImageSaveOptions`).
* Proyek Maven atau Gradle di mana Anda dapat menambahkan dependensi perpustakaan.
* Dokumen Word input (`input.docx`) yang berada di folder yang dapat Anda referensikan dari kode.

Jika Anda menggunakan Maven, tambahkan dependensi (ganti `VERSION` dengan rilis terbaru):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Cara membuat diagram pai di Word

Inti solusi berputar di sekitar tiga tindakan:

1. Memuat file `.docx` sumber.
2. **Menambahkan seri data** ke objek `Chart` baru dengan tipe `PIE`.
3. **Menyimpan diagram sebagai PNG** sehingga Anda memperoleh file gambar di samping dokumen Word.

Setiap langkah dijelaskan secara detail di bawah ini, diikuti oleh kode Java yang tepat yang Anda butuhkan.

### Langkah 1: Memuat dokumen sumber

Anda harus membuka file Word yang akan menampung diagram. Kelas `Document` membaca konten `.docx` ke dalam memori.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Mengapa ini penting*: Memuat dokumen membuat model yang dapat diubah. Semua operasi diagram berikutnya memodifikasi representasi dalam memori ini, yang kemudian Anda simpan kembali ke disk.

### Langkah 2: Menambahkan seri data ke diagram

Membuat **diagram pai** dimulai dengan sebuah instance `Chart`. Konstruktor menerima `Document` induk dan tipe diagram (`ChartType.PIE`). Setelah objek diagram ada, Anda mengisinya dengan nilai numerik dan label opsional.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Mengapa ini penting*: Metode `add` **menambahkan seri data** ke diagram. Setiap entri dalam `values` menjadi irisan pai, sementara `categories` menyediakan label legenda. Anda dapat memberikan sejumlah poin apa pun; perpustakaan akan secara otomatis menghitung sudut irisan.

### Langkah 3: Menyimpan diagram sebagai PNG

Setelah diagram menjadi bagian dari dokumen, Anda dapat mengekspor representasi visualnya. Metode `save` pada objek diagram yang mendasarinya menulis file PNG ke sistem file.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Mengapa ini penting*: Menyimpan diagram sebagai PNG memberi Anda gambar raster yang dapat disisipkan ke halaman web, email, atau laporan tanpa memerlukan file Word asli. Objek `ImageSaveOptions` memungkinkan Anda mengontrol format, resolusi, dan pengaturan ekspor lainnya.

## Menghasilkan diagram pai di Word – menyesuaikan tampilan

Selain langkah dasar, Anda mungkin ingin menyesuaikan warna, judul, atau label data. Sebagian besar perpustakaan menyediakan objek `ChartOptions` atau serupa. Berikut contoh singkat yang menambahkan judul dan mengubah warna irisan:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Penyesuaian ini bersifat opsional tetapi menggambarkan bagaimana Anda dapat **menghasilkan diagram pai di Word** yang sesuai dengan merek Anda.

## Menyimpan diagram Word sebagai gambar – pendekatan alternatif

Jika Anda hanya memerlukan gambar dan bukan diagram di dalam dokumen, Anda dapat melewatkan penyisipan bentuk diagram ke file Word dan langsung memanggil metode `save` setelah membuat diagram. Kode tetap sama; Anda cukup menghilangkan langkah apa pun yang menambahkan diagram ke badan dokumen.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Teknik ini berguna ketika Anda menghasilkan banyak diagram dalam proses batch dan hanya menginginkan output PNG.

## Contoh lengkap yang dapat dijalankan

Salin kelas berikut ke dalam proyek Anda, sesuaikan jalur file, dan jalankan. Program akan:

1. Memuat `input.docx`.
2. **Membuat diagram pai**, **menambahkan seri data**, dan menyisipkannya ke dalam dokumen.
3. **Menyimpan diagram sebagai PNG** (`radial.png`).
4. Menyimpan file Word yang dimodifikasi sebagai `output.docx`.



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Buat Diagram Sebar Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}