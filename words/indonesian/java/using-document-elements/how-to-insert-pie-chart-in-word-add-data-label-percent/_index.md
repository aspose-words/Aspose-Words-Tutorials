---
category: general
date: 2026-07-20
description: Cara menyisipkan diagram lingkaran di Word dengan Aspose.Words. Pelajari
  cara menambahkan label data persentase dan menampilkan persentase pada diagram untuk
  dokumen profesional.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: id
lastmod: 2026-07-20
og_description: cara memasukkan diagram lingkaran di Word menggunakan Aspose.Words.
  Panduan ini menunjukkan cara menambahkan persentase label data dan menampilkan persentase
  pada diagram hanya dalam beberapa baris.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: cara menyisipkan diagram lingkaran di Word – panduan cepat
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Cara menyisipkan diagram lingkaran di Word – tambahkan label data persentase
url: /id/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menyisipkan diagram pai di Word – menambahkan label data persentase

Pernah bertanya-tanya **how to insert pie chart** ke dalam dokumen Word tanpa berjuang dengan UI? Anda tidak sendirian. Dalam banyak skenario pelaporan Anda perlu *add pie chart to Word* dan, yang lebih penting, **show percent on pie chart** sehingga pembaca langsung memahami distribusi data.

Dalam tutorial ini kami akan memandu Anda melalui proses lengkap menggunakan Aspose.Words for Java. Pada akhir tutorial Anda akan tahu persis cara **add data label percent**, **display percentages on chart**, dan mendapatkan diagram pai yang rapi yang terlihat tepat pada percobaan pertama. Tanpa plugin tambahan, tanpa penyesuaian manual—hanya kode bersih yang dapat Anda sisipkan ke dalam proyek apa pun.

---

## Prasyarat

- Java 17 (atau lebih baru) – versi LTS saat ini yang didukung oleh Aspose.Words.
- Aspose.Words for Java 24.x (yang terbaru pada saat penulisan, Juli 2026).
- Setup Maven atau Gradle dasar untuk mengambil pustaka.
- IDE yang Anda suka (IntelliJ IDEA, Eclipse, VS Code… semua dapat digunakan).

Jika Anda sudah memiliki ini, bagus—mari kita mulai.

---

## Langkah 1: Siapkan proyek dan impor pustaka

Pertama, tambahkan dependensi Aspose.Words ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan chart.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Jaga nomor versi tetap terbaru; rilis yang lebih baru sering menambahkan perbaikan terkait chart yang membuat **display percentages on chart** lebih andal.

---

## Langkah 2: Buat dokumen Word baru dan builder

Builder adalah pisau Swiss‑army Anda untuk menyisipkan konten. Di sini kami membuat dokumen baru dan melampirkan `DocumentBuilder` ke dalamnya.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Mengapa kita membutuhkan builder? Builder mengabstraksi struktur OpenXML tingkat rendah, memungkinkan kami fokus pada *apa* yang kami inginkan—seperti **add pie chart to word**—bukan pada *bagaimana* XML terlihat.

---

## Langkah 3: Sisipkan diagram pai

Sekarang datang inti dari **how to insert pie chart**. Kami meminta builder menempatkan diagram pai dengan ukuran tertentu. Dimensi dalam poin (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Pada titik ini chart masih kosong, tetapi placeholder sudah ada di dokumen. Anda baru saja **add pie chart to word** secara programatis.

---

## Langkah 4: Isi chart dengan data

Diagram pai membutuhkan setidaknya satu seri nilai. Mari beri data contoh yang mewakili pangsa pasar.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Jika Anda membutuhkan beberapa seri (pie bertumpuk, doughnut, dll.) Anda dapat memanggil `pieChart.getSeries().add()` dan mengulangi langkah-langkah. Logika yang sama berlaku ketika Anda ingin **display percentages on chart** untuk setiap irisan.

---

## Langkah 5: **add data label percent** – tampilkan persentase pada irisan

Ini adalah bagian yang paling sering dilupakan oleh pengembang: mengonfigurasi label data agar menampilkan persentase. Tanpa ini, chart hanya menampilkan angka mentah, yang dapat ambigu.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Pemanggilan `setShowPercent(true)` memberi tahu Aspose.Words untuk merender label sebagai “30 %”, “45 %”, dll. Itu tepat cara Anda **show percent on pie chart** tanpa pekerjaan format tambahan.

---

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat memilih `.docx`, `.pdf`, atau bahkan `.html`. Untuk panduan ini kami akan tetap menggunakan format modern `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Jalankan program, buka `PieChartDemo.docx`, dan Anda akan melihat diagram pai yang dirender rapi dengan label persentase pada setiap irisan.

---

## Output yang Diharapkan

Di bawah ini adalah tangkapan layar file Word yang dihasilkan. Perhatikan bagaimana setiap irisan menampilkan bagiannya sebagai persentase—tepat seperti yang kami inginkan ketika kami mengatur **add data label percent**.

![Tangkapan layar dokumen Word yang berisi diagram pai dengan label persentase](/images/pie-chart-percent.png){.center width=600px alt="Tangkapan layar yang menunjukkan cara menyisipkan diagram pai di Word dengan label persentase"}

*Teks alt mencakup kata kunci utama, memenuhi kebutuhan SEO dan aksesibilitas.*

---

## Pertanyaan umum & penanganan kasus tepi

| Question | Answer |
|----------|--------|
| **Bisakah saya mengubah font label persentase?** | Ya. Setelah mengaktifkan `setShowPercent(true)`, ambil objek `DataLabel` dan sesuaikan properti `Font`-nya (`dataLabel.getFont().setSize(10);`). |
| **Bagaimana jika saya membutuhkan chart doughnut alih-alih pie?** | Ganti `ChartType.PIE` dengan `ChartType.DOUGHNUT` pada pemanggilan `insertChart`. Logika **add data label percent** yang sama berfungsi. |
| **Apakah versi Word lama (2007‑2010) menampilkan persentase dengan benar?** | Aspose.Words menulis XML dasar secara versi‑agnostik, sehingga persentase muncul di semua Word yang mendukung chart (2007+). |
| **Bagaimana menambahkan judul ke chart?** | Gunakan `pieChart.getTitle().setText("Market Share");` sebelum menyimpan. |
| **Bisakah saya menyisipkan chart ke paragraf atau sel tabel tertentu?** | Tentu saja. Pindahkan `DocumentBuilder` ke lokasi yang diinginkan (`builder.moveToParagraph(index, true);` atau `builder.moveToCell(table, row, column, true);`) sebelum memanggil `insertChart`. |

---

## Tips dan trik dari lapangan

- **Pro tip:** Jika Anda berencana menghasilkan banyak chart dalam loop, gunakan kembali satu instance `DocumentBuilder`; ini mengurangi penggunaan memori.
- **Watch out for:** Irisan yang sangat kecil (< 2 %). Aspose.Words mungkin menghilangkan label untuk menghindari kekacauan; Anda dapat memaksanya dengan `dataLabel.setShowLabel(true);`.
- **Performance note:** Rendering chart memakan banyak CPU. Untuk pembuatan laporan massal, pertimbangkan multi‑threading tetapi pastikan setiap thread bekerja pada instance `Document` masing‑masing.
- **Version check:** Metode `setShowPercent` diperkenalkan di Aspose.Words 22.8. Jika Anda menggunakan versi lebih lama, tingkatkan atau hitung persentase secara manual dan atur sebagai label khusus.

---

## Ringkasan

Kami telah membahas **how to insert pie chart** ke dalam dokumen Word menggunakan Aspose.Words, menunjukkan cara **add data label percent**, dan mendemonstrasikan cara termudah untuk **display percentages on chart**. Dengan hanya beberapa baris Java Anda dapat **add pie chart to word** dan **show percent on pie chart**, mengubah angka mentah menjadi visual yang langsung dapat dibaca.

---

## Apa Selanjutnya?

- Bereksperimen dengan tipe chart lain (`BAR`, `LINE`, `AREA`) dan lihat bagaimana logika **add data label percent** yang sama diterapkan.
- Gabungkan chart dengan tabel untuk laporan yang lebih kaya—Aspose.Words memudahkan menempatkan chart di samping tabel data.
- Jelajahi mengekspor dokumen yang sama ke PDF atau HTML untuk melihat bagaimana persentase dirender di berbagai format.

Silakan ubah dimensi, warna, atau sumber data (mis., kueri basis data) dan saksikan laporan Word Anda menjadi hidup. Jika Anda mengalami masalah, tinggalkan komentar di bawah—selamat membuat chart!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Menyisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Menyisipkan Diagram Bubble di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}