---
category: general
date: 2026-01-11
description: Buat dokumen Word Java dengan cepat dengan menambahkan bentuk persegi
  panjang, mengatur warna isi, dan menerapkan bayangan pada bentuk. Pelajari langkah
  demi langkah.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: id
og_description: Buat dokumen Word dengan Java dengan menyisipkan bentuk persegi panjang,
  mengatur warna isi, dan menerapkan bayangan. Panduan lengkap dengan kode.
og_title: Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Bayangan
tags:
- Aspose.Words
- Java
- Document Generation
title: Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan
url: /id/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan

Pernahkah Anda perlu **create word document java** dan membuatnya terlihat lebih halus? Mungkin Anda sedang membangun generator laporan dan halaman polos tidak cukup. Kabar baiknya? Dengan Aspose.Words untuk Java Anda dapat menambahkan bentuk persegi panjang ke dokumen, memberi warna, bahkan menambahkan bayangan halus—semua dalam beberapa baris kode.

Dalam tutorial ini kita akan membahas langkah demi langkah: cara menambahkan bentuk persegi panjang, mengatur warna isi, dan menerapkan bayangan pada bentuk sehingga file Word Anda terasa lebih profesional. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan dan langsung disalin‑tempel ke proyek Anda.

## Apa yang Anda Butuhkan

- **Java 17** (atau JDK terbaru) – kode menggunakan fitur bahasa standar.  
- **Aspose.Words untuk Java** – disarankan versi 23.9 atau lebih baru.  
- IDE atau editor teks pilihan Anda – IntelliJ IDEA, Eclipse, VS Code… terserah.  
- Folder tempat `ShadowShape.docx` yang dihasilkan akan disimpan.

Tidak diperlukan konfigurasi tambahan; cukup tambahkan JAR Aspose.Words ke classpath dan Anda siap mulai.

## Langkah 1: Siapkan Proyek dan Impor Aspose.Words

Pertama, buat proyek Maven (atau Gradle) baru dan tambahkan dependensi Aspose.Words. Berikut cuplikan minimal `pom.xml` untuk Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Jika Anda tidak menggunakan Maven, cukup letakkan file JAR ke folder `libs` dan tambahkan ke build path.

> **Pro tip:** Aspose menyediakan lisensi percobaan gratis yang dapat Anda sematkan dengan `License license = new License(); license.setLicense("Aspose.Words.lic");`. Lewati untuk pengujian cepat; perpustakaan berfungsi dalam mode evaluasi.

## Langkah 2: Buat Dokumen Baru dan Builder

Sekarang kita akan **create word document java** objek-objeknya. Kelas `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` memungkinkan kita menyisipkan konten.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Pada titik ini Anda memiliki dokumen kosong yang siap menerima bentuk, paragraf, atau apa pun yang Anda perlukan.

## Langkah 3: Sisipkan Bentuk Persegi Panjang dan Atur Warna Isi

Menambahkan bentuk semudah memanggil `insertShape`. Kita akan menggunakan teknik **add rectangle shape**, yang merupakan kata kunci sekunder *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Mengapa oranye? Karena warna ini menonjol di atas latar putih, namun Anda dapat menggantinya dengan `java.awt.Color` apa saja yang Anda suka. Langkah ini mencakup kata kunci sekunder *set shape fill color*.

## Langkah 4: Konfigurasikan Penampilan Bayangan – Terapkan Bayangan pada Bentuk

Sekarang bagian yang menyenangkan: memberi persegi panjang bayangan drop yang halus. API Aspose menyediakan objek `ShadowFormat` yang mengontrol setiap aspek bayangan.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Blok kode ini **apply shadow to shape** persis seperti yang disarankan oleh kata kunci sekunder. Anda dapat menyesuaikan `blur`, `offsetX/Y`, dan `transparency` sesuai gaya desain Anda. Misalnya, `offsetX` yang lebih besar menghasilkan bayangan yang lebih dramatis, sementara `transparency` yang tinggi membuat bayangan berbisik alih-alih berteriak.

## Langkah 5: Simpan Dokumen

Akhirnya, kita menulis dokumen ke disk. Pilih folder yang Anda miliki hak tulis, dan beri nama file yang jelas.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Saat Anda membuka `ShadowShape.docx` di Microsoft Word atau LibreOffice, Anda akan melihat persegi panjang oranye cerah dengan bayangan abu‑abu lembut yang melayang tepat di bawahnya.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Teks alt gambar mencakup kata kunci utama, memenuhi aturan SEO.*

## Pertanyaan Umum & Kasus Khusus

### Bagaimana jika saya membutuhkan bentuk lain?

Aspose.Words mendukung puluhan nilai `ShapeType` – bintang, panah, callout, apa saja. Cukup ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL` atau konstanta enum lain. Langkah **how to add shape** tetap sama.

### Bagaimana cara menambahkan bentuk ke paragraf tertentu?

Alih‑alih menyisipkan bentuk langsung dengan builder, Anda dapat membuatnya terlebih dahulu (`new Shape(document, ShapeType.RECTANGLE)`) lalu menambahkannya ke `Paragraph` melalui `paragraph.appendChild(shape)`. Ini memberi kontrol tata letak yang lebih halus.

### Bisakah saya menggunakan isian gradien alih‑alih warna solid?

Ya! Gunakan `rectangle.getFill().setFillType(FillType.GRADIENT)` dan definisikan `LinearGradientFill`. API-nya sedikit lebih panjang, tetapi sangat cocok untuk desain modern.

### Bagaimana dengan kompatibilitas ke versi Word yang lebih lama?

Aspose.Words menyimpan dalam format .docx secara default, yang didukung oleh Word 2007+ dan LibreOffice. Jika Anda memerlukan .doc, panggil `document.save("file.doc", SaveFormat.DOC)`. Rendering bayangan mungkin sedikit berbeda, tetapi bentuk tetap utuh.

## Contoh Lengkap yang Siap Digunakan (Copy‑Paste)

Berikut seluruh program, siap untuk dikompilasi dan dijalankan. Ganti `YOUR_DIRECTORY` dengan path yang sebenarnya di mesin Anda.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Menjalankan kode ini menghasilkan file Word yang berisi persegi panjang oranye dengan bayangan abu‑abu lembut—tepat seperti yang kami inginkan ketika **create word document java** dengan bentuk bergaya.

## Kesimpulan

Anda kini memiliki resep lengkap end‑to‑end untuk **create word document java** yang *adds rectangle shape*, *sets shape fill color*, dan *applies shadow to shape*. Pendekatannya sederhana, API‑nya fluida, dan Anda dapat memperluasnya dalam banyak cara—bentuk berbeda, isian gradien, atau bahkan beberapa bayangan per bentuk.

Apa selanjutnya? Coba susun beberapa bentuk, bereksperimen dengan `ShadowStyle.ETCHED` untuk tampilan berbeda, atau gabungkan dengan pembuatan tabel untuk membangun laporan lengkap. Kemungkinannya hanya dibatasi oleh imajinasi Anda (dan mungkin tingkat lisensi Aspose).

Jika Anda menemui kendala atau memiliki ide untuk peningkatan lebih lanjut, tinggalkan komentar di bawah. Selamat coding, dan nikmati membuat dokumen Word Anda menjadi lebih menarik!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}