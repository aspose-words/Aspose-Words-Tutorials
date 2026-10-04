---
category: general
date: 2026-10-04
description: Edit pemisah catatan kaki di Java menggunakan Aspose.Words – pelajari
  cara mengubah pemisah catatan kaki dan menambahkan kata pemisah khusus ke dokumen
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: id
lastmod: 2026-10-04
og_description: Edit pemisah catatan kaki di Java dengan Aspose.Words. Tutorial ini
  menunjukkan cara mengubah pemisah catatan kaki dan menyisipkan kata pemisah khusus.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Edit pemisah catatan kaki di Java – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Cara mengedit pemisah catatan kaki di Java dengan Aspose.Words
url: /id/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengedit pemisah catatan kaki di Java dengan Aspose.Words

Jika Anda perlu **mengedit pemisah catatan kaki** dalam dokumen Word, panduan ini menunjukkan secara tepat cara melakukannya di Java. Baik Anda ingin **mengubah pemisah catatan kaki** menjadi tanda hubung, bintang, atau **kata pemisah khusus** apa pun, langkah-langkah di bawah ini mencakup semua yang Anda perlukan.

Anda akan belajar cara memuat file `.docx`, mengambil bagian pemisah khusus, memodifikasi isinya, dan menyimpan hasilnya. Tidak diperlukan skrip eksternal atau penyuntingan manual – semuanya dilakukan secara programatis dengan pustaka Aspose.Words for Java.

## Prasyarat

- Java 17 atau yang lebih baru terpasang.
- Maven atau Gradle untuk mengelola dependensi (contoh menggunakan Maven).
- Lisensi Aspose.Words for Java yang valid (atau kunci evaluasi gratis).
- Dokumen Word yang sudah berisi catatan kaki (pemisah hanya ada bila ada catatan kaki).

## Tambahkan Aspose.Words ke proyek Anda

Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Untuk Gradle, tambahkan:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Langkah 1: Muat dokumen yang berisi catatan kaki

Langkah pertama adalah membuka file Word yang ingin Anda modifikasi. Aspose.Words membaca file tersebut ke dalam objek `Document`, yang memberi Anda akses penuh ke semua bagian dokumen, termasuk pemisah catatan kaki.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Mengapa ini penting:** Memuat dokumen membuat representasi dalam memori, sehingga Anda dapat dengan aman memodifikasi node apa pun tanpa menyentuh file asli sampai Anda secara eksplisit menyimpannya.

## Langkah 2: Ambil bagian pemisah catatan kaki

Word menyimpan pemisah catatan kaki sebagai node `Separator` khusus. Aspose.Words menyediakan metode `getFootnoteSeparator()` untuk memperolehnya secara langsung.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Tips pro:** Node pemisah hanya ada jika dokumen sudah memiliki setidaknya satu catatan kaki. Jika Anda mencoba mengedit dokumen tanpa catatan kaki, `getFootnoteSeparator()` mengembalikan `null`, jadi selalu periksa kondisi ini.

## Langkah 3: Sisipkan kata pemisah khusus

Sekarang Anda dapat mengubah tampilan pemisah. Dalam contoh ini kami mengganti garis default dengan em dash (`—`). Anda juga dapat menyisipkan **kata pemisah khusus** apa pun seperti `"NOTE:"` atau `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### Apa yang dilakukan kode ini

1. **`clearChildren()`** menghapus semua run yang ada, memastikan pemisah hanya berisi teks yang Anda berikan.
2. **`new Run(document, "—")`** membuat node teks dengan pemisah yang diinginkan. Objek `Run` menghormati gaya dokumen, sehingga pemisah mewarisi pemformatan pemisah catatan kaki asli.
3. **`appendChild(customRun)`** menyisipkan run baru ke dalam paragraf pemisah.

Anda juga dapat menerapkan pemformatan pada run, misalnya:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Langkah 4: Simpan dokumen yang telah dimodifikasi

Setelah mengedit pemisah, tulis kembali dokumen ke disk. Pilih nama file baru agar file asli tidak tersentuh.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Verifikasi hasil:** Buka `ModifiedNotes.docx` di Microsoft Word. Pemisah catatan kaki kini harus menampilkan dash khusus (atau kata apa pun yang Anda pilih) alih-alih garis default.

## Menangani beberapa pemisah catatan kaki

Word mendukung tiga jenis pemisah khusus:

| Tipe pemisah | Metode |
|----------------|----------------------------|
| Pemisah catatan kaki | `getFootnoteSeparator()` |
| Pemisah lanjutan catatan kaki | `getFootnoteContinuationSeparator()` |
| Pemisah catatan kaki untuk halaman pertama | `getFootnoteSeparatorForFirstPage()` |

Jika Anda perlu mengedit semuanya, ulangi **Langkah 2** dan **Langkah 3** untuk setiap metode. Contoh:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Kesalahan umum dan cara menghindarinya

| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Tidak ada pemisah yang muncul setelah menyimpan | Dokumen tidak memiliki catatan kaki → node pemisah adalah `null` | Tambahkan setidaknya satu catatan kaki sebelum mengedit, atau buat catatan kaki dummy secara programatis. |
| Pemisah menampilkan spasi berlebih | Run yang ada tidak dibersihkan | Panggil `clearChildren()` sebelum menambahkan run baru. |
| Pemformatan terlihat berbeda | Run mewarisi gaya dari pemisah asli | Secara eksplisit atur properti font pada `Run` jika Anda memerlukan tampilan tertentu. |

## Contoh lengkap yang berfungsi

Menggabungkan semua bagian, berikut adalah kelas Java mandiri yang dapat Anda salin, kompilasi, dan jalankan:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Jalankan program, lalu buka `ModifiedNotes.docx` untuk memastikan pemisah telah diperbarui.

## Kesimpulan

Anda sekarang tahu cara **mengedit pemisah catatan kaki** dalam dokumen Word menggunakan Java dan Aspose.Words. Tutorial ini mencakup memuat dokumen, mengambil node pemisah khusus, menyisipkan **kata pemisah khusus**, dan menyimpan hasilnya. Dengan mengikuti langkah‑langkah ini Anda juga dapat **mengubah pemisah catatan kaki** untuk bagian lanjutan atau catatan kaki halaman pertama.

Selanjutnya, Anda mungkin ingin menjelajahi:

- Menambahkan pemisah berbeda untuk catatan kaki halaman pertama (`getFootnoteSeparatorForFirstPage()`).
- Membuat catatan kaki secara programatis ketika tidak ada.
- Menggunakan Aspose.Words untuk menata teks catatan kaki (font, warna, indentasi).

Silakan bereksperimen dengan karakter atau kata lain untuk menyesuaikan merek dokumen Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sisipkan Pemisah Gaya Dokumen di Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Dapatkan Pemisah Gaya Paragraf dalam Dokumen Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Cara Memuat Dokumen Word dengan Aspose.Words Java: Panduan Komprehensif](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}