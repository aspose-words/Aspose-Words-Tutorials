---
category: general
date: 2026-05-26
description: Buka dokumen Word yang rusak di Java dengan Aspose.Words. Pelajari cara
  mengatur mode pemulihan dan memulihkan file Word yang rusak secara andal.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: id
og_description: Buka dokumen Word yang rusak di Java menggunakan Aspose.Words. Panduan
  ini menunjukkan cara mengatur mode pemulihan dan memulihkan file Word yang rusak
  secara efisien.
og_title: Buka Dokumen Word yang Rusak – Atur Mode Pemulihan di Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Buka Dokumen Word yang Rusak – Atur Mode Pemulihan di Java
url: /id/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buka Dokumen Word Rusak – Atur Mode Pemulihan di Java

Pernah mencoba membuka dokumen Word yang rusak dan melihat program terhenti karena pengecualian? Anda tidak sendirian—file .docx yang rusak memang menyebalkan. Kabar baiknya, Aspose.Words untuk Java memberi Anda kontrol yang detail sehingga Anda dapat **membuka dokumen word yang rusak** tanpa aplikasi crash, bahkan dapat memilih apakah ingin menampilkan peringatan, pemulihan diam-diam, atau penolakan keras.

Dalam tutorial ini kita akan melewati seluruh proses: mulai dari membuat `LoadOptions` yang tepat, memilih nilai **set recovery mode** yang sesuai, dan akhirnya memastikan dokumen memang berhasil dimuat. Pada akhir tutorial Anda akan tahu **cara memulihkan file word yang rusak** secara programatik, tanpa perlu menyalin‑tempel manual.

> **Apa yang Anda perlukan**  
> * Java 8 atau lebih baru (API juga bekerja dengan Java 11)  
> * Aspose.Words untuk Java 23.9 (atau versi terbaru)  
> * Contoh file .docx yang rusak—cukup ganti nama file yang valid untuk mensimulasikan kerusakan jika Anda belum memiliki file tersebut  

Mari kita mulai.

## Buka Dokumen Word Rusak – Ikhtisar Langkah‑per‑Langkah

Berikut alur tingkat tinggi yang akan kita implementasikan:

1. **Buat `LoadOptions`** – objek ini memberi tahu Aspose.Words bagaimana bersikap ketika menemukan masalah.  
2. **Atur mode pemulihan** – pilih `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS`, atau `REJECT_CORRUPTED`.  
3. **Muat dokumen** menggunakan opsi yang telah dikonfigurasi.  
4. **Verifikasi** bahwa pemuatan berhasil (misalnya, cetak jumlah halaman).  

Setiap langkah dijelaskan secara detail, dengan potongan kode yang dapat Anda salin‑tempel langsung ke IDE.

## Atur Mode Pemulihan untuk Berbagai Skenario

Aspose.Words mendefinisikan tiga strategi pemulihan di dalam `LoadOptions.RecoveryMode`:

| Mode | Perilaku | Kapan digunakan |
|------|----------|-----------------|
| `RECOVER_WITH_WARNINGS` | Mencoba memuat dokumen, tetapi menampilkan setiap masalah sebagai peringatan di konsol. | Anda ingin melihat *apa* yang salah tanpa menghentikan proses. |
| `RECOVER_WITHOUT_WARNINGS` | Diam‑diam memperbaiki apa yang bisa dan menekan peringatan. | Lingkungan produksi di mana log harus tetap bersih. |
| `REJECT_CORRUPTED` | Melempar pengecualian begitu kerusakan terdeteksi. | Pipeline validasi ketat yang harus gagal cepat. |

Memilih mode yang tepat adalah inti dari **set recovery mode** secara benar. Dalam kebanyakan sesi debugging, `RECOVER_WITH_WARNINGS` adalah pilihan yang ideal karena memberi tahu Anda bagian mana yang diperbaiki.

## Cara Memulihkan File Word Rusak Menggunakan Aspose.Words

Berikut adalah **program Java lengkap yang dapat dijalankan** yang mendemonstrasikan seluruh proses. Silakan letakkan ke dalam file `RecoveryModeDemo.java`, sesuaikan path, dan jalankan.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Mengapa setiap baris penting

* **`LoadOptions loadOptions = new LoadOptions();`** – tanpa objek ini Aspose.Words menggunakan pemulihan default, yang *menolak* file yang rusak. Membuatnya memberi Anda titik masuk untuk mengubah perilaku tersebut.  
* **`setRecoveryMode(...)`** – ini adalah pemanggilan **set recovery mode** yang menentukan apakah peringatan muncul, disembunyikan, atau menyebabkan pengecualian.  
* **`new Document(path, loadOptions);`** – konstruktor menerima `LoadOptions` yang baru saja kita konfigurasikan, sehingga perpustakaan tahu cara memperlakukan file rusak sejak awal.  
* **`doc.getPageCount()`** – pemeriksaan cepat. Jika dokumen dimuat dan mengembalikan jumlah halaman, Anda telah berhasil **cara memulihkan file word yang rusak**.  
* **`doc.save(...)`** – opsional namun berguna; Anda dapat menulis versi yang telah diperbaiki kembali ke disk untuk penggunaan selanjutnya.

## Menangani Kasus Edge yang Umum

### 1. File Tidak Ditemukan

Jika path salah, `Document` akan melempar `FileNotFoundException`. Bungkus pemuatan dalam blok try‑catch dan log pesan yang ramah:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Kerusakan yang Tidak Dapat Dipulihkan

Bahkan dengan `RECOVER_WITH_WARNINGS`, beberapa struktur berada di luar jangkauan perbaikan. Dalam kasus tersebut Aspose.Words tetap memuat apa yang dapat, tetapi Anda akan melihat peringatan seperti “Cannot read paragraph properties”. Perhatikan output konsol; peringatan tersebut sering menunjukkan bagian yang hilang yang mungkin perlu Anda susun kembali secara manual.

### 3. File Besar dan Kinerja

Pemulihan menambah sedikit overhead karena perpustakaan mem-parsing file dua kali—sekali untuk mendeteksi masalah, sekali lagi untuk membangun kembali. Untuk dokumen berukuran multi‑gigabyte, pertimbangkan streaming file atau meningkatkan heap JVM (`-Xmx2g`) agar terhindar dari `OutOfMemoryError`.

## Tips Pro – Membuat Pemulihan Lebih Tangguh

* **Log peringatan ke file** – alihkan `System.err` ke logger sehingga Anda memiliki jejak audit tentang apa yang telah diperbaiki.  
* **Validasi setelah pemulihan** – jalankan `doc.updatePageLayout();` lalu periksa kembali jumlah halaman; terkadang tata letak berubah setelah memperbaiki bagian yang rusak.  
* **Otomatisasi pemulihan batch** – bungkus demo dalam loop yang memproses folder berisi file rusak, menggunakan `LoadOptions` yang sama setiap kali.

## Kesimpulan

Anda kini tahu persis **cara memulihkan file word yang rusak** menggunakan Aspose.Words untuk Java. Dengan membuat instance `LoadOptions`, **set recovery mode** ke strategi yang sesuai dengan skenario Anda, dan memuat dokumen dengan opsi tersebut, Anda dapat dengan aman **membuka dokumen word yang rusak** tanpa membuat aplikasi Anda crash. Kode contoh di atas adalah solusi lengkap yang siap dijalankan, mencetak jumlah halaman, dan bahkan menyimpan salinan yang telah dibersihkan.

Apa selanjutnya? Cobalah mengganti mode pemulihan menjadi `RECOVER_WITHOUT_WARNINGS` dan bandingkan output konsol, atau bereksperimen dengan memuat dokumen terenkripsi (Anda perlu menyediakan kata sandi melalui

## Tutorial Terkait

- [Aspose.Words Java&#58; Panduan Komprehensif untuk Pemrosesan Dokumen Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Cara Mengonversi Word ke PDF Menggunakan Aspose.Words untuk Java](/words/english/java/document-converting/using-document-converting/)
- [Cara Membandingkan Dua File Word dengan Aspose.Words untuk Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}