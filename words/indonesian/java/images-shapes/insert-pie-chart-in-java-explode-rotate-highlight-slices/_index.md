---
category: general
date: 2026-07-20
description: Masukkan diagram lingkaran di Java dengan panduan langkah demi langkah.
  Pelajari cara memisahkan irisan, cara memutar diagram lingkaran, menyorot irisan
  diagram lingkaran, dan menyesuaikan irisan diagram lingkaran.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: id
lastmod: 2026-07-20
og_description: Masukkan diagram lingkaran di Java dan kuasai cara memisahkan irisan,
  memutar diagram lingkaran, menyorot irisan diagram, serta menyesuaikan irisan diagram
  lingkaran untuk laporan visual yang halus.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Masukkan Diagram Lingkaran di Java – Pecah, Putar & Sorot
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Sisipkan Diagram Lingkaran di Java – Pecah, Putar & Sorot Irisan
url: /id/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Diagram Pai di Java – Meledakkan, Memutar & Menyorot Irisan

Pernahkah Anda perlu **insert pie chart** dalam laporan Java tetapi tidak yakin bagaimana membuat satu irisan menonjol? Anda bukan satu-satunya. Baik Anda sedang membangun dasbor, menghasilkan faktur, atau sekadar memvisualisasikan hasil survei, diagram pai yang bergaya dengan baik dapat mengubah angka mentah menjadi wawasan yang langsung dapat dipahami.

Dalam tutorial ini Anda akan melihat contoh lengkap yang siap dijalankan yang menunjukkan cara menyisipkan diagram pai, **how to explode slice**, **how to rotate pie chart**, dan bahkan **highlight pie chart slice** dengan warna khusus. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali yang dapat Anda sisipkan ke proyek Java mana pun yang menggunakan pustaka *JFreeChart* yang populer (atau API serupa apa pun).

## Prasyarat

- Java 17 atau lebih baru (kode dapat dikompilasi dengan versi lebih lama, tetapi kami akan menggunakan sintaks `var` modern untuk singkatnya).  
- Maven atau Gradle untuk mengambil dependensi `org.jfree:jfreechart`.  
- Pemahaman dasar tentang kelas Java dan konsep pembuat diagram.  

Jika Anda belum pernah menambahkan pustaka ke proyek Maven, cukup masukkan ini ke dalam `pom.xml` Anda:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Itu saja—tidak ada pengaturan tambahan yang diperlukan.

## Langkah 1: Sisipkan Diagram Pai – Buat Builder dan Objek Chart

Hal pertama yang perlu dilakukan: kita membutuhkan sebuah *builder* (anggaplah sebagai pabrik) yang tahu cara menghasilkan diagram. Di JFreeChart, `ChartFactory` melakukan pekerjaan berat.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Mengapa kita memulai dengan dataset? Karena diagram itu sendiri hanyalah pembungkus visual di sekitar angka. Dengan **inserting pie chart** di sini kita sudah memiliki kanvas 400 × 300 (ukuran akan diterapkan nanti saat kita merendernya menjadi gambar).

## Langkah 2: How to Explode Slice – Tekankan Segmen Pertama

Sekarang diagram sudah ada, mari buat irisan pertama menonjol. Meledakkan sebuah irisan membuatnya sedikit terpisah dari lingkaran, menarik perhatian pembaca.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Perhatikan kami menggunakan frasa **how to explode slice** dalam nama metode; itu membuat maksudnya sangat jelas. Metode `setExplodePercent` menerima sebuah kunci (label irisan) dan persentase, sehingga Anda dapat menyesuaikan jarak “pop‑out” sesuai kebutuhan.

## Langkah 3: How to Rotate Pie Chart – Ubah Sudut Awal

Diagram pai default dimulai pada posisi jam 12. Terkadang Anda ingin irisan pertama dimulai di tempat lain—mungkin untuk disesuaikan dengan mock‑up desain atau agar cocok dengan diagram lain.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Memanggil `rotateChart(chart, 45)` memutar seluruh pai sehingga irisan “Apples” dimulai pada sudut 45 derajat, persis seperti yang diminta oleh persyaratan **how to rotate pie chart**.

## Langkah 4: Highlight Pie Chart Slice – Warna dan Label Kustom

Selain meledakkan, Anda mungkin ingin memberi sebuah irisan warna unik atau label tebal untuk benar‑benar **highlight pie chart slice**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Di sini kami **customize pie chart slice** dengan mengubah cat dan gaya labelnya. Silakan mengganti warna atau font agar sesuai dengan palet merek Anda.

## Langkah 5: Render Diagram ke Gambar (Opsional tapi Berguna)

Sebagian besar aplikasi dunia nyata membutuhkan diagram sebagai PNG, JPEG, atau bahkan PDF. Di bawah ini cara cepat menulis diagram ke sebuah file.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Menjalankan alur lengkap akan menghasilkan PNG 400 × 300 yang terlihat seperti ini:

![Insert pie chart example](image.png){: alt="Contoh diagram pai yang menampilkan irisan yang meledak dan diputar"}

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut adalah metode `main` yang dapat Anda salin‑tempel ke kelas Java baru dan jalankan:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Output yang Diharapkan

Menjalankan program akan membuat file bernama **fruit-pie.png**. Buka file tersebut dan Anda akan melihat:

- Diagram pai 400 × 300 dengan judul “Fruit Distribution”.  
- Irisan “Apples” meledak keluar sebesar 15 %.  
- Seluruh diagram diputar sehingga “Apples” mulai pada posisi 45 derajat.  
- Irisan yang meledak

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Sisipkan Diagram Sebar](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Sisipkan Diagram Area](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}