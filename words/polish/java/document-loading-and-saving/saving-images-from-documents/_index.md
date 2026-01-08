---
date: 2025-12-27
description: Dowiedz się, jak zapisać stronę jako JPEG i wyodrębnić obrazy z dokumentów
  Word przy użyciu Aspose.Words for Java. Zawiera wskazówki dotyczące ustawiania jasności
  obrazu, rozdzielczości oraz tworzenia wielostronicowego pliku TIFF.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Jak zapisać stronę jako JPEG i wyodrębnić obrazy z dokumentów przy użyciu Aspose.Words
  dla Javy
url: /pl/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz stronę jako JPEG i wyodrębnij obrazy z dokumentów w Aspose.Words dla Java

W tym samouczku dowiesz się, jak **save page as jpeg** z dokumentu Word oraz jak **extract images from Word** przy użyciu Aspose.Words dla Java. Przejdziemy przez rzeczywiste scenariusze, takie jak ustawianie jasności obrazu, dostosowywanie rozdzielczości obrazu w Javie oraz tworzenie wielostronicowego TIFF. Każdy krok zawiera gotowe do uruchomienia fragmenty kodu, które możesz skopiować, wkleić i od razu zobaczyć wyniki.

## Szybkie odpowiedzi
- **Czy mogę zapisać pojedynczą stronę jako JPEG?** Tak – użyj `ImageSaveOptions` z `setPageSet(new PageSet(pageIndex))`.
- **Jak zmienić jasność obrazu?** Wywołaj `options.setImageBrightness(floatValue)` (zakres 0‑1).
- **Co zrobić, jeśli potrzebuję wielostronicowego TIFF?** Ustaw `PageSet` obejmujący żądane strony i wybierz metodę kompresji TIFF.
- **Jak kontrolować rozdzielczość obrazu?** Użyj `setResolution(floatDpi)` lub `setHorizontalResolution(floatDpi)`.
- **Czy potrzebna jest licencja do produkcji?** Wymagana jest ważna licencja Aspose.Words do użytku nie‑trial.

## Co to jest „save page as jpeg”?
Zapisanie strony jako JPEG oznacza konwersję pojedynczej strony dokumentu Word do pliku obrazu rastrowego (JPEG). Jest to przydatne do generowania podglądów, tworzenia miniatur lub osadzania stron dokumentu w stronach internetowych, gdzie renderowanie PDF nie jest praktyczne.

## Dlaczego wyodrębniać obrazy z dokumentów Word?
Wiele procesów biznesowych wymaga wyciągnięcia oryginalnych grafik (logo, diagramy, zdjęcia) z pliku DOCX w celu ponownego użycia, archiwizacji lub analizy. Aspose.Words umożliwia łatwe wyodrębnienie każdego obrazu w jego natywnym formacie bez utraty jakości.

## Wymagania wstępne
- Zainstalowany Java Development Kit (JDK 8 lub nowszy).
- Biblioteka Aspose.Words dla Java dodana do projektu. Pobierz ją z [tutaj](https://releases.aspose.com/words/java/).
- Przykładowy dokument Word (np. `Rendering.docx`) umieszczony w znanym katalogu.

## Krok 1: Zapisz obrazy jako TIFF z kontrolą progu (Utwórz wielostronicowy TIFF)
Aby wygenerować wysokokontrastowy, szary TIFF, możesz kontrolować próg binaryzacji. Jest to przydatne, gdy potrzebujesz drukowanej, czarno‑białej wersji dokumentu.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Krok 2: Zapisz określoną stronę jako wielostronicowy TIFF
Jeśli potrzebujesz TIFF zawierającego tylko podzbiór stron (np. strony 1‑2), skonfiguruj `PageSet`. To demonstruje **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Krok 3: Zapisz obrazy jako 1 BPP Indexed PNG
Gdy potrzebujesz ultralekkich czarno‑białych PNG (1 bit na piksel), ustaw odpowiedni format pikseli. Jest to przydatne przy osadzaniu prostych grafik w scenariuszach o niskiej przepustowości.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Krok 4: Zapisz stronę jako JPEG z dostosowaniem (Ustaw jasność obrazu i rozdzielczość)
Tutaj **save page as jpeg** przy jednoczesnym dostosowywaniu jasności, kontrastu i rozdzielczości — idealne do tworzenia miniatur lub podglądów gotowych do sieci.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Krok 5: Użycie wywołania zwrotnego przy zapisywaniu stron (Zaawansowane dostosowanie)
Wywołanie zwrotne pozwala dynamicznie zmieniać nazwę każdego pliku wyjściowego, co jest przydatne przy eksportowaniu wielu stron jednocześnie.

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

## Pełny kod źródłowy dla wszystkich scenariuszy
Poniżej znajduje się pojedyncza klasa zawierająca wszystkie metody pokazane powyżej. Każdy test możesz uruchomić osobno.

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

## Typowe problemy i rozwiązania
- **„Unable to locate the document file”** – Sprawdź, czy ścieżka do pliku używa właściwego separatora (`/` lub `\\`) dla Twojego systemu operacyjnego.
- **Obrazy są puste** – Upewnij się, że ustawiłeś odpowiedni `ImageColorMode` (np. `GRAYSCALE` dla TIFF).
- **Błędy braku pamięci przy dużych dokumentach** – Przetwarzaj strony w partiach, dostosowując zakres `PageSet`.
- **Jakość JPEG jest słaba** – Zwiększ rozdzielczość za pomocą `setHorizontalResolution` lub `setResolution`.

## Najczęściej zadawane pytania

**Q: Jak zmienić format obrazu przy zapisywaniu przy użyciu Aspose.Words dla Java?**  
A: Ustaw żądany format w `ImageSaveOptions`. Dla PNG możesz po prostu utworzyć `ImageSaveOptions` i przypisać `SaveFormat.PNG`, jeśli to potrzebne.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Czy mogę dostosować ustawienia kompresji dla obrazów TIFF?**  
A: Tak. Użyj `setTiffCompression`, aby wybrać algorytm kompresji, taki jak `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Jak mogę zapisać określoną stronę dokumentu jako osobny obraz?**  
A: Użyj metody `setPageSet` z pojedynczym indeksem strony.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Jak zastosować własne ustawienia do obrazów JPEG przy zapisywaniu?**  
A: Dostosuj właściwości takie jak jasność, kontrast i rozdzielczość za pomocą `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Jak mogę użyć wywołania zwrotnego do dostosowania zapisywania obrazów?**  
A: Zaimplementuj `IPageSavingCallback` i przypisz go przy pomocy `setPageSavingCallback`.

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

## Podsumowanie
Masz teraz kompletny zestaw narzędzi do **saving page as jpeg**, wyodrębniania obrazów, kontrolowania jasności obrazu, ustawiania rozdzielczości obrazu w Javie oraz tworzenia wielostronicowych plików TIFF przy użyciu Aspose.Words dla Java. Eksperymentuj z różnymi ustawieniami `ImageSaveOptions`, aby dopasować je do potrzeb projektu, i odkrywaj szersze możliwości API Aspose.Words w zakresie jeszcze większej manipulacji dokumentami.

---

**Last Updated:** 2025-12-27  
**Testowane z:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}