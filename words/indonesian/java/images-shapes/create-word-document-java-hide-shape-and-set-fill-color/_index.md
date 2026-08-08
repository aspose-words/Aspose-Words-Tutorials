---
category: general
date: 2026-08-07
description: 'Buat dokumen Word Java dengan Aspose.Words: sisipkan elips, atur warna
  isi bentuk, dan sembunyikan bentuk di Word menggunakan contoh singkat.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: id
lastmod: 2026-08-07
og_description: Buat dokumen Word Java dengan Aspose.Words. Pelajari cara menyisipkan
  bentuk, mengatur warna isi, dan menyembunyikan bentuk di Word—semua dalam satu contoh
  yang dapat dijalankan.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Buat dokumen Word Java – sembunyikan bentuk dan atur warna isi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Buat dokumen Word Java – sembunyikan bentuk dan atur warna isi
url: /id/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen word java – sembunyikan bentuk dan atur warna isi

Jika Anda perlu **create word document java** dengan penanganan bentuk secara programatik, tutorial ini akan menunjukkan caranya. Anda akan belajar cara menyisipkan sebuah bentuk, mengatur warna isi, dan menyembunyikan bentuk di Word menggunakan Aspose.Words for Java.

Panduan ini mencakup setiap langkah mulai dari menginisialisasi objek `Document` hingga memverifikasi bahwa bentuk tidak terlihat saat file dibuka. Tidak ada sumber daya eksternal yang diperlukan selain pustaka Aspose.Words, dan kode sumber lengkap disediakan sehingga Anda dapat menjalankannya segera.

**Prerequisites**

- Java 8 atau lebih baru
- Maven atau Gradle untuk mengelola dependensi (atau Aspose.Words JAR pada classpath)
- Pemahaman dasar tentang sintaks Java
- IDE atau editor teks untuk pengembangan Java

Tutorial ini juga menjelaskan **how to hide shape** dalam file Word, **how to insert shape** dengan dimensi yang tepat, dan **set shape fill color** untuk gaya visual.

---

![Buat dokumen word java – pratinjau bentuk tersembunyi](image-placeholder.png){.align-center width=600 alt="Buat dokumen word java – pratinjau bentuk tersembunyi"}

## Buat dokumen word java – inisialisasi dokumen dan builder

Langkah pertama adalah membuat dokumen Word kosong dan `DocumentBuilder` yang memungkinkan Anda menambahkan konten. Menginisialisasi objek-objek ini mengalokasikan struktur internal yang dibutuhkan Aspose.Words untuk melacak halaman, paragraf, dan bentuk.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* Tanpa `DocumentBuilder` Anda tidak dapat menyisipkan bentuk, teks, atau objek lain. Builder bekerja pada instance `Document` di memori, memastikan semua perubahan tertangkap sebelum Anda menyimpan.

## Cara menyisipkan bentuk dengan Aspose.Words

Aspose.Words mendukung banyak bentuk geometris. Di sini kami menyisipkan sebuah elips dengan lebar 150 pt dan tinggi 100 pt. Metode `insertShape` mengembalikan objek `Shape` yang dapat Anda konfigurasi lebih lanjut.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Mengapa ini penting:* Menggunakan `insertShape` menjamin bahwa bentuk terpasang dengan benar dalam alur dokumen. `Shape` yang dikembalikan memungkinkan Anda mengubah properti seperti warna isi, gaya garis, dan visibilitas.

## Atur warna isi bentuk di Word

Bentuk tanpa isi terlihat transparan. Menetapkan warna isi membuat bentuk menonjol ketika terlihat. Contoh ini menggunakan `java.awt.Color.GREEN` untuk mendemonstrasikan **set shape fill color**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Mengapa ini penting:* Warna isi disimpan dalam definisi XML bentuk. Mengubahnya pada waktu berjalan memungkinkan Anda menghasilkan dokumen dengan warna khusus merek atau menyoroti wilayah penting.

## Cara menyembunyikan bentuk di Word

Terkadang Anda memerlukan bentuk yang mengatur tata letak atau berfungsi sebagai placeholder tetapi tidak boleh terlihat oleh pengguna akhir. Pemanggilan `setHidden(true)` menerapkan **how to hide shape** dan memenuhi persyaratan **hide shape in word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Mengapa ini penting:* Bentuk tersembunyi tetap menjadi bagian dari model objek dokumen, yang berarti mereka dapat dirujuk nanti (mis., untuk bookmark atau manipulasi programatik) tanpa mengacaukan tata letak visual.

## Simpan dokumen dan verifikasi hasil

Setelah mengkonfigurasi bentuk, simpan file ke disk. `.docx` yang disimpan dapat dibuka di Microsoft Word; elips akan tidak terlihat, tetapi keberadaannya dapat dikonfirmasi dengan memeriksa XML dokumen atau menggunakan Aspose.Words untuk menenumerasi bentuk.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Hasil yang diharapkan:* Membuka `ShapeVisibilityDemo.docx` menampilkan halaman normal tanpa grafik yang terlihat. Jika Anda memeriksa dokumen dengan penampil ZIP dan membuka `word/document.xml`, Anda akan menemukan elemen `<w:shape>` dengan `hidden="true"` dan `<v:fillcolor>` berwarna `#00FF00`.

---

## Variasi umum dan kasus tepi

- **Berbagai tipe bentuk:** Ganti `ShapeType.ELLIPSE` dengan `ShapeType.RECTANGLE`, `ShapeType.CLOUD`, atau nilai enum lain yang didukung untuk mencapai geometri yang diinginkan.
- **Visibilitas kondisional:** Anda dapat mengubah `ellipse.setHidden(false)` berdasarkan logika waktu jalan, memungkinkan pembuatan dokumen dinamis.
- **Isi kompleks:** Alih-alih warna solid, gunakan `ellipse.getFill().setTextureImage(...)` untuk isi pola. Metode `setHidden` yang sama tetap mengontrol visibilitas.
- **Banyak bentuk:** Buat array atau daftar objek `Shape`, konfigurasikan masing‑masing secara independen, dan sembunyikan hanya yang memenuhi kriteria tertentu.

*Tips pro:* Saat menghasilkan dokumen besar, gunakan kembali satu instance `DocumentBuilder` alih‑alih membuat yang baru untuk setiap bentuk. Ini mengurangi beban memori dan meningkatkan kinerja.

---

## Kesimpulan

Anda kini tahu cara **create word document java** yang menyisipkan sebuah elips, **set shape fill color**, dan **hide shape in word** menggunakan Aspose.Words. Contoh lengkap yang dapat dijalankan memperlihatkan setiap pemanggilan API, menjelaskan mengapa setiap langkah diperlukan, dan menampilkan hasil yang diharapkan.

Selanjutnya, jelajahi topik terkait seperti **how to insert shape** dengan pembungkus teks, menambahkan hyperlink ke bentuk, dan mengekspor dokumen ke PDF sambil mempertahankan elemen tersembunyi. Bereksperimenlah dengan warna, ukuran, dan flag visibilitas yang berbeda untuk menyesuaikan otomatisasi Word dengan kebutuhan proyek Anda.

Siap mengotomatisasi lebih banyak fitur Word? Lihat dokumentasi Aspose.Words untuk Java tentang [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) dan mulailah membuat dokumen yang lebih kaya, dihasilkan secara programatik hari ini.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Bentuk Grup dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}