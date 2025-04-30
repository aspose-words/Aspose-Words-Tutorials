---
"description": "Engedd szabadjára az Aspose.Words erejét Java-ban. Tanuld meg, hogyan tölts be szöveges dokumentumokat, hogyan kezeld a listákat, hogyan kezeld a szóközöket és hogyan szabályozd a szöveg irányát."
"linktitle": "Szövegfájlok betöltése"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Szövegfájlok betöltése az Aspose.Words segítségével Java-ban"
"url": "/hu/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Szövegfájlok betöltése az Aspose.Words segítségével Java-ban


## Bevezetés a szövegfájlok betöltésébe az Aspose.Words for Java segítségével

Ebben az útmutatóban azt vizsgáljuk meg, hogyan tölthetünk be szövegfájlokat az Aspose.Words for Java segítségével, és hogyan kezelhetjük őket Word-dokumentumokként. Különböző szempontokat fogunk áttekinteni, például a listák észlelését, a szóközök kezelését és a szövegirány szabályozását.

## 1. lépés: Listák észlelése

Szöveges dokumentum betöltéséhez és listák észleléséhez kövesse az alábbi lépéseket:

```java
// Hozz létre egy egyszerű szöveges dokumentumot karakterlánc formájában, amelynek részei listaként értelmezhetők.
// Betöltéskor az Aspose.Words mindig felismeri az első három listát,
// és a betöltés után létrejönnek hozzájuk a List objektumok.
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
// A negyedik lista, ahol a lista száma és a listaelem tartalma között szóköz van,
// csak akkor lesz listaként érzékelve, ha a LoadOptions objektumban a "DetectNumberingWithWhitespaces" értéke igaz,
// hogy elkerülje a számokkal kezdődő bekezdések téves felsorolásként való felismerését.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Töltse be a dokumentumot a LoadOptions paraméterrel, és ellenőrizze az eredményt.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Ez a kód bemutatja, hogyan lehet betöltődni egy szöveges dokumentumot különböző listaformátumokkal, és hogyan lehet használni a `DetectNumberingWithWhitespaces` lehetőség a listák helyes felismerésére.

## 2. lépés: A szóközök kezelési beállításai

A szöveges dokumentum betöltésekor a kezdő és záró szóközök szabályozásához a következő kódot használhatja:

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

Ebben a példában betöltünk egy szöveges dokumentumot, és levágjuk a kezdő és a záró szóközöket a következő használatával: `TxtLeadingSpacesOptions.TRIM` és `TxtTrailingSpacesOptions.TRIM`.

## 3. lépés: A szöveg irányának szabályozása

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

Ez a kód automatikus felismerésre állítja be a dokumentum irányát (`DocumentDirection.AUTO`) és betölt egy héber szöveget tartalmazó szöveges dokumentumot. Szükség szerint módosíthatja a dokumentum irányát.

## Teljes forráskód szövegfájlok betöltéséhez az Aspose.Words segítségével Java-ban

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Hozz létre egy egyszerű szöveges dokumentumot karakterlánc formájában, amelynek részei listaként értelmezhetők.
	// Betöltéskor az Aspose.Words mindig felismeri az első három listát,
	// és a betöltés után létrejönnek hozzájuk a List objektumok.
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
	// A negyedik lista, ahol a lista száma és a listaelem tartalma között szóköz van,
	// csak akkor lesz listaként érzékelve, ha a LoadOptions objektumban a "DetectNumberingWithWhitespaces" értéke igaz,
	// hogy elkerülje a számokkal kezdődő bekezdések téves felsorolásként való felismerését.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Töltse be a dokumentumot a LoadOptions paraméterrel, és ellenőrizze az eredményt.
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

Ebben az útmutatóban azt vizsgáltuk meg, hogyan lehet szövegfájlokat betölteni az Aspose.Words for Java segítségével, hogyan lehet listákat észlelni, szóközöket kezelni és a szöveg irányát szabályozni. Ezek a technikák lehetővé teszik a szöveges dokumentumok hatékony kezelését a Java alkalmazásokban.

## GYIK

### Mi az Aspose.Words Java-hoz?

Az Aspose.Words for Java egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára, hogy Word dokumentumokat hozzanak létre, szerkeszszenek és konvertáljanak programozottan Java alkalmazásokban. Széleskörű funkciókat kínál szövegekkel, táblázatokkal, képekkel és más dokumentumelemekkel való munkához.

### Hogyan kezdhetem el az Aspose.Words használatát Java-ban?

Az Aspose.Words Java-beli használatának megkezdéséhez kövesse az alábbi lépéseket:
1. Töltsd le és telepítsd az Aspose.Words for Java könyvtárat.
2. Lásd a dokumentációt a következő címen: [Aspose.Words Java API-referenciához](https://reference.aspose.com/words/java/) részletes információkért és példákért.
3. Ismerd meg a mintakódot és az oktatóanyagokat, hogy megtanuld, hogyan használhatod hatékonyan a könyvtárat.

### Hogyan tölthetek be egy szöveges dokumentumot az Aspose.Words for Java használatával?

Egy szöveges dokumentum betöltéséhez az Aspose.Words for Java használatával használhatja a következőt: `TxtLoadOptions` osztály és a `Document` osztály. Győződjön meg róla, hogy a megfelelő beállításokat adta meg a szóközök és a szövegirány kezeléséhez, szükség szerint. Részletes példáért lásd a cikkben található lépésenkénti útmutatót.

### Átalakíthatok egy betöltött szöveges dokumentumot más formátumokba?

Igen, az Aspose.Words for Java lehetővé teszi a betöltött szöveges dokumentumok különböző formátumokba konvertálását, beleértve a DOCX, PDF és egyebeket. Használhatja a `Document` osztály a konverziók végrehajtásához. A konkrét konverziós példákért tekintse meg a dokumentációt.

### Hogyan kezeljem a szóközöket a betöltött szöveges dokumentumokban?

A betöltött szöveges dokumentumokban a kezdő és a záró szóközök kezelését a következővel szabályozhatja: `TxtLoadOptions`. Lehetőségek, mint például `TxtLeadingSpacesOptions` és `TxtTrailingSpacesOptions` lehetővé teszik a szóközök szükség szerinti levágását vagy megőrzését. Példaért lásd a jelen útmutató „Szóközök kezelési beállításai” című részét.

### Mi a szövegirány jelentősége az Aspose.Words for Java-ban?

szövegirány elengedhetetlen a vegyes írásrendszert vagy nyelvet, például héberül vagy arabul tartalmazó dokumentumokhoz. Az Aspose.Words for Java beállításokat biztosít a szövegirány megadásához, biztosítva a szöveg megfelelő megjelenítését és formázását ezeken a nyelveken. Az útmutató „Szövegirány szabályozása” című szakasza bemutatja, hogyan állíthatja be a szövegirányt.

### Hol találok további forrásokat és támogatást az Aspose.Words for Java-hoz?

További forrásokért, dokumentációért és támogatásért látogassa meg a következő weboldalt: [Aspose.Words Java dokumentációhoz](https://reference.aspose.com/words/java/)Részt vehetsz az Aspose.Words közösségi fórumokon is, vagy felveheted a kapcsolatot az Aspose ügyfélszolgálatával, ha konkrét problémákkal vagy kérdésekkel szeretnél segítséget kérni.

### Alkalmas-e az Aspose.Words for Java kereskedelmi projektekhez?

Igen, az Aspose.Words for Java alkalmas mind személyes, mind kereskedelmi projektekhez. Licencelési lehetőségeket kínál a különféle felhasználási forgatókönyvek kielégítésére. A projektedhez megfelelő licenc kiválasztásához mindenképpen tekintsd át a licencelési feltételeket és az árakat az Aspose weboldalán.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}