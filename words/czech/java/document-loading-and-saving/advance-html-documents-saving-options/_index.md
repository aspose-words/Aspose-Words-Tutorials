---
"description": "V tomto tutoriálu jsme se zabývali různými pokročilými možnostmi ukládání HTML dokumentů pomocí Aspose.Words pro Javu. Tyto možnosti vám umožní vytvářet vysoce kvalitní HTML."
"linktitle": "Ukládání HTML dokumentů pomocí"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Pokročilé možnosti ukládání HTML dokumentů pomocí Aspose.Words v Javě"
"url": "/cs/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pokročilé možnosti ukládání HTML dokumentů pomocí Aspose.Words v Javě


V tomto tutoriálu se seznámíme s pokročilými možnostmi ukládání HTML dokumentů, které nabízí Aspose.Words pro Javu. Aspose.Words je výkonné Java API pro práci s dokumenty Wordu, které nabízí širokou škálu funkcí pro manipulaci s dokumenty a jejich převod.

## 1. Úvod
Aspose.Words pro Javu umožňuje programově pracovat s dokumenty Wordu. V tomto tutoriálu se zaměříme na pokročilé možnosti ukládání dokumentů HTML, které vám umožní ovládat, jak se dokumenty Wordu převádějí do HTML.

## 2. Export informací o zpáteční cestě
Ten/Ta/To `exportRoundtripInformation` Metoda umožňuje exportovat dokumenty Wordu do formátu HTML se zachováním informací o oboustranném přenosu. Tyto informace mohou být užitečné, pokud chcete převést HTML zpět do formátu Wordu bez ztráty podrobností specifických pro dokument.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Export písem jako Base64
S `exportFontsAsBase64` Metodou můžete exportovat písma použitá v dokumentu jako data kódovaná v Base64 v HTML. Tím je zajištěno, že HTML reprezentace zachová stejné styly písma jako původní dokument Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Export zdrojů
Ten/Ta/To `exportResources` Metoda umožňuje zadat typ stylu CSS a exportovat zdroje písem. Můžete také nastavit složku zdrojů a alias pro zdroje v HTML.

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

## 5. Převod metasouborů do formátu EMF nebo WMF
Ten/Ta/To `convertMetafilesToEmfOrWmf` Metoda umožňuje převést metasoubory v dokumentu do formátu EMF nebo WMF, což zajišťuje kompatibilitu a plynulé vykreslování v HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Červená tečka\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Převod metasouborů do formátu SVG
Použijte `convertMetafilesToSvg` metoda pro převod metasouborů do formátu SVG. Tento formát je ideální pro zobrazení vektorové grafiky v dokumentech HTML.

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

## 7. Přidejte předponu názvu třídy CSS
S `addCssClassNamePrefix` metodu, můžete přidat předponu k názvům tříd CSS v exportovaném HTML. To pomáhá předcházet konfliktům se stávajícími styly.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Export URL adres CID pro zdroje MHTML
Ten/Ta/To `exportCidUrlsForMhtmlResources` Metoda se používá při ukládání dokumentů ve formátu MHTML. Umožňuje exportovat adresy URL Content-ID pro zdroje.

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

## 9. Vyřešte názvy písem
Ten/Ta/To `resolveFontNames` Metoda pomáhá s rozpoznáváním názvů písem při ukládání dokumentů ve formátu HTML a zajišťuje tak konzistentní vykreslování napříč různými platformami.

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

## 10. Export pole formuláře pro zadávání textu jako text
Ten/Ta/To `exportTextInputFormFieldAsText` Metoda exportuje pole formuláře jako prostý text v HTML, takže jsou snadno čitelná a upravitelná.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Zadaná složka musí existovat a měla by být prázdná.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Nastavte možnost exportu polí formuláře jako prostého textu, nikoli jako vstupních prvků HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Závěr
V tomto tutoriálu jsme prozkoumali pokročilé možnosti ukládání HTML dokumentů, které nabízí Aspose.Words pro Javu. Tyto možnosti vám poskytují přesnou kontrolu nad procesem převodu a umožňují vám vytvářet HTML dokumenty, které se velmi podobají původním dokumentům Wordu.

## Často kladené otázky
Zde jsou některé často kladené otázky týkající se práce s Aspose.Words pro Javu a možností ukládání dokumentů HTML:

### Q1: Jak mohu převést HTML zpět do formátu Word pomocí Aspose.Words pro Javu?
Pro převod HTML zpět do formátu Word můžete použít API Aspose.Words. `load` metoda pro načtení HTML dokumentu a jeho následné uložení ve formátu Word.

### Q2: Mohu si při exportu do HTML upravit styly CSS?
Ano, styly CSS si můžete přizpůsobit úpravou stylů použitých v HTML nebo pomocí `addCssClassNamePrefix` metoda pro přidání prefixu k názvům tříd CSS.

### Q3: Existuje způsob, jak optimalizovat HTML výstup pro zobrazení na webu?
Ano, výstup HTML pro webové zobrazení můžete optimalizovat konfigurací možností, jako je export písem ve formátu Base64 a převod metasouborů do formátu SVG.

### Q4: Existují nějaká omezení při převodu složitých dokumentů Word do HTML?
Přestože Aspose.Words pro Javu nabízí výkonné konverzní funkce, složité dokumenty Wordu se složitým rozvržením mohou vyžadovat dodatečné následné zpracování k dosažení požadovaného výstupu HTML.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}