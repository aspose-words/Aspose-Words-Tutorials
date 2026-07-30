---
date: 2025-12-27
description: Узнайте, как сохранять страницу в формате JPEG и извлекать изображения
  из документов Word с помощью Aspose.Words для Java. Включает советы по настройке
  яркости изображения, разрешения и созданию многостраничных TIFF.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Как сохранить страницу в JPEG и извлечь изображения из документов с помощью
  Aspose.Words для Java
url: /ru/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить страницу как JPEG и извлечь изображения из документов в Aspose.Words for Java

## Быстрые ответы
- **Могу ли я сохранить отдельную страницу как JPEG?** Да — используйте `ImageSaveOptions` с `setPageSet(new PageSet(pageIndex))`.
- **Как изменить яркость изображения?** Вызовите `options.setImageBrightness(floatValue)` (диапазон 0‑1).
- **Что делать, если нужен многостраничный TIFF?** Установите `PageSet`, охватывающий нужные страницы, и выберите метод сжатия TIFF.
- **Как контролировать разрешение изображения?** Используйте `setResolution(floatDpi)` или `setHorizontalResolution(floatDpi)`.
- **Нужна ли лицензия для продакшн?** Для использования без пробного периода требуется действующая лицензия Aspose.Words.

## Что такое «save page as jpeg»?
Сохранение страницы как JPEG означает преобразование отдельной страницы документа Word в растровый файл изображения (JPEG). Это полезно для создания предварительных просмотров, миниатюр или встраивания страниц документа в веб‑страницы, где рендеринг PDF непрактичен.

## Почему извлекать изображения из документов Word?
Во многих бизнес‑процессах требуется извлекать оригинальные графические элементы (логотипы, схемы, фотографии) из файла DOCX для повторного использования, архивирования или анализа. Aspose.Words упрощает извлечение каждого изображения в его исходном формате без потери качества.

## Требования
- Установлен Java Development Kit (JDK 8 или новее).
- Библиотека Aspose.Words for Java добавлена в ваш проект. Скачайте её [здесь](https://releases.aspose.com/words/java/).
- Пример документа Word (например, `Rendering.docx`) размещён в известной директории.

## Шаг 1: Сохранить изображения как TIFF с управлением порогом (создание многостраничного TIFF)
Чтобы создать высококонтрастный, градационный TIFF, вы можете управлять порогом бинаризации. Это удобно, когда требуется печатная чёрно‑белая версия документа.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Шаг 2: Сохранить определённую страницу как многостраничный TIFF
Если нужен TIFF, содержащий только часть страниц (например, страницы 1‑2), настройте `PageSet`. Это демонстрирует **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Шаг 3: Сохранить изображения как 1‑битный индексированный PNG
Когда требуются ультра‑лёгкие чёрно‑белые PNG (1 бит на пиксель), задайте соответствующий формат пикселей. Это полезно для встраивания простых графических элементов в условиях ограниченной пропускной способности.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Шаг 4: Сохранить страницу как JPEG с настройкой (яркость и разрешение изображения)
Здесь мы **save page as jpeg**, одновременно регулируя яркость, контраст и разрешение — идеально для создания миниатюр или веб‑готовых превью.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Шаг 5: Использование обратного вызова при сохранении страниц (расширенная настройка)
Обратный вызов позволяет динамически переименовывать каждый файл вывода, что удобно при одновременном экспорте множества страниц.

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

## Полный исходный код для всех сценариев
Ниже представлен один класс, содержащий все продемонстрированные выше методы. Вы можете запускать каждый тест отдельно.

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

## Распространённые проблемы и их решения
- **«Unable to locate the document file»** — Убедитесь, что путь к файлу использует правильный разделитель (`/` или `\\`) для вашей ОС.
- **Изображения отображаются пустыми** — Убедитесь, что задали подходящий `ImageColorMode` (например, `GRAYSCALE` для TIFF).
- **Ошибки нехватки памяти при работе с большими документами** — Обрабатывайте страницы пакетами, изменяя диапазон `PageSet`.
- **Качество JPEG выглядит плохим** — Увеличьте разрешение с помощью `setHorizontalResolution` или `setResolution`.

## Часто задаваемые вопросы

**В: Как изменить формат изображения при сохранении с помощью Aspose.Words for Java?**  
О: Установите нужный формат в `ImageSaveOptions`. Для PNG можно просто создать `ImageSaveOptions` и задать `SaveFormat.PNG`, если требуется.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**В: Можно ли настроить параметры сжатия для TIFF‑изображений?**  
О: Да. Используйте `setTiffCompression`, чтобы выбрать алгоритм сжатия, например `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**В: Как сохранить отдельную страницу документа как отдельное изображение?**  
О: Используйте метод `setPageSet` с индексом одной страницы.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**В: Как применить пользовательские настройки к JPEG‑изображениям при сохранении?**  
О: Настройте свойства, такие как яркость, контраст и разрешение, через `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**В: Как использовать обратный вызов для настройки сохранения изображений?**  
О: Реализуйте `IPageSavingCallback` и назначьте его с помощью `setPageSavingCallback`.

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

## Заключение
Теперь у вас есть полноценный набор инструментов для **saving page as jpeg**, извлечения изображений, управления яркостью изображения, установки разрешения изображения в Java и создания многостраничных TIFF‑файлов с помощью Aspose.Words for Java. Экспериментируйте с различными настройками `ImageSaveOptions`, чтобы подобрать оптимальные параметры для вашего проекта, и изучайте более широкий API Aspose.Words для ещё большего спектра возможностей работы с документами.

---

**Последнее обновление:** 2025-12-27  
**Тестировано с:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}