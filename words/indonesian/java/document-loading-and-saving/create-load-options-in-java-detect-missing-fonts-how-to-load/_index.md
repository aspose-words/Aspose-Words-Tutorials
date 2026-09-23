---
category: general
date: 2026-02-18
description: Buat opsi pemuatan di Java untuk mendeteksi font yang hilang dan pelajari
  cara memuat file DOCX dengan callback peringatan.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: id
og_description: Buat opsi pemuatan di Java untuk mendeteksi font yang hilang dan pelajari
  cara memuat file DOCX dengan callback peringatan.
og_title: Buat Load Options di Java – Deteksi Font yang Hilang & Cara Memuat DOCX
tags:
- java
- aspose-words
- document-processing
title: Buat Opsi Memuat di Java – Deteksi Font yang Hilang & Cara Memuat DOCX
url: /id/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

curly braces? That's HTML attribute? The alt is inside the attribute alt="Create Load Options flow diagram". Should we translate alt? Probably yes, as it's text. But the alt attribute is inside HTML-like attribute; we can translate the value. The image alt text before the URL is also text: "Diagram showing the flow of creating load options, setting a warning callback, and loading a DOCX file". That should be translated. The alt attribute also. We'll translate both.

We must keep the code block placeholders unchanged.

Now translate headings and paragraphs.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Load Options di Java – Mendeteksi Font yang Hilang & Cara Memuat DOCX

Pernah bertanya-tanya bagaimana **membuat load options** yang tidak hanya membaca sebuah DOCX tetapi juga memberi tahu Anda ketika sebuah font hilang? Anda tidak sendirian. Font yang hilang dapat mengubah dokumen yang sudah bergaya menjadi berantakan, dan menemukan masalah ini lebih awal menghemat berjam‑jam debugging. Pada tutorial ini kami akan menelusuri langkah‑langkah tepat untuk **mendeteksi font yang hilang** sambil menunjukkan **cara memuat file DOCX** dengan callback peringatan khusus.

## Apa yang Akan Anda Pelajari

- Cara menginstansiasi `LoadOptions` dan mengonfigurasi handler peringatan.  
- Mengapa callback peringatan penting untuk menangkap masalah substitusi font.  
- Kode tepat yang dibutuhkan untuk **memuat file DOCX** dengan aman, plus beberapa tip praktis untuk proyek dunia nyata.  
- Penanganan kasus tepi, seperti menangani tipe peringatan lain atau memuat PDF dengan pendekatan yang sama.

Tidak diperlukan dokumentasi eksternal—semua yang Anda butuhkan ada di sini.

## Prasyarat

- Java 17 atau lebih baru (API ini juga bekerja pada versi lama, tetapi 17 adalah pilihan terbaik).  
- Library Aspose.Words for Java sudah ditambahkan ke proyek Anda (`aspose-words-x.x.jar`).  
- Pemahaman dasar tentang penanganan exception di Java.  

Jika Anda sudah memiliki semua itu, mari kita mulai.

![Diagram yang menunjukkan alur pembuatan load options, penetapan callback peringatan, dan pemuatan file DOCX](/images/create-load-options-diagram.png){: .center-image alt="Diagram alur Create Load Options"}

## Langkah 1: Membuat Load Options (Cara Memuat DOCX)

Hal pertama yang harus Anda lakukan adalah **membuat load options**. Objek ini memberi tahu Aspose.Words bagaimana bersikap saat membuka sebuah file. Anggap saja sebagai sekumpulan instruksi yang Anda serahkan ke library sebelum ia bahkan melihat DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Mengapa tidak langsung memanggil `new Document("file.docx")`? Karena tanpa `LoadOptions` Anda kehilangan kemampuan untuk merespons peringatan—seperti font yang hilang—hingga setelah dokumen sudah dimuat, yang mungkin terlalu terlambat untuk beberapa alur kerja.

## Langkah 2: Menyiapkan Callback Peringatan untuk Mendeteksi Font yang Hilang

Sekarang kita melampirkan callback yang akan dipanggil setiap kali Aspose.Words menemukan situasi yang ingin diperingatkan. Dalam kasus kami, kami tertarik pada `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Beberapa hal yang perlu dicatat:

- **Mengapa callback?** Callback dijalankan *selama* proses pemuatan, memberi Anda kesempatan untuk mencatat atau bahkan membatalkan operasi sebelum dokumen sepenuhnya terbentuk.  
- **Mengapa memeriksa `WarningType.FONT_SUBSTITUTION`?** Itu adalah nilai enum tepat yang digunakan Aspose.Words untuk skenario font yang hilang. Tipe peringatan lain (misalnya `TABLE_STRUCTURE`) dapat difilter dengan cara serupa bila diperlukan.  
- **Tip performa:** Callback ringan; hindari I/O berat di dalamnya. Jika Anda perlu menulis ke file, antrikan pesan dan flush setelah pemuatan selesai.

## Langkah 3: Memuat File DOCX dengan Opsi yang Sudah Dikonfigurasi

Dengan opsi dan callback siap, Anda akhirnya dapat memuat DOCX. Inilah bagian yang menjawab **cara memuat docx** sambil menghormati peringatan yang telah Anda atur.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Apa yang terjadi di balik layar?** Saat file mengalir, Aspose.Words memeriksa setiap referensi font. Jika sebuah font yang direferensikan tidak terpasang, ia memicu callback peringatan yang telah kita definisikan sebelumnya. Anda akan melihat output seperti:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Umpan balik langsung ini sangat berharga ketika Anda memproses batch file di server.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut adalah program mandiri yang dapat Anda salin‑tempel ke IDE Anda.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Output yang diharapkan**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Jika file tidak memiliki font yang hilang, callback tetap diam dan baris “DOCX loaded” muncul.

## Pro Tips & Kasus Tepi

| Situasi | Apa yang Harus Dilakukan |
|-----------|------------|
| **Beberapa font yang hilang** | Callback dipanggil untuk masing‑masing, jadi Anda akan mendapatkan satu baris per font. Kumpulkan mereka ke dalam `List<String>` bila Anda membutuhkan ringkasan nanti. |
| **Anda juga ingin menangkap peringatan lain** | Tambahkan cabang `else if` untuk `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT`, dll. |
| **Memuat file DOCX berukuran besar** | Gunakan `LoadOptions.setLoadFormat(LoadFormat.DOCX)` untuk memberi petunjuk format dan mempercepat deteksi. |
| **Menjalankan di layanan web** | Hindari `System.out.println`; sebaliknya, injeksikan logger (`SLF4J`, `Log4j`) di dalam callback. |
| **Font dipasang pada runtime** | Setelah mendeteksi font yang hilang, Anda dapat memuatnya secara programatis lewat `GraphicsEnvironment.registerFont(...)` dan memuat ulang dokumen. |

## Mengapa Pendekatan Ini Lebih Baik daripada Metode “Cuma Try‑Catch”

Banyak pengembang hanya membungkus `new Document(...)` dalam blok try‑catch, berharap sebuah exception akan memberi tahu mereka tentang font yang hilang. Sayangnya, Aspose.Words memperlakukan substitusi font sebagai *peringatan*, bukan error, sehingga tidak ada exception yang dilempar. Dengan **membuat load options** dan melampirkan callback peringatan, Anda mendapatkan wawasan deterministik tentang masalah font tanpa mengorbankan performa.

## Langkah Selanjutnya

- **Mendeteksi font yang hilang pada PDF** – pola `LoadOptions` yang sama berlaku untuk PDF, cukup ubah jalur file dan format pemuatan.  
- **Mengotomatiskan instalasi font** – gabungkan callback dengan skrip yang mengambil font yang hilang dari repositori bersama.  
- **Jelajahi tipe peringatan lain** – Aspose.Words dapat memberi peringatan tentang tag yang usang, tabel kompleks, dan lainnya.  

Silakan bereksperimen: ganti konstruktor `Document` dengan stream (`new Document(InputStream, loadOptions)`) jika Anda menangani data dalam memori, atau rangkai beberapa callback menggunakan pola komposit untuk pipeline pemrosesan skala besar.

---

### TL;DR

Kami menunjukkan cara **membuat load options** di Java, menyiapkan callback yang **mendeteksi font yang hilang**, dan akhirnya **memuat file DOCX** dengan aman. Dengan hanya tiga langkah singkat, Anda kini memiliki pola yang dapat dipakai ulang dalam proyek Aspose.Words mana pun.

Ada pertanyaan tentang format file lain atau butuh bantuan menyesuaikan callback untuk lingkungan spesifik Anda? Tinggalkan komentar di bawah, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}