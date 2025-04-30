---
"description": "Tanuld meg lépésről lépésre, hogyan használd a fejléceket és lábléceket az Aspose.Words for Java programban. Készíts professzionális dokumentumokat könnyedén."
"linktitle": "Fejlécek és láblécek használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Fejlécek és láblécek használata az Aspose.Words programban Java-ban"
"url": "/hu/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fejlécek és láblécek használata az Aspose.Words programban Java-ban


Ebben az átfogó útmutatóban végigvezetünk a fejlécek és láblécek használatának folyamatán az Aspose.Words for Java programban. A fejlécek és láblécek alapvető elemek a dokumentumformázásban, és az Aspose.Words hatékony eszközöket biztosít a létrehozásukhoz és testreszabásukhoz az igényeid szerint.

Most pedig részletesebben vizsgáljuk meg ezeket a lépéseket.

## 1. Bevezetés az Aspose.Words-be

Az Aspose.Words egy hatékony Java API, amely lehetővé teszi Word dokumentumok programozott létrehozását, kezelését és renderelését. Kiterjedt funkciókat kínál a dokumentumok formázásához, beleértve a fejléceket és a lábléceket.

## 2. Java környezet beállítása

Mielőtt elkezdenéd használni az Aspose.Words-öt, győződj meg róla, hogy a Java fejlesztői környezeted megfelelően van beállítva. A szükséges beállítási utasításokat az Aspose.Words dokumentációs oldalán találod: [Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/).

## 3. Új dokumentum létrehozása

A fejlécek és láblécek használatához létre kell hozni egy új dokumentumot az Aspose.Words használatával. A következő kód bemutatja, hogyan kell ezt megtenni:

```java
// Java kód új dokumentum létrehozásához
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Az oldalbeállítás megértése

Az oldalbeállítás kulcsfontosságú a dokumentum elrendezésének szabályozásához. A fejlécekhez és láblécekhez kapcsolódó különféle tulajdonságokat adhatja meg a `PageSetup` osztály. Például:

```java
// Oldaltulajdonságok beállítása
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Eltérő első oldali fejléc/lábléc

Az Aspose.Words lehetővé teszi, hogy különböző fejléceket és lábléceket használj a dokumentum első oldalán. Használd `pageSetup.setDifferentFirstPageHeaderFooter(true);` hogy engedélyezze ezt a funkciót.

## 6. Fejlécek használata

### 6.1. Szöveg hozzáadása a fejlécekhez

Szöveget adhatsz hozzá a fejlécekhez a következővel: `DocumentBuilder`Íme egy példa:

```java
// Szöveg hozzáadása az első oldal fejlécéhez
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Képek beszúrása fejlécekbe

Képek fejlécekbe való beszúrásához használhatja a `insertImage` módszer. Íme egy példa:

```java
// Kép beszúrása a fejlécbe
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Fejlécstílusok testreszabása

A fejlécstílusokat testreszabhatja különféle tulajdonságok, például betűtípus, igazítás és egyebek beállításával, ahogy a fenti példákban is látható.

## 7. Láblécek használata

### 7.1. Szöveg hozzáadása láblécekhez

A fejlécekhez hasonlóan a láblécekhez is hozzáadhat szöveget a `DocumentBuilder`Íme egy példa:

```java
// Szöveg hozzáadása az elsődleges lábléchez
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Szükség szerint illesszen be szöveget és mezőket
```

### 7.2. Képek beszúrása láblécbe

Képek láblécbe szúrásához használja a `insertImage` metódus, akárcsak a fejlécekben.

### 7.3. Lábléc stílusok testreszabása

Lábléc stílusok testreszabása a következővel: `DocumentBuilder`, hasonlóan a fejlécek testreszabásához.

## 8. Oldalszámozás

Oldalszámokat adhatsz meg a fejlécekben és láblécekben olyan mezők használatával, mint például `PAGE` és `NUMPAGES`Ezek a mezők automatikusan frissülnek, amikor oldalakat ad hozzá vagy távolít el.

## 9. Szerzői jogi információk a láblécekben

A dokumentum láblécében szerzői jogi információk hozzáadásához használhat egy két cellából álló táblázatot, az egyiket balra, a másikat jobbra igazítva, ahogy a kódrészletben is látható.

## 10. Több szekcióval való munka

Az Aspose.Words lehetővé teszi, hogy egy dokumentumon belül több szekcióval is dolgozz. Minden egyes szakaszhoz különböző oldalbeállításokat és fejléceket/lábléceket állíthatsz be.

## 11. Fekvő tájolás

Szükség esetén egyes szakaszok tájolását fekvő módra módosíthatja.

## 12. Fejlécek/láblécek másolása az előző szakaszokból

fejlécek és láblécek korábbi szakaszokból való másolása időt takaríthat meg összetett dokumentumok létrehozásakor.

## 13. A dokumentum mentése

A dokumentum létrehozása és testreszabása után ne felejtse el menteni a `doc.save()` módszer.

## Teljes forráskód
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Adja meg, hogy az első oldal fejlécei/láblécei eltérjenek-e a többi oldalétól.
        // A PageSetup.OddAndEvenPagesHeaderFooter tulajdonsággal is megadhatja
        // különböző fejlécek/láblécek a páros és páratlan oldalakhoz.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Helyezzen be egy pozicionált képet a fejléc bal felső sarkába.
        // Az oldal felső/bal szélétől mért távolság 10 pontra van állítva.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Egy kétcellás táblázatot használunk a szöveg egy részének a sorban való elkészítéséhez (oldalszámozással).
        // Balra igazítva, a szöveg másik részét (szerzői jogi védelemmel) jobbra igazítva.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // A PAGE és NUMPAGES mezőket használja az aktuális oldalszám és az oldalak számának automatikus kiszámításához.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Oldaltöréssel hozzon létre egy második oldalt, amelyen az elsődleges fejlécek/láblécek láthatók lesznek.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Ehhez a szakaszhoz nem kell külön első oldali fejléc/lábléc, csak egy címlapra van szükségünk a dokumentumban,
        // és az oldal fejlécét/láblécét már definiáltuk az előző szakaszban.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Ez a szakasz az előző szakasz fejléceit/lábléceit jeleníti meg.
        // alapértelmezés szerint a currentSection.HeadersFooters.LinkToPrevious(false) függvényt hívjuk meg az oldal szélességének törléséhez.
        // más az új szakasznál, ezért különböző cellassagosságokat kell beállítanunk egy lábléc táblázathoz.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Ha a már meglévő fejléc/lábléc készletet szeretnénk használni ehhez a szakaszhoz.
        // De néhány kisebb módosítással célszerű lehet a fejlécek/láblécek másolása
        // az előző szakaszból, és alkalmazzuk a szükséges módosításokat a kívánt helyen.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
A copyHeadersFootersFromPreviousSection metódus forráskódja
```java
    /// <összefoglaló>
    //Klónozza és átmásolja a fejléceket/lábléceket az előző szakaszból a megadott szakaszba.
    /// </összefoglaló>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Következtetés

Ebben az oktatóanyagban áttekintettük a fejlécek és láblécek használatának alapjait az Aspose.Words for Java programban. Megtanultad, hogyan hozhatsz létre, szabhatsz testre és formázhatsz fejléceket és lábléceket, valamint más alapvető dokumentumformázási technikákat is.

További részletekért és a speciális funkciókért lásd a [Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/).

## GYIK

### 1. Hogyan adhatok hozzá oldalszámokat a dokumentumom láblécéhez?
Oldalszámokat adhatsz hozzá a következő beillesztésével: `PAGE` mezőt a láblécbe az Aspose.Words használatával.

### 2. Kompatibilis az Aspose.Words Java fejlesztői környezetekkel?
Igen, az Aspose.Words támogatja a Java fejlesztést. Győződjön meg róla, hogy a szükséges beállítások megvannak.

### 3. Testreszabhatom a fejlécek és láblécek betűtípusát és stílusát?
Természetesen testreszabhatod a betűtípusokat, az igazítást és más stílusokat, hogy a fejlécek és láblécek vizuálisan vonzóbbak legyenek.

### 4. Lehetséges-e különböző fejléceket használni a páros és páratlan oldalakhoz?
Igen, használhatod `PageSetup.OddAndEvenPagesHeaderFooter` hogy a páratlan és páratlan oldalakhoz eltérő fejléceket adjon meg.

### 5. Hogyan kezdhetem el az Aspose.Words for Java használatát?
Kezdésként látogassa meg a [Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/) az API használatára vonatkozó átfogó útmutatásért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}