---
"description": "Kapsamlı adım adım kılavuzumuzla Aspose.Words for Java'yı kullanarak belgelerden görüntüleri nasıl kaydedeceğinizi öğrenin. Biçimleri, sıkıştırmayı ve daha fazlasını özelleştirin."
"linktitle": "Belgelerden Görüntüleri Kaydetme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Aspose.Words for Java'da Belgelerden Görüntüleri Kaydetme"
"url": "/tr/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Belgelerden Görüntüleri Kaydetme


## Aspose.Words for Java'da Belgelerden Görüntüleri Kaydetmeye Giriş

Bu eğitimde, Aspose.Words for Java kullanarak belgelerden resimlerin nasıl kaydedileceğini inceleyeceğiz. Resim kaydetme için çeşitli senaryoları ve özelleştirme seçeneklerini ele alacağız. Bu kılavuz, kaynak kodu örnekleriyle adım adım talimatlar sağlar.

## Ön koşullar

Başlamadan önce, projenize Aspose.Words for Java kütüphanesinin entegre olduğundan emin olun. Bunu şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/).

## Adım 1: Eşik Kontrolü ile Görüntüleri TIFF Olarak Kaydetme

Görüntüleri eşik değeri kontrolüyle TIFF formatında kaydetmek için şu adımları izleyin:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Adım 2: Belirli Bir Sayfayı Çok Sayfalı TIFF Olarak Kaydetme

Belirli bir sayfayı çok sayfalı TIFF olarak kaydetmek için aşağıdaki kodu kullanın:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Adım 3: Görüntüleri 1 BPP Dizinli PNG Olarak Kaydetme

Görüntüleri 1 BPP dizinli PNG olarak kaydetmek için şu adımları izleyin:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Adım 4: Özelleştirme ile Bir Sayfayı JPEG Olarak Kaydetme

Belirli bir sayfayı özelleştirme seçenekleriyle JPEG olarak kaydetmek için şu kodu kullanın:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Adım 5: Sayfa Kaydetme Geri Aramasını Kullanma

Sayfa kaydetmeyi özelleştirmek için bir geri arama kullanabilirsiniz. İşte bir örnek:

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

## Aspose.Words for Java'da Belgelerden Görüntüleri Kaydetmek İçin Tam Kaynak Kodu

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
	// Belgenin yalnızca ilk sayfasını dönüştürmek için "PageSet" değerini "0" olarak ayarlayın.
	options.setPageSet(new PageSet(0));
	// Görüntünün parlaklığını ve kontrastını değiştirin.
	// Her ikisi de 0-1 ölçeğindedir ve varsayılan olarak 0,5'tir.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Yatay çözünürlüğü değiştirin.
	// Bu özelliklerin varsayılan değeri 96 dpi çözünürlük için 96.0'dır.
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

## Çözüm

Aspose.Words for Java kullanarak belgelerden görüntüleri nasıl kaydedeceğinizi öğrendiniz. Bu örnekler, biçim, sıkıştırma ve geri arama kullanımı dahil olmak üzere görüntü kaydetme için çeşitli özelleştirme seçeneklerini göstermektedir. Aspose.Words for Java'nın güçlü yetenekleriyle daha fazla olasılığı keşfedin.

## SSS

### Aspose.Words for Java ile kaydederken görüntü formatını nasıl değiştirebilirim?

İstediğiniz formatı belirterek görüntü formatını değiştirebilirsiniz. `ImageSaveOptions`Örneğin, PNG olarak kaydetmek için şunu kullanın: `SaveFormat.PNG` kodda gösterildiği gibi:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### TIFF resimler için sıkıştırma ayarlarını özelleştirebilir miyim?

Evet, TIFF resim sıkıştırma ayarlarını özelleştirebilirsiniz. Örneğin, sıkıştırma yöntemini CCITT_3 olarak ayarlamak için aşağıdaki kodu kullanın:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Bir belgenin belirli bir sayfasını ayrı bir resim olarak nasıl kaydedebilirim?

Belirli bir sayfayı resim olarak kaydetmek için şunu kullanın: `setPageSet` yöntem `ImageSaveOptions`Örneğin, yalnızca ilk sayfayı kaydetmek için, `PageSet` ile `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // İlk sayfayı resim olarak kaydet
```

### JPEG resimleri kaydederken özel ayarları nasıl uygularım?

JPEG görüntülerine özel ayarlar uygulamak için şunları kullanabilirsiniz: `ImageSaveOptions`. Parlaklık, kontrast ve çözünürlük gibi özellikleri ayarlayın. Örneğin, parlaklığı 0,3'e ve kontrastı 0,7'ye değiştirmek için şu kodu kullanın:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Resim kaydetmeyi özelleştirmek için geri aramayı nasıl kullanabilirim?

Görüntü kaydetmeyi özelleştirmek için bir geri arama kullanmak üzere, şunu ayarlayın: `PageSaviçindegCallback` in `ImageSaveOptions`. Aşağıdakileri uygulayan bir sınıf oluşturun: `IPageSavingCallback` arayüz ve geçersiz kılma `pageSaving` yöntem.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Daha sonra, aşağıdakileri uygulayan bir sınıf oluşturun: `IPageSavingCallback` arayüz ve dosya adını ve konumunu özelleştirin `pageSaving` yöntem.

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