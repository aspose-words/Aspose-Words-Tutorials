---
category: general
date: 2026-02-15
description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Java. Pelajari
  cara menambahkan bayangan pada bentuk, menyimpan dokumen Word, dan menambahkan bentuk
  persegi panjang dengan Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: id
og_description: Buat bentuk persegi panjang dalam file Word dengan Java. Panduan ini
  menunjukkan cara menambahkan bayangan bentuk, menyimpan dokumen Word, dan menambahkan
  bentuk persegi panjang langkah demi langkah.
og_title: Buat bentuk persegi panjang – Tutorial Java Aspose.Words
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

# Membuat bentuk persegi panjang di Word dengan Java – Panduan Lengkap

Pernah perlu **membuat bentuk persegi panjang** dalam file Word tetapi tidak yakin harus mulai dari mana? Anda bukan satu-satunya—banyak pengembang mengalami hal yang sama saat mengotomatisasi laporan atau faktur. Kabar baiknya? Dengan Aspose.Words untuk Java Anda dapat membuat persegi panjang, menambahkan bayangan yang bagus, dan menyimpan dokumen Word dalam beberapa baris kode.

Dalam tutorial ini kami akan membahas semua yang Anda perlukan: mulai dari menginisialisasi dokumen kosong, mengkonfigurasi bayangan, hingga akhirnya menyimpan file. Pada akhir tutorial Anda akan mengetahui **cara memberi bayangan pada shape** objek, cara **menambahkan bayangan pada shape**, dan cara **menambahkan bentuk persegi panjang** ke dokumen Word apa pun yang Anda buat. Tidak diperlukan dokumen eksternal—hanya kode yang dapat dijalankan.

## Prasyarat

- Java 8 atau yang lebih baru (API juga berfungsi dengan Java 11+).  
- Perpustakaan Aspose.Words untuk Java (versi 23.9 atau lebih baru).  
- IDE seperti IntelliJ IDEA atau Eclipse—apa saja boleh.  
- Familiaritas dasar dengan sintaks Java.

> **Tip pro:** Jika Anda menggunakan Maven, tambahkan dependensi Aspose.Words ke `pom.xml` Anda dan biarkan IDE menangani sisanya.

---

## Langkah 1: Inisialisasi Dokumen Baru – Cara **membuat bentuk persegi panjang**

Hal pertama yang harus dilakukan: Anda memerlukan kanvas bersih. Di Aspose.Words kanvas tersebut adalah objek `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

Kelas `Document` mewakili seluruh file .docx. Anggaplah itu sebagai buku catatan di mana Anda nanti akan **menambahkan bentuk persegi panjang** dan bayangannya.

## Langkah 2: Bangun Persegi Panjang – **Tambahkan bentuk persegi panjang**

Sekarang kita benar‑benarnya membuat persegi panjang. Kita akan mengatur ukuran, tata letak, dan warna isi.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Mengapa menggunakan pembungkus `INLINE`? Karena kami ingin shape berperilaku seperti paragraf—sempurna untuk laporan sederhana. Anda dapat mengubahnya menjadi `TOPBOTTOM` jika nanti membutuhkan teks mengalir di sekitar shape.

## Langkah 3: Terapkan Bayangan – **Cara memberi bayangan pada shape**

Persegi panjang datar terlihat agak membosankan. Menambahkan bayangan memberi kedalaman dan membuat dokumen terasa lebih halus. Di sinilah kami menjawab “**cara memberi bayangan pada shape**” secara praktik.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Setiap properti melakukan sesuatu yang spesifik:

- `setVisible(true)` mengaktifkan bayangan.  
- `setColor` memilih abu‑abu gelap untuk efek halus.  
- `setBlurRadius` mengontrol seberapa lembut tepi terlihat.  
- `setOffsetX/Y` memindahkan bayangan ke kanan dan ke bawah, meniru sumber cahaya.  
- `setTransparency` membuatnya sedikit tembus pandang, sehingga shape tetap menjadi fokus.

> **Catatan:** Jika Anda pernah membutuhkan bayangan berwarna, cukup berikan `java.awt.Color` yang berbeda ke `setColor`.

## Langkah 4: Sisipkan Shape ke dalam Dokumen

Dengan persegi panjang dan bayangannya siap, kami menempatkannya ke bagian pertama dokumen.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Menambahkan ke body menempatkan shape di tempat paragraf baru akan berada. Jika Anda ingin persegi panjang pada lokasi tertentu, Anda dapat menggunakan `insertBefore` atau memanipulasi koleksi `Paragraph`.

## Langkah 5: **Simpan dokumen Word** – Simpan Pekerjaan Anda

Langkah terakhir adalah menulis file ke disk. Inilah saat Anda benar‑benar **menyimpan dokumen Word**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif di mesin Anda. Setelah menjalankan program, buka `ShadowShape.docx` di Microsoft Word—Anda akan melihat persegi panjang berwarna abu‑abu muda dengan bayangan gelap yang lembut.

![Diagram yang menunjukkan bentuk persegi panjang dengan bayangan yang dibuat menggunakan Aspose.Words](https://example.com/rectangle-shadow.png "buat bentuk persegi panjang dengan bayangan")

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan beberapa persegi panjang?

Cukup ulangi **Langkah 2** dan **Langkah 3** dalam sebuah loop, menyesuaikan `setWidth`, `setHeight`, atau `setFillColor` pada setiap iterasi. Ingat untuk memberi setiap shape nama variabel yang unik atau menyimpannya dalam sebuah list.

### Bisakah saya mengekspor ke PDF alih-alih DOCX?

Tentu saja. Setelah shape ditambahkan, panggil `document.save("output.pdf")`. Aspose.Words akan menangani konversi, mempertahankan bayangan.

### Bagaimana dengan versi Word yang lebih lama?

Gunakan overload `document.save("file.doc", SaveFormat.DOC)`. API secara otomatis menurunkan fitur, tetapi perhatikan bahwa beberapa gaya bayangan mungkin terlihat sedikit berbeda pada format lama.

### Bagaimana cara mengubah arah bayangan?

Manipulasi `setOffsetX` dan `setOffsetY`. X positif memindahkan bayangan ke kanan, negatif ke kiri. Y positif memindahkan ke bawah, negatif ke atas. Bereksperimenlah dengan angka-angka tersebut untuk mensimulasikan sumber cahaya dari sudut mana pun.

## Tips Bekerja dengan Shapes

- **Group shapes**: Jika Anda membutuhkan label di sebelah persegi panjang, buat `GroupShape` dan tambahkan baik persegi panjang maupun `TextBox`.  
- **Z‑order matters**: Gunakan `shape.moveToFront()` atau `shape.moveToBack()` untuk mengontrol shape mana yang muncul di atas.  
- **Performance**: Menambahkan ratusan shape dapat memperlambat. Kelompokkan mereka dalam satu section, lalu panggil `document.updatePageLayout()` sekali di akhir.

## Ringkasan

Kami telah membahas cara **membuat bentuk persegi panjang** dalam dokumen Word menggunakan Java, cara **menambahkan bayangan pada shape**, dan cara **menyimpan dokumen Word** dengan hasilnya. Kode lengkap yang dapat dijalankan terdapat dalam potongan di atas, dan Anda kini memahami “mengapa” di balik setiap properti—sehingga Anda dapat menyesuaikan warna, blur, dan offset sesuai desain apa pun.

Siap untuk tantangan berikutnya? Cobalah menggabungkan persegi panjang dengan diagram, atau ekspor file sebagai PDF dan lihat bagaimana bayangan ditampilkan. Anda juga dapat menjelajahi **menambahkan bentuk persegi panjang** di dalam tabel untuk tata letak laporan yang menarik.

Selamat coding, semoga dokumen Anda selalu tampak setajam kode Anda!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}