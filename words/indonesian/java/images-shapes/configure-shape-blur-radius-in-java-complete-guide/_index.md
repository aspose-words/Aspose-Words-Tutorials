---
category: general
date: 2026-06-27
description: Pelajari cara mengonfigurasi radius blur bentuk menggunakan Aspose.Words
  untuk Java. Tutorial langkah demi langkah ini juga mencakup pengaturan bayangan,
  transparansi, dan penyimpanan dokumen.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: id
og_description: Konfigurasikan radius blur bentuk dalam dokumen Word menggunakan Java.
  Ikuti tutorial terperinci ini untuk menguasai pengaturan bayangan bentuk Aspose.Words.
og_title: Mengonfigurasi Radius Blur Bentuk di Java – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Mengonfigurasi Radius Blur Bentuk di Java – Panduan Lengkap
url: /id/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonfigurasi Radius Blur Bentuk di Java – Panduan Lengkap

Pernah perlu **mengonfigurasi radius blur bentuk** dalam dokumen Word saat bekerja dengan Java? Anda bukan satu‑satunya yang kebingungan. Baik Anda sedang menyempurnakan laporan korporat atau menambahkan sentuhan visual halus pada selebaran, menguasai pengaturan ini dapat membuat dokumen Anda terlihat jauh lebih profesional.

Dalam tutorial ini kami akan membahas seluruh proses—dari memuat file `.docx` hingga menyesuaikan blur bayangan dan akhirnya menyimpan hasilnya. Sepanjang jalan kami juga akan menyentuh topik terkait seperti **bayangan bentuk Aspose.Words**, **format bayangan Java**, dan **manipulasi bentuk dokumen Word** secara umum. Pada akhir tutorial, Anda akan memiliki potongan kode yang siap dijalankan serta pemahaman jelas mengapa setiap baris penting.

## Apa yang Akan Anda Pelajari

- Cara memuat dokumen Word dengan Aspose.Words untuk Java.  
- Cara menemukan objek `Shape` pertama di dalam tubuh dokumen.  
- Langkah‑langkah tepat untuk **mengonfigurasi radius blur bentuk** serta properti bayangan lain seperti jarak dan transparansi.  
- Cara menyimpan perubahan ke file `.docx` baru.  

Tidak diperlukan pustaka eksternal selain Aspose.Words, dan kode ini bekerja dengan Java 8‑plus serta versi terbaru Aspose.Words untuk Java (misalnya 24.9). Jika Anda sudah familiar dengan sintaks Java dasar, Anda akan baik‑baik saja.

---

## Langkah 1: Muat Dokumen Word

Sebelum Anda dapat menyentuh bentuk apa pun, dokumen harus berada di memori. Aspose.Words menjadikannya satu baris kode.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Mengapa ini penting:**  
Membuat objek `Document` mem‑parsing seluruh file, memberi Anda akses ke bagian, paragraf, tabel, **dan bentuk**. Melewatkan langkah ini akan membuat Anda tidak memiliki konteks untuk menerapkan radius blur.

> **Pro tip:** Jika Anda menangani file besar, pertimbangkan menggunakan `LoadOptions` untuk mem‑stream hanya bagian yang diperlukan. Hal ini dapat mengurangi penggunaan memori secara signifikan.

---

## Langkah 2: Ambil Bentuk Target

Bentuk dapat berada di mana saja—header, footer, tabel, apa saja. Untuk kesederhanaan, kami akan mengambil bentuk pertama yang ditemukan di tubuh utama bagian pertama.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Mengapa ini penting:**  
Pemanggilan `getChild` menelusuri pohon node secara depth‑first, mengembalikan *bentuk pertama* yang cocok dengan `NodeType.SHAPE`. Jika dokumen Anda berisi banyak bentuk, Anda dapat menyesuaikan indeks (`0`) atau mengiterasi `document.getChildNodes(NodeType.SHAPE, true)`.

> **Kasus tepi:** Jika dokumen tidak memiliki bentuk, `shape` akan `null` dan baris berikutnya akan melempar `NullPointerException`. Selalu lakukan pengecekan null dalam kode produksi.

---

## Langkah 3: Konfigurasikan Bayangan Bentuk – Atur Radius Blur

Sekarang saatnya bintang utama: menyesuaikan radius blur. Ini berada di dalam objek `ShadowFormat` yang terikat pada bentuk.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Memahami Angka‑Angka

- **Radius blur** (`setBlurRadius`) mengontrol seberapa kabur bayangan terlihat. Nilai `0` menghasilkan tepi yang tajam, sementara `10` atau lebih menghasilkan cahaya yang lembut.  
- **DistanceX / DistanceY** menggeser bayangan relatif terhadap bentuk. X positif menggerakkannya ke kanan; Y positif menggerakkannya ke bawah.  
- **Transparency** membuat bayangan tembus pandang. Berguna ketika Anda menginginkan efek halus, bukan blok hitam solid.

> **Mengapa mengonfigurasi radius blur?**  
> Pada banyak templat korporat, blur ringan menambah kedalaman tanpa mengalihkan perhatian pembaca. Ini adalah penyesuaian visual kecil yang dapat meningkatkan kualitas yang dirasakan secara dramatis.

---

## Langkah 4: Simpan Dokumen yang Telah Dimodifikasi

Semua pekerjaan berat telah selesai; kini tulis perubahan kembali ke disk.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Mengapa ini penting:**  
Pemanggilan `save` menulis seluruh dokumen, termasuk `ShadowFormat` yang telah diperbarui. Jika Anda hanya membutuhkan bentuk sebagai gambar, Anda dapat mengekspornya melalui `shape.getImageData().save(...)` sebagai alternatif.

---

## Contoh Program Lengkap

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke IDE Java mana pun. Pastikan JAR Aspose.Words untuk Java ada di classpath Anda.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Output yang diharapkan:**  
Menjalankan program menghasilkan `output.docx` baru di mana bentuk pertama kini memiliki bayangan semi‑transparan yang lembut dengan radius blur `5` poin. Buka file di Word, pilih bentuk, dan di bawah **Shape Format → Shadow Effects → Shadow Options**, Anda akan melihat nilai‑nilai yang telah Anda setel tercermin di UI.

---

## Menangani Banyak Bentuk & Skenario Lanjutan

### Menargetkan Bentuk Spesifik Berdasarkan Nama

Jika dokumen Anda berisi banyak bentuk, gunakan **nama** bentuk (diatur di opsi tata letak Word) alih‑alih indeks:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Menerapkan Radius Blur Berbeda

Anda mungkin menginginkan blur lebih kuat untuk grafik latar belakang dan blur halus untuk ikon. Loop melalui semua bentuk:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Catatan Kompatibilitas

- **Satuan:** Aspose.Words menggunakan poin (1 pt = 1/72 inci). Jika Anda bekerja dengan milimeter, konversikan sesuai kebutuhan.  
- **Versi:** API yang ditunjukkan bekerja dengan Aspose.Words untuk Java 24.9 ke atas. Versi lebih lama mungkin menggunakan `setBlurRadius(double)` tetapi tidak memiliki beberapa properti bayangan terbaru.

---

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| `NullPointerException` pada `shape` | Dokumen tidak memiliki bentuk atau indeks query di luar jangkauan | Tambahkan pengecekan null sebelum mengakses `ShadowFormat`. |
| Bayangan tidak terlihat di Word | Warna bayangan default transparan atau nilai jarak memindahkannya keluar halaman | Atur `ShadowColor` yang terlihat (`shadow.setColor(Color.BLACK)`) dan jaga `DistanceX/Y` tetap wajar. |
| Radius blur tidak berubah | Menggunakan versi Aspose.Words lama yang mengabaikan properti tersebut | Upgrade ke pustaka terbaru; properti ini diperkenalkan pada versi 20.5. |
| Penurunan performa pada dokumen besar | Menyimpan seluruh dokumen setelah setiap modifikasi bentuk | Kelompokkan semua perubahan, lalu panggil `save` sekali saja. |

---

## Kesimpulan

Anda kini tahu **cara mengonfigurasi radius blur bentuk** dalam dokumen Word menggunakan Java dan Aspose.Words. Dari memuat file, mengambil `Shape` yang tepat, menyesuaikan `ShadowFormat`, hingga menyimpan perubahan—setiap langkah dibahas lengkap dengan penjelasan dan tips dunia nyata.  

Teknik ini tidak terbatas pada satu bentuk; Anda dapat memperluasnya ke seluruh dokumen, menerapkan level blur berbeda, atau menggabungkannya dengan atribut bayangan lain seperti **transparansi bayangan Java**. Langkah selanjutnya yang logis adalah mengeksplor **set blur radius** untuk gambar, bereksperimen dengan **format bayangan Java** pada diagram, atau menyelami lebih dalam **manipulasi bentuk dokumen Word** untuk pembuatan laporan dinamis.

Punya skenario yang belum tercakup di sini? Tinggalkan komentar atau periksa dokumentasi Aspose.Words untuk Java untuk efek bayangan lanjutan lainnya. Selamat coding!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat dan membangun atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Menggunakan Opsi dan Pengaturan Dokumen di Aspose.Words untuk Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Cara Mengonversi Word ke PDF Menggunakan Aspose.Words untuk Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}