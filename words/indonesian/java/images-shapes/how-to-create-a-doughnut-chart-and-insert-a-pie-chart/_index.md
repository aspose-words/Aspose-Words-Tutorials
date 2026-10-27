---
category: general
date: 2026-10-26
description: Buat diagram donat dan sisipkan diagram pai dalam Java dengan kode langkah
  demi langkah. Pelajari alur kerja lengkap untuk visualisasi diagram yang fleksibel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: id
lastmod: 2026-10-26
og_description: Buat grafik donat di Java dengan panduan ini yang juga menunjukkan
  cara menyisipkan grafik pai untuk visualisasi yang fleksibel.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Buat diagram donat dan sisipkan diagram lingkaran – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Cara membuat diagram donat dan menyisipkan diagram lingkaran
url: /id/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram donat dan menyisipkan diagram pai

Jika Anda perlu **membuat diagram donat** di Java, tutorial ini akan memandu Anda melalui langkah‑langkah yang tepat. Kami juga akan menunjukkan cara **menyisipkan diagram pai** menggunakan API builder yang sama, sehingga Anda dapat beralih antara gaya visual dengan mudah. Pada akhir panduan, Anda akan memiliki program lengkap yang dapat dijalankan yang menghasilkan kedua jenis diagram dan menunjukkan kustomisasi umum.

Tutorial ini mencakup:

* Menginisialisasi builder diagram yang disediakan oleh perpustakaan yang dipilih.  
* Membuat diagram donat dan mengonfigurasi ukuran lubang.  
* Menyisipkan diagram pai dan meledakkan sebuah irisan untuk penekanan.  
* Tips menangani kasus tepi seperti seri yang hilang atau tipe diagram yang tidak didukung.

Anda hanya memerlukan JDK terbaru (8 atau lebih baru) dan JAR perpustakaan diagram pada classpath Anda. Tidak diperlukan layanan eksternal.

---

## Prasyarat

| Item | Alasan |
|------|--------|
| Java Development Kit (JDK) 8+ | Diperlukan untuk mengompilasi dan menjalankan contoh. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Menyediakan `ChartBuilder`, `ChartType`, dan metode manipulasi seri yang digunakan dalam kode. |
| An IDE or a text editor | Untuk menulis dan mengeksekusi file sumber Java. |

Pastikan JAR perpustakaan ditambahkan ke jalur build proyek Anda. Jika Anda menggunakan Maven, tambahkan dependensi yang sesuai; jika tidak, letakkan JAR di folder `libs` dan referensikan saat kompilasi.

---

## Langkah 1: Siapkan builder diagram

Langkah pertama adalah membuat instance `ChartBuilder` (atau yang setara) yang akan menghasilkan objek diagram. Objek ini berfungsi sebagai pabrik dan menyimpan worksheet atau kanvas tempat diagram akan ditempatkan.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Mengapa ini penting:**  
Builder mengaitkan diagram dengan worksheet tertentu, memastikan semua objek diagram berikutnya berbagi permukaan gambar yang sama. Melewatkan langkah ini akan membuat Anda tidak memiliki lokasi target untuk elemen visual.

---

## Langkah 2: **Buat diagram donat**

Sekarang kami menghasilkan diagram donat dengan ukuran yang ditentukan. Ukuran lubang menentukan berapa banyak bagian tengah diagram yang kosong, mengubah pai biasa menjadi donat.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Penjelasan:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` membuat objek diagram dan memesan ruang pada worksheet.  
* `setHoleSize(30)` mengubah pai menjadi donat dengan pusat kosong 30 %.  
* `add("{10, 20, 30, 40}", true)` menyediakan empat titik data; flag `true` memberi tahu perpustakaan untuk memperlakukan nilai‑nilai tersebut sebagai satu seri.

**Kasus tepi:** Jika tipe diagram yang dipilih tidak mendukung lubang (misalnya, diagram batang), pemanggilan `getDoughnutChart()` akan melempar pengecualian. Selalu verifikasi tipe diagram sebelum menyesuaikan ukuran lubang.

---

## Langkah 3: **Sisipkan diagram pai**

Setelah donat siap, kami menunjukkan cara **menyisipkan diagram pai** menggunakan builder yang sama. Langkah ini menyoroti kesamaan antara kedua tipe diagram dan menunjukkan cara menekankan sebuah irisan.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Penjelasan:**  

* `ChartType.PIE` memberi tahu builder untuk membuat diagram pai klasik.  
* `setExplode(10)` menggeser irisan pertama sebesar 10 % radius, teknik umum untuk menyoroti titik data penting.  

**Tip:** Metode `setExplode` hanya berfungsi pada seri pertama diagram pai. Jika Anda memiliki beberapa seri, Anda harus menargetkan indeks yang tepat.

---

## Langkah 4: Simpan workbook

Akhirnya, tulis workbook ke file sehingga Anda dapat melihat diagram di Excel atau penampil kompatibel lainnya.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Mengapa menyimpan sekarang:** Menyimpan workbook memfinalisasi semua operasi gambar. Mencoba melihat file sebelum disimpan akan menghasilkan dokumen kosong atau tidak lengkap.

**Hasil:** Membuka *DoughnutAndPieChart.xlsx* menampilkan diagram donat dengan lubang 30 % di sebelah kiri dan diagram pai dengan irisan pertama yang meledak di sebelah kanan.

---

## Langkah 5: Variasi umum dan pemecahan masalah

| Situasi | Penyesuaian |
|-----------|------------|
| **Dimensi diagram berbeda** | Ubah argumen lebar dan tinggi pada `insertChart`. |
| **Beberapa seri data** | Panggil `add` beberapa kali atau berikan string array 2‑D. |
| **Ukuran lubang dinamis** | Hitung ukuran lubang berdasarkan rentang data, lalu panggil `setHoleSize`. |
| **Mengekspansi beberapa irisan** | Loop melalui `chart.getSeries().get(i).setExplode(percent)` untuk setiap irisan yang ingin Anda offset. |
| **Perpustakaan tidak mendukung donat** | Gunakan diagram pai dan gambar lingkaran putih secara manual sebagai overlay, meskipun ini kurang presisi. |

**Pro tip:** Selalu panggil `builder.flush()` (jika tersedia) setelah menyisipkan diagram saat bekerja dengan workbook besar. Ini melepaskan buffer internal dan mencegah kebocoran memori.

![Kode Java yang membuat diagram donat dan menyisipkan diagram pai](https://example.com/images/doughnut-pie-java.png "contoh membuat diagram donat dalam Java")

*Gambar ini menggambarkan tata letak workbook akhir dengan kedua diagram berdampingan.*

---

## Kesimpulan

Anda kini tahu cara **membuat diagram donat** dan **menyisipkan diagram pai** di Java menggunakan API builder yang fluens. Contoh lengkap mencakup inisialisasi, konfigurasi ukuran, penentuan ukuran lubang, ledakan irisan, dan output file. Dari sini Anda dapat menjelajahi kustomisasi tambahan seperti warna, legenda, dan label data untuk menyesuaikan kebutuhan pelaporan Anda.

**Langkah Selanjutnya**

* Bereksperimen dengan fitur **chart customization Java** seperti isian gradien dan label data.  
* Integrasikan pembuatan diagram ke dalam layanan web yang mengembalikan workbook sesuai permintaan.  
* Bandingkan pendekatan builder dengan perpustakaan lain (misalnya, JFreeChart) untuk memilih yang paling cocok bagi proyek Anda.

Selamat membuat diagram!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram donat dalam dokumen Word dengan Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Simpan dokumen Word setelah mengedit diagram donat di Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Sisipkan Diagram Pai di Java – Ekspansi, Rotasi & Sorot Irisan](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}