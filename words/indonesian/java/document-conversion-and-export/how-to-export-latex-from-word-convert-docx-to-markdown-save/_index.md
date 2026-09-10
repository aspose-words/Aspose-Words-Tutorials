---
category: general
date: 2025-12-25
description: Cara mengekspor LaTeX saat Anda mengonversi DOCX ke markdown dan menyimpan
  dokumen sebagai PDF—panduan langkah demi langkah dengan kode Java.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
language: id
og_description: Pelajari cara mengekspor LaTeX sambil mengonversi DOCX ke markdown
  dan menyimpan dokumen sebagai PDF dengan Java. Kode lengkap dan tips.
og_title: Cara Mengekspor LaTeX dari Word – Konversi DOCX ke Markdown & Simpan PDF
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

# Cara Mengekspor LaTeX dari Word: Mengonversi DOCX ke Markdown & Menyimpan sebagai PDF

Pernah bertanya-tanya **bagaimana cara mengekspor LaTeX** dari file Word tanpa kehilangan persamaan rumit itu? Anda tidak sendirian. Dalam banyak proyek—makalah akademik, blog teknis, atau dokumen internal—orang perlu mengambil LaTeX dari `.docx`, mengubah seluruhnya menjadi markdown, dan tetap mempertahankan versi PDF yang rapi untuk distribusi.  

Dalam tutorial ini kami akan membahas seluruh alur kerja: **mengonversi docx ke markdown**, **mengekspor LaTeX**, dan **menyimpan dokumen sebagai PDF** menggunakan pustaka Aspose.Words for Java. Pada akhir tutorial Anda akan memiliki program Java siap‑jalankan yang melakukan semuanya, plus beberapa tips praktis yang dapat Anda salin‑tempel ke basis kode Anda sendiri.

## Apa yang Akan Anda Pelajari

- Memuat dokumen Word yang mungkin rusak dalam mode pemulihan.  
- Mengekspor persamaan Office Math sebagai LaTeX saat menyimpan ke markdown.  
- Menyimpan dokumen yang sama sebagai PDF sambil menangani bentuk mengambang sebagai tag inline.  
- Menyesuaikan penanganan gambar selama ekspor markdown (menyimpan gambar di folder khusus).  
- Cara **menyimpan word sebagai markdown** dan tetap mempertahankan salinan PDF berkualitas tinggi.  

**Prasyarat**: Java 17 atau lebih baru, Maven atau Gradle, dan lisensi Aspose.Words for Java (versi percobaan gratis cukup untuk percobaan). Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## Langkah 1: Siapkan Proyek Anda

Hal pertama—tambahkan jar Aspose.Words ke classpath. Jika Anda menggunakan Maven, tambahkan dependensi ini ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

Untuk Gradle, cukup satu baris:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Selalu gunakan versi stabil terbaru; versi tersebut mencakup perbaikan bug untuk mode pemulihan dan ekspor LaTeX.

Buat kelas Java baru bernama `DocxProcessor.java`. Kami akan mengimpor semua yang diperlukan:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

---

## Langkah 2: Muat Dokumen dalam Mode Pemulihan

File yang rusak memang terjadi—terutama ketika mereka dikirim lewat email atau sinkronisasi cloud. Aspose.Words memungkinkan Anda membuka mereka dalam *mode pemulihan* sehingga Anda tidak kehilangan seluruh isi.

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

Mengapa menggunakan `RecoveryMode.RECOVER`? Metode ini berusaha menyelamatkan sebanyak mungkin konten, sambil tetap melemparkan pengecualian jika file benar‑benar tidak dapat dibaca. Ini menyeimbangkan keamanan dengan kepraktisan.

---

## Langkah 3: Ekspor LaTeX Saat Mengonversi DOCX ke Markdown

Sekarang saatnya bintang utama: **cara mengekspor LaTeX** dari dokumen Word. Kelas `MarkdownSaveOptions` memiliki properti `OfficeMathExportMode` yang memungkinkan Anda memilih output LaTeX, MathML, atau gambar. Kami akan memilih LaTeX.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

File `output.md` yang dihasilkan akan berisi fragmen LaTeX yang dibungkus dalam `$…$` untuk persamaan inline atau `$$…$$` untuk persamaan tampilan. Jika Anda membuka file tersebut di editor markdown yang mendukung MathJax atau KaTeX, persamaan akan dirender dengan indah.

> **Mengapa LaTeX?** Karena itu adalah bahasa universal penerbitan ilmiah. Mengekspor langsung ke LaTeX menghindari konversi lossy yang akan Anda dapatkan jika memilih gambar.

---

## Langkah 4: Simpan Dokumen sebagai PDF (dan Pertahankan Bentuk Mengambang)

Seringkali Anda masih membutuhkan versi PDF untuk reviewer yang tidak nyaman dengan markdown. Aspose.Words membuat ini sangat mudah, dan Anda dapat mengontrol bagaimana bentuk mengambang (seperti diagram) diperlakukan.

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

Menetapkan `ExportFloatingShapesAsInlineTag` ke `true` mengubah setiap bentuk mengambang menjadi tag `<span>` inline dalam struktur internal PDF, yang dapat berguna untuk pemrosesan lanjutan (misalnya, alat aksesibilitas PDF).

---

## Langkah 5: Sesuaikan Penanganan Gambar Saat Menyimpan Markdown

Secara default, Aspose.Words menaruh setiap gambar ke folder yang sama dengan file markdown, memberi nama secara berurutan. Jika Anda lebih suka subdirektori `images/` yang rapi, Anda dapat memanfaatkan `ResourceSavingCallback`.

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

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut adalah file lengkap `DocxProcessor.java` yang dapat Anda kompilasi dan jalankan:

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

Buka markdown di VS Code dengan ekstensi *Markdown Preview Enhanced*, dan Anda akan melihat persamaan dirender persis seperti yang muncul di file Word asli.

---

## Pertanyaan yang Sering Diajukan (FAQs)

**T: Apakah ini bekerja dengan file .doc atau hanya .docx?**  
J: Ya. Aspose.Words secara otomatis mendeteksi format. Cukup ubah ekstensi file di `inputPath`.

**T: Bagaimana jika saya membutuhkan MathML alih‑alih LaTeX?**  
J: Ganti `OfficeMathExportMode.LATEX` dengan `OfficeMathExportMode.MATHML`. Sisa alur tetap sama.

**T: Bisakah saya melewatkan langkah PDF?**  
J: Tentu saja. Cukup komentar blok PDF. Kode bersifat modular, sehingga Anda dapat **menyimpan dokumen sebagai PDF** hanya ketika diperlukan.

**T: Bagaimana cara menangani dokumen yang dilindungi password?**  
J: Gunakan `LoadOptions.setPassword("yourPassword")` sebelum membuat instance `Document`.

**T: Apakah ada cara menyematkan LaTeX langsung ke dalam PDF?**  
J: Tidak secara native; PDF tidak memahami LaTeX. Anda harus merender persamaan sebagai gambar terlebih dahulu, yang menghilangkan tujuan ekspor LaTeX yang bersih.

---

## Kasus Tepi & Tips

- **Gambar Rusak**: Jika sebuah gambar tidak dapat dibaca, Aspose.Words akan menyisipkan placeholder. Anda dapat mendeteksinya di `ResourceSavingCallback` dengan memeriksa `args.getStream().available()`.
- **Dokumen Besar**: Untuk file lebih dari 100 MB, pertimbangkan streaming output PDF (`doc.save(outputPdf, pdfOptions)` dimana `outputPdf` adalah `FileOutputStream`) untuk menghindari tekanan memori.
- **Kinerja**: Mengaktifkan `RecoveryMode.IGNORE` mempercepat pemuatan tetapi dapat menghilangkan konten. Gunakan `RECOVER` untuk pendekatan seimbang.
- **Penegakan Lisensi**: Dalam mode percobaan, setiap dokumen yang disimpan akan memiliki watermark. Daftarkan lisensi untuk menghilangkannya—cukup panggil `License license = new License(); license.setLicense("Aspose.Words.lic");` sebelum pemrosesan apa pun.

---

## Kesimpulan

Itulah cara **mengekspor LaTeX** dari file Word, **mengonversi docx ke markdown**, dan **menyimpan dokumen sebagai PDF** dalam satu program Java yang rapi. Kami telah membahas pemuatan dalam mode pemulihan, ekspor LaTeX, pembuatan PDF dengan penanganan bentuk mengambang, serta folder gambar khusus untuk markdown.  

Dari sini Anda dapat bereksperimen dengan format ekspor lain (HTML, EPUB), mengintegrasikan logika ini ke layanan web, atau mengotomatisasi pemrosesan batch ratusan file. Blok‑bangunan sudah tersedia, dan API Aspose.Words membuat memperluas alur kerja menjadi sangat mudah.

Jika panduan ini membantu, beri bintang di GitHub, bagikan kepada rekan tim, atau tinggalkan komentar di bawah dengan modifikasi Anda sendiri. Selamat coding, dan semoga LaTeX Anda selalu terrender dengan sempurna! 

![Diagram yang menunjukkan alur konversi dari DOCX → Markdown (dengan LaTeX) → PDF, teks alternatif: "Cara mengekspor LaTeX saat mengonversi DOCX ke markdown dan menyimpan sebagai PDF"]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}