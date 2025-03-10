---
title: Advance HTML dokumentumok mentési lehetőségek Aspose.Words Java
linktitle: HTML dokumentumok mentése ezzel
second_title: Aspose.Words Java Document Processing API
description: Ebben az oktatóanyagban az Aspose.Words for Java különféle fejlett HTML-dokumentummentési lehetőségeivel foglalkozunk. Ezek a lehetőségek kiváló minőségű HTML létrehozását teszik lehetővé
weight: 16
url: /hu/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Advance HTML dokumentumok mentési lehetőségek Aspose.Words Java


Ebben az oktatóanyagban megvizsgáljuk az Aspose.Words for Java által biztosított speciális HTML-dokumentummentési lehetőségeket. Az Aspose.Words egy hatékony Java API Word-dokumentumokkal való munkavégzéshez, és funkciók széles skáláját kínálja a dokumentumok kezeléséhez és konvertálásához.

## 1. Bevezetés
Az Aspose.Words for Java lehetővé teszi, hogy programozottan dolgozzon Word dokumentumokkal. Ebben az oktatóanyagban a speciális HTML-dokumentummentési lehetőségekre összpontosítunk, amelyek lehetővé teszik a Word-dokumentumok HTML-formátumba való konvertálásának szabályozását.

## 2. Oda-vissza információk exportálása
 A`exportRoundtripInformation` módszer lehetővé teszi a Word-dokumentumok exportálását HTML-be, miközben megőrzi az oda-vissza információk. Ez az információ akkor lehet hasznos, ha a HTML-t vissza kívánja konvertálni Word formátumba anélkül, hogy elveszítené a dokumentumspecifikus részleteket.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Betűtípusok exportálása Base64-ként
 A`exportFontsAsBase64` módszerrel a dokumentumban használt betűtípusokat Base64-kódolású adatként exportálhatja a HTML-be. Ez biztosítja, hogy a HTML-ábrázolás megőrizze ugyanazokat a betűstílusokat, mint az eredeti Word-dokumentum.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Erőforrások exportálása
 A`exportResources` metódus lehetővé teszi a CSS-stíluslap típusának megadását és a betűkészlet-erőforrások exportálását. A HTML-ben erőforrásmappát és álnevet is beállíthat az erőforrásokhoz.

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

## 5. Konvertálja a metafájlokat EMF-re vagy WMF-re
 A`convertMetafilesToEmfOrWmf` módszer lehetővé teszi a dokumentumban lévő metafájlok konvertálását EMF vagy WMF formátumba, ezzel biztosítva a kompatibilitást és a sima HTML-megjelenítést.

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

## 6. Konvertálja a metafájlokat SVG formátumba
 Használja a`convertMetafilesToSvg` módszer a metafájlok SVG formátumba konvertálására. Ez a formátum ideális vektorgrafikák megjelenítésére HTML dokumentumokban.

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

## 7. Adja hozzá a CSS-osztálynév előtagot
 A`addCssClassNamePrefix` módszerrel előtagot adhat a CSS-osztályok nevéhez az exportált HTML-ben. Ez segít megelőzni az ütközéseket a meglévő stílusokkal.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exportáljon CID URL-eket az MHTML-erőforrásokhoz
 A`exportCidUrlsForMhtmlResources` módszert használjuk dokumentumok MHTML formátumba mentésekor. Lehetővé teszi a Content ID URL-ek exportálását erőforrásokhoz.

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

## 9. A betűtípusnevek feloldása
 A`resolveFontNames` A metódus segít a betűtípusnevek feloldásában dokumentumok HTML formátumba mentésekor, biztosítva a konzisztens megjelenítést a különböző platformokon.

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
 A`exportTextInputFormFieldAsText`metódus az űrlapmezőket egyszerű szövegként exportálja a HTML-be, így könnyen olvashatóvá és szerkeszthetővé teszi őket.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// A megadott mappának léteznie kell, és üresnek kell lennie.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Állítsa be az űrlapmezők egyszerű szövegként, nem pedig HTML beviteli elemként történő exportálását.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Következtetés
Ebben az oktatóanyagban az Aspose.Words for Java által biztosított speciális HTML-dokumentummentési lehetőségeket fedeztük fel. Ezek a beállítások lehetővé teszik az átalakítási folyamat finom vezérlését, lehetővé téve olyan HTML-dokumentumok létrehozását, amelyek nagyon hasonlítanak az eredeti Word-dokumentumokra.

## GYIK
Íme néhány gyakran ismételt kérdés az Aspose.Words for Java és HTML-dokumentummentési beállításokkal kapcsolatban:

### 1. kérdés: Hogyan konvertálhatom vissza a HTML-t Word formátumba az Aspose.Words for Java használatával?
 A HTML Word formátumba való visszaállításához használhatja az Aspose.Words API-t`load` módszerrel töltheti be a HTML-dokumentumot, majd mentheti Word formátumban.

### 2. kérdés: Testreszabhatom a CSS-stílusokat HTML-be exportáláskor?
Igen, testreszabhatja a CSS-stílusokat a HTML-ben használt stíluslapok módosításával vagy a`addCssClassNamePrefix` módszer előtag hozzáadásához a CSS-osztálynevekhez.

### 3. kérdés: Van mód a HTML-kimenet optimalizálására webes megjelenítéshez?
Igen, optimalizálhatja a HTML-kimenetet a webes megjelenítéshez az olyan opciók konfigurálásával, mint a betűtípusok Base64-ként való exportálása és a metafájlok SVG formátumba való konvertálása.

### 4. kérdés: Vannak-e korlátozások az összetett Word dokumentumok HTML formátumba konvertálásakor?
Míg az Aspose.Words for Java hatékony konverziós képességeket biztosít, a bonyolult elrendezésű Word dokumentumok további utófeldolgozást igényelhetnek a kívánt HTML-kimenet eléréséhez.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
