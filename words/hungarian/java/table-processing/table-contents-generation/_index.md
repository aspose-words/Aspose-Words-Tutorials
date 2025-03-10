---
title: Tartalomjegyzék Generáció
linktitle: Tartalomjegyzék Generáció
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan hozhat létre dinamikus tartalomjegyzéket az Aspose.Words for Java használatával. Mester TOC generálás lépésről lépésre útmutatóval és forráskód példákkal.
weight: 14
url: /hu/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomjegyzék Generáció

## Bevezetés

Küzdött már valaha egy dinamikus és professzionális megjelenésű tartalomjegyzék (TOC) létrehozásával a Word-dokumentumokban? Ne keressen tovább! Az Aspose.Words for Java segítségével a teljes folyamatot automatizálhatja, így időt takaríthat meg és biztosítja a pontosságot. Akár átfogó jelentést, akár akadémiai dolgozatot készít, ez az oktatóanyag végigvezeti Önt a Java segítségével programozott TOC létrehozásán. Készen állsz a merülésre? Kezdjük is!

## Előfeltételek

A kódolás megkezdése előtt győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Java Development Kit (JDK): telepítve van a rendszerére. Letöltheti innen[Az Oracle webhelye](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words for Java Library: Töltse le a legújabb verziót a[kiadási oldal](https://releases.aspose.com/words/java/).
3. Integrált fejlesztői környezet (IDE): például az IntelliJ IDEA, az Eclipse vagy a NetBeans.
4.  Aspose ideiglenes licenc: Az értékelési korlátozások elkerülése érdekében szerezze be a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

## Csomagok importálása

Az Aspose.Words for Java hatékony használatához importálja a szükséges osztályokat. Íme az import:

```java
import com.aspose.words.*;
```

Kövesse ezeket a lépéseket dinamikus tartalomjegyzék létrehozásához a Word-dokumentumban.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 Az első lépés egy új dokumentum létrehozása és a`DocumentBuilder` osztályt manipulálni.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: A Word dokumentumot jelöli.
- `DocumentBuilder`: Segítő osztály, amely lehetővé teszi a dokumentum egyszerű kezelését.

## 2. lépés: Helyezze be a tartalomjegyzéket

Most pedig illesszük be a TOC-t a dokumentum elejére.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: TOC mezőt szúr be. A paraméterek megadják:
  - `\o "1-3"`: Tartalmazza az 1–3. szintű címsorokat.
  - `\h`: Hiperhivatkozások létrehozása a bejegyzésekben.
  - `\z`: Az oldalszámok letiltása webes dokumentumokhoz.
  - `\u`: Stílusok megőrzése a hiperhivatkozásokhoz.
- `insertBreak`: Oldaltörést ad a tartalomjegyzék után.

## 3. lépés: Adjon hozzá címeket a tartalomjegyzék feltöltéséhez

A TOC feltöltéséhez fejlécstílusú bekezdéseket kell hozzáadnia.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : A bekezdésstílust egy adott címsorszintre állítja (pl.`HEADING_1`, `HEADING_2`).
- `writeln`: Szöveget ad hozzá a dokumentumhoz a megadott stílusban.

## 4. lépés: Beágyazott címsorok hozzáadása

A TOC-szintek bemutatásához használjon beágyazott címsorokat.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Adjon hozzá mélyebb szintek címsorait a hierarchia megjelenítéséhez a tartalomjegyzékben.

## 5. lépés: Frissítse a TOC mezőket

A TOC mezőt frissíteni kell a legújabb fejlécek megjelenítéséhez.


```java
doc.updateFields();
```

- `updateFields`: Frissíti a dokumentum összes mezőjét, biztosítva, hogy a tartalomjegyzék tükrözze a hozzáadott címsorokat.

## 6. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a kívánt formátumba.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exportálja a dokumentumot a`.docx` fájlt. Megadhat más formátumokat is, mint pl`.pdf` vagy`.txt` ha szükséges.

## Következtetés

Gratulálok! Sikeresen létrehozott egy dinamikus tartalomjegyzéket egy Word-dokumentumban az Aspose.Words for Java használatával. Néhány sornyi kóddal automatizált egy olyan feladatot, amely egyébként órákig is eltarthatna. Szóval, mi lesz ezután? Kísérletezzen különböző címsorstílusokkal és formátumokkal, hogy a tartalomjegyzékét az adott igényekhez igazítsa.

## GYIK

### Testreszabhatom a TOC formátumot?
Teljesen! Beállíthatja a tartalomjegyzék paramétereit, például az oldalszámokat, a szöveg igazítását vagy az egyéni címsorstílusok használatát.

### Kötelező licenc az Aspose.Words for Java számára?
 Igen, a teljes funkcionalitáshoz licenc szükséges. Kezdheti a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

### Létrehozhatok TOC-t egy meglévő dokumentumhoz?
 Igen! Helyezze be a dokumentumot a`Document` objektumot, és kövesse ugyanazokat a lépéseket a tartalomjegyzék beszúrásához és frissítéséhez.

### Ez működik PDF-exportálásnál?
 Igen, a tartalomjegyzék megjelenik a PDF-ben, ha menti a dokumentumot`.pdf` formátum.

### Hol találok további dokumentációt?
 Nézze meg a[Aspose.Words for Java dokumentáció](https://reference.aspose.com/words/java/) további példákért és részletekért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
