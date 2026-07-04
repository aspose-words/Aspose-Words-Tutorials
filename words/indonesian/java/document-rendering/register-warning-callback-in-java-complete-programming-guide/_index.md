---
category: general
date: 2026-05-23
description: Daftarkan callback peringatan di Java untuk mendeteksi font yang hilang
  dan menangani substitusi font. Pelajari langkah demi langkah dengan contoh lengkap.
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: id
og_description: Daftarkan callback peringatan di Java untuk mendeteksi font yang hilang.
  Tutorial ini menunjukkan solusi lengkap dengan kode, penjelasan, dan praktik terbaik.
og_title: Daftarkan Callback Peringatan di Java – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Mendaftarkan Callback Peringatan di Java – Panduan Pemrograman Lengkap
url: /id/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftarkan Callback Peringatan di Java – Panduan Pemrograman Lengkap

Pernah perlu **mendaftarkan callback peringatan** di Java tetapi tidak yakin cara menangkap masalah font yang hilang? Anda tidak sendirian. Ketika dokumen bergantung pada tipe huruf khusus, substitusi font secara diam‑diam dapat merusak tata letak, dan satu‑satunya cara andal untuk mendeteksinya adalah dengan mendengarkan peringatan. Dalam panduan ini kami akan membahas solusi praktis yang tidak hanya **mendaftarkan callback peringatan** tetapi juga **mendeteksi font yang hilang** sebelum mereka secara diam‑diam merusak output Anda.

Masalahnya—Aspose.Words untuk Java menyediakan API yang bersih untuk manajemen font, namun banyak pengembang melewatkan langkah callback peringatan dan berakhir dengan PDF yang tidak mirip sama sekali dengan file Word asli. Pada akhir tutorial ini Anda akan memiliki potongan kode siap‑jalankan, memahami mengapa setiap baris penting, dan mengetahui cara memperluas pendekatan untuk skenario yang lebih kompleks.

## Apa yang Akan Anda Pelajari

Di beberapa bagian berikut kami akan membahas:

* Cara membuat `LoadOptions` dan mengaktifkan penanganan font khusus.  
* Cara **mendaftarkan callback peringatan** untuk menangkap peristiwa `FONT_SUBSTITUTION`.  
* Cara **mendeteksi font yang hilang** dan mencatat informasi berguna untuk debugging.  
* Contoh Java lengkap yang dapat dijalankan dan Anda dapat menempelkannya ke IDE hari ini.

Tidak diperlukan pustaka eksternal selain Aspose.Words, dan kode ini bekerja dengan Java 8+ dan Aspose.Words 23.9 (atau lebih baru). Jika Anda sudah memiliki proyek yang memuat file `.docx`, Anda hanya perlu menambahkan beberapa baris—tanpa refaktor besar.

## Prasyarat

* Java Development Kit (JDK) 8 atau lebih baru.  
* Aspose.Words untuk Java (unduh dari situs resmi atau tambahkan dependensi Maven).  
* Akses ke direktori yang berisi dokumen Word yang ingin Anda muat.  
* Familiaritas dasar dengan lambda Java atau kelas anonim (kami akan menggunakan kelas anonim untuk kejelasan).

Jika ada yang terdengar asing, jangan panik—setiap langkah dijelaskan dalam bahasa yang mudah dipahami, dan komentar kode mengisi kekosongan.

---

## Langkah 1: Buat Load Options dan Aktifkan Penanganan Font Khusus

Sebelum kita dapat mendengarkan peringatan terkait font, kita memerlukan instance `LoadOptions` yang memberi tahu Aspose.Words untuk menggunakan `FontSettings` milik kita. Anggap `LoadOptions` sebagai “kantong pengaturan” yang Anda serahkan ke pemuat dokumen.

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**Mengapa ini penting:**  
`FontSettings` adalah gerbang ke semua yang dilakukan perpustakaan dengan font—jalur pencarian, aturan substitusi, dan yang paling krusial, callback peringatan. Dengan membuat objek `FontSettings` khusus, Anda mendapatkan kontrol penuh atas cara font yang hilang diperlakukan alih‑alih mengandalkan nilai default perpustakaan.

> **Tip pro:** Jika aplikasi Anda sudah menyediakan `FontSettings` bersama (misalnya, untuk konversi PDF), gunakan kembali di sini agar resolusi font tetap konsisten di seluruh pipeline.

---

## Langkah 2: Daftarkan Callback Peringatan untuk Mendeteksi Font yang Hilang

Sekarang masuk ke inti tutorial: kami **mendaftarkan callback peringatan** pada `FontSettings` yang baru saja dibuat. Callback menerima objek `WarningInfo` untuk setiap peringatan yang dikeluarkan selama pemuatan dokumen.

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**Penjelasan logika:**

* `setWarningCallback` menempelkan listener khusus kami.  
* Di dalam `warning(WarningInfo info)`, kami memeriksa `info.getWarningType()`.  
* Ketika tipe sama dengan `WarningType.FONT_SUBSTITUTION`, perpustakaan memberi tahu bahwa ia tidak dapat menemukan font asli dan harus menggantinya dengan yang lain.  
* `info.getDescription()` berisi pesan yang dapat dibaca manusia seperti *“Font 'MyCustomFont' not found, substituted with 'Arial'.”*  

Dengan mencetak deskripsi tersebut, kami **mendeteksi font yang hilang** secara instan selama fase pemuatan, memungkinkan Anda mencatat, memberi peringatan, atau bahkan menghentikan operasi jika substitusi tidak dapat diterima.

> **Mengapa tidak cukup menangkap exception?**  
> Font yang hilang jarang melempar exception; mereka mengeluarkan peringatan. Tanpa callback, peringatan tersebut menghilang ke dalam kekosongan, dan Anda tidak pernah tahu bahwa kesetiaan visual dokumen telah terganggu.

### Opsional: Menggunakan Lambda (Java 8+)

Jika Anda lebih suka sintaks yang lebih ringkas, callback yang sama dapat dituliskan dengan lambda:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

Kedua pendekatan mencapai tujuan yang sama—pilih gaya yang cocok dengan basis kode Anda.

---

## Langkah 3: Muat Dokumen dengan Opsi yang Telah Dikonfigurasi

Dengan callback yang sudah dipasang, langkah terakhir adalah memuat dokumen. Konstruktor `Document` menerima jalur dan `LoadOptions` yang telah kita siapkan.

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Apa yang terjadi di balik layar?**  
Selama pemanggilan ini Aspose.Words mem-parsing file `.docx`, menyelesaikan setiap font yang direferensikan, dan memicu callback peringatan kami untuk setiap tipe huruf yang hilang. Jika semuanya ada, tidak akan ada output di konsol; jika tidak, Anda akan melihat baris seperti:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

Output tersebut adalah bukti konkret bahwa kami **mendaftarkan callback peringatan** dengan sukses dan **mendeteksi font yang hilang**.

---

## Contoh Kerja Lengkap

Berikut adalah program Java lengkap yang dapat Anda salin‑tempel ke file `Main.java` dan jalankan. Pastikan JAR Aspose.Words berada di classpath.

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan** (ketika font hilang):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

Jika semua font tersedia, Anda hanya akan melihat pesan keberhasilan.

---

## Menangani Kasus Tepi dan Kesalahan Umum

| Situasi | Hal yang Perlu Diwaspadai | Solusi yang Disarankan |
|-----------|-------------------|---------------|
| **Beberapa font yang hilang** | Callback dapat dipicu berkali‑kali, membuat log berantakan. | Kumpulkan pesan atau tulis ke file untuk analisis nanti. |
| **Dampak performa** | Logging berlebihan dapat memperlambat pemrosesan batch besar. | Filter peringatan berdasarkan tingkat keparahan atau nonaktifkan output konsol di produksi. |
| **Direktori font khusus** | `FontSettings` secara default hanya menggunakan font sistem. | Panggil `fontSettings.setFontsFolder("path/to/custom/fonts", true);` sebelum mendaftarkan callback. |
| **Substitusi diam‑diam** | Beberapa font dapat disubstitusi tanpa peringatan jika dianggap mirip. | Setel `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` dan sesuaikan aturan substitusi. |

Dengan mengantisipasi skenario ini Anda akan menjaga aplikasi tetap tangguh dan log tetap bermakna.

---

## Memperluas Solusi

Sekarang Anda tahu cara **mendaftarkan callback peringatan** dan **mendeteksi font yang hilang**, Anda mungkin ingin:

* **Menghentikan pemuatan** ketika font kritis tidak ditemukan (lempar exception di dalam callback).  
* **Mengumpulkan nama font yang hilang** ke dalam `Set<String>` untuk laporan ringkasan setelah dokumen dimuat.  
* **Mengintegrasikan dengan sistem pemantauan** (misalnya, kirim peringatan ke Slack atau Azure Monitor).  

Semua ekstensi ini dibangun di atas pola callback yang telah kami demonstrasikan.

---

## Kesimpulan

Kami telah menelusuri contoh lengkap yang siap produksi yang menunjukkan cara **mendaftarkan callback peringatan** di Java, memungkinkan Anda **mendeteksi font yang hilang** pada saat dokumen dimuat. Poin penting yang dapat diambil:

* Buat `LoadOptions` dengan `FontSettings` khusus.  
* Lampirkan `IWarningCallback` yang menyaring peringatan `FONT_SUBSTITUTION`.  
* Muat dokumen menggunakan opsi tersebut dan tanggapi setiap kejadian font yang hilang.

Dengan pengetahuan ini Anda dapat melindungi pipeline pemrosesan dokumen, memastikan kesetiaan visual, dan memberikan diagnostik yang jelas kepada pengguna akhir.  

Siap melangkah lebih jauh? Coba tambahkan folder font, bereksperimen dengan kebijakan substitusi yang berbeda, atau hubungkan callback ke kerangka logging yang sudah ada. Kemungkinannya seluas perpustakaan font yang Anda kelola.

Selamat coding, semoga PDF Anda selalu tampil persis seperti yang diharapkan!


## Tutorial Terkait

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}