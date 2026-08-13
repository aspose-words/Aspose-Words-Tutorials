---
category: general
date: 2026-07-20
description: Buat dokumen Word kosong dalam Java menggunakan Aspose.Words. Pelajari
  cara membuat grup, menyisipkan bentuk persegi panjang, dan menyematkan gambar ke
  dalam bentuk.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: id
lastmod: 2026-07-20
og_description: Buat dokumen Word kosong di Java dengan Aspose.Words. Panduan ini
  menunjukkan cara membuat grup, menyisipkan bentuk persegi panjang, dan menyematkan
  gambar dalam bentuk untuk file Word dinamis.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Buat dokumen Word kosong dengan bentuk yang dikelompokkan – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Buat dokumen Word kosong dengan bentuk yang dikelompokkan – Panduan Java
url: /id/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan bentuk grup – Panduan Java

Pernah bertanya-tanya bagaimana **membuat dokumen Word kosong** yang sudah berisi bentuk grup yang rapi? Mungkin Anda sedang membuat templat laporan, atau Anda memerlukan placeholder untuk logo dan keterangan. Bagaimanapun, masalahnya umum: Anda memulai dengan file kosong, lalu harus menambahkan grup, menaruh persegi panjang di dalamnya, dan akhirnya menyematkan gambar—semuanya secara programatik.

Dalam tutorial ini kami akan menelusuri contoh Java lengkap yang siap dijalankan dan melakukan hal tersebut. Anda akan belajar **cara membuat grup**, **menyisipkan bentuk persegi panjang**, dan **menambahkan gambar ke dokumen Word** di dalam grup yang sama. Pada akhir tutorial Anda akan memiliki file Word yang tampak seperti templat yang dipoles, siap untuk penyesuaian lebih lanjut.

> **Apa yang akan Anda dapatkan:** kelas Java yang berfungsi penuh, penjelasan langkah‑demi‑langkah, tip untuk menangani jalur file, dan pratinjau output yang diharapkan. Tidak diperlukan dokumentasi eksternal—semua yang Anda butuhkan ada di sini.

---

## Buat dokumen Word kosong – Ikhtisar Langkah‑demi‑Langkah

Hal pertama yang kita butuhkan adalah file Word yang benar‑benar kosong. Aspose.Words membuat ini sangat mudah: cukup instantiate kelas `Document` dengan konstruktor defaultnya. Ini memberi Anda kanvas bersih, setara dengan membuka Word dan mengklik **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa memulai dengan dokumen kosong?**  
> Dokumen kosong menjamin tidak ada gaya atau bagian tersembunyi yang mengganggu bentuk yang akan Anda tambahkan nanti. Ini juga menjaga ukuran file tetap minimal, yang berguna ketika Anda menghasilkan puluhan file dalam pekerjaan batch.

---

## Cara membuat grup dan menambahkan bentuk

Sebuah **group shape** pada dasarnya adalah kontainer yang dapat menampung beberapa bentuk anak—bayangkan sebagai folder untuk objek gambar. Dengan mengelompokkan, Anda dapat memindahkan, mengubah ukuran, atau memutar seluruh set dengan satu perintah.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Metode `insertGroupShape` mengembalikan objek `GroupShape` yang akan kita gunakan sebagai induk untuk persegi panjang dan gambar. Ukurannya dinyatakan dalam poin (1 poin = 1/72 inci), jadi 200 poin memberi Anda kotak kira‑kira 2,78 × 2,78 inci.

> **Pro tip:** Jika Anda menginginkan grup menjadi transparan, setel `group.setFillColor(Color.getWhite());` setelah pembuatan.

Sekarang grup sudah ada, kita harus memberi tahu builder di mana menempatkan bentuk berikutnya. Kursor builder harus diposisikan di dalam paragraf pertama grup.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Sisipkan bentuk persegi panjang di dalam grup

Persegi panjang sering digunakan sebagai placeholder untuk teks atau sebagai petunjuk visual. Menambahkannya sebagai **anak pertama** grup memastikan ia berada di belakang gambar apa pun yang ditambahkan kemudian.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Persegi panjang mewarisi sistem koordinat grup, sehingga ukuran 100 × 50 poin akan terpusat secara default. Anda dapat menata lebih lanjut—menambahkan border, mengubah warna isi, atau menerapkan bayangan—dengan mengakses objek `Shape` yang dikembalikan.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Tambahkan gambar ke dokumen Word – menyematkan gambar dalam bentuk

Sekarang bagian yang menyenangkan: **menyematkan gambar dalam bentuk**. Kami akan menyisipkan gambar JPEG sebagai anak kedua dari grup yang sama. Karena kursor masih berada di dalam grup, gambar secara otomatis menjadi node anak.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Jika file gambar tidak ditemukan, Aspose.Words akan melempar `FileNotFoundException`. Untuk menghindarinya, letakkan `sample.jpg` di direktori kerja proyek atau gunakan jalur absolut.

> **Bagaimana jika Anda memerlukan format gambar lain?**  
> Aspose.Words mendukung PNG, BMP, GIF, TIFF, dan bahkan SVG. Cukup ubah ekstensi file dan pustaka akan menangani konversinya.

---

## Simpan dokumen dan lihat hasilnya

Akhirnya, kami menyimpan dokumen dalam memori ke disk. File `.docx` yang dihasilkan akan berisi satu halaman dengan bentuk grup yang memuat baik persegi panjang maupun gambar.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Saat Anda membuka `output.docx` di Microsoft Word, Anda akan melihat grup 200 × 200 poin di pojok kiri atas. Di dalam grup, persegi panjang abu‑abu muda berada di bagian atas, dan tepat di bawahnya gambar yang Anda tentukan muncul, ter‑align dengan sempurna.

![Grouped shape example](grouped-shape.png){:alt="Tangkapan layar dokumen Word kosong dengan bentuk grup yang berisi persegi panjang dan gambar yang disematkan"}

---

## Variasi umum dan penanganan kasus tepi

| Skenario | Apa yang diubah | Mengapa penting |
|----------|----------------|----------------|
| **Ukuran grup berbeda** | Sesuaikan parameter `insertGroupShape(width, height)` | Grup yang lebih besar dapat menampung tata letak yang lebih kompleks. |
| **Beberapa gambar** | Panggil `builder.insertImage()` berulang kali setelah berpindah ke paragraf grup setiap kali | Setiap pemanggilan menambah anak baru; Anda juga dapat memposisikannya menggunakan `Shape.setLeft()` / `setTop()`. |
| **Jalur gambar dinamis** | Gunakan `String.format("images/%s.jpg", imageName)` | Membuat kode dapat digunakan kembali untuk pemrosesan batch. |
| **Menyimpan sebagai PDF** | Ganti `doc.save("output.pdf")` | Aspose.Words dapat mengonversi secara langsung, memungkinkan Anda menghasilkan PDF langsung. |
| **Memutar grup** | `group.setRotation(45);` | Berguna untuk watermark dekoratif atau header yang bergaya. |

---

## Output yang diharapkan dan verifikasi

Setelah menjalankan kelas:

1. `output.docx` muncul di folder proyek.  
2. Membuka file menampilkan satu halaman dengan bentuk grup.  
3. Di dalam grup, persegi panjang berada di kiri‑atas, dan gambar berada tepat di bawahnya.  
4. Memilih grup di Word menyorot kedua objek anak, mengonfirmasi bahwa mereka memang tergabung dalam grup.

Jika salah satu langkah ini gagal, periksa kembali jalur gambar dan pastikan JAR Aspose.Words ada di classpath Anda.

---

## Kesimpulan

Anda kini tahu **cara membuat dokumen Word kosong** dan memperkayainya dengan bentuk grup yang berisi persegi panjang serta gambar yang disematkan. Dengan menguasai **cara membuat grup**, **menyisipkan bentuk persegi panjang**, dan **menambahkan gambar ke dokumen Word**, Anda dapat membangun templat Word yang canggih sepenuhnya lewat kode—tanpa perlu penyuntingan manual.

Siap untuk tantangan berikutnya? Coba tambahkan kotak teks di dalam grup yang sama, atau bereksperimen dengan gaya bentuk yang berbeda untuk menyesuaikan dengan identitas merek perusahaan Anda. Anda bahkan dapat menghasilkan seluruh perpustakaan laporan di mana setiap dokumen dimulai dengan tata letak persis ini.

Selamat coding, dan jangan ragu untuk berbagi variasi Anda di kolom komentar di bawah!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cara Membuat Dokumen PDF dengan Aspose.Words untuk Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}