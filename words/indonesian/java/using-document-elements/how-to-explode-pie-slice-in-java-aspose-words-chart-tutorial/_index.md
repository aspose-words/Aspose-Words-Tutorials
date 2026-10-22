---
category: general
date: 2026-08-07
description: Cara meledakkan irisan pai di Java menggunakan Aspose.Words. Pelajari
  cara menambahkan garis pemimpin ke pai, membuat diagram Word, dan menyesuaikan irisan
  diagram pai.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: id
lastmod: 2026-08-07
og_description: Cara memisahkan irisan pai di Java dengan Aspose.Words. Panduan ini
  menunjukkan cara menambahkan garis penunjuk ke pai, membuat diagram Word, dan menyesuaikan
  irisan diagram pai untuk dampak visual yang jelas.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Cara memisahkan irisan pai di Java – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Cara memisahkan irisan pai di Java – Tutorial diagram Aspose.Words
url: /id/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara meledakkan irisan pai di Java – Tutorial diagram Aspose.Words

Jika Anda perlu mengetahui **cara meledakkan irisan pai** dalam dokumen Word menggunakan Java, tutorial ini akan membantu Anda. Kami juga akan menunjukkan **cara menambahkan garis pemimpin ke diagram pai**, **java create word chart** objects, dan **menyesuaikan irisan diagram pai** untuk hasil yang halus. Pada akhir panduan ini Anda akan memiliki contoh lengkap yang dapat dijalankan dan dapat langsung dimasukkan ke proyek Java mana pun.

![Cara meledakkan irisan pai di Java – Diagram Aspose.Words](/images/pie-chart-exploded.png)

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java Development Kit (JDK) 8 atau lebih tinggi.
* Maven atau Gradle untuk manajemen dependensi.
* Lisensi Aspose.Words untuk Java (evaluasi gratis dapat digunakan untuk tujuan pembelajaran).
* Familiaritas dasar dengan sintaks Java dan konsep berorientasi objek.

> **Pro tip:** Meskipun Aspose.Words menawarkan percobaan gratis, membeli lisensi menghilangkan watermark evaluasi dari dokumen yang dihasilkan.

## Apa yang dibahas dalam tutorial ini

* Membuat dokumen Word baru dari awal.  
* Menyisipkan **pie chart** menggunakan `DocumentBuilder`.  
* **Meledakkan irisan pai** untuk menyoroti titik data.  
* **Menambahkan garis pemimpin ke pai** untuk pelabelan yang lebih jelas.  
* Menyesuaikan tampilan irisan, seperti warna dan batas.  
* Menyimpan dokumen ke disk dan memverifikasi hasilnya.

---

## Cara meledakkan irisan pai dengan Aspose.Words di Java

Langkah pertama adalah menyiapkan objek diagram dan meledakkan irisan yang diinginkan. Aspose.Words menampilkan diagram melalui kelas `Shape`, dan setiap irisan adalah `ChartPoint`. Dengan mengatur properti `Explosion` Anda mengontrol seberapa jauh irisan bergerak ke luar.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Mengapa ini berhasil:**  
`setExplosion(20)` memberi tahu mesin diagram untuk menggeser irisan sebesar 20 poin dari pusat diagram. Nilainya bersifat relatif; angka yang lebih besar menghasilkan efek yang lebih dramatis. Anda dapat meledakkan irisan mana pun dengan mengubah indeks (`get(1)`, `get(2)`, …).

## Tambahkan garis pemimpin ke pai untuk label yang lebih jelas

Garis pemimpin menghubungkan label irisan ke tepinya, yang sangat berguna ketika irisan meledak atau ketika diagram berisi banyak bagian kecil. Pemanggilan `setLeaderLines(true)` mengaktifkan fitur ini untuk seluruh seri.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Mengapa Anda membutuhkan garis pemimpin:**  
Ketika sebuah irisan meledak, label default dapat tumpang tindih dengan elemen lain. Garis pemimpin menjaga label tetap terbaca dengan menggambar garis pendek dari irisan ke kotak teks.

## Java create Word chart – menyisipkan seri data

Diagram tanpa data tidak terlalu berguna. Anda harus mengisi seri dengan kategori dan nilai. Di bawah ini kami menambahkan tiga kategori yang mewakili pangsa pasar.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Penjelasan:**  
`ChartSeries` menyimpan baik kategori (nama irisan) maupun nilai numerik. Mengaktifkan `ShowCategoryName` dan `ShowPercentage` membuat diagram menjadi mandiri, yang cocok dengan garis pemimpin yang kami tambahkan sebelumnya.

## Sesuaikan irisan diagram pai selain meledakkan

Selain meledakkan irisan, Anda sering ingin menyesuaikan warna, batas, atau bahkan menyembunyikan irisan sepenuhnya. Potongan kode berikut menunjukkan tiga penyesuaian umum:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Mengapa menyesuaikan irisan:**  
Warna khusus membuat diagram selaras dengan merek perusahaan, sementara batas meningkatkan keterbacaan pada halaman cetak. Menyembunyikan irisan berguna ketika Anda ingin mempertahankan model data tetap utuh tetapi sementara menghilangkan kategori dari output visual.

## Simpan dokumen dan verifikasi hasilnya

Akhirnya, tulis dokumen ke disk. Anda dapat membuka file `.docx` yang dihasilkan di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung format tersebut.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Output yang diharapkan:**  
Saat Anda membuka `PieChartDemo.docx`, Anda akan melihat diagram pai di mana irisan pertama (Product A) meledak ke luar, garis pemimpin menunjuk dari setiap irisan ke labelnya, dan irisan muncul dengan warna hijau, biru, dan oranye khusus. Irisan yang disembunyikan (Product C) tidak akan terlihat, tetapi persentase tetap menjumlah 100 % karena data tetap ada dalam seri diagram.

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan setelah menambahkan dependensi Aspose.Words ke proyek Anda.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependensi (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cara Memuat Dokumen Word dengan Aspose.Words Java: Panduan Komprehensif](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}