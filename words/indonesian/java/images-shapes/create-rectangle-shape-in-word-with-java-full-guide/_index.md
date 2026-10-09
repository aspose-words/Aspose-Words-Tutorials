---
category: general
date: 2026-02-10
description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Aspose.Words
  untuk Java. Pelajari cara mengatur warna bayangan, cara menambahkan bayangan, dan
  membuat dokumen Word secara programatis.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: id
og_description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Aspose.Words
  untuk Java. Ikuti tutorial langkah demi langkah ini untuk mengatur warna bayangan,
  menambahkan bayangan, dan membuat dokumen Word.
og_title: Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap
tags:
- Aspose.Words
- Java
- Document Automation
title: Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap
url: /id/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap

Pernah perlu **membuat bentuk persegi panjang** dalam dokumen Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami kebingungan saat pertama kali mencoba menggambar grafik secara programatik di Word. Kabar baiknya? Dengan Aspose.Words untuk Java Anda dapat menambahkan persegi panjang ke halaman, memberi bayangan yang bagus, dan menyimpan file dalam hitungan detik. Pada tutorial ini kami akan menjelaskan secara detail **cara menambahkan bayangan**, **mengatur warna bayangan**, dan **membuat dokumen Word** dari awal.  

Kami akan membahas semua yang Anda perlukan: pustaka yang dibutuhkan, setiap baris kode, mengapa pengaturan tertentu penting, dan beberapa trik yang mungkin tidak Anda temukan di dokumentasi resmi. Pada akhir tutorial Anda akan memiliki contoh yang siap dijalankan yang membuat bentuk persegi panjang dengan bayangan abu‑abu lembut, disimpan sebagai *Shadow.docx*.

## Prasyarat – Apa yang Anda Butuhkan Sebelum Memulai

Sebelum kita masuk ke kode, pastikan Anda memiliki hal‑hal berikut:

| Persyaratan | Alasan |
|-------------|--------|
| Java Development Kit (JDK) 8 atau lebih baru | Aspose.Words berjalan pada JDK modern apa pun. |
| Maven atau Gradle (opsional) | Mempermudah menambahkan dependensi Aspose.Words. |
| Lisensi Aspose.Words untuk Java (atau percobaan gratis) | Pustaka ini bersifat komersial; percobaan cukup untuk pengujian. |
| IDE (IntelliJ IDEA, Eclipse, VS Code, dll.) | Membantu Anda menjalankan dan men-debug contoh dengan cepat. |

Jika Anda sudah memiliki proyek Java, cukup tambahkan koordinat Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Tidak ada pengaturan rumit selain itu—hanya metode `public static void main` biasa sudah cukup.

![contoh bentuk persegi panjang](https://example.com/rectangle-shadow.png "contoh bentuk persegi panjang dengan bayangan di Word")

*Teks alt gambar: contoh bentuk persegi panjang yang menampilkan persegi panjang sian dengan bayangan abu‑abu.*

## Langkah 1 – Buat Dokumen Word Baru

Hal pertama yang harus kita lakukan adalah membuat dokumen kosong. Anggap saja ini membuka file Word baru yang nantinya akan Anda gambar.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Mengapa memulai dengan `Document` kosong? Karena Aspose.Words memperlakukan kelas `Document` sebagai kanvas untuk semua operasi selanjutnya—menambahkan paragraf, tabel, atau bentuk. Jika Anda melewatkan langkah ini, Anda akan mendapatkan `NullPointerException` saat mencoba menyisipkan apa pun.

## Langkah 2 – Siapkan DocumentBuilder

`DocumentBuilder` adalah pena ramah yang menulis ke dalam `Document`. Ini adalah cara yang direkomendasikan untuk menambahkan konten karena secara otomatis mengelola posisi kursor.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Anda mungkin bertanya, “Mengapa tidak memanipulasi dokumen secara langsung?” Jawabannya: builder menyembunyikan detail tingkat‑rendah seperti penanganan section, sehingga kode menjadi lebih bersih dan kurang rawan kesalahan.

## Langkah 3 – Sisipkan Bentuk Persegi Panjang

Sekarang bagian yang menyenangkan—**cara membuat bentuk**. Kita akan menyisipkan persegi panjang berukuran 100 × 50 poin dan memberi isian sian agar Anda dapat melihatnya.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Beberapa catatan:

* `ShapeType.RECTANGLE` memberi tahu Aspose bahwa kita menginginkan persegi panjang; Anda dapat menggantinya dengan `OVAL`, `LINE`, dll.
* Dimensi dinyatakan dalam poin (1 pt ≈ 1/72 in). Sesuaikan sesuai tata letak Anda.
* Tanpa warna isian bentuk akan tidak terlihat di atas halaman putih—itulah mengapa dipilih sian.

## Langkah 4 – Tambahkan Bayangan dan **Atur Warna Bayangan**

Inilah bagian yang menjawab **cara menambahkan bayangan**. Objek `ShadowFormat` mengontrol setiap aspek visual bayangan, mulai dari warna hingga radius blur.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Mengapa nilai‑nilai ini dipilih?

* **Visibility** – Tanpa `setVisible(true)` pengaturan lainnya diabaikan.
* **Color** – Abu‑abu adalah pilihan netral yang cocok pada latar belakang terang maupun gelap. Ganti `java.awt.Color.GRAY` dengan warna `java.awt.Color` lain yang Anda suka.
* **Blur radius** – Nilai `5.0` memberikan efek lembut; angka lebih besar membuat bayangan tampak lebih menyebar.
* **OffsetX/Y** – Offset menggeser bayangan ke kanan dan ke bawah, meniru sumber cahaya dari kiri‑atas.
* **Transparency** – Bayangan semi‑transparan menyatu lebih baik dengan halaman, terutama saat dicetak.

Jika Anda menginginkan tampilan yang lebih tajam, turunkan blur radius menjadi `0` dan tingkatkan offset. Eksperimen sangat dianjurkan—bayangan bersifat visual, dan pengaturan yang tepat tergantung pada desain dokumen Anda.

## Langkah 5 – Simpan Dokumen

Akhirnya, kita menyimpan semuanya ke file `.docx`. Anda dapat memilih jalur apa pun; pastikan direktori tersebut sudah ada.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Saat Anda membuka *Shadow.docx* di Microsoft Word, Anda akan melihat persegi panjang sian dengan bayangan abu‑abu halus yang melayang 4 pt ke kanan dan ke bawah. Itu adalah alur kerja **membuat dokumen Word** yang lengkap.

### Hasil yang Diharapkan

| Elemen | Penampilan |
|--------|------------|
| Persegi panjang | Isian sian, ukuran 100 × 50 pt |
| Bayangan | Abu‑abu, 30 % transparan, blur 5 pt, offset (4, 4) |
| File | `Shadow.docx` disimpan pada jalur yang Anda berikan |

Jika bentuk tidak muncul, periksa kembali bahwa warna isian tidak sama dengan latar belakang halaman dan bahwa bayangan telah diatur menjadi terlihat.

## Tips Pro & Kesalahan Umum

* **Tips pro:** Gunakan `rectangle.setStrokeColor(java.awt.Color.BLACK);` jika Anda menginginkan batas di sekitar bentuk. Ini membuat persegi panjang lebih menonjol pada halaman cetak.
* **Waspadai:** Menyimpan ke folder yang hanya‑baca akan menghasilkan `IOException`. Pilih lokasi yang dapat ditulisi atau sesuaikan izin file.
* **Kasus khusus:** Jika Anda memerlukan isian transparan (tanpa warna), panggil `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Bentuk tetap akan menghasilkan bayangan, yang berguna untuk grafik gaya watermark.
* **Catatan kinerja:** Menambahkan ratusan bentuk dalam loop dapat meningkatkan penggunaan memori. Panggil `document.save` hanya sekali setelah semua bentuk ditambahkan.

## Contoh Lengkap yang Berfungsi

Berikut adalah seluruh program yang dapat Anda salin‑tempel ke dalam kelas Java bernama `ShadowDemo`. Program ini dapat dikompilasi dan dijalankan apa adanya (asalkan JAR Aspose.Words ada di classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Jalankan program, buka *Shadow.docx* yang dihasilkan, dan Anda akan melihat persegi panjang beserta bayangannya persis seperti yang dijelaskan.

## Bagaimana Jika Anda Membutuhkan Lebih Banyak Bentuk?

Anda mungkin bertanya, “Apakah saya dapat **membuat bentuk persegi panjang** berkali‑kali atau menggunakan bentuk lain?” Tentu saja. Cukup lakukan loop pada kode penyisipan dan sesuaikan koordinat menggunakan `builder.moveTo` atau `builder.insertParagraph`. Pengaturan bayangan yang sama dapat dipakai ulang dengan mengekstraknya ke dalam metode bantuan:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Panggil `applyStandardShadow(rectangle);` setelah setiap penyisipan bentuk untuk menjaga kode Anda tetap DRY (Don’t Repeat Yourself).

## Langkah Selanjutnya – Lebih Dari Dasar

Sekarang Anda sudah tahu **cara menambahkan bayangan**, pertimbangkan untuk mengeksplorasi topik terkait berikut:

* **Cara mengatur warna bayangan** untuk run teks – memberi judul efek angkat halus.
* **Membuat dokumen Word** dengan tabel dan gambar – menggabungkan bentuk dengan konten lain.
* **Cara membuat animasi bentuk** menggunakan fitur bawaan Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}