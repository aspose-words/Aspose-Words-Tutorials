---
category: general
date: 2026-09-11
description: Pelajari cara mengubah format catatan kaki di Java dengan Aspose.Words.
  Panduan ini menjelaskan cara mengedit catatan kaki, memperbarui gaya catatan kaki,
  dan memodifikasi pemisah catatan kaki.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: id
lastmod: 2026-09-11
og_description: Ubah format catatan kaki di Java dengan Aspose.Words. Ikuti panduan
  lengkap ini untuk mengedit catatan kaki, memperbarui gaya catatan kaki, dan memodifikasi
  pemisah catatan kaki.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Ubah format catatan kaki di Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Cara mengubah format catatan kaki dalam dokumen Word menggunakan Java
url: /id/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengubah format catatan kaki dalam dokumen Word menggunakan Java

Jika Anda perlu **mengubah format catatan kaki** dalam dokumen Word, tutorial ini akan memandu Anda melalui langkah‑langkah tepat menggunakan Aspose.Words for Java. Baik Anda sedang membangun pipeline penerbitan atau hanya perlu **cara mengedit tampilan catatan kaki** secara programatis, solusi di bawah ini mencakup semuanya mulai dari memuat file hingga menyimpan versi yang diperbarui.

Anda akan belajar cara **memperbarui gaya catatan kaki**, membuat pemisah catatan kaki menjadi tebal, dan bahkan **memodifikasi properti pemisah catatan kaki** seperti ukuran font atau warna. Panduan ini mengasumsikan Anda memiliki pengetahuan dasar Java dan lisensi Aspose.Words for Java yang aktif.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.  
* Aspose.Words for Java (versi 23.12 atau lebih baru) ditambahkan ke classpath proyek Anda.  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu catatan kaki.  
* IDE atau alat build (Maven/Gradle) untuk meng‑compile dan menjalankan kode.

Jika Anda belum yakin cara menambahkan Aspose.Words ke proyek Maven, sertakan dependensi berikut di `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Mengubah format catatan kaki dengan Aspose.Words for Java

Inti solusi adalah program Java singkat yang memuat dokumen, mengakses paragraf pemisah catatan kaki, mengubah formatnya, dan menyimpan hasilnya. Kode ini sepenuhnya mandiri, sehingga Anda dapat menyalinnya ke kelas baru dan menjalankannya langsung.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Mengapa setiap langkah penting

* **Memuat dokumen** (`new Document`) membuat representasi dalam memori yang dapat dimanipulasi oleh Aspose.Words.  
* **Mengambil pemisah catatan kaki** (`getFootnoteSeparator`) memberi Anda akses langsung ke paragraf yang memisahkan catatan kaki dari teks utama. Inilah elemen yang harus Anda targetkan ketika ingin **mengubah format catatan kaki**.  
* **Memformat run** (`setBold`, `setItalic`, `setSize`, `setColor`) menunjukkan cara **memodifikasi pemisah catatan kaki**. Anda dapat menambahkan atribut font tambahan di sini, seperti underline atau highlight, untuk mengontrol tampilan sepenuhnya.  
* **Menyimpan dokumen** menuliskan perubahan kembali ke disk, menghasilkan file baru (`output.docx`) yang mencerminkan gaya catatan kaki yang diperbarui.

> **Pro tip:** Jika dokumen sumber Anda menggunakan pemisah catatan kaki khusus yang berisi beberapa run (misalnya kombinasi simbol), lakukan loop melalui `footnoteSeparator.getRuns()` dan terapkan pengaturan `Font` yang sama pada setiap run untuk styling yang konsisten.

## Cara mengedit pemisah catatan kaki secara programatis

Kadang‑kadang Anda perlu mengedit tidak hanya pemisah tetapi juga teks catatan kaki itu sendiri. API yang sama dapat digunakan untuk mengakses setiap catatan kaki, menyesuaikan format paragrafnya, atau mengubah gaya penomoran.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

Potongan kode di atas menunjukkan **cara mengedit isi catatan kaki** setelah Anda **mengubah format catatan kaki** untuk pemisah. Dengan mengiterasi `doc.getFootnotes()`, Anda memastikan setiap catatan kaki mewarisi gaya yang sama, yang penting untuk dokumen yang tampak profesional.

## Memperbarui gaya catatan kaki untuk tampilan dokumen yang konsisten

Jika Anda lebih suka bekerja dengan gaya daripada run individual, Aspose.Words memungkinkan Anda membuat atau memodifikasi objek `Style` lalu menerapkannya ke catatan kaki dan pemisah. Pendekatan ini berguna ketika Anda perlu **memperbarui gaya catatan kaki** di banyak dokumen.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Menggunakan gaya khusus memudahkan pemeliharaan di masa depan—ubah gaya sekali, dan semua catatan kaki serta pemisah akan otomatis terupdate. Teknik ini merupakan cara yang direkomendasikan untuk **memperbarui gaya catatan kaki** dalam alur kerja penerbitan berskala besar.

## Memodifikasi pemisah catatan kaki agar sesuai dengan branding Anda

Pedoman merek terkadang mengharuskan pemisah catatan kaki menggunakan karakter tertentu (misalnya asterisk) atau garis khusus. Aspose.Words memungkinkan Anda mengganti seluruh konten pemisah default.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

Kode di atas **memodifikasi pemisah catatan kaki** dengan menghapus semua run yang ada dan menyisipkan run baru berisi teks serta format yang diinginkan. Anda juga dapat menggunakan karakter Unicode seperti `\u2022` (bullet) atau `\u2014` (em dash) untuk mencapai efek visual yang tepat sesuai merek Anda.

## Hasil yang diharapkan

Setelah menjalankan program:

* Pemisah catatan kaki di `output.docx` muncul **tebal**, **miring**, 10 pt, dan abu‑abu (atau warna apa pun yang Anda tentukan).  
* Semua paragraf catatan kaki mengadopsi gaya yang Anda definisikan, memastikan tampilan seragam di seluruh dokumen.  
* Jika Anda mengganti teks pemisah, garis khusus baru terlihat tepat di tempat garis asli sebelumnya.

Buka file hasilnya di Microsoft Word atau LibreOffice Writer untuk memverifikasi perubahan. Anda seharusnya melihat pemisah yang diperbarui tepat di atas catatan kaki pertama, dan teks catatan kaki mencerminkan semua modifikasi gaya yang Anda terapkan.

## Kesalahan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` melempar pengecualian | Beberapa dokumen memiliki paragraf pemisah yang kosong. | Tambahkan pemeriksaan defensif dan buat run jika tidak ada (lihat contoh kode). |
| Perubahan font tidak terlihat | Dokumen menggunakan tema yang menimpa format langsung. | Set `font.setThemeFont(null)` atau terapkan gaya khusus alih‑alih format langsung. |
| File yang disimpan tidak mencerminkan perubahan | File asli masih terbuka di Word, mengunci jalur output. | Tutup semua instance file sebelum menjalankan program, atau |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Pemrosesan Kata dengan Catatan Kaki dan Catatan Akhir](/words/english/net/working-with-footnote-and-endnote/)
- [Atur Posisi Catatan Kaki dan Catatan Akhir](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Cara Menampilkan Info Versi Aspose.Words di Java: Panduan Komprehensif](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}