---
category: general
date: 2026-05-26
description: Buat bentuk persegi panjang dalam dokumen Word Java dan terapkan efek
  bayangan. Pelajari cara menambahkan bayangan pada bentuk, mengatur jarak bayangan,
  dan menyimpan file.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: id
og_description: Buat bentuk persegi panjang dalam dokumen Word Java, terapkan efek
  bayangan, tambahkan bayangan bentuk, dan atur jarak bayangan dengan Aspose.Words.
og_title: Buat Bentuk Persegi Panjang di Dokumen Word Java – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Membuat Bentuk Persegi Panjang di Dokumen Word Java – Panduan Lengkap Langkah
  demi Langkah
url: /id/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Bentuk Persegi Panjang di Dokumen Word Java – Panduan Langkah-demi-Langkah Lengkap

Pernah membutuhkan untuk **create rectangle shape** di dokumen Word Java tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami kendala ini saat menghasilkan laporan atau faktur secara programatis. Dalam tutorial ini kami akan menjelaskan secara tepat cara **create rectangle shape**, menerapkan bayangan yang halus, dan menyesuaikan jarak bayangan sehingga hasilnya terlihat profesional.

Kami akan menggunakan Aspose.Words for Java, sebuah pustaka kuat yang memungkinkan Anda memanipulasi file Word tanpa perlu menginstal Microsoft Office. Pada akhir panduan ini Anda akan dapat membuat proyek **create word document java** yang **add shape shadow**, **apply shadow effect**, dan **set shadow distance** hanya dengan beberapa baris kode.

---

## Apa yang Akan Anda Bangun

- File `.docx` baru yang berisi persegi panjang berwarna sian.
- Bayangan jatuh realistis yang kabur, miring, dan sebagian transparan.
- Kontrol penuh atas jarak bayangan dari bentuk.
- Kelas Java siap‑jalankan yang dapat Anda masukkan ke proyek Maven atau Gradle mana pun.

Tanpa alat eksternal, tanpa langkah UI manual—hanya kode murni.

---

## Prasyarat

- Java 8 atau lebih baru (kode ini bekerja pada Java 11, Java 17, dll.).
- Pustaka Aspose.Words for Java (tersedia melalui Maven Central).
- IDE atau editor teks yang Anda sukai (IntelliJ IDEA, Eclipse, VS Code…).
- Pemahaman dasar tentang sintaks Java.

Jika Anda belum pernah menambahkan dependensi Maven sebelumnya, berikut cuplikan singkatnya:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Sekarang, mari kita mulai.

---

## Langkah 1: Buat Bentuk Persegi Panjang di Dokumen Word

Hal pertama yang kita butuhkan adalah dokumen kosong dan `DocumentBuilder`. Anggap builder sebagai pena yang menulis ke dalam dokumen. Setelah kita memiliki itu, kita dapat **create rectangle shape** dengan satu panggilan metode.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Mengapa ini penting:** Metode `insertShape` tidak hanya membuat geometri tetapi juga menambahkan bentuk ke koleksi internal dokumen, sehingga Anda dapat langsung mulai menata tampilannya.

---

## Langkah 2: Terapkan Efek Bayangan ke Bentuk

Sekarang persegi panjang berada di halaman, kita akan **apply shadow effect**. Bayangan memberikan kedalaman, membuat bentuk terasa seolah terangkat dari halaman—peningkatan UI halus yang dapat meningkatkan keterbacaan dalam laporan.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Tip pro:** Blur `5.0` terlihat alami untuk kebanyakan dokumen yang ditampilkan di layar. Jika Anda mencetak, Anda mungkin menginginkan nilai sedikit lebih rendah untuk menghindari tampilan kabur.

---

## Langkah 3: Atur Jarak Bayangan – Penyetelan Penempatan

Bayangan bukan hanya tentang blur; mereka juga membutuhkan offset yang tepat. Di sinilah kita **set shadow distance**. Jarak `7.0` poin menghasilkan offset sedang yang terlihat namun tidak berlebihan.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Bagaimana jika Anda membutuhkan offset yang lebih besar?** Tingkatkan nilai; turunkan untuk tampilan yang lebih ketat. Ingat, jarak bekerja bersama dengan sudut untuk menempatkan bayangan dengan benar.

---

## Langkah 4: Simpan Dokumen – Simpan Pekerjaan Anda

Akhirnya, kami menulis dokumen ke disk. Ubah path ke lokasi mana pun Anda ingin file tersebut disimpan.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Menjalankan kelas akan membuat file `shadow.docx` yang, ketika dibuka di Microsoft Word atau LibreOffice, menampilkan persegi panjang sian dengan bayangan abu-abu lembut yang miring 45° dan offset sebesar 7 poin.

---

## Contoh Kerja Lengkap

Berikut adalah kode lengkap yang siap disalin‑tempel. Kode ini mencakup semua impor, komentar, dan pemanggilan `save` akhir.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Output yang diharapkan:** Buka `shadow.docx` → Anda akan melihat persegi panjang sian terpusat di halaman pertama, memancarkan bayangan abu-abu halus yang sedikit offset ke kanan‑bawah. Blur dan transparansi bayangan membuatnya tampak seperti pencahayaan alami.

---

## Pertanyaan Umum & Kasus Tepi

### “Bisakah saya menggunakan bentuk lain?”

Tentu saja. Ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL`, `ShapeType.LINE`, atau enum lain yang didukung. Sisanya kode bayangan tetap sama.

### “Bagaimana jika saya membutuhkan beberapa bayangan?”

Aspose.Words hanya mendukung satu bayangan per bentuk. Untuk mensimulasikan beberapa bayangan, duplikat bentuk, offset setiap salinan, dan sesuaikan transparansi.

### “Apakah bayangan terlihat di LibreOffice?”

Ya—Aspose.Words menulis OOXML standar, yang diinterpretasikan LibreOffice dengan benar. Bayangan mungkin terlihat sedikit berbeda karena mesin rendering, tetapi efeknya tetap ada.

### “Bagaimana cara mengubah warna bayangan agar sesuai dengan merek saya?”

Cukup ganti `java.awt.Color.GRAY` dengan `java.awt.Color` apa pun yang Anda inginkan, misalnya `new java.awt.Color(0, 120, 215)` untuk biru korporat.

---

## Ilustrasi Gambar

![buat bentuk persegi panjang di dokumen Word Java](https://example.com/images/rectangle-shadow.png)

*Teks alt:* **create rectangle shape** ilustrasi yang menunjukkan persegi panjang sian dengan bayangan jatuh abu-abu dalam dokumen Word.

---

## Ringkasan & Langkah Selanjutnya

Kami telah membahas cara **create rectangle shape**, **apply shadow effect**, **add shape shadow**, dan **set shadow distance** menggunakan Aspose.Words for Java. Kode ini mandiri, berjalan pada JDK modern apa pun, dan menghasilkan file `.docx` yang halus siap didistribusikan.

Ingin melangkah lebih jauh? Coba:

- Menambahkan teks di dalam persegi panjang dengan `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Membuat tabel bentuk untuk membangun diagram.
- Mengekspor dokumen ke PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Setiap hal ini dibangun di atas dasar yang sama yang baru saja kami jelajahi, sehingga Anda akan merasa nyaman memperluas contoh ini.

---

## Pemikiran Akhir

Menguasai tugas **create word document java** seperti membentuk dan memberi bayangan memberi Anda keunggulan besar saat mengotomatisasi laporan, kontrak, atau materi pemasaran. Pendekatan yang ditunjukkan di sini bersih, dapat dipelihara, dan—yang terpenting—mudah disesuaikan untuk gaya visual apa pun yang Anda butuhkan.

Jalankan kode tersebut, sesuaikan blur, sudut, dan jarak, dan saksikan dokumen Anda bertransformasi dari biasa menjadi halus. Jika Anda menemui kendala, tinggalkan komentar di bawah; saya senang membantu.

Selamat coding!

## Tutorial Terkait

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Buat PDF dari Word dengan Generasi Barcode – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}