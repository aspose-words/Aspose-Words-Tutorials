---
category: general
date: 2026-10-20
description: Konfigurasikan encoding LoadOptions di Java untuk membaca dokumen dengan
  benar dan ubah encoding dokumen menjadi UTF-8 dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: id
lastmod: 2026-10-20
og_description: Konfigurasikan enkoding LoadOptions di Java untuk memastikan penanganan
  karakter yang benar dan pelajari cara mengubah enkoding dokumen menjadi UTF-8 menggunakan
  Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Konfigurasikan enkoding LoadOptions di Java – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Cara mengonfigurasi enkoding LoadOptions di Java
url: /id/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengonfigurasi enkoding LoadOptions di Java

Jika Anda perlu **mengonfigurasi enkoding LoadOptions** di Java, panduan ini menunjukkan cara mengatur set karakter yang tepat dan kemudian **mengubah enkoding dokumen menjadi UTF-8** menggunakan Aspose.Words. Enkoding yang benar mencegah teks yang rusak saat memuat file yang menggunakan halaman kode warisan seperti Big5, Shift_JIS, atau Windows‑1252.

Anda akan belajar cara:

* membuat instance `LoadOptions` dengan enkoding tertentu,
* memuat dokumen sumber yang menggunakan enkoding tersebut,
* menyimpan dokumen dalam enkoding berbeda (UTF‑8) tanpa kehilangan data,
* memverifikasi bahwa konversi berhasil.

Tutorial ini mengasumsikan Anda memiliki lingkungan pengembangan Java dasar dan lisensi Aspose.Words untuk Java yang valid. Tidak diperlukan alat eksternal.

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|-----------------|
| Java 17 atau lebih baru | Menyediakan fitur bahasa modern dan dukungan jangka panjang. |
| Aspose.Words untuk Java (v23.9 atau lebih baru) | `LoadOptions` class berada dalam pustaka ini. |
| Dokumen sumber yang dienkode dengan halaman kode warisan (mis., Big5) | Menunjukkan kebutuhan akan enkoding khusus. |
| IDE atau alat build (Maven/Gradle) | Memudahkan kompilasi dan menjalankan contoh. |

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda jika menggunakan Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Mengonfigurasi enkoding LoadOptions

Langkah pertama adalah memberi tahu Aspose.Words set karakter apa yang diharapkan saat membaca file. Ini dilakukan dengan mengonfigurasi objek `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Mengapa ini penting:** Ketika dokumen disimpan dengan enkoding warisan, loader default mengasumsikan UTF‑8. Dengan secara eksplisit mengatur enkoding, Anda menghindari mojibake (karakter rusak) dan mempertahankan teks asli.

### Tips Pro
Jika Anda tidak yakin enkoding apa yang digunakan file, Anda dapat memeriksa byte‑order mark (BOM) atau menanyakan kepada penyedia dokumen. Enkoding warisan umum meliputi `Big5`, `Shift_JIS`, dan `Windows-1252`.

## Memuat dokumen dengan opsi yang dikonfigurasi

Sekarang `LoadOptions` sudah siap, muat file sumber. Konstruktor yang menerima jalur file dan instance `LoadOptions` memastikan enkoding khusus diterapkan.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Mengapa ini penting:** Objek `Document` kini berisi teks persis seperti yang muncul di file asli, karena loader menghormati halaman kode Big5 yang Anda berikan.

## Mengubah enkoding dokumen menjadi UTF-8

Aspose.Words menyimpan teks secara internal sebagai Unicode, sehingga proses penyimpanan dokumen menentukan enkoding eksternal. Untuk menghasilkan file UTF‑8, cukup simpan tanpa menentukan enkoding tambahan—UTF‑8 adalah default untuk format Office Open XML modern. Namun, Anda dapat menegaskannya secara eksplisit untuk kejelasan.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Jika Anda perlu menghasilkan representasi teks biasa (mis., `.txt`) dengan UTF‑8, berikan objek `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Mengapa ini penting:** Menyimpan sebagai UTF‑8 menjamin bahwa sistem hilir mana pun—layanan web, basis data, atau editor modern—dapat membaca file tanpa langkah konversi tambahan.

## Verifikasi konversi

Cara cepat untuk memastikan bahwa perubahan enkoding berhasil adalah dengan membaca kembali file yang disimpan menggunakan pembaca UTF‑8 dan mencetak beberapa karakter.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Jika output menampilkan karakter yang dapat dibaca (tanpa simbol �), konversi berhasil seperti yang diharapkan.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program mandiri yang menggabungkan semua langkah. Ganti jalur file dengan lokasi Anda sendiri.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Output yang diharapkan**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Jika karakter muncul dengan benar, Anda telah berhasil **mengonfigurasi enkoding LoadOptions** dan **mengubah enkoding dokumen menjadi UTF-8**.

## Kesalahan umum dan cara menghindarinya

| Gejala | Penyebab | Solusi |
|--------|----------|--------|
| Karakter rusak setelah memuat | `LoadOptions` tidak diatur atau nama charset salah | Pastikan `loadOptions.setEncoding(Charset.forName("Big5"))` sesuai dengan halaman kode file sumber. |
| `UnsupportedEncodingException` | Nama charset salah eja | Gunakan nama tepat yang tercantum di `Charset.availableCharsets()`. |
| File output masih menunjukkan mojibake | Disimpan sebagai format warisan (mis., `.rtf`) tanpa opsi UTF‑8 | Gunakan `TxtSaveOptions` dengan `setEncoding("UTF-8")` atau simpan sebagai `.docx`. |
| Penurunan kinerja pada file besar | Membuat ulang `LoadOptions` untuk setiap dokumen | Gunakan kembali satu instance `LoadOptions` saat memproses banyak file dengan enkoding sumber yang sama. |

## Kesimpulan

Anda kini tahu cara **mengonfigurasi enkoding LoadOptions** di Java untuk membaca dokumen yang dienkode warisan dan cara **mengubah enkoding dokumen menjadi UTF-8** untuk konsumsi hilir yang aman. Pendekatan ini bekerja untuk setiap halaman kode yang didukung oleh kelas `Charset` Java, menjadikannya solusi fleksibel untuk aplikasi multibahasa.

Selanjutnya, Anda mungkin ingin menjelajahi:

* **Konversi batch** – iterasi folder dokumen dan terapkan logika enkoding yang sama.
* **Deteksi enkoding** – gunakan pustaka seperti juniversalchardet untuk mendeteksi otomatis charset sumber sebelum mengonfigurasi `LoadOptions`.
* **Mempertahankan format** – bereksperimen menyimpan ke PDF atau HTML sambil menjaga kepatuhan UTF‑8.

Silakan sesuaikan kode dengan arsitektur proyek Anda, dan biarkan API Aspose.Words yang kuat menangani pekerjaan berat manipulasi dokumen.

![Potongan kode yang menunjukkan konfigurasi enkoding LoadOptions dan penyimpanan dokumen](/images/encoding-demo.png){: .align-center alt="Mengonfigurasi enkoding LoadOptions dalam contoh kode Java"}

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cara Mengonversi Teks RTF dengan Enkoding UTF-8 di Java Menggunakan Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Memulihkan Dokumen Word DOCX yang Rusak Menggunakan Aspose.Words LoadOptions – Panduan Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}