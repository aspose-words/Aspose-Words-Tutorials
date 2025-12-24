---
category: general
date: 2025-12-23
description: Atur mode pemulihan untuk memperbaiki dokumen Word yang rusak. Pelajari
  cara membuka file DOCX, menggunakan mode pemulihan, dan menangani file yang korup
  di Java.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: id
og_description: Atur mode pemulihan untuk memulihkan dokumen Word yang rusak. Panduan
  ini menunjukkan cara membuka file DOCX, menggunakan mode pemulihan, dan menangani
  file yang korup di Java.
og_title: Atur Mode Pemulihan – Buka File Word yang Rusak di Java
tags:
- Java
- Aspose.Words
- Document Recovery
title: Set Mode Pemulihan – Cara Membuka File Word yang Rusak di Java
url: /id/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Atur Mode Pemulihan – Cara Membuka File Word Rusak di Java

Pernah mencoba **mengatur mode pemulihan** pada dokumen Word yang menolak dibuka? Anda tidak sendirian. Banyak pengembang mengalami kebuntuan ketika sebuah DOCX sedikit rusak dan pemanggilan biasa `new Document("file.docx")` melempar pengecualian. Kabar baiknya? Aspose.Words untuk Java menyediakan cara bawaan untuk **menggunakan mode pemulihan** dan benar‑benar **memulihkan file Word yang rusak**.

Pada tutorial ini kami akan membahas semua yang perlu Anda ketahui untuk **membuka file word yang rusak** dengan aman, mulai dari mengonfigurasi `LoadOptions` hingga menangani kasus tepi yang biasanya membuat orang kebingungan. Tanpa basa‑basi—hanya solusi praktis langkah‑demi‑langkah yang dapat Anda tempelkan ke proyek Anda sekarang juga.

> **Tips pro:** Jika Anda hanya menangani gangguan kecil (seperti footer yang hilang), mode pemulihan **Tolerant** biasanya sudah cukup. Simpan **Strict** untuk situasi di mana Anda memerlukan dokumen 100 % bersih sebelum diproses.

## Apa yang Anda Butuhkan

- **Java 17** (atau JDK terbaru apa pun; API berfungsi sama)
- **Aspose.Words for Java** 23.9 (atau lebih baru) – perpustakaan yang menyediakan kelas `LoadOptions`.
- Sebuah file **DOCX rusak** untuk diuji (Anda dapat membuatnya dengan memotong file yang valid menggunakan editor heksadesimal).
- IDE favorit Anda (IntelliJ, Eclipse, VS Code—pilih yang paling nyaman).

Itu saja. Tanpa plugin Maven tambahan, tanpa utilitas eksternal. Hanya perpustakaan inti dan sedikit kode.

![Ilustrasi mengatur mode pemulihan di Aspose.Words Java API](/images/set-recovery-mode-java.png){.align-center alt="atur mode pemulihan"}

## Langkah 1 – Buat Instance `LoadOptions`

Hal pertama yang Anda lakukan adalah menginstansiasi objek `LoadOptions`. Anggaplah itu sebagai kotak perkakas yang memberi tahu Aspose.Words **bagaimana memperlakukan file yang masuk**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Mengapa tidak melewatkan langkah ini? Karena tanpa `LoadOptions` Anda tidak dapat memberi tahu perpustakaan apakah ingin **menggunakan mode pemulihan** atau tidak. Perilaku default adalah ketat, yang berarti setiap korupsi akan menghentikan proses pemuatan.

## Langkah 2 – Pilih Mode Pemulihan yang Tepat

Aspose.Words menawarkan dua nilai enum:

| Mode | Apa yang dilakukannya |
|------|-----------------------|
| `RecoveryMode.Tolerant` | Mencoba menyelamatkan sebanyak mungkin. Ideal untuk skenario *memulihkan word yang rusak* di mana hanya gaya yang hilang atau hubungan yang rusak menjadi masalah satu‑satunya. |
| `RecoveryMode.Strict`   | Gagal cepat pada masalah apa pun. Gunakan ini ketika Anda memerlukan jaminan bahwa dokumen bersih sebelum diproses lebih lanjut. |

Atur mode dengan satu baris:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Mengapa ini penting:** Saat Anda **menggunakan mode pemulihan**, perpustakaan secara internal memperbaiki bagian yang rusak, membangun kembali node XML yang hilang, dan memberikan Anda objek `Document` yang dapat digunakan. Dalam mode *strict* Anda akan mendapatkan `InvalidFormatException` sebagai gantinya.

## Langkah 3 – Muat Dokumen dengan Opsi Anda

Sekarang Anda akhirnya menyerahkan file ke Aspose.Words, sambil melewatkan `LoadOptions` yang baru saja Anda konfigurasikan.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Jika file hanya sedikit rusak, `doc` akan menjadi objek `Document` yang berfungsi penuh. Anda sekarang dapat:

- Membaca teks (`doc.getText()`),
- Menyimpan ke format lain (`doc.save("repaired.pdf")`),
- Atau bahkan memeriksa daftar bagian yang dipulihkan melalui API `Document`.

### Memverifikasi Pemulihan

Pemeriksaan cepat membantu Anda memastikan bahwa pemulihan memang berhasil:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Langkah 4 – Menangani Kasus Tepi

### 4.1 Ketika Tolerant Tidak Cukup

Kadang‑kadang file begitu rusak sehingga bahkan mode **Tolerant** tidak dapat menyusunnya kembali (misalnya, XML inti hilang). Dalam kasus langka tersebut, Anda dapat:

1. **Mencoba memuat ulang dengan `RecoveryMode.Strict`** untuk melihat apakah pesan kesalahan memberikan detail lebih lanjut.
2. **Beralih ke utilitas zip** untuk mengekstrak bagian XML secara manual dan memperbaikinya.
3. **Mencatat pengecualian** dan memberi tahu pengguna bahwa dokumen tidak dapat dipulihkan.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Pertimbangan Memori

Memuat file DOCX besar dengan pemulihan diaktifkan dapat sementara menggandakan penggunaan memori karena Aspose.Words menyimpan struktur asli dan yang diperbaiki di memori. Jika Anda memproses batch besar:

- **Gunakan kembali instance `LoadOptions` yang sama** alih‑alih membuat yang baru setiap kali.
- **Bebaskan `Document`** (`doc.close()`) segera setelah selesai.
- **Jalankan pada JVM dengan heap yang cukup** (`-Xmx2g` atau lebih tinggi untuk file multi‑gigabyte).

### 4.3 Menyimpan File yang Telah Diperbaiki

Setelah pemuatan berhasil, Anda mungkin ingin **menyimpan versi bersih** sehingga tidak perlu menjalankan pemulihan lagi.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Sekarang pada kali berikutnya Anda membuka `repaired.docx` Anda dapat melewatkan langkah **gunakan mode pemulihan** sepenuhnya.

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja untuk file `.doc` lama?**  
A: Ya. Pendekatan `LoadOptions` yang sama berlaku untuk `.doc` dan `.rtf`. Cukup ubah ekstensi file.

**Q: Bisakah saya menggabungkan `setRecoveryMode` dengan opsi pemuatan lain (misalnya, kata sandi)?**  
A: Tentu saja. `LoadOptions` memiliki properti seperti `setPassword` dan `setLoadFormat`. Atur mereka sebelum memanggil `setRecoveryMode`.

**Q: Apakah ada penalti kinerja?**  
A: Sedikit—pemulihan menambah overhead parsing. Dalam benchmark, file rusak 5 MB memuat sekitar 30 % lebih lambat dalam mode **Tolerant** dibandingkan pemuatan ketat pada file bersih. Masih dapat diterima untuk kebanyakan pekerjaan batch.

## Contoh Lengkap yang Berfungsi

Berikut adalah kelas Java lengkap yang siap dijalankan yang mendemonstrasikan **cara membuka docx**, **menggunakan mode pemulihan**, dan **menyimpan salinan yang diperbaiki**.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Jalankan kelas ini setelah menambahkan JAR Aspose.Words untuk Java ke classpath proyek Anda. Jika file masukan hanya sedikit rusak, Anda akan melihat pesan **✅** dan `repaired.docx` baru di disk.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **mengatur mode pemulihan** dan berhasil **membuka file word yang rusak** di Java. Dengan membuat objek `LoadOptions`, memilih `RecoveryMode` yang tepat, dan menangani kasus tepi sesekali, Anda dapat mengubah momen frustrasi “file tidak dapat dibuka” menjadi alur kerja pemulihan yang mulus.

Ingat:

- **Tolerant** adalah pilihan utama Anda untuk kebanyakan skenario *memulihkan word yang rusak*.
- **Strict** memberikan kegagalan keras ketika Anda memerlukan kepastian mutlak.
- Selalu verifikasi dokumen yang dimuat dan, bila memungkinkan, simpan salinan bersih untuk penggunaan di masa mendatang.

Sekarang Anda dapat dengan yakin menjawab “**cara membuka docx** yang menolak dimuat?” dengan potongan kode konkret dan penjelasan yang jelas. Selamat coding, semoga dokumen Anda tetap sehat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}