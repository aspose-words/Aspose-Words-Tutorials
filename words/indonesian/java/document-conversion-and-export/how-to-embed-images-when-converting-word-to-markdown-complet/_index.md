---
category: general
date: 2026-02-28
description: Pelajari cara menyematkan gambar saat Anda mengonversi dokumen ke markdown.
  Ekspor markdown dengan gambar dan dapatkan gambar inline dalam markdown menggunakan
  Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: id
og_description: Temukan cara menyisipkan gambar saat mengonversi dokumen Word ke Markdown.
  Panduan ini menunjukkan cara mengekspor markdown dengan gambar dan mempertahankannya
  tetap inline.
og_title: Cara Menyematkan Gambar Saat Mengonversi Word ke Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Cara Menyisipkan Gambar Saat Mengonversi Word ke Markdown – Panduan Lengkap
url: /id/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyematkan Gambar Saat Mengonversi Word ke Markdown – Panduan Lengkap

Pernah bertanya-tanya **cara menyematkan gambar** dalam file Markdown yang Anda hasilkan dari dokumen Word? Mungkin Anda sudah mencoba ekspor cepat, hanya untuk berakhir dengan sekumpulan file gambar yang terputus dan tautan yang rusak. Itu adalah masalah umum—terutama ketika Anda membutuhkan satu file `.md` yang portabel untuk dimasukkan ke generator situs statis atau README GitHub.

Kabar baik? Anda dapat memberi tahu exporter untuk menyisipkan setiap gambar sebagai string yang dikodekan Base64, sehingga Markdown yang dihasilkan menjadi mandiri. Dalam tutorial ini kami akan membahas langkah‑langkah tepat, menunjukkan kode Java lengkap, dan menjelaskan mengapa setiap bagian penting. Pada akhir tutorial Anda akan dapat **mengonversi doc ke markdown** dengan gambar tersemat, dan Anda juga akan melihat cara menyesuaikan proses untuk skenario lain seperti “ekspor markdown dengan gambar” atau “menyematkan gambar dalam markdown”.

## Apa yang Akan Anda Pelajari

- Pustaka yang diperlukan dan penyiapan proyek minimal.  
- Cara mengonfigurasi `MarkdownSaveOptions` sehingga gambar menjadi data URI Base64.  
- Mengapa menggunakan `ResourceSavingCallback` adalah cara paling bersih untuk mengontrol penanganan gambar.  
- Cara memverifikasi bahwa file Markdown memang berisi gambar yang tersemat.  
- Tips untuk kasus tepi (gambar besar, tipe MIME berbeda, dan pertimbangan kinerja).  

Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words; latar belakang Java dasar sudah cukup.

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | API Aspose.Words untuk Java menargetkan Java 8+, tetapi menggunakan JDK terbaru memberi Anda utilitas `Base64` bawaan. |
| **Aspose.Words for Java** (latest version) | Pustaka ini menyediakan `MarkdownSaveOptions` dan infrastruktur callback yang akan kami gunakan. |
| **A Word document** (`.docx`) that contains at least one image | Kami membutuhkan sesuatu untuk dikonversi; contoh mengasumsikan file bernama `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | Untuk mengompilasi dan menjalankan contoh dengan cepat. |

Tambahkan dependensi Aspose ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Berikut cuplikan Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Jika Anda lebih suka Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Tip pro:** Aspose menawarkan percobaan gratis selama 30 hari. Dapatkan kunci lisensi sementara dan daftarkan lebih awal untuk menghindari pesan watermark.

## Langkah 1: Buat Markdown Save Options

Hal pertama yang kita lakukan adalah menginstansiasi `MarkdownSaveOptions`. Objek ini memberi tahu Aspose bagaimana kami ingin konversi berperilaku—penanganan font, pemformatan daftar, dan yang paling penting bagi kami, penanganan gambar.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Di Java sintaksnya identik; cukup ganti kata kunci `csharp` dengan `java` pada blok kode selanjutnya.  
Mengapa ini penting: tanpa menyesuaikan opsi, Aspose akan menulis setiap gambar ke file terpisah di samping `.md`. Dengan menyiapkan objek opsi sekarang, kami memberi diri kami kait untuk mencegat perilaku default tersebut.

## Langkah 2: Intersep Sumber Daya Gambar dan Enkode menjadi Base64

Aspose memicu callback setiap kali ingin menulis sebuah sumber daya (gambar, CSS, dll.). Dengan mengimplementasikan `IResourceSavingCallback` kami dapat memutuskan apa yang dilakukan dengan setiap sumber daya. Potongan kode di bawah memeriksa apakah sumber daya adalah gambar, menghapus nama file (sehingga tidak ada file eksternal yang dibuat), mengenkripsi data biner ke Base64, dan menetapkan tipe MIME yang tepat.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Apa yang terjadi di balik layar?**

1. **`args.getResourceType()`** – Aspose mengklasifikasikan setiap blob yang keluar. Kami hanya peduli pada `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – Dengan mengatur nama file menjadi null kami memberi tahu pustaka *untuk tidak* menulis file fisik.  
3. **`Base64.getEncoder().encodeToString(...)`** – Array byte mentah menjadi string teks yang dapat ditempatkan dengan aman dalam data URI Markdown.  
4. **`args.setResourceContentType("image/png")`** – Ini memastikan tag Markdown yang dihasilkan terlihat seperti `![alt](data:image/png;base64,…)`. Jika dokumen sumber Anda berisi JPEG, Anda dapat memeriksa byte asli dan memilih `"image/jpeg"` sebagai gantinya.

> **Mengapa Base64?**  
> Processor Markdown yang memahami data URI akan menampilkan gambar secara langsung, dan file yang dihasilkan tetap portabel—tidak ada aset tambahan yang perlu disalin. Ini sangat berguna untuk README GitHub atau situs dokumentasi yang melarang sumber daya eksternal.

## Langkah 3: Lakukan Konversi

Setelah opsi siap, cukup muat dokumen Word Anda dan panggil `save`. Jalur yang Anda berikan akan menjadi lokasi file Markdown yang dihasilkan.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Itu saja—dua baris kode konversi sebenarnya. Proses berat (membaca DOCX, mengekstrak gambar, mengonversi paragraf) semuanya ditangani oleh Aspose.

## Langkah 4: Verifikasi Hasil – Gambar Tersemat Muncul

Buka `output/doc.md` di editor teks apa pun. Anda seharusnya melihat sesuatu seperti:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Jika Anda menempelkan Markdown ke penampil yang mendukung data URI (GitHub, pratinjau VS Code, atau generator situs statis), gambar akan ditampilkan tanpa file tambahan.

**Pemeriksaan cepat**:  

- **Cari `data:image/`** – Jika Anda menemukan beberapa string panjang, penyematan berhasil.  
- **Hitung pola `![](`** – Pola tersebut harus sesuai dengan jumlah gambar di file Word asli.

## Menangani Kasus Tepi

### Gambar Besar

Base64 memperbesar ukuran asli sekitar **33 %**. Untuk gambar sangat besar (mis., foto resolusi tinggi), file Markdown dapat menjadi tidak praktis. Pertimbangkan strategi berikut:

| Strategy | When to use |
|----------|--------------|
| **Resize before conversion** – Use `java.awt.Image` to scale down. | Ketika dokumen sumber berisi aset resolusi tinggi yang tidak diperlukan dalam ukuran penuh. |
| **Switch to JPEG** – Change `args.setResourceContentType("image/jpeg")`. | Untuk foto di mana format lossless PNG berlebihan. |
| **Chunk the document** – Split the Word file into sections and export each separately. | Ketika Anda perlu menjaga file Markdown di bawah batas ukuran tertentu (mis., batas 10 MB GitHub). |

### Gambar Non‑PNG

Jika dokumen Word Anda berisi format campuran, Anda dapat mendeteksi tipe MIME secara dinamis:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose sudah mengisi `ResourceContentType`, jadi Anda sering tidak perlu menuliskan secara keras "image/png".

### Tips Kinerja

- **Gunakan kembali satu instance `Base64.Encoder`** jika Anda mengonversi banyak gambar dalam loop.  
- **Aktifkan `markdownSaveOptions.setExportImagesAsBase64(true)`** (jika versi API mendukungnya) untuk menghindari callback sepenuhnya.  
- **Jalankan konversi dalam thread latar belakang** saat memproses dokumen massal di lingkungan server.

## Contoh Kerja Lengkap (Semua Bersatu)

Berikut adalah program Java siap salin‑tempel yang mencakup impor, penanganan error, dan alur lengkap yang kami bahas.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan**: satu file `doc.md` yang berisi gambar Base64 tersemat, siap untuk alat apa pun yang mendukung Markdown.

## Pertanyaan yang Sering Diajukan

**T1: Apakah ini bekerja dengan versi lama Aspose.Words?**  
*Biasanya ya.* API callback telah stabil sejak versi 19. Namun, shortcut `setExportImagesAsBase64` muncul pada rilis yang lebih baru, jadi jika Anda menggunakan build lama, Anda perlu callback eksplisit yang ditunjukkan di atas.

**T2: Bagaimana jika saya perlu mengekspor ke GitHub Flavored Markdown (GFM)?**  
`MarkdownSaveOptions` milik Aspose sudah menghasilkan sintaks yang kompatibel dengan GFM. Satu-satunya langkah tambahan adalah memastikan mesin rendering repositori Anda mendukung data URI—GitHub melakukannya.

**T3: Bisakah saya menggunakan pendekatan ini untuk format lain, seperti HTML?**  
Tentu saja. `ResourceSavingCallback` yang sama bekerja untuk `HtmlSaveOptions`. Cukup ganti kelas opsi dan pertahankan logika Base64.

##

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}