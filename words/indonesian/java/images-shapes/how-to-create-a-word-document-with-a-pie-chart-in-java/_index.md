---
category: general
date: 2026-09-18
description: Pelajari cara membuat dokumen Word dan menyisipkan diagram lingkaran
  menggunakan Aspose.Words untuk Java. Termasuk langkah‑langkah memutar diagram lingkaran
  dan menghasilkan file Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: id
lastmod: 2026-09-18
og_description: Buat dokumen Word dan sisipkan diagram lingkaran menggunakan Java.
  Ikuti panduan ini untuk memutar diagram lingkaran, memisahkan irisan, dan menghasilkan
  file Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Buat dokumen Word dengan diagram lingkaran – panduan Java langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cara membuat dokumen Word dengan diagram lingkaran di Java
url: /id/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word dengan diagram lingkaran di Java

Jika Anda perlu **membuat dokumen Word** yang memvisualisasikan data, panduan ini menunjukkan cara melakukannya dengan Aspose.Words for Java. Anda akan belajar cara menyisipkan diagram lingkaran, meledakkan satu irisan, memutar diagram, dan akhirnya **menghasilkan file Word** yang dapat Anda buka di Microsoft Word.

Membangun laporan yang menggabungkan teks dan diagram tidak memerlukan alat grafis terpisah. Pada akhir tutorial ini Anda akan memiliki program lengkap yang dapat dijalankan dan menghasilkan file .docx berisi diagram lingkaran yang telah dikonfigurasi sepenuhnya.

## Prasyarat

- Java 17 atau lebih baru (kode juga dapat dikompilasi dengan Java 8+)
- Maven atau Gradle untuk manajemen dependensi
- Lisensi Aspose.Words for Java (versi percobaan gratis cukup untuk contoh ini)
- Familiaritas dasar dengan sintaks Java

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven baru dan tambahkan dependensi Aspose.Words ke `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Pastikan nomor versi selalu terbaru; rilis yang lebih baru menambahkan perbaikan tipe diagram dan perbaikan bug.

## Langkah 2: Buat dokumen Word baru

Operasi pertama saat Anda **membuat dokumen Word** secara programatik adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file .docx di memori.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Kelas `Document` adalah titik masuk untuk semua fitur pengolahan Word. Pada tahap ini tidak ada file yang ditulis ke disk; semuanya terjadi di RAM sampai Anda memanggil `save`.

## Langkah 3: Cara menyisipkan diagram lingkaran

`DocumentBuilder` memungkinkan Anda menambahkan konten ke dokumen. Dengan `insertChart` Anda dapat **menyisipkan objek diagram lingkaran** secara langsung.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` memberi tahu Aspose.Words untuk membuat diagram lingkaran. Dimensi dinyatakan dalam poin (1 pt ≈ 1/72 in). Setelah pemanggilan ini diagram muncul pada paragraf baru.

## Langkah 4: Isi diagram dengan data

Diagram lingkaran memerlukan serangkaian nilai. Di sini kami menambahkan tiga kategori: “Apples”, “Bananas”, dan “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Metode `add` membangun seri dan secara otomatis membuat entri legenda. Anda dapat menggunakan pola ini untuk dataset numerik apa pun.

## Langkah 5: Tekankan irisan pertama

Melelehkan (explode) sebuah irisan menarik perhatian ke nilai tertentu. Irisan pertama (indeks 0) dilelehkan sebesar 20 poin.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Menetapkan `explode` pada seri memengaruhi seluruh diagram, sehingga hanya titik data pertama yang dipindahkan.

## Langkah 6: Cara memutar diagram lingkaran

Memutar diagram meningkatkan keseimbangan visual, terutama ketika irisan terbesar tidak berada di bagian atas. Metode `setRotationAngle` menerima nilai dalam derajat.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Rotasi 45° menggeser sudut mulai searah jarum jam, membuat diagram lebih mudah dibaca dalam banyak tata letak.

## Langkah 7: Simpan dokumen dan hasilkan file Word

Akhirnya, tulis dokumen ke disk. Langkah ini **menghasilkan file Word** yang dapat dibuka dengan Microsoft Word, LibreOffice, atau penampil kompatibel lainnya.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Metode `save` secara otomatis mendeteksi ekstensi .docx dan menulis paket yang kompatibel dengan Word. Folder `output` harus ada atau Anda dapat membuatnya secara programatik.

### Output yang diharapkan

Setelah menjalankan program, buka `output/PieChart.docx`. Anda akan melihat:

- Satu halaman yang berisi diagram lingkaran berukuran 400 × 300 pt.
- Irisan “Apples” dilelehkan ke luar sebesar 20 pt.
- Seluruh diagram diputar 45° searah jarum jam.
- Legenda yang mencocokkan tiga kategori buah.

## Variasi umum dan kasus tepi

### Menyisipkan beberapa diagram

Jika Anda memerlukan lebih dari satu diagram, panggil `builder.insertChart` lagi setelah memindahkan kursor:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Mengubah warna diagram

Anda dapat menyesuaikan warna irisan melalui koleksi `getPoints()` pada seri:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Menangani dataset besar

Untuk dataset dengan lebih dari 10 irisan, pertimbangkan menggunakan diagram donat (`ChartType.DOUGHNUT`) agar visual tetap jelas.

## Kesimpulan

Sekarang Anda tahu cara **membuat dokumen Word**, **menyisipkan diagram lingkaran**, **memutar diagram lingkaran**, dan **menghasilkan file Word** menggunakan Aspose.Words for Java. Solusi lengkap ini menunjukkan alur kerja penuh mulai dari inisialisasi dokumen hingga output file akhir, mencakup baik “cara” maupun “mengapa” di setiap langkah.

Selanjutnya, jelajahi topik terkait seperti **cara membuat data diagram lingkaran** dari basis data, menambahkan label data, atau mengekspor diagram sebagai gambar. Bereksperimenlah dengan tipe diagram lain (batang, garis, donat) untuk memperluas toolkit otomatisasi Word Anda.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}