---
category: general
date: 2026-07-16
description: Buat diagram lingkaran di Java menggunakan Aspose.Words. Pelajari cara
  menambahkan garis penghubung, menampilkan legenda diagram, dan memisahkan potongan
  dalam satu tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: id
lastmod: 2026-07-16
og_description: Buat diagram lingkaran di Java menggunakan Aspose.Words. Panduan ini
  menunjukkan cara menambahkan garis penunjuk, menampilkan legenda diagram, dan memisahkan
  irisan, memberikan visual yang rapi dalam hitungan menit.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Buat Diagram Lingkaran dengan Aspose.Words Java – Tutorial Pemformatan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Membuat Diagram Lingkaran dengan Aspose.Words Java – Panduan Langkah-demi-Langkah
  Lengkap
url: /id/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Diagram Pai dengan Aspose.Words Java – Panduan Lengkap Langkah‑per‑Langkah

Pernah bertanya-tanya bagaimana cara **membuat diagram pai** secara programatis di Java tanpa berurusan dengan API menggambar tingkat‑rendah? Anda bukan satu‑satunya. Banyak pengembang membutuhkan visual cepat untuk laporan, dasbor, atau dokumen otomatis, dan mereka menggunakan Aspose.Words karena menangani pekerjaan berat.  

Dalam tutorial ini kami akan menelusuri contoh lengkap yang siap‑jalankan yang tidak hanya **membuat diagram pai** tetapi juga menunjukkan cara **menambahkan garis pemimpin**, **menampilkan legenda diagram**, dan bahkan **meletuskan sebuah irisan** untuk penekanan. Pada akhir tutorial Anda akan memiliki file `.docx` yang tampak rapi cukup untuk mengesankan klien.

> **Quick win:** Potongan kode di bawah ini langsung dapat digunakan dengan Aspose.Words for Java 23.9 (atau versi yang lebih baru). Tidak ada dependensi tambahan, hanya JAR‑nya.

## Apa yang Akan Anda Pelajari

- Menyiapkan dokumen Word kosong dengan `DocumentBuilder`.
- Menyisipkan **diagram pai** dengan ukuran khusus.
- Menggunakan fitur **meletuskan irisan** untuk menyoroti titik data.
- Mengaktifkan **garis pemimpin** agar irisan yang meletus tetap terhubung ke label.
- Mengaktifkan **legenda diagram** sehingga pembaca dapat langsung mengidentifikasi setiap irisan.
- Menyimpan hasil ke file `.docx` yang dapat dibuka di Microsoft Word atau LibreOffice.

**Prasyarat** – Anda memerlukan:

1. Java 17 (atau lebih baru) terpasang.
2. Aspose.Words for Java JAR di classpath Anda.
3. IDE atau editor teks dasar—IntelliJ IDEA, Eclipse, VS Code, apa saja yang Anda sukai.

Sekarang, mari kita mulai.

## Langkah 1: Inisialisasi Dokumen dan Builder – Menyiapkan untuk **membuat diagram pai**

Pertama, kita memerlukan kanvas dokumen yang bersih. `Document` mewakili seluruh file Word, sementara `DocumentBuilder` adalah pembantu yang memungkinkan kita menambahkan konten.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Mengapa ini penting:** Memulai dengan `Document` yang baru menjamin tidak ada gaya tersembunyi atau objek yang tertinggal yang dapat mengganggu proses rendering diagram.

## Langkah 2: Sisipkan **diagram pai** – Ukuran penting

Aspose.Words membuat penyisipan diagram menjadi satu baris kode. Di sini kami meminta diagram pai berukuran 400 × 300 poin—sekitar 5,5 × 4,2 inci pada layar tipikal.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Jika Anda memerlukan ukuran berbeda, cukup ubah dua argumen numerik tersebut. API bekerja dalam poin, di mana 72 poin = 1 inci.

## Langkah 3: **Cara meletuskan irisan** – Menekankan titik data kunci

Meletuskan sebuah irisan menariknya keluar dari sisa pai, menarik perhatian pembaca. Metode `setExplosion` menerima integer yang mewakili jarak dalam poin.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Bagaimana jika Anda memiliki beberapa seri?** Anda dapat memanggil `setExplosion` pada indeks seri mana pun (`get(1)`, `get(2)`, …) untuk meletuskan irisan yang berbeda.

## Langkah 4: **Tambahkan garis pemimpin** dan **tampilkan legenda diagram** – Menghubungkan titik‑titik

Ketika sebuah irisan meletus, labelnya dapat menjauh. Garis pemimpin menjaga label tetap terikat, mempertahankan keterbacaan. Pada saat yang sama, legenda memberikan kunci cepat untuk semua irisan.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Mengapa mengaktifkan garis pemimpin?** Tanpa garis pemimpin, label mungkin tampak mengambang, membingungkan pengguna tentang irisan mana yang menjadi miliknya.  
> **Butuh posisi legenda khusus?** Gunakan `chart.getLegend().setPosition(LegendPosition.TOP)` atau nilai enum lainnya.

## Langkah 5: Simpan Dokumen – Langkah akhir **membuat diagram pai**

Akhirnya, kami menyimpan dokumen ke disk. Sesuaikan jalur ke folder yang Anda miliki hak menulis.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Jalankan program, buka `PieChartDemo.docx` yang dihasilkan, dan Anda akan melihat diagram pai yang diformat dengan baik, irisan pertama yang meletus, garis pemimpin, dan legenda yang terlihat.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Contoh membuat diagram pai dengan irisan yang meletus, garis pemimpin, dan legenda"}

### Output yang Diharapkan

Saat Anda membuka file Word, diagram akan terlihat kira‑kira seperti ini:

- Diagram pai berukuran 400 × 300 pt.
- Irisan pertama dipindahkan sejauh 10 pt.
- Garis pemimpin tipis menghubungkan irisan yang meletus ke labelnya.
- Legenda di bawah diagram mencantumkan nama setiap seri.

Jika Anda tidak melihat garis pemimpin, periksa kembali bahwa `setLeaderLines(true)` dipanggil *setelah* pengaturan ledakan—urutan penting.

## Kesulitan Umum dan Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Tidak ada legenda muncul** | `setShowLegend(true)` tidak dipanggil atau dipanggil pada objek diagram yang salah. | Pastikan Anda memanggil `chart.setShowLegend(true)` **setelah** mengambil `Chart` dari shape. |
| **Garis pemimpin hilang** | Irisan tidak meletus, atau tipe diagram tidak mendukung garis pemimpin. | Hanya `ChartType.PIE` (atau `PIE_3D`) yang mendukung garis pemimpin. Panggil `setExplosion` terlebih dahulu, lalu `setLeaderLines(true)`. |
| **Irisan tidak bergerak** | Nilai ledakan terlalu rendah (0‑2 pt). | Tingkatkan nilai integer, misalnya `setExplosion(10)` atau lebih tinggi untuk efek yang lebih dramatis. |
| **Diagram terlihat terdistorsi** | Menggunakan ukuran yang tidak persegi (lebar ≠ tinggi) dapat memampatkan pai. | Jaga lebar dan tinggi sama atau hampir sama; 400 × 300 berfungsi tetapi 400 × 400 memberikan lingkaran yang sempurna. |

## Penyesuaian Lanjutan (Opsional)

Jika Anda ingin melampaui dasar, pertimbangkan:

- **Warna khusus**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Label data**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Efek 3‑D**: Ganti `ChartType.PIE` dengan `ChartType.PIE_3D`.

Opsi‑opsi ini memungkinkan Anda menyesuaikan visual agar sesuai dengan pedoman merek perusahaan.

## Ringkasan – Apa yang Telah Kami Capai

Kami memulai dengan dokumen Word kosong, **membuat diagram pai**, **meletuskan irisan pertama**, **menambahkan garis pemimpin**, dan **menampilkan legenda diagram**. Seluruh alur masuk dalam metode `main` yang ringkas, memudahkan penyisipan ke dalam pipeline pelaporan yang lebih besar.

## Langkah Selanjutnya

- **Tambahkan lebih banyak seri**: Isi diagram dengan data nyata dari basis data atau CSV.
- **Ekspor ke PDF**: Gunakan `doc.save("output.pdf", SaveFormat.PDF);` untuk menghasilkan versi PDF.
- **Gabungkan dengan bentuk lain**: Sisipkan tabel, gambar, atau diagram tambahan untuk laporan lengkap.

Jika Anda penasaran dengan tipe diagram lain—kolom, batang, garis—cukup ganti `ChartType.PIE` dengan enum yang sesuai dan ikuti langkah pemformatan yang sama.

---

*Selamat membuat diagram!* Jangan ragu meninggalkan komentar jika ada yang tidak berjalan seperti yang diharapkan, atau bagikan cara Anda menyesuaikan posisi legenda. Masukan Anda membantu kami semua membangun dokumen otomatis yang lebih baik.

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat dan membangun atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cara Membuat Dokumen PDF dengan Aspose.Words untuk Java | API Pemrosesan Dokumen](/words/english/java/)
- [Cara Menambahkan Watermark ke Dokumen Menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}