---
date: 2025-12-10
description: Pelajari cara membuat label kode batang khusus menggunakan Aspose.Words
  untuk Java. Panduan langkah demi langkah ini menunjukkan cara menyisipkan kode batang
  dalam dokumen Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Buat Label Barcode Kustom di Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat Label Barcode Kustom di Aspose.Words untuk Java

## Pendahuluan tentang membuat barcode kustom di Aspose.Words untuk Java

Barcode sangat penting dalam aplikasi modern—baik mengelola inventaris, mencetak tiket, atau membuat kartu identitas. Pada tutorial ini Anda akan **membuat label barcode kustom** dan menyematkannya langsung ke dalam dokumen Word menggunakan antarmuka `IBarcodeGenerator`. Kami akan membimbing Anda melalui setiap langkah, mulai dari menyiapkan lingkungan hingga menyisipkan gambar barcode, sehingga Anda dapat mulai menggunakan barcode dalam proyek Java Anda segera.

## Jawaban Cepat
- **Apa yang diajarkan tutorial ini?** Cara membuat label barcode kustom dan menyematkannya dalam file Word dengan Aspose.Words untuk Java.  
- **Jenis barcode apa yang digunakan dalam contoh?** QR code (Anda dapat menggantinya dengan jenis yang didukung lainnya).  
- **Apakah saya memerlukan lisensi?** Lisensi sementara diperlukan untuk akses tanpa batas selama pengembangan.  
- **Versi Java apa yang dibutuhkan?** JDK 8 atau lebih tinggi.  
- **Bisakah saya mengubah ukuran atau warna barcode?** Ya—modifikasi pengaturan `BarcodeParameters` dan `BarcodeGenerator`.

## Prasyarat

Sebelum kita mulai menulis kode, pastikan Anda memiliki hal‑hal berikut:

- Java Development Kit (JDK): Versi 8 atau lebih tinggi.  
- Aspose.Words untuk Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode untuk Java Library: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse, atau IDE lain yang Anda sukai.  
- Lisensi Sementara: Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk akses tanpa batas.

## Import Packages

Kami akan menggunakan pustaka Aspose.Words dan Aspose.BarCode. Impor paket‑paket berikut ke dalam proyek Anda:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Impor ini memberi kami akses ke API pembuatan barcode dan kelas dokumen Word yang diperlukan.

## Langkah 1: Buat Kelas Utilitas untuk Operasi Barcode

Agar kode utama tetap bersih, kami akan mengenkapsulasi helper umum—seperti **mengonversi twip ke piksel** dan **konversi warna hex**—dalam sebuah kelas utilitas.

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

- `twipsToPixels` – Word mengukur dimensi dalam **twip**; metode ini mengonversinya ke piksel layar, yang berguna ketika Anda perlu menentukan ukuran gambar barcode secara tepat.  
- `convertColor` – Mengubah string heksadesimal (misalnya `"FF0000"` untuk merah) menjadi objek `java.awt.Color`, memungkinkan Anda **menyisipkan barcode** dengan warna latar depan dan latar belakang yang disesuaikan.

## Langkah 2: Implementasikan Custom Barcode Generator

Sekarang kami akan mengimplementasikan antarmuka `IBarcodeGenerator`. Kelas ini akan bertanggung jawab menghasilkan gambar **generate qr code java**‑style yang dapat disisipkan oleh Aspose.Words.

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
- Metode ini juga menangani kesalahan secara elegan dengan mengembalikan gambar placeholder, memastikan proses pembuatan dokumen Word tidak pernah gagal.

## Langkah 3: Buat Barcode dan **sematkan barcode di Word**

Dengan generator yang siap, kita kini dapat menghasilkan gambar barcode dan **menyisipkannya ke dalam dokumen Word**.

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

1. **Inisialisasi Dokumen** – Membuat `Document` baru (atau Anda dapat memuat templat yang sudah ada).  
2. **Parameter Barcode** – Menentukan jenis barcode (`QR`), nilai yang akan dienkode, serta warna latar depan/latar belakang.  
3. **Penyisipan Gambar** – `builder.insertImage` menempatkan barcode yang dihasilkan pada ukuran yang diinginkan (200 × 200 piksel). Inilah inti **cara menyisipkan barcode** ke dalam file Word.  
4. **Penyimpanan** – Dokumen akhir, `CustomBarcodeLabels.docx`, berisi barcode yang disematkan dan siap dicetak atau didistribusikan.

## Mengapa membuat label barcode kustom dengan Aspose.Words?

- **Kontrol penuh** atas tampilan barcode (jenis, ukuran, warna).  
- **Integrasi mulus** – tidak perlu file gambar perantara; barcode dihasilkan di memori dan disisipkan langsung.  
- **Lintas‑platform** – bekerja pada sistem operasi apa pun yang mendukung Java, menjadikannya ideal untuk pembuatan dokumen sisi server.  
- **Skalabel** – Anda dapat melakukan loop pada sumber data untuk membuat ratusan label personalisasi dalam satu kali jalankan.

## Masalah Umum & Pemecahan Masalah

| Gejala | Penyebab Kemungkinan | Solusi |
|---------|----------------------|--------|
| Barcode muncul kosong | Warna `BarcodeParameters` sama (misalnya hitam di atas hitam) | Periksa nilai `foregroundColor` dan `backgroundColor`. |
| Gambar terdistorsi | Dimensi piksel yang diberikan ke `insertImage` salah | Sesuaikan argumen lebar/tinggi atau gunakan konversi `twipsToPixels` untuk ukuran yang tepat. |
| Kesalahan tipe barcode tidak didukung | Menggunakan tipe yang tidak dikenali oleh `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Pastikan string tipe barcode cocok dengan salah satu `EncodeTypes` yang didukung (misalnya `"QR"`, `"CODE128"`). |

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menggunakan Aspose.Words untuk Java tanpa lisensi?**  
J: Ya, tetapi akan ada beberapa batasan. Dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk fungsionalitas penuh.

**T: Jenis barcode apa saja yang dapat saya buat?**  
J: Aspose.BarCode mendukung QR, Code 128, EAN‑13, dan banyak format lainnya. Lihat [dokumentasi](https://reference.aspose.com/words/java/) untuk daftar lengkap.

**T: Bagaimana cara mengubah ukuran barcode?**  
J: Sesuaikan argumen lebar dan tinggi pada `builder.insertImage`, atau gunakan `twipsToPixels` untuk mengonversi satuan pengukuran Word ke piksel.

**T: Apakah saya dapat menggunakan font khusus untuk teks barcode?**  
J: Ya, Anda dapat menyesuaikan font teks melalui properti `CodeTextParameters` pada `BarcodeGenerator`.

**T: Di mana saya dapat mendapatkan bantuan jika mengalami masalah?**  
J: Kunjungi [forum dukungan](https://forum.aspose.com/c/words/8/) untuk bantuan dari komunitas dan insinyur Aspose.

## Kesimpulan

Dengan mengikuti langkah‑langkah di atas, Anda kini tahu cara **membuat gambar barcode kustom** dan **menyisipkan barcode ke dalam dokumen Word** menggunakan Aspose.Words untuk Java. Teknik ini cukup fleksibel untuk tag inventaris, tiket acara, atau skenario apa pun di mana barcode harus menjadi bagian dari dokumen yang dihasilkan. Bereksperimenlah dengan berbagai jenis barcode dan opsi gaya untuk menyesuaikannya dengan kebutuhan bisnis Anda.

---

**Terakhir Diperbarui:** 2025-12-10  
**Diuji Dengan:** Aspose.Words untuk Java 24.12, Aspose.BarCode untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}