---
date: 2025-12-27
description: Aspose.Words for Java kullanarak bir sayfayı JPEG olarak kaydetmeyi ve
  Word belgelerinden resim çıkarmayı öğrenin. Görüntü parlaklığı, çözünürlüğü ayarlama
  ve çok sayfalı TIFF oluşturma ipuçlarını içerir.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Sayfayı JPEG Olarak Kaydetme ve Belgelerden Görselleri
  Çıkarma
url: /tr/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sayfayı JPEG Olarak Kaydet ve Aspose.Words for Java ile Belgelerden Görselleri Çıkar

Bu öğreticide, bir Word belgesinden **sayfayı jpeg olarak kaydet** ve Aspose.Words for Java kullanarak **Word dosyalarından görselleri çıkar** nasıl yapılacağını keşfedeceksiniz. Görsel parlaklığını ayarlama, Java'da görüntü çözünürlüğünü düzenleme ve çok sayfalı TIFF oluşturma gibi gerçek dünya senaryolarını adım adım inceleyeceğiz. Her adım, kopyalayıp yapıştırarak anında sonuç alabileceğiniz çalıştırmaya hazır kod parçacıkları içerir.

## Hızlı Yanıtlar
- **Tek bir sayfayı JPEG olarak kaydedebilir miyim?** Evet – `ImageSaveOptions` ile `setPageSet(new PageSet(pageIndex))` kullanın.
- **Görsel parlaklığını nasıl değiştiririm?** `options.setImageBrightness(floatValue)` metodunu çağırın (0‑1 aralığı).
- **Çok sayfalı TIFF'e ihtiyacım olursa?** İstenen sayfaları kapsayan bir `PageSet` ayarlayın ve bir TIFF sıkıştırma yöntemi seçin.
- **Görsel çözünürlüğünü nasıl kontrol ederim?** `setResolution(floatDpi)` veya `setHorizontalResolution(floatDpi)` kullanın.
- **Üretim ortamında lisansa ihtiyacım var mı?** Deneme dışı kullanım için geçerli bir Aspose.Words lisansı gereklidir.

## “Sayfayı JPEG Olarak Kaydet” ne demektir?
Bir sayfayı JPEG olarak kaydetmek, Word belgesinin tek bir sayfasını raster bir görüntü dosyasına (JPEG) dönüştürmek anlamına gelir. Bu, ön izleme oluşturma, küçük resim üretme veya PDF görüntülemenin pratik olmadığı web sayfalarına belge sayfalarını yerleştirme gibi durumlarda faydalıdır.

## Word Belgelerinden Görselleri Neden Çıkaralım?
Birçok iş süreci, DOCX dosyasından orijinal grafiklerin (logolar, diyagramlar, fotoğraflar) yeniden kullanım, arşivleme veya analiz için çıkarılmasını gerektirir. Aspose.Words, her görseli kalite kaybı olmadan yerel formatında çıkarmayı kolaylaştırır.

## Önkoşullar
- Java Development Kit (JDK 8 veya üzeri) yüklü.
- Projenize Aspose.Words for Java kütüphanesini ekleyin. [buradan](https://releases.aspose.com/words/java/) indirebilirsiniz.
- Bilinen bir klasöre yerleştirilmiş örnek bir Word belgesi (ör. `Rendering.docx`).

## Adım 1: Eşik Kontrolü ile Görselleri TIFF Olarak Kaydet (Çok Sayfalı TIFF Oluştur)
Yüksek kontrastlı, gri tonlamalı bir TIFF oluşturmak için ikilileştirme eşiğini kontrol edebilirsiniz. Bu, belgenizin yazdırılabilir siyah‑beyaz bir versiyonuna ihtiyacınız olduğunda kullanışlıdır.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Adım 2: Belirli Bir Sayfayı Çok Sayfalı TIFF Olarak Kaydet
Sadece belirli sayfaları (ör. sayfalar 1‑2) içeren bir TIFF'e ihtiyacınız varsa, bir `PageSet` yapılandırın. Bu, **create multipage tiff** örneğini gösterir.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Adım 3: Görselleri 1 BPP İndeksli PNG Olarak Kaydet
Ultra hafif siyah‑beyaz PNG'lere (1 bit piksel başına) ihtiyacınız olduğunda, piksel formatını buna göre ayarlayın. Bu, düşük bant genişliğinde senaryolarda basit grafikleri yerleştirmek için faydalıdır.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Adım 4: Sayfayı JPEG Olarak Kaydet ve Özelleştir (Görsel Parlaklığı ve Çözünürlüğü Ayarla)
Burada **sayfayı jpeg olarak kaydediyoruz** ve aynı zamanda parlaklık, kontrast ve çözünürlüğü ayarlıyoruz—küçük resimler veya web için hazır ön izlemeler oluşturmak için mükemmeldir.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Adım 5: Sayfa‑Kaydetme Geri Çağrısı Kullanma (Gelişmiş Özelleştirme)
Bir geri çağrı, her çıktı dosyasını dinamik olarak yeniden adlandırmanıza olanak tanır; bu, birden fazla sayfayı aynı anda dışa aktarırken faydalıdır.

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

## Tüm Senaryolar İçin Tam Kaynak Kodu
Aşağıda, yukarıda gösterilen tüm yöntemleri içeren tek bir sınıf bulunmaktadır. Her testi ayrı ayrı çalıştırabilirsiniz.

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

## Yaygın Sorunlar ve Çözümleri
- **“Unable to locate the document file”** – Dosya yolunun işletim sisteminiz için doğru ayırıcıyı (`/` veya `\\`) kullandığından emin olun.
- **Görseller boş görünüyor** – Uygun bir `ImageColorMode` (ör. TIFF için `GRAYSCALE`) ayarladığınızdan emin olun.
- **Büyük belgelerde bellek yetersizliği hataları** – `PageSet` aralığını ayarlayarak sayfaları toplu işleyin.
- **JPEG kalitesi düşük görünüyor** – `setHorizontalResolution` veya `setResolution` ile çözünürlüğü artırın.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java ile kaydederken görüntü formatını nasıl değiştiririm?**  
C: `ImageSaveOptions` içinde istediğiniz formatı ayarlayın. PNG için, sadece `ImageSaveOptions` nesnesi oluşturup `SaveFormat.PNG` atayabilirsiniz.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**S: TIFF görüntüleri için sıkıştırma ayarlarını özelleştirebilir miyim?**  
C: Evet. `setTiffCompression` metodunu kullanarak `CCITT_3` gibi bir sıkıştırma algoritması seçebilirsiniz.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**S: Belgeden belirli bir sayfayı ayrı bir görüntü olarak nasıl kaydederim?**  
C: Tek bir sayfa indeksiyle `setPageSet` metodunu kullanın.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**S: JPEG görüntülerini kaydederken özel ayarları nasıl uygularım?**  
C: `ImageSaveOptions` aracılığıyla parlaklık, kontrast ve çözünürlük gibi özellikleri ayarlayın.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**S: Görüntü kaydetmeyi özelleştirmek için bir geri çağrıyı nasıl kullanabilirim?**  
C: `IPageSavingCallback` arayüzünü uygulayın ve `setPageSavingCallback` ile atayın.

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

## Sonuç
Artık **sayfayı jpeg olarak kaydet**, görselleri çıkart, görsel parlaklığını kontrol et, Java'da görüntü çözünürlüğünü ayarla ve Aspose.Words for Java ile çok sayfalı TIFF dosyaları oluşturmak için eksiksiz bir araç setine sahipsiniz. Projenizin gereksinimlerine uygun farklı `ImageSaveOptions` ayarlarıyla denemeler yapın ve daha fazla belge işleme yeteneği için geniş Aspose.Words API'sini keşfedin.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}