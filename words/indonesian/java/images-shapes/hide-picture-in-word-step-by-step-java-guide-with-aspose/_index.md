---
category: general
date: 2026-08-14
description: Sembunyikan gambar di Word menggunakan Java. Pelajari cara menyembunyikan
  gambar, menyembunyikan foto, mengatur properti tersembunyi, dan menyembunyikan bentuk
  di Word dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: id
lastmod: 2026-08-14
og_description: Sembunyikan gambar di Word menggunakan Java dan Aspose.Words. Tutorial
  ini menunjukkan cara mengatur properti tersembunyi pada gambar, menyembunyikan bentuk
  di Word, dan menyimpan dokumen dalam hitungan detik.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Sembunyikan gambar di Word – panduan Java langkah demi langkah dengan Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Menyembunyikan gambar di Word – panduan Java langkah demi langkah dengan Aspose
url: /id/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sembunyikan gambar di Word – panduan Java langkah demi langkah dengan Aspose

Jika Anda perlu **menyembunyikan gambar di Word** secara programatis, panduan ini menunjukkan solusi lengkapnya. Anda akan melihat cara menemukan sebuah gambar, menerapkan flag tersembunyi, dan menulis kembali file yang telah diperbarui ke disk.

Menyembunyikan grafik adalah kebutuhan umum ketika Anda menghasilkan laporan, membuat templat, atau menyiapkan dokumen untuk tinjauan kepatuhan. Contoh di bawah ini memperlihatkan **cara menyembunyikan gambar** menggunakan Aspose.Words untuk Java, tetapi konsep yang sama berlaku untuk pustaka pengolah kata apa pun yang menyediakan metode `setHidden` pada shape.

## Apa yang akan Anda capai

Pada akhir tutorial ini Anda akan dapat:

* Memuat file `.docx` dengan Aspose.Words.
* Menemukan shape gambar pertama dalam dokumen.
* **Mengatur properti tersembunyi** pada shape tersebut sehingga tidak muncul saat file dibuka di Microsoft Word.
* Menyimpan dokumen yang telah dimodifikasi tanpa mengubah konten lain.

Prasyarat satu-satunya adalah lingkungan pengembangan Java (JDK 8 atau lebih baru) dan lisensi Aspose.Words untuk Java yang valid. Tidak diperlukan plugin Maven tambahan selain pustaka inti.

## Sembunyikan gambar di Word dengan Aspose.Words

Langkah pertama adalah membuat objek `Document` yang mewakili file sumber. Aspose.Words membaca seluruh paket Word ke dalam memori, memudahkan penelusuran node seperti shape, paragraf, dan tabel.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Membuat instance `Document` memvalidasi format file dan membangun pohon node internal. Pohon ini menjadi dasar untuk semua operasi selanjutnya, termasuk **cara menyembunyikan objek gambar**.

## Cara menyembunyikan gambar menggunakan properti tersembunyi

Gambar dalam file Word disimpan sebagai node `Shape` dengan `ShapeType.IMAGE`. Pustaka menyediakan metode `setHidden(boolean)` untuk mengontrol visibilitas shape. Alur berikut menyaring koleksi node untuk menemukan shape gambar pertama.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

Pemanggilan `getChildNodes` menelusuri seluruh pohon dokumen (`true` mengaktifkan pencarian mendalam). Ekspresi lambda memeriksa `ShapeType` setiap node. Pola ini adalah cara yang direkomendasikan untuk **cara menyembunyikan gambar** ketika Anda memerlukan kontrol tepat atas pemilihan node.

## Cara menyembunyikan gambar dalam dokumen Word

Setelah shape target diidentifikasi, terapkan flag tersembunyi. Mengatur properti ini tidak menghapus gambar; hanya memberi instruksi kepada Word untuk memperlakukan shape sebagai tersembunyi saat rendering.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

Pemanggilan `setHidden(true)` secara langsung memetakan ke atribut XML dasar `w:hidden="true"`. Word menghormati atribut ini baik di editor desktop maupun online, memastikan gambar tetap tidak terlihat bagi semua pembaca.

## Sembunyikan shape di Word – pertimbangan tambahan

Meskipun contoh ini menyembunyikan hanya gambar pertama, Anda dapat memperluas logika untuk memproses banyak shape:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Kinerja** – Menelusuri pohon node bersifat O(n); untuk dokumen yang sangat besar, pertimbangkan mempersempit pencarian ke bagian tertentu.
* **Kompatibilitas** – Flag tersembunyi bekerja dengan Word 2007+ (`.docx`) dan Word 97‑2003 (`.doc`).
* **Toggle visibilitas** – Untuk membuat gambar tersembunyi kembali terlihat, panggil `shape.setHidden(false)`.

Tips ini membantu Anda menguasai skenario **menyembunyikan shape di Word** di luar kasus penggunaan dasar.

## Simpan dokumen yang telah dimodifikasi

Setelah memperbarui flag tersembunyi, tulis kembali dokumen ke penyimpanan. Aspose.Words secara otomatis mempertahankan semua bagian dokumen lainnya, seperti gaya, header, dan footer.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

Metode `save` mendukung berbagai format (PDF, HTML, ODT). Dalam tutorial ini kami mempertahankan output sebagai file Word untuk memperlihatkan efek gambar tersembunyi secara langsung.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah menghasilkan program mandiri yang dapat Anda kompilasi dan jalankan segera.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Hasil yang diharapkan:** Buka `output.docx` di Microsoft Word. Gambar asli tidak akan ditampilkan, tetapi sisanya (teks, tabel, grafik lain) tetap tidak berubah. Jika Anda memeriksa XML (`document.xml`) Anda akan melihat atribut `w:hidden="true"` pada elemen `<w:pict>` yang berhubungan dengan gambar tersembunyi.

## Kesimpulan

Anda kini tahu cara **menyembunyikan gambar di Word** menggunakan Java, Aspose.Words, dan properti `setHidden`. Tutorial ini mencakup cara menemukan shape gambar, menerapkan flag tersembunyi, dan menyimpan perubahan. Dengan dasar ini Anda juga dapat **menyembunyikan shape di Word**, memproses banyak gambar, atau mengubah visibilitas berdasarkan aturan bisnis.

**Langkah selanjutnya**

* Jelajahi **cara menyembunyikan gambar** secara kondisional berdasarkan metadata (misalnya peran pengguna).
* Gabungkan teknik ini dengan mail‑merge untuk menghasilkan dokumen yang dipersonalisasi dan memperhatikan privasi.
* Tinjau referensi API Aspose.Words untuk manipulasi shape lanjutan, seperti mengubah rotasi atau menerapkan watermark.

Silakan bereksperimen dengan variasi, seperti menyembunyikan chart atau objek SmartArt, dan bagikan temuan Anda dengan komunitas pengembang. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Show Hide Bookmarked Content In Word Document](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}