---
category: general
date: 2026-05-30
description: Daftarkan callback peringatan di Java untuk melacak font yang hilang
  dan menyesuaikan pemuatan dokumen dengan Aspose.Words. Pelajari solusi lengkap langkah
  demi langkah.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: id
og_description: Daftarkan callback peringatan di Java untuk melacak font yang hilang
  dan menyesuaikan pemuatan dokumen. Panduan lengkap dengan kode dan penjelasan.
og_title: Daftarkan callback peringatan di Java – Lacak font yang hilang
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Daftarkan callback peringatan di Java – Lacak font yang hilang
url: /id/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftarkan callback peringatan di Java – Lacak font yang hilang

Pernah bertanya-tanya bagaimana cara **melacak font yang hilang** saat memuat dokumen Word dengan Aspose.Words for Java? Mungkin Anda pernah melihat substitusi font yang diam-diam dan berpikir, “Apa yang terjadi pada tata letak saya?” Kabar baiknya, Anda tidak perlu menebak. Dengan **mendaftarkan callback peringatan**, Anda dapat menangkap setiap peristiwa substitusi font pada saat dokumen dibaca, dan Anda juga dapat **menyesuaikan pemuatan dokumen** agar sesuai dengan alur kerja Anda.

Dalam tutorial ini kami akan membahas contoh dunia nyata yang menunjukkan secara tepat cara menyiapkan callback, mengapa hal itu penting, dan bagaimana menjaga sisa alur pemrosesan Anda tetap bersih. Pada akhir tutorial Anda akan memiliki kelas Java siap‑jalankan yang mencetak setiap peringatan font yang hilang dan menyimpan salinan dokumen yang telah diproses. Tidak memerlukan referensi eksternal—hanya kode murni yang dapat dijalankan.

> **Apa yang akan Anda dapatkan:**  
> • Sebuah program Java lengkap menggunakan Aspose.Words  
> • Penjelasan langkah‑demi‑langkah untuk setiap baris  
> • Tips untuk menangani kasus tepi seperti file terenkripsi atau batch besar  
> • Pemeriksaan cepat yang dapat Anda jalankan pada file `.docx` apa pun

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- **Java 17** (atau JDK terbaru apa pun) terpasang dan `JAVA_HOME` sudah diset.  
- **Aspose.Words for Java** JAR di classpath Anda. Anda dapat mengambil versi terbaru dari repositori Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Sebuah dokumen Word contoh (`input.docx`) yang Anda curigai berisi font yang tidak terpasang di mesin Anda.  
- IDE atau alat build baris perintah (Maven/Gradle) yang Anda kuasai.

Itu saja. Tidak ada font tambahan, tidak ada layanan tambahan—hanya Java biasa dan Aspose.Words.

## Mengapa mendaftarkan callback peringatan?

Anggap **callback peringatan** sebagai kamera keamanan untuk proses pemuatan dokumen Anda. Ketika Aspose.Words menemukan glyph yang hilang, ia tidak melemparkan pengecualian; ia diam‑diam mengganti dengan font cadangan. Substitusi diam itu dapat merusak tata letak Anda, terutama pada PDF atau faktur yang kritis terhadap merek. Dengan mendaftarkan callback Anda:

1. **Dapatkan wawasan waktu‑nyata** – setiap peringatan `FONT_SUBSTITUTION` dikirim secara instan.  
2. **Catat atau reaksi** – Anda dapat mencatat ke file, mengirim peringatan, atau bahkan mengganti font secara programatis.  
3. **Pertahankan output bersih** – mengetahui font mana yang hilang memungkinkan Anda memperbaiki dokumen sumber sebelum dipublikasikan.

Singkatnya, callback mengubah masalah tersembunyi menjadi terlihat, menjadikan alur dokumen Anda jauh lebih dapat diandalkan.

## Langkah 1 – Buat `LoadOptions` untuk menyesuaikan cara dokumen dimuat

Hal pertama yang kita lakukan adalah menginstansiasi `LoadOptions`. Objek ini adalah gerbang untuk setiap penyesuaian saat pemuatan yang mungkin Anda perlukan, mulai dari penanganan kata sandi hingga fitur **mendaftarkan callback peringatan** kami.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Mengapa tidak langsung memanggil `new Document("file.docx")`? Karena tanpa `LoadOptions` Anda kehilangan kesempatan untuk menyisipkan ke dalam peristiwa pemuatan. `LoadOptions` adalah satu‑satunya tempat Aspose.Words memungkinkan Anda **menyesuaikan pemuatan dokumen**.

## Langkah 2 – Daftarkan callback peringatan untuk melacak font yang hilang

Sekarang hadir bintang utama: kami **mendaftarkan callback peringatan** yang mengimplementasikan `IWarningCallback`. Di dalam metode `warning` kami menyaring `WarningType.FONT_SUBSTITUTION` dan mencetak pesan yang membantu.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Beberapa hal yang perlu dicatat:

- **Mengapa `IWarningCallback`?** Ini adalah antarmuka yang digunakan Aspose.Words untuk semua jenis peringatan, memberikan Anda satu titik masuk untuk banyak masalah yang mungkin terjadi.  
- **Penyaringan sangat penting** – tanpa pemeriksaan `if` Anda akan melihat peringatan tentang gambar yang hilang, fitur yang sudah usang, dll., yang akan memenuhi log Anda.  
- **Keamanan thread** – callback dijalankan pada thread yang sama dengan proses pemuatan dokumen, sehingga Anda dapat memperbarui struktur bersama dengan aman jika perlu mengumpulkan hasil nanti.

Potongan kode tersebut **mendaftarkan callback peringatan**, dan mulai saat itu setiap peristiwa font yang hilang akan dicetak ke `stdout`. Ini adalah inti dari **melacak font yang hilang**.

## Langkah 3 – Muat dokumen menggunakan `LoadOptions` yang telah dikonfigurasi

Dengan callback yang sudah dipasang, kami akhirnya memuat file. Jika dokumen merujuk pada font yang tidak Anda miliki, callback akan dipicu sebelum objek dokumen selesai dibangun.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya di mesin Anda. Konstruktor `Document` membaca file, menerapkan kata sandi (jika Anda mengatur satu di `loadOptions`), dan memicu callback peringatan untuk setiap font yang hilang. Anda akan melihat output seperti:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Baris itu membuktikan Anda telah berhasil **melacak font yang hilang**.

## Langkah 4 – Lanjutkan memproses dokumen (opsional)

Pada tahap ini Anda dapat memanipulasi dokumen sesuka hati—mengganti teks, menyisipkan gambar, atau bahkan secara program mengganti font yang disubstitusi. Callback sudah memberikan Anda daftar font bermasalah, sehingga Anda dapat, misalnya, menyematkan font cadangan:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Silakan lewati blok ini jika Anda hanya perlu **melacak font yang hilang**. Intinya, Anda kini memiliki informasi yang diperlukan untuk membuat keputusan yang tepat.

## Langkah 5 – Simpan dokumen yang telah diproses

Akhirnya, simpan dokumen. Anda dapat menimpa yang asli, menyimpan ke lokasi baru, atau mengekspor ke PDF—semua tanpa kehilangan data peringatan yang Anda tangkap sebelumnya.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Menjalankan seluruh kelas akan menghasilkan output konsol untuk setiap font yang hilang dan file baru bernama `processed.docx` di folder yang sama.

## Contoh Kerja Lengkap

Berikut adalah kelas Java lengkap yang dapat Anda salin‑tempel ke IDE Anda. Kelas ini mencakup semua yang telah dibahas, ditambah pembungkus metode `main` kecil.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Output yang Diharapkan

Saat Anda menjalankan program terhadap dokumen yang menggunakan font yang tidak terpasang di sistem Anda, Anda akan melihat sesuatu seperti:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Jika dokumen tidak mengandung **font yang hilang**, konsol tetap tenang hingga baris akhir “Document saved successfully.”—tepat seperti yang Anda harapkan dari implementasi **mendaftarkan callback peringatan** yang berperilaku baik.

## Tips Pro & Kesalahan Umum

- **Multiple callbacks?** Aspose.Words hanya memperbolehkan satu handler peringatan. Jika Anda perlu mencatat ke file dan konsol sekaligus, implementasikan callback komposit yang meneruskan peringatan ke beberapa tujuan.  
- **Large batches** – saat memproses ratusan file, pertimbangkan untuk menggunakan kembali satu instance `LoadOptions`; membuatnya per file menambah beban yang tidak perlu.  
- **Encrypted docs** – setel kata sandi pada `LoadOptions` sebelum memuat, jika tidak Anda akan mendapatkan `IncorrectPasswordException` sebelum callback pernah dipicu.  
- **Performance** – callback berjalan secara sinkron. Jika Anda mencatat ke layanan remote, buffer pesan dan flush setelah pemuatan selesai untuk menghindari bottleneck I/O.  
- **Font fallback** – Anda juga dapat menyediakan koleksi `FontSource` khusus jika memiliki font proprietari yang ingin dipertimbangkan Aspose.Words sebelum kembali ke font sistem.

## Kesimpulan

Anda baru saja mempelajari cara **mendaftarkan callback peringatan** di Java, secara efektif **melacak font yang hilang**, dan **menyesuaikan pemuatan dokumen** dengan Aspose.Words. Solusi ini mandiri, dijalankan dengan satu metode `main`, dan memberi Anda visibilitas langsung terhadap setiap substitusi font yang sebaliknya tidak terlihat.

Langkah selanjutnya? Coba perpanjang callback untuk menulis peringatan ke file CSV untuk keperluan audit, atau gabungkan dengan pemroses batch yang secara otomatis menyematkan font yang hilang. Anda juga dapat menjelajahi jenis peringatan lain seperti `IMAGE_SUBSTITUTION` atau `DEPRECATED_FEATURE`—pola yang sama berlaku.

Selamat coding, dan semoga dokumen Anda selalu ditampilkan persis seperti yang Anda inginkan!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## Apa yang Harus Anda Pelajari Selanjutnya?

- [Callback Peringatan di Dokumen Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Sesuaikan Warna Tema & Font di Aspose.Words Java: Panduan Komprehensif](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Lacak Perubahan dalam Dokumen Word Menggunakan Aspose.Words Java: Panduan Lengkap Revisi Dokumen](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}