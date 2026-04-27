---
date: '2026-04-27'
description: Pelajari cara mengatur bookmark dan menyimpan PDF dengan bookmark menggunakan
  Aspose.Words untuk Java. Tingkatkan keterbacaan dan navigasi dengan panduan komprehensif
  ini.
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: Cara Menetapkan Bookmark di PDF dengan Aspose.Words Java
url: /id/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menetapkan Bookmark di PDF dengan Aspose.Words Java

## Pendahuluan
Jika Anda kesulitan mengelola **cara menetapkan bookmark** saat mengonversi dokumen Word menjadi PDF, Anda berada di tempat yang tepat. Dalam tutorial ini kami akan membahas seluruh proses menggunakan Aspose.Words untuk Java, mulai dari membuat bookmark bersarang hingga mengonfigurasi level outline mereka sehingga PDF akhir bersih, profesional, dan mudah dinavigasi.

**Apa yang Akan Anda Pelajari**
- Menyiapkan Aspose.Words untuk Java dalam proyek Anda  
- **Membuat bookmark bersarang** di dalam dokumen Word  
- **Mengonfigurasi level outline bookmark** untuk outline PDF yang terstruktur  
- **Menyimpan PDF dengan bookmark** yang mencerminkan hierarki yang Anda definisikan  

### Jawaban Cepat
- **Apa kelas utama untuk membangun dokumen?** `DocumentBuilder`  
- **Opsi mana yang mengontrol hierarki bookmark?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **Bisakah saya menggunakan Maven atau Gradle?** Ya, keduanya didukung (lihat potongan kode)  
- **Apakah saya memerlukan lisensi?** Versi percobaan dapat digunakan untuk evaluasi; lisensi permanen diperlukan untuk produksi  
- **Apakah PDF akan mempertahankan bookmark bersarang?** Tentu saja, ketika level outline diatur dengan benar  

## Apa itu “cara menetapkan bookmark” dalam PDF?
Menetapkan bookmark berarti mendefinisikan entri yang dapat diklik di panel navigasi PDF yang melompat ke bagian tertentu dari dokumen. Ketika bookmark bersarang dan diberikan level outline, mereka muncul sebagai pohon yang dapat dilipat, membuat dokumen besar jauh lebih mudah dijelajahi.

## Mengapa menggunakan Aspose.Words untuk level outline bookmark?
Aspose.Words memberi Anda kontrol pemrograman penuh atas konversi Word‑ke‑PDF, termasuk kemampuan untuk **menghasilkan PDF dengan bookmark** yang mencerminkan struktur dokumen Anda. Ini menghilangkan kebutuhan akan pemrosesan manual setelah konversi dan memastikan pengalaman pengguna yang konsisten di semua PDF yang dihasilkan.

## Prasyarat
- **Perpustakaan dan Dependensi**: Aspose.Words untuk Java (versi 25.3 atau lebih baru).  
- **Lingkungan**: JDK 8 atau lebih baru, IDE seperti IntelliJ IDEA atau Eclipse.  
- **Pengetahuan**: Java dasar, familiar dengan Maven atau Gradle.

## Menyiapkan Aspose.Words
Tambahkan perpustakaan yang diperlukan ke sistem build Anda.

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
Aspose.Words adalah produk komersial, tetapi Anda dapat memulai dengan percobaan gratis.

1. **Percobaan Gratis**: Unduh dari [halaman rilis Aspose](https://releases.aspose.com/words/java/) untuk menguji semua kemampuan.  
2. **Lisensi Sementara**: Ajukan lisensi sementara di [halaman lisensi sementara Aspose](https://purchase.aspose.com/temporary-license/) jika diperlukan.  
3. **Pembelian**: Untuk penggunaan berkelanjutan, beli lisensi dari [portal pembelian Aspose](https://purchase.aspose.com/buy).

Inisialisasi file lisensi dalam kode Anda untuk membuka semua fitur.

## Panduan Implementasi
Berikut adalah panduan langkah‑demi‑langkah yang mencakup **membuat bookmark bersarang**, mengatur level outline mereka, dan akhirnya **menyimpan PDF dengan bookmark**.

### Membuat Bookmark Bersarang
**Gambaran Umum**: Bangun dokumen Word dan sematkan bookmark yang mencerminkan hierarki.

#### Langkah 1: Inisialisasi Dokumen dan Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Ini membuat dokumen baru yang siap untuk penyisipan konten.

#### Langkah 2: Sisipkan Bookmark Bersarang
Mulailah dengan bookmark utama, kemudian sisipkan bookmark kedua di dalamnya.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### Langkah 3: Tambahkan Bookmark Tambahan
Anda dapat terus menambahkan bookmark independen sesuai kebutuhan.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Mengonfigurasi Level Outline Bookmark
**Gambaran Umum**: Tetapkan level outline sehingga panel bookmark PDF mencerminkan hierarki yang dimaksud.

#### Langkah 1: Siapkan PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Opsi-opsi ini akan digunakan saat menyimpan dokumen sebagai PDF.

#### Langkah 2: Tambahkan Level Outline
Pemetaan setiap nama bookmark ke level outline (1 = tingkat atas, 2 = anak, dll.).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Langkah 3: Simpan Dokumen
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
PDF yang dihasilkan kini berisi pohon bookmark terstruktur.

## Masalah Umum dan Solusinya
- **Bookmark hilang** – Verifikasi setiap `startBookmark` memiliki `endBookmark` yang cocok.  
- **Hierarki tidak tepat** – Periksa nomor level outline; anak harus memiliki nomor yang lebih tinggi daripada induknya.  
- **Dokumen besar** – Panggil `doc.removeUnusedResources()` sebelum menyimpan untuk mengurangi ukuran file.

## Aplikasi Praktis
1. **Kontrak hukum** – Lompat cepat ke klausul dan sub‑klausul.  
2. **Laporan tahunan** – Menavigasi bagian, tabel, dan grafik dengan mudah.  
3. **Materi e‑learning** – Menyediakan daftar isi yang dapat diklik untuk siswa.

## Pertimbangan Kinerja
- Hapus node yang tidak diperlukan sebelum konversi untuk menjaga PDF tetap ringan.  
- Untuk file yang sangat besar, pertimbangkan streaming dokumen untuk menghindari konsumsi memori yang tinggi.

## Kesimpulan
Anda sekarang tahu **cara menetapkan bookmark**, mengonfigurasi level outline mereka, dan **menyimpan PDF dengan bookmark** menggunakan Aspose.Words untuk Java. Teknik ini secara dramatis meningkatkan navigasi PDF dan memberikan dokumen Anda sentuhan profesional.

**Langkah Selanjutnya**: Coba tambahkan ikon khusus ke bookmark atau integrasikan alur kerja ini ke layanan pemrosesan batch.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menginstal Aspose.Words untuk Java?**  
A: Tambahkan dependensi Maven atau Gradle yang ditunjukkan di atas, lalu letakkan file lisensi Anda di folder resources proyek.

**Q: Bisakah saya membuat bookmark tanpa level outline?**  
A: Ya, tetapi tanpa level outline panel navigasi PDF akan menampilkan semua bookmark pada level yang sama, membuat dokumen besar lebih sulit dijelajahi.

**Q: Apakah ada batas seberapa dalam bookmark dapat bersarang?**  
A: Secara teknis tidak, tetapi jaga agar hierarki tetap dapat dibaca oleh pengguna akhir—biasanya 3‑4 level sudah cukup.

**Q: Bagaimana Aspose menangani file Word yang sangat besar?**  
A: Ia melakukan streaming konten dan menawarkan metode seperti `Document.optimizeResources()` untuk menjaga penggunaan memori tetap rendah.

**Q: Bisakah saya mengedit bookmark setelah PDF dihasilkan?**  
A: Ya, Anda dapat menggunakan Aspose.PDF untuk Java untuk memodifikasi judul bookmark, tujuan, atau hierarki setelah konversi.

---

**Last Updated:** 2026-04-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

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