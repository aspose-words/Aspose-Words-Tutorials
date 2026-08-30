---
category: general
date: 2026-07-03
description: Buat bentuk persegi panjang di Java dan pelajari cara menambahkan bayangan
  ke bentuk, menerapkan efek bayangan, mengatur transparansi bentuk, serta membuat
  dokumen kosong dengan cepat.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: id
og_description: Buat bentuk persegi panjang di Java dengan bayangan, transparansi,
  dan dokumen kosong. Ikuti panduan ini untuk menguasai penanganan bentuk.
og_title: Buat bentuk persegi panjang di Java – Tutorial Pemrograman Lengkap
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Buat bentuk persegi panjang di Java – Panduan Lengkap Langkah demi Langkah
url: /id/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat bentuk persegi panjang di Java – Panduan Lengkap Langkah‑per‑Langkah

Pernah bertanya-tanya bagaimana cara **create rectangle shape** dalam dokumen Word menggunakan Java? Anda tidak sendirian—para pengembang sering membutuhkan cara cepat untuk menambahkan grafik geometris, lalu memberi bayangan halus agar tata letak terasa lebih rapi. Dalam tutorial ini kami akan membahas seluruh proses: mulai dari membuat **create blank document** hingga **add shadow to shape**, **apply shadow effect**, dan bahkan **set shape transparency** untuk tampilan profesional.

Potongan kode di bawah ini adalah contoh yang berfungsi penuh dan dapat Anda salin‑tempel ke dalam proyek Anda. Tidak memerlukan dokumentasi eksternal—cukup ikuti langkah‑langkahnya, pahami “mengapa,” dan Anda akan menghasilkan persegi panjang dengan bayangan dalam hitungan detik.

## Apa yang Akan Anda Pelajari

- Cara **create rectangle shape** secara programatis dengan Aspose.Words for Java.
- Panggilan tepat yang diperlukan untuk **add shadow to shape** dan mengonfigurasi properti visualnya.
- Cara **apply shadow effect** serta menyesuaikan parameter seperti offset, blur radius, dan warna.
- Teknik **set shape transparency** untuk tampilan yang lebih halus.
- Cara **create blank document**, menyisipkan bentuk, dan menyimpan hasilnya.

> **Tips pro:** Semua tindakan ini dilakukan pada satu instance `Document`, yang berarti Anda dapat menautkannya secara berurutan tanpa khawatir tentang I/O file menengah.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- Java 17 (atau JDK terbaru) terpasang.
- Perpustakaan Aspose.Words for Java ditambahkan ke proyek Anda (koordinat Maven: `com.aspose:aspose-words:23.12`).
- IDE Java atau editor teks sederhana—tidak perlu yang canggih, cukup tempat untuk mengompilasi dan menjalankan.

Jika ada yang belum ada, unduh JDK dari Oracle dan tambahkan dependensi Aspose melalui Maven atau Gradle. Setelah itu, Anda siap melanjutkan.

## Langkah 1: **Create blank document** – kanvas untuk semuanya

Hal pertama yang Anda butuhkan adalah objek `Document` kosong. Anggap saja ini sebagai lembar kertas baru; tanpa itu, tidak ada tempat untuk menaruh persegi panjang Anda.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Mengapa memulai dengan dokumen kosong? Karena setiap bentuk berada di dalam sebuah `Section`, dan `Document` yang baru di‑instansiasi sudah berisi section default dengan body yang siap menerima node. Melewatkan langkah ini akan memaksa Anda membuat section secara manual nanti, yang menambah kompleksitas yang tidak perlu.

## Langkah 2: **Create rectangle shape** dan tentukan ukurannya

Setelah kita memiliki kanvas, mari **create rectangle shape**. Kelas `Shape` menerima referensi dokumen dan sebuah `ShapeType`. Di sini kita pilih `RECTANGLE` dan mengatur lebar/tinggi dalam poin (1 pt ≈ 1/72 inci).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Mengapa mengatur `WrapType.INLINE`? Pembungkus inline membuat bentuk berperilaku seperti karakter dalam paragraf, memastikan ia bergerak bersama teks di sekitarnya. Jika Anda membutuhkan perilaku mengambang, ubah menjadi `WrapType.SQUARE` atau `WrapType.TOP_BOTTOM`.

## Langkah 3: **Apply shadow effect** – beri kedalaman pada persegi panjang

Persegi panjang datar terlihat… ya, datar. Menambahkan bayangan membuatnya menonjol. Kami akan **apply shadow effect** dengan membuat instance `ShadowEffect`, lalu menyesuaikan properti visualnya.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Mari kita uraikan sedikit:

- **Color** – `Color.getGray(0.5)` menghasilkan abu‑abu 50 %, yang netral dan cocok pada kebanyakan latar belakang.
- **OffsetX/Y** – Nilai positif menggeser bayangan ke kanan dan ke bawah; nilai negatif akan memindahkannya ke kiri/atas.
- **BlurRadius** – Nilai yang lebih besar menghasilkan bayangan yang lebih lembut dan tersebar.
- **Transparency** – Berkisar dari `0` (opaque) hingga `1` (sepenuhnya transparan). Di sini kami memilih `0.3` untuk efek yang halus.

## Langkah 4: **Add shadow to shape** – kaitkan efeknya

Membuat efek saja tidak cukup; kita harus **add shadow to shape** dengan menetapkan objek `ShadowEffect` ke persegi panjang.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Di balik layar, pemanggilan ini memperbarui markup OpenXML dasar (`<w:shdw>`) yang digunakan Word untuk merender bayangan. Jika Anda memeriksa file `.docx` yang disimpan, akan terlihat elemen `<w:effect>` yang terisi dengan parameter yang kami set.

## Langkah 5: **Set shape transparency** – opsional namun sering berguna

Kadang‑kadang Anda ingin persegi panjang itu sendiri semi‑transparent, sehingga teks latar belakang tetap terlihat. Kelas `Shape` menyediakan `setFillColor` dan `setFillTransparency`. Berikut contoh singkat yang membuat persegi panjang 40 % transparan:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Mengapa melakukan ini? Bayangkan sebuah watermark atau call‑out yang disorot di mana konten di bawahnya harus tetap dapat dibaca. Sesuaikan nilai transparansi sesuai bahasa desain Anda.

## Langkah 6: Sisipkan bentuk ke dalam dokumen

Kami telah membangun persegi panjang, menambahkan bayangan, dan (opsional) mengatur transparansinya. Langkah akhir adalah **add the shape to the first section of the document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Menambahkan bentuk ke body menempatkannya di akhir paragraf pertama. Jika Anda memerlukan titik sisipan khusus, ambil `Paragraph` target dan gunakan `insertBefore` atau `insertAfter`.

## Langkah 7: Simpan dokumen – lihat hasilnya

Semua kerja keras tersebut berujung pada satu pemanggilan `save`. Pilih jalur yang masuk akal untuk lingkungan Anda.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Buka `ShadowShape.docx` yang dihasilkan di Microsoft Word atau LibreOffice, dan Anda akan melihat persegi panjang yang tajam dengan bayangan abu‑abu lembut, sedikit transparan jika Anda mengikuti langkah opsional. Visualnya sesuai dengan parameter yang kami definisikan secara programatis.

---

![buat bentuk persegi panjang dengan bayangan dalam dokumen Word](https://example.com/images/rectangle-shadow.png "buat bentuk persegi panjang dengan bayangan")

*Teks alt gambar:* **create rectangle shape with shadow** – representasi visual dari output akhir.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya ingin warna bayangan yang berbeda?

Cukup ubah pemanggilan `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Ingat bahwa bayangan yang terlalu mencolok dapat terlihat tidak profesional; nada yang halus biasanya lebih cocok.

### Bisakah saya menerapkan bayangan yang sama ke beberapa bentuk?

Ya. Buat satu instance `ShadowEffect`, konfigurasikan, lalu gunakan kembali:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Hanya hindari memodifikasi `ShadowEffect` setelah Anda menautkannya ke bentuk lain, kecuali Anda memang ingin memperbarui semuanya.

### Bagaimana cara mengubah blur bayangan secara dinamis?

Sediakan slider UI yang memetakan ke `setBlurRadius`. Nilai antara `2` dan `12` biasanya cukup; angka yang lebih besar menghasilkan “glow” alih‑alih bayangan yang tajam.

### Bagaimana jika saya membutuhkan bentuk mengambang bukan inline?

Ganti tipe pembungkus:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Bentuk mengambang memberi Anda kebebasan tata letak lebih, tetapi memerlukan logika posisi tambahan.

## Contoh Kerja Lengkap

Berikut adalah program lengkap yang siap disalin‑tempel dan mencakup semua langkah yang telah dibahas. Jalankan sebagai aplikasi Java biasa.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Output yang diharapkan:** Saat Anda membuka `ShadowShape.docx`, akan terlihat persegi panjang putih, 200 × 100 pt, berada di tengah paragraf pertama, dengan bayangan abu‑abu sedang yang bergeser 5 pt, blur radius 8, dan transparansi 30 %. Persegi panjang itu sendiri 40 % transparan, memungkinkan teks di bawahnya terlihat sekilas.

## Penutup

Kami baru saja **create rectangle shape** dari awal, **add shadow to shape**, **apply shadow effect**, dan bahkan **set shape transparency**—semua sambil **create blank document** sebagai fondasi. Pendekatannya sederhana, mengandalkan API fluida Aspose.Words, dan dapat diperluas ke lingkaran, bintang, atau poligon khusus.

Apa langkah selanjutnya dalam roadmap Anda? Coba ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL` untuk menghasilkan lingkaran berbayangan, atau bereksperimen dengan isian gradien untuk


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}