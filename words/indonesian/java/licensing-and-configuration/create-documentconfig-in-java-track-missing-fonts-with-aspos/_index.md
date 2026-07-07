---
category: general
date: 2026-07-06
description: Buat DocumentConfig dalam Java untuk melacak font yang hilang menggunakan
  Aspose.Words – panduan lengkap langkah demi langkah untuk pengembang.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: id
og_description: Buat DocumentConfig dalam Java untuk melacak font yang hilang dengan
  Aspose.Words. Pelajari alur kerja lengkap, mulai dari penyiapan hingga penanganan
  peringatan.
og_title: Buat DocumentConfig di Java – Lacak Font yang Hilang
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Buat DocumentConfig di Java – Lacak Font yang Hilang dengan Aspose.Words
url: /id/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat DocumentConfig di Java – Lacak Font yang Hilang dengan Aspose.Words

**Create DocumentConfig in Java** untuk memantau peringatan substitusi font saat memuat dokumen Word. Pernah bertanya-tanya mengapa beberapa karakter terlihat aneh setelah Anda membuka DOCX? Kemungkinan besar font asli tidak ada di mesin, dan Aspose.Words diam‑diam menggantinya. Dalam tutorial ini kami akan menunjukkan cara **melacak font yang hilang** sehingga Anda tidak pernah terkejut oleh glyph yang tidak diinginkan lagi.

Kami akan membahas semua yang Anda perlukan: pengaturan Maven/Gradle, kode yang membuat `DocumentConfig`, `IWarningCallback` khusus yang menyaring hanya peringatan substitusi font, dan cara cepat mencatat pesan‑pesan tersebut. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan yang mencetak setiap peringatan font yang hilang ke konsol (atau ke file, bila Anda lebih suka).

---

## Apa yang Akan Anda Pelajari

- Mengapa `DocumentConfig` adalah tempat yang tepat untuk menangkap peristiwa substitusi font.  
- Cara **melacak font yang hilang** tanpa mencemari log Anda dengan peringatan yang tidak relevan.  
- Program Java lengkap yang siap disalin‑tempel yang mendemonstrasikan teknik ini.  
- Tips untuk memperluas solusi—misalnya, menulis peringatan ke basis data atau mengirimkan peringatan email.

### Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| Java 8 atau lebih baru | Aspose.Words for Java mendukung JDK 8+. |
| Perpustakaan Aspose.Words for Java (versi terbaru) | Menyediakan `DocumentConfig`, `IWarningCallback`, dll. |
| IDE atau alat build (IntelliJ, Eclipse, Maven/Gradle) | Untuk mengompilasi dan menjalankan contoh. |
| File DOCX yang merujuk pada font yang tidak Anda miliki | Untuk melihat peringatan beraksi. |

Jika Anda sudah memiliki proyek, cukup tambahkan dependensi Aspose dan Anda siap melanjutkan.

---

## Langkah 1: Tambahkan Aspose.Words ke Build Anda

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro tip:** Versi trial gratis berfungsi dengan baik untuk pengujian, tetapi ingat untuk menerapkan lisensi pada produksi agar watermark evaluasi dihapus.

---

## Langkah 2: Buat DocumentConfig dan Daftarkan Warning Callback

Inti solusi berada pada potongan kode ini. Kami **membuat DocumentConfig**, melampirkan `IWarningCallback` khusus, dan memberitahukannya untuk **hanya melacak font yang hilang**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Mengapa ini berhasil:** Ketika Aspose.Words mengurai dokumen, ia menghasilkan objek `WarningInfo` untuk setiap ketidakteraturan. Dengan menyediakan callback, Anda menangkap peringatan‑peringatan tersebut *sebelum* mereka menghilang ke dalam kekosongan. Pemeriksaan `if` menjamin kami hanya **melacak font yang hilang**, mengabaikan peringatan lain seperti tag usang atau fitur yang tidak didukung.

---

## Langkah 3: Jalankan Contoh dan Amati Outputnya

Letakkan file DOCX yang merujuk pada font yang tidak Anda miliki (misalnya “Comic Sans MS” pada mesin Linux). Jalankan program:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Anda akan melihat sesuatu yang mirip dengan:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Setiap baris mewakili satu font yang hilang dan otomatis diganti oleh Aspose. Jika tidak ada font yang hilang, program tidak menghasilkan output—tepat seperti yang Anda inginkan untuk log yang bersih.

---

## Langkah 4: Simpan Daftar Font yang Hilang (Opsional)

Mencetak ke konsol berguna untuk demo, tetapi dalam layanan dunia nyata Anda mungkin ingin menyimpan data tersebut. Berikut cara cepat menulis peringatan ke file teks.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Sekarang setiap peristiwa font yang hilang menambahkan satu baris ke `missing-fonts.log`. Anda dapat mem‑parse file tersebut nanti, mengirimkannya ke dasbor pemantauan, atau bahkan memicu peringatan bila font kritis menghilang dari server Anda.

---

## Langkah 5: Kesalahan Umum dan Cara Menghindarinya

| Gejala | Penyebab Kemungkinan | Solusi |
|--------|----------------------|--------|
| Tidak ada peringatan muncul meskipun DOCX menggunakan font yang tidak dikenal | Callback tidak terdaftar atau `setWarningCallback` dipanggil setelah memuat dokumen | Pastikan `config.setWarningCallback(...)` dijalankan **sebelum** membuat instance `Document`. |
| Aplikasi crash dengan `NullPointerException` | `info.getDescription()` mengembalikan `null` untuk beberapa tipe peringatan yang jarang | Lindungi dari null: `String desc = info.getDescription(); if (desc != null) …` |
| Terlalu banyak peringatan tidak relevan membanjiri konsol | Callback hanya menyaring `FONT_SUBSTITUTION`? | Periksa kembali kondisi `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Penurunan performa pada batch besar | Menulis ke file secara sinkron untuk setiap peringatan | Lakukan penulisan batch atau gunakan `BufferedWriter` untuk mengurangi beban I/O. |

---

## Langkah 6: Memperluas Solusi – Dari Konsol ke Enterprise

- **Pencatatan ke basis data:** Ganti `FileWriter` dengan insert JDBC; simpan `documentName`, `missingFont`, dan `timestamp`.  
- **Peringatan email:** Hubungkan ke JavaMail; kirim ringkasan setelah memproses batch dokumen.  
- **Logika substitusi khusus:** Alih‑alih membiarkan Aspose memilih fallback, Anda dapat memuat koleksi font lokal melalui `FontSettings.setFontsFolder()` dan memuat ulang dokumen bila terjadi substitusi.

Ekstensi‑ekstensi ini mempertahankan gagasan inti—**membuat DocumentConfig** dan **melacak font yang hilang**—sementara memungkinkan skala ke kebutuhan produksi.

---

## Kesimpulan

Anda kini memiliki pola yang solid, siap disalin‑tempel, untuk **membuat DocumentConfig** di Java dan menggunakannya untuk **melacak font yang hilang** dengan Aspose.Words. Pendekatan ini ringan, hanya memerlukan beberapa baris kode, dan memberi Anda kontrol penuh atas cara peringatan substitusi font ditangani. Baik Anda membangun layanan konversi dokumen, generator laporan otomatis, atau alat audit kepatuhan, mengetahui secara tepat font mana yang hilang dapat menghemat berjam‑jam debugging.

Langkah selanjutnya? Coba ganti output konsol dengan log JSON terstruktur, atau integrasikan callback ke microservice Spring Boot yang memproses unggahan secara real‑time. Dan jika Anda menemukan kasus pinggiran—misalnya, font OpenType khusus yang tidak dapat diparse Aspose—tinggalkan komentar di bawah; kami akan membantu memecahkan bersama.

Selamat coding, semoga PDF Anda selalu menampilkan font yang Anda harapkan!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Using Fonts in Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}