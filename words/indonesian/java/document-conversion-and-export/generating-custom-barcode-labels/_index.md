---
date: 2026-02-09
description: Buat label barcode khusus menggunakan Aspose Barcode Java di Aspose.Words
  untuk Java. Pelajari cara menyisipkan barcode dalam dokumen Word dan menghasilkan
  contoh QR code Java.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Menghasilkan Label Barcode Kustom dengan Aspose Barcode Java
url: /id/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Label Barcode Kustom dengan Aspose Barcode Java

## Pengantar Membuat Label Barcode Kustom di Aspose.Words untuk Java

Barcode sangat penting dalam aplikasi modern, dan **Aspose Barcode Java** memungkinkannya dibuat secara langsung di dalam dokumen Word dengan mudah. Apakah Anda perlu **menyematkan kode batang di Word**, membuat kode QR untuk URL, atau mengonversi satu ukuran, tutorial ini akan memandu Anda melalui semua yang diperlukan. Siap memulai? Ayo!

## Jawaban Cepat
- **Perpustakaan apa yang membuat barcode di Java?** Aspose Barcode Java dipasangkan dengan Aspose.Words for Java.
- **Jenis barcode apa yang ditunjukkan?** Kode QR (menghasilkan kode qr java).
- **Bagaimana cara mengonversi twips ke piksel?** Gunakan metode utilitas `twipsToPixels` yang disediakan.
- ** meminta saya menambahkan barcode ke file Word yang sudah ada?** Ya – cukup gunakan metode `DocumentBuilder.insertImage`.
- **Apakah saya membutuhkan lisensi?** Lisensi sementara menghilangkan batasan evaluasi.

## Apa itu Aspose Barcode Java?
Aspose Barcode Java adalah API yang kuat yang memungkinkan pengembang menghasilkan berbagai barcode 1D dan 2D (termasuk kode QR) secara terprogram. Ketika digabungkan dengan Aspose.Words untuk Java, Anda dapat **menyematkan barcode di Word** dokumen tanpa meninggalkan lingkungan Java Anda.

## Mengapa menggunakan Aspose Barcode Java dengan Aspose.Words?
- **Kontrol penuh** atas tampilan barcode (warna, ukuran, format).
- **Integrasi mulus** – gambar barcode dapat disisipkan langsung ke dalam dokumen Word.
- **Lintas‑platform** – bekerja pada platform apa pun yang kompatibel dengan Java.
- **Dapat diisi** – Anda dapat membuat kelas utilitas untuk menggunakan kembali logika barcode di berbagai proyek.

## Prasyarat

Sebelum kita mulai menulis kode, pastikan Anda memiliki hal‑hal berikut:

- Java Development Kit (JDK): Versi 8 atau lebih tinggi.
- Aspose.Words untuk Java Library: [Unduh di sini](https://releases.aspose.com/words/java/).
- Aspose.BarCode untuk Java Library: [Unduh di sini](https://releases.aspose.com/).
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse, atau IDE apa pun yang Anda sukai.
- Lisensi Sementara: Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk akses tidak terbatas.

## Impor Paket

Kami akan menggunakan pustaka Aspose.Words dan Aspose.BarCode. Impor paket berikut ke dalam proyek Anda:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Impor ini memungkinkan kita memanfaatkan fitur pembuatan barcode dan mengintegrasikannya ke dalam dokumen Word.

Mari kita bagi tugas ini menjadi langkah‑langkah yang dapat dikelola.

## Langkah 1: Buat Kelas Utilitas untuk Operasi Barcode

Untuk memberikan operasi yang berhubungan dengan barcode, kami akan membuat kelas utilitas dengan metode bantu untuk tugas umum seperti konversi warna dan **convert twips to pixel**.

### Kode:

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

- `twipsToPixels` mengubah satuan ukuran yang digunakan Word (twips) menjadi piksel layar – bantuan yang berguna ketika Anda memerlukan ukuran yang tepat.
- `convertColor` mengubah string warna heksadesimal (mis., “FF0000”) menjadi objek Java `Color`, memungkinkan Anda menyesuaikan latar depan dan latar belakang barcode.

## Langkah 2: Terapkan Generator Kode Batang Khusus

Kami akan mengimplementasikan antarmuka `IBarcodeGenerator` sehingga Aspose.Words dapat meminta gambar barcode setiap kali menemukan bidang barcode.

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

**Penjelasan**

- `getBarcodeImage` membangun `BarcodeGenerator` menggunakan tipe **generate qr code java** yang Anda temukan (QR dalam contoh kami).
- Ia menerapkan warna latar depan dan latar belakang melalui metode utilitas, lalu mengembalikan gambar yang di-render.
- Gambar fallback memastikan program tetap berjalan meskipun pembuatan barcode gagal.

## Langkah 3: Buat Barcode dan Tambahkan ke Dokumen Word

Sekarang kami menggabungkan semuanya: membuat dokumen, menghasilkan barcode, dan **cara menambahkan barcode** ke file Word.

### Kode:

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

1. **Inisialisasi Dokumen** – membuat `Document` baru (atau Anda dapat memuat .docx yang sudah ada).
2. **Parameter Barcode** – menentukan tipe (`QR`), nilai, dan warna, menunjukkan penggunaan **menghasilkan kode qr java**.
3. **Penyisipan Gambar** – `builder.insertImage` menempatkan barcode di lokasi yang diinginkan, secara efektif menunjukkan **cara menambahkan barcode** ke file Word.
4. **Menyimpan** – dokumen akhir (`CustomBarcodeLabels.docx`) berisi barcode yang disematkan siap untuk dicetak atau didistribusikan.

## Masalah Umum dan Solusinya

| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Barcode muncul kosong | String warna tidak valid atau tipe barcode tidak didukung | Verifikasi format warna hex dan gunakan tipe yang didukung (mis., QR, Code128). |
| Ukuran gambar tidak tepat | Konversi piksel yang salah | Gunakan `twipsToPixels` untuk menghitung dimensi tepat berdasarkan tata letak Word. |
| Pengecualian lisensi | Tidak ada lisensi Aspose yang valid | Terapkan lisensi sementara atau berbayar sebelum menjalankan kode. |

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menggunakan Aspose.Words untuk Java tanpa lisensi?**
A: Ya, tetapi Anda akan mengalami batasan evaluasi. Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk fungsionalitas penuh.

**T: Jenis barcode apa yang dapat saya hasilkan?**
J: Aspose.BarCode mendukung QR, Code128, EAN‑13, dan masih banyak lagi. Lihat [dokumentasi] resmi(https://reference.aspose.com/words/java/) untuk daftar lengkapnya.

**T: Bagaimana saya dapat mengubah ukuran barcode?**
A: Sesuaikan parameter lebar/tinggi di `builder.insertImage` atau ubah properti `XDimension` dan `BarHeight` pada objek `BarcodeGenerator`.

**T: Bisakah saya menggunakan font khusus untuk bagian yang dapat dibaca manusia dari barcode?**
J: Tentu saja. Gunakan properti `CodeTextParameters` untuk mengatur jenis font, ukuran, dan gaya.

**T: Di mana saya dapat mendapatkan bantuan untuk Aspose.Words?**
J: Kunjungi [forum dukungan](https://forum.aspose.com/c/words/8/) untuk mendapatkan bantuan komunitas dan dukungan resmi.

---

**Terakhir Diperbarui:** 09-02-2026
**Diuji Dengan:** Aspose.Words untuk Java 24.12, Aspose.BarCode untuk Java 24.12
**Penulis:** Berasumsi  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}