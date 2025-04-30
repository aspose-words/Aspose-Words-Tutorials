---
"description": "W tym samouczku omówiliśmy różne zaawansowane opcje zapisywania dokumentów HTML za pomocą Aspose.Words dla Java. Opcje te umożliwiają tworzenie wysokiej jakości dokumentów HTML"
"linktitle": "Zapisywanie dokumentów HTML za pomocą"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Zaawansowane opcje zapisywania dokumentów HTML z Aspose.Words Java"
"url": "/pl/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zaawansowane opcje zapisywania dokumentów HTML z Aspose.Words Java


W tym samouczku przyjrzymy się zaawansowanym opcjom zapisywania dokumentów HTML udostępnianym przez Aspose.Words dla Java. Aspose.Words to potężne API Java do pracy z dokumentami Word, oferujące szeroki zakres funkcji do manipulacji dokumentami i konwersji.

## 1. Wprowadzenie
Aspose.Words for Java umożliwia programową pracę z dokumentami Word. W tym samouczku skupimy się na zaawansowanych opcjach zapisywania dokumentów HTML, które umożliwiają kontrolowanie sposobu konwersji dokumentów Word na HTML.

## 2. Informacje o eksporcie w obie strony
Ten `exportRoundtripInformation` Metoda ta pozwala eksportować dokumenty Word do HTML, zachowując jednocześnie informacje o obiegu zamkniętym. Informacje te mogą być przydatne, gdy chcesz przekonwertować HTML z powrotem do formatu Word bez utraty szczegółów specyficznych dla dokumentu.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Eksportuj czcionki jako Base64
Z `exportFontsAsBase64` metodą, możesz eksportować czcionki używane w dokumencie jako dane zakodowane w Base64 w HTML. Zapewnia to, że reprezentacja HTML zachowuje te same style czcionek, co oryginalny dokument Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Eksportuj zasoby
Ten `exportResources` Metoda ta pozwala określić typ arkusza stylów CSS i eksportować zasoby czcionek. Można również ustawić folder zasobów i alias dla zasobów w HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/zasoby");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Konwertuj metapliki do formatu EMF lub WMF
Ten `convertMetafilesToEmfOrWmf` Metoda ta umożliwia konwersję metaplików w dokumencie do formatu EMF lub WMF, zapewniając zgodność i płynne renderowanie w formacie HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Czerwona kropka\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Konwertuj metapliki do formatu SVG
Użyj `convertMetafilesToSvg` metoda konwersji metaplików do formatu SVG. Ten format jest idealny do wyświetlania grafiki wektorowej w dokumentach HTML.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

## 7. Dodaj prefiks nazwy klasy CSS
Z `addCssClassNamePrefix` metodą, możesz dodać prefiks do nazw klas CSS w eksportowanym HTML. Pomaga to zapobiegać konfliktom z istniejącymi stylami.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Eksportuj adresy URL CID dla zasobów MHTML
Ten `exportCidUrlsForMhtmlResources` Metoda jest używana podczas zapisywania dokumentów w formacie MHTML. Pozwala ona na eksportowanie adresów URL Content-ID dla zasobów.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

## 9. Rozwiąż nazwy czcionek
Ten `resolveFontNames` Metoda ta pomaga rozpoznawać nazwy czcionek podczas zapisywania dokumentów w formacie HTML, zapewniając spójne renderowanie na różnych platformach.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

## 10. Eksportuj pole formularza wprowadzania tekstu jako tekst
Ten `exportTextInputFormFieldAsText` Metoda eksportuje pola formularza jako zwykły tekst w formacie HTML, dzięki czemu są one łatwe do odczytania i edycji.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Podany folder musi istnieć i powinien być pusty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Ustaw opcję eksportowania pól formularza jako zwykłego tekstu, a nie jako elementów wejściowych HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Wniosek
W tym samouczku przyjrzeliśmy się zaawansowanym opcjom zapisywania dokumentów HTML udostępnianym przez Aspose.Words dla Java. Opcje te dają Ci szczegółową kontrolę nad procesem konwersji, umożliwiając tworzenie dokumentów HTML, które ściśle przypominają oryginalne dokumenty Word.

## Najczęściej zadawane pytania
Poniżej znajdują się najczęściej zadawane pytania dotyczące pracy z opcjami zapisywania dokumentów Java i HTML w Aspose.Words:

### P1: W jaki sposób mogę przekonwertować HTML z powrotem do formatu Word za pomocą Aspose.Words dla Java?
Aby przekonwertować HTML z powrotem do formatu Word, możesz skorzystać z interfejsu API Aspose.Words `load` metoda ładowania dokumentu HTML i zapisywania go w formacie Word.

### P2: Czy mogę dostosować style CSS podczas eksportowania do HTML?
Tak, możesz dostosować style CSS, modyfikując arkusze stylów używane w kodzie HTML lub korzystając z `addCssClassNamePrefix` metoda dodawania prefiksu do nazw klas CSS.

### P3: Czy istnieje sposób na optymalizację wyjścia HTML do wyświetlania w sieci?
Tak, możesz zoptymalizować wyjście HTML do wyświetlania w Internecie, konfigurując opcje takie jak eksportowanie czcionek jako Base64 i konwersja metaplików do SVG.

### P4: Czy istnieją jakieś ograniczenia przy konwersji złożonych dokumentów Word do formatu HTML?
Chociaż Aspose.Words for Java oferuje zaawansowane możliwości konwersji, złożone dokumenty Word ze skomplikowanymi układami mogą wymagać dodatkowego przetwarzania końcowego w celu uzyskania pożądanego wyniku HTML.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}