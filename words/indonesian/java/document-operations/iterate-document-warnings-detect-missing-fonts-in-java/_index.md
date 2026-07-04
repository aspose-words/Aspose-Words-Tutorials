---
category: general
date: 2026-04-28
description: Iterasi peringatan dokumen dalam file Word untuk mendeteksi font yang
  hilang, mengambil nama font yang hilang, dan mencetak detail font yang hilang menggunakan
  Aspose.Words untuk Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: id
og_description: Iterasi peringatan dokumen untuk menemukan font yang hilang, mengambil
  nama font yang hilang, dan mencetak detail font yang hilang dengan contoh Java lengkap.
og_title: 'Iterasi peringatan dokumen: Deteksi Font yang Hilang di Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterasi peringatan dokumen: Deteksi Font yang Hilang di Java'
url: /id/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterasi peringatan dokumen – Deteksi Font yang Hilang di Java

Pernah perlu **iterate document warnings** saat membuka file Word dan bertanya-tanya font apa yang hilang? Anda bukan satu‑satunya. Font yang hilang dapat merusak tampilan laporan, dan tanpa cara untuk menemukannya Anda mungkin mengirimkan dokumen yang tampak sangat berbeda dari aslinya.  

Dalam tutorial ini kami akan menunjukkan cara **detect missing fonts** dengan memuat dokumen Word, mengiterasi peringatannya, mengambil nama font yang hilang, dan akhirnya mencetak informasi font yang hilang—semua dengan Aspose.Words for Java.  

Kami akan membahas semuanya mulai dari baris kode pertama hingga output konsol yang diharapkan, sehingga Anda dapat menyalin‑tempel solusi yang bekerja ke dalam proyek Anda sekarang juga. Tidak perlu dokumen tambahan.

## Prasyarat

- Java 8 atau lebih baru terpasang.
- Perpustakaan Aspose.Words for Java (versi terbaru per 2026‑04‑28).
- File Word yang mungkin berisi font yang tidak terpasang di mesin Anda (misalnya, `doc-with-missing-font.docx`).

Jika Anda sudah memiliki semua itu, bagus—Anda siap **load word document** dan mulai mengiterasi.

## Langkah 1 – Load Word Document dengan Opsi Default

Sebelum kita dapat **iterate document warnings**, file harus dimuat ke memori. Aspose.Words memungkinkan Anda melakukan ini dengan satu pemanggilan konstruktor. Menggunakan `LoadOptions` default biasanya sudah cukup, tetapi kami akan menunjukkan pembuatan eksplisit untuk kejelasan.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Mengapa ini penting:**  
> Memuat dokumen memicu Aspose.Words untuk memindai file demi menemukan sumber daya yang tidak dapat di‑resolve, seperti font yang tidak terpasang secara lokal. Masalah‑masalah tersebut disimpan sebagai **warnings**, yang akan kita **iterate document warnings** pada langkah berikutnya.

## Langkah 2 – Iterate Document Warnings untuk Menemukan Masalah Font

Berikutnya adalah inti solusi: kita melintasi setiap peringatan yang dikumpulkan perpustakaan saat memuat. Objek `WarningInfo` memberi tahu apa yang salah, dan kita dapat menyaring `FontSubstitutionWarning` untuk **detect missing fonts**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Tip profesional:** Pemeriksaan `instanceof` memastikan kita hanya menangani peringatan yang berhubungan dengan font, mengabaikan yang lain seperti masalah pemuatan gambar. Ini membuat loop menjadi efisien dan output terfokus pada font yang memang perlu Anda **retrieve missing font**.

### Output Konsol yang Diharapkan

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Jika dokumen tidak mengandung font yang hilang, loop akan selesai dengan diam—tidak ada yang **print missing font**.

## Langkah 3 – Mengapa Tidak Hanya Menangkap Exception?

Anda mungkin bertanya, “Mengapa tidak membungkus pemanggilan `new Document(...)` dengan try‑catch dan mencari exception?” Jawabannya dua‑lipat:

1. **Informasi Granular:** Exception hanya memberi tahu bahwa sesuatu gagal. Warning memberikan nama font yang tepat dan fallback yang dipilih Aspose.Words.
2. **Masalah Non‑Fatal:** Font yang hilang biasanya tidak fatal; dokumen tetap dapat dimuat, tetapi kesetiaan visual terganggu. Dengan **iterating document warnings**, Anda tetap dapat memproses sisa file.

## Langkah 4 – Memperluas Contoh: Mengumpulkan Font yang Hilang ke dalam List

Terkadang Anda memerlukan font yang hilang untuk pemrosesan lebih lanjut—mungkin untuk menyematkannya atau memberi peringatan kepada pengguna melalui UI. Berikut modifikasi singkat yang mengumpulkan nama‑nama tersebut ke dalam `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Sekarang Anda memiliki cara bersih untuk **retrieve missing font** secara programatis, yang dapat Anda salurkan ke modul pelaporan atau wizard instalasi font.

## Langkah 5 – Pertimbangan Dunia Nyata

- **Multiple Substitutions:** Satu font yang hilang dapat disubstitusi oleh font berbeda di bagian dokumen yang berbeda. Daftar warning akan berisi setiap kejadian, sehingga Anda mungkin melihat entri font‑hilang yang duplikat.
- **Kinerja:** Memuat dokumen sangat besar dapat menghasilkan ribuan warning. Jika Anda hanya peduli pada font, saring lebih awal seperti yang ditunjukkan untuk menjaga loop tetap cepat.
- **Font Lintas Platform:** Di Linux, font substitusi default sering kali *Liberation Sans*. Di Windows, biasanya *Arial*. Mengetahui fallback membantu Anda memutuskan apakah perlu menyertakan font khusus bersama aplikasi Anda.

## Langkah 6 – Bantuan Visual

Berikut adalah tangkapan layar output konsol (teks alt mencakup kata kunci utama untuk SEO).

![Output konsol iterate document warnings yang menampilkan font yang hilang dan substitusinya](/images/iterate-document-warnings.png)

*Alt text:* *contoh iterate document warnings yang menampilkan nama font yang hilang dan detail substitusinya.*

## Kesimpulan

Anda baru saja mempelajari cara **iterate document warnings** di Aspose.Words for Java, **detect missing fonts**, **load word document** dengan aman, **retrieve missing font** information, dan **print missing font** details ke konsol. Potongan kode lengkap dapat dijalankan apa adanya, dan Anda dapat menyesuaikannya untuk mencatat ke file, menampilkan dialog UI, atau bahkan menyematkan font yang hilang secara otomatis ke dalam file.

Selanjutnya, Anda mungkin ingin menjelajahi cara **load word document** dengan sumber font khusus (misalnya menambahkan folder berisi font perusahaan) atau cara menyematkan font yang hilang langsung ke dalam file untuk mempertahankan tata letak di semua mesin. Kedua topik tersebut merupakan kelanjutan alami dari apa yang telah kami bahas.

Selamat coding, semoga PDF Anda selalu tampil persis seperti yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}