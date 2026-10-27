---
category: general
date: 2026-08-07
description: Cara mengedit catatan kaki di Java dengan Aspose.Words – menambahkan
  tanda hubung khusus, mengubah garis catatan kaki, dan mengatur perataan paragraf
  untuk dokumen yang rapi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: id
lastmod: 2026-08-07
og_description: Cara mengedit catatan kaki di Java dengan Aspose.Words. Pelajari cara
  menambahkan tanda hubung khusus, mengubah garis catatan kaki, dan mengatur perataan
  paragraf hanya dalam beberapa langkah.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Cara mengedit catatan kaki di Java – tambahkan tanda hubung, ubah baris,
  atur perataan
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Cara mengedit catatan kaki di Java dengan Aspose.Words
url: /id/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengedit catatan kaki di Java dengan Aspose.Words

Jika Anda perlu **cara mengedit catatan kaki** dalam dokumen Word menggunakan Java, panduan ini menunjukkan alur kerja lengkap. Anda akan belajar menambahkan dash khusus, mengubah garis catatan kaki, dan mengatur perataan paragraf sehingga pemisah catatan kaki terlihat profesional.

Mengedit catatan kaki adalah kebutuhan umum saat menyiapkan kontrak hukum, makalah akademik, atau brosur pemasaran. Langkah‑langkah di bawah ini mencakup semua yang Anda perlukan—dari memuat dokumen hingga menyimpan file akhir—tanpa memerlukan alat tambahan.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.
* Aspose.Words for Java (versi terbaru) ditambahkan ke classpath proyek Anda.
* File DOCX (`input.docx`) yang berisi setidaknya satu catatan kaki.

Item‑item ini menjamin kode dapat dijalankan tanpa error runtime.

## Cara mengedit pemisah catatan kaki dan garis

Pemisah catatan kaki adalah paragraf yang muncul antara teks utama dan daftar catatan kaki. Mengubah tampilannya meningkatkan keterbacaan dan menyesuaikan dengan branding perusahaan.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Mengapa setiap baris penting

1. **Memuat dokumen** – `new Document(...)` membaca file DOCX ke memori, memberi Anda akses ke semua node‑nya.  
2. **Mengambil pemisah** – `getFootnoteSeparator()` mengembalikan paragraf khusus yang diperlakukan Aspose.Words sebagai garis catatan kaki. Objek ini adalah satu‑satunya tempat yang aman untuk memodifikasi pemisah.  
3. **Mengatur perataan paragraf** – `setAlignment(ParagraphAlignment.CENTER)` mengubah perataan garis. Kata kunci *set paragraph alignment* diterapkan langsung pada pemisah, memastikan dash berada di tengah.  
4. **Menambahkan dash khusus** – Dengan menghapus run yang ada dan menambahkan `Run` baru dengan karakter em‑dash (`—`), Anda mencapai efek *add custom dash* sekaligus *change footnote line* ke gaya yang diinginkan.  
5. **Menyimpan dokumen** – `doc.save(...)` menulis perubahan kembali ke disk, menghasilkan file output yang mencerminkan semua modifikasi.

## Tambahkan dash khusus ke pemisah catatan kaki

Kode pada **Langkah 4** memperlihatkan teknik *add custom dash*. Anda dapat mengganti em‑dash dengan string apa pun, seperti `"***"` atau `"---"`, untuk menyesuaikan bahasa visual dokumen Anda.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Menggunakan dash khusus sangat membantu ketika garis tipis default tidak memenuhi pedoman branding.

## Ubah gaya garis catatan kaki

Jika Anda lebih suka garis solid daripada dash, Anda dapat menyisipkan karakter Unicode box‑drawing atau underscore berulang.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Langkah *change footnote line* bekerja sama cara terlepas dari karakter yang Anda pilih, karena paragraf pemisah hanya menampilkan teks yang ada di dalamnya.

## Atur perataan paragraf untuk pemisah catatan kaki

Operasi *set paragraph alignment* tidak terbatas pada perataan tengah. Anda dapat meratakan kiri, kanan, atau justify sesuai kebutuhan tata letak.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Meratakan pemisah ke kanan dapat berguna untuk dokumen yang menggunakan catatan kaki ber‑perataan kanan, seperti publikasi dwibahasa.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang menggabungkan semua konsep—memuat dokumen, mengedit pemisah catatan kaki, menambahkan dash khusus, mengubah gaya garis, dan mengatur perataan.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** File `output.docx` berisi em‑dash yang terpusat di tempat garis tipis semula. Semua catatan kaki tetap utuh, dan tata letak dokumen mencerminkan gaya pemisah baru.

## Kesalahan umum dan cara menghindarinya

| Issue | Reason | Fix |
|-------|--------|-----|
| Separator not found | Document has no footnotes or uses a custom footnote style | Ensure the source DOCX contains at least one footnote before calling `getFootnoteSeparator()` |
| Custom dash not visible | Font does not support the chosen character | Use a Unicode character that is supported by the document’s default font, or embed a compatible font |
| Alignment appears unchanged | Paragraph format is overridden later in the code | Apply alignment **after** any other formatting calls that might reset it |

Menangani poin‑poin ini mencegah error runtime dan menjamin proses *cara mengedit catatan kaki* berjalan andal.

## Langkah selanjutnya

Sekarang Anda tahu **cara mengedit catatan kaki** elemen, Anda dapat menjelajahi tugas terkait:

* **Add custom footnote reference style** – modify `FootnoteReference` nodes to change numbering or symbols.  
* **Programmatically insert new footnotes** – use `DocumentBuilder.insertFootnote()` for dynamic content.  
* **Apply conditional formatting** – change footnote appearance based on paragraph style or content length.  

Setiap ekstensi ini dibangun di atas permukaan API yang sama yang Anda gunakan untuk *add custom dash*, *change footnote line*, dan *set paragraph alignment*.

---

*Selamat coding! Jika tutorial ini membantu Anda menguasai pengeditan catatan kaki, pertimbangkan untuk membagikannya dengan tim Anda atau mengirim pull request untuk meningkatkan contoh lebih lanjut.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Atur Posisi Catatan Kaki Dan Catatan Akhir](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}