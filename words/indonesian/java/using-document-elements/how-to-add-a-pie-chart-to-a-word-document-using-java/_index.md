---
category: general
date: 2026-11-15
description: Pelajari cara menambahkan diagram lingkaran ke dokumen Word dengan Aspose.Words
  for Java. Termasuk konversi donat, irisan meledak, dan contoh kode lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: id
lastmod: 2026-11-15
og_description: Tambahkan diagram lingkaran ke dokumen Word menggunakan Aspose.Words
  for Java. Tutorial ini menunjukkan cara meledakkan irisan dan mengubah diagram menjadi
  donat.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Tambahkan diagram lingkaran ke dokumen Word dengan Java – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cara menambahkan diagram lingkaran ke dokumen Word menggunakan Java
url: /id/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan diagram lingkaran ke dokumen Word – panduan lengkap Java

Jika Anda perlu **menambahkan diagram lingkaran ke dokumen Word** secara programatis, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk Java. Anda akan melihat alur kerja lengkap: memuat DOCX, membuat diagram lingkaran, meledakkan irisan pertama, dan mengubah diagram menjadi donat dengan mengatur ukuran lubang.

Panduan ini juga mencakup variasi umum—seperti menambahkan beberapa seri, menyesuaikan warna, dan menangani dokumen yang sudah berisi diagram—sehingga Anda dapat menyesuaikan kode untuk proyek dunia nyata seperti pelaporan otomatis atau presentasi dinamis.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 atau lebih baru (kode dapat dikompilasi dengan JDK 11+ juga)
* Maven 3.6+ atau Gradle untuk manajemen dependensi
* Lisensi Aspose.Words untuk Java (versi percobaan gratis dapat digunakan untuk pengujian)
* Pemahaman dasar tentang sintaks Java dan struktur proyek Maven

## Langkah 1: Siapkan proyek Maven dan impor Aspose.Words

Buat proyek Maven baru (atau tambahkan ke proyek yang sudah ada) dan sertakan dependensi Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Jika Anda menggunakan Gradle, entri yang setara adalah `implementation 'com.aspose:aspose-words:24.9'`.

Dependensi ini membawa kelas `Document`, `Chart`, dan `ChartType` yang Anda perlukan untuk memanipulasi diagram.

## Langkah 2: Muat dokumen target

Anda dapat memulai dari file `.docx` yang sudah ada atau membuat dokumen kosong baru. Contoh di bawah memuat templat bernama `input.docx` yang berada di folder `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Jika file tidak ada, Aspose.Words akan secara otomatis membuat dokumen kosong baru ketika Anda memanggil `new Document()` tanpa nama file.

## Langkah 3: Buat diagram lingkaran dan sisipkan ke dalam dokumen

Aspose.Words memperlakukan diagram sebagai bentuk yang dapat ditempatkan di mana saja paragraf dapat muncul. Kode berikut membuat **diagram lingkaran**, menambahkan satu seri data, dan menyisipkan diagram setelah paragraf pertama.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Mengapa langkah ini penting:**  
* `ChartType.PIE` memberi tahu Aspose.Words untuk merender diagram lingkaran tradisional.  
* Menambahkan seri dengan label kategori dan nilai numerik secara otomatis mengisi irisan.  
* Menyisipkan diagram sebagai anak dari `Paragraph` menjaga alur dokumen tetap utuh.

## Langkah 4: Meledakkan irisan pertama untuk menyorotnya

*Irisan yang meledak* menarik perhatian ke titik data tertentu. API menyediakan `setExplode(boolean)` pada objek `ChartSeries`. Menetapkannya pada seri pertama (indeks 0) membuat irisan pertama menonjol.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Pertanyaan umum:** *Bagaimana jika saya memiliki beberapa seri?*  
> Anda dapat menargetkan seri tertentu berdasarkan indeksnya, misalnya `pieChart.getSeries().get(1).setExplode(true)` untuk seri kedua.

## Langkah 5: Ubah diagram lingkaran menjadi donat dengan mengatur ukuran lubang

Diagram donat pada dasarnya adalah diagram lingkaran dengan pusat yang berlubang. Aspose.Words memungkinkan Anda mendefinisikan ukuran lubang sebagai persentase dari radius diagram.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Metode `setHoleSize` menerima nilai dari **0** (lingkaran biasa) hingga **100** (sepenuhnya kosong). Nilai sekitar **30‑40** menghasilkan donat yang seimbang secara visual.

## Langkah 6: Simpan dan verifikasi hasilnya

Setelah semua modifikasi, simpan dokumen. Baris berikut menulis file ke folder `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Output yang diharapkan

Buka `final-pie-doughnut.docx` di Microsoft Word:

* Diagram donat muncul di tempat paragraf pertama berada.  
* Irisan “Apples” meledak (sedikit terpisah dari yang lain).  
* Diagram menampilkan empat irisan berlabel *Apples*, *Bananas*, *Cherries*, *Dates* dengan persentase yang Anda berikan.

Jika Anda lebih suka output PDF, ubah `SaveFormat` menjadi `SaveFormat.PDF`.

## Menangani kasus tepi dan variasi

### Menambahkan beberapa seri

Jika Anda memerlukan beberapa seri (misalnya donat bertumpuk), tambahkan secara berurutan:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Warna khusus

Anda dapat menetapkan warna untuk setiap irisan melalui `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Bekerja dengan diagram yang sudah ada

Jika dokumen sudah berisi diagram dan Anda hanya ingin memodifikasinya, temukan bentuk diagram:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Penanganan lisensi

Aspose.Words memerlukan lisensi untuk penggunaan produksi. Letakkan file `Aspose.Words.lic` Anda di classpath dan muat pada saat aplikasi dimulai:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Jika lisensi tidak disetel, akan ditambahkan watermark pada dokumen yang dihasilkan.

## Contoh lengkap yang dapat dijalankan

Berikut adalah kelas Java lengkap yang menggabungkan semua langkah yang dibahas. Salin ke `src/main/java/com/example/AddPieChart.java` dan jalankan `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Menjalankan program menghasilkan diagram donat seperti yang dijelaskan sebelumnya. Sesuaikan `categories`, `values`, atau `holeSize` sesuai data Anda.

## Kesimpulan

Anda kini tahu cara **menambahkan diagram lingkaran ke dokumen Word** menggunakan Java dan Aspose.Words. Tutorial ini mencakup memuat dokumen, membuat diagram lingkaran, meledakkan irisan, mengubah diagram menjadi donat, serta menangani variasi umum seperti beberapa seri, warna khusus, dan diagram yang sudah ada. Dengan fondasi ini Anda dapat membangun alat pelaporan otomatis, menghasilkan presentasi dinamis, atau menyematkan visualisasi kaya langsung ke file Word.

### Apa yang dapat Anda jelajahi selanjutnya

* **menambahkan diagram batang ke dokumen Word** – langkah serupa tetapi gunakan `ChartType.BAR`.  
* **menyesuaikan legenda dan judul diagram** – gunakan `pieChart.getTitle().setText("...")` dan `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **mengekspor dokumen Word sebagai PDF** – ubah `SaveFormat` menjadi `PDF` untuk file siap distribusi.  
* **mengisi data diagram dari basis data** – gantikan array statis dengan hasil kueri JDBC.

Silakan bereksperimen dengan berbagai tipe diagram, sumber data, dan opsi styling. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}