---
category: general
date: 2026-01-11
description: Pelajari cara menyisipkan gambar dalam Markdown saat mengonversi file
  DOCX, menggunakan Base64 untuk gambar kecil, dan menyimpan sumber daya yang lebih
  besar secara terpisah.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: id
og_description: Pelajari cara menyematkan gambar dalam Markdown saat mengonversi file
  DOCX, menggunakan Base64 untuk gambar kecil dan menyimpan sumber daya yang lebih
  besar secara terpisah.
og_title: Cara Menyisipkan Gambar dalam Markdown Saat Mengonversi DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Cara Menyisipkan Gambar dalam Markdown Saat Mengonversi DOCX
url: /id/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyisipkan Gambar dalam Markdown Saat Mengonversi DOCX

Pernah bertanya-tanya **bagaimana cara menyisipkan gambar** dalam file Markdown yang berasal dari dokumen Word? Anda tidak sendirian. Kebanyakan pengembang mengalami masalah ketika konversi menghilangkan gambar atau menyimpannya dengan cara yang merusak tata let akhir.  

Dalam panduan ini kami akan menelusuri contoh lengkap yang siap dijalankan yang menunjukkan **bagaimana cara menyisipkan gambar** sebagai Base64 data URIs untuk grafik kecil, sementara aset yang lebih ditulis ke folder samping. Sepanjang jalan kami juga akan membahas **convert docx to markdown**, menyentuh **how to convert docx** dengan Aspose.Words, dan menjelaskan perbedaan antara menyisipkan gambar sebagai Base64 versus mengekspornya sebagai file terpisah.  

> **Pro tip:** Jika Anda hanya membutuhkan proof‑of‑concept cepat, kode di bawah ini berfungsi langsung dengan satu dependensi Maven.

---

## Apa yang Anda Butuhkan

- **Java 17** (atau JDK terbaru apa pun) – API berfokus pada Java, tetapi konsepnya dapat diterapkan ke bahasa lain.
- **Aspose.Words for Java** – perpustakaan komersial yang mendukung konversi DOCX → Markdown.
- Sebuah **sample DOCX** yang berisi campuran ikon kecil dan foto yang lebih besar.
- Sebuah folder tempat Anda ingin menyimpan Markdown dan sumber dayanya.

Tidak ada kerangka kerja tambahan, tidak ada skrip eksternal. Hanya Java biasa dan Aspose.Words.

---

## Langkah 1 – Tambahkan Aspose.Words ke Proyek Anda (convert docx to markdown)

Jika Anda menggunakan Maven, letakkan cuplikan berikut ke dalam `pom.xml` Anda. Silakan ganti versi dengan rilis terbaru pada saat Anda membaca.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Aspose.Words menangani pekerjaan berat dalam mengurai struktur DOCX, mengekstrak gambar, dan merender sintaks Markdown. Mencoba membuat parser sendiri akan menjadi lubang kelinci yang mungkin tidak perlu Anda masuki.

---

## Langkah 2 – Muat Dokumen DOCX Sumber

Pertama, arahkan API ke file Word yang ingin Anda transformasi. Konstruktor `Document` melakukan semua pekerjaan—tidak diperlukan penguraian XML manual.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Perhatikan komentar yang menjelaskan *mengapa* baris ini penting: tanpa instance `Document` tidak ada yang dapat dikonversi.

---

## Langkah 3 – Siapkan MarkdownSaveOptions dengan Callback Penyimpanan Sumber Daya

Inilah inti dari **bagaimana cara menyisipkan gambar** dengan benar. Callback memberi Anda hook untuk setiap sumber daya (gambar, gaya, dll.) yang ingin ditulis oleh konverter.

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

### Mengapa Callback?

- **Control:** Anda memutuskan apakah gambar menjadi string Base64 inline atau file terpisah.
- **Performance:** Ikon kecil menjadi bagian dari Markdown, menghilangkan permintaan HTTP tambahan.
- **Portability:** Gambar yang lebih besar tetap sebagai file eksternal, menjaga ukuran Markdown tetap wajar.

---

## Langkah 4 – Simpan Dokumen sebagai Markdown

Akhirnya, beri tahu Aspose.Words untuk menulis file Markdown menggunakan opsi yang baru saja kami konfigurasikan.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Menjalankan program menghasilkan dua hal:

1. `output.md` – representasi Markdown dari DOCX asli Anda.
2. Sebuah folder `markdown_resources` yang berisi gambar besar yang tidak disisipkan.

---

## Contoh Lengkap yang Berfungsi (Semua Langkah dalam Satu Tempat)

Berikut adalah file sumber lengkap, siap disalin‑tempel ke IDE Anda. Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya di mesin Anda.

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

**Expected output:** Buka `output.md` di penampil Markdown apa pun. Ikon kecil muncul inline, misalnya:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Gambar yang lebih besar direferensikan seperti:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Itulah tepatnya yang Anda butuhkan untuk **menyisipkan gambar** sambil tetap menjaga ukuran file tetap dapat dikelola.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika gambar berupa JPEG bukan PNG?

Callback di atas selalu menambahkan prefiks URI dengan `image/png`. Untuk JPEG, Anda dapat memeriksa beberapa byte pertama dari `args.getData()` atau menggunakan `args.getFileName()` untuk menebak tipe MIME yang tepat:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Bisakah saya mengubah ambang batas ukuran?

Tentu saja. Batas `10_000` byte hanyalah contoh. Jika Anda memiliki anggaran bandwidth yang cukup, naikkan menjadi 50 KB atau lebih. Sebaliknya, turunkan jika Anda membutuhkan file Markdown yang sangat ringan.

### Apakah ini bekerja dengan tabel atau objek Word lainnya?

Ya. Aspose.Words secara otomatis mengonversi tabel, daftar, dan bahkan catatan kaki ke Markdown. Callback sumber daya hanya memproses gambar, jadi Anda tidak memerlukan kode tambahan untuk elemen lain.

### Bagaimana dengan nama file non‑ASCII?

API dengan aman mengenkode nama file Unicode saat menulis ke folder `markdown_resources`. Pastikan sistem file Anda mendukung UTF‑8 (sebagian besar OS modern melakukannya).

---

## Tips Pro untuk Konversi yang Lancar

- **Keep the output folder clean.** Jalankan `Files.createDirectories` hanya sekali per konversi, atau hapus folder sebelum setiap run jika Anda menginginkan awal yang bersih.
- **Validate the Markdown.** Alat seperti `markdownlint` dapat menangkap karakter stray yang diperkenalkan oleh string Base64 yang tidak terbentuk dengan baik.
- **Version lock Aspose.Words.** Versi spesifik memastikan kode Anda tetap berfungsi meski rilis mayor berikutnya mengubah perilaku default.
- **Use a .gitignore** entry untuk `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}