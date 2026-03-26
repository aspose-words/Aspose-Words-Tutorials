---
category: general
date: 2026-03-25
description: Simpan gambar Word saat Anda mengonversi docx ke markdown menggunakan
  Aspose.Words untuk Java. Pelajari cara mengekstrak gambar dari Word dan membuat
  markdown dari docx dalam hitungan menit.
draft: false
keywords:
- save word images
- convert docx to markdown
- extract images from word
- export docx images
- create markdown from docx
language: id
og_description: Simpan gambar Word saat mengonversi file DOCX ke Markdown. Panduan
  ini memandu Anda melalui proses mengekstrak gambar dari Word dan membuat markdown
  dari DOCX menggunakan Java.
og_title: Simpan Gambar Word – Konversi DOCX ke Markdown dengan Java
tags:
- Aspose.Words
- Java
- Markdown
- Image Extraction
title: Simpan Gambar Word – Konversi DOCX ke Markdown dengan Java
url: /id/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Gambar Word – Konversi DOCX ke Markdown dengan Java

Perlu **menyimpan gambar Word** saat Anda mengonversi file DOCX ke Markdown? Anda bukan satu‑satunya yang mengalami masalah ini. Banyak pengembang bertanya, *“Bagaimana cara mengekstrak gambar dari Word dan tetap mendapatkan file markdown yang bersih?”* Dalam panduan ini kami akan memandu Anda melalui proses lengkap—memuat DOCX, mengonfigurasi Aspose.Words sehingga setiap gambar disimpan di folder `assets/`, dan akhirnya menulis dokumen markdown yang merujuk ke gambar‑gambar tersebut. Pada akhir tutorial Anda akan dapat **mengonversi docx ke markdown**, **mengekspor gambar docx**, dan **membuat markdown dari docx** hanya dengan beberapa baris Java.

Kami juga akan membahas jebakan umum (seperti ekstensi yang hilang) dan memberi Anda tips untuk menangani diagram atau SVG yang diperlakukan sebagai sumber daya oleh Aspose.Words. Siapkan IDE Anda, dan mari kita mulai.

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki hal‑hal berikut:

- **Java 17** (atau JDK terbaru; Aspose.Words mendukung 8+)
- **Aspose.Words for Java** JAR – Anda dapat mengunduhnya dari repositori Maven Central atau mengunduh versi percobaan dari situs web Aspose.
- Sebuah **DOCX** yang berisi setidaknya satu gambar (kami akan menyebutnya `doc-with-images.docx`).
- Sebuah folder tempat Anda ingin menyimpan markdown dan aset (misalnya `output/`).

Itu saja—tidak ada pustaka tambahan, tidak ada kerangka kerja berat. Sederhana, kan?

![contoh menyimpan gambar word](image.png "contoh menyimpan gambar word")

*Image alt text: contoh menyimpan gambar word yang menunjukkan folder assets dengan gambar yang diekstrak.*

## Langkah 1 – Siapkan Proyek Maven Anda (atau Java Biasa)

Jika Anda menggunakan Maven, tambahkan Aspose.Words sebagai dependensi:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- check for the latest version -->
</dependency>
```

Jika Anda lebih suka proyek Java biasa, cukup letakkan `aspose-words-24.9.jar` ke dalam classpath Anda. Tidak perlu sistem build yang lengkap.

> **Pro tip:** Gunakan versi terbaru untuk mendapatkan perbaikan bug bagi format gambar baru (WebP, HEIC, dll.).

## Langkah 2 – Muat DOCX yang Berisi Gambar

Hal pertama yang kami lakukan adalah membaca file sumber. Kelas `Document` milik Aspose.Words mengabstraksi format file, sehingga Anda dapat memperlakukan DOCX persis seperti PDF atau RTF.

```java
import com.aspose.words.*;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");
```

Mengapa harus memuat dokumen terlebih dahulu? Karena mesin konversi memerlukan model objek lengkap (paragraf, run, gambar) sebelum dapat memutuskan di mana menempatkan setiap sumber daya. Melewatkan langkah ini akan membuat callback berikutnya tidak dapat dipicu.

## Langkah 3 – Konfigurasikan Opsi Penyimpanan Markdown dengan Callback Sumber Daya

Aspose.Words memungkinkan Anda menyela setiap sumber daya eksternal melalui `IResourceSavingCallback`. Di sinilah kami memberi tahu perpustakaan **cara menamai dan di mana menyimpan setiap gambar yang diekstrak**.

```java
        // Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Store each resource in the "assets/" folder, preserving its original name
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String fileName = "assets/" + args.getResourceFileName() + extension;
                args.setResourceFileName(fileName);
            }
        });
```

### Mengapa menggunakan callback?

- **Kontrol atas penamaan** – Secara default Aspose mungkin menghasilkan GUID. Callback memungkinkan Anda mempertahankan nama file Word asli, yang jauh lebih mudah dibaca.
- **Organisasi folder** – Menempatkan semuanya di bawah `assets/` mencerminkan cara banyak generator situs statis mengharapkan gambar, sehingga markdown menjadi portabel.
- **Keamanan ekstensi** – Beberapa sumber daya tidak memiliki ekstensi; `getResourceFileExtension()` menjamin sufiks yang tepat, mencegah tautan gambar yang rusak.

## Langkah 4 – Simpan Dokumen sebagai Markdown

Sekarang kami benar‑benar melakukan konversi. Metode `save` menulis file markdown dan, berkat callback, menaruh setiap gambar ke sub‑folder `assets/`.

```java
        // Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);
    }
}
```

Saat kode selesai, Anda akan melihat:

```
output/
 ├─ doc.md          ← the markdown file
 └─ assets/
      ├─ image1.png
      └─ chart1.svg
```

Buka `doc.md` di editor apa pun dan Anda akan melihat tautan gambar markdown seperti `![Image1](assets/image1.png)`. Itulah hasil **simpan gambar word** yang Anda cari.

## Langkah 5 – Verifikasi Ekstraksi (Opsional tetapi Disarankan)

Pemeriksaan cepat dapat menyelamatkan Anda dari kejutan di kemudian hari.

```java
import java.nio.file.*;

public class VerifyExtraction {
    public static void main(String[] args) throws Exception {
        Path assets = Paths.get("output/assets");
        if (Files.isDirectory(assets)) {
            try (DirectoryStream<Path> stream = Files.newDirectoryStream(assets)) {
                System.out.println("Extracted resources:");
                for (Path p : stream) {
                    System.out.println("- " + p.getFileName());
                }
            }
        } else {
            System.out.println("No assets folder found. Did the callback run?");
        }
    }
}
```

Menjalankan ini seharusnya mencetak daftar setiap gambar, diagram, atau SVG yang diambil dari DOCX asli. Jika daftar kosong, periksa kembali bahwa callback Anda telah terpasang dengan benar.

## Langkah 6 – Kasus Tepi & Masalah Umum

### 1. Gambar di Dalam Tabel atau Header

Aspose memperlakukan mereka sama seperti gambar inline, tetapi markdown mungkin menampilkannya berbeda tergantung pada penampil. Jika Anda perlu mempertahankan tata letak tabel, pertimbangkan mengonversi ke HTML terlebih dahulu, lalu ke markdown dengan alat seperti `pandoc`.

### 2. Format Tidak Didukung

Versi lama Aspose.Words mungkin mengalami kesulitan dengan format baru seperti WebP. Memperbarui ke versi terbaru (atau mengonversi gambar ke PNG terlebih dahulu) menyelesaikan masalah ini.

### 3. Nama File Duplikat

Jika dua gambar memiliki nama yang sama di dalam DOCX, callback akan menimpa yang pertama. Solusi cepat adalah menambahkan sufiks unik:

```java
String uniqueName = args.getResourceFileName() + "_" + UUID.randomUUID();
String fileName = "assets/" + uniqueName + extension;
args.setResourceFileName(fileName);
```

### 4. Dokumen Besar

Untuk file DOCX yang sangat besar (ratusan MB), Anda mungkin ingin men-stream output alih‑alih memuat seluruh file ke memori. Aspose.Words menyediakan `DocumentBuilder` dan `LoadOptions` untuk menangani skenario tersebut, tetapi itu topik untuk tutorial lain.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```java
// File: MarkdownResourceDemo.java
import com.aspose.words.*;
import java.util.UUID;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // 3️⃣ Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Preserve original name, add a UUID if a duplicate might occur
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String baseName = args.getResourceFileName();
                String uniqueName = baseName + "_" + UUID.randomUUID();
                String fileName = "assets/" + uniqueName + extension;
                args.setResourceFileName(fileName);
            }
        });

        // 4️⃣ Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);

        System.out.println("Conversion complete! Check output/doc.md and the assets folder.");
    }
}
```

### Hasil yang Diharapkan

- `output/doc.md` berisi sintaks markdown dengan referensi gambar seperti `![Image1](assets/Image1_3f9c2a4e-... .png)`.
- Semua gambar yang diekstrak berada di bawah `output/assets/`.
- Tidak perlu menyalin file secara manual; callback menangani semuanya.

## Kesimpulan

Anda kini tahu **cara menyimpan gambar Word** saat Anda **mengonversi docx ke markdown** menggunakan Aspose.Words untuk Java. Langkah‑langkah kunci adalah memuat dokumen, mengonfigurasi sebuah `Markdown

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}