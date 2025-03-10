---
title: Listák használata az Aspose.Words for Java-ban
linktitle: Listák használata
second_title: Aspose.Words Java Document Processing API
description: Tanulja meg a listák használatát az Aspose.Words for Java programban ezzel a lépésről lépésre mutató oktatóanyaggal. Hatékonyan rendszerezze és formázza dokumentumait.
weight: 18
url: /hu/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Listák használata az Aspose.Words for Java-ban


Ebben az átfogó oktatóanyagban megvizsgáljuk, hogyan lehet hatékonyan használni a listákat az Aspose.Words for Java-ban, amely egy hatékony API a Microsoft Word dokumentumok programozott kezelésére. A listák elengedhetetlenek a dokumentumok tartalmának strukturálásához és rendszerezéséhez. A listákkal való munka két kulcsfontosságú szempontjával foglalkozunk: a listák újraindításával minden szakaszban és a listaszintek megadásával. Merüljünk el!

## Az Aspose.Words for Java bemutatása

Mielőtt elkezdenénk a listákkal dolgozni, ismerkedjünk meg az Aspose.Words for Java programmal. Ez az API eszközöket biztosít a fejlesztők számára Word dokumentumok létrehozásához, módosításához és manipulálásához Java környezetben. Sokoldalú megoldás az egyszerű dokumentumgenerálástól a bonyolult formázásig és tartalomkezelésig terjedő feladatokhoz.

### Környezetének beállítása

 Kezdésként győződjön meg arról, hogy az Aspose.Words for Java telepítve van és be van állítva a fejlesztői környezetben. Letöltheti[itt](https://releases.aspose.com/words/java/). 

## Listák újraindítása minden szakasznál

Sok esetben előfordulhat, hogy újra kell indítania a listákat a dokumentum egyes részeiben. Ez hasznos lehet több részből álló strukturált dokumentumok, például jelentések, kézikönyvek vagy tudományos dolgozatok létrehozásához.

Íme egy lépésről lépésre bemutatott útmutató, hogyan érheti el ezt az Aspose.Words for Java használatával:

### A dokumentum inicializálása: 
Kezdje egy új dokumentum objektum létrehozásával.

```java
Document doc = new Document();
```

### Számozott lista hozzáadása: 
Adjon hozzá egy számozott listát a dokumentumhoz. Az alapértelmezett számozási stílust fogjuk használni.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Listabeállítások konfigurálása: 
\Engedélyezze a lista újraindítását minden szakasznál.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### A DocumentBuilder beállítása: 
Hozzon létre egy DocumentBuilder programot, amellyel tartalmat adhat a dokumentumhoz.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Listaelemek hozzáadása: 
Használjon hurkot listaelemek hozzáadásához a dokumentumhoz. A 15. elem után szakasztörést szúrunk be.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Mentse el a dokumentumot: 
Mentse el a dokumentumot a kívánt opciókkal.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Ezen lépések követésével dokumentumokat hozhat létre listákkal, amelyek minden szakasznál újraindulnak, megőrizve az egyértelmű és szervezett tartalomstruktúrát.

## Listaszintek megadása

Az Aspose.Words for Java lehetővé teszi listaszintek megadását, ami különösen akkor hasznos, ha különböző listaformátumokra van szüksége a dokumentumban. Vizsgáljuk meg, hogyan kell ezt megtenni:

### A dokumentum inicializálása: 
Hozzon létre egy új dokumentumobjektumot.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Számozott lista létrehozása: 
Alkalmazzon számozott listasablont a Microsoft Word programból.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Listaszintek megadása: 
Iteráljon különböző listaszinteken, és adjon hozzá tartalmat.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Felsorolásos lista létrehozása: 
Most hozzunk létre egy felsorolt listát.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Határozza meg a felsorolásjeles lista szintjeit: 
A számozott listához hasonlóan adjon meg szinteket és adjon hozzá tartalmat.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Stop lista formázása: 
A lista formázásának leállításához állítsa a listát nullra.

```java
builder.getListFormat().setList(null);
```

### Mentse el a dokumentumot: 
Mentse el a dokumentumot.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Ezeket a lépéseket követve egyéni listaszintű dokumentumokat hozhat létre, amelyek lehetővé teszik a listák formázásának szabályozását a dokumentumokban.

## Teljes forráskód
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // Az IsRestartAtEachSection csak akkor kerül megírásra, ha a megfelelőség magasabb, mint az OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Hozzon létre egy számozott listát az egyik Microsoft Word listasablon alapján
        //és alkalmazza a dokumentumkészítő aktuális bekezdésére.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Kilenc szint található ebben a listában, próbáljuk ki mindegyiket.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Hozzon létre egy felsorolásjeles listát a Microsoft Word listasablonjainak egyike alapján
        //és alkalmazza a dokumentumkészítő aktuális bekezdésére.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Ezzel leállíthatja a lista formázását.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Hozzon létre egy listát egy sablon alapján.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Az első lista újrafelhasználásához újra kell indítanunk a számozást az eredeti listaformázás másolatának létrehozásával.
        List list2 = doc.getLists().addCopy(list1);
        // Az új listát bármilyen módon módosíthatjuk, beleértve az új rajtszám beállítását is.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Következtetés

Gratulálok! Megtanulta, hogyan kell hatékonyan dolgozni listákkal az Aspose.Words for Java programban. A listák kulcsfontosságúak a dokumentumok tartalmának rendszerezéséhez és megjelenítéséhez. Akár újra kell indítania a listákat az egyes szakaszokban, akár a listaszinteket kell megadnia, az Aspose.Words for Java biztosítja a professzionális megjelenésű dokumentumok létrehozásához szükséges eszközöket.

Most már magabiztosan használhatja ezeket a funkciókat a dokumentum-előállítási és -formázási feladatok javítására. Ha bármilyen kérdése van, vagy további segítségre van szüksége, forduljon bizalommal a[Aspose közösségi fórum](https://forum.aspose.com/) támogatásért.

## GYIK

### Hogyan telepíthetem az Aspose.Words for Java programot?
 Az Aspose.Words for Java letölthető innen:[itt](https://releases.aspose.com/words/java/) és kövesse a dokumentációban található telepítési utasításokat.

### Testreszabhatom a listák számozási formátumát?
Igen, az Aspose.Words for Java kiterjedt lehetőségeket kínál a listaszámozási formátumok testreszabására. Részletekért tekintse meg az API dokumentációját.

### Az Aspose.Words for Java kompatibilis a legújabb Word dokumentumszabványokkal?
Igen, az Aspose.Words for Java konfigurálható úgy, hogy megfeleljen a különféle Word dokumentumszabványoknak, beleértve az ISO 29500 szabványt is.

### Létrehozhatok összetett dokumentumokat táblázatokkal és képekkel az Aspose.Words for Java használatával?
Teljesen! Az Aspose.Words for Java támogatja a fejlett dokumentumformázást, beleértve a táblázatokat, képeket és egyebeket. Nézze meg a dokumentációt példákért.

### Hol szerezhetek ideiglenes licencet az Aspose.Words for Java számára?
Kaphat ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
