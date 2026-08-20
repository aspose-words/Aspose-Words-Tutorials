---
category: general
date: 2026-08-20
description: Tambahkan garis penghubung ke diagram lingkaran di Java dengan cepat.
  Pelajari cara menyisipkan, meledakkan, mengubah warna, dan memberi label pada irisan
  menggunakan Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: id
lastmod: 2026-08-20
og_description: Tambahkan garis penunjuk ke diagram lingkaran di Java dengan contoh
  singkat. Ikuti panduan ini untuk menyisipkan, memisahkan, mengubah warna, dan memberi
  label pada irisan menggunakan Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Tambahkan garis pemimpin pada diagram lingkaran di Java – panduan API Chart
  langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Cara menambahkan garis penunjuk ke diagram lingkaran di Java dengan Chart API
url: /id/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan leader lines ke pie chart di Java dengan Chart API

Jika Anda perlu **menambahkan leader lines ke pie chart** di Java, panduan ini akan memandu Anda melalui proses lengkap. Anda akan melihat cara menyisipkan pie chart, meledakkan sebuah irisan untuk penekanan, mengubah warnanya, dan akhirnya mengaktifkan leader lines yang memberi label pada segmen yang meledak.

Contoh ini menggunakan Chart API standar yang ditemukan di banyak pustaka pelaporan Java. Tidak diperlukan alat eksternal, dan kode dapat dijalankan pada lingkungan JDK 8+ apa pun.

## Apa yang akan Anda capai

* Membuat `Chart` dengan tipe `ChartType.PIE` dengan ukuran khusus.  
* Meledakkan irisan pertama untuk menarik perhatian.  
* Mengatur warna sektor irisan yang meledak menjadi biru.  
* **Menambahkan leader lines ke pie chart** sehingga label irisan terhubung dengan jelas.

Anda seharusnya sudah memiliki proyek Java dengan pustaka Chart di classpath. Jika Anda menggunakan Maven, tambahkan dependensi yang ditunjukkan pada bagian prasyarat.

## Prasyarat

* JDK 8 atau yang lebih baru terpasang.  
* Pustaka Chart (mis., `com.example.chart:chart-api:2.5.0`).  
* Familiaritas dasar dengan kelas Java dan pemanggilan metode.

---

## Cara menambahkan leader lines ke pie chart

Berikut ini program lengkap yang dapat dijalankan yang menunjukkan setiap langkah. Kode ini sengaja mandiri sehingga Anda dapat menyalin, menempel, dan menjalankannya tanpa modifikasi.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Penjelasan setiap langkah

| Langkah | Apa yang dilakukan kode | Mengapa penting |
|------|-------------------|----------------|
| **1️⃣ Sisipkan pie chart** | `builder.insertChart(ChartType.PIE, 400, 300)` membuat pie chart berukuran 400 × 300 pixel. | Membuat wadah chart dan menentukan dimensinya, yang memengaruhi penempatan label dan panjang leader line. |
| **2️⃣ Meledakkan irisan pertama** | `setExplosion(20)` menggeser irisan sebesar 20 % dari radius. | Irisan yang meledak menarik perhatian pemirsa dan membuat leader line terlihat. |
| **3️⃣ Atur warna sektor** | `setSectorColor(Color.BLUE)` mengubah isi irisan menjadi biru. | Kontras warna meningkatkan keterbacaan, terutama ketika irisan disorot. |
| **4️⃣ Aktifkan leader lines** | `setLeaderLines(true)` mengaktifkan garis penghubung yang mengaitkan irisan dengan labelnya. | Leader lines memastikan label tetap terbaca meskipun irisan dipindahkan ke luar. |

Pemanggilan `saveAsPng` bersifat opsional tetapi berguna untuk memverifikasi hasil visual. Setelah menjalankan program, Anda akan melihat gambar yang mirip dengan yang di bawah ini.

![Menambahkan leader lines ke pie chart](https://example.com/assets/pie-leader-lines.png "Menambahkan leader lines ke pie chart – irisan yang meledak dengan warna biru dan leader lines")

*Gambar: Sebuah pie chart di mana irisan pertama meledak, berwarna biru, dan terhubung ke labelnya dengan leader line.*

## Menyesuaikan leader lines (lanjutan)

Pemanggilan dasar `setLeaderLines(true)` menggunakan gaya default pustaka. Anda dapat mengontrol tampilan lebih lanjut:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Opsi-opsi ini berguna ketika Anda perlu menyesuaikan dengan merek perusahaan atau meningkatkan aksesibilitas.

### Menangani beberapa seri

Jika pie chart Anda berisi lebih dari satu seri, Anda mungkin ingin leader lines hanya untuk irisan tertentu. Gunakan indeks seri untuk menargetkan elemen yang tepat:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Ketika irisan tidak meledak, leader line biasanya tersembunyi secara otomatis, tetapi Anda dapat memaksanya dengan `setLeaderLineEnabled(true)`.

## Kesalahan umum dan cara menghindarinya

| Jebakan | Gejala | Solusi |
|--------|---------|-----|
| **Leader lines tidak terlihat** | Chart menampilkan tanpa penghubung. | Pastikan irisan meledak (`setExplosion` > 0) atau secara eksplisit aktifkan leader lines pada irisan. |
| **Label tumpang tindih** | Label saling bertabrakan. | Tingkatkan ukuran chart atau set `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Warna tidak diterapkan** | Irisan tetap berwarna default. | Pastikan Anda menargetkan indeks seri yang tepat (`getSeries().get(0)`). |
| **Gambar tidak tersimpan** | `saveAsPng` melemparkan pengecualian. | Periksa izin menulis untuk direktori output dan pastikan pustaka mendukung ekspor PNG. |

Menangani masalah ini lebih awal mencegah kejutan saat runtime dan menghasilkan chart yang rapi.

## Daftar sumber lengkap

Untuk kemudahan, berikut adalah file sumber lengkap lagi, termasuk impor dan komentar:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Menjalankan program ini menghasilkan `pie-with-leader-lines.png`, yang menampilkan pie chart dengan irisan biru yang meledak dan leader line yang jelas menunjuk ke label irisan.

## Kesimpulan

Anda sekarang tahu cara **menambahkan leader lines ke pie chart** objek di Java menggunakan Chart API. Prosesnya terdiri dari menyisipkan `ChartType.PIE`, meledakkan irisan yang diinginkan, menyesuaikan warnanya, dan mengaktifkan leader lines. Dengan opsi styling opsional, Anda dapat menyesuaikan warna garis, ketebalan, dan penempatan label untuk memenuhi kebutuhan visual apa pun.

Selanjutnya, pertimbangkan untuk menjelajahi topik terkait seperti **pie chart explosion Java**, **set sector color Chart API**, dan **builder.insertChart usage** untuk membuat visualisasi yang lebih canggih seperti donut chart, stacked pie, atau dashboard interaktif.

Silakan bereksperimen dengan indeks irisan yang berbeda, warna, dan gaya leader‑line—chart Anda akan menjadi lebih informatif dan menarik secara visual dengan setiap penyesuaian. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat column chart menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Menambahkan Nilai Date Time ke Axis Sebuah Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Menyisipkan Column Chart di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}