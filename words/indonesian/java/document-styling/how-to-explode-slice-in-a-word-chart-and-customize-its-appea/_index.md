---
category: general
date: 2026-10-04
description: Pelajari cara meledakkan irisan pada diagram Word, meledakkan irisan
  diagram lingkaran, dan mengubah ukuran diagram donat dengan contoh Java langkah
  demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: id
lastmod: 2026-10-04
og_description: Cara meledakkan irisan pada diagram Word dan menyesuaikan diagram
  pai atau donat dengan Java. Ikuti contoh lengkap untuk memodifikasi diagram di Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Cara meledakkan irisan pada diagram Word – panduan Java lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Cara memisahkan irisan pada diagram Word dan menyesuaikan tampilannya
url: /id/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara meledakkan irisan pada diagram Word dan menyesuaikan tampilannya

Jika Anda perlu **meledakkan irisan** dalam diagram Word, panduan ini menunjukkan cara melakukannya secara tepat. Baik Anda menyiapkan presentasi penjualan maupun laporan keuangan, meledakkan irisan diagram pie atau menyesuaikan lubang doughnut dapat membuat data terpenting lebih menonjol. Pada bagian berikut Anda juga akan belajar cara **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, dan **customize pie chart word** dokumen menggunakan Aspose.Words for Java.

Anda akan menyelesaikan tutorial ini dengan program Java lengkap yang siap dijalankan, yang memuat file `.docx`, meledakkan irisan pertama diagram pie, mengubah ukuran lubang doughnut, dan menyimpan hasilnya. Tidak diperlukan skrip eksternal atau penyuntingan manual.

## Prasyarat

- Java 17 atau lebih baru yang terpasang di mesin pengembangan Anda.  
- Maven 3.6+ (atau Gradle) untuk mengelola dependensi.  
- Pustaka Aspose.Words for Java (versi percobaan gratis dapat digunakan untuk pengembangan).  
- Dokumen Word (`input.docx`) yang berisi setidaknya satu diagram (pie atau doughnut).

## Langkah 1: Tambahkan Aspose.Words ke proyek Anda

Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Untuk Gradle, letakkan ini di `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Jaga versi pustaka Anda tetap terbaru; rilis terbaru menambahkan dukungan untuk tipe diagram tambahan dan meningkatkan kinerja.

## Langkah 2: Muat dokumen Word yang berisi diagram

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** Memuat dokumen membuat representasi dalam memori yang dapat dijelajahi oleh Aspose.Words. Tanpa objek ini Anda tidak dapat mengakses node diagram.

## Langkah 3: Ambil diagram pertama dalam dokumen

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` mencakup semua objek gambar, termasuk diagram. Argumen `true` memberi tahu Aspose untuk mencari secara rekursif, memastikan diagram pertama ditemukan bahkan jika berada di dalam tabel.

## Langkah 4: Meledakkan irisan pertama diagram pie

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** Metode `setExplosion` menerima nilai numerik yang menentukan seberapa jauh irisan bergerak menjauh dari pusat. Nilai `20` cukup terlihat tanpa merusak tata letak diagram.

## Langkah 5: Sesuaikan ukuran lubang doughnut untuk diagram doughnut

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** Lubang doughnut yang lebih besar dapat meningkatkan keterbacaan ketika Anda memiliki banyak titik data. Metode `setDoughnutHoleSize` mengharapkan persentase (0‑100).

## Langkah 6: Simpan dokumen yang telah dimodifikasi

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Output yang diharapkan

- Irisan pertama pada diagram pie pertama dipindahkan ke luar, sehingga menonjol.  
- Jika diagramnya berupa doughnut, lubang pusat memperluas hingga 40 % dari radius diagram.  
- File hasil `PieChart.docx` dapat dibuka di Microsoft Word, LibreOffice, atau penampil kompatibel lainnya, menampilkan perubahan visual yang Anda terapkan secara programatis.

## Contoh lengkap yang dapat dijalankan

Berikut seluruh program dalam satu blok. Salin ke `ChartExploder.java`, sesuaikan jalur file, dan jalankan dengan `mvn compile exec:java` (atau konfigurasi run IDE Anda).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Menjalankan kode ini akan **modify chart in Word**, **explode pie chart slice**, dan **change doughnut chart size** secara otomatis.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika dokumen berisi beberapa diagram?* | Contoh ini menargetkan **diagram pertama** (`NodeType.SHAPE, 0`). Untuk bekerja dengan diagram lain, ubah indeks atau iterasi melalui `doc.getChildNodes(NodeType.SHAPE, true)` dan filter dengan `shape.getChart() != null`. |
| *Apakah saya dapat meledakkan irisan selain yang pertama?* | Ya. Akses seri yang diinginkan melalui `chart.getSeries().get(seriesIndex)` dan panggil `setExplosion(value)`. Indeks dimulai dari nol. |
| *Apakah ini bekerja dengan file Word 2007‑2021?* | Aspose.Words mendukung `.doc`, `.docx`, `.dot`, dan `.dotx`. Kode yang sama berfungsi di semua versi karena pustaka mengabstraksi format file. |
| *Bagaimana jika diagramnya berupa bar atau line chart?* | `setExplosion` dan `setDoughnutHoleSize` hanya berlaku untuk diagram tipe pie. Kode secara aman melewati operasi tersebut ketika tipe diagram berbeda. |
| *Apakah saya memerlukan lisensi untuk Aspose.Words?* | Lisensi evaluasi gratis menghapus batas 30 hari tetapi menambahkan watermark. Untuk produksi, beli lisensi untuk menghilangkan watermark dan membuka semua fungsi. |

## Kesimpulan

Anda kini tahu **cara meledakkan irisan** dalam diagram Word, cara **modify chart in Word**, dan cara **change doughnut chart size** menggunakan Aspose.Words for Java. Contoh lengkap memperlihatkan alur kerja penuh—dari memuat dokumen, menemukan diagram, menerapkan penyesuaian visual, hingga menyimpan hasil—sehingga Anda dapat mengintegrasikan langkah‑langkah ini ke dalam pipeline pelaporan atau pembuatan dokumen apa pun.

**Langkah selanjutnya**

- Jelajahi penyesuaian diagram lain seperti mengubah warna, menambahkan label data, atau mengganti tipe diagram (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Gabungkan logika ini dengan Aspose.PDF untuk menghasilkan versi PDF dari laporan yang sama.  
- Otomatiskan proses untuk sekumpulan dokumen dengan melakukan loop pada file‑file dalam sebuah direktori.

Silakan bereksperimen dengan nilai ledakan atau persentase lubang doughnut yang berbeda untuk menyesuaikan pedoman desain Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Sembunyikan Sumbu Diagram dalam Dokumen Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Sisipkan Diagram Buih dalam Dokumen Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}