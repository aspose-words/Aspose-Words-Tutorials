---
category: general
date: 2026-06-05
description: Deteksi substitusi font yang hilang di Java menggunakan Aspose.Words.
  Pelajari cara mengonfigurasi LoadOptions, FontSettings, dan callback peringatan
  untuk pemrosesan dokumen yang andal.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: id
og_description: deteksi substitusi font yang hilang di Java dengan Aspose.Words. Panduan
  ini menunjukkan langkah demi langkah cara mengatur LoadOptions, FontSettings, dan
  callback peringatan untuk menangkap font yang hilang.
og_title: deteksi substitusi font yang hilang di Java – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: deteksi substitusi font yang hilang di Java – Panduan Lengkap Aspose.Words
url: /id/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# deteksi substitusi font yang hilang di Java – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya bagaimana cara **detect missing font substitution** saat memuat dokumen Word di Java? Anda tidak sendirian. Font yang hilang dapat secara diam‑diam merusak PDF atau halaman yang dirender, dan menemukan masalah ini lebih awal menghemat berjam‑jam debugging. Pada tutorial ini kami akan membahas solusi praktis yang tidak hanya memuat dokumen tetapi juga memberi tahu Anda tepat kapan terjadi substitusi font.

Kami akan membahas semuanya mulai dari membuat `LoadOptions` hingga menghubungkan `WarningCallback` yang mencetak pesan jelas setiap kali Aspose.Words mengganti font yang hilang. Pada akhir tutorial, Anda akan memiliki potongan kode yang dapat digunakan kembali untuk file `.docx` apa pun, dan Anda akan memahami *mengapa* setiap bagian penting. Tanpa pustaka tambahan, hanya Java murni dan Aspose.Words.

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi **LoadOptions** untuk menggunakan **FontSettings** khusus.  
- Cara mengimplementasikan **IWarningCallback** yang menangkap peringatan `FONT_SUBSTITUTION`.  
- Cara memuat dokumen sambil memantau font yang hilang dengan aman.  
- Output konsol yang diharapkan dan cara menyesuaikan kode untuk kerangka kerja logging.  

**Prasyarat**: Java 8+ terpasang, Aspose.Words for Java (v23.12 atau lebih baru) berada di classpath Anda, serta contoh file `.docx` yang merujuk pada font yang tidak Anda miliki. Itu saja—tidak diperlukan alat build tambahan.

---

## Langkah 1: Siapkan Proyek dan Tambahkan Aspose.Words

Sebelum kita masuk ke kode, pastikan Aspose.Words tersedia. Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Jika Anda lebih suka Gradle, setaraannya adalah:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Setelah pustaka berada di classpath, Anda siap untuk **detect missing font substitution** dengan satu pemanggilan metode.

---

## Langkah 2: Buat LoadOptions dan Lampirkan FontSettings

Inti solusi terletak pada menyiapkan instance `LoadOptions` yang dapat memantau masalah font. Berikut kode yang diuraikan baris‑per‑baris.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Mengapa ini penting**: `LoadOptions` memberi tahu Aspose.Words *bagaimana* menafsirkan file yang masuk. Dengan menyematkan `FontSettings` yang disesuaikan, kami memberikan loader sebuah hook (`IWarningCallback`) yang dipicu **tepat ketika font yang hilang disubstitusi**. Tanpa callback ini, Aspose.Words akan mengganti font secara diam‑diam dan Anda tidak akan pernah mengetahuinya.

---

## Langkah 3: Muat Dokumen dengan Opsi yang Dikonfigurasi

Sekarang sistem peringatan sudah siap, memuat dokumen menjadi sangat sederhana.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Saat pemanggilan `new Document(...)` dijalankan, Aspose.Words membaca file, memeriksa setiap referensi font, dan jika tidak menemukan font yang cocok di sistem, ia memicu metode `warning` yang telah kami definisikan sebelumnya. Konsol akan langsung menampilkan baris seperti:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Baris itu adalah output **detect missing font substitution** yang Anda cari.

---

## Langkah 4: Verifikasi Hasil dan Sesuaikan Callback (Lanjutan)

### 4.1 Verifikasi cepat

Jalankan program dari IDE Anda atau lewat `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Jika dokumen merujuk pada font yang tidak Anda miliki, Anda akan melihat pesan peringatan tercetak. Jika konsol tetap diam, berarti font tersebut memang ada di mesin Anda atau dokumen tidak meminta font yang hilang.

### 4.2 Logging alih-alih `System.out`

Pada kode produksi Anda mungkin ingin menggunakan logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Perubahan kecil ini membuat mekanisme **detect missing font substitution** berintegrasi dengan baik pada pipeline logging yang sudah ada.

### 4.3 Menangani tipe peringatan lain

Callback menerima *semua* peringatan, bukan hanya masalah font. Jika Anda ingin memantau masalah lain (misalnya `UNKNOWN_STYLE`), tambahkan cabang `if` tambahan. Berikut contoh singkat:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Langkah 5: Kesalahan Umum dan Tips Profesional

| Pitfall | Mengapa Terjadi | Solusi |
|--------|----------------|-----|
| **Tidak ada peringatan muncul** | Font sebenarnya ada di OS, atau dokumen menggunakan fallback yang dianggap Aspose.Words sebagai “ditemukan”. | Hapus font tersebut dari sistem sementara atau gunakan nama font yang benar‑benar tidak ada di dokumen sumber. |
| **Callback tidak pernah dipanggil** | `setWarningCallback` dipanggil pada instance `FontSettings` *yang berbeda* dari yang dilampirkan ke `LoadOptions`. | Pastikan Anda memanggil `loadOptions.setFontSettings(fontSettings)` **setelah** mengonfigurasi callback. |
| **Penurunan performa** | Memuat banyak dokumen besar dengan callback dapat menambah overhead. | Cache satu instance `FontSettings` dan gunakan kembali pada setiap pemuatan jika Anda memproses batch. |
| **Beberapa thread** | `FontSettings` tidak thread‑safe secara default. | Buat `FontSettings` terpisah per thread atau sinkronkan aksesnya. |

**Tips pro**: Jika Anda menghasilkan PDF untuk layanan web, Anda mungkin ingin mengumpulkan semua peringatan substitusi ke dalam daftar dan mengembalikannya dalam respons API, alih‑alih mencetak ke konsol.

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Output konsol yang diharapkan** (asumsi file merujuk pada font yang hilang):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Jika tidak ada font yang hilang, Anda hanya akan melihat baris akhir “Document loaded successfully.”.

---

## Kesimpulan

Kami baru saja menunjukkan cara **detect missing font substitution** di Java menggunakan Aspose.Words. Dengan mengonfigurasi `LoadOptions`, membuat instance `FontSettings`, dan menghubungkan `IWarningCallback`, Anda mendapatkan visibilitas penuh atas setiap font yang diganti oleh pustaka di balik layar. Pendekatan ini tidak hanya mencegah gangguan rendering yang diam‑diam, tetapi juga memberi Anda hook untuk logging, alert, atau bahkan auto‑embedding font fallback.

Dari sini Anda dapat:

- Memperluas callback untuk mengumpulkan peringatan ke dalam daftar bagi respons API.  
- Menggabungkan teknik ini dengan **konfigurasi LoadOptions** untuk skenario lain (misalnya pemuatan sumber daya khusus).  
- Menjelajahi ekosistem **Java Aspose.Words** yang lebih luas: konversi ke PDF, ekstraksi teks, atau melakukan mail merge.

Cobalah, sesuaikan logger, dan biarkan aplikasi Anda memberi tahu ketika sebuah font hilang. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}