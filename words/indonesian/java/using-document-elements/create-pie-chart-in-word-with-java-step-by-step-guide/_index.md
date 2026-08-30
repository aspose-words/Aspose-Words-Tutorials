---
category: general
date: 2026-08-14
description: Buat diagram lingkaran di Word dengan Java menggunakan Aspose.Words.
  Pelajari cara menambahkan data seri ke diagram dan memutar irisan diagram lingkaran
  hanya dalam beberapa baris kode.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: id
lastmod: 2026-08-14
og_description: Buat diagram lingkaran di Word dengan Java menggunakan Aspose.Words.
  Tutorial ini menunjukkan cara menambahkan data seri ke diagram dan memutar irisan
  diagram lingkaran dengan cepat.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Buat diagram lingkaran di Word dengan Java – panduan pemrograman lengkap
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Buat diagram lingkaran di Word dengan Java – panduan langkah demi langkah
url: /id/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat diagram lingkaran di Word dengan Java – panduan langkah demi langkah

Jika Anda perlu **membuat diagram lingkaran di Word** secara programatis, panduan ini menunjukkan secara tepat cara melakukannya dengan Java dan Aspose.Words. Anda akan mempelajari alur kerja lengkap, mulai dari menyisipkan diagram hingga menambahkan titik data dan memutar irisan pertama.

Membuat diagram langsung dalam file `.docx` menghilangkan langkah salin‑tempel manual dan memungkinkan Anda mengotomatisasi laporan, faktur, atau dasbor. Sepanjang proses kami juga akan membahas **cara menambahkan data seri ke diagram** dan cara **memutar irisan diagram lingkaran** untuk penekanan visual yang lebih baik.

## Membuat diagram lingkaran di Word – ikhtisar

Aspose.Words for Java menyediakan API `DocumentBuilder` yang fluida yang dapat menyisipkan objek diagram ke dalam dokumen Word. Jenis diagram yang Anda pilih menentukan tata letak default, dan Anda dapat menyesuaikan seri, warna, sudut, bahkan beralih ke bentuk donat dengan satu panggilan metode.

### Mengapa menggunakan Aspose.Words?

* **Tidak memerlukan Microsoft Office** – perpustakaan ini bekerja di server mana pun atau lingkungan CI.  
* **Fidelity .docx penuh** – diagram yang dihasilkan terlihat identik dengan yang dibuat secara manual di Word.  
* **Dependensi satu‑file** – cukup tambahkan JAR dan Anda siap menggunakannya.

## Cara menambahkan data seri ke diagram

Diagram tanpa data hanyalah placeholder. Objek `Chart` menyediakan koleksi `Series`; setiap seri menyimpan daftar nilai numerik yang dipetakan ke irisan (untuk diagram lingkaran) atau titik (untuk diagram garis). Menambahkan data sangat mudah:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Apa yang dilakukan kode:**  
* `chart.getSeries()` mengembalikan `List<ChartSeries>`.  
* `get(0)` memilih seri pertama karena diagram lingkaran secara definisi hanya memiliki satu seri.  
* `add(double)` menambahkan sebuah titik data. Nilai-nilai secara otomatis dikonversi menjadi persentase yang jumlahnya 100 % saat diagram dirender.

> **Pro tip:** Jika sumber data Anda berisi lebih dari tiga kategori, terus tambahkan nilai dengan cara yang sama. Aspose.Words akan secara otomatis membuat irisan tambahan.

## Memutar irisan diagram lingkaran

Kadang Anda ingin irisan tertentu mulai pada sudut tertentu sehingga segmen paling penting menghadap pemirsa. Metode `setFirstSliceAngle(double)` memutar seluruh diagram, secara efektif memindahkan awal irisan pertama:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Sudut diukur dalam derajat searah jarum jam dari sumbu vertikal. Menetapkannya ke `0` (default) menempatkan irisan pertama di bagian atas. Sesuaikan nilai untuk menyorot irisan atau agar sesuai dengan pedoman desain.

> **Pertanyaan umum:** *Apakah memutar memengaruhi urutan data?*  
> Tidak. Urutan data tetap sama; hanya posisi awal visual yang berubah.

## Contoh Java lengkap

Berikut ini adalah program lengkap yang siap dijalankan yang membuat dokumen Word dengan diagram lingkaran, menambahkan data seri, memutar irisan, dan menyimpan file. Semua impor yang diperlukan tercantum, sehingga Anda dapat menyalin kode ke IDE mana pun.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Output yang diharapkan

* Sebuah file bernama **PieChart.docx** muncul di folder `output`.  
* Membuka file tersebut di Microsoft Word menampilkan diagram lingkaran berwarna dengan tiga irisan (40 %, 30 %, 30 %).  
* Diagram diputar 45° searah jarum jam, sehingga irisan pertama mulai sedikit ke kanan sumbu vertikal.

## Kesulitan umum dan praktik terbaik

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Diagram muncul kosong** | Dokumen disimpan sebelum diagram sepenuhnya dirender. | Panggil `doc.save()` **setelah** semua modifikasi diagram. |
| **Nilai irisan tidak berjumlah 100 %** | Menambahkan angka mentah yang tidak mewakili persentase dapat menyebabkan skala yang tidak terduga. | Berikan nilai yang secara logis mewakili bagian dari keseluruhan, atau biarkan Aspose.Words menghitung persentase secara otomatis. |
| **Rotasi tidak berpengaruh** | Menggunakan `ChartType.DOUGHNUT` tanpa mengatur `holeSize` dapat menyembunyikan efek rotasi. | Pertahankan diagram sebagai `PIE` atau sesuaikan `holeSize` setelah mengatur sudut. |
| **Kesalahan jalur file** | Jalur relatif dapat terresolusi berbeda pada Windows vs. Linux. | Gunakan `Paths.get("output", "PieChart.docx").toString()` atau jalur absolut untuk kode produksi. |

### Tips untuk penggunaan produksi

* **Gunakan kembali `DocumentBuilder`** – Anda dapat menyisipkan beberapa diagram dalam dokumen yang sama dengan memanggil `insertChart` berulang kali.  
* **Styling** – gunakan `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` untuk menampilkan persentase langsung pada diagram.  
* **Kinerja** – buat diagram sekali dan kloning (`chart.deepClone()`) jika Anda memerlukan diagram identik di beberapa tempat.

## Memutar irisan diagram lingkaran – skenario lanjutan

* **Sudut dinamis** – hitung sudut berdasarkan data (misalnya, buat irisan terbesar mulai di bagian atas).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Beberapa seri** – meskipun diagram lingkaran biasanya memiliki satu seri, Aspose.Words memungkinkan Anda menambahkan lebih banyak untuk diagram lingkaran bertumpuk. Rotasi tetap hanya berlaku pada seri pertama.

## Kesimpulan

Anda sekarang tahu cara **membuat diagram lingkaran di Word** menggunakan Java, cara **menambahkan data seri ke diagram**, dan cara **memutar irisan diagram lingkaran** untuk penekanan visual. Contoh lengkap menunjukkan seluruh alur kerja—dari inisialisasi dokumen hingga menyimpan file `.docx` akhir—sehingga Anda dapat mengintegrasikan pembuatan diagram ke dalam pipeline pelaporan otomatis apa pun.

### Selanjutnya?

* Jelajahi tipe diagram lain (`ChartType.BAR`, `ChartType.LINE`) untuk memperluas toolkit otomatisasi Anda.  
* Gabungkan pembuatan diagram dengan **mail merge** untuk menghasilkan laporan yang dipersonalisasi bagi setiap penerima.  
* Selami **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) untuk menyesuaikan dengan merek perusahaan Anda.

Silakan bereksperimen dengan set data, sudut, dan gaya diagram yang berbeda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cara Mengonversi Word ke PDF Menggunakan Aspose.Words untuk Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}