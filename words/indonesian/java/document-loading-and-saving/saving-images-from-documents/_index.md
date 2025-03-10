---
title: Menyimpan Gambar dari Dokumen di Aspose.Words untuk Java
linktitle: Menyimpan Gambar dari Dokumen
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara menyimpan gambar dari dokumen menggunakan Aspose.Words untuk Java dengan panduan langkah demi langkah yang komprehensif. Sesuaikan format, kompresi, dan banyak lagi.
weight: 17
url: /id/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyimpan Gambar dari Dokumen di Aspose.Words untuk Java


## Pengantar Menyimpan Gambar dari Dokumen di Aspose.Words untuk Java

Dalam tutorial ini, kita akan menjelajahi cara menyimpan gambar dari dokumen menggunakan Aspose.Words untuk Java. Kita akan membahas berbagai skenario dan opsi penyesuaian untuk penyimpanan gambar. Panduan ini menyediakan petunjuk langkah demi langkah dengan contoh kode sumber.

## Prasyarat

 Sebelum memulai, pastikan Anda telah mengintegrasikan pustaka Aspose.Words for Java ke dalam proyek Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/java/).

## Langkah 1: Menyimpan Gambar sebagai TIFF dengan Kontrol Ambang Batas

Untuk menyimpan gambar dalam format TIFF dengan kontrol ambang batas, ikuti langkah-langkah berikut:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Langkah 2: Menyimpan Halaman Tertentu sebagai TIFF Multihalaman

Untuk menyimpan halaman tertentu sebagai TIFF multihalaman, gunakan kode berikut:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Langkah 3: Menyimpan Gambar sebagai PNG Terindeks 1 BPP

Untuk menyimpan gambar sebagai PNG berindeks 1 BPP, ikuti langkah-langkah berikut:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Langkah 4: Menyimpan Halaman sebagai JPEG dengan Kustomisasi

Untuk menyimpan halaman tertentu sebagai JPEG dengan opsi penyesuaian, gunakan kode ini:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Langkah 5: Menggunakan Page Saving Callback

Anda dapat menggunakan panggilan balik untuk menyesuaikan penyimpanan halaman. Berikut contohnya:

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

## Kode Sumber Lengkap Untuk Menyimpan Gambar dari Dokumen di Aspose.Words untuk Java

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
	// Atur "PageSet" ke "0" untuk mengonversi hanya halaman pertama dokumen.
	options.setPageSet(new PageSet(0));
	// Ubah kecerahan dan kontras gambar.
	// Keduanya berada pada skala 0-1 dan secara default berada pada 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Ubah resolusi horizontal.
	// Nilai default untuk properti ini adalah 96.0, untuk resolusi 96dpi.
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

## Kesimpulan

Anda telah mempelajari cara menyimpan gambar dari dokumen menggunakan Aspose.Words untuk Java. Contoh-contoh ini menunjukkan berbagai opsi penyesuaian untuk penyimpanan gambar, termasuk format, kompresi, dan penggunaan callback. Jelajahi lebih banyak kemungkinan dengan kemampuan canggih Aspose.Words untuk Java.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengubah format gambar saat menyimpan dengan Aspose.Words untuk Java?

 Anda dapat mengubah format gambar dengan menentukan format yang diinginkan di`ImageSaveOptions` Misalnya, untuk menyimpan sebagai PNG, gunakan`SaveFormat.PNG` seperti yang ditunjukkan dalam kode:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Dapatkah saya menyesuaikan pengaturan kompresi untuk gambar TIFF?

Ya, Anda dapat menyesuaikan pengaturan kompresi gambar TIFF. Misalnya, untuk mengatur metode kompresi ke CCITT_3, gunakan kode berikut:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Bagaimana cara menyimpan halaman tertentu dari dokumen sebagai gambar terpisah?

 Untuk menyimpan halaman tertentu sebagai gambar, gunakan`setPageSet`metode dalam`ImageSaveOptions` Misalnya, untuk menyimpan hanya halaman pertama, atur`PageSet` ke`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Simpan halaman pertama sebagai gambar
```

### Bagaimana cara menerapkan pengaturan khusus pada gambar JPEG saat menyimpan?

Anda dapat menerapkan pengaturan khusus ke gambar JPEG menggunakan`ImageSaveOptions`. Sesuaikan properti seperti kecerahan, kontras, dan resolusi. Misalnya, untuk mengubah kecerahan menjadi 0,3 dan kontras menjadi 0,7, gunakan kode ini:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Bagaimana saya dapat menggunakan panggilan balik untuk menyesuaikan penyimpanan gambar?

 Untuk menggunakan panggilan balik untuk menyesuaikan penyimpanan gambar, atur`PageSavingCallback` di dalam`ImageSaveOptions` . Buatlah kelas yang mengimplementasikan`IPageSavingCallback` antarmuka dan mengganti`pageSaving` metode.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Kemudian, buatlah kelas yang mengimplementasikan`IPageSavingCallback` antarmuka dan menyesuaikan nama file dan lokasi di`pageSaving` metode.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
