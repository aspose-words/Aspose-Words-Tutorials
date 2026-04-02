---
date: '2026-04-02'
description: Pelajari cara membuat bookmark bersarang, mengatur level outline bookmark,
  dan menyimpan dokumen Word sebagai PDF dengan Aspose.Words untuk Java.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Buat Bookmark Bersarang dan Atur Tingkat Outline dalam PDF Menggunakan Aspose.Words
  untuk Java
url: /id/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat Bookmark Bersarang dan Atur Tingkat Outline dalam PDF Menggunakan Aspose.Words untuk Java

## Pendahuluan
Kesulitan mengelola bookmark saat mengonversi dokumen Word ke PDF? **Tutorial ini menunjukkan cara membuat bookmark bersarang**, mengonfigurasi tingkat outline mereka, dan menyimpan hasilnya sebagai PDF yang bersih dan dapat dinavigasi menggunakan Aspose.Words untuk Java. Pada akhir panduan ini Anda akan memiliki PDF berpenampilan profesional di mana pembaca dapat langsung melompat ke bagian yang mereka butuhkan.

**Apa yang Akan Anda Pelajari**
- Menyiapkan Aspose.Words untuk Java dalam proyek Anda  
- **Membuat bookmark bersarang** dalam dokumen Word  
- **Cara mengatur tingkat outline bookmark** untuk hierarki yang jelas  
- **Menyimpan bookmark PDF Word** dengan struktur yang tepat  

### Jawaban Cepat
- **Apa kelas utama untuk membangun dokumen?** `DocumentBuilder`  
- **Metode mana yang menambahkan tingkat outline bookmark?** `BookmarksOutlineLevels.add()`  
- **Apakah saya memerlukan lisensi untuk mengekspor PDF?** Lisensi diperlukan untuk produksi; versi percobaan gratis dapat digunakan untuk evaluasi.  
- **Bisakah saya menumpuk bookmark secara mendalam?** Ya, tetapi pertahankan hierarki yang dapat dibaca oleh pengguna akhir.  
- **Versi Aspose.Words apa yang diperlukan?** Versi 25.3 atau lebih baru.

## Apa itu “membuat bookmark bersarang”?
Bookmark bersarang adalah bookmark yang ditempatkan di dalam bookmark lain, membentuk hierarki induk‑anak. Di PDF mereka muncul sebagai item yang dapat diperluas di panel bookmark, memungkinkan pembaca untuk menutup atau membuka bagian sesuai kebutuhan.

## Mengapa mengatur tingkat outline bookmark?
Tingkat outline menentukan urutan penumpukan visual di panel bookmark PDF. Tingkat yang tepat meningkatkan navigasi, terutama dalam kontrak hukum yang panjang, laporan teknis, atau e‑book di mana pengguna perlu menemukan informasi dengan cepat.

## Prasyarat
- **Perpustakaan dan Dependensi**: Aspose.Words untuk Java (versi 25.3 atau lebih baru).  
- **Lingkungan**: JDK 8+ dan IDE seperti IntelliJ IDEA atau Eclipse.  
- **Pengetahuan**: Dasar Java, familiaritas dengan Maven atau Gradle.

### Menyiapkan Aspose.Words
Tambahkan perpustakaan ke proyek Anda dengan Maven atau Gradle.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Akuisisi Lisensi
Aspose.Words adalah produk komersial, tetapi Anda dapat memulai dengan versi percobaan gratis.

1. **Percobaan Gratis** – Unduh dari [halaman rilis Aspose](https://releases.aspose.com/words/java/) untuk menguji semua kemampuan.  
2. **Lisensi Sementara** – Ajukan di [halaman lisensi sementara Aspose](https://purchase.aspose.com/temporary-license/) jika Anda memerlukan kunci jangka pendek.  
3. **Pembelian** – Beli lisensi permanen melalui [portal pembelian Aspose](https://purchase.aspose.com/buy).

Inisialisasi file lisensi dalam kode Anda sebelum menggunakan API Aspose apa pun untuk membuka semua fitur.

## Panduan Implementasi

### Cara membuat bookmark bersarang dalam dokumen Word
Kami akan membuat dokumen sederhana dan menambahkan tiga bookmark, salah satunya berisi bookmark lain.

#### Langkah 1: Inisialisasi dokumen dan builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Langkah 2: Sisipkan bookmark pertama (induk)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Langkah 3: Tempatkan bookmark kedua di dalam yang pertama
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Langkah 4: Tutup bookmark luar
```java
builder.endBookmark("Bookmark 1");
```

#### Langkah 5: Tambahkan bookmark ketiga yang independen
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Cara mengatur tingkat outline bookmark untuk ekspor PDF
Sekarang kami akan mengonfigurasi hierarki outline yang akan muncul di PDF akhir.

#### Langkah 1: Siapkan `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Langkah 2: Tetapkan tingkat outline ke setiap bookmark
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Langkah 3: Simpan dokumen sebagai PDF dengan bookmark yang telah dikonfigurasi
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Masalah Umum dan Solusinya
- **Bookmark tidak muncul** – Pastikan setiap `startBookmark` memiliki `endBookmark` yang cocok.  
- **Hierarki salah** – Periksa kembali nomor level yang Anda tetapkan; angka yang lebih rendah berarti level (induk) yang lebih tinggi.  
- **Lisensi tidak diterapkan** – Jika bookmark menghilang, pastikan file lisensi dimuat sebelum pemrosesan dokumen apa pun.  

## Aplikasi Praktis
1. **Kontrak hukum** – Lompat cepat ke klausul, sub‑klausul, dan lampiran.  
2. **Laporan teknis** – Navigasi bagian, tabel, dan gambar tanpa harus menggulir.  
3. **Materi e‑learning** – Biarkan siswa memperluas bab dan menutup contoh sesuai kebutuhan.

## Tips Kinerja
- Hapus bagian atau gambar yang tidak terpakai sebelum menyimpan untuk menjaga ukuran PDF tetap kecil.  
- Untuk dokumen yang sangat besar, panggil `doc.cleanup()` atau proses file dalam potongan untuk mengurangi tekanan memori.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menginstal Aspose.Words untuk Java?**  
J: Tambahkan dependensi Maven atau Gradle yang ditunjukkan di atas, kemudian letakkan file lisensi Anda di proyek dan inisialisasi dalam kode.

**T: Bisakah saya menggunakan bookmark tanpa mengatur tingkat outline?**  
J: Ya, tetapi tanpa tingkat outline panel bookmark PDF akan menampilkan daftar datar, membuat navigasi lebih sulit.

**T: Apakah ada batas seberapa dalam bookmark dapat bersarang?**  
J: Secara teknis tidak, tetapi pertahankan hierarki yang wajar (3‑4 level) untuk keterbacaan pengguna.

**T: Bagaimana Aspose menangani file Word yang sangat besar?**  
J: Perpustakaan ini melakukan streaming konten dan menawarkan metode seperti `Document.optimizeResources()` untuk menjaga penggunaan memori tetap rendah.

**T: Bisakah saya mengedit bookmark setelah PDF dihasilkan?**  
J: Ya, Anda dapat menggunakan Aspose.PDF untuk Java untuk memodifikasi judul bookmark, tujuan, atau hierarki setelah pembuatan.

## Sumber Daya
- [Dokumentasi Aspose.Words](https://reference.aspose.com/words/java/)
- [Unduh Rilis Terbaru](https://releases.aspose.com/words/java/)
- [Beli Lisensi](https://purchase.aspose.com/buy)
- [Percobaan Gratis](https://releases.aspose.com/words/java/)
- [Aplikasi Lisensi Sementara](https://purchase.aspose.com/temporary-license/)
- [Forum Dukungan Aspose](https://forum.aspose.com/c/words/10)

---

**Terakhir Diperbarui:** 2026-04-02  
**Diuji Dengan:** Aspose.Words 25.3 untuk Java  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}