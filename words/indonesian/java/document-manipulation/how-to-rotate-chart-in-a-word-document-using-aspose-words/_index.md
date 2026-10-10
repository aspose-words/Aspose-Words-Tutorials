---
category: general
date: 2026-10-10
description: Pelajari cara memutar diagram dalam file Word dan memodifikasi diagram
  di Word untuk mengubah ukuran diagram donat dengan contoh Java lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: id
lastmod: 2026-10-10
og_description: Cara memutar diagram dalam file Word dan memodifikasi diagram di Word
  untuk mengubah ukuran diagram donat menggunakan Aspose.Words untuk Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Cara memutar grafik dalam dokumen Word – panduan Java langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cara memutar bagan dalam dokumen Word menggunakan Aspose.Words
url: /id/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memutar grafik dalam dokumen Word menggunakan Aspose.Words

Jika Anda perlu **memutar grafik** di dalam file Microsoft Word, panduan ini menunjukkan langkah‑langkah tepatnya. Anda juga akan belajar cara **memodifikasi grafik di Word** untuk **mengubah ukuran grafik donat** tanpa meninggalkan kode Java Anda.

Otomatisasi Word sering terasa seperti serangkaian panggilan API yang terpisah, tetapi dengan Aspose.Words Anda dapat memperlakukan grafik seperti node dokumen lainnya. Pada akhir tutorial ini Anda akan memiliki program yang dapat dijalankan yang memuat file `.docx` yang ada, memutar grafik donat sebesar 45°, mengurangi lubang menjadi 50 % dari radius, dan menyimpan hasilnya sebagai file baru.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.
* Maven (atau Gradle) untuk mengelola dependensi.
* Dokumen Word input (`input.docx`) yang sudah berisi grafik donat.
* Lisensi Aspose.Words for Java yang valid (atau gunakan mode evaluasi).

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven baru atau tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Menjalankan `mvn clean install` akan mengunduh pustaka dan membuat kelas tersedia di classpath Anda.

## Langkah 2: Muat dokumen Word yang berisi grafik

Operasi pertama adalah membuka dokumen yang sudah ada. Kelas `Document` mewakili seluruh file.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Memuat file **tidak** mengubahnya; ia hanya membuat representasi dalam memori yang dapat Anda query dan edit.

## Langkah 3: Buat DocumentBuilder untuk navigasi

`DocumentBuilder` memberi Anda API mirip kursor untuk menelusuri pohon dokumen. Kita akan menggunakannya untuk menemukan bentuk grafik pertama.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder memulai di awal dokumen, tetapi Anda dapat memindahkannya ke node mana pun nanti jika diperlukan.

## Langkah 4: Dapatkan bentuk grafik pertama

Grafik disimpan sebagai node `Shape`. Dengan memfilter child node berjenis `NodeType.SHAPE` kita dapat mengekstrak objek grafik.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Jika dokumen berisi beberapa grafik, Anda dapat mengiterasi `getChildNodes` dan memeriksa setiap `Shape` dengan `hasChart()` sebelum melakukan casting.

## Langkah 5: Putar grafik (cara memutar grafik)

Grafik donat pada dasarnya adalah grafik pai dengan lubang. Memutarnya mengubah sudut mulai irisan pertama.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Metode `setStartAngle` mengharapkan nilai double yang mewakili derajat. Nilai positif memutar searah jarum jam, sedangkan nilai negatif memutar berlawanan arah jarum jam.

## Langkah 6: Ubah ukuran lubang donat (ubah ukuran grafik donat)

Ukuran lubang dinyatakan sebagai fraksi dari radius grafik. Nilai `0.5` berarti lubang menempati 50 % dari total radius.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** Rentang nilai yang valid adalah `0.0` (tanpa lubang, yaitu pai biasa) hingga `0.9` (cincin sangat tipis). Nilai di luar rentang ini akan melempar `IllegalArgumentException`.

## Langkah 7: Simpan dokumen yang telah dimodifikasi

Akhirnya, tulis perubahan kembali ke disk.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Saat Anda membuka `DoughnutFormatted.docx` di Microsoft Word, Anda akan melihat grafik donat berputar 45° dan lubang berkurang menjadi setengah ukuran aslinya.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut program lengkap yang dapat Anda salin‑tempel ke IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Output yang diharapkan

Menjalankan program mencetak:

```
Chart rotated and doughnut size changed successfully.
```

Membuka `DoughnutFormatted.docx` menampilkan grafik donat yang irisan pertamanya dimulai pada posisi 45° dan radius dalamnya menempati setengah radius luar.

## Variasi umum dan kasus tepi

| Situasi | Apa yang harus disesuaikan | Mengapa penting |
|-----------|----------------------------|-----------------|
| **Beberapa grafik** | Loop melalui `getChildNodes(NodeType.SHAPE, true)` dan periksa `shape.hasChart()` untuk masing‑masing | Menjamin Anda memodifikasi grafik yang dimaksud, bukan yang pertama |
| **Grafik batang atau garis** | `setStartAngle` tidak berlaku; gunakan `chart.getSeries().get(0).setFillFormat(...)` untuk penyesuaian visual lainnya | Tidak semua tipe grafik mendukung rotasi; hanya grafik donat/pai yang memiliki sudut mulai |
| **Grafik tanpa lubang donat** | Lewati `setDoughnutHoleSize` atau ubah tipe grafik menjadi donat via `chart.setChartType(ChartType.DONUT)` | Mengubah ukuran lubang pada grafik non‑donat akan menimbulkan pengecualian |
| **Dokumen besar** | Gunakan `DocumentBuilder.moveToDocumentStart()` dan `builder.moveToNode(chartShape)` untuk navigasi terarah | Meningkatkan kinerja dengan menghindari traversal penuh node yang tidak relevan |

## Pro tip untuk manipulasi grafik yang andal

* **Cache referensi grafik** – Jika Anda berencana mengubah beberapa properti, simpan variabel `Chart` lokal daripada terus‑menerus memanggil `chartShape.getChart()`.
* **Validasi nilai input** – Sebelum memanggil `setStartAngle` atau `setDoughnutHoleSize`, periksa rentang nilai untuk menghindari error runtime.
* **Gunakan lisensi** – Mode evaluasi menambahkan watermark pada halaman pertama. Menerapkan lisensi (`License license = new License(); license.setLicense("Aspose.Words.lic");`) menghilangkannya.

## Langkah selanjutnya

Sekarang Anda tahu **cara memutar grafik** dan **mengubah ukuran grafik donat**, Anda dapat menjelajahi skenario **memodifikasi grafik di Word** lainnya:

* Ubah warna irisan dengan `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Tambahkan label data dengan memanggil `chart.getSeries().get(0).setHasDataLabel(true)`.
* Ekspor grafik sebagai gambar menggunakan `chart.toImage(300, 300, ImageType.PNG)`.

Setiap ekstensi ini mengikuti pola yang sama: dapatkan objek `Chart`, panggil setter yang sesuai, dan simpan dokumen.

---

**Anda baru saja menguasai cara memutar dan mengubah ukuran grafik donat di Word menggunakan Java.** Silakan sesuaikan kode untuk tipe grafik lain, integrasikan ke dalam pipeline pembuatan dokumen yang lebih besar, atau gabungkan dengan Aspose.Slides untuk otomatisasi PowerPoint. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}