---
category: general
date: 2026-07-20
description: Ubah jarak catatan kaki dalam file DOCX dengan mudah. Pelajari cara mengatur
  jarak, menyesuaikan pemisah catatan kaki, dan mengatur jarak baris paragraf dengan
  Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: id
lastmod: 2026-07-20
og_description: Ubah jarak catatan kaki dalam file DOCX dengan cepat. Panduan ini
  menunjukkan cara mengatur jarak, menyesuaikan pemisah catatan kaki, dan menyesuaikan
  jarak baris paragraf di Java.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Ubah Jarak Catatan Kaki di DOCX – Panduan Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Ubah jarak catatan kaki di DOCX – Panduan Lengkap
url: /id/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengubah Jarak Catatan Kaki di DOCX – Panduan Lengkap

Pernah perlu **mengubah jarak catatan kaki** dalam dokumen Word tetapi tidak tahu harus mulai dari mana? Anda tidak sendirian. Baik Anda sedang memoles tesis atau menyempurnakan kontrak, menyesuaikan pemisah catatan kaki dengan tepat dapat membuat perbedaan besar.  

Dalam tutorial ini kami akan membahas **cara mengatur jarak**, menyesuaikan pemisah catatan kaki, dan **mengatur jarak baris paragraf** menggunakan pustaka berbasis Java. Pada akhir tutorial Anda akan memiliki contoh siap‑jalankan yang dapat Anda masukkan ke proyek mana pun.

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki:

- Java 17 atau yang lebih baru (kode menggunakan fitur bahasa modern)
- Maven atau Gradle untuk manajemen dependensi
- File DOCX dengan setidaknya satu catatan kaki (atau Anda dapat membuatnya secara manual)
- Pustaka **Aspose.Words for Java** (atau API kompatibel apa pun; kami akan menggunakan Aspose dalam contoh)

Itu saja—tanpa kerangka kerja berat, hanya Java biasa dan satu pustaka.

![Change footnote spacing in DOCX example](/images/footnote-spacing.png){alt="Contoh mengubah jarak catatan kaki di DOCX"}

## Langkah 1: Muat Dokumen DOCX (Ubah jarak catatan kaki)

Hal pertama yang harus Anda lakukan adalah membuka file Word. Ini memberi Anda objek `Document` yang dapat dimanipulasi.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Mengapa ini penting*: Memuat dokumen adalah titik masuk untuk **mengubah jarak catatan kaki**. Tanpa instance `Document` Anda tidak dapat mengakses pemisah catatan kaki atau format paragraf apa pun.

## Langkah 2: Ambil dan Sesuaikan Pemisah Catatan Kaki (Sesuaikan pemisah catatan kaki)

Pemisah catatan kaki adalah paragraf tersembunyi yang berada di antara teks utama dan daftar catatan kaki. Untuk mengubah jarak barisnya, Anda perlu mengambil paragraf tersebut dan menyesuaikan formatnya.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Bagaimana ini menyelesaikan masalah

- **Ambil pemisah catatan kaki** – inilah bagian yang sebenarnya ingin Anda ubah, memenuhi kebutuhan *menyesuaikan pemisah catatan kaki*.
- **Atur jarak baris** – `setLineSpacing(12.0)` secara langsung menjawab *cara mengatur jarak* untuk paragraf tersembunyi tersebut.
- **Penanganan kasus tepi** – jika dokumen tidak memiliki pemisah, kami membuatnya secara dinamis, mencegah `NullPointerException`.

## Langkah 3: Verifikasi Perubahan dan Simpan (Atur jarak baris paragraf)

Setelah Anda mengubah pemisah, Anda ingin memastikan perubahan tersebut tersimpan. Membuka file yang disimpan di Word akan menampilkan jarak baru, tetapi Anda juga dapat memeriksanya secara programatis.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Tambahkan pemanggilan `verifySpacing(doc);` tepat sebelum `doc.save(...)` di `main`. Saat Anda menjalankan program, Anda akan melihat:

```
Current footnote separator line spacing: 12.0
```

Itu mengonfirmasi operasi **mengubah jarak baris docx** berhasil.

## Kesalahan Umum & Tips Pro

- **Kesalahan**: Menggunakan `setLineSpacing` dengan nilai yang tampak “12” tetapi diinterpretasikan sebagai “12 pts” vs “12 lines”. Aspose mengharapkan poin, jadi 12 berarti 12 pt. Untuk jarak ganda gunakan `24.0`.
- **Tips pro**: Jika Anda memerlukan tampilan konsisten di semua tipe catatan kaki (pemisah, pemisah lanjutan, dll.), ulangi langkah yang sama untuk `doc.getFootnoteContinuationSeparator()` dan `doc.getFootnoteContinuationNotice()`.
- **Kesalahan**: Lupa memanggil `save()` setelah melakukan modifikasi. Dokumen di memori berubah, tetapi file di disk tetap sama.
- **Tips pro**: Gabungkan perubahan jarak dengan pembaruan gaya (`ParagraphStyle`) untuk bagian catatan kaki yang benar‑benar dipoles.

## Contoh Lengkap yang Berfungsi (Semua Langkah dalam Satu File)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Salin kode di atas ke kelas Java baru, tambahkan dependensi Maven Aspose.Words, dan jalankan. `output.docx` Anda kini memiliki jarak baris pemisah catatan kaki yang disetel ke **12 pt**, secara efektif **mengubah jarak catatan kaki**.

### Dependensi Maven

Tambahkan potongan berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Jika Anda lebih suka Gradle, ekuivalennya adalah:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Kesimpulan

Anda baru saja mempelajari cara **mengubah jarak catatan kaki** dalam file DOCX menggunakan Java. Dengan memuat dokumen, mengambil **pemisah catatan kaki**, dan menerapkan **set paragraph line spacing**, Anda mendapatkan kontrol presisi atas tampilan catatan kaki.  

Selanjutnya Anda dapat menjelajahi penyesuaian terkait, seperti mengubah gaya teks catatan kaki, menambahkan pemisah khusus, atau bahkan mengotomatisasi pembaruan massal pada banyak dokumen.  

Punya pertanyaan lebih lanjut tentang **menyesuaikan pemisah catatan kaki** atau tugas otomatisasi Word lainnya? Tinggalkan komentar, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Ubah Jarak dan Inden Paragraf Asia di Dokumen Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ubah Jarak dan Inden Paragraf Asia](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ubah Jarak dan Inden Paragraf Asia](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}