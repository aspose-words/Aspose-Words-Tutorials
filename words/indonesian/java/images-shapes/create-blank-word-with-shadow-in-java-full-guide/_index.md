---
category: general
date: 2026-05-04
description: Buat dokumen Word kosong dalam Java dan pelajari cara mengatur warna
  bayangan, blur, dan offset untuk bentuk – tutorial singkat.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: id
og_description: Buat dokumen Word kosong di Java dan pelajari cara mengatur warna
  bayangan, blur, serta offset untuk bentuk. Ikuti tutorial langkah demi langkah ini.
og_title: Buat kata kosong dengan bayangan di Java – Panduan lengkap
tags:
- Aspose.Words
- Java
- Document Automation
title: Buat kata kosong dengan bayangan di Java – Panduan lengkap
url: /id/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word dengan bayangan di Java – Panduan Lengkap

Pernahkah Anda perlu **create blank word** file dari kode dan membuatnya terlihat lebih menarik? Anda bukan satu-satunya. Dalam banyak proyek pelaporan atau pembuatan templat, hal pertama yang Anda lakukan adalah membuat dokumen Word kosong, lalu menambahkan sebuah bentuk dengan bayangan untuk memberi kesan yang lebih halus.

Dalam tutorial ini kami akan membahas langkah demi langkah—cara membuat dokumen Word kosong menggunakan Aspose.Words for Java, **how to add shadow** ke sebuah bentuk, serta detail tentang **set shadow color**, **how to set blur**, dan **how to set offset**. Pada akhir tutorial Anda akan memiliki file `.docx` siap pakai yang menampilkan sebuah persegi panjang dengan bayangan merah yang agak blur dan semi‑transparent.

## Apa yang Anda perlukan

- **Aspose.Words for Java** (versi terbaru apa pun; kode ini bekerja dengan 23.9+)
- JDK 8 atau yang lebih baru
- Sebuah IDE atau editor teks sederhana plus terminal
- Pengetahuan dasar Java—tidak perlu yang rumit, cukup kemampuan menjalankan metode `main`

Tidak diperlukan konfigurasi Maven atau Gradle tambahan untuk demo ini; cukup letakkan JAR Aspose pada classpath Anda dan Anda siap.

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="create blank word document with shadow example"}

## Create blank word – Menginisialisasi Dokumen

Langkah pertama adalah membuat file Word kosong yang baru. Anggaplah ini sebagai kanvas bersih di mana Anda nanti dapat menggambar bentuk, tabel, atau teks.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Mengapa ini penting:** `Document` mewakili seluruh paket `.docx`. Dengan membuatnya menggunakan konstruktor default, Anda secara efektif **create blank word** – tidak ada konten, tidak ada bagian, hanya struktur file yang siap diisi.

## Cara menambahkan bayangan ke sebuah bentuk

Setelah kita memiliki dokumen yang bersih, mari sisipkan sebuah persegi panjang yang akan menampung bayangan kita. Di sinilah keajaiban visual dimulai.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Tip pro:** Pemanggilan `insertShape` secara otomatis menambahkan bentuk ke paragraf saat ini, jadi Anda tidak perlu mengatur posisi secara manual kecuali Anda menginginkan penempatan absolut.

## Set shadow color – membuat bayangan menonjol

Bayangan tanpa warna hanyalah blur abu-abu, yang dapat terlihat datar. Dengan mengatur warna bayangan, Anda dapat menyesuaikannya dengan merek atau sekadar membuatnya lebih menonjol.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Apa yang terjadi:** `ShadowFormat` mengontrol setiap aspek visual bayangan. Mengaktifkan `setVisible(true)` menyalakan efek, dan `setColor` memungkinkan Anda memilih warna `java.awt.Color` apa pun. Dalam contoh kami, kami memilih merah untuk memperlihatkan **set shadow color** dengan jelas.

## Cara mengatur blur untuk efek halus

Bayangan yang tajam dan bertepi keras dapat terlihat keras. Menambahkan blur melunakkan tepi, memberikan tampilan yang lebih alami.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Mengapa blur penting:** Nilai `setBlur` diukur dalam poin. Nilai `5.0` menghasilkan difusi lembut; tingkatkan untuk bayangan yang lebih kabur, turunkan untuk outline yang lebih tajam.

## Cara mengatur offset – memposisikan bayangan

Offset menentukan di mana bayangan jatuh relatif terhadap bentuk. Anggaplah sebagai pergeseran X dan Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Penjelasan offset:** X positif memindahkan bayangan ke kanan, Y positif memindahkannya ke bawah. Coba gunakan angka negatif jika Anda ingin bayangan muncul di sisi berlawanan.

## Menyempurnakan transparansi

Jika Anda ingin bayangan tidak terlalu dominan, sesuaikan transparansinya. Langkah ini bukan persyaratan kata kunci tetapi melengkapi kontrol visual.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Menyimpan dokumen – lihat hasilnya

Akhirnya, tulis dokumen ke disk. Anda akan mendapatkan file `.docx` yang dapat dibuka di Word, LibreOffice, atau penampil lain yang mendukung format tersebut.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Apa yang akan Anda lihat:** Buka `ShadowShape.docx`. Satu halaman akan menampilkan persegi panjang 150 × 80 pt dengan bayangan merah yang sedikit blur, dipindahkan 8 pt ke bawah dan kanan. Bayangan tersebut 30 % transparan, sehingga persegi panjang tetap terlihat jelas.

---

## Pertanyaan umum dan kasus khusus

### Bagaimana jika saya membutuhkan bentuk lain?

Ganti `ShapeType.RECTANGLE` dengan nilai enum lain (`ELLIPSE`, `CLOUD`, `CALLOUT`, dll.). Pengaturan bayangan bekerja identik pada semua bentuk.

### Bisakah saya menerapkan bayangan yang sama ke beberapa bentuk tanpa mengulang kode?

Tentu saja. Buat metode pembantu:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Kemudian panggil `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` untuk bentuk apa pun.

### Apakah ini bekerja dengan versi Aspose yang lebih lama?

`API` `ShadowFormat` telah stabil sejak versi 19.8, jadi Anda seharusnya tidak mengalami masalah dengan rilis terbaru. Jika Anda menggunakan build yang sangat lama, periksa Javadoc untuk `ShadowFormat` untuk memastikan nama metode.

### Cara mengekspor ke PDF sambil mempertahankan bayangan?

Cukup panggil `document.save("output.pdf");` setelah bentuk dibuat. Aspose.Words merender bayangan dengan benar di PDF, mempertahankan blur dan transparansi.

---

## Ringkasan – create blank word dengan bayangan khusus

Kami memulai dengan **create blank word** menggunakan `new Document()`, lalu menyisipkan persegi panjang, **set shadow color**, mempelajari **how to add shadow**, menyesuaikan **how to set blur**, dan akhirnya mengatur **how to set offset** untuk memposisikannya dengan tepat. Kode lengkap yang dapat dijalankan ada di cuplikan di atas, dan file hasilnya memperlihatkan efek tersebut dengan jelas.

---

## Selanjutnya?

- **Bereksperimen dengan properti bayangan lain** seperti `ShadowFormat.setStyle(ShadowStyle.OUTER)` untuk gaya visual yang berbeda.
- **Menggabungkan beberapa bentuk** masing‑masing dengan bayangan sendiri untuk membuat diagram kompleks.
- **Menambahkan teks di dalam bentuk** menggunakan `builder.insertHtml("<b>Hello</b>")` sebelum menyisipkan bentuk, lalu terapkan logika bayangan yang sama.
- **Jelajahi opsi pemformatan lain** seperti gaya garis, warna isi, atau isian gradien—Aspose.Words menyediakan API yang kaya untuk semua itu.

Silakan sesuaikan radius blur, offset, atau warna hingga bayangan terasa tepat untuk bahasa desain dokumen Anda. Selamat coding, dan semoga file Word yang Anda hasilkan selalu tampak lebih halus!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}