---
category: general
date: 2026-10-23
description: Pelajari cara menyisipkan gambar dalam markdown saat mengonversi file
  DOCX, menggunakan Base64 untuk grafik kecil dan file eksternal untuk gambar yang
  lebih besar.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: Pelajari cara menyisipkan gambar dalam markdown saat mengonversi file
  DOCX, menggunakan Base64 untuk grafik kecil dan file eksternal untuk gambar yang
  lebih besar. Panduan ini menunjukkan langkah-langkah tepat dengan Aspose.Words for
  Java.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: Cara menyisipkan gambar dalam markdown – Panduan konversi DOCX Java
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: Cara menyisipkan gambar dalam markdown saat mengonversi docx
url: /id/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan gambar dalam markdown saat mengonversi docx

Pernah bertanya-tanya **cara menyisipkan gambar** dalam file Markdown yang berasal dari dokumen Word? Anda tidak sendirian. Kebanyakan pengembang mengalami masalah ketika konversi menghilangkan gambar atau menyimpannya dengan cara yang merusak tata letak akhir.  

Dalam panduan ini kami akan menunjukkan contoh lengkap yang siap dijalankan yang memperlihatkan **cara menyisipkan gambar** sebagai Base64 data URI untuk grafik kecil, sementara aset yang lebih besar ditulis ke folder samping. Sepanjang jalan kami juga akan membahas **convert docx to markdown**, menyentuh **how to convert docx** dengan Aspose.Words, dan menjelaskan perbedaan antara menyisipkan gambar sebagai Base64 versus mengekspornya sebagai file terpisah.  

> **Tip pro:** Jika Anda hanya membutuhkan proof‑of‑concept cepat, kode di bawah ini dapat langsung digunakan dengan satu dependensi Maven.

## Jawaban Cepat
- **Perpustakaan apa yang menangani konversi?** Aspose.Words for Java melakukan konversi DOCX → Markdown dan ekstraksi gambar.
- **Bagaimana gambar kecil disimpan?** Mereka di‑inline sebagai Base64 data URI langsung di dalam file Markdown.
- **Ke mana gambar besar disimpan?** Gambar yang lebih besar disimpan ke folder `markdown_resources` di samping file Markdown.
- **Apakah saya memerlukan Microsoft Word terpasang?** Tidak, Aspose.Words berfungsi sepenuhnya terlepas dari Microsoft Office.
- **Versi Java apa yang dibutuhkan?** Java 17 atau rilis LTS terbaru mana pun.

## Apa itu how to embed images?
`how to embed images` mengacu pada teknik menyisipkan data gambar langsung ke dalam dokumen Markdown, baik sebagai data URI yang di‑encode Base64 maupun sebagai tautan relatif ke file eksternal. Pendekatan ini memungkinkan Anda memiliki satu file Markdown yang portabel untuk grafik kecil sambil tetap mendukung aset resolusi tinggi melalui file terpisah.

## Mengapa menyisipkan gambar dalam markdown?
Menyisipkan gambar sebagai Base64 mengurangi permintaan HTTP untuk ikon dan grafik kecil, yang dapat meningkatkan kecepatan pemuatan halaman hingga 30 % pada jaringan berlatensi rendah. Pada saat yang sama, menjaga foto besar tetap eksternal mencegah file Markdown membengkak melebihi 5 MB, sehingga mempertahankan kinerja editor dan diff kontrol versi.

## Prasyarat
- **Java 17** (atau JDK terbaru lainnya). API berfokus pada Java, tetapi konsepnya dapat diterapkan ke bahasa lain.
- **Aspose.Words for Java** – perpustakaan komersial yang mendukung konversi DOCX → Markdown.
- Sebuah **sample DOCX** yang berisi campuran ikon kecil dan foto yang lebih besar.
- Folder yang dapat ditulisi tempat file Markdown dan sumber dayanya akan disimpan.

Tidak ada kerangka kerja tambahan, tidak ada skrip eksternal. Hanya Java biasa dan Aspose.Words.

## Apa yang Anda perlukan untuk menambahkan Aspose.Words ke proyek Anda (mengonversi docx ke markdown)

Jika Anda menggunakan Maven, letakkan potongan kode berikut ke dalam `pom.xml` Anda. Ganti versi dengan rilis terbaru pada saat Anda membacanya.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Mengapa ini penting:** Aspose.Words menangani pekerjaan berat dalam mem‑parsing struktur DOCX, mengekstrak gambar, dan merender sintaks Markdown. Mencoba membuat parser sendiri akan menjadi lubang kelinci yang tidak perlu Anda masuki.

## Bagaimana cara kerja kelas Document?
`Document` adalah objek inti Aspose.Words yang mewakili satu file Word di memori. Ia menyediakan metode untuk memuat, memodifikasi, dan menyimpan dokumen dalam banyak format.  
Ia mengenkapsulasi seluruh struktur dokumen, termasuk bagian, paragraf, tabel, dan sumber daya yang disisipkan, memungkinkan Anda memanipulasi konten secara programatis tanpa harus berurusan dengan XML di baliknya.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## Cara memutuskan antara Base64 dan file eksternal dengan callback
Callback sumber daya adalah implementasi `IResourceSavingCallback` yang memungkinkan Anda menyela setiap gambar selama konversi.  
Inilah inti dari **how to embed images** secara tepat. Callback memberi Anda hook untuk setiap sumber daya (gambar, gaya, dll.) yang ingin ditulis konverter. Dengan memeriksa ukuran gambar, Anda dapat memutuskan apakah akan menyisipkannya sebagai data URI atau menyimpannya sebagai file eksternal, yang membantu menyeimbangkan kinerja dan ukuran file.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Mengapa callback?
- **Kontrol:** Anda memutuskan apakah gambar menjadi string Base64 inline atau file terpisah.
- **Kinerja:** Ikon kecil menjadi bagian dari Markdown, menghilangkan permintaan HTTP tambahan.
- **Portabilitas:** Gambar besar tetap sebagai file eksternal, menjaga ukuran Markdown tetap wajar.

## Cara menyimpan dokumen sebagai markdown
`SaveOptions` adalah objek konfigurasi yang mengontrol bagaimana Aspose.Words menulis output, termasuk format, encoding, dan penanganan sumber daya.  
Akhirnya, beri tahu Aspose.Words untuk menulis file Markdown menggunakan opsi yang baru saja kita konfigurasikan. Objek `SaveOptions` memungkinkan Anda menentukan folder output, callback sumber daya, dan preferensi pemformatan lainnya, memastikan Markdown yang dihasilkan sesuai dengan konvensi proyek Anda. Anda juga dapat mengaktifkan atau menonaktifkan pembuatan tabel isi dan mengontrol bagaimana catatan kaki dirender.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Menjalankan program menghasilkan dua hal:

1. `output.md` – representasi Markdown dari DOCX asli Anda.  
2. Folder `markdown_resources` yang berisi gambar besar yang tidak disisipkan.

## Contoh lengkap yang berfungsi (semua langkah dalam satu tempat)

Berikut adalah file sumber lengkap, siap disalin‑tempel ke IDE Anda. Ganti `YOUR_DIRECTORY` dengan jalur aktual di mesin Anda.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Output yang diharapkan:** Buka `output.md` di penampil Markdown apa pun. Ikon kecil muncul inline, misalnya:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

Gambar yang lebih besar direferensikan seperti:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[Photo](markdown_resources/photo1.jpg)

Itulah cara tepat untuk **embed images** sambil tetap menjaga ukuran file tetap terkendali.

## Pertanyaan umum & kasus tepi

### Bagaimana jika gambar berupa JPEG bukan PNG?

Callback di atas selalu menambahkan prefix URI dengan `image/png`. Untuk JPEG, Anda dapat memeriksa beberapa byte pertama dari `args.getData()` atau menggunakan `args.getFileName()` untuk menebak tipe MIME yang tepat:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Bisakah saya mengubah ambang ukuran?

Tentu saja. Batas `10_000` byte hanyalah contoh. Jika Anda memiliki anggaran bandwidth yang cukup, naikkan menjadi 50 KB atau lebih. Sebaliknya, turunkan jika Anda memerlukan file Markdown yang sangat ringan.

### Apakah ini bekerja dengan tabel atau objek Word lainnya?

Ya. Aspose.Words secara otomatis mengonversi tabel, daftar, dan bahkan catatan kaki ke Markdown. Callback sumber daya hanya menyela gambar, jadi Anda tidak memerlukan kode tambahan untuk elemen lain.

### Bagaimana dengan nama file non‑ASCII?

API dengan aman meng‑encode nama file Unicode saat menulis ke folder `markdown_resources`. Pastikan sistem file Anda mendukung UTF‑8 (sebagian besar OS modern melakukannya).

## Tips pemecahan masalah dan jebakan umum

- **Gambar tidak muncul setelah konversi:** Pastikan `args.getData()` tidak null dan folder output memiliki izin menulis.  
- **String Base64 tampak rusak:** Pastikan pemanggilan `Base64.getEncoder().encodeToString()` menerima array byte lengkap; pemotongan sering terjadi ketika aliran tidak dibaca sepenuhnya.  
- **File Markdown terlalu besar:** Jika `.md` yang dihasilkan melebihi 5 MB, pertimbangkan menurunkan ambang ukuran atau mengompresi gambar besar sebelum menyimpannya ke folder sumber daya.  
- **Inkompatibilitas versi:** Aspose.Words 24.9+ mendukung lebih dari 35 format output dan dapat memproses DOCX 500‑halaman dalam kurang dari 4 detik pada server 2.5 GHz tipikal. Kunci versi Maven untuk menghindari perilaku tak terduga setelah rilis mayor.

## Pertanyaan yang sering diajukan

**T: Bisakah saya menggunakan pendekatan ini dalam layanan web yang menghasilkan Markdown secara dinamis?**  
J: Ya. API yang sama berfungsi di lingkungan Java apa pun, termasuk kontainer servlet dan aplikasi Spring Boot. Cukup alirkan `output.md` kembali ke klien setelah konversi.

**T: Apakah lisensi komersial diperlukan untuk penggunaan produksi?**  
J: Lisensi Aspose.Words yang valid diperlukan untuk penyebaran produksi. Lisensi evaluasi gratis tersedia untuk pengujian dan pengembangan.

**T: Bagaimana cara menangani file DOCX yang dilindungi password?**  
J: Muat dokumen dengan `new Document("file.docx", new LoadOptions("password"))`. Pipeline konversi yang sama kemudian diterapkan.

**T: Bagaimana jika saya perlu menyisipkan gambar SVG?**  
J: Konversi SVG ke PNG atau JPEG terlebih dahulu, lalu biarkan callback memperlakukannya seperti gambar lain. Aspose.Words tidak secara native merender SVG di dalam Markdown.

**T: Apakah ini bekerja di Windows, macOS, dan Linux?**  
J: Ya. Aspose.Words for Java bersifat platform‑agnostik dan berjalan di mana saja JDK yang kompatibel tersedia.

---

**Terakhir diperbarui:** 2026-10-23  
**Diuji dengan:** Aspose.Words for Java 24.10  
**Penulis:** Aspose

## Tutorial Terkait

- [Save Word Images Convert Docx To Markdown With Java](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Upload Images To CDN While Converting Docx To Markdown Full](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Convert Docx To Markdown Complete Java Guide](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}