---
category: general
date: 2026-05-04
description: Pelajari cara loadoptions Aspose.Words dapat memulihkan file Word yang
  rusak, menggunakan mode pemulihan, memperbaiki docx yang rusak, dan mendapatkan
  jumlah halaman Word dalam satu tutorial.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: id
og_description: Kuasi loadoptions Aspose.Words untuk memulihkan file Word yang rusak,
  pilih mode pemulihan yang tepat, perbaiki docx yang rusak, dan dapatkan jumlah halaman.
og_title: aspose words loadoptions – Memulihkan Dokumen Word yang Rusak
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Pulihkan Dokumen Word Rusak di Java
url: /id/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Memulihkan Dokumen Word Rusak di Java

Pernah mencoba membuka file Word yang tiba‑tiba menolak untuk dimuat? Itu perasaan seperti pukulan perut ketika seorang klien mengirimkan **corrupted docx** dan Anda tidak tahu apakah dapat diselamatkan. Kabar baik? Dengan **aspose words loadoptions** Anda dapat memberi tahu Aspose.Words secara tepat bagaimana berperilaku ketika dokumen rusak, apakah melemparkan exception atau mencoba perbaikan diam.  

Dalam panduan ini kami akan menjelaskan cara menggunakan `LoadOptions` untuk **recover corrupted Word** file, mengeksplorasi pengaturan **use recovery mode**, melihat cara **repair corrupted docx** secara otomatis, dan mengakhiri dengan **getting the word page count** dari dokumen yang dipulihkan. Tanpa alat eksternal, hanya Java murni dan Aspose.Words.

## Apa yang Anda Butuhkan

- **Aspose.Words for Java** (v24.12 atau lebih baru) – versi terbaru menambahkan beberapa pemeriksaan keamanan tambahan.
- Sebuah **Java IDE** (IntelliJ IDEA, Eclipse, atau bahkan editor teks sederhana dengan `javac`).
- **corrupted DOCX** yang ingin Anda uji (kami akan menyebutnya `Corrupted.docx`).
- **pemahaman dasar** tentang sintaks Java – tidak ada yang rumit, hanya `public static void main`.

> **Pro tip:** simpan cadangan file asli; upaya pemulihan terkadang dapat menulis ulang bagian-bagian binary.

## Langkah 1: Buat LoadOptions – Inti Pemulihan

Hal pertama yang Anda lakukan adalah menginstansiasi objek `LoadOptions`. Objek ini adalah panel kontrol Anda; ia memberi tahu Aspose.Words bagaimana memperlakukan file ketika menemukan masalah.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Mengapa langkah ini penting? Karena tanpa `LoadOptions` perpustakaan akan kembali ke perilaku defaultnya, yang mungkin secara diam‑diam mengabaikan kesalahan atau, lebih buruk lagi, mengembalikan dokumen yang dimuat sebagian yang dapat menyebabkan crash nanti. Dengan mengonfigurasi opsi secara eksplisit Anda mendapatkan penanganan error yang deterministik.

## Langkah 2: Pilih Mode Pemulihan yang Tepat

Aspose.Words menawarkan dua strategi pemulihan:

| Mode | Behaviour |
|------|-----------|
| `RecoveryMode.STRICT` | Melemparkan exception jika dokumen tidak dapat diperbaiki sepenuhnya. |
| `RecoveryMode.REPAIR` | Mencoba memperbaiki file dan melanjutkan pemuatan, meskipun sebagian konten hilang. |

Untuk skenario **recover corrupted word** di mana Anda perlu mengetahui apakah perbaikan berhasil, `STRICT` adalah pilihan paling aman. Jika Anda lebih suka pendekatan best‑effort, beralihlah ke `REPAIR`.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Mengapa memilih satu daripada yang lain?**  
> *STRICT* memberi Anda sinyal yang jelas—apakah dokumen dapat digunakan atau Anda perlu memberi tahu pengguna. *REPAIR* berguna dalam pekerjaan batch di mana Anda dapat kehilangan satu atau dua gambar yang tidak penting.

## Langkah 3: Muat Dokumen yang Mungkin Rusak

Sekarang Anda benar‑benar membuka file, dengan melewatkan `LoadOptions` yang baru saja Anda konfigurasikan. Jika file berada di luar perbaikan dan Anda memilih `STRICT`, sebuah exception akan muncul; jika tidak, Anda akan mendapatkan objek `Document` yang siap untuk inspeksi.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Perhatikan bahwa path dapat berupa absolut atau relatif terhadap root proyek Anda. Kelas `Document` mengabstraksi seluruh file Word, memudahkan untuk menanyakan hal‑hal seperti jumlah halaman, bagian, atau bahkan mengedit konten setelah pemulihan.

## Langkah 4: Verifikasi Pemuatan – Dapatkan Jumlah Halaman Word

Pemeriksaan cepat adalah menanyakan kepada Aspose.Words berapa banyak halaman yang dianggap dokumen miliki. Jika hitungannya tidak nol, Anda kemungkinan besar telah berhasil **repair corrupted docx**.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Output tipikal:

```
Loaded successfully, page count = 12
```

Jika dokumen benar‑benar tidak dapat dibaca dengan `STRICT`, kode akan melemparkan exception sebelum mencapai baris ini. Hal itu membuat pemeriksaan `page count` menjadi verifikasi sekaligus informasi berguna untuk logika selanjutnya (misalnya, pagination dalam penampil web).

## Contoh Lengkap yang Berfungsi

Berikut adalah program Java lengkap yang siap dijalankan yang menggabungkan semua bagian. Salin‑tempel ke dalam file bernama `RecoveryModeDemo.java`, sesuaikan path, dan jalankan `javac RecoveryModeDemo.java && java RecoveryModeDemo`.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Hasil yang Diharapkan

- **Jika file dapat dipulihkan:** konsol mencetak jumlah halaman, dan Anda dapat melanjutkan pemrosesan objek `Document` dengan aman.
- **Jika file berada di luar perbaikan (mode STRICT):** sebuah `com.aspose.words.UnsupportedFileFormatException` (atau serupa) dilemparkan, yang dapat Anda tangkap dan tangani dengan elegan.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya perlu mencatat detail error yang tepat?

Bungkus kode pemuatan dalam blok `try‑catch` dan catat `e.getMessage()`. Ini memberi Anda alasan yang jelas—apakah itu bagian yang hilang, hubungan yang rusak, atau aliran yang korup.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Bisakah saya memulihkan hanya bagian tertentu (seperti teks tetapi bukan gambar)?

Aspose.Words tidak menyediakan toggle pemulihan granular, tetapi setelah memuat Anda dapat mengiterasi elemen `NodeType` dan membuang yang berjenis `NodeType.SHAPE` (gambar) jika menyebabkan masalah pada proses selanjutnya.

### Apakah ini bekerja dengan file `.doc` lama?

Ya. `LoadOptions` berfungsi pada semua format Word (`.doc`, `.docx`, `.dot`, `.dotx`). Logika pemulihan yang sama berlaku.

### Bagaimana perpustakaan menangani file yang dilindungi password?

Jika file terenkripsi, `LoadOptions` tidak akan melewati password. Anda harus menyediakan password melalui `loadOptions.setPassword("yourPassword")`. Mode pemulihan hanya aktif setelah dekripsi berhasil.

## Tips untuk Penggunaan Produksi

- **Catat mode pemulihan yang dipilih** – Ini membantu saat Anda kemudian meninjau mengapa file tertentu berhasil atau gagal.
- **Jangan pernah menimpa file asli** – Simpan dokumen yang dipulihkan ke lokasi baru (`document.save("Recovered.docx")`).
- **Gabungkan dengan validasi** – Setelah pemulihan, jalankan pemeriksaan ejaan cepat atau validasi struktural untuk memastikan dokumen memenuhi aturan bisnis Anda.
- **Pemrosesan batch** – Saat menangani banyak file, lakukan loop, tangkap exception secara individual, dan simpan laporan ringkas tentang keberhasilan vs. kegagalan.

## Kesimpulan

Anda kini memiliki resep lengkap yang solid untuk menggunakan **aspose words loadoptions** untuk **recover corrupted Word** dokumen, memutuskan apakah akan **use recovery mode** secara ketat atau permisif, secara opsional **repair corrupted docx**, dan akhirnya **get the word page count** dari file yang dipulihkan. Pendekatan ini deterministik, mudah diintegrasikan ke dalam pipeline Java yang ada, dan memberi Anda kontrol penuh atas seberapa agresif perpustakaan harus beroperasi ketika menghadapi binary yang rusak.

Siap melangkah lebih jauh? Coba ganti `RecoveryMode.STRICT` dengan `REPAIR` dalam pekerjaan batch, atau kembangkan contoh untuk secara otomatis menyimpan file yang diperbaiki ke folder yang aman. Kemungkinannya tak terbatas, dan dengan Aspose.Words Anda siap menangani bahkan gangguan file Word yang paling sulit.

Selamat coding, semoga dokumen Anda selalu dapat dimuat dengan bersih!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}