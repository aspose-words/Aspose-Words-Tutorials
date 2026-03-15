---
date: '2026-03-15'
description: Pelajari cara menambahkan bookmark PDF dan mengatur tingkat outline menggunakan
  Aspose.Words for Java, meningkatkan navigasi dan keterbacaan PDF.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Tambahkan bookmark PDF dan level outline dengan Aspose.Words Java
url: /id/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Penanda PDF dan Tingkat Garis Besar dengan Aspose.Words Java

## Pendahuluan
Dalam tutorial ini Anda akan belajar **cara menambahkan penanda PDF** dan mengonfigurasi tingkat garis besar mereka menggunakan **Aspose.Words for Java**. Penanda yang terorganisir dengan baik membuat PDF besar mudah dinavigasi, baik Anda sedang menangani kontrak hukum, laporan terperinci, atau materi e‑learning.

**Apa yang Akan Anda Pelajari**
- Siapkan dan gunakan **Aspose.Words for Java**
- **Buat penanda bersarang** dalam dokumen Word
- **Cara mengatur tingkat garis besar penanda** untuk hierarki yang bersih
- **Simpan dokumen sebagai PDF** dengan pohon penanda terstruktur

Pastikan Anda memiliki semua yang diperlukan sebelum kita mulai.

### Prasyarat
Sebelum memulai, pastikan Anda memiliki:
- **Perpustakaan dan Dependensi**: Aspose.Words for Java (versi 25.3 atau lebih baru).  
- **Pengaturan Lingkungan**: JDK terinstal dan IDE seperti IntelliJ IDEA atau Eclipse.  
- **Prasyarat Pengetahuan**: Keterampilan pemrograman Java dasar dan familiaritas dengan Maven atau Gradle.

## Jawaban Cepat
- **Apa tujuan utama?** Menambahkan penanda PDF dan mendefinisikan tingkat garis besar.  
- **Perpustakaan apa yang diperlukan?** Aspose.Words for Java (v25.3+).  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis cukup untuk pengujian; lisensi komersial diperlukan untuk produksi.  
- **Bisakah saya menghasilkan PDF dengan penanda dalam satu langkah?** Ya—konfigurasikan `PdfSaveOptions` dan panggil `doc.save`.  
- **Apakah bersarang didukung?** Tentu saja, Anda dapat membuat tingkat tak terbatas dari penanda bersarang.

## Menyiapkan Aspose.Words
Untuk memulai, sertakan dependensi yang diperlukan dalam proyek Anda. Berikut cara melakukannya menggunakan Maven dan Gradle:

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

### Perolehan Lisensi
Aspose.Words adalah produk komersial, tetapi Anda dapat memulai dengan percobaan gratis untuk menjelajahi fiturnya.

1. **Percobaan Gratis**: Unduh dari [halaman rilis Aspose](https://releases.aspose.com/words/java/) untuk menguji semua kemampuan.  
2. **Lisensi Sementara**: Ajukan lisensi sementara di [halaman lisensi sementara Aspose](https://purchase.aspose.com/temporary-license/) jika Anda memerlukan waktu evaluasi yang lebih lama.  
3. **Pembelian**: Untuk penggunaan berkelanjutan, beli lisensi dari [portal pembelian Aspose](https://purchase.aspose.com/buy).

Setelah Anda memiliki file lisensi, inisialisasi di proyek Anda untuk membuka semua fitur.

## Panduan Implementasi
Kami akan membimbing Anda melalui implementasi langkah demi langkah, memecah setiap bagian menjadi potongan kecil.

### Membuat Penanda Bersarang
**Gambaran Umum**: Pelajari cara **membuat penanda bersarang** dalam dokumen Word menggunakan Aspose.Words for Java.

#### Langkah 1: Inisialisasi Dokumen dan Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Ini membuat dokumen Word baru dan objek builder yang memungkinkan Anda menyisipkan konten dan penanda.

#### Langkah 2: Sisipkan Penanda Bersarang
Mulailah dengan membuat penanda utama:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Sekarang, sisipkan penanda lain di dalamnya:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Selesaikan penanda luar:
```java
builder.endBookmark("Bookmark 1");
```

#### Langkah 3: Tambahkan Penanda Tambahan
Anda dapat terus menambahkan penanda sesuai kebutuhan. Misalnya, penanda ketiga terpisah:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Mengonfigurasi Tingkat Garis Besar Penanda
**Gambaran Umum**: Atur penanda Anda dengan menetapkan tingkat garis besar mereka, yang menentukan hierarki yang akan terlihat di penampil PDF.

#### Langkah 1: Siapkan PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Opsi ini akan diterapkan saat Anda **menyimpan dokumen sebagai PDF**.

#### Langkah 2: Tambahkan Tingkat Garis Besar
Tetapkan tingkat untuk setiap penanda; angka yang lebih rendah muncul lebih tinggi dalam pohon garis besar:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Langkah 3: Simpan Dokumen
Akhirnya, hasilkan PDF dengan hierarki penanda yang telah dikonfigurasi:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### Tips Pemecahan Masalah
- **Penanda Hilang**: Pastikan setiap `startBookmark` memiliki `endBookmark` yang cocok.  
- **Tingkat Tidak Tepat**: Periksa kembali urutan penambahan tingkat garis besar; hierarki mengikuti tingkat numerik yang Anda tetapkan.  
- **Dokumen Besar**: Gunakan `doc.removeUnusedResources()` sebelum menyimpan untuk mengurangi ukuran PDF.

## Aplikasi Praktis
Berikut beberapa skenario dunia nyata di mana **menambahkan penanda PDF** bersinar:

1. **Dokumen Hukum** – Lompat cepat ke klausul, lampiran, atau aneks.  
2. **Laporan Keuangan** – Navigasi antar bagian, tabel, dan grafik.  
3. **Materi E‑Learning** – Berikan pembaca tabel isi yang dapat diklik.  

## Pertimbangan Kinerja
- **Manajemen Memori**: Saat memproses file Word yang sangat besar, panggil `System.gc()` setelah menyimpan untuk membebaskan memori.  
- **Ukuran Dokumen**: Hapus gambar yang tidak diperlukan atau teks tersembunyi sebelum membuat penanda untuk menjaga PDF akhir tetap ringan.

## Kesimpulan
Anda kini memiliki metode lengkap dan siap produksi untuk **menambahkan penanda PDF**, mengonfigurasi tingkat garis besar mereka, dan **menghasilkan PDF dengan penanda** menggunakan Aspose.Words for Java. Pendekatan ini secara dramatis meningkatkan kegunaan PDF dan memberikan pengguna akhir pengalaman navigasi yang profesional.

**Langkah Selanjutnya**: Cobalah menggabungkan teknik ini dengan Aspose.PDF untuk Java untuk mengedit penanda setelah PDF dibuat, atau integrasikan ke dalam layanan pemrosesan batch yang secara otomatis menambahkan tabel isi ke setiap laporan yang Anda hasilkan.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menginstal Aspose.Words untuk Java?**  
J: Tambahkan dependensi Maven atau Gradle yang ditunjukkan di atas, kemudian letakkan file lisensi Anda di folder resources proyek dan inisialisasi saat startup.

**T: Bisakah saya menggunakan penanda tanpa tingkat garis besar?**  
J: Ya, tetapi tanpa tingkat garis besar penampil PDF akan menampilkan semua penanda pada hierarki yang sama, sehingga navigasi menjadi lebih sulit.

**T: Apa batasan pada penataan bersarang penanda?**  
J: Secara teknis tidak ada batas keras, tetapi pertahankan hierarki yang wajar (3‑5 tingkat) untuk keterbacaan optimal.

**T: Bagaimana Aspose menangani dokumen besar?**  
J: Ia melakukan streaming konten dan menyediakan metode seperti `Document.optimizeResources()` untuk menjaga penggunaan memori tetap rendah.

**T: Bisakah saya memodifikasi penanda setelah menyimpan PDF?**  
J: Tentu saja—gunakan Aspose.PDF untuk Java untuk mengedit, mengubah urutan, atau menghapus penanda setelah pembuatan.

## Sumber Daya
- [Dokumentasi Aspose.Words](https://reference.aspose.com/words/java/)
- [Unduh Rilis Terbaru](https://releases.aspose.com/words/java/)
- [Beli Lisensi](https://purchase.aspose.com/buy)
- [Percobaan Gratis](https://releases.aspose.com/words/java/)
- [Aplikasi Lisensi Sementara](https://purchase.aspose.com/temporary-license/)
- [Forum Dukungan Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Terakhir Diperbarui:** 2026-03-15  
**Diuji Dengan:** Aspose.Words for Java 25.3  
**Penulis:** Aspose