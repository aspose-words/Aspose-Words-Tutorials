---
category: general
date: 2026-09-24
description: Pelajari cara membuat diagram di Word menggunakan Java, sisipkan diagram
  radial, dan simpan dokumen sebagai docx dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: id
lastmod: 2026-09-24
og_description: Buat diagram di Word dengan Java dan Aspose.Words. Tutorial ini menunjukkan
  cara menambahkan diagram radial, menyesuaikan data, dan menyimpan dokumen sebagai
  docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Buat diagram di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Cara membuat grafik di Word dengan Java dan Aspose.Words
url: /id/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat chart di Word dengan Java dan Aspose.Words

Jika Anda perlu **create chart in Word** dari aplikasi Java, panduan ini akan memandu Anda melalui proses lengkap. Anda akan melihat cara menambahkan radial chart, secara opsional mengisi serinya, dan akhirnya **save document as docx** menggunakan library Aspose.Words for Java.

Menghasilkan data visual di dalam file Word adalah kebutuhan umum untuk pelaporan, penagihan, atau pembuatan dokumen otomatis. Pada akhir tutorial ini Anda akan dapat membuat proyek **create word document java** yang **add chart to Word** tanpa penyuntingan manual.

## Prasyarat

* Java Development Kit (JDK) 8 atau lebih baru.
* Maven atau Gradle untuk manajemen dependensi.
* IDE seperti IntelliJ IDEA, Eclipse, atau VS Code.
* Lisensi Aspose.Words untuk Java yang valid (versi percobaan gratis dapat digunakan untuk pengembangan).

Alat-alat ini menyediakan dasar untuk contoh kode yang akan diikuti.

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven baru (atau perbarui yang sudah ada) dan tambahkan dependensi Aspose.Words ke `pom.xml` Anda:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Menjalankan `mvn clean install` akan mengunduh library dan membuat kelas seperti `Document`, `DocumentBuilder`, dan `ChartType` tersedia di classpath.

> **Pro tip:** Jaga versi library tetap terbaru. Rilis baru menambahkan tipe chart dan meningkatkan kinerja rendering.

## Langkah 2: Buat dokumen Word baru

Langkah programatik pertama untuk **create chart in Word** adalah menginstansiasi `Document` kosong. Objek ini mewakili seluruh paket `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` berfungsi seperti kursor; ia mengetahui titik sisipan saat ini dan menyediakan metode untuk teks, tabel, dan chart. Pada titik ini Anda telah **created word document java** – kanvas bersih siap untuk konten.

## Langkah 3: Sisipkan radial chart

Aspose.Words mendukung banyak tipe chart. Untuk **insert radial chart**, panggil `insertChart` dengan `ChartType.RADIAL`. Metode ini juga memerlukan lebar dan tinggi dalam poin (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Objek `Shape` yang dikembalikan berisi objek chart yang mendasarinya. Chart secara otomatis merender graduasi untuk tata letak 24,9°, yang merupakan default untuk radial chart di Word.

### Mengapa menggunakan radial chart?

Diagram radial memvisualisasikan data yang melingkari lingkaran, menjadikannya ideal untuk menampilkan pola siklus (mis., penjualan bulanan, metrik jam). API yang sama dapat menyisipkan diagram batang, pai, atau garis, tetapi tipe radial menambahkan tampilan khas tanpa kode styling tambahan.

## Langkah 4: (Opsional) Isi data seri chart

Jika Anda ingin chart menampilkan nilai nyata, Anda perlu menambahkan seri dan titik. Potongan kode berikut menambahkan satu seri dengan tiga titik data:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Anda dapat mengulangi pemanggilan `add` sebanyak titik yang diperlukan. Aspose.Words secara otomatis memperbarui representasi visual, sehingga Anda melihat irisan radial menyesuaikan dengan nilai baru.

> **Common question:** *Bagaimana jika saya perlu mengikat data dari basis data?*  
> Ambil baris-barisnya, lakukan loop, dan panggil `series.getDataPoints().add(value, label)` di dalam loop. API ini thread‑safe dan bekerja dengan `ResultSet` apa pun yang Anda sediakan.

## Langkah 5: Simpan dokumen sebagai DOCX

Ketika chart sudah siap, langkah terakhir adalah **save document as docx**. Metode `save` menentukan format output dari ekstensi file.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

File yang dihasilkan berisi radial chart yang berfungsi penuh dan dapat dibuka di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung format DOCX. Karena kami menggunakan ekstensi `.docx`, Word menyimpan file dalam format Open XML, yang merupakan standar modern untuk dokumen Word.

### Memverifikasi hasil

Buka `RadialChartDemo.docx` di Word:

1. Anda harus melihat satu halaman dengan radial chart yang terpusat.
2. Jika Anda menambahkan data seri, chart menampilkan empat irisan berlabel Q1‑Q4.
3. Klik kanan pada chart → **Edit Data** untuk mengonfirmasi tabel data yang mendasarinya.

Jika chart muncul kosong, periksa kembali bahwa Anda memanggil `chart.getChart()` sebelum menambahkan seri, dan pastikan cursor `DocumentBuilder` berada pada posisi di mana Anda menginginkan chart.

## Langkah 6: Tips lanjutan untuk bekerja dengan chart

| Tip | Mengapa penting |
|-----|-----------------|
| **Atur gaya chart** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Meningkatkan konsistensi visual tanpa harus memformat setiap elemen secara manual. |
| **Ubah ukuran setelah penyisipan** – `chart.setWidth(500); chart.setHeight(350);` | Memungkinkan Anda menyesuaikan ukuran chart secara tepat berdasarkan tata letak halaman. |
| **Tambahkan judul** – `chart.getChart().getTitle().setText("Revenue Overview");` | Memberikan konteks kepada pembaca yang melihat dokumen tanpa teks di sekitarnya. |
| **Ekspor ke PDF** – `doc.save("RadialChartDemo.pdf");` | Berguna ketika Anda memerlukan versi yang tidak dapat diedit untuk distribusi. |
| **Penanganan lisensi** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Mencegah watermark evaluasi pada build produksi. |

Peningkatan ini bersifat opsional tetapi menunjukkan bagaimana Anda dapat menyesuaikan chart lebih lanjut setelah Anda mempelajari cara **add chart to Word**.

## Kesimpulan

Anda kini memiliki contoh lengkap dan mandiri yang menunjukkan cara **create chart in Word** menggunakan Java, **insert radial chart**, secara opsional mengisinya dengan data, dan **save document as docx**. Pola yang sama berlaku untuk tipe chart lain, sehingga Anda dapat memperluas tutorial ini ke chart batang, garis, atau pai sesuai kebutuhan.

Selanjutnya Anda mungkin ingin menjelajahi:

- **create word document java** proyek yang menggabungkan tabel, gambar, dan beberapa chart.
- Menggunakan **save document as docx** bersama dengan **save document as pdf** untuk pelaporan multi‑format.
- Menambahkan data dinamis dari REST API atau basis data ke chart Anda.

Silakan bereksperimen dengan opsi styling, dimensi chart, dan sumber data. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}