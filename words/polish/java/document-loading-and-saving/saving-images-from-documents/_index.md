---
title: Zapisywanie obrazów z dokumentów w Aspose.Words dla Java
linktitle: Zapisywanie obrazów z dokumentów
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak zapisywać obrazy z dokumentów za pomocą Aspose.Words for Java dzięki naszemu kompleksowemu przewodnikowi krok po kroku. Dostosuj formaty, kompresję i nie tylko.
weight: 17
url: /pl/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisywanie obrazów z dokumentów w Aspose.Words dla Java


## Wprowadzenie do zapisywania obrazów z dokumentów w Aspose.Words dla Java

W tym samouczku pokażemy, jak zapisywać obrazy z dokumentów za pomocą Aspose.Words for Java. Omówimy różne scenariusze i opcje dostosowywania zapisywania obrazów. Ten przewodnik zawiera instrukcje krok po kroku z przykładami kodu źródłowego.

## Wymagania wstępne

 Zanim zaczniesz, upewnij się, że biblioteka Aspose.Words for Java jest zintegrowana z Twoim projektem. Możesz ją pobrać ze strony[Tutaj](https://releases.aspose.com/words/java/).

## Krok 1: Zapisywanie obrazów jako TIFF z kontrolą progu

Aby zapisać obrazy w formacie TIFF z kontrolą progu, wykonaj następujące kroki:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Krok 2: Zapisywanie określonej strony jako wielostronicowego pliku TIFF

Aby zapisać konkretną stronę jako wielostronicowy plik TIFF, użyj następującego kodu:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Krok 3: Zapisywanie obrazów jako 1 BPP indeksowanych plików PNG

Aby zapisać obrazy jako pliki PNG z indeksem 1 BPP, wykonaj następujące czynności:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Krok 4: Zapisywanie strony jako JPEG z dostosowaniem

Aby zapisać konkretną stronę w formacie JPEG z opcjami dostosowywania, użyj tego kodu:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Krok 5: Korzystanie z funkcji wywołania zwrotnego zapisywania strony

Możesz użyć wywołania zwrotnego, aby dostosować zapisywanie strony. Oto przykład:

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

## Kompletny kod źródłowy do zapisywania obrazów z dokumentów w Aspose.Words dla Java

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
	// Ustaw „PageSet” na „0”, aby przekonwertować tylko pierwszą stronę dokumentu.
	options.setPageSet(new PageSet(0));
	// Zmień jasność i kontrast obrazu.
	// Oba są w skali 0-1 i domyślnie mają wartość 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Zmień rozdzielczość poziomą.
	// Wartość domyślna tych właściwości wynosi 96,0 dla rozdzielczości 96 dpi.
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

## Wniosek

Nauczyłeś się, jak zapisywać obrazy z dokumentów za pomocą Aspose.Words for Java. Te przykłady pokazują różne opcje dostosowywania zapisywania obrazów, w tym format, kompresję i użycie wywołania zwrotnego. Odkryj więcej możliwości dzięki potężnym możliwościom Aspose.Words for Java.

## Najczęściej zadawane pytania

### Jak zmienić format obrazu podczas zapisywania go za pomocą Aspose.Words dla Java?

 Możesz zmienić format obrazu, określając żądany format w`ImageSaveOptions` Na przykład, aby zapisać jako PNG, użyj`SaveFormat.PNG` jak pokazano w kodzie:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Czy mogę dostosować ustawienia kompresji obrazów TIFF?

Tak, możesz dostosować ustawienia kompresji obrazu TIFF. Na przykład, aby ustawić metodę kompresji na CCITT_3, użyj następującego kodu:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Jak mogę zapisać konkretną stronę dokumentu jako osobny obraz?

 Aby zapisać konkretną stronę jako obraz, użyj`setPageSet`metoda w`ImageSaveOptions` Na przykład, aby zapisać tylko pierwszą stronę, ustaw`PageSet` Do`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Zapisz pierwszą stronę jako obraz
```

### Jak zastosować ustawienia niestandardowe do obrazów JPEG podczas ich zapisywania?

Możesz zastosować ustawienia niestandardowe do obrazów JPEG za pomocą`ImageSaveOptions`. Dostosuj właściwości takie jak jasność, kontrast i rozdzielczość. Na przykład, aby zmienić jasność na 0,3 i kontrast na 0,7, użyj tego kodu:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Jak mogę użyć funkcji wywołania zwrotnego w celu dostosowania zapisywania obrazu?

 Aby użyć funkcji wywołania zwrotnego w celu dostosowania zapisywania obrazu, ustaw`PageSavingCallback` W`ImageSaveOptions` . Utwórz klasę implementującą`IPageSavingCallback` interfejs i nadpisanie`pageSaving` metoda.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Następnie utwórz klasę implementującą`IPageSavingCallback` interfejs i dostosuj nazwę pliku i lokalizację w`pageSaving` metoda.

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
