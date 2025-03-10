---
title: Membuat Label Barcode Kustom di Aspose.Words untuk Java
linktitle: Membuat Label Barcode Kustom
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Buat Label Barcode Kustom di Aspose.Words untuk Java. Pelajari cara membuat solusi barcode yang dipersonalisasi menggunakan Aspose.Words untuk Java dalam panduan langkah demi langkah ini.
weight: 10
url: /id/java/document-conversion-and-export/generating-custom-barcode-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Label Barcode Kustom di Aspose.Words untuk Java


## Pengantar Pembuatan Label Barcode Kustom di Aspose.Words untuk Java

Kode batang sangat penting dalam aplikasi modern, baik Anda mengelola inventaris, membuat tiket, atau membuat kartu identitas. Dengan Aspose.Words untuk Java, membuat label kode batang khusus menjadi mudah. Tutorial langkah demi langkah ini akan memandu Anda membuat label kode batang khusus menggunakan antarmuka IBarcodeGenerator. Siap untuk mencobanya? Ayo mulai!


## Prasyarat

Sebelum kita memulai pengkodean, pastikan Anda memiliki hal berikut:

- Java Development Kit (JDK): Versi 8 atau lebih tinggi.
-  Aspose.Words untuk Pustaka Java:[Unduh di sini](https://releases.aspose.com/words/java/).
-  Aspose.BarCode untuk Pustaka Java:[Unduh di sini](https://releases.aspose.com/).
- Lingkungan Pengembangan Terpadu (IDE): IntelliJ IDEA, Eclipse, atau IDE apa pun yang Anda sukai.
-  Lisensi Sementara: Dapatkan[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk akses tanpa batas.

## Paket Impor

Kami akan menggunakan pustaka Aspose.Words dan Aspose.BarCode. Impor paket berikut ke dalam proyek Anda:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Impor ini memungkinkan kita untuk memanfaatkan fitur pembuatan kode batang dan mengintegrasikannya ke dalam dokumen Word.

Mari kita bagi tugas ini menjadi langkah-langkah yang dapat dikelola.

## Langkah 1: Buat Kelas Utilitas untuk Operasi Kode Batang

Untuk menyederhanakan operasi terkait kode batang, kita akan membuat kelas utilitas dengan metode pembantu untuk tugas umum seperti konversi warna dan penyesuaian ukuran.

### Kode:

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Dengan asumsi DPI default adalah 96
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

### Penjelasan:

- `twipsToPixels` Metode: Mengubah twips (digunakan dalam dokumen Word) menjadi piksel.
- `convertColor` Metode: Menerjemahkan kode warna heksadesimal ke`Color` objek.

## Langkah 2: Terapkan Generator Kode Batang Kustom

 Kami akan menerapkan`IBarcodeGenerator` antarmuka untuk menghasilkan kode batang dan mengintegrasikannya dengan Aspose.Words.

### Kode:

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

### Penjelasan:

- `getBarcodeImage` Metode:
  -  Menciptakan sebuah`BarcodeGenerator` contoh.
  - Mengatur warna kode batang, warna latar belakang, dan menghasilkan gambar.

## Langkah 3: Hasilkan Kode Batang dan Tambahkan ke Dokumen Word

Sekarang, kita akan mengintegrasikan generator kode batang kita ke dalam dokumen Word.

### Kode:

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Memuat atau membuat dokumen Word
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Siapkan generator kode batang khusus
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://contoh.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Hasilkan gambar kode batang
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Masukkan gambar kode batang ke dalam dokumen Word
        builder.insertImage(barcodeImage, 200, 200);

        // Simpan dokumen
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

### Penjelasan:

- Inisialisasi Dokumen: Buat atau muat dokumen Word.
- Parameter Kode Batang: Menentukan jenis, nilai, dan warna kode batang.
- Penyisipan Gambar: Tambahkan gambar kode batang yang dihasilkan ke dokumen Word.
- Simpan Dokumen: Simpan file dalam format yang diinginkan.

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat membuat dan menyematkan label kode batang kustom dalam dokumen Word menggunakan Aspose.Words untuk Java dengan mudah. Pendekatan ini fleksibel dan dapat disesuaikan dengan berbagai aplikasi. Selamat membuat kode!


## Tanya Jawab Umum

1. Dapatkah saya menggunakan Aspose.Words untuk Java tanpa lisensi?
 Ya, tetapi akan ada beberapa keterbatasan. Dapatkan[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk fungsionalitas penuh.

2. Jenis kode batang apa yang dapat saya buat?
Aspose.BarCode mendukung QR, Kode 128, EAN-13, dan banyak jenis lainnya. Periksa[dokumentasi](https://reference.aspose.com/words/java/) untuk daftar lengkap.

3. Bagaimana cara mengubah ukuran kode batang?
 Sesuaikan`XDimension` Dan`BarHeight` parameter dalam`BarcodeGenerator` pengaturan.

4. Bisakah saya menggunakan font khusus untuk kode batang?
 Ya, Anda dapat menyesuaikan font teks kode batang melalui`CodeTextParameters` milik.

5. Di mana saya bisa mendapatkan bantuan dengan Aspose.Words?
 Kunjungi[forum dukungan](https://forum.aspose.com/c/words/8/) untuk bantuan.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
