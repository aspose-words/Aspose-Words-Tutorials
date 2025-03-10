---
title: Сохранение изображений из документов в Aspose.Words для Java
linktitle: Сохранение изображений из документов
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как сохранять изображения из документов с помощью Aspose.Words для Java с помощью нашего комплексного пошагового руководства. Настройте форматы, сжатие и многое другое.
weight: 17
url: /ru/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение изображений из документов в Aspose.Words для Java


## Введение в сохранение изображений из документов в Aspose.Words для Java

В этом руководстве мы рассмотрим, как сохранять изображения из документов с помощью Aspose.Words for Java. Мы рассмотрим различные сценарии и параметры настройки для сохранения изображений. Это руководство содержит пошаговые инструкции с примерами исходного кода.

## Предпосылки

 Прежде чем начать, убедитесь, что в ваш проект интегрирована библиотека Aspose.Words for Java. Вы можете загрузить ее с[здесь](https://releases.aspose.com/words/java/).

## Шаг 1: Сохранение изображений в формате TIFF с контролем порога

Чтобы сохранить изображения в формате TIFF с контролем порога, выполните следующие действия:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Шаг 2: Сохранение определенной страницы в виде многостраничного TIFF-файла

Чтобы сохранить определенную страницу в виде многостраничного TIFF, используйте следующий код:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Шаг 3: Сохранение изображений в формате PNG с индексацией 1 BPP

Чтобы сохранить изображения в формате PNG с индексацией 1 BPP, выполните следующие действия:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Шаг 4: Сохранение страницы в формате JPEG с настройкой

Чтобы сохранить определенную страницу в формате JPEG с возможностью настройки, используйте этот код:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Шаг 5: Использование обратного вызова сохранения страницы

Вы можете использовать обратный вызов для настройки сохранения страницы. Вот пример:

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

## Полный исходный код для сохранения изображений из документов в Aspose.Words для Java

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
	// Установите «PageSet» на «0», чтобы преобразовать только первую страницу документа.
	options.setPageSet(new PageSet(0));
	// Измените яркость и контрастность изображения.
	// Оба показателя имеют шкалу от 0 до 1 и по умолчанию равны 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Измените горизонтальное разрешение.
	// Значение по умолчанию для этих свойств — 96,0, что соответствует разрешению 96 точек на дюйм.
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

## Заключение

Вы узнали, как сохранять изображения из документов с помощью Aspose.Words for Java. Эти примеры демонстрируют различные параметры настройки для сохранения изображений, включая формат, сжатие и использование обратного вызова. Изучите больше возможностей с мощными возможностями Aspose.Words for Java.

## Часто задаваемые вопросы

### Как изменить формат изображения при сохранении с помощью Aspose.Words для Java?

 Вы можете изменить формат изображения, указав желаемый формат в`ImageSaveOptions` . Например, чтобы сохранить в формате PNG, используйте`SaveFormat.PNG` как показано в коде:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Могу ли я настроить параметры сжатия для изображений TIFF?

Да, вы можете настроить параметры сжатия изображений TIFF. Например, чтобы задать метод сжатия CCITT_3, используйте следующий код:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Как сохранить определенную страницу документа как отдельное изображение?

 Чтобы сохранить определенную страницу как изображение, используйте`setPageSet`метод в`ImageSaveOptions` . Например, чтобы сохранить только первую страницу, установите`PageSet` к`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Сохранить первую страницу как изображение
```

### Как применить пользовательские настройки к изображениям JPEG при сохранении?

Вы можете применять пользовательские настройки к изображениям JPEG, используя`ImageSaveOptions`. Отрегулируйте такие свойства, как яркость, контрастность и разрешение. Например, чтобы изменить яркость на 0,3 и контрастность на 0,7, используйте этот код:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Как использовать обратный вызов для настройки сохранения изображений?

 Чтобы использовать обратный вызов для настройки сохранения изображения, установите`PageSavingCallback` в`ImageSaveOptions` . Создайте класс, реализующий`IPageSavingCallback` интерфейс и переопределить`pageSaving` метод.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Затем создайте класс, реализующий`IPageSavingCallback` интерфейс и настройте имя файла и его местоположение в`pageSaving` метод.

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
