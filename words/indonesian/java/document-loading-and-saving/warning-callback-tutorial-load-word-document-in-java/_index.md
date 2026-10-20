---
category: general
date: 2026-03-25
description: Tutorial callback peringatan untuk memuat dokumen Word di Java dan menangani
  font yang hilang. Pelajari pendekatan memuat dokumen Word dengan Java menggunakan
  callback peringatan khusus.
draft: false
keywords:
- warning callback tutorial
- load word document java
- handle missing fonts
language: id
og_description: Tutorial callback peringatan menunjukkan cara memuat dokumen Word
  di Java sambil menangani font yang hilang dengan callback peringatan khusus.
og_title: Tutorial Callback Peringatan – Memuat Dokumen Word di Java
tags:
- java
- aspose-words
- document-processing
title: tutorial callback peringatan – Memuat Dokumen Word di Java
url: /id/java/document-loading-and-saving/warning-callback-tutorial-load-word-document-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# tutorial callback peringatan – Memuat Dokumen Word di Java

Pernah mencoba memuat file **.docx** di Java hanya untuk melihat peringatan misterius tentang font yang hilang? Anda tidak sendirian. Dalam **tutorial callback peringatan** ini, kami akan membimbing Anda melalui contoh lengkap yang siap dijalankan yang tidak hanya memuat dokumen Word tetapi juga menangkap peringatan substitusi font sehingga Anda dapat menanggapinya secara programatik.

Jika Anda bertanya-tanya bagaimana cara **load word document java** dengan gaya sambil tetap memperhatikan peringatan *handle missing fonts*, Anda berada di tempat yang tepat. Pada akhir panduan ini Anda akan memiliki pola yang dapat digunakan kembali yang dapat Anda masukkan ke dalam proyek Java mana pun yang menggunakan Aspose.Words (atau perpustakaan serupa) dan Anda akan memahami mengapa callback peringatan adalah cara paling bersih untuk tetap mendapat informasi tentang masalah font.

---

## Apa yang Akan Anda Pelajari

- Kode tepat yang dibutuhkan untuk mengonfigurasi callback peringatan di Java.  
- Bagaimana callback membedakan peringatan substitusi font dari tipe pesan lainnya.  
- Cara mencatat, menekan, atau bahkan mengganti font yang hilang secara dinamis.  
- Tips untuk memecahkan masalah umum saat memuat dokumen Word yang merujuk pada font yang tidak tersedia.

### Prasyarat

- Java 17 (atau lebih baru) terpasang di mesin Anda.  
- Alat build seperti Maven atau Gradle (kami akan menampilkan cuplikan Maven).  
- Perpustakaan Aspose.Words for Java (versi percobaan gratis cukup untuk pengujian).  
- Contoh **input.docx** yang menggunakan font yang tidak Anda miliki (untuk memicu peringatan).

> **Pro tip:** Jika Anda belum memiliki Aspose.Words, tambahkan dependensi yang ditunjukkan di bawah ini dan biarkan Maven mengunduhnya untuk Anda—tidak perlu mengatur JAR secara manual.

---

## Langkah 1: Siapkan Proyek Anda dan Impor Kelas yang Diperlukan

Pertama, kita memerlukan koordinat Maven yang tepat. Tambahkan ini ke `pom.xml` Anda:

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Sekarang buat kelas Java baru, misalnya `WordLoader.java`, dan impor tipe yang diperlukan:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import com.aspose.words.WarningType;
```

Impor ini memberi kita akses ke `LoadOptions`, antarmuka `IWarningCallback`, dan objek `WarningInfo` yang memberi tahu *apa* yang salah.

---

## Langkah 2: Definisikan Callback Peringatan – Inti dari Tutorial

**Tutorial callback peringatan** bergantung pada intersepsi peristiwa substitusi font. Berikut implementasi singkat namun sepenuhnya fungsional:

```java
// Step 2: Create a warning callback that prints font substitution messages
class FontSubstitutionCallback implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("⚠️ Font substituted: " + info.getDescription());
        }
    }
}
```

**Mengapa ini penting:**  
- `IWarningCallback` dipanggil *setiap* kali Aspose.Words menemukan situasi yang dianggap penting.  
- Dengan memeriksa `info.getWarningType()`, kita menyaring peringatan yang tidak relevan (seperti fitur yang sudah usang) dan fokus pada skenario **handle missing fonts**.  
- Mencatat deskripsi memberi Anda nama font asli dan fallback yang digunakan, yang krusial untuk pemeriksaan tata letak selanjutnya.

---

## Langkah 3: Sambungkan Callback ke LoadOptions

Sekarang kita melampirkan callback kita ke instance `LoadOptions`. Ini adalah titik di mana proses **load word document java** menjadi sadar akan handler khusus kami.

```java
// Step 3: Prepare LoadOptions with the custom warning callback
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontSubstitutionCallback());
```

Anda juga dapat mengatur opsi lain di sini—seperti `setPassword` untuk file terenkripsi atau `setLoadFormat` jika Anda perlu memaksa format tertentu. Callback bekerja secara independen dari pengaturan tersebut.

---

## Langkah 4: Muat Dokumen dan Amati Callback Beraksi

Dengan semua terhubung, memuat dokumen cukup satu baris:

```java
// Step 4: Load the .docx file using the configured LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Ketika file merujuk pada font yang hilang, Anda akan melihat output serupa dengan:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Jika semua font dalam dokumen tersedia, callback tetap diam—tepat seperti yang Anda harapkan ketika **handling missing fonts** secara elegan.

---

## Langkah 5: Verifikasi Hasil dan Pemrosesan Opsional Setelahnya

Setelah memuat, Anda mungkin ingin memastikan dokumen dapat digunakan, misalnya dengan mengonversinya ke PDF atau mengekstrak teks biasa:

```java
// Optional: Save as PDF to verify visual fidelity
document.save("output.pdf");

// Or extract plain text to a console for quick inspection
System.out.println(document.getText());
```

Kedua tindakan akan menghormati substitusi yang terjadi sebelumnya, sehingga Anda dapat melihat dampak nyata font yang hilang pada output akhir.

---

## Kasus Tepi & Kesulitan Umum

| Situasi | Apa yang Terjadi | Cara Menangani |
|-----------|--------------|---------------|
| **Multiple missing fonts** | Callback dipicu sekali per font yang hilang. | Jaga callback tetap ringan; hindari I/O berat di dalam `warning()`. |
| **Custom font directory** | Aspose.Words tetap melaporkan substitusi jika font tidak berada di jalur pencarian default. | Gunakan `loadOptions.setFontSettings(FontSettings.getDefaultInstance())` dan tambahkan folder font Anda via `FontSettings.getDefaultInstance().setFontsFolder("path", true)`. |
| **Performance‑critical apps** | Logging berlebihan dapat memperlambat pemrosesan batch. | Beralih ke logger dengan level `WARN` dan nonaktifkan pencetakan ke konsol di produksi. |
| **Non‑font warnings** | Callback menerima banyak tipe peringatan (mis., `DEPRECATED_FEATURE`). | Filter berdasarkan `WarningType` seperti yang ditunjukkan; Anda juga dapat mengumpulkan peringatan lain untuk laporan diagnostik. |

---

## Contoh Lengkap yang Berfungsi

Berikut program lengkap yang mandiri yang dapat Anda salin‑tempel ke IDE. Program ini mencakup semua impor, kelas callback, dan metode `main` sederhana.

```java
import com.aspose.words.*;

public class WordLoader {
    // Custom warning callback – only cares about font substitution
    static class FontSubstitutionCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("⚠️ Font substituted: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with our callback
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setWarningCallback(new FontSubstitutionCallback());

            // 2️⃣ Load the document – this triggers the callback if needed
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 3️⃣ Optional verification – save as PDF and print text
            doc.save("output.pdf");                     // visual check
            System.out.println("--- Extracted Text ---");
            System.out.println(doc.getText());          // quick sanity check
        } catch (Exception e) {
            // In real apps, use proper logging instead of printStackTrace
            e.printStackTrace();
        }
    }
}
```

**Output konsol yang diharapkan** (ketika font yang hilang terdeteksi):

```
⚠️ Font substituted: Font 'Times New Roman' was not found. Substituted with 'Liberation Serif'.
--- Extracted Text ---
[Document text appears here...]
```

Jika tidak ada font yang hilang, Anda hanya akan melihat header teks yang diekstrak.

---

## Gambaran Visual

![diagram tutorial callback peringatan yang menunjukkan alur dari LoadOptions → IWarningCallback → output konsol](/images/warning-callback-tutorial.png "diagram tutorial callback peringatan")

*Diagram ini menggambarkan bagaimana callback peringatan menyela peristiwa substitusi font selama proses pemuatan dokumen.*

---

## Ringkasan & Langkah Selanjutnya

Kami baru saja menyelesaikan **tutorial callback peringatan** yang menunjukkan cara **load word document java** dengan gaya sambil **handle missing fonts** secara elegan. Poin penting yang dapat diambil:

1. Implementasikan `IWarningCallback` dan filter untuk `WarningType.FONT_SUBSTITUTION`.  
2. Lampirkan callback ke `LoadOptions` sebelum memuat dokumen.  
3. Verifikasi hasil dengan menyimpan atau mengekstrak teks, dan opsional sesuaikan jalur pencarian font.

Dari sini Anda dapat menjelajahi:

- **Custom font substitution**: Ganti font yang hilang dengan salah satu pilihan Anda secara programatik.  
- **Batch processing**: Loop melalui folder dokumen, kumpulkan semua peringatan substitusi ke dalam laporan CSV.  
- **Integration with logging frameworks**: Salurkan peringatan ke Log4j atau SLF4J untuk diagnostik tingkat produksi.

Cobalah ide‑ide tersebut, dan Anda akan segera melihat betapa kuatnya callback peringatan yang ditempatkan dengan tepat dalam alur kerja dokumen dunia nyata.

---

### Ada Pertanyaan?

Silakan tinggalkan komentar di bawah atau hubungi saya di GitHub. Selamat coding, semoga dokumen Anda selalu ter-render dengan font yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}