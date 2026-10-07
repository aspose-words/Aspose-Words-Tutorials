---
category: general
date: 2026-09-27
description: Pelajari cara menyisipkan diagram lingkaran ke dalam dokumen Word dengan
  Java, membuat diagram lingkaran di Word, dan menampilkan persentase pada diagram
  lingkaran untuk wawasan data yang jelas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: id
lastmod: 2026-09-27
og_description: Cara menyisipkan diagram lingkaran ke dalam dokumen Word dengan Java.
  Panduan ini menunjukkan cara membuat diagram lingkaran di Word, menampilkan persentase
  pada diagram lingkaran, dan menambahkan garis penunjuk.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Cara memasukkan diagram lingkaran ke dalam dokumen Word menggunakan Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Cara menyisipkan diagram lingkaran ke dalam dokumen Word menggunakan Java
url: /id/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan diagram pai ke dalam dokumen Word menggunakan Java

Jika Anda perlu **cara menyisipkan diagram pai** ke dalam file Word, panduan ini akan memandu Anda melalui proses lengkap. Anda akan melihat cara **membuat diagram pai di Word**, menampilkan persentase pada setiap irisan, dan menambahkan garis pemimpin untuk tampilan yang rapi.

Otomatisasi Word sering terasa berat, tetapi dengan Aspose.Words for Java Anda dapat menghasilkan dokumen yang sepenuhnya diformat secara programatis. Pada akhir tutorial ini Anda akan memiliki potongan kode Java yang dapat dijalankan yang menghasilkan dokumen Word berisi diagram pai yang bergaya.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

- Java 17 atau lebih baru terpasang
- Maven atau Gradle untuk mengelola dependensi
- Aspose.Words for Java (versi 23.11 atau lebih baru) ditambahkan ke proyek Anda
- Pemahaman dasar tentang sintaks Java

Anda tidak memerlukan pengalaman sebelumnya dengan API diagram; langkah-langkah di bawah ini mencakup semua mulai dari penyiapan proyek hingga output akhir.

## Langkah 1: Siapkan dependensi Maven

Tambahkan pustaka Aspose.Words ke `pom.xml` Anda. Dependensi tunggal ini memberi Anda akses ke `Document`, `DocumentBuilder`, dan kelas diagram.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Jika Anda menggunakan Gradle, yang setara adalah:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Gunakan versi stabil terbaru untuk mendapatkan perbaikan bug dan fitur diagram baru.

## Langkah 2: Buat dokumen baru dan builder

`Object` `Document` mewakili file Word, sementara `DocumentBuilder` memungkinkan Anda menyisipkan konten. Ini adalah dasar untuk **menambahkan diagram ke dokumen Word**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder kini siap menempatkan objek di mana saja dalam dokumen.

## Langkah 3: Sisipkan diagram pai

Aspose.Words mendukung beberapa jenis diagram; kami memilih `ChartType.PIE`. Ukuran dinyatakan dalam poin (1 poin = 1/72 inci).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Pada tahap ini diagram berisi seri data default dengan nilai placeholder. Anda dapat mengganti nilai tersebut nanti jika diperlukan.

## Langkah 4: Akses seri diagram

Diagram pai memiliki satu seri yang menyimpan nilai irisan. Ambil seri tersebut untuk menerapkan pemformatan.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Langkah 5: Pecah irisan pertama

Mengekspolir irisan menarik perhatian ke titik data tertentu. Ini adalah isyarat visual umum ketika Anda ingin menyoroti metrik utama.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Langkah 6: Tampilkan persentase pada setiap irisan

Menampilkan persentase langsung pada diagram meningkatkan pemahaman data. Ini memenuhi persyaratan **menampilkan persentase pada diagram pai**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Langkah 7: Tambahkan garis pemimpin untuk label yang lebih jelas

Garis pemimpin menghubungkan label irisan ke bagian yang bersesuaian, menghilangkan ambiguitas. Ini memenuhi **cara menambahkan garis pemimpin**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Langkah 8: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat memilih folder mana saja yang Anda memiliki akses menulis.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Menjalankan program akan membuat `output/PieFormatted.docx`. Buka file tersebut di Microsoft Word, dan Anda akan melihat diagram pai dimana:

- Irisan pertama terpecah.
- Setiap irisan menampilkan nilai persentasenya.
- Garis pemimpin menunjuk dari persentase ke irisan yang bersesuaian.

### Output yang diharapkan

![Diagram pai terformat di Word](/images/pie-formatted.png){: .center-image alt="Diagram pai terformat dimasukkan ke dalam dokumen Word"}

Tangkapan layar (teks alt menggunakan kata kunci utama) menggambarkan tampilan akhir: diagram pai yang bersih dan berbasis data siap untuk laporan, proposal, atau dasbor.

## Variasi umum dan kasus tepi

### Mengubah nilai irisan

Jika Anda memerlukan data khusus, ganti nilai seri default:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Beberapa seri (diagram donat)

Meskipun diagram pai sederhana memiliki satu seri, Aspose.Words juga mendukung diagram donat dengan beberapa seri. Ganti `ChartType.PIE` menjadi `ChartType.DONUT` dan ulangi langkah konfigurasi seri.

### Mengekspor ke PDF

Jika alur kerja Anda selanjutnya memerlukan PDF, panggil `doc.save("output/PieFormatted.pdf");` setelah diagram selesai dibangun. Tata letak visual tetap identik.

## Daftar sumber lengkap

Berikut adalah file Java lengkap yang dapat Anda salin‑tempel ke IDE Anda.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Kompilasi dan jalankan program dengan `mvn compile exec:java -Dexec.mainClass=PieChartExample` (atau perintah Gradle yang setara). File Word yang dihasilkan akan berisi diagram pai yang sepenuhnya diformat.

## Kesimpulan

Anda kini tahu **cara menyisipkan diagram pai** ke dalam dokumen Word menggunakan Java, cara **membuat diagram pai di Word**, cara **menampilkan persentase pada diagram pai**, dan cara **menambahkan diagram ke dokumen Word** dengan garis pemimpin. Contoh lengkap ini menunjukkan setiap langkah, menjelaskan mengapa kode ditulis demikian, dan memberikan tip untuk kustomisasi.

Selanjutnya, Anda mungkin ingin menjelajahi:

- Menambahkan label data dengan font khusus (variasi **menampilkan persentase pada diagram pai**)
- Menggabungkan beberapa diagram dalam satu dokumen (**menambahkan diagram ke dokumen Word** kasus penggunaan)
- Mengotomatiskan pembuatan laporan dengan tabel dan diagram bersama-sama

Silakan bereksperimen dengan warna, urutan irisan, atau mengekspor ke PDF. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Sembunyikan Sumbu Diagram dalam Dokumen Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Buat Diagram Garis di Word menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}