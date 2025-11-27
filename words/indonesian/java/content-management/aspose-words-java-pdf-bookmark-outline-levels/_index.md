---
date: '2025-11-27'
description: Pelajari cara membuat bookmark, menghasilkan PDF dengan bookmark, dan
  mengonversi Word ke PDF dalam Java menggunakan Aspose.Words. Panduan ini mencakup
  bookmark bersarang dan tingkat outline.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: id
title: Cara Membuat Bookmark dan Menetapkan Tingkat Outline dalam PDF Menggunakan
  Aspose.Words Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Membuat Bookmark dan Menetapkan Tingkat Outline dalam PDF Menggunakan Aspose.Words Java

## Pendahuluan
Jika Anda pernah mengalami kesulitan **cara membuat bookmark** yang tetap teratur saat mengonversi dokumen Word ke PDF, Anda berada di tempat yang tepat. Dalam tutorial ini kami akan membahas proses lengkap menghasilkan PDF dengan bookmark, menumpuknya, dan menetapkan tingkat outline sehingga PDF akhir mudah dinavigasi. Pada akhir tutorial Anda akan dapat **mengonversi Word ke PDF dengan Java**‑style dengan hierarki bookmark yang bersih dan berfungsi di semua penampil PDF.

### Apa yang Akan Anda Pelajari
- Siapkan Aspose.Words untuk Java di lingkungan pengembangan Anda.  
- **Cara membuat bookmark** secara programatis dan menumpukkannya.  
- Konfigurasikan tingkat outline bookmark untuk menghasilkan PDF dengan bookmark yang mencerminkan struktur dokumen.  
- Simpan file Word sebagai PDF sambil mempertahankan hierarki bookmark.

## Jawaban Cepat
- **Apa kelas utama untuk membangun dokumen?** `DocumentBuilder`.  
- **Opsi mana yang mengontrol hierarki bookmark?** `BookmarksOutlineLevelCollection` di dalam `PdfSaveOptions`.  
- **Bisakah saya menggunakan Maven atau Gradle?** Ya – keduanya ditampilkan di bawah.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi permanen diperlukan untuk produksi.  
- **Apakah pendekatan ini cocok untuk dokumen besar?** Ya, tetapi pertimbangkan teknik optimasi memori (mis., menghapus sumber daya yang tidak terpakai).

### Prasyarat
Sebelum Anda mulai, pastikan Anda memiliki:

- **Perpustakaan dan Dependensi** – Aspose.Words untuk Java (25.3 atau lebih baru).  
- **Lingkungan** – JDK 8 atau lebih baru, serta IDE seperti IntelliJ IDEA atau Eclipse.  
- **Pengetahuan Dasar** – Dasar-dasar pemrograman Java dan familiaritas dengan Maven atau Gradle.

## Menyiapkan Aspose.Words
Untuk memulai, sertakan dependensi yang diperlukan dalam proyek Anda. Berikut cara menambahkan Aspose.Words menggunakan Maven atau Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Akuisisi Lisensi
Aspose.Words adalah perpustakaan komersial, tetapi Anda dapat memulai dengan versi percobaan gratis:

1. **Versi Percobaan Gratis** – Unduh dari [halaman rilis Aspose](https://releases.aspose.com/words/java/).  
2. **Lisensi Sementara** – Ajukan di [halaman lisensi sementara](https://purchase.aspose.com/temporary-license/) jika Anda memerlukan kunci jangka pendek.  
3. **Lisensi Penuh** – Beli melalui [portal pembelian Aspose](https://purchase.aspose.com/buy) untuk penggunaan produksi.

Setelah memperoleh file lisensi, muatlah pada saat aplikasi dimulai untuk membuka semua fitur.

## Cara Membuat Bookmark dalam PDF dengan Aspose.Words Java
Di bawah ini kami membagi implementasi menjadi langkah-langkah yang jelas dan bernomor. Setiap langkah mencakup penjelasan singkat diikuti oleh blok kode asli (tidak diubah).

### Langkah 1: Inisialisasi Document dan DocumentBuilder
Kami memulai dengan instance `Document` baru dan `DocumentBuilder` yang memungkinkan kami menyisipkan konten dan bookmark.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Langkah 2: Sisipkan Bookmark Pertama (Induk)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Langkah 3: Tempatkan Bookmark Anak di Dalam Induk
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Langkah 4: Tutup Bookmark Induk
```java
builder.endBookmark("Bookmark 1");
```

### Langkah 5: Tambahkan Bookmark Ketiga yang Independen
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Mengonfigurasi Tingkat Outline Bookmark
Setelah bookmark ditempatkan, kami memberi tahu Aspose.Words bagaimana bookmark tersebut harus muncul di outline PDF (panel navigasi sebelah kiri).

### Langkah 6: Siapkan PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Langkah 7: Tetapkan Tingkat Hierarki
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Langkah 8: Simpan Document sebagai PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Mengapa Menggunakan Pendekatan Ini untuk Menghasilkan PDF dengan Bookmark?
- **Navigasi Profesional** – Pembaca dapat langsung melompat ke bagian, meningkatkan kegunaan untuk laporan besar atau kontrak hukum.  
- **Kontrol Penuh** – Anda yang menentukan hierarki, bukan penampil PDF.  
- **Lintas‑Platform** – Berfungsi sama di Windows, Linux, dan macOS karena murni Java.  

## Masalah Umum dan Solusinya
| Gejala | Penyebab Kemungkinan | Solusi |
|---|---|---|
| Bookmark tidak muncul di PDF | `startBookmark` tanpa `endBookmark` yang cocok | Pastikan setiap `startBookmark` memiliki `endBookmark` yang sesuai. |
| Hierarki tidak tepat | Tingkat outline ditetapkan tidak berurutan | Pastikan bookmark induk memiliki nomor level lebih rendah daripada anaknya. |
| Lisensi tidak diterapkan | File lisensi tidak dimuat sebelum pembuatan dokumen | Muat lisensi di awal aplikasi Anda (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Aplikasi Praktis
1. **Dokumen Hukum** – Navigasi cepat ke klausul, lampiran, dan tambahan.  
2. **Laporan Keuangan** – Lompat antar bagian seperti Laporan Laba Rugi, Neraca, dan Catatan.  
3. **Materi E‑Learning** – Sediakan daftar isi yang mencerminkan outline PDF.  

## Pertimbangan Kinerja
- **Manajemen Memori** – Untuk file Word yang sangat besar, pertimbangkan memanggil `doc.cleanup()` sebelum menyimpan.  
- **Optimasi Sumber Daya** – Hapus gambar atau gaya yang tidak terpakai untuk menjaga ukuran PDF tetap kecil.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menginstal Aspose.Words untuk Java?**  
A: Tambahkan dependensi Maven atau Gradle yang ditunjukkan sebelumnya, kemudian letakkan file lisensi Anda di classpath dan muat pada saat runtime.

**Q: Bisakah saya membuat bookmark tanpa mengatur tingkat outline?**  
A: Ya, tetapi penampil PDF akan menampilkannya sebagai daftar datar, yang dapat sulit dinavigasi pada dokumen yang kompleks.

**Q: Apakah ada batas seberapa dalam bookmark dapat ditumpuk?**  
A: Secara teknis tidak, tetapi kebanyakan penampil PDF mendukung hingga 9 tingkat dengan nyaman. Jaga hierarki tetap logis bagi pembaca.

**Q: Bagaimana Aspose menangani file Word yang sangat besar?**  
A: Perpustakaan ini melakukan streaming konten dan menyediakan metode seperti `Document.optimizeResources()` untuk mengurangi jejak memori.

**Q: Bisakah saya mengedit bookmark setelah PDF dihasilkan?**  
A: Tentu – Anda dapat menggunakan Aspose.PDF untuk Java untuk menambah, menghapus, atau mengganti nama bookmark dalam PDF yang sudah ada.

## Sumber Daya
- [Dokumentasi Aspose.Words](https://reference.aspose.com/words/java/)  
- [Unduh Rilis Terbaru](https://releases.aspose.com/words/java/)  
- [Beli Lisensi](https://purchase.aspose.com/buy)  
- [Versi Percobaan Gratis](https://releases.aspose.com/words/java/)  
- [Aplikasi Lisensi Sementara](https://purchase.aspose.com/temporary-license/)  
- [Forum Dukungan Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Terakhir Diperbarui:** 2025-11-27  
**Diuji Dengan:** Aspose.Words 25.3 untuk Java  
**Penulis:** Aspose