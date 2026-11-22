---
category: general
date: 2026-11-22
description: Buat diagram lingkaran di Java dan pelajari cara mengatur ukuran diagram,
  menambahkan label data, menampilkan persentase, serta memutar irisan pertama untuk
  dampak visual yang jelas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: id
lastmod: 2026-11-22
og_description: Buat diagram lingkaran di Java, lalu atur ukuran diagram, tampilkan
  persentase pada label data, dan putar irisan pertama—semua dalam satu contoh yang
  dapat dijalankan.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Buat diagram lingkaran dengan ukuran khusus, label, dan rotasi di Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Buat diagram lingkaran dengan ukuran khusus, label data, dan rotasi di Java
url: /id/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat diagram lingkaran dengan ukuran khusus, label data, dan rotasi di Java

Jika Anda perlu **create pie chart** di Java, panduan ini akan membawa Anda melalui seluruh proses. Anda akan belajar cara **set chart size**, mengaktifkan **show percentages pie chart**, menambahkan **data labels pie chart**, dan **rotate pie chart slice** sehingga irisan pertama dimulai pada sudut 45‑derajat.

Contoh ini menggunakan **Aspose.Slides for Java**, sebuah perpustakaan yang banyak digunakan untuk memanipulasi file PowerPoint. Konsep yang sama berlaku untuk perpustakaan charting lainnya; cukup ganti panggilan API dengan yang setara dalam toolkit Anda.

## Prasyarat

* Java 17 atau lebih baru terpasang  
* Maven 3.8+ (atau Gradle) untuk manajemen dependensi  
* Pemahaman dasar tentang sintaks Java  
* Akses ke binary Aspose.Slides for Java (Anda dapat memperoleh trial gratis dari situs resmi)

Tambahkan dependensi ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Buat diagram lingkaran – contoh lengkap

Program berikut membuat slide PowerPoint yang berisi diagram lingkaran dengan ukuran khusus, label data persentase, dan irisan pertama yang diputar.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Mengapa setiap langkah penting

| Langkah | Tujuan | Bagaimana kaitannya dengan kata kunci |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – objek inti yang akan merender visual. | Secara langsung memenuhi kebutuhan *create pie chart*. |
| **Set dimensions** | Pemanggilan `addChart(..., 400, 300)` menunjukkan **set chart size**. | Mengontrol lebar (400 px) dan tinggi (300 px). |
| **Show percentages** | `setShowPercentage(true)` membuat diagram **show percentages pie chart** pada setiap irisan. | Pengguna sering membutuhkan persentase alih-alih nilai mentah. |
| **Add data labels** | Konfigurasi `DataLabelFormat` menambahkan **data labels pie chart** dengan visibilitas yang diinginkan. | Label meningkatkan keterbacaan dan dapat disesuaikan. |
| **Rotate slice** | `setFirstSliceAngle(45)` memutar diagram sehingga irisan pertama dimulai pada sudut 45‑derajat, memenuhi **rotate pie chart slice**. | Meningkatkan penekanan visual pada irisan tertentu. |

## Penjabaran langkah‑demi‑langkah

### 1. Sisipkan diagram lingkaran dan set chart size

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Metode `addChart` membuat diagram dan secara bersamaan **set chart size** menjadi 400 × 300 poin.*  
Jika Anda memerlukan ukuran berbeda, sesuaikan dua argumen terakhir.

### 2. Isi diagram dengan data

Demo ini menambahkan tiga kategori dan satu seri. Ganti angka yang di‑hard‑code dengan data dari basis data, CSV, atau input pengguna sesuai kebutuhan.

### 3. Tampilkan persentase pada setiap irisan

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Mengaktifkan `setShowPercentage(true)` memastikan diagram **show percentages pie chart** secara otomatis menghitung bagian masing‑masing irisan dari total.*

### 4. Tambahkan label data terperinci

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Anda dapat mengubah opsi label lain (`setShowValue`, `setShowSeriesName`, dll.) untuk menyesuaikan pengalaman **add data labels pie chart**.

### 5. Putar irisan pertama

```java
chart.setFirstSliceAngle(45);
```

*Memanggil `setFirstSliceAngle(45)` **rotate pie chart slice** sehingga segmen pertama dimulai pada sudut 45‑derajat, membuatnya menonjol.*

### 6. Simpan dan lihat hasilnya

Menjalankan program menghasilkan `output/PieChartDemo.pptx`. Buka file tersebut di PowerPoint atau penampil kompatibel lainnya untuk melihat diagram lingkaran akhir:

![Contoh membuat diagram lingkaran](images/pie_chart_example.png){.align-center alt="Tangkapan layar diagram lingkaran yang dibuat dengan ukuran khusus, label persentase, dan irisan pertama yang diputar"}

Gambar di atas menunjukkan hasil **create pie chart**, mengonfirmasi bahwa ukuran, label, persentase, dan rotasi diterapkan dengan benar.

## Variasi umum dan kasus tepi

| Situasi | Penyesuaian |
|-----------|------------|
| **Different chart dimensions** | Ubah parameter lebar/tinggi pada `addChart`. |
| **Multiple series** | Tambahkan objek `IChartSeries` tambahan; setiap seri dapat memiliki pengaturan labelnya masing‑masing. |
| **Custom label format** | Gunakan `series.getDataLabelFormat().setNumberFormat("0.0%")` untuk mengontrol tempat desimal. |
| **Rotating to another angle** | Berikan integer apa pun (0‑360) ke `setFirstSliceAngle`. |
| **Export as image** | Setelah menyimpan, panggil `chart.writeAsSvg(outPath)` atau `chart.writeAsPng(outPath)` untuk versi raster. |

> **Pro tip:** Jika Anda berencana menghasilkan banyak diagram dalam loop, gunakan kembali objek `Presentation` yang sama dan hanya ganti data diagram. Ini mengurangi beban memori dan mempercepat pemrosesan.

## Kesimpulan

Anda kini tahu cara **create pie chart** di Java, **set chart size**, mengaktifkan **show percentages pie chart**, **add data labels pie chart**, dan **rotate pie chart slice** untuk penekanan visual yang lebih baik. Contoh lengkap yang dapat dijalankan memperlihatkan setiap langkah mulai dari inisialisasi hingga menyimpan file PowerPoint akhir.

### Apa selanjutnya?

* Jelajahi tipe diagram lain (Bar, Line, Area) menggunakan enum `ChartType` yang sama.  
* Gabungkan beberapa diagram dalam satu slide untuk dasbor.  
* Ekspor diagram ke PNG atau SVG untuk digunakan dalam aplikasi web.  

Silakan bereksperimen dengan warna, legenda, dan efek animasi—visualisasi data Anda hanya dibatasi oleh imajinasi. Selamat membuat diagram!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [cara menyisipkan diagram lingkaran di Word – tambahkan label data persen](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Cara meledakkan irisan diagram lingkaran di Java – tutorial chart Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Sisipkan Diagram Lingkaran di Java – Meledakkan, Memutar & Menyorot Irisan](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}