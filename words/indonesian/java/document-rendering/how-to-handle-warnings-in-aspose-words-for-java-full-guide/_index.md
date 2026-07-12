---
category: general
date: 2026-06-24
description: cara menangani peringatan saat memproses file Word di Java. pelajari
  cara menangkap font, mencetak pesan font, dan menangani font yang hilang dengan
  lancar.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: id
og_description: cara menangani peringatan di Aspose.Words untuk Java. Panduan ini
  menunjukkan cara menangkap font, mencetak pesan font, dan mengelola font yang hilang
  secara efisien.
og_title: Cara menangani peringatan di Aspose.Words – Tutorial Java Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Cara menangani peringatan di Aspose.Words untuk Java – Panduan Lengkap
url: /id/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menangani peringatan di Aspose.Words untuk Java – Panduan Lengkap

Pernah bertanya-tanya **bagaimana menangani peringatan** yang muncul saat Anda memuat dokumen Word dengan Aspose.Words? Mungkin Anda pernah melihat pesan misterius tentang font yang hilang dan berpikir, “Bagus, PDF saya tampak tidak berpusat—lalu apa?” Anda tidak sendirian. Dalam banyak proyek dunia nyata, peringatan substitusi font adalah penyebab diam-diam yang merusak kesetiaan tata letak.

Dalam tutorial ini kami akan membahas solusi praktis: mendaftarkan callback peringatan, mendeteksi peringatan terkait font, dan **mencetak pesan font** sehingga Anda dapat memutuskan apakah akan menyematkan fallback atau mengirim file font khusus. Pada akhir tutorial Anda akan mengetahui **cara menangkap font**, dengan elegan **menangani font yang hilang**, dan menjaga pipeline konversi dokumen Anda tetap kokoh.

## Apa yang Akan Anda Pelajari

- Tujuan callback peringatan Aspose.Words.
- Cara mendeteksi dan menyaring peringatan *substitusi font*.
- Cara mencatat atau menampilkan **pesan cetak font** untuk debugging.
- Strategi untuk **menangani font yang hilang** di lingkungan produksi.
- Contoh Java lengkap, siap‑jalankan yang dapat Anda masukkan ke proyek Maven atau Gradle mana pun.

### Prasyarat

- Java 8 atau lebih baru (kode ini juga berfungsi dengan JDK 11).
- Perpustakaan Aspose.Words untuk Java (unduh dari situs Aspose atau tambahkan dependensi Maven/Gradle).
- Contoh `input.docx` yang merujuk pada font yang tidak terpasang secara lokal (sempurna untuk menguji callback).

---

## Langkah 1: Siapkan Proyek Anda dan Impor Aspose.Words

Sebelum Anda dapat **menangani peringatan**, Anda memerlukan proyek Java yang mengenal Aspose.Words. Jika Anda menggunakan Maven, tambahkan potongan kode berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Untuk Gradle, yang setara adalah:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

Setelah dependensi terpasang, impor kelas yang diperlukan dalam file sumber Java Anda:

```java
import com.aspose.words.*;
```

> **Tip pro:** Jaga agar perpustakaan Aspose Anda tetap terbaru. Rilis baru sering meningkatkan penanganan peringatan dan menambahkan detail `WarningInfo` yang lebih kaya.

---

## Langkah 2: Muat Dokumen Word dan Daftarkan Callback Peringatan

Sekarang perpustakaan sudah berada di classpath, kita dapat **menangkap font** yang diganti oleh mesin. Kuncinya adalah `Document.setWarningCallback`, yang menerima implementasi apa pun dari `IWarningCallback`. Di bawah ini contoh singkat namun lengkap yang mencetak setiap peringatan substitusi font ke konsol.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Mengapa Ini Berfungsi

- **`Document.setWarningCallback`** memberi tahu Aspose.Words untuk memanggil kode Anda setiap kali menemukan situasi yang memerlukan peringatan.
- **`WarningInfo.getWarningType()`** memungkinkan kami membedakan antara kategori yang berbeda (mis., `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Dengan memfokuskan pada `FONT_SUBSTITUTION` kami **menangani font yang hilang** tanpa memenuhi log.
- Baris `System.out.println` **mencetak pesan font** secara real time, yang sangat berharga selama pengembangan atau saat memecahkan masalah pipeline produksi.

---

## Langkah 3: Uji Callback dengan Font yang Hilang

Untuk memastikan bahwa callback kami benar‑benar **menangkap font**, buat file Word yang menggunakan font yang tidak terpasang di mesin Anda—misalnya, “Comic Sans MS” pada server Linux yang hanya memiliki “DejaVu Sans”. Saat Anda menjalankan demo, Anda akan melihat output serupa dengan:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Jika Anda tidak melihat pesan apa pun, periksa kembali:

1. Dokumen memang merujuk pada font yang hilang.
2. Jalur ke `input.docx` sudah benar.
3. Anda menggunakan versi terbaru Aspose.Words (build lama kadang menekan peringatan tertentu).

---

## Langkah 4: Penanganan Lanjutan – Menyematkan Font Fallback

Mencetak peringatan memang bagus, tetapi dalam sistem produksi Anda mungkin ingin **menangani font yang hilang** secara otomatis. Salah satu pendekatan umum adalah menyematkan font fallback (mis., “Liberation Sans”) sebelum menyimpan. Berikut cara memperluas callback untuk mengganti font yang hilang secara programatis:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**Apa yang terjadi?**

- Kami mengurai deskripsi peringatan untuk mengekstrak nama font yang hilang.
- Dengan menggunakan `FontSettings`, kami memberi tahu Aspose.Words untuk menggantikan *setiap* kemunculan font tersebut dengan “Liberation Sans”.
- Pada kali berikutnya dokumen dirender atau disimpan, fallback diterapkan secara diam‑diam.

> **Peringatan:** Penggunaan berlebihan substitusi otomatis dapat menyembunyikan masalah desain yang sebenarnya. Sebaiknya log substitusi (seperti yang sudah kami **cetak pesan font**) dan tinjau output secara manual selama QA.

---

## Langkah 5: Logging Alih-alih Mencetak – Membuatnya Siap Produksi

Di pipeline CI/CD Anda mungkin tidak menginginkan output konsol. Ganti `System.out.println` dengan logger yang tepat (mis., SLF4J). Berikut adaptasi singkatnya:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Sekarang peringatan Anda terintegrasi dengan alat agregasi log yang ada (ELK, Splunk, dll.), memudahkan **menangani font yang hilang** di banyak pekerjaan.

---

## Langkah 6: Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| Tidak ada peringatan muncul | Font sebenarnya ada di sistem, atau dokumen menggunakan font yang disematkan. | Verifikasi bahwa dokumen uji benar‑benar merujuk pada font yang tidak tersedia. |
| Callback tidak dipanggil | `setWarningCallback` dipanggil **setelah** dokumen sudah dimuat. | Daftarkan callback **sebelum** operasi apa pun yang dapat memicu peringatan (mis., sebelum `Document.save`). |
| Banyak peringatan membanjiri log | Dokumen besar memicu banyak substitusi. | Tambahkan mekanisme throttling atau agregasikan pesan sebelum logging. |
| Substitusi tidak berlaku | `FontSettings` tidak terhubung ke instance dokumen. | Pastikan Anda mengatur `FontSettings` pada objek `Document` yang sama saat menyimpan. |

---

## Langkah 7: Contoh Lengkap, Siap‑Jalankan

Berikut adalah program lengkap, siap untuk disalin‑tempel. Program ini mencakup impor, callback, logging, dan strategi font fallback.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Output konsol/log yang diharapkan** (dengan asumsi “Comic Sans MS” tidak ada):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

File `output.pdf` yang dihasilkan akan menggunakan “Liberation Sans” di mana pun “Comic Sans MS” direferensikan, berkat substitusi otomatis yang kami tambahkan.

---

## Kesimpulan

Kami baru saja membahas **cara menangani peringatan** di Aspose.Words untuk Java dari awal hingga akhir. Dengan mendaftarkan callback peringatan, menyaring peringatan **substitusi font**, dan **mencetak pesan font**, Anda memperoleh visibilitas penuh terhadap skenario font yang hilang. Menambahkan fallback melalui `FontSettings` memungkinkan Anda **menangani font yang hilang** tanpa intervensi manual, sementara kerangka logging yang tepat membuat solusi siap produksi.

Langkah selanjutnya? Coba gabungkan pendekatan ini dengan Aspose.PDF untuk memverifikasi bahwa font yang disematkan tetap ada setelah konversi, atau jelajahi tipe peringatan lain (mis., `DEPRECATED_FEATURE`) untuk mempersiapkan kode Anda di masa depan. Dan jika Anda penasaran tentang **cara menangkap font** dari bucket penyimpanan remote

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menangkap Peringatan Substitusi Font di Java dengan Aspose.Words – Panduan Lengkap](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Cara Mendeteksi Font di Aspose.Words – Menangani Peringatan & Pengaturan](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cara Menangkap Font di Aspose.Words – Panduan Lengkap](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}