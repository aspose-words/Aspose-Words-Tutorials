---
category: general
date: 2026-09-11
description: Cara mengedit diagram dalam dokumen Word dengan Java – pelajari cara
  memperbarui pengaturan diagram, mengaktifkan garis kisi diagram, mengubah opsi diagram,
  dan menyimpan dokumen yang telah diperbarui.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: id
lastmod: 2026-09-11
og_description: Cara mengedit grafik dalam dokumen Word dengan Java. Ikuti panduan
  ini untuk memperbarui pengaturan grafik, mengaktifkan garis kisi grafik, mengubah
  opsi grafik, dan menyimpan dokumen yang telah diperbarui.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Cara mengedit diagram dalam dokumen Word menggunakan Java – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Cara mengedit bagan dalam dokumen Word menggunakan Java
url: /id/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengedit diagram dalam dokumen Word menggunakan Java

Jika Anda perlu **cara mengedit diagram** dalam file Word, panduan ini menunjukkan langkah‑langkah tepatnya. Anda akan belajar cara memperbarui pengaturan diagram, mengaktifkan garis kisi diagram, mengubah opsi diagram, dan akhirnya **menyimpan dokumen yang diperbarui** tanpa kehilangan format apa pun.

Bekerja dengan diagram secara programatik sering terasa seperti operasi kotak hitam, terutama ketika Anda ingin menyesuaikan detail visual seperti graduasi atau garis kisi. Tutorial ini mencakup semua yang perlu Anda ketahui, mulai dari memuat dokumen hingga menyimpan perubahan. Tidak diperlukan alat eksternal—hanya pustaka Aspose.Words for Java (versi 24.9 atau lebih baru).

Pada akhir artikel ini Anda akan dapat:

* Memuat file `.docx` yang berisi diagram.
* Menemukan shape diagram dan mengubah propertinya.
* Mengaktifkan garis kisi diagram (graduasi) dan menyesuaikan opsi lainnya.
* **Menyimpan dokumen yang diperbarui** ke file baru.

## Prasyarat

* Java 17 atau yang lebih baru terpasang di mesin Anda.  
* Maven atau Gradle untuk mengelola dependensi.  
* Aspose.Words for Java 24.9+ (versi yang memperkenalkan `setShowGraduations`).  
* Dokumen Word (`input.docx`) yang sudah berisi setidaknya satu diagram.

Jika Anda belum familiar dengan Aspose.Words, anggaplah itu sebagai API lengkap yang memungkinkan Anda membaca, memodifikasi, dan menulis dokumen Word secara programatik—mirip dengan cara Anda memanipulasi DOM di peramban web.

## Langkah 1: Siapkan proyek dan impor pustaka

Buat proyek Maven baru atau tambahkan dependensi ke proyek yang sudah ada:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Tips profesional:** Gunakan rilis stabil terbaru untuk memastikan Anda memiliki metode `setShowGraduations`. Versi lama tidak akan dapat dikompilasi.

## Langkah 2: Muat dokumen Word yang berisi diagram

Tindakan pertama dalam alur kerja **cara mengedit diagram** apa pun adalah memuat file sumber. Aspose.Words merepresentasikan seluruh dokumen dengan kelas `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Objek `Document` memberi Anda akses ke setiap node di dalam file, termasuk shape, tabel, dan paragraf.

## Langkah 3: Temukan shape diagram pertama dalam dokumen

Diagram disimpan sebagai node `Shape` yang renderer‑nya adalah `Chart`. Untuk mengedit diagram, Anda harus terlebih dahulu mengambil node tersebut.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Jika dokumen berisi beberapa diagram, iterasi melalui `shapes` dan periksa `chartShape.getChart() != null` sebelum melakukan casting. Ini mencegah `ClassCastException` dan memastikan Anda **mengubah opsi diagram** hanya pada objek diagram yang valid.

## Langkah 4: Aktifkan garis kisi diagram (graduasi) – properti baru di versi 24.9

Properti `setShowGraduations` mengubah visibilitas garis kisi minor pada sumbu nilai. Mengaktifkannya sering meningkatkan keterbacaan untuk set data yang padat.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Mengapa ini penting:** Garis kisi memberikan referensi visual bagi penonton untuk setiap titik data, sehingga tren lebih mudah terlihat. Nilai default adalah `false`, jadi Anda harus secara eksplisit mengaktifkannya bila diperlukan.

Anda juga dapat menyesuaikan aspek lain, seperti garis kisi utama, judul sumbu, atau penempatan legenda. Di bawah ini contoh mengubah judul diagram dan posisi legenda—keduanya merupakan bagian dari **mengubah opsi diagram**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Langkah 5: Simpan dokumen dengan pengaturan diagram yang diperbarui

Setelah memodifikasi diagram, simpan perubahan. Langkah ini menyelesaikan fase **menyimpan dokumen yang diperbarui**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Menjalankan program akan menghasilkan `output.docx` di mana diagram kini menampilkan garis kisi, judul baru, dan legenda yang dipindahkan. Buka file tersebut di Microsoft Word untuk memverifikasi perubahan visual.

## Kode sumber lengkap (dapat dijalankan)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Hasil yang diharapkan

Saat Anda membuka `output.docx`:

* Diagram menampilkan garis kisi minor pada sumbu nilai.  
* Judul menampilkan **“Sales Overview 2026”**.  
* Legenda muncul di bagian bawah diagram.

Jika diagram asli sudah memiliki garis kisi, tampilan visual tetap tidak berubah, mengonfirmasi bahwa kode tersebut **idempotent**.

## Pertanyaan umum dan penanganan kasus tepi

### Bagaimana jika dokumen tidak memiliki diagram?

Mencoba melakukan casting pada shape yang bukan diagram akan melempar `ClassCastException`. Lindungi dari hal ini dengan memeriksa tipe shape:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Bagaimana cara mengedit diagram tertentu alih‑alih yang pertama?

Iterasi melalui `shapes` dan cocokkan judul yang diketahui atau pengidentifikasi alternatif:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Bisakah saya menonaktifkan kembali garis kisi nanti?

Ya, cukup set properti ke `false`:

```java
chart.setShowGraduations(false);
```

### Apakah ini bekerja dengan file `.doc` (biner)?

Aspose.Words mengabstraksi format file, sehingga kode yang sama bekerja untuk `.doc` dan `.docx`. Namun, beberapa fitur diagram terbaru (seperti graduasi) hanya disimpan dalam format OOXML, jadi Anda akan melihat efeknya hanya saat menyimpan sebagai `.docx`.

## Tips untuk kode siap produksi

* **Validasi jalur input** – gunakan `Files.exists(Paths.get(inputPath))` sebelum memuat.  
* **Bungkus panggilan API** dalam blok try‑catch untuk menampilkan detail `Exception`, terutama saat menangani dokumen yang rusak.  
* **Bebaskan sumber daya** – meskipun Aspose.Words mengelola memori, memanggil `doc.close()` (atau menggunakan try‑with‑resources bila tersedia) dapat membebaskan handle native lebih cepat.  
* **Pemeriksaan versi** – pastikan versi pustaka runtime ≥ 24.9 sebelum memanggil `setShowGraduations`. Anda dapat menanyakan `License.getVersion()` jika memerlukan guard programatik.

## Kesimpulan

Anda kini tahu **cara mengedit diagram** dalam dokumen Word menggunakan Java. Proses—memuat dokumen, menemukan diagram, mengaktifkan garis kisi diagram, mengubah opsi diagram, dan **menyimpan dokumen yang diperbarui**—mencakup skenario paling umum untuk manipulasi diagram secara programatik.

Dari sini Anda dapat menjelajahi kustomisasi tambahan seperti mengubah warna seri data, menerapkan gaya diagram, atau mengekspor diagram sebagai gambar. Setiap tugas tersebut mengikuti pola yang sama: ambil instance `Chart`, sesuaikan propertinya, dan **simpan dokumen yang diperbarui**.

Selamat coding, dan silakan bereksperimen dengan pengaturan diagram lainnya untuk menyesuaikan kebutuhan pelaporan Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cara menyimpan dokumen sebagai PDF dengan Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}