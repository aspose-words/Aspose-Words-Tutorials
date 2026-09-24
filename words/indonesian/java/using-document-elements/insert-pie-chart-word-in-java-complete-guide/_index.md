---
category: general
date: 2026-09-24
description: Masukkan diagram lingkaran ke dalam DOCX menggunakan Aspose.Words for
  Java. Pelajari cara mengatur ukuran lubang, meledakkan irisan diagram lingkaran,
  menyorot irisan diagram lingkaran, dan membuat diagram DOCX dengan mudah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: id
lastmod: 2026-09-24
og_description: Masukkan grafik pai ke dalam DOCX dengan Aspose.Words untuk Java.
  Kuasai pengaturan ukuran lubang, meletuskan irisan grafik pai, menyorot irisan grafik
  pai, dan buat grafik DOCX dalam hitungan menit.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Masukkan kata diagram lingkaran di Java – tutorial langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Menyisipkan kata diagram lingkaran di Java – panduan lengkap
url: /id/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan pie chart ke dalam Word – panduan lengkap

Jika Anda perlu **menyisipkan pie chart** ke dalam file DOCX, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words for Java. Anda akan melihat alur kerja lengkap mulai dari membuat dokumen hingga menyesuaikan diagram sehingga irisan meletus, ukuran lubang diatur menjadi nol, dan irisan tersebut disorot.

Bekerja dengan diagram dalam dokumen Word sering terasa seperti urusan terpisah dari pemrosesan teks biasa, tetapi Aspose.Words menyatukan keduanya. Pada langkah‑langkah berikut Anda juga akan belajar cara **membuat docx chart** yang siap dibuka di Microsoft Word, Google Docs, atau penampil DOCX lainnya.

## Apa yang akan Anda capai

* **Menyisipkan pie chart** ke dalam dokumen kosong  
* **Mengatur ukuran lubang** untuk mengubah diagram menjadi lingkaran penuh (bukan donat)  
* **Melepaskan irisan pie** untuk menarik perhatian pada segmen tertentu  
* **Menyorot irisan pie chart** dengan format khusus  
* **Membuat docx chart** yang dapat dibagikan atau diedit lebih lanjut  

### Prasyarat

* Java 17 atau lebih baru (kode juga dapat dikompilasi dengan Java 8)  
* Perpustakaan Aspose.Words for Java (versi 23.9 atau lebih baru)  
* IDE atau alat build (Maven/Gradle) yang dapat menyelesaikan dependensi Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Cara menyisipkan pie chart ke dalam DOCX menggunakan Aspose.Words

Langkah pertama adalah membuat dokumen kosong baru dan memperoleh `DocumentBuilder`. Builder memberikan akses langsung ke aliran konten dokumen, sehingga sangat mudah untuk **menyisipkan pie chart**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Mengapa ini penting
`Document` mewakili seluruh file Word, sementara `DocumentBuilder` adalah API tingkat tinggi yang memungkinkan Anda menyisipkan paragraf, tabel, dan diagram tanpa harus berurusan dengan XML tingkat rendah. Memulai dengan dokumen bersih memastikan bahwa diagram yang Anda tambahkan menjadi satu‑satunya konten, yang ideal untuk belajar atau menghasilkan laporan berbasis templat.

## Atur ukuran lubang untuk membuat lingkaran penuh

Secara default, Aspose.Words membuat diagram donat ketika Anda meminta diagram pie. Untuk menjadikan diagram benar‑benar lingkaran, Anda harus **mengatur ukuran lubang** ke `0`. Ini menghilangkan lubang tengah dan menghasilkan tampilan pie klasik.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Tips praktis
Jika nanti Anda memutuskan beralih ke diagram donat, cukup ubah nilai `holeSize` menjadi persentase (misalnya `30`). API yang sama bekerja untuk kedua jenis diagram.

## Melepaskan irisan pie untuk menyorot segmen

Melepaskan (explode) sebuah irisan membuatnya menonjol secara visual. Operasi **explode pie slice** memindahkan irisan yang dipilih ke luar dengan persentase tertentu dari radius diagram.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Mengapa harus explode?
Irisan yang meletus menarik mata pembaca ke titik data paling penting—sangat cocok untuk dasbor atau ringkasan eksekutif. Nilai `20` berarti 20 % dari radius; Anda dapat menyesuaikannya antara `0` (tidak meletus) dan `100` (sepenuhnya terlepas).

## Sorot irisan pie chart dengan format khusus

Selain meletus, Anda mungkin ingin **menyorot irisan pie chart** dengan mengubah warna isian atau border. Walaupun kode demo berfokus pada ledakan, Anda dapat memperluasnya sebagai berikut:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Catatan ahli
Mengubah warna isian sebuah irisan tertentu memerlukan akses ke objek `DataPoint`. Jika Anda memiliki beberapa seri, iterasikan melalui `series.getDataPoints()` dan terapkan gaya secara kondisional.

## Simpan dan verifikasi docx chart yang telah dibuat

Akhirnya, Anda **membuat docx chart** dengan menyimpan `Document`. File yang dihasilkan dapat dibuka di Microsoft Word untuk melihat diagram pie yang telah diformat.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Output yang diharapkan
Membuka `PieChartFormatted.docx` menampilkan satu diagram pie:

* Diagram menempati area 400 × 300 pt.  
* Ukuran lubang adalah `0`, sehingga diagram menjadi pie penuh.  
* Irisan pertama meletus sebesar 20 % dan berwarna merah (jika Anda menambahkan format opsional).  

Sekarang Anda memiliki **docx chart** yang dapat didistribusikan, disematkan dalam email, atau diedit lebih lanjut secara programatik.

---

## Variasi umum dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Beberapa seri** | Loop melalui `pieChart.getChart().getSeries()` dan atur `Explosion` atau `FillColor` per seri. |
| **Data dinamis** | Isi seri dengan nilai dari basis data atau CSV sebelum memanggil `setExplosion`. |
| **Ukuran diagram berbeda** | Ubah argumen lebar/tinggi pada `insertChart(ChartType.PIE, width, height)`. |
| **Ekspor ke PDF** | Setelah menyimpan DOCX, panggil `doc.save("output.pdf")` untuk menghasilkan versi PDF dari diagram yang sama. |
| **Lokalisasi** | Gunakan `DocumentBuilder.insertChart` dengan format angka spesifik locale untuk label. |

### Pro tip
Selalu panggil `setHoleSize(0)` **setelah** `insertChart`. Jika Anda mengaturnya sebelum penyisipan, Aspose.Words akan mengembalikan ukuran donat default begitu diagram dibuat.

---

## Ringkasan

Anda kini tahu cara **menyisipkan pie chart** ke dalam dokumen Word menggunakan Java, cara **mengatur ukuran lubang** untuk tampilan pie penuh, cara **meletuskan irisan pie** untuk menarik perhatian, dan cara **menyorot irisan pie chart** dengan warna khusus. Contoh lengkap juga menunjukkan cara **membuat docx chart** yang siap didistribusikan.

---

## Langkah selanjutnya

* Jelajahi tipe diagram lain (`BAR`, `LINE`, `SCATTER`) dengan `ChartType`.  
* Gabungkan pembuatan diagram dengan mail merge untuk menghasilkan laporan yang dipersonalisasi.  
* Integrasikan DOCX yang dihasilkan ke dalam layanan web yang mengembalikan file sesuai permintaan.  

Jika Anda menemui masalah, pastikan Anda menggunakan versi Aspose.Words yang kompatibel dan bahwa direktori output ada serta dapat ditulisi.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}