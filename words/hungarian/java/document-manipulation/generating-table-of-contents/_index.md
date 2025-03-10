---
title: Tartalomjegyzék létrehozása az Aspose.Words for Java programban
linktitle: Tartalomjegyzék létrehozása
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan hozhat létre és szabhat testre tartalomjegyzéket (TOC) az Aspose.Words for Java használatával. Rendezett és professzionális dokumentumokat készíthet könnyedén.
weight: 21
url: /hu/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomjegyzék létrehozása az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java tartalomjegyzék létrehozásába

Ebben az oktatóanyagban végigvezetjük a tartalomjegyzék (TOC) létrehozásának folyamatán az Aspose.Words for Java használatával. A TOC kulcsfontosságú funkció a szervezett dokumentumok létrehozásához. Kitérünk arra, hogyan szabhatjuk testre a TOC megjelenését és elrendezését.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy az Aspose.Words for Java telepítve van, és be van állítva a Java projektben.

## 1. lépés: Hozzon létre egy új dokumentumot

Először is hozzunk létre egy új dokumentumot, amellyel dolgozni szeretnénk.

```java
Document doc = new Document();
```

## 2. lépés: A TOC stílusok testreszabása

A TOC megjelenésének testreszabásához módosíthatja a hozzá tartozó stílusokat. Ebben a példában az első szintű TOC bejegyzéseket félkövérre szedjük.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## 3. lépés: Adjon hozzá tartalmat a dokumentumhoz

A tartalmat hozzáadhatja a dokumentumhoz. Ez a tartalom lesz felhasználva a TOC létrehozásához.

## 4. lépés: A TOC létrehozása

A TOC létrehozásához szúrjon be egy tartalomjegyzék mezőt a dokumentum kívánt helyére. Ez a mező automatikusan kitöltődik a dokumentumban található címsorok és stílusok alapján.

```java
// Szúrjon be egy TOC mezőt a dokumentum kívánt helyére.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## 5. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot a tartalomjegyzékkel.

```java
doc.save("your_output_path_here");
```

## Tabulátorok testreszabása a TOC-ban

Az oldalszámok elrendezésének szabályozásához testreszabhatja a TOC tabulátorpontjait is. Így módosíthatja a tabulátorokat:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Szerezze be az ebben a bekezdésben használt első tabulátort, amely az oldalszámokat igazítja.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Távolítsa el a régi fület.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Szúrjon be egy új fület egy módosított pozícióba (pl. 50 egységgel balra).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Most már van egy személyre szabott tartalomjegyzéke a dokumentumban, beállított tabulátorokkal az oldalszámok igazításához.


## Következtetés

Ebben az oktatóanyagban megvizsgáltuk, hogyan hozhat létre tartalomjegyzéket (TOC) az Aspose.Words for Java segítségével, amely egy hatékony könyvtár a Word-dokumentumokkal való munkavégzéshez. A jól strukturált tartalomjegyzék elengedhetetlen a hosszadalmas dokumentumok rendszerezéséhez és navigálásához, az Aspose.Words pedig eszközöket biztosít a tartalomjegyzékek könnyű létrehozásához és testreszabásához.

## GYIK

### Hogyan változtathatom meg a TOC-bejegyzések formázását?

 A tartalomjegyzék-szintekhez társított stílusokat a segítségével módosíthatja`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, ahol X a TOC szint.

### Hogyan adhatok több szintet a TOC-hoz?

Ha több szintet szeretne felvenni a TOC-ba, módosíthatja a TOC mezőt, és megadhatja a szintek kívánt számát.

### Módosíthatom a tabulátorpozíciókat bizonyos tartalomjegyzék-bejegyzéseknél?

Igen, ahogy a fenti kódpéldában is látható, módosíthatja az adott tartalomjegyzék-bejegyzések tabulátorpozícióit a bekezdések iterációjával és a tabulátorok megfelelő módosításával.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
