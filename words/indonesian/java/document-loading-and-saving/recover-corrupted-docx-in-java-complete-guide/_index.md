---
category: general
date: 2026-06-20
description: Pulihkan file docx yang rusak di Java dengan Aspose.Words. Pelajari cara
  mengatur mode pemulihan dan memuat dokumen dengan pemulihan untuk membuka secara
  mulus.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: id
og_description: Pulihkan file docx yang rusak di Java menggunakan Aspose.Words. Tutorial
  ini menunjukkan cara mengatur mode pemulihan, memuat dokumen dengan pemulihan, dan
  membuka docx yang rusak dengan aman.
og_title: Pulihkan docx yang rusak di Java – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Pulihkan docx yang rusak di Java – Panduan Lengkap
url: /id/java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Memulihkan docx yang rusak di Java – Panduan Lengkap

Pernah mencoba **memulihkan docx yang rusak** dan menemui jalan buntu? Pada tutorial ini kami akan menunjukkan cara **memulihkan docx yang rusak** menggunakan Aspose.Words for Java dengan **mengatur mode pemulihan** dan **memuat dokumen dengan pemulihan** sehingga file terbuka seperti dokumen Word yang sehat.  

Jika Anda pernah bertanya-tanya mengapa beberapa file DOCX menolak untuk dibuka di Word, jawabannya seringkali adalah kerusakan tersembunyi yang tidak dapat ditangani oleh pemuat standar. Kami akan memandu langkah‑langkah tepat yang Anda perlukan, mulai dari menambahkan pustaka hingga memverifikasi jumlah halaman, dan Anda akan mendapatkan dokumen bersih yang dapat digunakan—tidak ada lagi pop‑up “file rusak”.

## Apa yang Akan Anda Pelajari

- Cara **mengatur mode pemulihan** untuk memberi tahu Aspose.Words seberapa agresif ia harus memperbaiki file yang rusak.  
- Kode tepat yang diperlukan untuk **memuat dokumen dengan pemulihan** dan menangani kerusakan parah secara elegan.  
- Tips untuk skenario **membuka Word dengan pemulihan** dan apa yang harus dilakukan ketika file tidak dapat diselamatkan.  
- Contoh lengkap yang dapat dijalankan dan Anda cukup salin‑tempel ke IDE Anda.  

### Prasyarat

- Java 8 atau yang lebih baru terpasang.  
- Maven atau Gradle untuk mengelola dependensi (kami akan membahas Maven).  
- File `.docx` yang rusak yang ingin Anda uji (file apa pun yang menolak dibuka di Microsoft Word sudah cukup).  

Tidak diperlukan pengetahuan mendalam tentang API Aspose—hanya keterampilan Java dasar. Mari mulai.

![contoh pemulihan docx yang rusak](recover_corrupted_docx.png "tangkapan layar pemulihan docx yang rusak")

## Langkah 1: Tambahkan Aspose.Words for Java ke Proyek Anda

Hal pertama yang perlu dilakukan—proyek Anda memerlukan JAR Aspose.Words. Jika Anda menggunakan Maven, tambahkan ini ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Pengguna Gradle dapat menambahkan:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**Tips pro:** Selalu periksa situs web Aspose untuk versi terbaru; rilis yang lebih baru biasanya menyertakan algoritma pemulihan yang lebih baik.

## Langkah 2: Atur Mode Pemulihan – Kunci untuk Memperbaiki File yang Rusak

Setelah pustaka tersedia, Anda harus memberi tahu cara ia berperilaku ketika menemukan korupsi. Di sinilah `setRecoveryMode` berperan. Enum `RecoveryMode` menawarkan dua pilihan:

| Mode | Deskripsi |
|------|-----------|
| `RECOVER` | Mencoba memperbaiki sebanyak mungkin, menghasilkan dokumen yang sebagian diperbaiki. |
| `REJECT` | Melemparkan pengecualian pada masalah serius apa pun, berguna ketika Anda menginginkan dokumen yang bersih. |

Berikut kode yang **mengatur mode pemulihan** ke opsi yang lunak `RECOVER`:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Mengapa ini penting:** Tanpa mengatur mode pemulihan, Aspose.Words secara default menggunakan `REJECT`, yang berarti program Anda akan melempar pengecualian begitu menemukan bagian yang rusak. Dengan secara eksplisit **mengatur mode pemulihan**, Anda memberi pustaka izin untuk menambal node XML yang hilang, memulihkan hubungan yang hilang, dan secara umum “membersihkan” file.

## Langkah 3: Muat Dokumen dengan Pemulihan – Menggabungkan Semua

Potongan kode di atas sudah memperlihatkan **memuat dokumen dengan pemulihan**, tetapi mari kita uraikan untuk kejelasan:

1. **Instansiasi `LoadOptions`** – objek ini menyimpan semua flag yang ingin Anda terapkan pada pemuat.  
2. **Panggil `setRecoveryMode`** – kami memilih `RECOVER` karena ingin peluang terbaik membuka file.  
3. **Berikan opsi tersebut ke konstruktor `Document`** – Aspose.Words membaca file, menerapkan logika pemulihan, dan mengembalikan objek `Document` yang dapat digunakan.

Jika Anda lebih suka pendekatan defensif, Anda dapat membungkus proses pemuatan dalam blok try‑catch dan beralih ke `REJECT` bila hasil `RECOVER` tidak memuaskan:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Langkah 4: Verifikasi Dokumen yang Telah Diperbaiki

Setelah dokumen dimuat, Anda perlu memastikan isinya masih masuk akal. Pemeriksaan umum meliputi:

- **Jumlah halaman** – pemeriksaan cepat (`doc.getPageCount()`).  
- **Ekstraksi teks** – `doc.getText()` untuk melihat apakah bagian utama masih utuh.  
- **Menyimpan salinan** – tulis versi yang dipulihkan ke disk untuk inspeksi selanjutnya.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

Jika pratinjau terlihat berantakan, file mungkin mengalami kerusakan yang tidak dapat dipulihkan. Dalam kasus tersebut, pertimbangkan menggunakan mode `REJECT` untuk menghindari penyebaran data yang rusak.

## Langkah 5: Opsional – Buka Word dengan Pemulihan (Pendekatan Manual)

Kadang‑kadang Anda tidak ingin menulis kode; Anda cukup perlu **membuka Word dengan pemulihan** secara manual. Microsoft Word sendiri menyediakan fitur “Open and Repair”:

1. Buka Word → *File* → *Open*.  
2. Pilih file `.docx` yang rusak.  
3. Klik panah dropdown di samping *Open* dan pilih **Open and Repair**.

Meskipun cara ini berhasil untuk banyak pengguna, ia tidak memiliki kemampuan otomatisasi dan pemrosesan batch seperti pendekatan Java yang baru saja kami bahas. Gunakan metode manual untuk perbaikan sesekali; andalkan Aspose.Words ketika Anda perlu memproses puluhan atau ratusan file secara programatik.

## Kasus Khusus & Jebakan Umum

- **Kerusakan parah** – Jika file kehilangan `[Content_Types].xml` inti, bahkan `RECOVER` tidak dapat membantu. Harapkan pengecualian dan beri tahu pengguna.  
- **File yang diproteksi password** – Mode pemulihan tidak melewati enkripsi. Anda harus menyediakan password melalui `LoadOptions.setPassword("yourPwd")` sebelum mencoba pemulihan.  
- **Dokumen besar** – Memuat DOCX berukuran besar dengan `RECOVER` dapat mengonsumsi lebih banyak memori. Pertimbangkan meningkatkan heap JVM (`-Xmx2g`) jika Anda menemui `OutOfMemoryError`.  

## Contoh Program Lengkap yang Berfungsi

Berikut adalah program lengkap yang dapat Anda kompilasi dan jalankan langsung. Ganti jalur file dengan lokasi DOCX yang rusak milik Anda.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Output yang diharapkan (ketika pemulihan berhasil):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

Jika dokumen berada di luar batas perbaikan, Anda akan melihat pesan error yang jelas alih‑alih jejak tumpukan, berkat blok `try‑catch` di sekitarnya.

## Kesimpulan

Anda kini tahu cara **memulihkan docx yang rusak** di Java menggunakan Aspose.Words. Dengan **mengatur mode pemulihan** ke `RECOVER` dan kemudian **memuat dokumen dengan pemulihan**, Anda dapat secara otomatis memperbaiki banyak masalah umum yang sebaliknya akan mencegah file Word terbuka. Baik Anda perlu **membuka Word dengan pemulihan** secara programatik atau hanya ingin **membuka docx yang rusak** secara manual, teknik yang dibahas di sini memberikan fondasi yang kuat.

**Langkah selanjutnya:**  

- Bereksperimen  

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Pemulihan docx yang rusak – Panduan Lengkap untuk Memperbaiki dan Memproses Dokumen](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Cara Memuat HTML dan Menyimpan sebagai DOCX menggunakan Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Cara Menggabungkan Beberapa File DOCX Menggunakan Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}