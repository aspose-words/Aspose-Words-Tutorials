---
category: general
date: 2026-10-23
description: Cara mengekspor LaTeX sambil mengonversi DOCX ke markdown dan menyimpan
  dokumen sebagai PDF—panduan langkah demi langkah dengan kode Java.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
lastmod: 2026-10-23
og_description: Pelajari cara mengekspor LaTeX saat mengonversi DOCX ke markdown dan
  menyimpan dokumen sebagai PDF dengan Java. Kode lengkap dan tips.
og_image_alt: Diagram of DOCX to markdown (LaTeX) and PDF conversion pipeline
og_title: Cara mengekspor LaTeX dari Word dan menyimpan PDF menggunakan Java
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: How to export LaTeX while you convert DOCX to markdown and save document
    as PDF—step‑by‑step guide with Java code.
  headline: 'How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF'
  type: TechArticle
- description: How to export LaTeX while you convert DOCX to markdown and save document
    as PDF—step‑by‑step guide with Java code.
  name: 'How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF'
  steps:
  - name: set up your project
    text: 'First things first—let’s get the Aspose.Words jar on the classpath. If
      you’re using Maven, add this dependency to your `pom.xml`: For Gradle, it’s
      a one‑liner: > **Pro tip:** Always use the latest stable version; it includes
      bug fixes for recovery mode and LaTeX export. Create a new Java class calle'
  - name: load the document in recovery mode
    text: '`RecoveryMode.RECOVER` tells Aspose.Words to attempt salvaging a broken
      file. **Definition:** `RecoveryMode.RECOVER` is an enum value that enables partial
      document reconstruction while still reporting unrecoverable errors. Why use
      `RecoveryMode.RECOVER`? It attempts to salvage as much content as pos'
  - name: export LaTeX while converting DOCX to markdown
    text: 'Now comes the star of the show: **how to export LaTeX** from the Word document.
      The `MarkdownSaveOptions` class has an `OfficeMathExportMode` property that
      lets you choose LaTeX, MathML, or image output. We’ll pick LaTeX. **Definition:**
      `MarkdownSaveOptions` configures how Aspose.Words writes a doc'
  - name: save the document as PDF (and preserve floating shapes)
    text: Often you still need a PDF version for reviewers who aren’t comfortable
      with markdown. Aspose.Words makes this trivial, and you can control how floating
      shapes (like diagrams) are handled. **Definition:** `ExportFloatingShapesAsInlineTag`
      is a boolean flag that, when true, converts each floating sha
  - name: customize image handling when saving markdown
    text: By default, Aspose.Words dumps every image into the same folder as the markdown
      file, naming them sequentially. If you prefer a tidy `images/` subdirectory,
      you can hook into the `ResourceSavingCallback`. **Definition:** `ResourceSavingCallback`
      is an interface you implement to control where and how
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words automatically detects the format; simply change the
      file extension in `inputPath`.
    question: Does this work with .doc files or only .docx?
  - answer: Replace `OfficeMathExportMode.LATEX` with `OfficeMathExportMode.MATHML`.
      The rest of the pipeline stays identical.
    question: What if I need MathML instead of LaTeX?
  - answer: Absolutely. Comment out the PDF block; the code is modular, so you can
      **save document as PDF** only when you need it.
    question: Can I skip the PDF step?
  - answer: Use `LoadOptions.setPassword("yourPassword")` before creating the `Document`
      instance.
    question: How do I handle password‑protected documents?
  - answer: Not natively; PDFs don’t understand LaTeX. You’d have to render the equations
      as images first, which defeats the purpose of a clean LaTeX export.
    question: Is there a way to embed the LaTeX directly into the PDF?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'Cara Mengekspor LaTeX dari Word: Mengonversi DOCX ke Markdown & Menyimpan
  sebagai PDF'
url: /id/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengekspor LaTeX dari Word: mengonversi DOCX ke markdown & menyimpan sebagai PDF

Pernah bertanya-tanya **bagaimana mengekspor LaTeX** dari file Word tanpa kehilangan persamaan rumit itu? Anda tidak sendirian. Dalam banyak proyek—makalah akademik, blog teknis, atau dokumen internal—orang perlu mengambil LaTeX dari sebuah `.docx`, mengubah seluruhnya menjadi markdown, dan tetap menjaga versi PDF yang rapi untuk distribusi.  

Dalam tutorial ini kami akan membahas seluruh alur: **mengonversi docx ke markdown**, **mengekspor LaTeX**, dan **menyimpan dokumen sebagai PDF** menggunakan pustaka Aspose.Words untuk Java. Pada akhir tutorial Anda akan memiliki program Java siap‑jalankan yang melakukan semuanya, plus beberapa tips praktis yang dapat Anda salin‑tempel ke basis kode Anda.

## Jawaban Cepat
- **Bisakah saya mengonversi DOCX yang rusak?** Ya – muat dalam mode pemulihan untuk menyelamatkan sebagian besar konten.  
- **Format apa yang digunakan ekspor LaTeX?** Inline `$…$` untuk persamaan sederhana, `$$…$$` untuk persamaan tampilan.  
- **Apakah saya perlu menginstal Microsoft Word?** Tidak, Aspose.Words berfungsi secara independen.  
- **Bagaimana gambar disimpan saat mengekspor ke markdown?** Anda dapat mengarahkannya ke subfolder `images/` melalui callback.  
- **Apakah lisensi diperlukan untuk produksi?** Ya – versi percobaan menambahkan watermark; lisensi yang tepat menghilangkannya.

## Apa yang akan Anda pelajari

- Memuat dokumen Word yang mungkin rusak dalam mode pemulihan.  
- Mengekspor persamaan Office Math sebagai LaTeX saat menyimpan ke markdown.  
- Menyimpan dokumen yang sama sebagai PDF sambil menangani bentuk mengambang sebagai tag inline.  
- Menyesuaikan penanganan gambar selama ekspor markdown (menyimpan gambar di folder khusus).  
- Cara **menyimpan word sebagai markdown** dan tetap mempertahankan salinan PDF berkualitas tinggi.  

**Prasyarat**: Java 17 atau lebih baru, Maven atau Gradle, dan lisensi Aspose.Words untuk Java (versi percobaan gratis dapat digunakan untuk eksperimen). Tidak ada pustaka pihak ketiga lain yang diperlukan.

## Cara mengekspor LaTeX dari Word?

Muat DOCX Anda dengan `new Document("input.docx", loadOptions)` dan atur `loadOptions.setRecoveryMode(RecoveryMode.RECOVER)`. Aspose.Words kemudian berusaha membangun kembali struktur dokumen, mempertahankan sebanyak mungkin elemen sambil tetap melemparkan pengecualian jika file tidak dapat dibaca sama sekali. Pendekatan ini memberi Anda cadangan aman untuk file yang rusak tanpa mengorbankan mayoritas konten.

### Langkah 1: menyiapkan proyek Anda

First things first—let’s get the Aspose.Words jar on the classpath. If you’re using Maven, add this dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

For Gradle, it’s a one‑liner:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Tips profesional:** Selalu gunakan versi stabil terbaru; versi tersebut mencakup perbaikan bug untuk mode pemulihan dan ekspor LaTeX.

Create a new Java class called `DocxProcessor.java`. We’ll import everything we need:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

### Langkah 2: memuat dokumen dalam mode pemulihan

`RecoveryMode.RECOVER` memberi tahu Aspose.Words untuk mencoba menyelamatkan file yang rusak.  

**Definisi:** `RecoveryMode.RECOVER` adalah nilai enum yang memungkinkan rekonstruksi dokumen parsial sambil tetap melaporkan kesalahan yang tidak dapat dipulihkan.

```java
public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown = "YOUR_DIRECTORY/output.md";
        String outputPdf = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown = "YOUR_DIRECTORY/output_with_custom_images.md";

        // Step 2: Load with recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // STRICT, IGNORE are alternatives
        Document doc = new Document(inputPath, loadOptions);

        // Continue with export steps...
```

Mengapa menggunakan `RecoveryMode.RECOVER`? Ia berusaha menyelamatkan sebanyak mungkin konten, sambil tetap melemparkan pengecualian jika file benar‑benar tidak dapat dibaca. Ini menyeimbangkan keamanan dengan kepraktisan.

### Langkah 3: mengekspor LaTeX sambil mengonversi DOCX ke markdown

Sekarang hadir bintang utama: **cara mengekspor LaTeX** dari dokumen Word. Kelas `MarkdownSaveOptions` memiliki properti `OfficeMathExportMode` yang memungkinkan Anda memilih output LaTeX, MathML, atau gambar. Kami akan memilih LaTeX.

**Definisi:** `MarkdownSaveOptions` mengonfigurasi cara Aspose.Words menulis dokumen ke format Markdown, termasuk penanganan gambar dan ekspor matematika.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

File `output.md` yang dihasilkan akan berisi fragmen LaTeX yang dibungkus dalam `$…$` untuk persamaan inline atau `$$…$$` untuk persamaan tampilan. Jika Anda membuka file tersebut di editor markdown yang mendukung MathJax atau KaTeX, persamaan akan ditampilkan dengan indah.

> **Mengapa LaTeX?** Karena itu adalah bahasa universal penerbitan ilmiah. Mengekspor langsung ke LaTeX menghindari konversi lossy yang akan Anda dapatkan jika memilih gambar.

### Langkah 4: menyimpan dokumen sebagai PDF (dan mempertahankan bentuk mengambang)

Seringkali Anda masih memerlukan versi PDF untuk reviewer yang tidak nyaman dengan markdown. Aspose.Words membuat ini mudah, dan Anda dapat mengontrol bagaimana bentuk mengambang (seperti diagram) ditangani.

**Definisi:** `ExportFloatingShapesAsInlineTag` adalah flag boolean yang, ketika true, mengonversi setiap bentuk mengambang menjadi tag `<span>` inline di dalam representasi XML internal PDF.

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

Mengatur `ExportFloatingShapesAsInlineTag` ke `true` mengonversi setiap bentuk mengambang menjadi tag `<span>` inline dalam struktur internal PDF, yang dapat berguna untuk pemrosesan lanjutan (mis., alat aksesibilitas PDF).

### Langkah 5: menyesuaikan penanganan gambar saat menyimpan markdown

Secara default, Aspose.Words menaruh setiap gambar ke folder yang sama dengan file markdown, memberi nama secara berurutan. Jika Anda lebih suka subdirektori `images/` yang rapi, Anda dapat mengaitkan ke `ResourceSavingCallback`.

**Definisi:** `ResourceSavingCallback` adalah antarmuka yang Anda implementasikan untuk mengontrol dimana dan bagaimana sumber daya eksternal (seperti gambar) ditulis selama ekspor.

```java
        // Step 5: Custom image folder for markdown export
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Place each image under YOUR_DIRECTORY/images/
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs(); // Ensure the folder exists
                args.setFileName(imageFolder + args.getFileName());
                // You could also modify the stream here or skip saving if needed
            }
        });

        doc.save(customMarkdown, customMdOptions);
```

Sekarang semua gambar yang direferensikan dalam `output_with_custom_images.md` berada rapi di bawah `images/`. Ini membuat kontrol versi lebih bersih dan mencerminkan tata letak tipikal yang Anda lihat di GitHub.

## Contoh lengkap yang berfungsi

Putting it all together, here’s the complete `DocxProcessor.java` file you can compile and run:

```java
import com.aspose.words.*;

import java.io.File;

public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // ==== USER CONFIGURATION ====
        String inputPath        = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown   = "YOUR_DIRECTORY/output.md";
        String outputPdf        = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown   = "YOUR_DIRECTORY/output_with_custom_images.md";

        // ==== 1️⃣ Load document with recovery mode ====
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
        Document doc = new Document(inputPath, loadOptions);

        // ==== 2️⃣ Export LaTeX while converting to markdown ====
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);

        // ==== 3️⃣ Save as PDF, handling floating shapes ====
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);

        // ==== 4️⃣ Custom image folder for markdown export ====
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs();
                args.setFileName(imageFolder + args.getFileName());
            }
        });
        doc.save(customMarkdown, customMdOptions);

        System.out.println("All exports completed successfully!");
    }
}
```

### Output yang Diharapkan

- `output.md` – file markdown dengan persamaan LaTeX (`$…$` dan `$$…$$`).  
- `output.pdf` – PDF resolusi tinggi, bentuk mengambang diubah menjadi tag inline.  
- `output_with_custom_images.md` – markdown yang sama tetapi semua gambar disimpan di bawah `images/`.  

Buka markdown di VS Code dengan ekstensi *Markdown Preview Enhanced*, dan Anda akan melihat persamaan ditampilkan persis seperti yang muncul di file Word asli.

## Manfaat terukur menggunakan Aspose.Words

Aspose.Words mendukung **lebih dari 35 format input dan output** — termasuk DOCX, ODT, RTF, PDF, HTML, EPUB, dan Markdown — dan dapat memproses **dokumen 500 halaman dalam kurang dari 3 detik** pada CPU server tipikal. Pustaka ini juga menangani **hingga 200 MB media tersemat** tanpa memerlukan kode manajemen memori tambahan, menjadikannya ideal untuk konversi batch skala besar.

## Masalah umum & tips pemecahan masalah

- **Gambar rusak** – Jika gambar tidak dapat dibaca, Aspose.Words menyisipkan placeholder. Deteksi ini dalam `ResourceSavingCallback` dengan memeriksa `args.getStream().available()`.  
- **Dokumen besar** – Untuk file lebih dari 100 MB, alirkan output PDF (`doc.save(outputPdf, pdfOptions)` dimana `outputPdf` adalah `FileOutputStream`) untuk menjaga penggunaan memori tetap rendah.  
- **Kinerja** – Mengaktifkan `RecoveryMode.IGNORE` mempercepat pemuatan tetapi dapat menghilangkan konten. Gunakan `RECOVER` untuk pendekatan seimbang.  
- **Penegakan lisensi** – Dalam mode percobaan, setiap dokumen yang disimpan mendapatkan watermark. Daftarkan lisensi untuk menghilangkannya—cukup panggil `License license = new License(); license.setLicense("Aspose.Words.lic");` sebelum pemrosesan apa pun.

## Pertanyaan yang sering diajukan

**Q: Apakah ini bekerja dengan file .doc atau hanya .docx?**  
A: Ya. Aspose.Words secara otomatis mendeteksi format; cukup ubah ekstensi file di `inputPath`.

**Q: Bagaimana jika saya membutuhkan MathML alih-alih LaTeX?**  
A: Ganti `OfficeMathExportMode.LATEX` dengan `OfficeMathExportMode.MATHML`. Sisa alur tetap sama.

**Q: Bisakah saya melewatkan langkah PDF?**  
A: Tentu saja. Komentari blok PDF; kode bersifat modular, sehingga Anda dapat **menyimpan dokumen sebagai PDF** hanya ketika diperlukan.

**Q: Bagaimana cara menangani dokumen yang dilindungi kata sandi?**  
A: Gunakan `LoadOptions.setPassword("yourPassword")` sebelum membuat instance `Document`.

**Q: Apakah ada cara untuk menyematkan LaTeX langsung ke dalam PDF?**  
A: Tidak secara native; PDF tidak memahami LaTeX. Anda harus merender persamaan sebagai gambar terlebih dahulu, yang menghilangkan tujuan ekspor LaTeX yang bersih.

---

**Terakhir Diperbarui:** 2026-10-23  
**Diuji Dengan:** Aspose.Words 24.12 untuk Java  
**Penulis:** Aspose

## Tutorial Terkait

- [Cara Mengekspor Latex Dari Docx Panduan Lengkap Java](/words/java/document-conversion-and-export/how-to-export-latex-from-docx-complete-java-guide/)
- [Mengonversi Docx Ke Markdown Panduan Lengkap Dengan Ekspor Math](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-guide-with-math-export/)
- [Menyimpan Docx Sebagai Txt Dengan Ekspor Math Latex Panduan Lengkap Java](/words/java/document-conversion-and-export/save-docx-as-txt-with-latex-math-export-complete-java-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}