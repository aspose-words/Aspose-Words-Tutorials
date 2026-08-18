---
category: general
date: 2026-07-03
description: Daftarkan callback peringatan di Java untuk mendeteksi font yang hilang
  saat memproses dokumen Word. Pelajari penanganan peringatan Aspose.Words dan deteksi
  substitusi font.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: id
og_description: Daftarkan callback peringatan di Java untuk mendeteksi font yang hilang.
  Panduan ini menunjukkan cara menangkap peringatan substitusi font dengan Aspose.Words.
og_title: Daftarkan callback peringatan di Java – Deteksi font yang hilang
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Daftarkan callback peringatan di Java – Deteksi font yang hilang dengan mudah
url: /id/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftarkan callback peringatan di Java – Deteksi font yang hilang dengan mudah

Pernah bertanya-tanya bagaimana cara **register warning callback** sehingga Anda dapat **detect missing fonts** saat mengonversi atau mengedit dokumen Word? Anda bukan satu-satunya. Font yang hilang dapat secara diam‑diam merusak tata letak, mengubah laporan yang rapi menjadi berantakan, dan kebanyakan pengembang bahkan tidak menyadarinya sampai PDF akhir terlihat aneh.  

Dalam tutorial ini kami akan membimbing Anda melalui contoh lengkap yang siap dijalankan yang menunjukkan secara tepat cara mengaitkan ke sistem peringatan Aspose.Words for Java, menangkap peringatan penggantian font yang mengganggu, dan mencatatnya atau merespons sesuai kebutuhan Anda. Tanpa jalan pintas “lihat dokumentasi” yang samar—hanya kode murni copy‑and‑paste dan penjelasan di balik setiap baris.

## Prasyarat

Sebelum kita melanjutkan, pastikan Anda memiliki:

* **Java 17** (atau JDK terbaru apa pun) terpasang dan `JAVA_HOME` diset.  
* **Aspose.Words for Java** JAR (unduh dari situs resmi atau tarik via Maven).  
* Sebuah contoh `.docx` yang merujuk pada font **tidak** terpasang di mesin Anda—ini akan memicu peringatan.  
* IDE favorit Anda atau editor teks sederhana dan alat build baris perintah.

Itu saja. Tanpa kerangka kerja tambahan, tanpa layanan eksternal. Siap? Mari kita mulai.

## Langkah 1: Siapkan proyek dan tambahkan Aspose.Words

Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Untuk Gradle, letakkan ini ke dalam `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Jika Anda lebih suka cara manual, cukup letakkan `aspose-words-24.10.jar` pada classpath Anda.  
**Pro tip:** simpan JAR di samping folder `src`; ini menyederhanakan perintah `javac` nanti.

## Langkah 2: Muat dokumen yang mungkin berisi font yang hilang

Hal pertama yang Anda lakukan adalah membuat objek `Document` yang menunjuk ke file sumber. Langkah ini sederhana, namun di sinilah perpustakaan memindai file dan *potensial* menemukan font yang hilang.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Di sini, `Document` adalah titik masuk untuk semua operasi Aspose.Words. Ketika konstruktor dijalankan, perpustakaan mem-parsing XML dokumen, menyelesaikan font, dan jika ada font yang tidak tersedia, ia *menempatkan* peringatan yang dapat kita tangkap nanti.

## Langkah 3: Daftarkan callback peringatan untuk menangkap peringatan penggantian font

Sekarang bagian utama: **register warning callback**. Aspose.Words memungkinkan Anda menyambungkan implementasi dari antarmuka `IWarningCallback`. Setiap kali mesin menemukan situasi yang layak ditandai—seperti font yang hilang—ia memanggil metode `warning` Anda.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Mengapa ini penting

* **Visibility:** Tanpa callback, penggantian terjadi secara diam‑diam, dan Anda mungkin mengirimkan dokumen dengan tampilan yang salah.  
* **Automation:** Dalam pipeline batch Anda dapat mencatat setiap insiden font yang hilang dan kemudian memberi daftar tersebut ke skrip instalasi font.  
* **Compliance:** Beberapa industri (misalnya, hukum) memerlukan bukti bahwa font asli digunakan atau diganti dengan benar.

Perhatikan kami menyaring pada `WarningType.FONT_SUBSTITUTION`. Aspose.Words menghasilkan banyak jenis peringatan—kelebihan tata letak, fitur usang, dll.—tetapi kami hanya peduli pada yang memberi tahu bahwa font tidak tersedia. Ini membuat konsol bersih dan fokus pada tujuan **detect missing fonts**.

## Langkah 4: Simpan dokumen dan biarkan callback dipicu

Ketika Anda akhirnya memanggil `save`, mesin menyelesaikan pemuatan malas apa pun dan memicu callback peringatan untuk setiap font yang hilang yang ditemukan selama operasi penyimpanan.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Output konsol yang diharapkan

Dengan asumsi `input.docx` merujuk pada font *“Comic Sans MS”* yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Jika dokumen sumber sudah hanya berisi font yang terpasang, baris peringatan tidak pernah muncul—artinya **detect missing fonts** berhasil secara diam‑diam.

![Output konsol yang menunjukkan register warning callback beraksi dan detect missing fonts](register-warning-callback-output.png)

* Teks alt gambar: output register warning callback yang menunjukkan detect missing fonts

## Langkah 5: Menangani kasus tepi dan tips praktik terbaik

### Banyak font yang hilang

Jika sebuah dokumen merujuk pada beberapa font yang tidak tersedia, callback akan dipicu sekali per font. Anda dapat menggabungkan pesan-pesan ke dalam daftar jika membutuhkan laporan ringkasan nanti.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Mengontrol perilaku substitusi

Kadang Anda *memang* ingin memaksa font fallback tertentu. Gunakan `FontSettings` sebelum memuat dokumen:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Sekarang callback tetap akan dipicu, tetapi Anda tahu tepat font mana yang akan digunakan.

### Pertimbangan kinerja

Mendaftarkan callback peringatan menambahkan overhead kecil—hanya beberapa nanodetik per peringatan. Pada layanan dengan throughput tinggi (mis., mengonversi ribuan dokumen per jam) dampaknya dapat diabaikan. Namun, jika Anda memproses jutaan, pertimbangkan menonaktifkan peringatan setelah Anda memverifikasi set font lengkap:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Catatan lintas‑platform

Callback bekerja identik di Windows, macOS, dan Linux. Satu‑satunya perbedaan adalah kumpulan font yang tersedia pada masing‑masing OS. Jika Anda menjalankan pekerjaan yang sama pada beberapa agen, Anda mungkin melihat pesan substitusi yang berbeda. Untuk menjaga hasil deterministik, kirimkan **folder font khusus** dan arahkan Aspose.Words ke sana via `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Contoh lengkap yang dapat dijalankan

Berikut adalah seluruh kelas Java yang dapat Anda copy‑paste ke `src/main/java/FontWarningDemo.java`. Ini mencakup semua import, penanganan error, dan komentar yang Anda perlukan untuk menjalankannya langsung.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Kompilasi dan jalankan:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Anda akan melihat baris peringatan (jika ada) diikuti oleh pesan sukses.

## Kesimpulan

Anda baru saja mempelajari **how to register warning callback** di Java untuk **detect missing fonts** saat bekerja dengan Aspose.Words. Dengan menyambungkan ke sistem peringatan perpustakaan, Anda memperoleh visibilitas penuh terhadap peristiwa penggantian font, dapat mencatatnya untuk kepatuhan, dan bahkan mengganti font secara programatik bila diperlukan.  

Dari sini Anda dapat menjelajahi:

* **Detect missing fonts** di seluruh batch file menggunakan loop atau parallel streams.  
* Mengintegrasikan callback dengan kerangka logging (SLF4J, Log4j) untuk laporan produksi.  
* Menggunakan `FontSettings` untuk menegakkan palet font perusahaan dan menghindari fallback yang tidak diinginkan.

Cobalah—ganti dokumen input, coba skenario font yang hilang yang berbeda, dan lihat bagaimana callback berperilaku. Jika Anda menemukan kejanggalan, tinggalkan komentar di bawah; selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menangkap Peringatan Penggantian Font di Java dengan Aspose.Words – Panduan Lengkap](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback Peringatan dalam Dokumen Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Penyimpanan Kustom](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}