---
title: Szöveges fájlok betöltése az Aspose.Words for Java segítségével
linktitle: Szöveges fájlok betöltése a
second_title: Aspose.Words Java Document Processing API
description: Fedezze fel az Aspose.Words for Java erejét. Ismerje meg a szöveges dokumentumok betöltését, a listák kezelését, a szóközök kezelését és a szöveg irányának vezérlését.
weight: 13
url: /hu/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szöveges fájlok betöltése az Aspose.Words for Java segítségével


## Bevezetés a szöveges fájlok betöltéséhez az Aspose.Words for Java segítségével

Ebben az útmutatóban megvizsgáljuk, hogyan tölthet be szöveges fájlokat az Aspose.Words for Java használatával, és hogyan kezelheti azokat Word-dokumentumként. Kitérünk a különféle szempontokra, például a listák észlelésére, a szóközök kezelésére és a szöveg irányának szabályozására.

## 1. lépés: Listák észlelése

Szöveges dokumentum betöltéséhez és listák észleléséhez kövesse az alábbi lépéseket:

```java
// Hozzon létre egy egyszerű szöveges dokumentumot karakterlánc formájában, amely részek listákként értelmezhetők.
// Betöltéskor az első három listát mindig észleli az Aspose.Words,
// és a Lista objektumok a betöltés után jönnek létre számukra.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// negyedik lista, szóközzel a lista száma és a listaelem tartalma között,
// csak akkor észlelhető listaként, ha egy LoadOptions objektum "DetectNumberingWithWhitespaces" értéke igaz,
// hogy elkerüljük, hogy a számokkal kezdődő bekezdések tévesen listákként jelenjenek meg.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Töltse be a dokumentumot a LoadOptions paraméterként történő alkalmazása közben, és ellenőrizze az eredményt.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Ez a kód bemutatja, hogyan tölthet be egy szöveges dokumentumot különböző listaformátumokkal, és hogyan használhatja a`DetectNumberingWithWhitespaces` lehetőség a listák helyes észlelésére.

## 2. lépés: A Spaces opciók kezelése

Szöveges dokumentum betöltésekor a kezdő és záró szóközök szabályozásához a következő kódot használhatja:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 Ebben a példában egy szöveges dokumentumot töltünk be, és a kezdő és záró szóközöket levágjuk`TxtLeadingSpacesOptions.TRIM` és`TxtTrailingSpacesOptions.TRIM`.

## 3. lépés: A szöveg irányának vezérlése

A szöveg irányának megadásához szöveges dokumentum betöltésekor a következő kódot használhatja:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Ez a kód a dokumentum irányát automatikus felismerésre állítja (`DocumentDirection.AUTO`), és betölt egy szöveges dokumentumot héber szöveggel. Szükség szerint módosíthatja a dokumentum irányát.

## Teljes forráskód szöveges fájlok betöltéséhez az Aspose.Words for Java segítségével

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Hozzon létre egy egyszerű szöveges dokumentumot karakterlánc formájában, amely részek listákként értelmezhetők.
	// Betöltéskor az első három listát mindig észleli az Aspose.Words,
	// és a Lista objektumok a betöltés után jönnek létre számukra.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// A negyedik lista, szóközzel a lista száma és a listaelem tartalma között,
	// csak akkor észlelhető listaként, ha egy LoadOptions objektum "DetectNumberingWithWhitespaces" értéke igaz,
	// hogy elkerüljük, hogy a számokkal kezdődő bekezdések tévesen listákként jelenjenek meg.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Töltse be a dokumentumot a LoadOptions paraméterként történő alkalmazása közben, és ellenőrizze az eredményt.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Következtetés

Ebben az útmutatóban megvizsgáltuk, hogyan tölthet be szöveges fájlokat az Aspose.Words for Java használatával, hogyan lehet felismerni a listákat, kezelni a szóközöket és szabályozni a szöveg irányát. Ezek a technikák lehetővé teszik a szöveges dokumentumok hatékony kezelését a Java-alkalmazásokban.

## GYIK

### Mi az Aspose.Words for Java?

Az Aspose.Words for Java egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, kezelését és konvertálását Java alkalmazásokban. A funkciók széles skáláját kínálja a szöveggel, táblázatokkal, képekkel és egyéb dokumentumelemekkel való munkavégzéshez.

### Hogyan kezdhetem el az Aspose.Words for Java használatát?

Az Aspose.Words for Java használatának megkezdéséhez kövesse az alábbi lépéseket:
1. Töltse le és telepítse az Aspose.Words for Java könyvtárat.
2.  Tekintse meg a dokumentációt a címen[Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) részletes információkért és példákért.
3. Fedezze fel a mintakódot és az oktatóanyagokat, hogy megtanulja, hogyan kell hatékonyan használni a könyvtárat.

### Hogyan tölthetek be szöveges dokumentumot az Aspose.Words for Java használatával?

 Szöveges dokumentum betöltéséhez az Aspose.Words for Java használatával a`TxtLoadOptions` osztály és a`Document` osztály. Győződjön meg arról, hogy szükség szerint megadta a megfelelő beállításokat a szóközök és a szövegirány kezeléséhez. A részletes példaért tekintse meg a cikk lépésenkénti útmutatóját.

### Átalakíthatok egy betöltött szöveges dokumentumot más formátumba?

 Igen, az Aspose.Words for Java lehetővé teszi a betöltött szöveges dokumentumok különböző formátumokba konvertálását, beleértve a DOCX-et, PDF-t és egyebeket. Használhatja a`Document` osztályt a konverziók végrehajtásához. Tekintse meg a dokumentációt konkrét konverziós példákért.

### Hogyan kezelhetem a szóközöket a betöltött szöveges dokumentumokban?

 Szabályozhatja, hogy a betöltött szöveges dokumentumokban a kezdő és a záró szóközök hogyan legyenek kezelve`TxtLoadOptions` . Opciók, mint`TxtLeadingSpacesOptions` és`TxtTrailingSpacesOptions`lehetővé teszi a terek vágását vagy megőrzését szükség szerint. Példaként tekintse meg a jelen útmutató „Térbeállítások kezelése” című részét.

### Mi a jelentősége a szövegiránynak az Aspose.Words for Java-ban?

Vegyes írásmódot vagy nyelvet, például héber vagy arab, tartalmazó dokumentumok szövegének iránya elengedhetetlen. Az Aspose.Words for Java lehetőséget biztosít a szöveg irányának megadására, biztosítva a szöveg megfelelő megjelenítését és formázását ezeken a nyelveken. Ennek az útmutatónak a "Szöveg irányának vezérlése" szakasza bemutatja, hogyan kell beállítani a szöveg irányát.

### Hol találok további forrásokat és támogatást az Aspose.Words for Java számára?

 További forrásokért, dokumentációért és támogatásért keresse fel a[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/). Ezenkívül részt vehet az Aspose.Words közösségi fórumokon, vagy kapcsolatba léphet az Aspose ügyfélszolgálatával, ha segítségre van szüksége konkrét kérdésekben vagy kérdésekben.

### Alkalmas az Aspose.Words for Java kereskedelmi projektekhez?

Igen, az Aspose.Words for Java alkalmas személyes és kereskedelmi projektekre is. Licencelési lehetőségeket kínál a különféle használati forgatókönyvekhez. Feltétlenül tekintse át a licencfeltételeket és az árakat az Aspose webhelyén, hogy kiválaszthassa a projektjéhez megfelelő licencet.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
