---
category: general
date: 2026-03-19
description: Pelajari cara mengatur bayangan pada bentuk dengan cepat, menambahkan
  bayangan ke bentuk, mengubah transparansi, mengaburkan bayangan, dan mengatur jarak
  menggunakan Aspose.Words for Java.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to change transparency
- how to blur shadow
- how to set distance
language: id
og_description: Kuasai cara mengatur bayangan pada bentuk di Aspose.Words. Panduan
  ini menunjukkan cara menambahkan bayangan ke bentuk, mengubah transparansi, mengaburkan
  bayangan, dan mengatur jarak.
og_title: Cara Menambahkan Bayangan pada Bentuk – Panduan Java Langkah demi Langkah
tags:
- Aspose.Words
- Java
- ShapeShadow
title: Cara Menetapkan Bayangan pada Bentuk di Aspose.Words – Panduan Lengkap
url: /id/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menambahkan Bayangan pada Bentuk di Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya **bagaimana cara menambahkan bayangan** pada sebuah bentuk tanpa harus menyelam melalui dokumentasi API yang tak berujung? Anda tidak sendirian. Banyak pengembang menemui kesulitan ketika mereka membutuhkan bayangan halus untuk diagram, logo, atau call‑out dalam dokumen Word. Kabar baiknya? Ini sangat mudah dengan Aspose.Words for Java, dan Anda dapat melakukannya hanya dengan beberapa baris kode.

Dalam tutorial ini kami akan membahas seluruh proses: **menambahkan bayangan ke bentuk**, menyesuaikan **transparansi**, menerapkan **blur**, dan menyetel **jarak** serta sudut. Pada akhir tutorial Anda akan memiliki bentuk yang sepenuhnya bergaya, tampak rapi, dan Anda akan memahami mengapa setiap properti penting.

---

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- Java 8 atau yang lebih baru terpasang.
- Aspose.Words for Java (versi terbaru; pada saat penulisan v24.10).
- File `.docx` sederhana yang berisi setidaknya satu bentuk (misalnya, persegi panjang atau gambar) dalam file `input.docx`.
- IDE favorit Anda (IntelliJ IDEA, Eclipse, VS Code… semuanya dapat digunakan).

Tidak ada perpustakaan tambahan yang diperlukan—Aspose.Words sudah menyertakan semua yang Anda butuhkan.

---

## Cara Menambahkan Bayangan pada Bentuk – Langkah‑per‑Langkah

Di bawah ini kami memecah solusi menjadi langkah‑langkah kecil. Setiap langkah mencakup cuplikan kode singkat, penjelasan **mengapa** kami melakukannya, dan tip yang mungkin berguna.

### 1. Muat dokumen sumber

Pertama, kita memerlukan objek `Document` yang menunjuk ke file di disk. Anggap saja ini seperti membuka file Word di memori.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Mengapa ini penting:* Tanpa dokumen yang dimuat, Anda tidak memiliki apa‑apa untuk dimodifikasi. Kelas `Document` adalah titik masuk untuk setiap operasi Aspose.Words.

> **Tip profesional:** Gunakan jalur absolut selama pengembangan untuk menghindari kejutan “file tidak ditemukan”.

### 2. Tambahkan bayangan ke bentuk – ambil bentuk pertama

Sekarang kita menemukan bentuk yang ingin kita beri gaya. Selektor `NodeType.SHAPE` menelusuri pohon node dan mengembalikan `Shape` pertama yang ditemukannya.

```java
        // Step 2: Retrieve the first shape in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Mengapa ini penting:* Bentuk dapat berupa gambar, gambar vektor, atau SmartArt. Mengambil node yang tepat memastikan kita tidak secara tidak sengaja mengubah paragraf atau tabel.

> **Waspada:** Jika dokumen Anda tidak memiliki bentuk, `firstShape` akan bernilai `null` dan baris‑baris berikut akan melempar `NullPointerException`. Selalu periksa `null` dalam kode produksi.

### 3. Cara Mengubah Transparansi Bayangan

Bayangan yang sepenuhnya pekat terlihat berat. Menyetel properti `transparency` memungkinkan Anda menurunkannya menjadi tirai halus.

```java
        // Step 3: Obtain the shadow formatting object for the shape
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Step 4: Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);
```

*Mengapa ini penting:* Transparansi mengontrol seberapa banyak konten di bawahnya terlihat melalui bayangan. Nilai `0.0` berarti hitam solid; `0.3` memberikan efek tembus pandang yang lembut.

> **Kesalahan umum:** Lupa memanggil `setTransparency` akan meninggalkan nilai default (sepenuhnya pekat), yang dapat membuat bayangan tampak terlalu keras.

### 4. Cara Memburamkan Bayangan

Memburamkan melunakkan tepi, membuat bayangan tampak lebih alami, terutama pada layar beresolusi tinggi.

```java
        // Step 5: Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);
```

*Mengapa ini penting:* Radius blur `0` menghasilkan tepi yang tajam dan tidak realistis. Meningkatkan radius menyebarkan bayangan, meniru cara cahaya menyebar di dunia nyata.

> **Uji cepat:** Ubah `5.0` menjadi `10.0` dan jalankan kembali—perhatikan bagaimana bayangan menjadi lebih berbulu.

### 5. Cara Mengatur Jarak dan Sudut Bayangan

Jarak memindahkan bayangan menjauh dari bentuk, sementara sudut menentukan arah sumber cahaya.

```java
        // Step 6: Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Step 7: Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);
```

*Mengapa ini penting:* Jarak `0` menempelkan bayangan tepat di belakang bentuk, yang sering terlihat datar. Sudut `45°` mensimulasikan sumber cahaya dari kiri‑atas, pilihan desain yang umum.

> **Kasus khusus:** Sudut diukur searah jarum jam dari sumbu horizontal. Sudut `180` membalikkan bayangan ke sisi berlawanan.

### 6. Simpan dokumen

Akhirnya, tulis dokumen yang telah dimodifikasi kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");
    }
}
```

*Mengapa ini penting:* Menyimpan memastikan semua pengaturan bayangan yang baru saja Anda konfigurasikan tersimpan. Buka file hasilnya di Word untuk melihat efeknya.

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the first shape (add null‑check for safety)
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }

        // Access the shadow format
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);

        // Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);

        // Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.out.println("Shadow applied successfully!");
    }
}
```

**Hasil yang diharapkan:** Buka `output_with_shadow.docx`. Bentuk pertama harus menampilkan bayangan lembut dengan transparansi 30 %, sedikit diburamkan, bergeser 4 pt pada sudut 45°. Tampaknya bentuk tersebut melayang sedikit di atas halaman.

---

## Pertanyaan yang Sering Diajukan (FAQ)

### Bisakah saya menambahkan bayangan ke beberapa bentuk sekaligus?

Tentu saja. Ganti pengambilan satu‑bentuk dengan loop:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node node : shapes) {
    Shape shape = (Shape) node;
    ShadowFormat sf = shape.getShadowFormat();
    // Apply the same settings or vary per shape
}
```

### Bagaimana jika saya membutuhkan bayangan berwarna selain hitam?

`ShadowFormat` juga menyediakan metode `setColor(Color)`. Untuk bayangan biru tua:

```java
shadowFormat.setColor(Color.fromArgb(0, 0, 255));
```

### Apakah ini bekerja dengan gambar di dalam bentuk?

Ya. Aspose.Words memperlakukan gambar sebagai objek `Shape` selama mereka dimasukkan sebagai “Picture” (bukan inline). Properti bayangan yang sama berlaku.

### Apakah radius blur diukur dalam poin atau piksel?

Radius blur diukur dalam poin (1 pt = 1/72 in). Ini menjaga tampilan tetap konsisten di berbagai pengaturan DPI.

---

## Kesimpulan

Kami telah membahas **cara menambahkan bayangan** pada sebuah bentuk dari awal hingga akhir, mendemonstrasikan **menambahkan bayangan ke bentuk**, menunjukkan **cara mengubah transparansi**, menjelaskan **cara memburamkan bayangan**, dan akhirnya merinci **cara mengatur jarak** serta sudut. Kode singkat, konsep jelas, dan Anda kini memiliki pola yang dapat digunakan kembali untuk menata bentuk apa pun di Aspose.Words for Java.

Siap untuk tantangan berikutnya? Coba gabungkan pengaturan bayangan ini dengan **gradient fills**, atau bereksperimen dengan **multiple shadows** dengan menggandakan bentuk dan menggeser setiap salinan. Langit adalah batasnya, dan dengan alat yang baru Anda pelajari, Anda dapat memberikan dokumen Anda sentuhan profesional dalam sekejap.

Jika panduan ini membantu, tinggalkan komentar, bagikan variasi Anda, atau jelajahi tutorial lain kami tentang **shape formatting**, **text effects**, dan **document conversion**. Selamat coding! 

![contoh cara menambahkan bayangan pada bentuk](image.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}