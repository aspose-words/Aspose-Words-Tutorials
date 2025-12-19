---
date: 2025-12-19
description: Poznaj sposób eksportowania HTML przy użyciu Aspose.Words Java, obejmujący
  zaawansowane opcje zapisywania dokumentów Word jako HTML oraz efektywne konwertowanie
  Worda na HTML.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Jak wyeksportować HTML przy użyciu Aspose.Words Java: Zaawansowane opcje'
url: /pl/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak eksportować HTML przy użyciu Aspose.Words Java: Zaawansowane opcje

W tym samouczku odkryjesz **jak eksportować HTML** z dokumentów Word przy użyciu Aspose.Words for Java. Niezależnie od tego, czy musisz **zapisać Word jako HTML** do publikacji w sieci, czy **przekształcić Word do HTML** w celu dalszego przetwarzania, zaawansowane opcje zapisu dają Ci precyzyjną kontrolę nad wynikiem. Przejdziemy krok po kroku przez każdą opcję, wyjaśnimy, kiedy ją stosować, i pokażemy rzeczywiste scenariusze, w których te ustawienia robią różnicę.

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do eksportu HTML?** `HtmlSaveOptions`  
- **Czy czcionki mogą być osadzone bezpośrednio w HTML?** Tak, ustaw `exportFontsAsBase64` na `true`.  
- **Jak zachować specyficzne dla Word danych round‑trip?** Włącz `exportRoundtripInformation`.  
- **Jaki format jest najlepszy dla grafiki wektorowej?** Użyj `convertMetafilesToSvg` dla wyjścia SVG.  
- **Czy można uniknąć kolizji nazw klas CSS?** Tak, użyj `addCssClassNamePrefix`.

## 1. Wprowadzenie
Aspose.Words for Java to solidne API, które umożliwia programistom manipulowanie dokumentami Word w sposób programowy. Ten przewodnik koncentruje się na zaawansowanych opcjach zapisu dokumentu HTML, które pozwalają dostosować proces konwersji do konkretnych wymagań sieciowych lub integracyjnych.

## 2. Export Roundtrip Information
Zachowanie informacji round‑trip umożliwia konwersję HTML z powrotem do dokumentu Word bez utraty układu lub szczegółów formatowania.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Kiedy używać
- Kiedy potrzebujesz odwracalnego potoku konwersji (HTML → Word → HTML).  
- Idealne w scenariuszach współdzielonej edycji, gdzie oryginalna struktura Word musi być zachowana.

## 3. Export Fonts as Base64
Osadzanie czcionek bezpośrednio w HTML eliminuje zależności od zewnętrznych czcionek i zapewnia wizualną wierność we wszystkich przeglądarkach.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Wskazówka pro
Użyj tej opcji, gdy docelowe środowisko ma ograniczony dostęp do zasobów zewnętrznych (np. biuletyny e‑mail).

## 4. Export Resources
Kontroluj sposób emisji zasobów CSS i czcionek oraz określ niestandardowy folder lub alias URL dla tych zasobów.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Dlaczego to ważne
Rozdzielenie CSS do zewnętrznego pliku zmniejsza rozmiar HTML i umożliwia buforowanie, co przyspiesza ładowanie stron.

## 5. Convert Metafiles to EMF or WMF
Metafiles (np. EMF/WMF) są konwertowane do formatu, który przeglądarki mogą renderować niezawodnie.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Przypadek użycia
Wybierz EMF/WMF, gdy docelowe przeglądarki obsługują te formaty wektorowe i potrzebujesz skalowania bez utraty jakości.

## 6. Convert Metafiles to SVG
SVG zapewnia najlepszą skalowalność i jest szeroko wspierany we współczesnych przeglądarkach.

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

### Korzyść
Pliki SVG są lekkie i utrzymują dokument niezależny od rozdzielczości, co jest idealne dla responsywnego projektowania stron.

## 7. Add CSS Class Name Prefix
Zapobiegaj konfliktom stylów, dodając prefiks do wszystkich generowanych nazw klas CSS.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Praktyczna wskazówka
Użyj unikalnego prefiksu (np. nazwy Twojego projektu) przy osadzaniu HTML w istniejących stronach, aby uniknąć konfliktów CSS.

## 8. Export CID URLs for MHTML Resources
Podczas zapisu jako MHTML możesz eksportować zasoby przy użyciu URL‑ów Content‑ID, co poprawia kompatybilność z e‑mailami.

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

### Kiedy używać
Idealne do generowania jednego, samodzielnego pliku HTML, który można dołączyć do wiadomości e‑mail.

## 9. Resolve Font Names
Zapewnia, że HTML odwołuje się do właściwych rodzin czcionek, poprawiając spójność między platformami.

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

### Dlaczego to pomaga
Jeśli oryginalny dokument używa czcionek niezainstalowanych na komputerze klienta, ta opcja podmienia je na alternatywy web‑safe.

## 10. Export Text Input Form Field as Text
Renderuj pola formularzy jako zwykły tekst zamiast interaktywnych elementów HTML input.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Przypadek użycia
Kiedy potrzebujesz tylko do odczytu reprezentacji formularza do archiwizacji lub drukowania.

## Common Pitfalls & Troubleshooting
| Problem | Typowa przyczyna | Rozwiązanie |
|---------|------------------|-------------|
| Brak czcionek w wyjściu | `exportFontsAsBase64` nie włączony | Ustaw `setExportFontsAsBase64(true)` |
| Uszkodzony CSS po osadzeniu | Użycie `EXTERNAL` bez podania pliku CSS | Upewnij się, że plik CSS jest wdrożony w określonym `resourceFolderAlias` |
| Duży rozmiar HTML | Osadzanie wielu obrazów jako Base64 | Przejdź na zewnętrzne zasoby obrazów za pomocą `setExportFontResources(true)` i skonfiguruj `resourceFolder` |
| SVG nie renderuje się w starszych przeglądarkach | Przeglądarka nie obsługuje SVG | Zapewnij alternatywny PNG, eksportując także jako EMF/WMF |

## Frequently Asked Questions

**Q: Czy mogę jednocześnie osadzić czcionki jako Base64 i zachować zewnętrzny CSS?**  
A: Tak. Ustaw `exportFontsAsBase64(true)` przy zachowaniu `CssStyleSheetType.EXTERNAL`, aby oddzielić dane czcionek od reguł stylów.

**Q: Jak przekształcić istniejący HTML z powrotem do dokumentu Word?**  
A: Załaduj HTML przy pomocy `Document doc = new Document("input.html");`, a następnie `doc.save("output.docx");`. Zachowaj dane round‑trip używając `exportRoundtripInformation` podczas początkowego eksportu.

**Q: Czy konwersja do SVG wpływa na wydajność?**  
A: Konwersja dużych metafili do SVG może wydłużyć czas przetwarzania, aleowy HTML jest zazwyczaj mniejszy i renderuje się szybciej w przeglądarkach.

**Q: Czy te opcje działają również z Aspose.Words dla .NET?**  
A: Te same koncepcje istnieją w API .NET, choć nazwy metod mogą się nieco różnić (np. `HtmlSaveOptions` jest wspólne dla obu platform).

**Q: Którą opcję wybrać dla HTML przyjaznego e‑mailom?**  
A: Użyj `SaveFormat.MHTML` wraz z `exportCidUrlsForMhtmlResources`, aby osadzić wszystkie zasoby bezpośrednio w treści e‑maila.

---

**Ostatnia aktualizacja:** 2025-12-19  
**Testowano z:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}