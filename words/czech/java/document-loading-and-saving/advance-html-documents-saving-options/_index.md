---
title: Pokročilé možnosti ukládání dokumentů HTML pomocí Aspose.Words Java
linktitle: Ukládání HTML dokumentů pomocí
second_title: Aspose.Words Java Document Processing API
description: V tomto tutoriálu jsme se zabývali různými pokročilými možnostmi ukládání dokumentů HTML pomocí Aspose.Words pro Java. Tyto možnosti vám umožňují vytvářet vysoce kvalitní HTML
weight: 16
url: /cs/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pokročilé možnosti ukládání dokumentů HTML pomocí Aspose.Words Java


V tomto tutoriálu prozkoumáme pokročilé možnosti ukládání dokumentů HTML, které poskytuje Aspose.Words pro Java. Aspose.Words je výkonné Java API pro práci s dokumenty Wordu a nabízí širokou škálu funkcí pro manipulaci s dokumenty a jejich převod.

## 1. Úvod
Aspose.Words for Java vám umožňuje pracovat s dokumenty Wordu programově. V tomto tutoriálu se zaměříme na pokročilé možnosti ukládání dokumentů HTML, které vám umožňují řídit, jak se dokumenty aplikace Word převádějí do HTML.

## 2. Exportujte informace o zpáteční cestě
 The`exportRoundtripInformation` umožňuje exportovat dokumenty Wordu do HTML při zachování zpátečních informací. Tyto informace mohou být užitečné, když chcete převést HTML zpět do formátu Word bez ztráty jakýchkoli podrobností specifických pro dokument.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Exportujte písma jako Base64
 s`exportFontsAsBase64` můžete exportovat fonty použité v dokumentu jako data kódovaná Base64 do HTML. Tím je zajištěno, že reprezentace HTML zachová stejné styly písem jako původní dokument aplikace Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Export zdrojů
 The`exportResources` umožňuje určit typ šablony stylů CSS a exportovat zdroje písem. Můžete také nastavit složku prostředků a alias pro prostředky v HTML.

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

## 5. Převeďte metasoubory na EMF nebo WMF
 The`convertMetafilesToEmfOrWmf`metoda umožňuje převést metasoubory v dokumentu buď do formátu EMF nebo WMF, což zajišťuje kompatibilitu a plynulé vykreslování v HTML.

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

## 6. Převeďte metasoubory na SVG
 Použijte`convertMetafilesToSvg` metoda pro převod metasouborů do formátu SVG. Tento formát je ideální pro zobrazování vektorové grafiky v dokumentech HTML.

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
 s`addCssClassNamePrefix` můžete přidat předponu k názvům tříd CSS v exportovaném HTML. To pomáhá předcházet konfliktům s existujícími styly.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exportujte adresy URL CID pro zdroje MHTML
 The`exportCidUrlsForMhtmlResources` metoda se používá při ukládání dokumentů ve formátu MHTML. Umožňuje exportovat adresy URL Content-ID pro zdroje.

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
 The`resolveFontNames` Tato metoda pomáhá vyřešit názvy písem při ukládání dokumentů ve formátu HTML a zajišťuje konzistentní vykreslování na různých platformách.

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

## 10. Export textového vstupního pole formuláře jako text
 The`exportTextInputFormFieldAsText`metoda exportuje pole formuláře jako prostý text v HTML, takže je snadno čitelná a upravitelná.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Zadaná složka musí existovat a měla by být prázdná.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Nastavte možnost exportovat pole formuláře jako prostý text, nikoli jako vstupní prvky HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Závěr
V tomto tutoriálu jsme prozkoumali pokročilé možnosti ukládání dokumentů HTML, které poskytuje Aspose.Words pro Java. Tyto možnosti vám poskytují jemnou kontrolu nad procesem převodu a umožňují vám vytvářet dokumenty HTML, které se velmi podobají původním dokumentům aplikace Word.

## FAQ
Zde jsou některé často kladené otázky o práci s Aspose.Words pro Java a možnosti uložení dokumentu HTML:

### Q1: Jak mohu převést HTML zpět do formátu Word pomocí Aspose.Words for Java?
 Chcete-li převést HTML zpět do formátu Word, můžete použít rozhraní API Aspose.Words`load` způsob načtení dokumentu HTML a jeho uložení ve formátu Word.

### Q2: Mohu přizpůsobit styly CSS při exportu do HTML?
Ano, styly CSS můžete přizpůsobit úpravou šablon stylů používaných v HTML nebo pomocí`addCssClassNamePrefix` metoda pro přidání předpony k názvům tříd CSS.

### Q3: Existuje způsob, jak optimalizovat výstup HTML pro zobrazení na webu?
Ano, výstup HTML můžete optimalizovat pro webové zobrazení konfigurací možností, jako je export písem jako Base64 a převod metasouborů do SVG.

### Q4: Existují nějaká omezení při převodu složitých dokumentů aplikace Word do HTML?
Zatímco Aspose.Words for Java poskytuje výkonné konverzní možnosti, složité dokumenty Wordu se složitým rozvržením mohou vyžadovat dodatečné následné zpracování k dosažení požadovaného výstupu HTML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
