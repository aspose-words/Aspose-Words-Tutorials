---
category: general
date: 2026-10-10
description: Terapkan catatan kaki dengan gaya heading dalam dokumen Word menggunakan
  Aspose.Words untuk Java – panduan lengkap langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply heading style footnotes
- footnote separator
- endnote separator
- Aspose.Words for Java
- style identifier
language: id
lastmod: 2026-10-10
og_description: Terapkan catatan kaki dengan gaya heading dalam dokumen Word menggunakan
  Aspose.Words untuk Java. Pelajari cara menata pemisah catatan kaki dan catatan akhir
  dalam hitungan menit.
og_image_alt: Document after applying heading style footnotes to footnote and endnote
  separators
og_title: Terapkan catatan kaki dengan gaya heading menggunakan Aspose.Words untuk
  Java – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Apply heading style footnotes in a Word document using Aspose.Words
    for Java – a complete step‑by‑step guide.
  headline: Apply heading style footnotes with Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word processing
- Document styling
title: Terapkan catatan kaki gaya heading dengan Aspose.Words untuk Java
url: /id/java/annotations-comments/apply-heading-style-footnotes-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Terapkan catatan kaki gaya heading dengan Aspose.Words untuk Java

Jika Anda perlu **menerapkan catatan kaki gaya heading** dalam dokumen Word, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk Java. Anda akan melihat contoh lengkap yang dapat dijalankan yang memberi gaya pada pemisah catatan kaki dan pemisah catatan akhir menggunakan gaya heading bawaan.

Memberi gaya pada pemisah catatan kaki dan catatan akhir membuat dokumen lebih mudah dibaca dan memberikan format yang konsisten di seluruh naskah besar. Panduan ini juga mencakup jebakan umum, seperti memastikan `StyleIdentifier` yang tepat digunakan dan menangani dokumen yang sudah berisi pemisah khusus.

## Apa yang akan Anda pelajari

* Cara memuat file `.docx` yang berisi catatan kaki dan catatan akhir.  
* Cara mengambil paragraf **pemisa catatan kaki** dan mengatur gayanya menjadi `HEADING_2`.  
* Cara mengambil paragraf **pemisa catatan akhir** dan mengatur gayanya menjadi `HEADING_3`.  
* Cara menyimpan dokumen yang telah dimodifikasi dan memverifikasi perubahan.  

**Prasyarat**

* Java 17 atau lebih baru.  
* Aspose.Words untuk Java 23.12 (atau versi terbaru).  
* Familiaritas dasar dengan konsep pengolahan Word (catatan kaki, catatan akhir, gaya).

---

## Terapkan catatan kaki gaya heading – ikhtisar

Ide dasarnya adalah menggunakan metode `Document.getFootnoteSeparator()` dan `Document.getEndnoteSeparator()` dari Aspose.Words. Kedua metode mengembalikan objek `Paragraph` yang mewakili garis pemisah tersembunyi antara teks utama dan area catatan kaki/catatan akhir. Dengan mengubah `ParagraphFormat` paragraf dan menetapkan `StyleIdentifier`, Anda secara efektif **menerapkan catatan kaki gaya heading** tanpa harus mengedit UI Word secara manual.

---

## Langkah 1: Siapkan proyek

Buat proyek Maven (atau Gradle) dan tambahkan dependensi Aspose.Words untuk Java:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** Gunakan versi terbaru untuk mendapatkan perbaikan bug terkait enumerasi `StyleIdentifier`.

---

## Langkah 2: Muat dokumen sumber

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // Load a Word document that already contains footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");
        // From here we will manipulate the footnote and endnote separators.
```

*Konstruktor `Document` membaca file ke memori, memberi Anda akses programatik penuh.*  

---

## Langkah 3: Beri gaya pada pemisah catatan kaki

```java
        // Retrieve the hidden paragraph that separates footnotes from the main text.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();

        // Apply the built‑in Heading 2 style to this separator.
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);
```

Mengapa `HEADING_2`? Gaya heading mewarisi ukuran font, warna, dan spasi, yang membuat pemisah terlihat berbeda secara visual sambil tetap mengikuti hierarki gaya dokumen.

---

## Langkah 4: Beri gaya pada pemisah catatan akhir

```java
        // Retrieve the hidden paragraph that separates endnotes.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();

        // Apply the built‑in Heading 3 style to this separator.
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);
```

Menggunakan `HEADING_3` menjaga bobot visual lebih rendah dibandingkan pemisah catatan kaki, sesuai konvensi format akademik umum.

---

## Langkah 5: Simpan dokumen yang telah dimodifikasi

```java
        // Persist the changes to a new file.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

Setelah menjalankan program, buka `FootnoteStyled.docx` di Microsoft Word. Anda akan melihat:

* Pemisah catatan kaki kini muncul dengan format **Heading 2** (font lebih besar, tebal secara default).  
* Pemisah catatan akhir mencerminkan **Heading 3** (sedikit lebih kecil, tetap tebal).  

Perubahan ini diterapkan secara otomatis ke setiap catatan kaki dan catatan akhir dalam dokumen, bahkan jika yang baru ditambahkan kemudian.

---

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika dokumen sudah menggunakan gaya khusus untuk pemisah?** | Menimpa `StyleIdentifier` akan menggantikan gaya yang ada. Jika Anda perlu mempertahankan format khusus, kloning gaya asli, modifikasi, lalu tetapkan identifier klon tersebut. |
| **Bisakah saya menggunakan gaya khusus alih-alih heading bawaan?** | Ya. Buat gaya khusus dengan `document.getStyles().add(StyleIdentifier.CUSTOM)`, konfigurasikan atributnya, lalu tetapkan identifier gaya tersebut ke paragraf pemisah. |
| **Apakah ini akan bekerja dengan file `.doc` (biner)?** | Tentu saja. Aspose.Words mengabstraksi format file, sehingga kode yang sama bekerja untuk `.doc` dan `.docx`. |
| **Apakah ada dampak kinerja pada dokumen besar?** | Operasi bersifat O(1) karena menargetkan satu paragraf tersembunyi; bahkan dokumen 500 halaman diproses dalam hitungan milidetik. |

---

## Kode sumber lengkap (dapat dijalankan)

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document containing footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2️⃣ Retrieve the footnote separator and apply Heading 2.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);

        // 3️⃣ Retrieve the endnote separator and apply Heading 3.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);

        // 4️⃣ Save the modified document.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

**Output yang diharapkan** (konsol):

```
Document saved with styled footnote and endnote separators.
```

Buka file yang disimpan untuk melihat pemisah yang telah diberi gaya.

---

## Kesimpulan

Anda kini tahu cara **menerapkan catatan kaki gaya heading** dalam dokumen Word menggunakan Aspose.Words untuk Java. Dengan mengambil paragraf **pemisa catatan kaki** dan **pemisa catatan akhir** serta menetapkan nilai `StyleIdentifier` yang tepat, Anda memperoleh format yang konsisten dan profesional dengan hanya beberapa baris kode.

Langkah selanjutnya yang dapat Anda pertimbangkan:

* Bereksperimen dengan gaya khusus alih-alih heading bawaan.  
* Mengotomatiskan perubahan gaya pada sekumpulan dokumen menggunakan pendekatan yang sama.  
* Menggabungkan teknik ini dengan API `Document` lainnya, seperti `getFootnoteOptions()` untuk penomoran catatan kaki yang lebih halus.

Silakan sesuaikan kode untuk alur kerja penerbitan Anda sendiri, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menggunakan Catatan Kaki dan Catatan Akhir di Aspose.Words untuk Java](/words/english/java/using-document-elements/using-footnotes-and-endnotes/)
- [Simpan Word sebagai PDF dengan Aspose.Words – Panduan Langkah‑per‑Langkah Java](/words/english/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Ekspor Word ke Markdown – Panduan Java menggunakan Aspose.Words](/words/english/java/document-conversion-and-export/export-word-to-markdown-java-guide-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}