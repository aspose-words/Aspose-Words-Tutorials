---
category: general
date: 2026-06-30
description: Buat contoh Java dokumen Word yang menunjukkan cara menambahkan bentuk
  ke dokumen Word, mengatur warna isi bentuk, dan menerapkan efek bayangan pada bentuk
  hanya dalam beberapa baris.
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: id
og_description: Buat tutorial Java dokumen Word yang menunjukkan cara menambahkan
  bentuk ke dokumen Word, mengatur warna isi bentuk, dan menerapkan efek bayangan
  pada bentuk.
og_title: Buat Dokumen Word Java – Tambahkan Bentuk dengan Efek Bayangan
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: Buat Dokumen Word Java – Tambahkan Bentuk dengan Efek Bayangan
url: /id/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word Java – Tambahkan Bentuk dengan Efek Bayangan

Pernah membutuhkan kode **create word document java** yang menggambar sebuah persegi panjang dan memberikan bayangan halus? Anda bukan satu-satunya. Baik Anda membuat laporan, faktur, atau selebaran sederhana, kemampuan untuk **add shape to word document** secara programatik menghemat berjam‑jam penyesuaian manual.  

Dalam panduan ini kami akan menelusuri contoh lengkap yang siap dijalankan yang tidak hanya membuat file Word baru, tetapi juga **set shape fill color**, **how to add shadow to shape**, dan akhirnya **apply shadow effect shape** dengan Aspose.Words for Java. Tanpa basa‑basi—hanya langkah‑langkah tepat yang dapat Anda salin‑tempel ke IDE Anda.

> **Pro tip:** Jika Anda baru mengenal Aspose.Words, pastikan Anda memiliki JAR terbaru di classpath Anda. API yang kami gunakan bekerja dengan versi 23.10 dan lebih baru.

## Apa yang Akan Anda Bangun

Pada akhir tutorial ini Anda akan memiliki file `.docx` yang berisi:

* Sebuah dokumen Word kosong yang dibuat dari awal.
* Sebuah persegi panjang kuning (150 × 80 pts) disisipkan ke halaman pertama.
* Bayangan abu‑abu lembut yang digeser beberapa poin, memberikan tampilan bentuk yang terangkat.
* Semua hal di atas dicapai hanya dengan beberapa pernyataan Java.

Tanpa templat eksternal, tanpa XML yang rumit—kode Java murni yang dapat dijalankan siapa saja.

---

## Buat Dokumen Word Java – Sisipkan Bentuk

Hal pertama yang kita butuhkan adalah objek `Document` baru dan `DocumentBuilder`. Anggap builder sebagai pena yang memungkinkan kita menggambar di dalam dokumen.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting:* `Document` mewakili seluruh file, sementara `DocumentBuilder` memberi kita metode praktis seperti `insertShape`. Tanpa builder kita harus memanipulasi node tingkat‑rendah secara langsung—lebih banyak pekerjaan.

## Tambahkan Bentuk ke Dokumen Word – Menambahkan Persegi Panjang

Sekarang kita benar‑benar **add shape to word document**. Dalam kasus kami itu adalah persegi panjang, tetapi Anda dapat memilih `ShapeType` apa pun yang didukung Aspose (elips, panah, dll.).

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

Baris tunggal itu melakukan tiga hal:

1. Membuat objek shape.  
2. Menempatkannya pada lokasi kursor saat ini (pojok kiri‑atas halaman secara default).  
3. Menambahkannya ke koleksi node internal dokumen.

Jika Anda pernah bertanya-tanya *how to add shadow to shape* setelah ini, terus baca—karena kami akan membahasnya selanjutnya.

## Atur Warna Isi Bentuk – Menyesuaikan Penampilan

Sebuah persegi panjang putih polos tidak terlalu menarik, jadi mari **set shape fill color** ke sesuatu yang cerah. Kami akan menggunakan kelas `java.awt.Color` milik Java, yang diterima langsung oleh Aspose.

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

Silakan ganti `YELLOW` dengan `RED`, `GREEN`, atau nilai RGB kustom apa pun (`new Color(123, 45, 67)`). Warna isi adalah permukaan yang akan Anda lihat sebelum bayangan muncul.

## Cara Menambahkan Bayangan ke Bentuk – Mengonfigurasi Bayangan

Inilah tempat keajaiban terjadi. Aspose.Words menyediakan objek `ShadowEffect` yang memungkinkan kita menyesuaikan tampilan bayangan secara detail.

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**Mengapa setiap properti penting:**

| Properti | Apa fungsinya | Nilai tipikal |
|----------|---------------|----------------|
| `setColor` | Menentukan warna bayangan. Abu‑abu bekerja untuk kebanyakan kasus, tetapi Anda dapat menggunakan warna berani seperti `Color.BLUE`. | Any `java.awt.Color` |
| `setBlurRadius` | Mengontrol seberapa lembut tepi terlihat. Angka yang lebih besar memberikan tampilan yang lebih menyebar. | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | Memindahkan bayangan ke kanan/kiri dan atas/bawah. Nilai positif menggeser bayangan ke kanan‑bawah. | -10 – 10 |
| `setTransparency` | Menetapkan transparansi; 0 solid, 1 tidak terlihat. | 0.0 – 1.0 |

Jika Anda bertanya-tanya **how to add shadow to shape** tanpa mengacaukan tata letak, kuncinya adalah menjaga offset tetap wajar. Terlalu besar dan bayangan dapat meluber ke halaman berikutnya.

## Terapkan Bayangan pada Bentuk – Menyimpan Dokumen

Dengan bentuk yang telah diatur gaya dan bayangan yang dikonfigurasi, kita hanya perlu menyimpan file.

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang ada di mesin Anda. Setelah menjalankan program, buka `ShadowShape.docx` di Microsoft Word atau LibreOffice—Anda akan melihat persegi panjang kuning mengambang di atas halaman, berkat bayangan abu‑abu yang kami terapkan.

---

## Verifikasi Hasil – Apa yang Harus Diperhatikan

Saat Anda membuka file yang dihasilkan:

* Persegi panjang harus berada di posisi di mana kursor mulai (pojok kiri‑atas halaman secara default).
* Isinya berwarna kuning cerah.
* Bayangan abu‑abu halus berada 4 pts ke kanan dan ke bawah, dengan transparansi sekitar 30 %.

Jika bayangan terlihat terlalu keras, turunkan `BlurRadius` atau tingkatkan `Transparency`. Jika bentuk itu sendiri tidak terlihat, periksa kembali pemanggilan `setFillColor`—mungkin warna yang Anda pilih menyatu dengan latar belakang halaman.

---

## Kesalahan Umum & Kasus Tepi

| Masalah | Penyebab | Solusi |
|---------|----------|--------|
| **Shadow disappears** | `Transparency` diatur ke `1.0` (sepenuhnya transparan). | Gunakan nilai yang lebih rendah, misalnya `0.3`. |
| **Shape not visible** | Warna isi cocok dengan latar belakang halaman (biasanya putih). | Pilih warna kontras dengan `setFillColor`. |
| **Shadow clips on page margin** | Offset mendorong bayangan keluar area cetak. | Kurangi `OffsetX`/`OffsetY` atau perbesar margin halaman melalui `PageSetup`. |
| **Compilation error: `cannot find symbol ShadowEffect`** | Menggunakan versi Aspose.Words yang lebih lama yang tidak mendukung bayangan. | Upgrade ke Aspose.Words 23.10+ (API memperkenalkan `ShadowEffect` pada 22.12). |

---

## Langkah Selanjutnya – Melampaui Dasar

Sekarang Anda tahu cara **create word document java**, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, dan **apply shadow effect shape**, Anda mungkin bertanya-tanya apa lagi yang dapat Anda lakukan. Berikut beberapa ide:

* **Warna dinamis** – Ambil nilai RGB dari basis data untuk memberi kode warna pada bentuk berdasarkan status.  
* **Multiple shadows** – Tumpuk dua konfigurasi `ShadowEffect` dengan menggandakan bentuk dan menggeser setiap salinan.  
* **Teks di dalam bentuk** – Gunakan `Shape.getTextFrame()` untuk menyisipkan keterangan atau label.  
* **Ekspor ke PDF** – Panggil `document.save("output.pdf", SaveFormat.PDF)` untuk mendapatkan versi siap cetak dengan fidelitas visual yang sama.  

Masing‑masing dari ini dibangun di atas pola inti yang kami tunjukkan: membuat dokumen, menyisipkan bentuk, memberi gaya, dan menyimpan.

---

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

Menjalankan kelas menghasilkan `ShadowShape.docx` di direktori kerja saat ini. Buka file tersebut, dan Anda akan melihat hasil tepat seperti yang dijelaskan sebelumnya.

---

## Kesimpulan

Kami baru saja menunjukkan cara **create word document java** dari awal, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, dan akhirnya **apply shadow effect shape**—semua dengan contoh kode yang ringkas dan mudah dipahami.  

Pendekatan ini sengaja sederhana sehingga Anda dapat menyesuaikannya dengan skenario yang lebih kompleks—baik Anda membutuhkan banyak bentuk, warna berbeda, atau bayangan gaya animasi. Ingat untuk selalu memeriksa kompatibilitas versi API, dan jangan ragu mengubah parameter bayangan agar sesuai dengan bahasa desain Anda.  

Ada variasi yang Anda coba? Mungkin Anda menempatkan gambar di belakang persegi panjang atau menambahkan tabel di dalam bentuk. Tinggalkan komentar di bawah; saya senang mendengar bagaimana pengembang mengembangkan contoh ini lebih jauh. Selamat coding


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara Membuat Dokumen PDF dengan Aspose.Words untuk Java | API Pemrosesan Dokumen](/words/english/java/)
- [Aspose.Words Java: Panduan Komprehensif untuk Pemrosesan Dokumen Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}