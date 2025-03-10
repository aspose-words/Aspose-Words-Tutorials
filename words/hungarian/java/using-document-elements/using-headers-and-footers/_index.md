---
title: Fejlécek és láblécek használata az Aspose.Words for Java-ban
linktitle: Fejlécek és láblécek használata
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg lépésről lépésre a fejlécek és láblécek használatát az Aspose.Words for Java programban. Hozzon létre professzionális dokumentumokat könnyedén.
weight: 16
url: /hu/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fejlécek és láblécek használata az Aspose.Words for Java-ban


Ebben az átfogó útmutatóban végigvezetjük az Aspose.Words for Java fejléceivel és lábléceivel való munka folyamatán. A fejlécek és a láblécek alapvető elemei a dokumentumformázásnak, az Aspose.Words pedig hatékony eszközöket biztosít azok létrehozásához és igényeinek megfelelő testreszabásához.

Most pedig nézzük meg ezeket a lépéseket részletesen.

## 1. Az Aspose.Words bemutatása

Az Aspose.Words egy hatékony Java API, amely lehetővé teszi Word-dokumentumok programozott létrehozását, kezelését és megjelenítését. Széleskörű szolgáltatásokat kínál a dokumentum formázásához, beleértve a fejlécet és a láblécet.

## 2. Java környezet beállítása

 Az Aspose.Words használatának megkezdése előtt győződjön meg arról, hogy a Java fejlesztői környezet megfelelően van beállítva. A szükséges beállítási utasításokat az Aspose.Words dokumentációs oldalán találja:[Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/).

## 3. Új dokumentum létrehozása

A fejlécek és láblécek használatához új dokumentumot kell létrehoznia az Aspose.Words használatával. A következő kód bemutatja, hogyan kell ezt megtenni:

```java
// Java kód új dokumentum létrehozásához
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Az oldalbeállítások ismertetése

 Az oldalbeállítás kulcsfontosságú a dokumentum elrendezésének szabályozásához. A fejlécekhez és láblécekhez kapcsolódó különféle tulajdonságokat adhat meg a`PageSetup` osztály. Például:

```java
// Az oldal tulajdonságainak beállítása
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Különböző első oldal fejléce/lábléce

Az Aspose.Words lehetővé teszi, hogy a dokumentum első oldalán különböző fejlécek és láblécek legyenek. Használat`pageSetup.setDifferentFirstPageHeaderFooter(true);` hogy engedélyezze ezt a funkciót.

## 6. Fejlécek használata

### 6.1. Szöveg hozzáadása a fejlécekhez

 A fejlécekhez szöveget adhat hozzá a`DocumentBuilder`. Íme egy példa:

```java
// Szöveg hozzáadása az első oldal fejlécéhez
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Képek beszúrása a fejlécekbe

 Ha képeket szeretne beszúrni a fejlécekbe, használhatja a`insertImage` módszer. Íme egy példa:

```java
// Kép beszúrása a fejlécbe
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Fejlécstílusok testreszabása

A fejlécstílusokat testreszabhatja különféle tulajdonságok, például betűtípus, igazítás és egyebek beállításával, amint az a fenti példákban látható.

## 7. Munka láblécekkel

### 7.1. Szöveg hozzáadása a láblécekhez

 A fejlécekhez hasonlóan a láblécekhez is hozzáadhat szöveget a`DocumentBuilder`. Íme egy példa:

```java
// Szöveg hozzáadása az elsődleges lábléchez
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Szükség szerint szúrjon be szöveget és mezőket
```

### 7.2. Képek beszúrása láblécekbe

 Ha képeket szeretne beszúrni a láblécekbe, használja a`insertImage` módszer, akárcsak a fejlécekben.

### 7.3. A láblécstílusok testreszabása

 A láblécstílusok testreszabása a`DocumentBuilder`hasonlóan a fejlécek testreszabásához.

## 8. Oldalszámozás

 A fejlécekbe és a láblécekbe oldalszámokat is beilleszthet olyan mezők használatával, mint pl`PAGE` és`NUMPAGES`. Ezek a mezők automatikusan frissülnek, amikor oldalakat ad hozzá vagy eltávolít.

## 9. Szerzői jogi információk a láblécekben

Ha szerzői jogi információkat szeretne hozzáadni a dokumentum láblécéhez, használhat két cellát tartalmazó táblázatot, az egyiket balra, a másikat pedig jobbra igazítva, ahogy a kódrészlet is mutatja.

## 10. Munka több szakasszal

Az Aspose.Words lehetővé teszi, hogy egy dokumentumon belül több résszel dolgozzon. Az egyes szakaszokhoz különböző oldalbeállításokat és fejléceket/lábléceket állíthat be.

## 11. Táj tájolás

Szükség esetén módosíthatja az egyes szakaszok tájolását fekvő módba.

## 12. Fejlécek/láblécek másolása az előző szakaszokból

Az előző szakaszok fejléceinek és lábléceinek másolása időt takaríthat meg összetett dokumentumok létrehozásakor.

## 13. A dokumentum mentése

 dokumentum létrehozása és testreszabása után ne felejtse el menteni a`doc.save()` módszer.

## Teljes forráskód
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Adja meg, hogy az első oldal fejlécei/láblécei eltérjenek-e a többi oldaltól.
        // A PageSetup.OddAndEvenPagesHeaderFooter tulajdonságot is megadhatja
        // különböző fejlécek/láblécek páratlan és páros oldalakhoz.
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
        // Helyezzen be egy elhelyezett képet a fejléc felső/bal sarkába.
        // Az oldal felső/bal szélétől mért távolság 10 pont.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Két cellás táblázatot használunk, hogy a szöveg egy részét a sorban készítsük el (oldalszámozással).
        // Balra igazítandó, a szöveg másik része (szerzői joggal) pedig jobbra igazítandó.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // PAGE és NUMPAGES mezőket használ az aktuális oldalszám és sok oldal automatikus kiszámításához.
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
        // Oldaltöréssel hozzon létre egy második oldalt, amelyen az elsődleges fejléc/lábléc látható.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Ennek a szakasznak nincs szüksége más első oldali fejlécre/láblécre, csak egy címlapra van szükség a dokumentumban,
        //és ennek az oldalnak a fejléce/lábléce már meghatározásra került az előző részben.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Ez a szakasz az előző szakasz fejléceit/lábléceit jeleníti meg
        // alapértelmezés szerint hívja a currentSection.HeadersFooters.LinkToPrevious(false) elemet az oldalszélesség törléséhez
        // eltérő az új szakaszban, ezért különböző cellaszélességeket kell beállítanunk egy lábléctáblázathoz.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Ha ehhez a szakaszhoz a már meglévő fejléc/lábléc készletet szeretnénk használni.
        // Kisebb módosításokkal azonban célszerű lehet a fejléceket/lábléceket másolni
        // az előző részből, és alkalmazzuk a szükséges módosításokat ott, ahol szeretnénk.
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
    /// Klónozza és másolja a fejléceket/lábléceket az előző szakaszból a megadott szakaszba.
    /// </summary>
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

Ebben az oktatóanyagban bemutattuk az Aspose.Words for Java fejléceivel és lábléceivel való munka alapjait. Megtanulta fej- és láblécek létrehozását, testreszabását és stílusát, valamint más alapvető dokumentumformázási technikákat.

 További részletekért és speciális funkciókért tekintse meg a[Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/).

## GYIK

### 1. Hogyan adhatok oldalszámokat a dokumentumom láblécéhez?
 Oldalszámokat adhat hozzá a`PAGE` mezőbe az Aspose.Words használatával.

### 2. Az Aspose.Words kompatibilis a Java fejlesztői környezetekkel?
Igen, az Aspose.Words támogatja a Java fejlesztést. Győződjön meg arról, hogy a szükséges beállítások a helyükön vannak.

### 3. Testreszabhatom a fej- és láblécek betűtípusát és stílusát?
Természetesen testreszabhatja a betűtípusokat, az igazítást és más stílusokat, hogy a fejlécet és láblécet látványosan tetszetőssé tegye.

### 4. Lehetséges-e különböző fejlécek páratlan és páros oldalakhoz?
 Igen, használhatod`PageSetup.OddAndEvenPagesHeaderFooter` különböző fejlécek megadásához a páratlan és páros oldalakhoz.

### 5. Hogyan kezdhetem el az Aspose.Words for Java használatát?
 Kezdésként látogassa meg a[Aspose.Words Java dokumentáció](https://reference.aspose.com/words/java/) átfogó útmutatásért az API használatához.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
