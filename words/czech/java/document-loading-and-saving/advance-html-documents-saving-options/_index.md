---
date: 2025-12-19
description: Naučte se exportovat HTML pomocí Aspose.Words pro Java, včetně pokročilých
  možností ukládání Wordu jako HTML a efektivního převodu Wordu do HTML.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Jak exportovat HTML pomocí Aspose.Words pro Javu: Pokročilé možnosti'
url: /cs/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak exportovat HTML pomocí Aspose.Words Java: Pokročilé možnosti

V tomto tutoriálu objevíte **jak exportovat HTML** z dokumentů Word pomocí Aspose.Words pro Java. Ať už potřebujete **uložit Word jako HTML** pro publikování na webu nebo **převést Word do HTML** pro následné zpracování, pokročilé možnosti ukládání vám poskytují detailní kontrolu nad výstupem. Provedeme vás každou možnost krok za krokem, vysvětlíme, kdy ji použít, a ukážeme reálné scénáře, kde tato nastavení dělají rozdíl.

## Rychlé odpovědi
- **Jaká je hlavní třída pro export HTML?** `HtmlSaveOptions`  
- **Lze písma vložit přímo do HTML?** Ano, nastavte `exportFontsAsBase64` na `true`.  
- **Jak zachovat Word‑specifické data pro round‑trip?** Povolit `exportRoundtripInformation`.  
- **Který formát je nejlepší pro vektorovou grafiku?** Použijte `convertMetafilesToSvg` pro výstup SVG.  
- **Je možné předejít kolizím názvů CSS tříd?** Ano, použijte `addCssClassNamePrefix`.

## 1. Úvod
Aspose.Words pro Java je robustní API, které umožňuje vývojářům programově manipulovat s dokumenty Word. Tento průvodce se zaměřuje na pokročilé možnosti ukládání HTML dokumentů, které vám umožní přizpůsobit proces konverze tak, aby vyhovoval konkrétním požadavkům webu nebo integrace.

## 2. Export informací pro round‑trip
Zachování informací pro round‑trip vám umožní převést HTML zpět do dokumentu Word, aniž byste ztratili detaily rozvržení nebo formátování.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Kdy použít
- Když potřebujete reverzní konverzní pipeline (HTML → Word → HTML).  
- Ideální pro scénáře kolaborativního editování, kde je nutné zachovat původní strukturu Word.

## 3. Export písem jako Base64
Vkládání písem přímo do HTML eliminuje závislosti na externích písmech a zajišťuje vizuální věrnost napříč prohlížeči.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Profesionální tip
Použijte tuto možnost, když cílové prostředí má omezený přístup k externím zdrojům (např. e‑mailové newslettery).

## 4. Export zdrojů
Řiďte, jak jsou CSS a fontové zdroje emitovány, a určete vlastní složku nebo URL alias pro tyto assety.

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

### Proč je to důležité
Oddělení CSS do externího souboru snižuje velikost HTML a umožňuje cachování pro rychlejší načítání stránek.

## 5. Převod metafilek na EMF nebo WMF
Metafily (např. EMF/WMF) jsou převedeny do formátu, který prohlížeče dokážou spolehlivě vykreslit.

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

### Případ použití
Zvolte EMF/WMF, když cílové prohlížeče podporují tyto vektorové formáty a potřebujete bezztrátové škálování.

## 6. Převod metafilek na SVG
SVG poskytuje nejlepší škálovatelnost a je široce podporováno moderními prohlížeči.

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

### Přínos
SVG soubory jsou lehké a udržují dokument nezávislý na rozlišení, což je ideální pro responzivní webdesign.

## 7. Přidat prefix názvu CSS třídy
Zabránit kolizím stylů tím, že přidáte prefix ke všem generovaným názvům CSS tříd.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Praktický tip
Použijte jedinečný prefix (např. název vašeho projektu), když vkládáte HTML do existujících stránek, abyste se vyhnuli konfliktům CSS.

## 8. Export CID URL pro MHTML zdroje
Při ukládání jako MHTML můžete exportovat zdroje pomocí Content‑ID URL pro lepší kompatibilitu s e‑maily.

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

### Kdy použít
Ideální pro generování jediného, samostatného HTML souboru, který lze připojit k e‑mailům.

## 9. Vyřešit názvy písem
Zajišťuje, že HTML odkazuje na správné rodiny písem, což zlepšuje konzistenci napříč platformami.

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

### Proč to pomáhá
Pokud původní dokument používá písma, která nejsou nainstalována na klientském počítači, tato možnost je nahradí web‑bezpečnými alternativami.

## 10. Export textového vstupního formulářového pole jako text
Vykreslí formulářová pole jako prostý text místo interaktivních HTML vstupních prvků.

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

### Případ použití
Když potřebujete pouze‑čtení reprezentaci formuláře pro archivaci nebo tisk.

## Časté úskalí a řešení problémů
| Problém | Typická příčina | Řešení |
|-------|---------------|-----|
| Chybějící písma ve výstupu | `exportFontsAsBase64` není povoleno | Nastavte `setExportFontsAsBase64(true)` |
| Poškozené CSS po vložení | Použití `EXTERNAL` bez poskytnutí CSS souboru | Zajistěte, aby byl CSS soubor nasazen na určeném `resourceFolderAlias` |
| Velká velikost HTML | Vkládání mnoha obrázků jako Base64 | Přepněte na externí obrázkové zdroje pomocí `setExportFontResources(true)` a nakonfigurujte `resourceFolder` |
| SVG se nevykresluje ve starších prohlížečích | Prohlížeč nepodporuje SVG | Poskytněte záložní PNG také exportováním jako EMF/WMF |

## Často kladené otázky

**Q: Mohu zároveň vkládat písma jako Base64 a zachovat externí CSS?**  
A: Ano. Nastavte `exportFontsAsBase64(true)` a zároveň ponechte `CssStyleSheetType.EXTERNAL`, aby se data písem oddělila od stylových pravidel.

**Q: Jak převést existující HTML zpět do dokumentu Word?**  
A: Načtěte HTML pomocí `Document doc = new Document("input.html");` a poté `doc.save("output.docx");`. Zachovejte data pro round‑trip pomocí `exportRoundtripInformation` během počátečního exportu.

**Q: Má použití konverze do SVG dopad na výkon?**  
A: Převod velkých metafilek na SVG může zvýšit dobu zpracování, ale výsledné HTML je obvykle menší a v prohlížečích se vykresluje rychleji.

**Q: Fungují tyto možnosti také s Aspose.Words pro .NET?**  
A: Stejné koncepty existují v .NET API, i když se názvy metod mohou mírně lišit (např. `HtmlSaveOptions` je sdílené napříč platformami).

**Q: Kterou možnost bych měl zvolit pro e‑mail‑přátelské HTML?**  
A: Použijte `SaveFormat.MHTML` s `exportCidUrlsForMhtmlResources`, aby se všechny zdroje vložily přímo do těla e‑mailu.

---

**Poslední aktualizace:** 2025-12-19  
**Testováno s:** Aspose.Words pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}