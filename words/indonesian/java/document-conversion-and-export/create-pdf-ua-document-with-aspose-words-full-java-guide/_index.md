---
category: general
date: 2026-04-28
description: Buat dokumen PDF UA menggunakan Aspose.Words untuk Java. Pelajari cara
  memuat file docx dengan pemulihan, mengekspor persamaan ke LaTeX, menyimpan markdown
  dari Word, dan mengambil font yang hilang.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: id
og_description: Buat dokumen PDF UA dengan Aspose.Words untuk Java. Panduan langkah
  demi langkah yang mencakup pemulihan pemuatan, ekspor LaTeX, penyimpanan Markdown,
  dan pengambilan font yang hilang.
og_title: Buat Dokumen PDF UA – Tutorial Java Lengkap
tags:
- Aspose.Words
- Java
- PDF/UA
title: Buat Dokumen PDF UA dengan Aspose.Words – Panduan Lengkap Java
url: /id/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen PDF UA – Tutorial Java Lengkap

Perlu **membuat dokumen PDF UA** dari file Word sambil menangani konten yang rusak? Dalam tutorial ini kami akan memandu Anda melalui proses memuat DOCX dengan mode pemulihan, mengekspor persamaan ke LaTeX, menyimpan Markdown dari Word, dan mengambil font yang hilang—semua dengan Aspose.Words untuk Java.  

Jika Anda pernah menatap file .docx yang rusak dan bertanya-tanya mengapa PDF Anda tidak dapat diakses, Anda berada di tempat yang tepat. Pada akhir tutorial Anda akan memiliki file PDF/UA 1 yang sepenuhnya sesuai, versi Markdown yang berisi persamaan LaTeX, dan daftar jelas tentang substitusi font apa pun yang terjadi selama pemuatan.

## Apa yang Anda Butuhkan

- **Aspose.Words for Java** (versi terbaru per 2026) – tambahkan dependensi Maven/Gradle atau JAR ke classpath Anda.  
- Java 17 atau lebih baru (API menggunakan streams, jadi JDK terbaru disarankan).  
- Contoh `input.docx` yang mungkin berisi bagian yang rusak, persamaan Office Math, dan bentuk mengambang.  

Tidak ada pustaka tambahan yang diperlukan; semuanya berada di dalam Aspose.Words.

---

## Langkah 1 – Muat DOCX dengan Mode Pemulihan  

Ketika sebuah dokumen sebagian rusak, pemuat default akan melempar pengecualian. Dengan mengaktifkan mode pemulihan Anda memberi tahu Aspose.Words untuk terus berjalan dan menampilkan peringatan sebagai gantinya.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Mengapa ini penting:* Mode pemulihan mencegah seluruh alur kerja Anda terhenti karena satu paragraf yang buruk. Ini juga mengisi `doc.getWarnings()` sehingga Anda dapat nanti **mengambil font yang hilang** dan masalah lainnya.

---

## Langkah 2 – Ekspor Persamaan ke LaTeX dalam File Markdown  

Sebagian besar pengembang menyukai Markdown untuk dokumentasi, tetapi persamaan bawaan Word sulit disalin. Aspose.Words dapat menerjemahkannya langsung ke LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Tips pro:* Callback memastikan setiap gambar yang diekstrak disimpan di bawah `imgs/`. Ini meniru cara GitHub merender Markdown – bersih dan dapat dipindahkan.

---

## Langkah 3 – Buat Dokumen PDF / UA dengan Tagging yang Tepat  

Kepatuhan PDF/UA (Universal Accessibility) wajib untuk banyak proyek sektor publik. Opsi berikut membuat Aspose.Words menandai bentuk mengambang dengan benar dan mengatur flag kepatuhan PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Apa yang akan Anda lihat:* Membuka `output.pdf` di Adobe Acrobat Pro akan menampilkan “PDF/UA‑1 compliant” di properti dokumen. Semua bentuk mengambang (kotak teks, gambar) akan memiliki tag yang sesuai untuk pembaca layar.

---

## Langkah 4 – Sesuaikan Bayangan Bentuk (Styling Opsional)  

Meskipun tidak diperlukan untuk aksesibilitas, menyesuaikan aspek visual dapat berguna untuk laporan internal.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Mengapa repot?* Jika PDF juga merupakan materi pemasaran, bayangan halus membuat tata letak terasa lebih rapi tanpa melanggar kepatuhan.

---

## Langkah 5 – Ambil Font yang Hilang dan Peringatan Lainnya  

Selama pemuatan dengan pemulihan, Aspose.Words mencatat setiap substitusi font. Menyusun daftar ini membantu Anda memutuskan apakah akan menyematkan font yang benar atau menerima fallback.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Output tipikal* (konsol Anda akan menampilkan sesuatu seperti):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Jika Anda melihat font penting yang hilang, pertimbangkan menginstalnya di server atau menyematkannya melalui `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Contoh Lengkap yang Berfungsi  

Berikut adalah kelas Java lengkap yang siap dijalankan. Tempelkan ke IDE Anda, sesuaikan jalur, dan tekan **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Hasil yang diharapkan**

| Output | Deskripsi |
|--------|-----------|
| `output.md` | File Markdown di mana setiap persamaan Office Math muncul sebagai LaTeX (`$…$`). Gambar disimpan di bawah `imgs/`. |
| `output.pdf` | Dokumen yang mematuhi PDF/UA‑1; buka di Acrobat untuk melihat “PDF/UA‑1” di File → Properties → Standards. |
| Console | Daftar font yang hilang, misalnya, “Missing: Calibri → substituted: Arial”. |

---

## Pertanyaan yang Sering Diajukan (FAQ)

**Q: Apakah ini bekerja dengan versi Aspose.Words yang lebih lama?**  
A: Enum `RecoveryMode`, `OfficeMathExportMode.LATEX`, dan `PdfCompliance.PDF_UA_1` diperkenalkan pada versi 22.8. Jika Anda menggunakan rilis yang lebih lama, lakukan upgrade – fitur aksesibilitas tidak disertakan kembali.

**Q: Bagaimana jika saya perlu menyematkan font asli alih-alih substitusi?**  
A: Atur `pdfOptions.setEmbedFullFonts(true)` dan pastikan file font dapat diakses pada jalur font JVM.

**Q: Bisakah saya mengekspor ke format markup lain (misalnya HTML) sambil mempertahankan persamaan LaTeX?**  
A: Ya. Gunakan `HtmlSaveOptions` dan set `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – enum yang sama berfungsi di semua format.

**Q: Dokumen DOCX saya berisi banyak bentuk mengambang; apakah semuanya akan ditandai?**  
A: Dengan `setExportFloatingShapesAsInlineTag(true)`, Aspose.Words membungkus setiap bentuk mengambang dalam tag `<Figure>` untuk PDF/UA, memenuhi sebagian besar pemeriksaan pembaca layar.

---

## Kesimpulan  

Kami baru saja menunjukkan cara **membuat dokumen PDF UA** dari sumber Word, sekaligus **memuat docx dengan pemulihan**, **mengekspor persamaan ke LaTeX**, **menyimpan markdown dari Word**, dan **mengambil font yang hilang**. Kode ini sepenuhnya mandiri, berjalan pada lingkungan Java 17+ apa pun, dan menghasilkan aset yang siap untuk audit aksesibilitas serta pengembang

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}