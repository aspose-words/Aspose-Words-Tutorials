---
category: general
date: 2026-06-17
description: Catat peringatan substitusi font di Java menggunakan Aspose.Words – tangkap
  font yang hilang saat memuat dokumen dan pertahankan konsistensi output Anda.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: id
og_description: Catat peringatan substitusi font di Java dengan Aspose.Words. Pelajari
  cara menangkap peringatan font yang hilang saat memuat dokumen dan jaga PDF Anda
  tetap bersih.
og_title: Mencatat Peringatan Substitusi Font di Java – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Mencatat Peringatan Substitusi Font di Java dengan Aspose.Words
url: /id/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mencatat Peringatan Substitusi Font di Java – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **mencatat peringatan substitusi font** ketika dokumen Word mengambil font yang tidak Anda miliki di server? Anda bukan satu-satunya yang kebingungan dengan font yang hilang dan secara diam‑diam diganti. Kabar baiknya? Aspose.Words for Java memberikan cara yang bersih untuk menangkap substitusi tersebut saat dokumen dimuat.

Dalam tutorial ini kami akan membimbing Anda melalui contoh langsung yang menunjukkan secara tepat cara mendaftarkan callback peringatan, menyaring peringatan **substitusi font**, dan menuliskannya ke konsol (atau logger apa pun yang Anda sukai). Pada akhirnya Anda akan memiliki potongan kode yang dapat dipakai ulang dan dapat disisipkan ke proyek Java mana pun yang menggunakan **Aspose.Words Java**.

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi **LoadOptions** untuk menangkap peringatan.
- Cara mengimplementasikan **IWarningCallback** yang hanya merespons peristiwa **font substitution**.
- Cara memuat dokumen dengan aman sambil menjaga jejak audit yang jelas untuk font yang hilang.
- Tips untuk memperluas solusi ke log berbasis file atau sistem pemantauan.

### Prasyarat

- Java 8 atau lebih baru (kode ini juga berfungsi dengan Java 11+).
- Perpustakaan Aspose.Words for Java (versi 23.10 atau lebih baru disarankan).
- Contoh file `.docx` yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya `MissingFont.docx`).

Tidak ada kerangka kerja tambahan yang diperlukan—hanya Java biasa dan Aspose.JARs.

---

## Langkah 1: Konfigurasikan LoadOptions untuk Aspose.Words Java

Sebelum Anda dapat menangkap peringatan apa pun, Anda memerlukan instance **LoadOptions**. Objek ini memberi tahu Aspose.Words bagaimana berperilaku saat mem-parsing file yang masuk.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Mengapa langkah ini penting? Tanpa objek `LoadOptions`, perpustakaan secara diam‑diam menggantikan font yang hilang dan Anda tidak pernah melihat jejaknya. Dengan secara eksplisit membuatnya, Anda membuka pintu ke **callback peringatan** khusus yang dapat mencatat tepat apa yang Anda butuhkan.

> **Pro tip:** Jika Anda memuat banyak dokumen secara batch, gunakan kembali satu instance `LoadOptions` untuk menghindari pembuatan objek yang tidak perlu.

---

## Langkah 2: Implementasikan Callback Peringatan untuk Substitusi Font

Aspose.Words menyediakan antarmuka `IWarningCallback`. Mengimplementasikannya memungkinkan Anda menentukan apa yang harus dilakukan ketika mesin mengeluarkan `WarningInfo`. Dalam kasus kami, kami hanya ingin merespons `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Beberapa hal yang perlu diperhatikan:

1. **Penyaringan** – Pernyataan `if` memastikan kami mengabaikan peringatan yang tidak terkait (seperti masalah tata letak) dan menjaga log tetap rapi.
2. **Keamanan thread** – Callback dijalankan pada thread yang sama dengan proses pemuatan dokumen, sehingga Anda tidak memerlukan sinkronisasi tambahan untuk output konsol sederhana. Jika Anda menulis ke logger bersama, pastikan logger tersebut thread‑safe.
3. **Ekstensibilitas** – Ingin menulis ke file? Ganti `System.out.println` dengan `java.util.logging.Logger` atau kerangka kerja logging pihak ketiga.

---

## Langkah 3: Muat Dokumen Menggunakan Opsi yang Telah Dikonfigurasi

Sekarang callback sudah siap, muat file Word Anda. Begitu Aspose.Words mem-parsing dokumen, setiap font yang hilang akan memicu callback yang telah didefinisikan di atas.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Jika file sumber merujuk pada font yang tidak terpasang, Anda akan melihat output serupa dengan:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Baris tersebut adalah **log peringatan substitusi font** yang Anda cari. Anda kini dapat menindaklanjutinya—mungkin memberi peringatan kepada pengguna, beralih ke stylesheet cadangan, atau sekadar menyimpan catatan untuk kepatuhan.

---

## Langkah 4: Lanjutkan Pemrosesan Normal

Setelah pemuatan, dokumen berperilaku seperti objek `Document` lainnya. Silakan inspeksi bagian, ekstrak teks, atau konversi ke PDF. Pencatatan peringatan terjadi secara otomatis selama langkah pemuatan, jadi Anda tidak memerlukan kode tambahan.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Konsol kini akan menampilkan baik peringatan substitusi font (jika ada) **dan** jumlah bagian, mengonfirmasi bahwa dokumen berfungsi sepenuhnya.

---

## Tips Lanjutan & Kasus Edge

### Mencatat ke File Alih-alih Konsol

Jika Anda menginginkan log yang persisten, ganti pemanggilan `System.out.println` dengan `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Ingat untuk menangani `IOException` dengan tepat dalam kode produksi.

### Menangkap Banyak Dokumen dalam Loop

Saat memproses folder berisi dokumen, Anda dapat menggunakan kembali callback yang sama:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Karena callback terpasang pada `loadOptions`, setiap iterasi secara otomatis mencatat peristiwa substitusi font apa pun.

### Menangani Font yang Di‑embed

Aspose.Words dapat menyematkan font yang hilang jika Anda mengaktifkannya:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Bahkan dengan embedding diaktifkan, callback peringatan tetap dipicu, memberi Anda visibilitas tentang apa yang telah disubstitusi.

---

## Contoh Lengkap yang Siap Dijalan

Berikut adalah program lengkap yang siap dijalankan. Salin ke kelas bernama `FontSubstitutionDiagnostics.java`, sesuaikan jalur file, dan eksekusi.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Output yang diharapkan** (asumsi dokumen sumber merujuk pada font yang hilang):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Baik konsol maupun `font_substitution_log.txt` akan berisi peringatan, memberikan jejak audit yang dapat diandalkan.

---

## Kesimpulan

Kami baru saja menunjukkan cara **mencatat peringatan substitusi font** di Java menggunakan Aspose.Words. Dengan mengonfigurasi `LoadOptions`, menyiapkan `IWarningCallback`, dan memuat dokumen, Anda memperoleh visibilitas penuh terhadap setiap peristiwa font yang hilang yang sebaliknya tidak akan terlihat. Dari sini Anda dapat:

- Mengarahkan peringatan ke layanan logging terpusat.
- Memicu alert untuk pipeline kontrol kualitas.
- Menggabungkan teknik ini dengan strategi **document loading** lainnya, seperti konversi PDF atau mail‑merge.

Silakan bereksperimen—ganti logger konsol dengan SLF4J, tambahkan timestamp, atau bahkan kirim alert ke dashboard pemantauan. Pola intinya tetap sama, dan kini Anda memiliki fondasi kuat untuk penanganan font yang andal dalam alur kerja dokumen berbasis Java apa pun.

Ada trik yang ingin Anda bagikan? Mungkin Anda telah mengintegrasikannya dengan Spring Boot atau fungsi cloud. Tinggalkan komentar di bawah, dan mari teruskan diskusi. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}