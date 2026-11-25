---
category: general
date: 2026-11-25
description: Pelajari cara membuat diagram lingkaran di Java, menyisipkan diagram
  lingkaran ke dalam dokumen Word, memisahkan irisan diagram, dan mengubah orientasi
  diagram dengan contoh kode yang jelas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: id
lastmod: 2026-11-25
og_description: Buat diagram lingkaran di Java, sisipkan diagram lingkaran ke dalam
  dokumen, pecah irisan diagram, dan ubah orientasi diagram dengan kode langkah demi
  langkah.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Buat diagram lingkaran di Java – sisipkan, pecah irisan, dan putar
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Cara membuat diagram lingkaran, menyisipkannya, dan menyesuaikan orientasi
  di Java
url: /id/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram pai, menyisipkannya, dan menyesuaikan orientasi di Java

Jika Anda perlu **membuat diagram pai** di dalam dokumen Word, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara **menyisipkan diagram pai**, meledakkan sebuah irisan untuk penekanan, dan **mengubah orientasi diagram** dengan rotasi sederhana.

Tutorial ini mencakup semua yang Anda perlukan—dari menyiapkan pustaka Aspose.Words for Java hingga menghasilkan file `.docx` akhir yang menampilkan diagram pai yang diputar dan meledak. Tidak diperlukan dokumentasi eksternal; cukup ikuti langkah-langkah dan jalankan kode.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.
* Maven atau Gradle untuk mengelola dependensi.
* Lisensi Aspose.Words for Java yang valid (atau gunakan mode evaluasi gratis).

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Contoh untuk Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Jaga versi pustaka tetap terbaru; rilis terbaru (24.10 pada saat penulisan) mencakup perbaikan bug untuk rendering diagram.

## Langkah 1: Membuat diagram pai dan menyisipkannya ke dalam dokumen

Langkah pertama adalah **membuat objek diagram pai** dan menyematkannya dalam file Word. Kode di bawah ini membuat dokumen sederhana, menambahkan placeholder diagram, dan menyisipkan diagram pai berukuran 400 × 300 piksel.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Mengapa ini penting:** `builder.insertChart` membuat placeholder diagram yang secara otomatis dikonversi Aspose.Words menjadi diagram OOXML saat dokumen disimpan. Argumen `ChartType.PIE` memberi tahu pustaka untuk merender diagram pai, memenuhi persyaratan **menyisipkan diagram pai**.

## Langkah 2: Meledakkan irisan diagram pai untuk menyorot segmen

Meledakkan sebuah irisan menarik perhatian ke titik data tertentu. Baris berikut meledakkan irisan pertama (indeks 0) sebesar 10 poin:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Anda dapat mengubah indeks untuk menargetkan irisan lain, atau menyesuaikan jarak ledakan untuk efek yang lebih halus. Meledakkan irisan adalah cara standar untuk **meledakkan irisan diagram pai** di Aspose.Words.

## Langkah 3: Mengubah orientasi diagram dengan memutarnya

Memutar diagram memberikan perspektif visual yang segar. Gunakan `setRotationAngle` untuk memutar seluruh diagram searah jarum jam (sudut diukur dalam derajat).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Pemanggilan di atas memenuhi persyaratan **memutar diagram pai** dan **mengubah orientasi diagram**. Semua sudut antara 0 dan 360 derajat diterima.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua, berikut adalah program lengkap yang berdiri sendiri yang membuat diagram pai, meledakkan sebuah irisan, dan memutar diagram. Jalankan dari IDE Anda atau dari baris perintah dengan `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Output yang diharapkan

* Sebuah file bernama **CreatePieChartDemo.docx** muncul di direktori kerja.
* Membuka file tersebut di Microsoft Word menampilkan diagram pai 400 × 300 piksel.
* Irisan pertama (Q1) dipindahkan ke luar sebesar 10 poin, menghasilkan efek **meledakkan irisan diagram pai**.
* Seluruh diagram dimiringkan 45 derajat, menunjukkan **mengubah orientasi diagram** dan **memutar diagram pai**.

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|-----------------------|
| **Ukuran diagram berbeda** | Ubah argumen `400, 300` pada `insertChart`. |
| **Beberapa seri** | Tambahkan lebih banyak objek `ChartSeries` ke `chart.getSeries()`. |
| **Meledakkan irisan lain** | Gunakan `setExplode(sliceIndex, distance)` dengan `sliceIndex` yang diinginkan. |
| **Tidak perlu rotasi** | Hilangkan pemanggilan `setRotationAngle` atau setel sudut menjadi `0`. |
| **Ekspor ke PDF alih-alih DOCX** | Setelah membangun dokumen, panggil `doc.save("output.pdf")` dengan format PDF. |

> **Waspada:** Menggunakan jarak ledakan negatif akan memunculkan `IllegalArgumentException`. Selalu berikan nilai non‑negatif.

## Tips kinerja

Jika Anda menghasilkan banyak diagram dalam sebuah loop, gunakan kembali satu `DocumentBuilder` dan hanya panggil `insertChart` untuk setiap iterasi. Ini mengurangi beban memori dan mempercepat pemrosesan.

## Kesimpulan

Anda kini tahu cara **membuat diagram pai**, **menyisipkan diagram pai**, **meledakkan irisan diagram pai**, dan **memutar diagram pai** menggunakan Aspose.Words for Java. Contoh lengkap menunjukkan alur kerja penuh—dari menginisialisasi dokumen hingga menyimpan file yang memvisualisasikan diagram pai yang diputar dan meledak.

Selanjutnya, Anda dapat menjelajahi **mengubah orientasi diagram** lebih lanjut dengan menerapkan efek 3‑D, atau bereksperimen dengan tipe diagram lain seperti **Bar** atau **Line**. Pola API yang sama berlaku, sehingga memperluas tutorial ini menjadi mudah.

Silakan ubah data, indeks irisan, atau sudut rotasi untuk menyesuaikan kebutuhan pelaporan Anda, dan bagikan hasil Anda dengan komunitas!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyisipkan diagram pai ke dalam dokumen Word menggunakan Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Cara meledakkan irisan diagram pai di Java – tutorial chart Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}