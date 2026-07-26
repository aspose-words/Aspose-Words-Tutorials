---
category: general
date: 2026-07-26
description: Masukkan bentuk persegi panjang di Java menggunakan Aspose.Words. Pelajari
  cara mengatur ukuran bentuk, memposisikan bentuk, dan cara mengelompokkan bentuk-bentuk
  dalam file DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: id
lastmod: 2026-07-26
og_description: Masukkan bentuk persegi panjang di Java untuk membuat grafik DOCX
  yang kaya. Ikuti panduan langkah demi langkah ini untuk mengatur ukuran bentuk,
  memposisikan bentuk, dan mengelompokkan bentuk dengan mudah.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Sisipkan Bentuk Persegi Panjang di Java – Kuasai Pengelompokan & Penempatan
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Sisipkan Bentuk Persegi Panjang di Java – Kelompokkan dan Atur Posisi Bentuk
url: /id/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Bentuk Persegi Panjang di Java – Mengelompokkan dan Menentukan Posisi Bentuk

Pernah butuh **insert rectangle shape** ke dalam dokumen Word saat menulis kode Java? Anda bukan satu-satunya—pengembang yang membuat laporan, faktur, atau templat khusus sering menemui hal ini. Kabar baiknya, dengan beberapa baris Aspose.Words for Java Anda dapat **insert rectangle shape**, **set shape size**, **position shape**, dan bahkan **how to group shapes** sehingga mereka bergerak sebagai satu unit.

Dalam panduan ini kami akan membahas seluruh proses mulai dari membuat dokumen kosong hingga menyimpan `.docx` yang berisi dua persegi panjang yang dikelompokkan rapi bersama. Pada akhir tutorial Anda akan mengetahui **how to add rectangle** objek, mengontrol dimensinya, menempatkannya tepat di tempat yang Anda inginkan, dan menggabungkannya ke dalam grup yang dapat digunakan kembali. Tidak diperlukan pustaka eksternal selain Aspose.Words, dan kode ini bekerja dengan Java 8‑plus.

## Prasyarat

- Java 8 atau lebih baru terinstal (Saya menggunakan JDK 17, tetapi apa pun yang mendukung Maven dapat digunakan)
- Aspose.Words for Java 23.9 atau lebih baru – tambahkan dependensi ke `pom.xml` Anda atau unduh JAR
- Pemahaman dasar tentang sintaks Java (jika Anda dapat menulis metode `main`, Anda siap)
- IDE atau editor teks pilihan Anda (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Jika Anda menggunakan Maven, dependensinya terlihat seperti ini:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Sekarang setelah kami menyiapkan dasar-dasarnya, mari kita selami kode.

## Sisipkan Bentuk Persegi Panjang dan Atur Ukurannya

Hal pertama yang akan Anda lakukan adalah membuat `Document` baru dan `DocumentBuilder`. Builder adalah “pena” Anda yang menggambar bentuk pada halaman. Di bawah ini kami **insert rectangle shape** dan langsung **set shape size** menjadi 100 × 80 poin.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Perhatikan bagaimana pemanggilan `setWidth`/`setHeight` **set shape size** dalam poin (1 pt ≈ 1/72 inci). Anda juga dapat menggunakan `setSize` jika lebih suka satu metode, tetapi pemanggilan eksplisit membuat niatnya sangat jelas.

## Tentukan Posisi Bentuk pada Halaman

Setelah kami memiliki persegi panjang pertama, kami perlu **position shape** yang kedua agar tidak tumpang tindih dengan yang pertama. Penentuan posisi bekerja dengan cara yang sama: Anda mengatur properti `Left` dan `Top` relatif terhadap asal grup.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Jika Anda bertanya-tanya mengapa kami menggunakan `setLeft` alih‑alih `setX`, itu karena Aspose.Words mengadopsi sistem koordinat klasik Windows GDI—`Left` adalah offset horizontal, `Top` adalah offset vertikal. Mengubah nilai‑nilai ini memungkinkan Anda menyesuaikan tata letak secara halus tanpa harus mengutak‑atik tabel atau paragraf.

## Cara Mengelompokkan Bentuk

Anda mungkin bertanya, “Mengapa repot‑repot membuat grup?” Pengelompokan masuk akal ketika Anda ingin bentuk bergerak bersama, berputar sebagai satu unit, atau berbagi gaya yang sama. Pada potongan kode di atas kami sudah membuat `GroupShape` melalui `builder.insertGroupShape`. Objek itu pada dasarnya adalah wadah—bayangkan seperti folder yang menyimpan file bentuk lainnya.

> **Why this matters:** Jika Anda kemudian memutuskan menambahkan keterangan atau memutar seluruh diagram, Anda hanya perlu memodifikasi grup, bukan setiap persegi panjang secara terpisah.

## Cara Menambahkan Persegi Panjang ke dalam Grup

Tindakan **how to add rectangle** ke grup cukup dengan memanggil `group.appendChild(rectangle)`. Di balik layar Aspose.Words memperbarui koleksi internal grup dan secara otomatis menghitung ulang kotak pembatas sehingga grup tetap sesuai dengan lebar dan tinggi yang ditentukan.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Anda dapat bereksperimen dengan `ShapeType` lain—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, dll.—dan pola `appendChild` yang sama berfungsi.

## Simpan Dokumen

Akhirnya, kami menyimpan dokumen ke disk. Path dapat berupa absolut atau relatif; pastikan foldernya ada.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Saat Anda membuka `GroupShape.docx` di Microsoft Word, Anda akan melihat dua persegi panjang berdampingan, keduanya terkunci di dalam kotak abu‑abu muda. Memilih kotak abu‑abu tersebut akan menyorot kedua persegi panjang sekaligus—bukti bahwa **how to group shapes** memang berfungsi.

![Persegi panjang yang dikelompokkan dalam dokumen Word](placeholder-image.png){: .center-image alt="Contoh insert rectangle shape yang menunjukkan dua persegi panjang dikelompokkan dalam file DOCX yang dihasilkan oleh Java"}

*Teks alt gambar (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Output yang Diharapkan

- Sebuah file `GroupShape.docx` yang terletak di folder `output`.
- Di dalam dokumen: grup 400 × 200 pt yang berisi dua persegi panjang (100 × 80 pt dan 120 × 60 pt) yang ditempatkan pada (20, 30) dan (150, 50) masing‑masing.
- Grup tersebut memiliki border hitam tipis dan isi abu‑abu muda, sehingga pengelompokan terlihat jelas.

Buka file tersebut dan coba seret kotak abu‑abu—kedua persegi panjang harus bergerak bersama. Jika tidak, periksa kembali bahwa Anda telah memanggil `group.appendChild` untuk setiap bentuk.

## Kesalahan Umum & Kasus Tepi

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Persegi panjang muncul di luar halaman** | nilai `Left`/`Top` melebihi dimensi grup | Tingkatkan ukuran grup (`insertGroupShape(width, height)`) atau kurangi offset |
| **Grup menghilang setelah disimpan** | `Width`/`Height` grup diatur ke 0 | Berikan dimensi non‑nol saat memanggil `insertGroupShape` |
| **Warna bentuk terlihat salah** | Isi default transparan; Word mungkin menampilkannya sebagai putih | Secara eksplisit atur `setFillColor` atau gunakan `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | Menggunakan koordinat negatif | Pastikan `Left` dan `Top` tidak negatif |

## Ringkasan & Langkah Selanjutnya

Kami telah membahas seluruh siklus hidup **insert rectangle shape** di Java: membuat dokumen, **set shape size**, **position shape**, **how to group shapes**, dan **how to add rectangle** ke grup tersebut. Contoh lengkap yang dapat dijalankan berada di blok kode di atas, dan Anda dapat menempelkannya langsung ke proyek Maven untuk melihat hasilnya.

Apa selanjutnya? Pertimbangkan untuk bereksperimen dengan:

- Menambahkan teks di dalam setiap persegi panjang melalui

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Bayangan – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}