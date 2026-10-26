---
category: general
date: 2026-10-26
description: Pelajari cara menentukan encoding di Java menggunakan LoadOptions. Panduan
  ini mencakup pengkodean karakter, metode setEncoding, dan opsi pemuatan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: id
lastmod: 2026-10-26
og_description: Cara menentukan encoding di Java menggunakan Aspose.Words. Ikuti tutorial
  lengkap ini untuk memuat dokumen dengan set karakter yang benar.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Cara menentukan encoding di Java dengan Aspose.Words – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Cara menentukan encoding saat memuat dokumen dengan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menentukan encoding saat memuat dokumen dengan Aspose.Words untuk Java

Jika Anda perlu **cara menentukan encoding** untuk file sumber di Java, tutorial ini menunjukkan langkah‑langkah tepatnya. Baik dokumen menggunakan Big5, UTF‑8, atau set karakter lainnya, Anda dapat mengontrol proses pembacaan dengan `LoadOptions`. Pada akhir panduan Anda akan memahami mengapa encoding karakter penting, cara menerapkan metode `setEncoding`, dan cara memverifikasi bahwa dokumen dimuat dengan benar.

Memuat dokumen dengan encoding karakter yang tepat mencegah teks menjadi rusak dan memastikan konten multibahasa ditampilkan sebagaimana mestinya. Tutorial ini mencakup:

* Peran **character encoding in Java** saat membaca file.
* Cara mengkonfigurasi **LoadOptions encoding** untuk Aspose.Words.
* Kode praktis yang dapat Anda salin ke dalam proyek Anda.
* Kesalahan umum seperti encoding yang tidak cocok dan cara mengatasinya.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java Development Kit (JDK) 8 atau yang lebih tinggi.
* Maven atau Gradle untuk mengelola dependensi.
* Aspose.Words for Java 23.10 atau yang lebih baru (versi yang digunakan dalam panduan ini).
* Dokumen teks contoh (`input.doc`) yang disimpan dengan encoding yang diinginkan (misalnya, Big5).

Anda tidak memerlukan pustaka tambahan apa pun; contoh ini hanya menggunakan core Aspose.Words API.

## Langkah 1: Tambahkan Aspose.Words ke proyek Anda

Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Untuk Gradle, letakkan baris ini di `build.gradle` Anda:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Menyertakan pustaka membuat kelas `LoadOptions`, `Document`, dan `Encoding` tersedia.

## Langkah 2: Buat instance `LoadOptions`

`LoadOptions` memungkinkan Anda menyesuaikan cara Aspose.Words membuka file. Membuat objek ini adalah bagian pertama dari **cara menentukan encoding**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Objek `LoadOptions` dimulai dengan pengaturan default. Anda akan menyesuaikan propertinya pada langkah berikutnya.

## Langkah 3: Tetapkan encoding karakter yang diinginkan

Metode `setEncoding` menentukan **character encoding in Java** yang harus digunakan oleh loader. Dalam contoh ini kami memilih halaman kode Big5, yang umum untuk file teks bahasa Mandarin tradisional.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Mengapa ini penting*: Jika byte file diinterpretasikan dengan halaman kode yang salah, karakter akan muncul sebagai tanda tanya atau gibberish. Dengan secara eksplisit memanggil `setEncoding`, Anda memberi tahu Aspose.Words untuk mendekode aliran byte menggunakan tabel pemetaan Big5.

Anda dapat mengganti `"Big5"` dengan nama charset apa pun yang dikenali oleh Java, seperti `"UTF-8"`, `"ISO-8859-1"`, atau `"Windows-1252`. Metode ini melempar `UnsupportedEncodingException` jika nama tidak valid, jadi Anda mungkin ingin menangkap pengecualian tersebut dalam kode produksi.

## Langkah 4: Muat dokumen dengan opsi yang dikonfigurasi

Sekarang **LoadOptions encoding** sudah diatur, berikan opsi tersebut ke konstruktor `Document`. Langkah ini menyelesaikan alur kerja inti **cara menentukan encoding**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Ganti `YOUR_DIRECTORY` dengan path absolut atau relatif ke file Anda. Instance `Document` kini berisi konten yang sepenuhnya diparse, menghormati encoding yang Anda berikan.

## Langkah 5: Verifikasi bahwa teks dimuat dengan benar

Verifikasi cepat membantu Anda memastikan bahwa encoding telah diterapkan seperti yang diharapkan. Anda dapat mengekstrak teks dokumen dan mencetaknya ke konsol:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Jika konsol menampilkan karakter Mandarin yang dapat dibaca (atau bahasa yang Anda harapkan), encoding berhasil. Jika Anda masih melihat output yang rusak, periksa kembali encoding file asli dan pastikan nama charset cocok persis.

## Menangani kasus tepi umum

### 5.1 Memuat dari `InputStream`

Kadang-kadang Anda menerima dokumen sebagai aliran (mis., dari layanan web). Anda masih dapat mengontrol encoding dengan mengirimkan aliran bersama `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Opsi **document loading options** yang sama berlaku, dan pemanggilan `setEncoding` tetap tidak berubah.

### 5.2 Cadangan ketika encoding tidak diketahui

Jika Anda tidak dapat menentukan charset file sumber, Anda dapat mencoba pustaka deteksi (seperti ICU4J) sebelum mengatur encoding. Setelah Anda memiliki perkiraan, panggil `setEncoding` dengan nilai tersebut. Pendekatan ini mengurangi risiko teks yang terdecode salah.

### 5.3 Menangani encoding yang tidak didukung

Java mendukung berbagai halaman kode, tetapi beberapa encoding legacy mungkin tidak tersedia. Dalam kasus tersebut, pertimbangkan untuk mengonversi file ke UTF‑8 secara eksternal (mis., menggunakan `iconv`) sebelum memuatnya dengan Aspose.Words. Setelah konversi, Anda dapat menghilangkan pemanggilan `setEncoding` karena UTF‑8 adalah default untuk sebagian besar API modern.

## Tips pro: Gunakan kembali `LoadOptions` untuk pemrosesan batch

Jika Anda perlu memuat banyak dokumen yang menggunakan charset yang sama, buat satu instance `LoadOptions` dan gunakan kembali:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Menggunakan kembali objek mengurangi overhead pembuatan objek dan menjamin encoding yang konsisten di seluruh batch.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang menggabungkan semua langkah, menyertakan impor yang diperlukan, dan menangani kemungkinan pengecualian.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Output yang diharapkan** (asumsi file sumber berisi teks Mandarin yang diencode dalam Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Jika output menampilkan simbol yang tidak dapat dibaca, tinjau kembali nama charset atau verifikasi encoding asli file.

## Pertanyaan yang sering diajukan

**Apakah ini bekerja dengan format dokumen lain (DOCX, RTF, HTML)?**  
Ya. Objek `LoadOptions` yang sama berlaku untuk format apa pun yang didukung oleh Aspose.Words. Satu‑satunya persyaratan adalah file yang mendasarinya memang menggunakan charset yang ditentukan.

**Bagaimana jika saya perlu mengubah encoding setelah dokumen dimuat?**  
Encoding hanya memengaruhi fase pembacaan. Setelah objek `Document` ada, representasi Unicode internalnya independen dari charset asli. Untuk mengubah encoding output, sesuaikan `SaveOptions` saat Anda menulis file.

**Apakah saya dapat menggunakan pendekatan ini dengan pustaka lain (mis., Apache POI)?**  
Apache POI menangani deteksi charset-nya sendiri untuk format biner lama, tetapi konsep menyediakan charset ke loader serupa. Untuk Aspose.Words, `LoadOptions` adalah cara resmi untuk mengontrol **cara menentukan encoding**.

## Kesimpulan

Anda sekarang tahu **cara menentukan encoding** saat memuat dokumen dengan Aspose.Words untuk Java. Dengan membuat objek `LoadOptions`, memanggil metode `setEncoding`, dan memberikan opsi tersebut ke konstruktor `Document`, Anda memastikan byte file diinterpretasikan dengan benar. Praktik ini menghilangkan teks yang rusak, mendukung konten multibahasa, dan terintegrasi mulus dengan pemrosesan batch atau alur kerja berbasis stream.

Jelajahi topik terkait seperti **document loading options**, **saving with specific encodings**, dan **handling Unicode in Java** untuk memperdalam penguasaan Anda dalam pemrosesan teks. Bereksperimenlah dengan nama charset yang berbeda, gabungkan pendekatan ini dengan konversi PDF, atau integrasikan ke dalam layanan web yang menerima unggahan dalam berbagai encoding.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}