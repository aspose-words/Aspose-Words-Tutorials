---
category: general
date: 2026-07-06
description: Buat bentuk persegi panjang di Java menggunakan Aspose.Words – pelajari
  cara menambahkan bayangan pada bentuk, mengatur transparansi bentuk, dan menyimpan
  dokumen sebagai PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: id
og_description: Buat bentuk persegi panjang di Java dengan Aspose.Words. Panduan ini
  menunjukkan cara menambahkan bayangan pada bentuk, mengatur transparansi bentuk,
  dan menyimpan dokumen sebagai PDF.
og_title: Buat bentuk persegi panjang di Java – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Membuat bentuk persegi panjang di Java dengan Aspose.Words – Panduan Lengkap
url: /id/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Bentuk Persegi Panjang di Java dengan Aspose.Words – Panduan Lengkap

Pernah bertanya‑tanya bagaimana cara **create rectangle shape** di Java tanpa berurusan dengan API menggambar tingkat rendah? Anda tidak sendirian. Banyak pengembang membutuhkan cara cepat dan andal untuk menambahkan persegi panjang ke dokumen Word, memberi bayangan halus, menyesuaikan transparansinya, dan kemudian mengirimkan hasilnya sebagai PDF.  

Dalam tutorial ini kami akan membahas langkah demi langkah—dengan kode lengkap yang dapat dijalankan. Pada akhir tutorial Anda akan tahu **how to add shadow** ke sebuah shape, cara **set shape transparency**, dan cara **save document as PDF** menggunakan Aspose.Words untuk Java. Tanpa basa‑basi, hanya panduan praktis yang dapat Anda salin‑tempel ke proyek Anda hari ini.

## Apa yang Akan Anda Pelajari

- Pengaturan minimal yang diperlukan untuk bekerja dengan Aspose.Words dalam proyek Java.  
- Cara **create rectangle shape** secara programatis.  
- Panggilan tepat yang diperlukan untuk **add shadow to shape** serta menyesuaikan blur, offset, dan opacity.  
- Cara **set shape transparency** sehingga persegi panjang menyatu dengan konten di sekitarnya.  
- Metode paling sederhana untuk **save document as PDF** tanpa langkah konversi tambahan.  

Jika Anda sudah nyaman dengan Java dasar dan memiliki build Maven atau Gradle, Anda siap memulai.

## Prasyarat

- Java 8 atau yang lebih baru.  
- Aspose.Words untuk Java 23.x (atau versi terbaru pada saat Anda membaca).  
- IDE atau alat build baris perintah (IntelliJ, Eclipse, Maven, Gradle—pilih yang Anda suka).  

> **Pro tip:** Aspose menawarkan lisensi sementara gratis untuk evaluasi. Dapatkan dari portal akun Anda dan letakkan file `license.xml` ke dalam classpath; jika tidak, Anda akan melihat watermark pada PDF.

---

## Langkah 1: **Create rectangle shape** dengan Aspose.Words

Hal pertama yang kita butuhkan adalah sebuah `Document` kosong dan `DocumentBuilder`. Builder adalah tenaga utama yang memungkinkan kita menyisipkan shape langsung ke alur dokumen.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Why this matters:** `ShapeType.RECTANGLE` memberi tahu Aspose bahwa kita menginginkan persegi panjang yang sempurna. Lebar dan tinggi dinyatakan dalam poin (1 pt ≈ 1/72 in), yang memberi Anda kontrol detail atas ukuran akhir.

---

## Langkah 2: **Add shadow to shape**

Sekarang kita sudah memiliki persegi panjang, mari beri bayangan jatuh yang halus. Objek `ShadowFormat` menyediakan semua yang kita perlukan—radius blur, offset X/Y, dan bahkan transparansi.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Why this matters:** Bayangan tanpa blur terlihat seperti garis keras, yang jarang diinginkan desainer. Pemanggilan `setBlur` melunakkan tepi, sementara `setTransparency` membuat bayangan memudar ke latar belakang. Sesuaikan nilai‑nilai ini agar sesuai dengan pedoman UI Anda.

---

## Langkah 3: **Set shape transparency**

Kadang‑kadang Anda memerlukan persegi panjang itu sendiri menjadi semi‑transparent—mungkin untuk menempatkan logo atau watermark. Aspose membuatnya menjadi satu baris kode.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Why this matters:** Transparansi dapat menjadi penyelamat ketika Anda menumpuk shape. Perhatikan bahwa transparansi bayangan bersifat independen, sehingga Anda dapat memiliki shape yang redup dengan bayangan yang lebih gelap bila itu cocok dengan desain Anda.

---

## Langkah 4: **Save document as PDF**

Semua pekerjaan visual telah selesai; langkah terakhir adalah menyimpan dokumen. Aspose.Words dapat menulis langsung ke PDF, menghilangkan kebutuhan akan pustaka konversi terpisah.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Why this matters:** Dengan menentukan `SaveFormat.PDF`, pustaka menangani penyematan font, kompresi gambar, dan kepatuhan PDF/A di balik layar. File yang dihasilkan siap untuk distribusi, pencetakan, atau pengarsipan.

---

## Contoh Lengkap yang Dapat Dijalankan

Menggabungkan semuanya, berikut kelas lengkap yang siap dijalankan. Salin‑tempel, sesuaikan folder output, dan Anda akan memiliki PDF dengan persegi panjang yang menghasilkan bayangan realistis.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Expected output:** Saat Anda membuka `RectangleWithShadow.pdf`, Anda akan melihat persegi panjang abu‑abu muda yang terpusat di halaman pertama, terangkat ringan dari halaman oleh bayangan semi‑transparent yang lembut. Shape itu sendiri memiliki transparansi 20 %, memungkinkan teks di bawahnya (jika Anda menambahkannya) terlihat sedikit.

---

## Pertanyaan Umum & Kasus Tepi

### 1️⃣ Bagaimana jika saya membutuhkan persegi panjang yang lebih besar?

Cukup ubah parameter lebar dan tinggi pada `insertShape`. Ingat bahwa 72 pt = 1 in, jadi `400.0, 200.0` akan memberi Anda persegi panjang berukuran 5,5 × 2,8 inci.

### 2️⃣ Bisakah saya menggunakan warna berbeda untuk bayangan?

Tentu saja. Kelas `ShadowFormat` juga menyediakan `setColor(java.awt.Color)`. Untuk bayangan abu‑abu halus, coba `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ Apakah `save document as pdf` berfungsi di semua platform?

Ya. Aspose.Words untuk Java bersifat platform‑agnostik; kode yang sama berjalan di Windows, macOS, dan Linux selama Anda memiliki JRE yang kompatibel.

### 4️⃣ Bagaimana cara menghapus bayangan nanti?

Panggil `rect.getShadowFormat().clear();` atau set properti `Visible` menjadi `false` (`shadow.setVisible(false);`).

### 5️⃣ Bagaimana dengan DPI dan kualitas gambar?

Saat menyimpan ke PDF, Aspose secara otomatis menggunakan 300 DPI untuk grafis vektor seperti shape, sehingga Anda mendapatkan hasil yang tajam terlepas dari tingkat zoom.

---

## Pro Tips & Praktik Terbaik

- **Batch processing:** Jika Anda perlu menghasilkan puluhan PDF, gunakan kembali satu instance `Document` dan hanya bersihkan bagiannya di antara iterasi untuk mengurangi tekanan GC.  
- **Licensing:** Letakkan `License license = new License(); license.setLicense("license.xml");` di awal `main` untuk menghindari watermark evaluasi.  
- **Performance:** Rendering bayangan murah untuk shape sederhana, tetapi jalur kompleks dapat memperlambat pembuatan PDF. Lakukan profiling jika Anda memproses batch besar.  
- **Testing:** Gunakan `Document.save(..., SaveFormat.DOCX)` terlebih dahulu untuk memverifikasi bahwa shape muncul dengan benar di Word sebelum mengonversi ke PDF.

---

## Kesimpulan

Anda kini tahu cara **create rectangle shape** di Java dengan Aspose.Words, **add shadow to shape**, **set shape transparency**, dan akhirnya **save document as PDF**. Kode ini berdiri sendiri, bekerja dengan pustaka Aspose terbaru, dan memperlihatkan panggilan API penting yang Anda perlukan untuk sebagian besar skenario otomasi dokumen.

Siap untuk tantangan berikutnya? Coba ganti persegi panjang dengan elips, bereksperimen dengan isian gradien, atau jelajahi cara **add shadow** ke frame teks. Prinsip yang sama berlaku, dan API Aspose membuatnya terasa seperti sepotong kue.

Selamat coding, dan jangan ragu meninggalkan komentar jika Anda menemui kendala!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara menyimpan dokumen sebagai pdf dengan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}