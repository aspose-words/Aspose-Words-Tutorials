---
category: general
date: 2026-03-04
description: How to recover DOCX files using Java – learn to set recovery mode and
  display load warnings for corrupted documents in a few easy steps.
draft: false
keywords:
- how to recover docx
- set recovery mode
- use recovery mode
- recover corrupted docx
- display load warnings
language: id
og_description: Cara memulihkan file DOCX menggunakan Java. Panduan ini menunjukkan
  cara mengatur mode pemulihan dan menampilkan peringatan pemuatan saat memuat dokumen
  yang rusak.
og_title: How to Recover DOCX – Set Recovery Mode & Display Warnings
tags:
- Java
- Aspose.Words
- Document Recovery
title: Cara Memulihkan DOCX – Atur Mode Pemulihan & Tampilkan Peringatan
url: /id/java/document-loading-and-saving/how-to-recover-docx-set-recovery-mode-display-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memulihkan DOCX – Mengatur Mode Pemulihan & Menampilkan Peringatan

Pernah membuka file **DOCX** hanya untuk melihat teks yang berantakan atau paragraf yang hilang? Saat itulah Anda mulai bertanya-tanya *bagaimana cara memulihkan docx* tanpa kehilangan jam‑jam kerja. Kabar baiknya, Aspose.Words for Java menyediakan mode pemulihan bawaan yang dapat mendeteksi masalah, menyimpan bagian yang baik, dan bahkan memberi tahu apa yang salah.

Dalam tutorial ini kami akan menelusuri langkah‑langkah tepat untuk **set recovery mode**, **use recovery mode** saat memuat dokumen yang rusak, dan **display load warnings** sehingga Anda tahu persis apa yang telah diperbaiki. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang memulihkan DOCX yang rusak dan memberi tahu berapa banyak peringatan yang dihasilkan.

> **Prerequisite:** Anda memerlukan Aspose.Words for Java (v23.9 atau lebih baru) di classpath Anda. Jika belum memilikinya, dapatkan artefak Maven `com.aspose:aspose-words:23.9` atau unduh JAR dari situs web Aspose.

![how to recover docx](/images/recover-docx.png)

---

## Apa yang Dibahas dalam Panduan Ini

* Cara mengonfigurasi **LoadOptions** untuk mengendalikan perilaku pemulihan.  
* Perbedaan antara `RECOVER_WITH_WARNINGS` dan `RECOVER_SILENTLY`.  
* Cara **display load warnings** setelah dokumen dibuka.  
* Program Java lengkap yang dapat dijalankan dan Anda dapat copy‑paste ke IDE Anda.

Mari kita mulai—tanpa basa‑basi, hanya hal yang benar‑benar menyelesaikan pekerjaan.

---

## Langkah 1: Siapkan Load Options – Pilih Mode Pemulihan yang Tepat

Sebelum Anda menyentuh file, Anda harus memberi tahu Aspose.Words bagaimana bersikap ketika menemukan data yang rusak. Di sinilah **set recovery mode** berperan.

```java
import com.aspose.words.LoadOptions;
import com.aspose.words.LoadOptions.RecoveryMode;

// Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Choose a recovery strategy
// 1️⃣ Recover with warnings – you’ll get a list of issues.
// 2️⃣ Recover silently – the library fixes everything quietly.
loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
// Or, if you prefer no output:
// loadOptions.setRecoveryMode(RecoveryMode.RECOVER_SILENTLY);
```

*Mengapa ini penting:* `RECOVER_WITH_WARNINGS` sangat cocok ketika Anda perlu mengaudit proses perbaikan, sementara `RECOVER_SILENTLY` berguna untuk pekerjaan batch di mana Anda tidak menginginkan kebisingan di konsol.

---

## Langkah 2: Muat DOCX yang Rusak Menggunakan Opsi yang Telah Dikonfigurasi

Sekarang **load options** sudah siap, membuka file menjadi sangat mudah. Perhatikan bagaimana kami melewatkan objek `loadOptions` ke konstruktor `Document`—ini adalah langkah **use recovery mode**.

```java
import com.aspose.words.Document;

// Path to the potentially corrupted file
String corruptedPath = "C:/Docs/corrupted.docx";

// Load the document with the previously defined options
Document document = new Document(corruptedPath, loadOptions);
```

Jika file berada di luar batas perbaikan, Aspose.Words tetap akan melempar `FileCorruptedException`. Dalam kebanyakan skenario dunia nyata, perpustakaan ini menyelamatkan bagian yang dapat dibaca dan menandai sisanya.

---

## Langkah 3: Tampilkan Peringatan Muat – Ketahui Persis Apa yang Telah Diperbaiki

Setelah dokumen dimuat, Anda dapat menanyakan koleksi peringatan. Ini adalah bagian **display load warnings** dari tutorial kami.

```java
// Retrieve the warning collection
int warningCount = document.getWarningInfo().size();

// Print a friendly message
System.out.println("Document loaded with warnings: " + warningCount);

// Optional: iterate and print each warning for deeper insight
document.getWarningInfo().forEach(w -> System.out.println("- " + w.getDescription()));
```

Output tipikal mungkin terlihat seperti:

```
Document loaded with warnings: 3
- Warning: Missing end tag for <w:p>.
- Warning: Invalid hyperlink target.
- Warning: Unsupported bitmap format.
```

Melihat daftar tersebut memungkinkan Anda memutuskan apakah perlu memperbaiki sesuatu secara manual nanti atau apakah dokumen yang dipulihkan sudah cukup baik untuk kasus penggunaan Anda.

---

## Contoh Lengkap yang Berfungsi – Dari Awal hingga Selesai

Berikut adalah kelas Java mandiri yang dapat Anda masukkan ke proyek apa pun. Kelas ini mendemonstrasikan **how to recover docx**, **set recovery mode**, **use recovery mode**, dan **display load warnings**—semua dalam satu langkah.

```java
import com.aspose.words.*;

public class DocxRecoveryDemo {

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with the desired recovery strategy
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
            // Uncomment the line below to suppress warnings
            // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_SILENTLY);

            // 2️⃣ Load the potentially corrupted DOCX file
            String filePath = "C:/Docs/corrupted.docx";
            Document doc = new Document(filePath, loadOptions);

            // 3️⃣ Show how many warnings were generated
            int warnings = doc.getWarningInfo().size();
            System.out.println("Document loaded with warnings: " + warnings);

            // Optional: print each warning for debugging
            for (WarningInfo wi : doc.getWarningInfo()) {
                System.out.println("- " + wi.getDescription());
            }

            // 4️⃣ Save the recovered document (optional)
            String outputPath = "C:/Docs/recovered.docx";
            doc.save(outputPath);
            System.out.println("Recovered document saved to: " + outputPath);

        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected result:** Program mencetak jumlah peringatan, menampilkan masing‑masing, dan menulis `recovered.docx` yang bersih ke disk. Bahkan jika file asli setengah rusak, output akan berisi semua konten yang dapat dipulihkan.

---

## Pertanyaan Umum & Kasus Pinggir

### Bagaimana jika saya perlu memulihkan DOCX dari stream alih‑alih path file?
Cukup lewati `InputStream` ke konstruktor `Document` bersama dengan `LoadOptions` yang sama. API berfungsi secara identik.

```java
InputStream is = new FileInputStream("corrupted.docx");
Document doc = new Document(is, loadOptions);
```

### Bisakah saya mengubah mode pemulihan setelah dokumen sudah dimuat?
Tidak. Mode hanya dibaca selama fase pemuatan. Jika Anda memerlukan strategi berbeda, muat ulang file dengan instance `LoadOptions` yang baru.

### Bagaimana **recover corrupted docx** berbeda dari sekadar membukanya di Microsoft Word?
Word mencoba auto‑repair tetapi sering menyembunyikan detailnya. Aspose.Words memberi Anda daftar programatik setiap masalah melalui **display load warnings**, yang sangat berharga untuk pipeline otomatis.

### Apakah ada penalti kinerja saat menggunakan `RECOVER_WITH_WARNINGS`?
Sedikit—mengumpulkan peringatan menambah overhead, tetapi tidak signifikan untuk kebanyakan file (<5 MB). Untuk pemrosesan massal di mana kecepatan penting, beralihlah ke `RECOVER_SILENTLY`.

---

## Pro Tips & Pitfalls

* **Pro tip:** Selalu log peringatan ke file saat memproses batch. Dengan begitu Anda dapat mengaudit file bermasalah nanti tanpa memenuhi konsol.
* **Watch out for:** File DOCX sangat besar (>100 MB) dapat menyebabkan `OutOfMemoryError` jika Anda juga mengaktifkan `RECOVER_WITH_WARNINGS`. Pertimbangkan meningkatkan heap JVM atau gunakan `RECOVER_SILENTLY` untuk kasus tersebut.
* **Tip:** Setelah pemulihan, jalankan pemeriksaan cepat—misalnya, `doc.getSections().size()`—untuk memastikan struktur dokumen tetap utuh sebelum Anda menyerahkannya ke layanan downstream.

---

## Kesimpulan

Kami baru saja membahas **how to recover docx** dengan mengonfigurasi **load options**, **set recovery mode**, **use recovery mode**, dan **display load warnings** untuk setiap DOCX yang rusak yang Anda temui. Contoh lengkap di atas siap untuk copy‑paste, dijalankan, dan disesuaikan dengan alur kerja Anda.

Langkah selanjutnya? Coba ganti `RECOVER_WITH_WARNINGS` dengan `RECOVER_SILENTLY` dalam pekerjaan volume tinggi, atau integrasikan daftar peringatan ke sistem pemantauan Anda. Anda juga dapat menjelajahi fitur Aspose.Words lain seperti **document protection** atau **format conversion**—semua menghormati pengaturan pemulihan yang sama.

Masih ada pertanyaan tentang memulihkan dokumen, menangani format Office lain, atau menyesuaikan pengaturan Aspose.Words? Tinggalkan komentar, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}