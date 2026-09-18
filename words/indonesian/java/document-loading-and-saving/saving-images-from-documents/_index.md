---
date: 2025-12-27
description: Pelajari cara menyimpan halaman sebagai JPEG dan mengekstrak gambar dari
  dokumen Word menggunakan Aspose.Words untuk Java. Termasuk tips untuk mengatur kecerahan
  gambar, resolusi, dan membuat TIFF multi‑halaman.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Cara Menyimpan Halaman sebagai JPEG dan Mengekstrak Gambar dari Dokumen dengan
  Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Simpan halaman sebagai JPEG dan Ekstrak Gambar dari Dokumen di Aspose.Words untuk Java

Dalam tutorial ini Anda akan menemukan cara **save page as jpeg** dari dokumen Word dan cara **extract images from Word** menggunakan Aspose.Words untuk Java. Kami akan membahas skenario dunia nyata seperti mengatur kecerahan gambar, menyesuaikan resolusi gambar di Java, dan membuat TIFF multipage. Setiap langkah menyertakan potongan kode siap‑jalankan sehingga Anda dapat menyalin, menempel, dan melihat hasil secara instan.

## Jawaban Cepat
- **Can I save a single page as JPEG?** Ya – gunakan `ImageSaveOptions` dengan `setPageSet(new PageSet(pageIndex))`.
- **How do I change image brightness?** Bagaimana cara mengubah kecerahan gambar? Panggil `options.setImageBrightness(floatValue)` (rentang 0‑1).
- **What if I need a multipage TIFF?** Bagaimana jika saya membutuhkan TIFF multipage? Atur `PageSet` yang mencakup halaman yang diinginkan dan pilih metode kompresi TIFF.
- **How can I control image resolution?** Bagaimana cara mengontrol resolusi gambar? Gunakan `setResolution(floatDpi)` atau `setHorizontalResolution(floatDpi)`.
- **Do I need a license for production?** Apakah saya memerlukan lisensi untuk produksi? Lisensi Aspose.Words yang valid diperlukan untuk penggunaan non‑trial.

## Apa itu “save page as jpeg”?
Menyimpan halaman sebagai JPEG berarti mengonversi satu halaman dokumen Word menjadi file gambar raster (JPEG). Ini berguna untuk pembuatan pratinjau, pembuatan thumbnail, atau menyematkan halaman dokumen dalam halaman web di mana rendering PDF tidak praktis.

## Mengapa mengekstrak gambar dari dokumen Word?
Banyak alur kerja bisnis memerlukan pengambilan grafik asli (logo, diagram, foto) dari file DOCX untuk digunakan kembali, pengarsipan, atau analisis. Aspose.Words memudahkan mengekstrak setiap gambar dalam format aslinya tanpa kehilangan kualitas.

## Prasyarat
- Java Development Kit (JDK 8 atau lebih baru) terpasang.
- Pustaka Aspose.Words untuk Java ditambahkan ke proyek Anda. Unduh dari [here](https://releases.aspose.com/words/java/).
- Dokumen Word contoh (misalnya `Rendering.docx`) ditempatkan di direktori yang diketahui.

## Langkah 1: Simpan Gambar sebagai TIFF dengan Kontrol Threshold (Buat TIFF Multipage)
Untuk menghasilkan TIFF grayscale dengan kontras tinggi, Anda dapat mengontrol ambang binarisasi. Ini berguna ketika Anda membutuhkan versi cetak hitam‑putih dari dokumen Anda.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Langkah 2: Simpan Halaman Tertentu sebagai TIFF Multipage
Jika Anda memerlukan TIFF yang hanya berisi subset halaman (misalnya, halaman 1‑2), konfigurasikan `PageSet`. Ini mendemonstrasikan **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Langkah 3: Simpan Gambar sebagai PNG Indexed 1 BPP
Ketika Anda memerlukan PNG hitam‑putih yang sangat ringan (1 bit per piksel), atur format piksel yang sesuai. Ini berguna untuk menyematkan grafik sederhana dalam skenario bandwidth rendah.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Langkah 4: Simpan Halaman sebagai JPEG dengan Kustomisasi (Atur Kecerahan Gambar & Resolusi)
Di sini kami **save page as jpeg** sambil menyesuaikan kecerahan, kontras, dan resolusi—sempurna untuk membuat thumbnail atau pratinjau siap‑web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Langkah 5: Menggunakan Callback Penyimpanan Halaman (Kustomisasi Lanjutan)
Callback memungkinkan Anda mengganti nama setiap file output secara dinamis, yang berguna saat mengekspor banyak halaman sekaligus.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Kode Sumber Lengkap untuk Semua Skenario
Berikut adalah satu kelas yang berisi setiap metode yang ditunjukkan di atas. Anda dapat menjalankan setiap tes secara terpisah.

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Masalah Umum dan Solusinya
- **“Unable to locate the document file”** – Verifikasi bahwa path file menggunakan pemisah yang benar (`/` atau `\\`) untuk OS Anda.
- **Images appear blank** – Pastikan Anda mengatur `ImageColorMode` yang sesuai (misalnya, `GRAYSCALE` untuk TIFF).
- **Out‑of‑memory errors on large documents** – Proses halaman dalam batch dengan menyesuaikan rentang `PageSet`.
- **JPEG quality looks poor** – Tingkatkan resolusi dengan `setHorizontalResolution` atau `setResolution`.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara mengubah format gambar saat menyimpan dengan Aspose.Words untuk Java?**  
A: Atur format yang diinginkan dalam `ImageSaveOptions`. Untuk PNG, Anda cukup menginstansiasi `ImageSaveOptions` dan menetapkan `SaveFormat.PNG` jika diperlukan.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Apakah saya dapat menyesuaikan pengaturan kompresi untuk gambar TIFF?**  
A: Ya. Gunakan `setTiffCompression` untuk memilih algoritma kompresi seperti `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Bagaimana saya dapat menyimpan halaman tertentu dari dokumen sebagai gambar terpisah?**  
A: Gunakan metode `setPageSet` dengan indeks halaman tunggal.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Bagaimana cara menerapkan pengaturan khusus pada gambar JPEG saat menyimpan?**  
A: Sesuaikan properti seperti kecerahan, kontras, dan resolusi melalui `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Bagaimana saya dapat menggunakan callback untuk menyesuaikan penyimpanan gambar?**  
A: Implementasikan `IPageSavingCallback` dan tetapkan dengan `setPageSavingCallback`.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Kesimpulan
Anda kini memiliki kotak alat lengkap untuk **saving page as jpeg**, mengekstrak gambar, mengontrol kecerahan gambar, mengatur resolusi gambar di Java, dan membuat file TIFF multipage dengan Aspose.Words untuk Java. Bereksperimenlah dengan berbagai pengaturan `ImageSaveOptions` untuk menyesuaikan kebutuhan proyek Anda, dan jelajahi API Aspose.Words yang lebih luas untuk kemampuan manipulasi dokumen yang lebih banyak.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}