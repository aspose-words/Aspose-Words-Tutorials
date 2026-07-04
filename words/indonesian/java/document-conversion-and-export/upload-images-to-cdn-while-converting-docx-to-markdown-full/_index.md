---
category: general
date: 2026-04-24
description: Unggah gambar ke CDN sambil mengonversi DOCX ke markdown menggunakan
  Aspose.Words. Pelajari cara mengekspor Word ke markdown dengan penanganan gambar
  dan integrasi CDN.
draft: false
keywords:
- upload images to cdn
- convert docx to markdown
- export word to markdown
- how to convert docx
- markdown conversion with images
language: id
og_description: Unggah gambar ke CDN sambil mengonversi DOCX ke markdown. Panduan
  Java langkah demi langkah yang mencakup ekspor Word ke markdown, penanganan gambar,
  dan unggah ke CDN.
og_title: Unggah Gambar ke CDN Saat Mengonversi DOCX ke Markdown – Tutorial Java
tags:
- Java
- Aspose.Words
- Markdown
- CDN
- Document Conversion
title: Unggah Gambar ke CDN Saat Mengonversi DOCX ke Markdown – Panduan Java Lengkap
url: /id/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengunggah Gambar ke CDN Saat Mengonversi DOCX ke Markdown

Pernahkah Anda **mengunggah gambar ke CDN** sebagai bagian dari konversi DOCX‑ke‑Markdown? Anda bukan satu‑satunya. Banyak pengembang menemui kendala ketika markdown yang dihasilkan menunjuk ke file gambar lokal yang tidak pernah sampai ke produksi. Kabar baik? Dengan Aspose.Words for Java Anda dapat mengontrol persis di mana setiap gambar disimpan—apakah tetap di folder “imgs” lokal atau di‑push ke CDN pilihan Anda.

Dalam tutorial ini kami akan menelusuri contoh lengkap yang dapat dijalankan yang **mengonversi dokumen Word ke markdown**, menyimpan gambar dalam sub‑folder, dan menunjukkan cara mengganti path lokal dengan URL CDN. Pada akhir tutorial Anda akan memiliki file markdown siap‑pakai yang merujuk ke gambar yang dihosting di CDN mana pun yang Anda inginkan.

> **Apa yang akan Anda pelajari**
> - Cara memuat file DOCX dengan Aspose.Words.
> - Cara mengonfigurasi `MarkdownSaveOptions` dan mengimplementasikan `IResourceSavingCallback`.
> - Di mana menambahkan logika unggah CDN Anda sendiri.
> - Cara memverifikasi output markdown akhir.

Tidak ada layanan eksternal yang diperlukan untuk langkah‑langkah inti, tetapi kami akan membahas di mana menyambungkan klien HTTP atau SDK jika Anda ingin mengunggah gambar ke Amazon S3, Cloudflare, atau Azure Blob Storage.

---

## Prasyarat

- **Java 17** atau lebih baru (kode dapat dikompilasi dengan versi lebih lama, tetapi 17 adalah LTS saat ini).
- **Aspose.Words for Java** 23.9 atau yang lebih baru. Anda dapat mengambilnya dari Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

- File **DOCX** yang ingin Anda konversi (kami akan menyebutnya `input.docx`).
- Opsional: kredensial untuk CDN Anda jika Anda berencana benar‑benar mengunggah gambar.

---

## Langkah 1 – Memuat Dokumen Word Sumber

Hal pertama yang kami lakukan adalah membaca DOCX ke dalam objek `Document` Aspose. Ini memberi kami akses penuh ke struktur dokumen, termasuk paragraf, tabel, dan sumber daya yang disematkan.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source Word document from the file system
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Mengapa ini penting:**  
> Memuat dokumen di awal memungkinkan kami memeriksa atau memodifikasi isinya sebelum menyentuh penulis markdown. Jika Anda perlu menghapus komentar atau menerapkan gaya, Anda dapat melakukannya tepat setelah baris ini.

---

## Langkah 2 – Menyiapkan Opsi Penyimpanan Markdown

Aspose.Words menyediakan kelas `MarkdownSaveOptions` yang memungkinkan kami menyesuaikan konversi. Pada langkah ini kami membuat sebuah instance dan mengaktifkan callback penyimpanan sumber daya yang akan kami kembangkan selanjutnya.

```java
        // Create save options for Markdown output
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

        // Optional: tweak options (e.g., use GitHub‑flavored markdown)
        saveOptions.setExportImagesAsBase64(false); // keep images as external files
```

> **Tip:** Membiarkan `ExportImagesAsBase64` tetap `false` sangat penting jika Anda ingin mengunggah gambar ke CDN. Gambar yang dikodekan Base64 akan tertanam langsung dalam markdown, meniadakan tujuan hosting eksternal.

---

## Langkah 3 – Mengimplementasikan Callback Penyimpanan Sumber Daya

Berikut adalah inti dari tutorial. `IResourceSavingCallback` dipicu untuk setiap sumber daya eksternal (gambar, CSS, dll.) yang perlu ditulis oleh Aspose. Kami dapat menyela panggilan tersebut, mengunggah gambar ke CDN, lalu menulis ulang referensi markdown.

```java
        // Define a callback to control how external resources (e.g., images) are saved
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Only act on image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a local relative path first (e.g., imgs/picture1.png)
                    String localPath = "imgs/" + args.getResourceFileName();
                    args.setResourceFileName(localPath);

                    // --------------------------------------------------------------
                    // OPTIONAL: Upload to CDN here.
                    // --------------------------------------------------------------
                    // For illustration we’ll pretend to upload and get a CDN URL.
                    // Replace the stub with real SDK calls (AWS S3, Azure Blob, etc.).
                    String cdnUrl = uploadToCdn(args.getResourceBytes(), args.getResourceFileName());

                    // If the upload succeeded, tell Aspose to use the CDN URL instead.
                    if (cdnUrl != null && !cdnUrl.isEmpty()) {
                        args.setResourceUri(cdnUrl);
                    }
                    // --------------------------------------------------------------
                }
            }

            // ----- Helper method that you would replace with real upload logic -----
            private String uploadToCdn(byte[] imageBytes, String fileName) {
                // Placeholder: simulate a CDN URL.
                // In production you might use an HTTP client or cloud SDK.
                // Example: return "https://cdn.example.com/images/" + fileName;
                return "https://cdn.example.com/images/" + fileName;
            }
        });
```

### Mengapa menggunakan callback?

- **Kontrol atas nama file:** Kami menyimpan semuanya di dalam folder `imgs/`, menjaga markdown tetap rapi.
- **Integrasi CDN:** Dengan menetapkan `args.setResourceUri(...)` kami memberi tahu penulis markdown untuk menyisipkan URL CDN alih‑alih path lokal.
- **Masa depan:** Jika Anda beralih ke penyedia CDN lain, Anda hanya perlu mengubah metode `uploadToCdn`.

> **Jebakan umum:** Lupa memanggil `args.setResourceFileName(...)` akan menyebabkan Aspose menaruh gambar di samping file markdown dengan nama acak, yang memutuskan tautan relatif.

---

## Langkah 4 – Menyimpan Dokumen sebagai Markdown

Dengan callback yang sudah terpasang, langkah akhir cukup satu baris yang menulis file markdown. Callback akan berjalan otomatis untuk setiap gambar.

```java
        // Save the document as Markdown, applying the custom resource handling
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Saat program selesai, Anda akan menemukan:

1. `output.md` yang berisi teks markdown dengan referensi gambar yang mengarah ke CDN Anda (misalnya `![](https://cdn.example.com/images/picture1.png)`).
2. Folder `imgs/` yang berisi gambar asli—berguna untuk debugging atau skenario fallback.

---

## Output yang Diharapkan

Misalkan `input.docx` berisi satu gambar bernama `chart.png`, maka `output.md` yang dihasilkan akan terlihat seperti:

```markdown
# My Document Title

Here is an introductory paragraph.

![](https://cdn.example.com/images/chart.png)

More text follows...
```

Gambar kini dilayani dari CDN, artinya konsumen downstream mana pun (GitHub, generator situs statis, dll.) akan mengambilnya dari lokasi edge yang tersebar secara global.

---

## Tips Pro & Kasus Edge

| Situasi | Apa yang Harus Dilakukan |
|-----------|------------|
| **DOCX besar dengan puluhan gambar** | Unggah gambar secara batch secara asynchronous untuk menghindari pemblokiran thread utama. |
| **Format gambar tidak didukung oleh CDN Anda** | Konversi `args.getResourceBytes()` ke format yang didukung (misalnya PNG) sebelum mengunggah. |
| **Anda memerlukan struktur folder khusus per dokumen** | Gunakan `args.setResourceFileName("docs/" + docId + "/" + args.getResourceFileName());` |
| **CDN Anda memerlukan header otentikasi** | Implementasikan unggahan dalam `uploadToCdn` menggunakan URL bertanda tangan atau SDK yang menangani autentikasi. |
| **Anda menginginkan fallback base64 untuk dokumen offline** | Set `saveOptions.setExportImagesAsBase64(true)` *dan* tetap gunakan callback untuk unggahan CDN bila diinginkan. |

---

## Pertanyaan yang Sering Diajukan

**T: Apakah ini bekerja dengan versi Aspose.Words yang lebih lama?**  
J: API `IResourceSavingCallback` diperkenalkan pada versi 20.5. Jika Anda menggunakan rilis yang lebih lama, lakukan upgrade—kode Anda akan kompatibel ke depan dan Anda juga akan mendapatkan peningkatan performa.

**T: Bagaimana jika saya belum memiliki CDN?**  
J: Metode `uploadToCdn` dalam contoh hanya mengembalikan URL palsu. Anda dapat menjalankan konversi tanpa mengunggah ke CDN; markdown akan merujuk ke path lokal `imgs/` sebagai gantinya.

**T: Bisakah saya mengonversi banyak file DOCX secara batch?**  
J: Tentu saja. Bungkus logika dalam loop, berikan `input.docx` dan jalur output yang berbeda tiap iterasi. Ingat untuk menggunakan satu instance `MarkdownSaveOptions` jika memproses banyak file demi kecepatan.

---

## Kesimpulan

Kami baru saja menunjukkan cara **mengunggah gambar ke CDN saat mengonversi DOCX ke markdown** menggunakan Aspose.Words for Java. Prosesnya dapat diringkas menjadi tiga aksi utama:

1. Memuat dokumen Word.  
2. Menyambungkan `IResourceSavingCallback` yang mengunggah setiap gambar dan menulis ulang tautan markdown.  
3. Menyimpan dokumen dengan `MarkdownSaveOptions`.

Itu saja—tanpa skrip post‑processing tambahan, tanpa menyalin‑tempel URL gambar secara manual. Sekarang Anda memiliki file markdown bersih yang siap untuk generator situs statis, portal dokumentasi, atau platform lain yang mendukung markdown.

Siap untuk tantangan berikutnya? Coba ganti unggahan CDN dengan panggilan SDK **Azure Blob Storage**, atau bereksperimen dengan opsi **GitHub‑flavored markdown** (`saveOptions.setExportImagesAsBase64(true)`). Anda bahkan dapat mengintegrasikannya ke dalam pipeline CI/CD yang secara otomatis memublikasikan dokumen yang diperbarui pada setiap commit.

Jika Anda menemukan kendala atau memiliki trik cerdas, silakan tinggalkan komentar di bawah. Selamat coding, dan nikmati kecepatan penyajian gambar dari edge!

---

![Diagram illustrating the upload images to cdn workflow during DOCX to Markdown conversion](upload-images-to-cdn-diagram.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}