---
date: 2025-12-27
description: Tanulja meg, hogyan állíthat be irányt, tölthet be txt fájlokat, távolíthatja
  el a szóközöket, és konvertálhat txt-et docx formátumba az Aspose.Words for Java
  segítségével.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Hogyan állítsuk be az irányt és töltsünk be szövegfájlokat az Aspose.Words
  for Java segítségével
url: /hu/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsuk be az irányt és töltsünk be szövegfájlokat az Aspose.Words for Java-val

## Bevezetés a szövegfájlok betöltésébe az Aspose.Words for Java-val

Ebben az útmutatóban megtudja, **hogyan állítsa be az irányt** egyszerű szöveges dokumentumok betöltésekor, és gyakorlati módszereket lát **txt betöltésére**, **szóközök levágására**, valamint **txt konvertálására docx formátumba** az Aspose.Words for Java használatával. Akár dokumentum‑konverziós szolgáltatást épít, akár finomhangolt vezérlést igényel a listák felismeréséhez, ez a tutorial minden lépésen végigvezet, világos magyarázatokkal és azonnal futtatható kóddal.

## Gyors válaszok
- **Hogyan állíthatom be a szöveg irányát egy betöltött TXT fájlhoz?** Használja a `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` metódust, vagy adja meg a `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT` értékeket.
- **Képes-e az Aspose.Words számozott listákat felismerni egyszerű szövegben?** Igen – engedélyezze a `DetectNumberingWithWhitespaces` beállítást a `TxtLoadOptions`‑ban.
- **Hogyan vághatom le a kezdő és záró szóközöket?** Állítsa be a `TxtLeadingSpacesOptions.TRIM` és a `TxtTrailingSpacesOptions.TRIM` értékeket.
- **Lehetséges-e egy sorban konvertálni egy TXT fájlt DOCX formátumba?** Töltse be a TXT‑t `TxtLoadOptions` segítségével, majd hívja a `Document.save("output.docx")` metódust.
- **Milyen Java verzió szükséges?** A Java 8+ elegendő az Aspose.Words 24.x‑hez.

## Mi az a „hogyan állítsuk be az irányt” az Aspose.Words-ben?

Amikor egy szövegfájl jobb‑balra írt írásrendszereket (pl. héber vagy arab) tartalmaz, a könyvtárnak ismernie kell az olvasási sorrendet. A `DocumentDirection` felsorolt típus lehetővé teszi, hogy **manuálisan állítsa be az irányt**, vagy hagyja, hogy az Aspose automatikusan felismerje, ezáltal biztosítva a helyes elrendezést és a kétirányú (bidi) formázást.

## Miért használjuk az Aspose.Words-t TXT fájlok betöltéséhez?

- **Pontos lista felismerés** – kezeli a számozott, felsorolásos és szóköz‑elválasztott listákat.
- **Finomhangolt szóközkezelés** – levágja vagy megőrzi a kezdő/záró szóközöket.
- **Automatikus szövegirány felismerés** – tökéletes többnyelvű dokumentumokhoz.
- **Egylépéses konverzió** – töltsön be egy `.txt` fájlt, és mentse `.docx`, `.pdf` vagy bármely támogatott formátumba.

## Előfeltételek
- Java 8 vagy újabb.
- Aspose.Words for Java könyvtár (adja hozzá a Maven/Gradle függőséget vagy a JAR‑t a projektjéhez).
- Alapvető ismeretek a Java I/O stream‑ekről.

## Lépésről‑lépésre útmutató

### 1. lépés: Listák felismerése (hogyan töltsünk be txt)

A szöveges dokumentum betöltéséhez és a listák automatikus felismeréséhez hozzon létre egy `TxtLoadOptions` példányt, és engedélyezze a lista felismerést. Az alábbi kód több lista stílust mutat, és engedélyezi a szóköz‑érzékeny számozást.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro tipp:** Ha csak alap lista felismerésre van szüksége, kihagyhatja a szóköz opciót – az Aspose továbbra is felismeri a szabványos `1.` és `1)` mintákat.

### 2. lépés: Szóközkezelési beállítások (hogyan vágjunk le szóközöket)

A kezdő és záró szóközök gyakran okoznak formázási hibákat. Használja a `TxtLeadingSpacesOptions` és a `TxtTrailingSpacesOptions` beállításokat a viselkedés szabályozásához.

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

> **Miért fontos:** A szóközök levágása megakadályozza a nem kívánt behúzást a létrehozott DOCX‑ben, így a dokumentum tisztán néz ki manuális utófeldolgozás nélkül.

### 3. lépés: Szövegirány vezérlése (hogyan állítsuk be az irányt)

Jobb‑balra írt nyelvek esetén a betöltés előtt állítsa be a dokumentum irányát. Az alábbi példa egy héber szövegfájlt tölt be, és kiírja a bidi jelzőt az irány megerősítéséhez.

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

> **Gyakori hibák:** A `DocumentDirection` beállításának elhagyása torz arab/hebre szöveget eredményezhet, ahol a karakterek rossz sorrendben jelennek meg.

### Teljes forráskód a szövegfájlok betöltéséhez az Aspose.Words for Java-val

Az alábbiakban a teljes, azonnal futtatható forráskód található, amely egyesíti a lista felismerést, a szóközkezelést és az irányvezérlést. Másolja be egyetlen osztályba, és futtassa a három tesztmetódust külön‑külön.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Gyakori problémák és megoldások

| Probléma | Ok | Megoldás |
|----------|----|----------|
| Listák nem kerülnek felismerésre | `DetectNumberingWithWhitespaces` `false` maradt a szóköz‑elválasztott listák esetén | Engedélyezze a `loadOptions.setDetectNumberingWithWhitespaces(true)` beállítást |
| Túlzott behúzás a betöltés után | A kezdő szóközök megmaradtak | Állítsa be a `TxtLeadingSpacesOptions.TRIM` értéket |
| A héber szöveg fordítottként jelenik meg | A dokumentum irány nincs beállítva vagy `LEFT_TO_RIGHT` értékre van állítva | Használja a `DocumentDirection.AUTO` vagy `RIGHT_TO_LEFT` értéket |
| A kimeneti DOCX üres | A bemeneti stream nem lett visszaállítva a második betöltés előtt | Hozzon létre új `ByteArrayInputStream`‑et minden betöltési hívásnál |

## Gyakran Ismételt Kérdések

### K: Mi az Aspose.Words for Java?

A: Az Aspose.Words for Java egy erőteljes dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és konvertáljanak Word dokumentumokat Java alkalmazásokban. Széles körű funkciókat támogat, az egyszerű szövegbetöltéstől a komplex formázásig és konverzióig.

### K: Hogyan kezdhetem el az Aspose.Words for Java használatát?

A: 1. Töltse le és telepítse az Aspose.Words for Java könyvtárat. 2. Tekintse meg a dokumentációt a [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) oldalon a részletes információkért és példákért. 3. Fedezze fel a mintakódokat és tutorialokat, hogy hatékonyan megtanulja a könyvtár használatát.

### K: Hogyan töltsek be egy szöveges dokumentumot az Aspose.Words for Java-val?

A: Használja a `TxtLoadOptions` osztályt a `Document` konstruktorával együtt. Adja meg a listafelismerés, szóközkezelés vagy szövegirány beállításait, ahogyan a fenti lépésről‑lépésre szakaszokban bemutattuk.

### K: Átkonvertálhatom a betöltött szöveges dokumentumot más formátumokra?

A: Igen. A TXT fájl betöltése után egy `Document` objektumba, hívja a `doc.save("output.pdf")`, `doc.save("output.docx")` vagy bármely más támogatott formátumot.

### K: Hogyan kezelem a szóközöket a betöltött szöveges dokumentumokban?

A: A kezdő és záró szóközöket a `TxtLeadingSpacesOptions` és a `TxtTrailingSpacesOptions` segítségével szabályozhatja. Állítsa őket `TRIM` értékre a nem kívánt szóközök eltávolításához, vagy `PRESERVE` értékre, ha az eredeti szóközöket meg kell tartani.

### K: Mi a szövegirány jelentősége az Aspose.Words for Java-ban?

A: A szövegirány biztosítja a jobb‑balra írt írásrendszerek (héber, arab stb.) helyes megjelenítését. A `DocumentDirection` beállításával garantálja, hogy a kétirányú (bidi) szöveg megfelelően jelenik meg a létrehozott dokumentumban.

### K: Hol találok további forrásokat és támogatást az Aspose.Words for Java-hoz?

A: Látogassa meg a [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) oldalt az API hivatkozásokért, kópmintákért és részletes útmutatókért. Csatlakozhat az Aspose közösségi fórumokhoz vagy felveheti a kapcsolatot az Aspose támogatással konkrét kérdések esetén.

### K: Alkalmas-e az Aspose.Words for Java kereskedelmi projektekhez?

A: Igen. Licencelési lehetőségeket kínál személyes és kereskedelmi felhasználásra egyaránt. Tekintse át a licencfeltételeket az Aspose weboldalán, hogy a projektjéhez megfelelő csomagot válasszon.

## Összegzés

Most már rendelkezik egy teljes eszközkészlettel a **txt fájlok betöltéséhez**, **listák felismeréséhez**, **szóközök levágásához**, és a **szövegirány beállításához**, amikor egyszerű szöveget gazdag Word dokumentummá konvertál az Aspose.Words for Java-val. Alkalmazza ezeket a mintákat a dokumentumfolyamatok automatizálásához, a többnyelvű támogatás javításához, és minden alkalommal tiszta, professzionális kimenet biztosításához.

---

**Utolsó frissítés:** 2025-12-27  
**Tesztelt verzió:** Aspose.Words for Java 24.12  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}