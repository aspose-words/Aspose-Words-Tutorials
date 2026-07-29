---
category: general
date: 2026-07-29
description: Buat dokumen Word di Java menggunakan Aspose.Words. Pelajari cara menyisipkan
  bentuk persegi panjang, mengelompokkan bentuk di Word, dan menyimpan dokumen sebagai
  docx dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: id
lastmod: 2026-07-29
og_description: Buat dokumen Word dalam Java dengan Aspose.Words. Sisipkan bentuk
  persegi panjang, grupkan bentuk-bentuk di Word, dan simpan dokumen sebagai docx
  dalam hitungan menit.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Buat Dokumen Word dengan Bentuk – Tutorial Java Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Buat Dokumen Word dengan Bentuk di Java – Panduan Lengkap Aspose.Words
url: /id/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen Word dengan Bentuk di Java – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya bagaimana cara **membuat dokumen word** secara programatis dan menambahkan grafik khusus? Anda tidak sendirian. Baik Anda perlu menghasilkan laporan dengan bagian yang disorot atau merancang flyer secara cepat, menguasai penanganan bentuk di Word dapat menghemat berjam‑jam kerja manual.

Dalam tutorial ini kita akan melangkah melalui langkah‑langkah tepat untuk **membuat dokumen word** menggunakan Aspose.Words for Java, **menyisipkan bentuk persegi panjang**, **mengelompokkan bentuk di Word**, dan akhirnya **menyimpan dokumen sebagai docx**. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan sepenuhnya dan dapat dimasukkan ke proyek apa pun.

## Apa yang Akan Anda Dapatkan

- File Word baru yang dihasilkan sepenuhnya dari kode Java.  
- Dua bentuk berbeda (sebuah persegi panjang dan sebuah elips) yang ditambahkan ke halaman.  
- Bentuk‑bentuk tersebut digabungkan menggunakan API **group shapes in word**, sehingga berperilaku seperti satu objek.  
- File disimpan di disk sebagai `.docx` standar yang dapat dibuka di Microsoft Word tanpa masalah.  

Tanpa alat eksternal, tanpa hack XML yang rumit—hanya Java bersih dan Aspose.Words.

---

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

1. **Java Development Kit (JDK) 8 atau lebih baru** – kode ini menargetkan Java 8+.  
2. **Aspose.Words for Java** JAR (Anda dapat mengambil versi terbaru dari repositori Maven Central).  
3. IDE sederhana (IntelliJ IDEA, Eclipse, atau bahkan editor teks biasa).  

Jika semua sudah siap, bagus—mari kita mulai.

---

## Implementasi Langkah‑per‑Langkah

Berikut kami memecah proses menjadi langkah‑langkah kecil. Setiap langkah menyertakan cuplikan kode, penjelasan singkat, dan tip yang mungkin tidak Anda temukan di dokumentasi resmi.

### ## Membuat Dokumen Word dengan Bentuk Menggunakan Aspose.Words

Hal pertama yang Anda perlukan adalah file Word kosong untuk bekerja. Aspose.Words membuat ini menjadi satu baris kode.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:**  
`Document` adalah wadah untuk segala hal—teks, tabel, gambar, dan bentuk. `DocumentBuilder` adalah pembantu yang ramah yang memungkinkan Anda menambahkan konten tanpa berurusan dengan objek‑objek tingkat rendah. Anggap saja sebagai pena yang menulis langsung ke halaman.

> **Pro tip:** Jika Anda berencana memulai dengan templat (misalnya kop surat perusahaan), ganti `new Document()` dengan `new Document("template.docx")`.

### ## Menyisipkan Bentuk Persegi Panjang dan Bentuk Lainnya

Sekarang kita akan menambahkan persegi panjang biru dan elips hijau. Persegi panjang memperlihatkan kata kunci **insert rectangle shape**, sementara elips menunjukkan bahwa Anda dapat mencampur tipe bentuk secara bebas.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Apa yang terjadi di balik layar?**  
Setiap pemanggilan `insertShape` membuat objek `Shape` dan secara otomatis menambahkannya ke paragraf saat ini. Metode `setLeft`/`setTop` memposisikan bentuk relatif terhadap margin halaman, diukur dalam poin (1 pt = 1/72 in). Dengan menyesuaikan angka‑angka ini Anda dapat menempatkan bentuk di mana saja yang Anda inginkan.

> **Pertanyaan umum:** *Apakah saya dapat menambahkan gambar alih‑alih warna solid?*  
> Tentu—cukup ganti warna isi dengan gambar menggunakan `shape.getFill().setImage("path/to/image.png")`.

### ## Mengelompokkan Bentuk di Word untuk Manipulasi Mudah

Memiliki dua objek terpisah memang baik, tetapi seringkali Anda ingin memindahkannya bersama. Di sinilah **group shapes in word** berperan.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Mengapa mengelompokkan?**  
Ketika bentuk‑bentuk dikelompokkan, setiap transformasi—memindah, memutar, mengubah ukuran—berlaku pada seluruh koleksi. Ini meniru perilaku yang Anda dapatkan ketika secara manual memilih beberapa bentuk di UI Word dan menekan *Group*. Ini juga menyederhanakan kode selanjutnya karena Anda hanya perlu menyesuaikan satu objek, bukan banyak.

> **Kasus khusus:** Jika Anda nanti perlu memisahkan grup, panggil `group.getParentNode().removeChild(group)` dan sisipkan kembali anak‑anaknya secara individual.

### ## Menyimpan Dokumen sebagai DOCX dan Memverifikasi Output

Akhirnya, kita menyimpan file. Langkah ini memenuhi persyaratan **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Apa yang diharapkan:**  
Buka `GroupShapeExample.docx` yang dihasilkan di Microsoft Word. Anda akan melihat persegi panjang biru dan elips hijau, terkelompok rapi. Seret grup tersebut—kedua bentuk bergerak bersama, persis seperti yang Anda harapkan dari UI.

> **Tip:** Gunakan `SaveFormat.PDF` jika Anda memerlukan versi PDF; kode yang sama bekerja tanpa perubahan.

### ## Contoh Lengkap yang Siap Jalan dan Kesalahan Umum

Berikut adalah kelas Java lengkap yang siap dijalankan. Salin‑tempel ke proyek Anda, sesuaikan folder output, dan tekan *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **`NullPointerException` pada `builder`** | Lupa menginstansiasi `DocumentBuilder` setelah membuat `Document`. | Pastikan `new DocumentBuilder(doc)` dijalankan sebelum menyisipkan bentuk apa pun. |
| **Bentuk muncul di luar halaman** | Menggunakan nilai piksel alih‑alih poin, atau tidak memperhitungkan margin. | Ingat bahwa Aspose.Words mengharapkan poin; 72 pt = 1 in. Sesuaikan `setLeft`/`setTop` secara tepat. |
| **Grup menghilang setelah disimpan** | Menambahkan bentuk ke grup *setelah* grup disimpan. | Selalu kelompokkan sebelum memanggil `doc.save()`. |
| **File tidak ditemukan saat menyimpan** | Direktori output tidak ada. | Buat direktori secara programatis (`new File("output").mkdirs();`) atau gunakan path yang sudah ada. |

---

## Kesimpulan

Kita baru saja **create word document** dari nol, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, dan akhirnya **save document as docx**—semua dengan beberapa baris Java. Kekuatan Aspose.Words terletak pada model objeknya yang jelas; Anda dapat memperlakukan file Word seperti kanvas, melukis di atasnya dengan bentuk, dan kemudian mengekspornya ke mana pun Anda butuhkan.

Merasa berani? Coba ganti persegi panjang dengan bintang, tambahkan teks di dalam bentuk menggunakan `Shape.getTextBox()`, atau bereksperimen dengan rotasi (`shape.setRotationAngle(45)`). API ini kaya, dan kemungkinan hampir tak terbatas.

Punya pertanyaan tentang skenario yang lebih maju—seperti menautkan bentuk ke bookmark atau mengekspor ke PDF dengan font tersemat? Tinggalkan komentar di bawah, dan kami akan menggali lebih dalam bersama. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}