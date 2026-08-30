---
category: general
date: 2026-06-20
description: Simpan dokumen Word menggunakan Aspose.Words di Java sambil menambahkan
  bentuk persegi panjang dan menerapkan bayangan. Pelajari cara menyisipkan bentuk
  langkah demi langkah.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: id
og_description: Simpan dokumen Word dengan Aspose.Words Java. Panduan ini menunjukkan
  cara menambahkan bentuk persegi panjang, menerapkan bayangan, dan menyisipkannya
  ke dalam paragraf.
og_title: Simpan Dokumen Word – Tambahkan Bentuk Persegi Panjang & Bayangan di Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Simpan Dokumen Word – Tambahkan Bentuk Persegi Panjang & Bayangan di Java
url: /id/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Dokumen Word – Tambahkan Bentuk Persegi Panjang & Bayangan di Java

Pernah bertanya-tanya bagaimana cara **menyimpan dokumen Word** setelah Anda menyesuaikan tata letaknya? Anda tidak sendirian—banyak pengembang mengalami kendala ini ketika mereka perlu memperkaya file DOCX secara programatis. Kabar baiknya, dengan Aspose.Words for Java Anda dapat **menyimpan dokumen Word**, menambahkan bentuk persegi panjang tepat di tempat yang diinginkan, dan bahkan memberikan bayangan halus pada bentuk tersebut.

Dalam tutorial ini kita akan melangkah melalui seluruh proses: memuat file yang ada, **menambahkan bentuk persegi panjang**, mengonfigurasi **bayangannya**, menyisipkan bentuk ke paragraf pertama, dan akhirnya **menyimpan dokumen Word**. Pada akhir tutorial Anda akan memiliki program Java yang dapat dijalankan dan menghasilkan file `shadow.docx` yang rapi—tanpa perlu penyesuaian manual.

> **Apa yang Anda perlukan**  
> * Java 17 (atau JDK terbaru lainnya)  
> * Perpustakaan Aspose.Words for Java (Maven/Gradle atau JAR)  
> * File DOCX input (`input.docx`) di folder yang diketahui  

Jika Anda sudah menyiapkan hal‑hal dasar tersebut, mari kita mulai.

---

## Simpan Dokumen Word – Contoh Java Lengkap

Berikut adalah kode sumber lengkap yang siap dijalankan. Salin ke IDE Anda, sesuaikan jalur file, dan tekan **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Hasil yang diharapkan:** Setelah menjalankan program, buka `shadow.docx`. Anda akan melihat konten asli ditambah persegi panjang hitam berukuran 100 × 50 pt dengan bayangan lembut tepat di awal paragraf pertama.

---

## Tambahkan Bentuk Persegi Panjang ke Dokumen Word

Mengapa harus menggunakan bentuk persegi panjang? Anggap saja sebagai penanda visual—sempurna untuk call‑out, placeholder, atau grafik sederhana. Di Aspose.Words kelas `Shape` mengabstraksi semua objek gambar, dan `ShapeType.RECTANGLE` memberi Anda kotak bersih tanpa kerumitan tambahan.

**Poin penting saat menambahkan bentuk persegi panjang**

- **Satuan adalah poin** (1 pt = 1/72 in). Sesuaikan `setWidth`/`setHeight` agar cocok dengan tata letak Anda.  
- Bentuk berada di dalam pohon node dokumen, sehingga Anda dapat menyisipkannya di mana saja `Paragraph` atau `Run` diizinkan.  
- Anda dapat menata persegi panjang (isi, warna garis, dll.) sebelum menerapkan bayangan.

> **Tip pro:** Jika Anda memerlukan isi transparan, panggil `rectangle.getFill().setTransparent(true);`.

---

## Terapkan Bayangan pada Bentuk

Bayangan memberikan kedalaman. Objek `Shadow` yang terhubung ke `Shape` menampilkan properti yang langsung memetakan ke opsi UI Word.

| Properti | Fungsinya | Nilai tipikal |
|----------|-----------|---------------|
| `setVisible(true)` | Mengaktifkan bayangan | `true` |
| `setColor(Color.BLACK)` | Warna bayangan | `Color.BLACK` |
| `setBlurRadius(5.0)` | Kelembutan tepi | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Perpindahan horizontal/vertikal | `4.0` masing‑masing |
| `setTransparency(0.3)` | Kejernihan (0 = tidak tembus, 1 = tidak terlihat) | `0.3` |

Saat Anda menanyakan **cara menerapkan bayangan pada bentuk**, jawabannya cukup dengan menyesuaikan enam properti tersebut. Anda dapat bereksperimen—offset yang lebih besar menciptakan kesan “terangkat”, sementara radius blur yang lebih tinggi menghasilkan tampilan yang lebih tersebar.

> **Kesalahan umum:** Lupa memanggil `setVisible(true)` membuat bentuk tidak memiliki bayangan meskipun properti lain sudah diatur.

---

## Cara Menyisipkan Bentuk ke dalam Paragraf

Menyisipkan bentuk bukan sihir; hanya manipulasi node. Metode `appendChild` menempatkan bentuk di akhir node anak paragraf. Jika Anda memerlukan bentuk sebelum teks, gunakan `insertBefore` sebagai gantinya.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Perubahan kecil itu menjawab **cara menyisipkan bentuk** tepat di tempat yang Anda butuhkan—sebelum run yang ada, setelah heading, atau bahkan di dalam sel tabel (cukup ambil node `Cell` yang sesuai terlebih dahulu).

---

## Menjalankan Kode dan Memverifikasi Output

1. **Kompilasi** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Jalankan** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Buka** `shadow.docx` di Microsoft Word atau LibreOffice. Anda akan melihat persegi panjang dengan bayangan hitam lembut yang terpasang di awal paragraf pertama.

Jika bentuk tidak muncul, periksa kembali:

- Path file input sudah benar.  
- Anda menggunakan versi terbaru Aspose.Words (API sedikit berubah sebelum 20.12).  
- Dokumen memang memiliki setidaknya satu paragraf (jika tidak, `getParagraphs().get(0)` akan melempar `IndexOutOfBoundsException`).

---

## Pertanyaan yang Sering Diajukan (FAQ)

**T: Bisakah saya menambahkan bentuk ke halaman tertentu?**  
J: Ya. Ambil `Section` atau `PageSetup` target dan sisipkan bentuk ke paragraf yang berada di halaman tersebut.

**T: Apakah ini bekerja dengan file .doc?**  
J: Tentu saja. Aspose.Words mengabstraksi format, sehingga kode yang sama **menyimpan dokumen Word** baik itu `.doc` maupun `.docx`.

**T: Bagaimana jika saya memerlukan bentuk lain, misalnya elips?**  
J: Ganti `ShapeType.RECTANGLE` dengan `ShapeType.ELLIPSE`. Semua properti bayangan tetap sama.

---

## Kesimpulan

Anda kini tahu cara **menyimpan dokumen Word** sambil **menambahkan bentuk persegi panjang**, **menerapkan bayangan**, dan **menyisipkan bentuk** ke paragraf pertama—semua dengan beberapa baris kode Java yang bersih. Pola ini dapat diperluas: ganti tipe bentuk, ubah pengaturan bayangan, atau tempatkan bentuk di tabel dan header. Kemungkinannya seluas kebutuhan otomasi dokumen Anda.

Siap untuk tantangan berikutnya? Coba lapiskan beberapa bentuk, tambahkan teks di dalam persegi panjang, atau hasilkan laporan lengkap dengan diagram dan watermark. Setiap tugas tersebut dibangun di atas dasar yang sama yang telah dibahas di sini—jadi Anda sudah selangkah lebih maju.

Selamat coding, semoga otomasi Word Anda bebas dari bug bayangan!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara menyimpan dokumen sebagai PDF dengan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Cara menyimpan Word sebagai PCL dengan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}