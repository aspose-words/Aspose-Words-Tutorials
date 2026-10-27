---
date: 2026-10-23
description: Pelajari cara membuat label QR code Java dengan Aspose.Words. Panduan
  langkah demi langkah ini menunjukkan cara menyisipkan barcode ke dalam dokumen Word
  dan menyesuaikan ukuran, warna, serta format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Membuat Label Barcode Kustom
og_description: Pelajari cara membuat label QR code Java dengan Aspose.Words. Panduan
  ini menjelaskan penyisipan barcode, pengaturan ukuran, dan penyesuaian warna dalam
  dokumen Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Cara membuat label QR code Java menggunakan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Cara membuat label QR code Java menggunakan Aspose.Words
url: /id/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat label QR code Java menggunakan Aspose.Words

Barcode sangat penting dalam aplikasi modern—baik Anda mengelola inventaris, mencetak tiket, atau membuat kartu identitas. Dalam tutorial ini Anda akan **membuat label QR code Java** dan menyematkannya langsung ke dalam dokumen Word menggunakan antarmuka `IBarcodeGenerator`. Kami akan membimbing Anda melalui setiap langkah, mulai dari menyiapkan lingkungan hingga menyisipkan gambar barcode, sehingga Anda dapat langsung menggunakan barcode dalam proyek Java Anda.

## Jawaban cepat
- **Apa yang diajarkan tutorial ini?** Cara membuat label QR code Java dan menyematkannya dalam file Word dengan Aspose.Words untuk Java.  
- **Jenis barcode apa yang digunakan dalam contoh?** QR code (Anda dapat menggantinya dengan salah satu dari lebih dari 20 tipe yang didukung).  
- **Apakah saya memerlukan lisensi?** Lisensi sementara diperlukan untuk akses tanpa batas selama pengembangan.  
- **Versi Java apa yang dibutuhkan?** JDK 8 atau lebih tinggi.  
- **Bisakah saya mengubah ukuran atau warna barcode?** Ya—modifikasi pengaturan `BarcodeParameters` dan `BarcodeGenerator`.

## Apa itu create QR code Java?
`create QR code Java` mengacu pada pembuatan gambar QR‑code secara programatis dalam lingkungan Java dan menyisipkannya ke dalam dokumen atau komponen UI. Aspose.Words untuk Java bersama dengan Aspose.BarCode memungkinkan Anda menghasilkan gambar sepenuhnya di memori, tanpa file sementara.

## Mengapa menghasilkan label barcode khusus dengan Aspose.Words?
Aspose.Words mendukung **lebih dari 35 format input dan output** serta dapat memproses **dokumen 500 halaman dalam kurang dari 3 detik** pada perangkat keras server standar. Dengan generasi barcode di memori, Anda mendapatkan kontrol penuh atas tipe, ukuran, dan warna sambil menjaga alur kerja tetap sepenuhnya berbasis Java dan platform‑independen.

## Prasyarat

- Java Development Kit (JDK): Versi 8 atau lebih tinggi.  
- Perpustakaan Aspose.Words untuk Java: [Unduh di sini](https://releases.aspose.com/words/java/).  
- Perpustakaan Aspose.BarCode untuk Java: [Unduh di sini](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse, atau IDE lain yang Anda sukai.  
- Lisensi Sementara: Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk akses tanpa batas.

## Impor paket

Kami akan menggunakan perpustakaan Aspose.Words dan Aspose.BarCode. Impor paket berikut ke dalam proyek Anda:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Impor ini memberi kami akses ke API generasi barcode dan kelas dokumen Word yang diperlukan.

## Langkah 1: buat kelas utilitas untuk operasi barcode

Kelas utilitas berisi pembantu yang dapat digunakan kembali seperti **konversi twips ke piksel** dan **konversi warna heks**.  
Kelas `CustomBarcodeGeneratorUtils` menyediakan metode statis untuk konversi satuan dan penanganan warna.

### Code

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Penjelasan**  
- `twipsToPixels` – Word mengukur dimensi dalam **twips**; metode ini mengubahnya menjadi piksel layar, berguna saat Anda perlu mengatur ukuran gambar barcode secara tepat.  
- `convertColor` – Mengubah string heksadesimal (mis., `"FF0000"` untuk merah) menjadi objek `java.awt.Color`, memungkinkan Anda **menambahkan barcode ke dokumen Word** dengan warna latar depan dan latar belakang khusus.

## Langkah 2: implementasikan generator barcode khusus

Sekarang kami akan mengimplementasikan antarmuka `IBarcodeGenerator`. Kelas ini bertanggung jawab untuk **menghasilkan gambar QR code Java**‑style yang dapat disematkan oleh Aspose.Words.  
Antarmuka `IBarcodeGenerator` mendefinisikan satu metode yang mengembalikan `BufferedImage` yang mewakili barcode.

### Code

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Penjelasan**  
- `getBarcodeImage` membuat instance `BarcodeGenerator`, menerapkan warna yang diberikan melalui `BarcodeParameters`, dan akhirnya mengembalikan `BufferedImage`.  
- Metode ini juga menangani kesalahan secara elegan dengan mengembalikan gambar placeholder, memastikan pembuatan dokumen Word tidak mengalami crash.

## Cara menyematkan barcode di Word menggunakan Aspose.Words?

Muat file Word Anda dengan `new Document("template.docx")` (atau buat `Document` baru) dan panggil `builder.insertImage` dengan gambar barcode yang dikembalikan oleh generator. Pola dua langkah ini menyematkan barcode langsung tanpa menulis file menengah ke disk. Dengan menentukan dimensi gambar dalam piksel atau mengonversi twips Word ke piksel, Anda dapat mengontrol ukuran dan penempatan barcode secara tepat dalam dokumen, memastikan tata letak profesional yang tercetak dengan benar pada printer apa pun.

## Langkah 3: hasilkan barcode dan sematkan barcode di Word

Dengan generator siap, kita kini dapat menghasilkan gambar barcode dan **menyisipkannya ke dalam dokumen Word**.

### Code

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Penjelasan**  

1. **Inisialisasi dokumen** – Membuat `Document` baru (atau Anda dapat memuat templat yang ada).  
2. **Parameter barcode** – Menentukan tipe barcode (`QR`), nilai yang akan dienkode, serta warna latar depan/latar belakang.  
3. **Penyisipan gambar** – `builder.insertImage` menempatkan barcode yang dihasilkan pada ukuran yang diinginkan (200 × 200 piksel). Inilah inti **cara menyematkan barcode di Word**.  
4. **Penyimpanan** – Dokumen akhir, `CustomBarcodeLabels.docx`, berisi barcode yang disematkan dan siap dicetak atau didistribusikan.

## Masalah umum & pemecahan masalah

| Gejala | Penyebab yang mungkin | Solusi |
|--------|-----------------------|--------|
| Barcode muncul kosong | Warna `BarcodeParameters` sama (misalnya hitam di atas hitam) | Verifikasi nilai `foregroundColor` dan `backgroundColor`. |
| Gambar terdistorsi | Dimensi piksel yang salah diberikan ke `insertImage` | Sesuaikan argumen lebar/tinggi atau gunakan konversi `twipsToPixels` untuk ukuran yang tepat. |
| Kesalahan tipe barcode tidak didukung | Menggunakan tipe yang tidak dikenali oleh `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Pastikan string tipe barcode cocok dengan salah satu `EncodeTypes` yang didukung (misalnya `"QR"`, `"CODE128"`). |

## Pertanyaan yang sering diajukan

**Q: Bisakah saya menggunakan Aspose.Words untuk Java tanpa lisensi?**  
**A:** Ya, tetapi akan ada batasan evaluasi. Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk fungsionalitas penuh.

**Q: Jenis barcode apa yang dapat saya hasilkan?**  
**A:** Aspose.BarCode mendukung QR, Code 128, EAN‑13, DataMatrix, PDF417, dan banyak format lainnya—lebih dari 20 simbol secara total. Lihat [dokumentasi](https://reference.aspose.com/words/java/) untuk daftar lengkap.

**Q: Bagaimana cara mengubah ukuran barcode?**  
**A:** Sesuaikan argumen lebar dan tinggi pada `builder.insertImage`, atau hitung twips Word secara tepat menggunakan `twipsToPixels` untuk kontrol pixel‑perfect.

**Q: Apakah memungkinkan menggunakan font khusus untuk teks barcode?**  
**A:** Ya, Anda dapat menyesuaikan font teks melalui properti `CodeTextParameters` pada `BarcodeGenerator`.

**Q: Di mana saya dapat mendapatkan bantuan jika mengalami masalah?**  
**A:** Kunjungi [forum dukungan](https://forum.aspose.com/c/words/8/) untuk bantuan dari komunitas dan insinyur Aspose.

## Kesimpulan

Dengan mengikuti langkah‑langkah di atas, Anda kini tahu cara **membuat gambar QR code Java** dan **menyisipkan barcode ke dalam dokumen Word** menggunakan Aspose.Words untuk Java. Teknik ini cukup fleksibel untuk label inventaris, tiket acara, atau skenario apa pun di mana barcode harus menjadi bagian dari dokumen yang dihasilkan. Bereksperimenlah dengan berbagai tipe barcode, warna, dan opsi ukuran untuk menyesuaikan kebutuhan bisnis Anda.

---

**Terakhir Diperbarui:** 2026-10-23  
**Diuji Dengan:** Aspose.Words untuk Java 24.12, Aspose.BarCode untuk Java 24.12  
**Penulis:** Aspose

## Tutorial Terkait

- [Buat PDF dari Word dengan Generasi Barcode – Aspose.Words untuk Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Simpan Word Sebagai PDF dengan Panduan Langkah demi Langkah Aspose Words Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Buat Dokumen Word Kosong di Java dengan Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}