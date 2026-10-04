---
category: general
date: 2026-10-04
description: Pelajari cara menyembunyikan bentuk di Word dengan Java. Panduan langkah
  demi langkah ini menunjukkan cara menyembunyikan bentuk di Word, membuat bentuk
  tidak terlihat di Word, dan menyembunyikan bentuk di Microsoft Word secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: id
lastmod: 2026-10-04
og_description: Cara menyembunyikan bentuk di Word dengan Java. Ikuti panduan ini
  untuk menyembunyikan bentuk di Word, membuat bentuk tidak terlihat di Word, dan
  menyembunyikan bentuk Microsoft Word dalam beberapa baris kode.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Cara menyembunyikan bentuk dalam dokumen Word menggunakan Java – panduan
  lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Cara menyembunyikan bentuk dalam dokumen Word menggunakan Java
url: /id/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyembunyikan shape di dokumen Word menggunakan Java

Jika Anda perlu menyembunyikan sebuah shape dalam file Word, panduan ini menunjukkan **cara menyembunyikan shape** secara programatis. Baik Anda menghasilkan laporan, membersihkan template, atau menyiapkan dokumen untuk kepatuhan, Anda dapat membuat shape menjadi tidak terlihat tanpa menghapusnya dari struktur file.

Di bagian-bagian berikut Anda akan mempelajari cara menyembunyikan shape di Word, membuat shape tidak terlihat di Word, dan menyembunyikan shape di Microsoft Word menggunakan pustaka Aspose.Words for Java. Tutorial ini mengasumsikan Anda memiliki pengetahuan dasar Java dan lingkungan pengembangan Java yang berfungsi.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java Development Kit (JDK) 8 atau yang lebih baru  
* Maven atau Gradle untuk manajemen dependensi  
* Aspose.Words for Java (versi 23.9 atau lebih baru) – tambahkan koordinat Maven `com.aspose:aspose-words:23.9`  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu shape (misalnya gambar, textbox, atau SmartArt)

## Langkah 1: Siapkan proyek dan impor Aspose.Words

Buat proyek Maven baru atau tambahkan dependensi Aspose.Words ke proyek yang sudah ada.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

Pustaka menyediakan kelas `Document`, `NodeType`, dan `Shape` yang digunakan pada langkah-langkah berikut. Impor kelas-kelas tersebut di bagian atas file sumber Java Anda:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Langkah 2: Muat dokumen Word

Memuat dokumen adalah langkah pertama dalam setiap alur kerja pengolahan Word. Konstruktor `Document` membaca file ke dalam memori, mempertahankan semua node, termasuk shape yang tersembunyi.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Mengapa ini penting*: Memuat file membuat DOM (Document Object Model) yang memungkinkan Anda menavigasi, mengkueri, dan memodifikasi node individu seperti shape, paragraf, atau tabel.

## Langkah 3: Dapatkan shape target

Jika dokumen berisi banyak shape, Anda dapat menemukan shape tertentu berdasarkan indeks, nama, atau kriteria lainnya. Untuk demonstrasi cepat, contoh ini mengambil shape pertama dalam hierarki dokumen, termasuk shape yang berada di dalam tabel atau grup.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Mengapa ini penting*: Metode `getChild` dengan nilai `true` untuk flag `isDeep` menelusuri seluruh pohon node, memastikan Anda menangkap shape yang bukan anak langsung dari badan dokumen.

## Langkah 4: Sembunyikan shape

Menetapkan properti `Hidden` ke `true` memberi tahu Microsoft Word untuk mengecualikan shape dari rendering tata letak sambil tetap mempertahankannya dalam struktur dokumen. Shape tidak akan terlihat saat file dibuka di Word, tetapi tetap dapat diakses untuk pemrosesan selanjutnya.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Mengapa ini penting*: Menyembunyikan shape berguna ketika Anda perlu mempertahankan shape untuk aktivasi di masa mendatang (misalnya konten bersyarat, versioning) tanpa menampilkannya kepada pengguna akhir.

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Setelah mengubah visibilitas shape, tulis kembali dokumen ke disk. Anda dapat menimpa file asli atau membuat file baru; contoh ini menulis ke `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Saat Anda membuka `HiddenShape.docx` di Microsoft Word, shape akan tidak terlihat, namun tata letak dokumen akan mencerminkan keadaan tersembunyi (tanpa spasi putih tambahan).

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah menghasilkan program mandiri yang dapat Anda kompilasi dan jalankan langsung.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Hasil yang diharapkan**  
Menjalankan program menghasilkan `HiddenShape.docx`. Membuka file tersebut di Microsoft Word menampilkan konten asli tetapi shape yang ada di `input.docx` tidak lagi terlihat. Struktur dokumen masih berisi node shape, yang dapat ditampilkan kembali nanti dengan menetapkan `shape.setHidden(false)`.

## Mengapa menyembunyikan shape daripada menghapusnya?

* **Mempertahankan metadata** – Shape sering membawa teks alternatif, hyperlink, atau data khusus yang mungkin Anda perlukan nanti.  
* **Tampilan bersyarat** – Dalam skenario mail‑merge atau pembuatan laporan Anda mungkin menampilkan shape hanya untuk penerima tertentu.  
* **Kontrol versi** – Menyembunyikan shape memungkinkan Anda mempertahankan satu template sambil mengubah visibilitas secara programatis.

## Variasi umum dan kasus tepi

| Situasi | Penyesuaian yang direkomendasikan |
|-----------|------------------------|
| Banyak shape, butuh yang spesifik | Gunakan `doc.getChild(NodeType.SHAPE, index, true)` dengan indeks yang tepat, atau iterasi melalui `doc.getChildNodes(NodeType.SHAPE, true)` dan cocokkan dengan `shape.getName()` atau `shape.getAlternativeText()`. |
| Shape berada di dalam GroupShape | Pencarian mendalam (`true`) sudah mencapai dalam grup, tetapi Anda mungkin perlu melakukan cast ke `GroupShape` terlebih dahulu jika ingin menyembunyikan hanya anggota tertentu dari grup. |
| Anda ingin menyembunyikan semua shape | Lakukan loop pada semua node shape dan panggil `setHidden(true)` di dalam loop. |
| Kompatibilitas dengan versi Word lama | Flag `Hidden` didukung sejak Word 2000. Format lama (`.doc`) juga menghormatinya, tetapi uji pada versi target jika Anda menemukan perubahan tata letak yang tidak terduga. |

**Tip profesional:** Setelah menyembunyikan shape, Anda dapat memanggil `doc.updatePageLayout()` jika perlu menghitung ulang tata letak halaman sebelum menyimpan. Ini jarang diperlukan karena Word secara otomatis mengalirkan ulang konten saat dibuka, tetapi dapat berguna untuk pembuatan pratinjau sisi server.

## Menguji hasil secara programatis

Jika Anda ingin memastikan shape tersembunyi tanpa membuka Word, Anda dapat mengkueri properti tersebut setelah menyimpan:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Langkah selanjutnya

Sekarang Anda tahu cara menyembunyikan shape di Word, pertimbangkan topik terkait berikut:

* **Menyembunyikan shape di Word berdasarkan kondisi khusus** – Gabungkan flag `Hidden` dengan field mail‑merge untuk mengubah visibilitas per penerima.  
* **Membuat shape tidak terlihat di Word menggunakan VBA** – Untuk otomasi di perangkat, properti yang sama dapat diatur melalui VBA (`Shape.Visible = msoFalse`).  
* **Menyembunyikan shape Microsoft Word secara massal** – Proses folder dokumen dengan loop yang menerapkan kode yang sama pada setiap file.  

Menjelajahi ekstensi ini akan memperdalam kontrol Anda atas otomasi dokumen Word dan menjaga file yang dihasilkan tetap bersih serta profesional.

--- 

*Tutorial ini mengikuti Google Developer Documentation Style Guide, menggunakan suara aktif, perspektif orang kedua, dan menyediakan solusi lengkap yang dapat dikutip untuk mesin pencari serta asisten AI.*

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat shape persegi panjang di Word dengan Java – Panduan Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Tambahkan bayangan ke shape di Word – Panduan Aspose.Words Lengkap](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Buat Dokumen Word dengan Java – Tambahkan Shape Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}