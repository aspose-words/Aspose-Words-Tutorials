---
date: 2026-02-14
description: Pelajari cara menampilkan matematika secara inline, menyisipkan persamaan
  matematika, dan memanipulasi objek Office Math dengan mudah menggunakan Aspose.Words
  for Java.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Menampilkan Matematika Inline dengan Office Math di Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menampilkan Matematika Inline dengan Office Math di Aspose.Words untuk Java

Dalam tutorial komprehensif ini Anda akan menemukan cara **menampilkan matematika inline** menggunakan objek Office Math di Aspose.Words untuk Java. Baik Anda perlu **menyisipkan persamaan matematika** ke dalam laporan atau menyempurnakan pemformatan rumus kompleks, panduan ini akan memandu Anda melalui setiap langkah—dari memuat dokumen Word hingga menyimpan hasil akhir.

## Jawaban Cepat
- **Apa arti “display math inline”?** Persamaan muncul dalam alur teks, bukan pada baris terpisah.  
- **Kelas mana yang mewakili objek matematika?** `OfficeMath` dalam API Aspose.Words.  
- **Apakah saya dapat mengubah perataan?** Ya, gunakan `setJustification` dengan LEFT, CENTER, atau RIGHT.  
- **Apakah saya memerlukan lisensi untuk fitur ini?** Lisensi Aspose.Words untuk Java yang valid diperlukan untuk penggunaan produksi.  
- **Versi apa yang ditunjukkan?** Kode ini bekerja dengan rilis terbaru Aspose.Words untuk Java (2026).  

## Apa itu “display math inline”?
Menampilkan matematika inline berarti persamaan diperlakukan sebagai bagian dari teks paragraf, memungkinkan ia membungkus secara alami dengan kata‑kata di sekitarnya. Ini berguna untuk rumus singkat yang tidak boleh memutus alur bacaan.

## Mengapa menggunakan objek Office Math di Aspose.Words untuk Java?
- **Kontrol presisi** atas tata letak persamaan (inline vs. display).  
- **Manipulasi programatik** persamaan tanpa membuka Word secara manual.  
- **Rendering konsisten** di seluruh platform, sempurna untuk pembuatan laporan otomatis.

## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki:

- Aspose.Words untuk Java terinstal dan direferensikan dalam proyek Anda.  
- File Word yang sudah berisi persamaan Office Math (misalnya `OfficeMath.docx`).  
- Lisensi yang valid jika Anda berencana menjalankan kode di luar mode evaluasi.

## Panduan Langkah‑per‑Langkah

### Memuat Dokumen
Pertama, muat dokumen yang berisi persamaan Office Math yang ingin Anda kerjakan:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Mengakses Objek Office Math
Ambil node Office Math pertama dari dokumen:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Mengatur Tipe Tampilan (Inline vs. Display)
Kontrol apakah persamaan muncul inline dengan teks di sekitarnya atau pada baris terpisah. Untuk **display math inline**, gunakan enum `INLINE`; untuk baris terpisah, gunakan `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Jika Anda ingin persamaan tetap inline, ganti `DISPLAY` dengan `INLINE`.*

### Mengatur Justifikasi
Sesuaikan perataan persamaan. Di bawah ini kami menyesuaikannya ke kiri, tetapi Anda juga dapat memilih `CENTER` atau `RIGHT`:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Menyimpan Dokumen yang Dimodifikasi
Akhirnya, tulis perubahan kembali ke file baru:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Kode Sumber Lengkap untuk Menggunakan Objek Office Math di Aspose.Words untuk Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Masalah Umum & Pemecahan Masalah
- **Persamaan tidak ditemukan:** Pastikan dokumen memang berisi objek Office Math; jika tidak, `doc.getChild` akan mengembalikan `null`.  
- **Tipe tampilan tidak berpengaruh:** Pastikan Anda menggunakan versi terbaru Aspose.Words; rilis lama mungkin memiliki dukungan terbatas untuk `OfficeMathDisplayType`.  
- **Pengecualian lisensi:** Jika Anda melihat kesalahan lisensi, periksa kembali bahwa file lisensi Anda telah dimuat dengan benar sebelum membuat instance `Document`.  

## Pertanyaan yang Sering Diajukan

**Q: Apa tujuan objek Office Math di Aspose.Words untuk Java?**  
A: Objek Office Math memungkinkan Anda merepresentasikan dan memanipulasi persamaan matematika secara programatik, memberi Anda kontrol penuh atas tampilan dan pemformatan.

**Q: Bisakah saya mengatur perataan persamaan Office Math secara berbeda dalam dokumen saya?**  
A: Ya, gunakan metode `setJustification` untuk meratakan ke kiri, kanan, atau tengah.

**Q: Apakah Aspose.Words untuk Java cocok untuk menangani dokumen matematika yang kompleks?**  
A: Tentu saja. Perpustakaan ini sepenuhnya mendukung persamaan kompleks, pecahan bersarang, matriks, dan lainnya.

**Q: Bagaimana saya dapat mempelajari lebih lanjut tentang Aspose.Words untuk Java?**  
A: Untuk dokumentasi lengkap dan unduhan, kunjungi [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**Q: Di mana saya dapat mengunduh Aspose.Words untuk Java?**  
A: Anda dapat mengunduh Aspose.Words untuk Java dari situs web: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Terakhir Diperbarui:** 2026-02-14  
**Diuji Dengan:** Aspose.Words for Java 24.12 (latest as of Feb 2026)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}