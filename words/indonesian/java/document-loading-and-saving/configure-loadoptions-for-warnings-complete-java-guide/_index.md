---
category: general
date: 2026-06-30
description: Konfigurasikan LoadOptions untuk peringatan di Aspose.Words Java. Pelajari
  cara mengatur callback peringatan untuk substitusi font dan peringatan load‑options
  lainnya.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: id
og_description: Konfigurasikan LoadOptions untuk peringatan di Aspose.Words Java.
  Panduan ini menunjukkan cara menangkap peringatan substitusi font dengan callback
  peringatan.
og_title: Konfigurasikan LoadOptions untuk Peringatan – Tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Konfigurasikan LoadOptions untuk Peringatan – Panduan Java Lengkap
url: /id/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konfigurasikan LoadOptions untuk Peringatan – Panduan Lengkap Java

Pernah perlu **mengonfigurasi LoadOptions untuk peringatan** saat membuka dokumen Word dengan Aspose.Words for Java? Anda tidak sendirian. Banyak pengembang mengalami masalah ketika font yang hilang secara diam-diam diganti, membuat PDF akhir terlihat tidak sesuai merek. Kabar baik? Dengan menambahkan **callback peringatan Java** ke dalam `LoadOptions` Anda, Anda dapat menangkap setiap peringatan substitusi font pada saat terjadi.

Dalam tutorial ini kami akan membahas contoh langsung yang tidak hanya menunjukkan cara menyiapkan callback tetapi juga menjelaskan *mengapa* setiap bagian penting. Pada akhir tutorial Anda akan dapat **menangani peringatan font**, mencatatnya, atau bahkan mengganti font secara dinamis—tanpa tebakan.

## Apa yang Akan Anda Dapatkan

- Program Java yang dapat dijalankan sepenuhnya yang mencetak setiap peringatan substitusi font.
- Pemahaman tentang mekanisme **Aspose.Words font substitution**.
- Tips untuk menyesuaikan penanganan peringatan untuk proyek yang lebih besar.
- Wawasan tentang **document loading options** dan kapan harus menyesuaikannya.

> **Prasyarat:** Java 8+ dan pustaka Aspose.Words for Java (versi 23.9 atau lebih baru). Tidak ada dependensi eksternal lain yang diperlukan.

---

## Langkah 1: Konfigurasikan LoadOptions untuk Peringatan

Hal pertama yang Anda butuhkan adalah instance `LoadOptions` yang mengetahui bahwa ia harus melaporkan peringatan. Anggap `LoadOptions` sebagai kotak perkakas yang Anda berikan kepada Aspose.Words sebelum ia membuka file.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Mengapa ini penting:**  
`LoadOptions` mengontrol cara perpustakaan membaca dokumen. Dengan menetapkan sebuah `IWarningCallback`, Anda memberi tahu Aspose.Words untuk memanggil kode Anda setiap kali menemukan sesuatu yang penting—seperti font yang hilang. Tanpa ini, perpustakaan akan secara diam-diam mengganti font dan Anda tidak akan pernah mengetahuinya.

> **Tip Pro:** Jika Anda ingin menangkap *semua* peringatan, hapus pemeriksaan `if`. Untuk saat ini kami fokus pada masalah font karena itu merupakan sumber kejutan tata letak yang paling umum.

---

## Langkah 2: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Setelah callback siap, muat file `.docx` Anda (atau format lain yang didukung) dengan `LoadOptions` yang sama. Di sinilah **document loading options** benar‑benar berpengaruh.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Di balik layar:**  
Saat Aspose.Words mem-parsing `input.docx`, ia memindai tabel font. Jika sebuah font yang direferensikan dalam dokumen tidak terpasang di mesin host, mesin akan mengeluarkan peringatan `FONT_SUBSTITUTION`, yang langsung memicu callback yang telah kita definisikan sebelumnya.

---

## Langkah 3: Simpan Dokumen – Peringatan Telah Dicetak

Menyimpan dokumen cukup sederhana, tetapi itu adalah momen di mana Anda dapat memverifikasi bahwa callback telah dipanggil dengan benar. Semua peringatan dicetak selama langkah pemuatan, sehingga operasi penyimpanan hanya bersifat pembersihan.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Expected console output:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Jika tidak ada output, kemungkinan dokumen hanya menggunakan font yang terpasang, atau callback tidak terhubung dengan benar—periksa kembali Langkah 1.

---

## Langkah 4: Perluas Callback untuk **Menangani Peringatan Font** dengan Elegan

Mencetak ke konsol cukup untuk demo, tetapi kode produksi sering memerlukan penanganan yang lebih kaya: mencatat ke file, mengirim peringatan, atau bahkan menukar font secara programatis.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Mengapa Anda melakukannya:**  
File log memberi Anda wawasan pasca‑mortem, terutama saat memproses batch dokumen. Blok substitusi opsional menunjukkan cara **mengonfigurasi LoadOptions untuk peringatan** *dan* campur tangan untuk menegakkan kebijakan font perusahaan.

---

## Lanjutan: Mengontrol Skenario **Aspose.Words Font Substitution** Lainnya

Callback peringatan tidak terbatas pada font yang hilang. Anda juga dapat menangkap:

- **Karakter Unicode yang tidak didukung** (`WarningType.UNSUPPORTED_CHAR`).
- **Masalah skrip kompleks** (`WarningType.COMPLEX_SCRIPT`).

Cukup perluas pernyataan `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Ini membuat solusi Anda kuat untuk dokumen multibahasa, sebuah kasus tepi yang umum dalam aplikasi global.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap dijalankan. Tempelkan ke dalam IDE Java apa pun, ganti placeholder `YOUR_DIRECTORY`, dan tekan *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Hasil yang Diharapkan

- Konsol mencetak semua peringatan substitusi font.
- `font-warnings.log` berisi daftar berstempel waktu (jika Anda menyimpan logging opsional).
- `output.docx` disimpan dengan font yang diganti, sesuai fallback yang Anda definisikan.

---

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|-----------------|--------|
| **Tidak ada peringatan muncul** | Callback tidak terpasang, atau dokumen hanya menggunakan font yang terpasang. | Pastikan `loadOptions.setWarningCallback(...)` dipanggil *sebelum* memuat dokumen. |
| **FileNotFoundException** pada `input.docx` | Jalur salah atau file tidak termasuk dalam proyek. | Gunakan jalur absolut atau letakkan file di folder resources proyek. |
| **Penurunan performa** saat memproses ribuan dokumen | Logging berlebihan ke disk pada setiap peringatan. | Buffer log dan tulis secara batch, atau batasi logging hanya pada peringatan kritis. |
| **Substitusi font tak terduga** meskipun ada fallback | Tabel substitusi tidak diterapkan cukup awal. | Tetapkan pengaturan substitusi **sebelum** memuat dokumen, atau gunakan `FontSettings.setSubstitutionSettings` secara global. |

---

## Langkah Selanjutnya

Setelah Anda menguasai **mengonfigurasi LoadOptions untuk peringatan**, pertimbangkan topik lanjutan berikut:

- **Pemrosesan batch**: Loop melalui direktori dokumen, mengumpulkan semua peringatan font menjadi satu laporan.
- **Penyedia font khusus**: Muat font dari jaringan bersama atau sumber daya tersemat alih-alih OS lokal.
- **Integrasikan dengan kerangka kerja logging** seperti Log4j untuk jejak tingkat perusahaan.
- Jelajahi **document loading options** lainnya seperti deteksi `LoadFormat` atau penanganan `Password` untuk file yang dilindungi.

Setiap hal ini dibangun di atas pola yang sama—buat objek `LoadOptions`, lampirkan callback yang sesuai, dan biarkan Aspose.Words melakukan pekerjaan berat.

---

## Kesimpulan

Kami telah menyelami cara **mengonfigurasi LoadOptions untuk peringatan** di Aspose.Words for Java, menyiapkan **callback peringatan Java**, dan menggunakan informasi tersebut untuk **menangani peringatan font** secara cerdas. Kode ini ringkas, konsepnya jelas, dan Anda kini memiliki fondasi yang kuat untuk memperluas penanganan peringatan ke skenario lain seperti karakter yang tidak didukung atau skrip kompleks.

Cobalah, sesuaikan tabel substitusi agar cocok dengan font merek Anda, dan saksikan pertukaran font diam‑diam menghilang. Selamat coding!

![Diagram yang menunjukkan alur mengonfigurasi LoadOptions untuk peringatan, memuat dokumen, menangkap peristiwa substitusi font, dan menyimpan output](configure-loadoptions-for-warnings-diagram.png "Alur mengonfigurasi LoadOptions untuk peringatan")

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menangkap Peringatan Substitusi Font di Java dengan Aspose.Words – Panduan Lengkap](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cara Memuat Dokumen RTF dengan Mengonfigurasi Opsi Muat RTF di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}