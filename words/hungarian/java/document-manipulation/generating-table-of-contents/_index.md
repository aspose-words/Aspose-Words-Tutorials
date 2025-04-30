---
"description": "Tanuld meg, hogyan hozhatsz létre és szabhatsz testre tartalomjegyzéket (TOC) az Aspose.Words for Java segítségével. Készíts könnyedén szervezett és professzionális dokumentumokat."
"linktitle": "Tartalomjegyzék létrehozása"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Tartalomjegyzék generálása az Aspose.Words programban Java-hoz"
"url": "/hu/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomjegyzék generálása az Aspose.Words programban Java-hoz


## Bevezetés a tartalomjegyzék létrehozásába az Aspose.Words Java-ban

Ebben az oktatóanyagban végigvezetünk a tartalomjegyzék (TOC) létrehozásának folyamatán az Aspose.Words for Java használatával. A TOC kulcsfontosságú funkció a rendezett dokumentumok létrehozásához. Bemutatjuk, hogyan szabhatod testre a TOC megjelenését és elrendezését.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy az Aspose.Words for Java telepítve és beállítva van a Java projektedben.

## 1. lépés: Új dokumentum létrehozása

Először is hozzunk létre egy új dokumentumot, amellyel dolgozhatunk.

```java
Document doc = new Document();
```

## 2. lépés: Tartalomjegyzék stílusok testreszabása

A tartalomjegyzék megjelenésének testreszabásához módosíthatja a hozzá tartozó stílusokat. Ebben a példában az első szintű tartalomjegyzék-bejegyzéseket félkövér betűtípussal fogjuk szedni.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## 3. lépés: Tartalom hozzáadása a dokumentumhoz

Hozzáadhatja a tartalmát a dokumentumhoz. Ezt a tartalmat fogja felhasználni a tartalomjegyzék létrehozásához.

## 4. lépés: Tartalomjegyzék létrehozása

A tartalomjegyzék létrehozásához illesszen be egy tartalomjegyzék mezőt a dokumentum kívánt helyére. Ez a mező automatikusan kitöltődik a dokumentum címsorai és stílusai alapján.

```java
// Szúrjon be egy tartalomjegyzék mezőt a dokumentum kívánt helyére.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## 5. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a tartalomjegyzékkel együtt.

```java
doc.save("your_output_path_here");
```

## Tabulátorpozíciók testreszabása a tartalomjegyzékben

A tartalomjegyzékben a tabulátorpozíciókat is testreszabhatja az oldalszámok elrendezésének szabályozásához. A tabulátorpozíciók módosításának módja:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Szerezd meg az ebben a bekezdésben használt első tabulátort, amely igazítja az oldalszámokat.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Távolítsa el a régi fület.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Helyezzen be egy új fület módosított pozícióba (pl. 50 egységgel balra).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Most már van egy testreszabott tartalomjegyzéke a dokumentumban, amelyben az oldalszámok igazításához igazított tabulátorhelyek vannak.


## Következtetés

Ebben az oktatóanyagban azt vizsgáltuk meg, hogyan hozhatunk létre tartalomjegyzéket (TOC) az Aspose.Words for Java segítségével, amely egy hatékony könyvtár a Word dokumentumokkal való munkához. Egy jól strukturált TOC elengedhetetlen a hosszú dokumentumok rendszerezéséhez és navigálásához, az Aspose.Words pedig eszközöket biztosít a TOC-ok egyszerű létrehozásához és testreszabásához.

## GYIK

### Hogyan módosíthatom a tartalomjegyzék-bejegyzések formázását?

tartalomjegyzék szintjeihez társított stílusokat a következővel módosíthatja: `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, ahol X a tartalomjegyzék szintje.

### Hogyan adhatok hozzá több szintet a tartalomjegyzékhez?

Ha több szintet szeretne a tartalomjegyzékbe foglalni, módosíthatja a tartalomjegyzék mezőt, és megadhatja a kívánt szintek számát.

### Módosíthatom a tabulátorpozíciókat bizonyos tartalomjegyzék-bejegyzésekhez?

Igen, ahogy a fenti kódpéldában is látható, a tabulátorpozíciókat a bekezdéseken végighaladva, ennek megfelelően módosíthatod.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}