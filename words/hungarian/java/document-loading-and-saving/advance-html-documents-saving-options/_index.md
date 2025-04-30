---
"description": "Ebben az oktatóanyagban számos haladó HTML dokumentummentési lehetőséget ismertettünk az Aspose.Words for Java segítségével. Ezek a lehetőségek lehetővé teszik kiváló minőségű HTML létrehozását."
"linktitle": "HTML dokumentumok mentése"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Speciális HTML dokumentumok mentési beállításai az Aspose.Words Java segítségével"
"url": "/hu/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Speciális HTML dokumentumok mentési beállításai az Aspose.Words Java segítségével


Ebben az oktatóanyagban az Aspose.Words for Java által biztosított fejlett HTML dokumentummentési lehetőségeket vizsgáljuk meg. Az Aspose.Words egy hatékony Java API a Word dokumentumokkal való munkához, és számos funkciót kínál a dokumentumok kezeléséhez és konvertálásához.

## 1. Bevezetés
Az Aspose.Words for Java lehetővé teszi a Word dokumentumok programozott kezelését. Ebben az oktatóanyagban a HTML dokumentumok mentésének speciális beállításaira fogunk összpontosítani, amelyek lehetővé teszik a Word dokumentumok HTML-re konvertálásának szabályozását.

## 2. Oda-vissza információk exportálása
A `exportRoundtripInformation` metódus lehetővé teszi Word-dokumentumok HTML-be exportálását az oda-vissza információk megőrzése mellett. Ez az információ hasznos lehet, ha a HTML-t vissza szeretné konvertálni Word formátumba anélkül, hogy elveszítené a dokumentumspecifikus részleteket.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Betűtípusok exportálása Base64 formátumban
A `exportFontsAsBase64` metódussal a dokumentumban használt betűtípusokat Base64 kódolású adatokként exportálhatja a HTML-be. Ez biztosítja, hogy a HTML-ábrázolás megőrzi az eredeti Word-dokumentuméval megegyező betűstílusokat.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Erőforrások exportálása
A `exportResources` A metódus lehetővé teszi a CSS stíluslap típusának megadását és a betűtípus-erőforrások exportálását. Beállíthat egy erőforrásmappát és egy aliast az erőforrásokhoz a HTML-ben.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://példa.com/erőforrások");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Metafájlok konvertálása EMF vagy WMF formátumba
A `convertMetafilesToEmfOrWmf` A metódus lehetővé teszi a dokumentumban található metafájlok EMF vagy WMF formátumba konvertálását, biztosítva a kompatibilitást és a zökkenőmentes megjelenítést HTML-ben.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Piros pont\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Metafájlok konvertálása SVG-vé
Használd a `convertMetafilesToSvg` módszer metafájlok SVG formátumba konvertálására. Ez a formátum ideális vektorgrafikák HTML dokumentumokban történő megjelenítéséhez.

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

## 7. CSS osztálynév előtag hozzáadása
A `addCssClassNamePrefix` metódussal előtagot adhatsz a CSS osztálynevekhez az exportált HTML-ben. Ez segít elkerülni az ütközéseket a meglévő stílusokkal.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. CID URL-ek exportálása MHTML-erőforrásokhoz
A `exportCidUrlsForMhtmlResources` A metódust MHTML formátumú dokumentumok mentésekor használják. Lehetővé teszi az erőforrások Content-ID URL-jeinek exportálását.

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

## 9. Betűtípusok nevének feloldása
A `resolveFontNames` A metódus segít a betűtípusnevek feloldásában HTML formátumú dokumentumok mentésekor, biztosítva a különböző platformokon egységes megjelenítést.

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

## 10. Szövegbeviteli űrlap mező exportálása szövegként
A `exportTextInputFormFieldAsText` A metódus egyszerű szövegként exportálja az űrlapmezőket a HTML-be, így azok könnyen olvashatók és szerkeszthetők.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// megadott mappának léteznie kell, és üresnek kell lennie.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Állítson be egy opciót az űrlapmezők egyszerű szövegként történő exportálására, ne HTML beviteli elemként.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Következtetés
Ebben az oktatóanyagban az Aspose.Words for Java által biztosított fejlett HTML dokumentummentési lehetőségeket vizsgáltuk meg. Ezek a beállítások részletes szabályozást biztosítanak a konvertálási folyamat felett, lehetővé téve az eredeti Word dokumentumokhoz nagyon hasonló HTML dokumentumok létrehozását.

## GYIK
Íme néhány gyakran ismételt kérdés az Aspose.Words Java-ban és HTML-dokumentumok mentési beállításaival kapcsolatban:

### 1. kérdés: Hogyan konvertálhatom vissza a HTML-t Word formátumba az Aspose.Words for Java segítségével?
A HTML Word formátumba való visszakonvertálásához használhatja az Aspose.Words API-ját. `load` módszer a HTML dokumentum betöltéséhez, majd Word formátumban történő mentéséhez.

### 2. kérdés: Testreszabhatom a CSS stílusokat HTML-be exportáláskor?
Igen, testreszabhatja a CSS stílusokat a HTML-ben használt stíluslapok módosításával vagy a `addCssClassNamePrefix` metódus előtag hozzáadásához a CSS osztálynevekhez.

### 3. kérdés: Van mód a HTML-kimenet optimalizálására webes megjelenítéshez?
Igen, optimalizálhatod a HTML kimenetet webes megjelenítéshez olyan beállítások konfigurálásával, mint a betűtípusok Base64 formátumba exportálása és a metafájlok SVG formátumba konvertálása.

### 4. kérdés: Vannak-e korlátozások az összetett Word-dokumentumok HTML-be konvertálásakor?
Bár az Aspose.Words for Java hatékony konvertálási képességeket kínál, a bonyolult elrendezésű, összetett Word-dokumentumok további utófeldolgozást igényelhetnek a kívánt HTML-kimenet eléréséhez.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}