---
category: general
date: 2026-11-22
description: Pelajari cara memuat markdown dengan pemformatan di Java. Panduan ini
  menunjukkan cara membaca markdown dengan pemformatan menggunakan LoadOptions dan
  Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: id
lastmod: 2026-11-22
og_description: Cara memuat markdown dengan format di Java. Ikuti tutorial lengkap
  ini untuk membaca markdown dengan format, mempertahankan gaya underline, dan bekerja
  dengan objek Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Cara memuat markdown dengan format di Java – panduan langkah demi langkah
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Cara memuat markdown dengan pemformatan di Java
url: /id/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memuat markdown dengan format di Java

Jika Anda perlu **memuat markdown** sambil mempertahankan gaya visualnya, tutorial ini memberikan solusi siap‑jalankan. Anda akan melihat secara tepat cara **membaca markdown dengan format** seperti teks bergaris bawah, sehingga dokumen yang dihasilkan cocok dengan sumber aslinya.

Panduan ini mencakup setiap langkah mulai dari mengonfigurasi loader hingga memverifikasi bahwa format tetap ada setelah impor. Tidak diperlukan alat eksternal selain pustaka standar GroupDocs.Viewer (atau API kompatibel lain yang menyediakan `LoadOptions` dan `Document`). Pada akhir tutorial Anda dapat mengintegrasikan pemuatan markdown ke dalam backend Java apa pun, layanan web, atau aplikasi desktop.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 atau yang lebih baru terpasang.
* Maven atau Gradle untuk manajemen dependensi.
* Akses ke JAR GroupDocs.Viewer (atau setara) yang berisi `LoadOptions` dan `Document`.
* File markdown contoh (`sample.md`) yang mencakup markup underline (misalnya `<u>underlined text</u>` atau `_underlined_` tergantung parser).

## Langkah 1: Tambahkan dependensi yang diperlukan

Jika Anda menggunakan Maven, tambahkan berikut ke `pom.xml` Anda. Sesuaikan versi ke rilis stabil terbaru.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Pengguna Gradle dapat menambahkan:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Menyertakan pustaka membuat kelas `LoadOptions` dan `Document` tersedia pada saat kompilasi.

## Langkah 2: Konfigurasikan LoadOptions untuk mengimpor format underline

Objek `LoadOptions` memberi tahu parser fitur markdown mana yang harus dipertahankan. Mengaktifkan format underline memastikan gaya visual muncul pada `Document` yang dihasilkan.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Mengapa ini penting:**  
Tanpa `setImportUnderlineFormatting(true)`, parser akan menghapus tag underline, meninggalkan teks biasa. Mengaktifkan flag tersebut menjaga gaya tetap utuh, yang penting ketika konsumen hilir (misalnya generator PDF) bergantung pada petunjuk visual.

## Langkah 3: Muat dokumen markdown menggunakan opsi yang telah dikonfigurasi

Sekarang Anda dapat membaca file markdown. Konstruktor `Document` menerima jalur file dan `LoadOptions` yang baru saja Anda siapkan.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Mengapa ini penting:**  
Menyertakan `LoadOptions` ke konstruktor `Document` menjamin parser menghormati flag underline selama seluruh proses impor. Objek `Document` yang dihasilkan dapat dirender, dikonversi, atau diperiksa dengan format lengkap.

## Langkah 4: Verifikasi bahwa format underline tetap ada

Cara cepat untuk memastikan underline ada adalah merender dokumen ke HTML dan mencetak hasilnya. HTML akan berisi tag `<u>` jika impor berhasil.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Menjalankan program lengkap harus menampilkan potongan HTML yang mencakup `<u>underlined text</u>`. Jika tag tersebut tidak muncul, periksa kembali bahwa `setImportUnderlineFormatting(true)` telah dipanggil sebelum memuat file.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut kelas Java mandiri yang dapat Anda kompilasi dan jalankan:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Output yang diharapkan (dipotong untuk singkat):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Jika tag `<u>` muncul, markdown telah dimuat dengan format tetap utuh.

## Variasi umum dan kasus tepi

| Situasi                                 | Apa yang harus diubah                                          |
|----------------------------------------|---------------------------------------------------------------|
| **Ekstensi markdown yang berbeda**      | Gunakan `loadOptions.setImportBoldFormatting(true)` untuk **bold**. |
| **File besar (> 10 MB)**                | Stream file dengan `FileInputStream` dan berikan stream ke `Document`. |
| **Butuh output PDF**                    | Setelah memuat, gunakan `PdfViewOptions` dengan `Viewer` untuk menghasilkan PDF yang mempertahankan gaya underline. |
| **Menjalankan di container servlet**    | Simpan `Document` dalam scope request dan render ke HTML secara langsung. |

**Tips pro:** Selalu buat instance `LoadOptions` baru untuk setiap operasi pemuatan. Menggunakan kembali objek yang sama di antara thread dapat menyebabkan kebocoran status yang tidak terduga.

## Kesimpulan

Sekarang Anda tahu **cara memuat markdown dengan format di Java** dan bagaimana **membaca markdown dengan format** menggunakan `LoadOptions`. Contoh lengkap menunjukkan konfigurasi, pemuatan, dan verifikasi, sehingga Anda dapat menyematkan pola ini dalam proyek Java apa pun yang memproses file markdown.  

Selanjutnya, jelajahi topik terkait seperti **membaca markdown dengan gambar**, **mengonversi markdown ke PDF**, atau **menyesuaikan impor gaya lain** (bold, italic, strikethrough). Setiap ekstensi tersebut mengikuti pola yang sama: sesuaikan flag `LoadOptions`, muat `Document`, dan render dalam format yang diinginkan.

Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to load markdown document in Java with custom import options](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [How to read and load a Markdown file in Java with Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [How to Load Markdown in Java – Complete Guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}