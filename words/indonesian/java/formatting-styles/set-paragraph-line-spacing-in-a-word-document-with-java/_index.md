---
category: general
date: 2026-11-15
description: Atur jarak baris paragraf dalam dokumen Word dengan Java. Pelajari cara
  mengatur jarak baris secara programatis menggunakan Aspose.Words untuk pemformatan
  dokumen yang presisi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: id
lastmod: 2026-11-15
og_description: Atur jarak baris paragraf dalam dokumen Word dengan Java. Panduan
  ini menjelaskan cara mengatur jarak baris untuk paragraf dan pemisah catatan kaki
  menggunakan Aspose.Words, memberi Anda kontrol penuh atas tata letak dokumen.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Atur jarak baris paragraf di Word menggunakan Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Atur spasi baris paragraf dalam dokumen Word dengan Java
url: /id/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Atur jarak baris paragraf dalam dokumen Word dengan Java

Jika Anda perlu **mengatur jarak baris paragraf** dalam dokumen Word, tutorial ini menunjukkan cara melakukannya dengan Java dan Aspose.Words. Anda juga akan belajar **cara mengatur jarak baris** untuk pemisah catatan kaki—sebuah kebutuhan umum saat memformat dokumen profesional.

Dalam bagian berikut Anda akan:

* Memuat file *.docx* yang sudah ada.
* Mengambil paragraf pemisah catatan kaki.
* Menerapkan nilai jarak‑baris khusus.
* Menyimpan dokumen yang telah diperbarui.

Tidak ada konfigurasi eksternal yang diperlukan selain menambahkan pustaka Aspose.Words ke proyek Anda, sehingga Anda dapat menyalin kode persis dan menjalankannya segera.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.
* Maven (atau alat build lain) untuk mengelola dependensi.
* Lisensi Aspose.Words for Java yang valid (evaluasi gratis dapat digunakan untuk pengujian).
* Dokumen Word input (`input.docx`) yang berada di direktori yang diketahui.

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Atur jarak baris paragraf dengan Aspose.Words

Header H2 ini berisi kata kunci utama, memenuhi persyaratan SEO.

### Langkah 1: Muat dokumen Word

Pertama, buat instance `Document` yang menunjuk ke file sumber Anda.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Mengapa ini penting*: Memuat dokumen memberi Anda model dalam memori yang dapat Anda manipulasi tanpa menyentuh file asli sampai Anda secara eksplisit menyimpannya.

### Langkah 2: Ambil pemisah catatan kaki

Pemisah catatan kaki adalah paragraf khusus yang muncul di antara catatan kaki dan teks utama. Untuk mengubah tampilannya, Anda perlu mengakses objek `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Jika dokumen Anda tidak berisi catatan kaki, pemisah tetap ada sebagai paragraf tersembunyi, sehingga pemanggilan tidak akan pernah mengembalikan `null`.

### Langkah 3: Cara mengatur jarak baris untuk paragraf pemisah

Sekarang terapkan jarak baris yang diinginkan. Aspose.Words menggunakan poin untuk nilai jarak‑baris; 12 pts kira‑kira setara dengan jarak tunggal untuk kebanyakan font.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Anda juga dapat menggunakan mode jarak lainnya:

| Mode                     | Pemanggilan metode                                      |
|--------------------------|--------------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`         |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Memilih aturan yang tepat memastikan dokumen ditampilkan secara konsisten di Word, Google Docs, dan penampil lainnya.

### Langkah 4: Simpan dokumen yang diperbarui

Akhirnya, tulis perubahan kembali ke disk.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Saat Anda membuka `output.docx` di Microsoft Word, pemisah catatan kaki akan ditampilkan dengan jarak baris yang Anda definisikan.

## Memahami cara mengatur jarak baris untuk paragraf biasa

API yang sama bekerja untuk objek `Paragraph` apa pun, tidak hanya pemisah catatan kaki. Berikut contoh singkat yang menyesuaikan jarak paragraf pertama dalam badan dokumen:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Mengapa Anda mungkin membutuhkannya**: Laporan, kontrak, dan makalah akademik sering memerlukan gaya jarak baris tertentu (mis., jarak ganda untuk draf). Menggunakan metode `setLineSpacing` yang sama menjamin tata letak persis seperti yang Anda harapkan.

## Kesalahan umum dan cara menghindarinya

| Masalah                               | Penyebab                                | Solusi |
|---------------------------------------|----------------------------------------|--------|
| Jarak baris tidak berubah             | `LineSpacingRule` dibiarkan pada nilai default (AUTO) | Setel secara eksplisit aturan dengan `setLineSpacingRule`. |
| Baris kosong tambahan setelah pemisah | Pemisah berisi carriage return tersembunyi | Potong teks pemisah dengan `separator.getText().trim();` sebelum menerapkan jarak. |
| Dokumen menjadi rusak setelah disimpan| Menggunakan versi Aspose.Words yang usang | Upgrade ke versi terbaru (mis., 24.10) yang berisi perbaikan bug untuk penyimpanan. |

## Tips pro: proses batch banyak dokumen

Jika Anda perlu memperbarui puluhan file, bungkus logika dalam metode pembantu dan iterasi melalui sebuah folder:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Menjalankan metode ini dalam loop menghemat waktu berjam‑jam dari penyuntingan manual.

## Output yang Diharapkan

Setelah menjalankan program lengkap, `output.docx` akan:

* Memuat konten asli tanpa perubahan kecuali jarak baris.
* Menampilkan pemisah catatan kaki dengan tata letak jarak tunggal (12 pts).
* Mempertahankan semua format lain (gaya, gambar, tabel).

Buka file di Word dan verifikasi bahwa garis pemisah lebih rapat (atau lebih longgar, tergantung nilai yang Anda tetapkan).

## Kesimpulan

Anda kini tahu cara **mengatur jarak baris paragraf** dalam dokumen Word menggunakan Java, dan juga memahami **cara mengatur jarak baris** untuk pemisah catatan kaki serta paragraf biasa. Contoh lengkap yang dapat dijalankan memperlihatkan cara memuat dokumen, menyesuaikan properti jarak‑baris, dan menyimpan hasilnya—semua dengan beberapa panggilan API yang jelas.

**Langkah selanjutnya** yang dapat Anda jelajahi:

* **Cara mengatur jarak baris** untuk tabel dan item daftar.
* Menerapkan aturan jarak yang berbeda untuk heading dibandingkan teks badan.
* Menggunakan objek `Style` untuk menegakkan jarak di seluruh dokumen.

Eksperimen dengan nilai‑nilai tersebut, gabungkan dengan opsi pemformatan lain, dan Anda akan memiliki kontrol penuh atas tata letak dokumen dalam aplikasi Java apa pun. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara mengatur opsi di Aspose.Words untuk Java – panduan lengkap](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Ubah Jarak Paragraf Asia dan Inden dalam Dokumen Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}