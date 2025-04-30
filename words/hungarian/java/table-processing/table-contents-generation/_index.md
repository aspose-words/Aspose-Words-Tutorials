---
"description": "Tanuld meg, hogyan hozhatsz létre dinamikus tartalomjegyzéket az Aspose.Words for Java segítségével. Sajátítsd el a tartalomjegyzék generálását lépésről lépésre útmutatóval és forráskód példákkal."
"linktitle": "Tartalomjegyzék generálása"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Tartalomjegyzék generálása"
"url": "/hu/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomjegyzék generálása

## Bevezetés

Nehézséget okozott már a dinamikus és professzionális megjelenésű tartalomjegyzék (TOC) létrehozása a Word-dokumentumaidban? Ne keress tovább! Az Aspose.Words for Java segítségével automatizálhatod a teljes folyamatot, időt takarítva meg és biztosítva a pontosságot. Akár egy átfogó jelentést, akár egy tudományos dolgozatot készítesz, ez az oktatóanyag végigvezet a tartalomjegyzék programozott létrehozásán Java-ban. Készen állsz a belevágni? Kezdjük is!

## Előfeltételek

Mielőtt elkezdenénk a kódolást, győződjünk meg arról, hogy a következőkkel rendelkezünk:

1. Java fejlesztőkészlet (JDK): Telepítve van a rendszerére. Letöltheti innen: [Az Oracle weboldala](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words Java könyvtárhoz: Töltse le a legújabb verziót innen: [kiadási oldal](https://releases.aspose.com/words/java/).
3. Integrált fejlesztői környezet (IDE): Például az IntelliJ IDEA, az Eclipse vagy a NetBeans.
4. Aspose Ideiglenes Licenc: Az értékelési korlátozások elkerülése érdekében szerezzen be egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

## Csomagok importálása

Az Aspose.Words hatékony Java-beli használatához importáld a szükséges osztályokat. Az importálás a következő:

```java
import com.aspose.words.*;
```

Kövesse az alábbi lépéseket egy dinamikus tartalomjegyzék létrehozásához a Word-dokumentumban.

## 1. lépés: A dokumentum és a DocumentBuilder inicializálása

Az első lépés egy új dokumentum létrehozása és használata `DocumentBuilder` osztály manipulálni azt.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: A Word dokumentumot jelöli.
- `DocumentBuilder`Egy segítő osztály, amely lehetővé teszi a dokumentum egyszerű kezelését.

## 2. lépés: Tartalomjegyzék beillesztése

Most illesszük be a tartalomjegyzéket a dokumentum elejére.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Beszúr egy tartalomjegyzék mezőt. A paraméterek a következőket adják meg:
  - `\o "1-3"`: Tartalmazza az 1–3. szintű címsorokat.
  - `\h`: Bejegyzések hiperhivatkozások létrehozása.
  - `\z`: Oldalszámok letiltása webes dokumentumokban.
  - `\u`: Hivatkozások stílusainak megőrzése.
- `insertBreak`: Oldaltörést ad hozzá a tartalomjegyzék után.

## 3. lépés: Címsorok hozzáadása a tartalomjegyzék kitöltéséhez

A tartalomjegyzék kitöltéséhez címsorstílusokkal kell bekezdéseket hozzáadni.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: Bekezdésstílust állít be egy adott címsorszintre (pl. `HEADING_1`, `HEADING_2`).
- `writeln`Szöveget ad a dokumentumhoz a megadott stílusban.

## 4. lépés: Beágyazott címsorok hozzáadása

A tartalomjegyzék szintjeinek bemutatásához használjon beágyazott címsorokat.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Adjon hozzá mélyebb szintek címsorait a tartalomjegyzék hierarchiájának megjelenítéséhez.

## 5. lépés: Tartalomjegyzék mezők frissítése

A tartalomjegyzék mezőt frissíteni kell a legújabb címsorok megjelenítéséhez.


```java
doc.updateFields();
```

- `updateFields`: Frissíti a dokumentum összes mezőjét, biztosítva, hogy a tartalomjegyzék tükrözze a hozzáadott címsorokat.

## 6. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a kívánt formátumban.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: Exportálja a dokumentumot egy `.docx` fájl. Megadhat más formátumokat is, például `.pdf` vagy `.txt` ha szükséges.

## Következtetés

Gratulálunk! Sikeresen létrehoztál egy dinamikus tartalomjegyzéket egy Word-dokumentumban az Aspose.Words for Java segítségével. Mindössze néhány sornyi kóddal automatizáltál egy feladatot, amely egyébként órákig is eltarthatna. Szóval, mi a következő lépés? Kísérletezz különböző címsorstílusokkal és formátumokkal, hogy a tartalomjegyzéket az igényeidhez igazítsd.

## GYIK

### Testreszabhatom a tartalomjegyzék formátumát?
Természetesen! Módosíthatod a tartalomjegyzék paramétereit, például az oldalszámok hozzáadását, a szöveg igazítását vagy az egyéni címsorstílusok használatát.

### Kötelező licenc az Aspose.Words for Java használatához?
Igen, a teljes funkcionalitáshoz licenc szükséges. Kezdheti egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

### Létrehozhatok tartalomjegyzéket egy meglévő dokumentumhoz?
Igen! Töltse be a dokumentumot egy `Document` objektumot, és kövesse ugyanazokat a lépéseket a tartalomjegyzék beszúrásához és frissítéséhez.

### Ez működik PDF exportálásnál?
Igen, a tartalomjegyzék megjelenik a PDF-ben, ha a dokumentumot ide menti: `.pdf` formátum.

### Hol találok további dokumentációt?
Nézd meg a [Aspose.Words Java dokumentációhoz](https://reference.aspose.com/words/java/) további példákért és részletekért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}