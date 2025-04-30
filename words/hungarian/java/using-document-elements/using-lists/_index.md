---
"description": "Tanuld meg a listák használatát az Aspose.Words for Java programban ezzel a lépésről lépésre szóló oktatóanyaggal. Rendszerezd és formázd hatékonyan a dokumentumaidat."
"linktitle": "Listák használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Listák használata az Aspose.Words Java-ban"
"url": "/hu/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Listák használata az Aspose.Words Java-ban


Ebben az átfogó oktatóanyagban megvizsgáljuk, hogyan használhatjuk hatékonyan a listákat az Aspose.Words for Java-ban, amely egy hatékony API a Microsoft Word dokumentumok programozott használatához. A listák elengedhetetlenek a dokumentumok tartalmának strukturálásához és rendszerezéséhez. A listákkal való munka két kulcsfontosságú aspektusát fogjuk áttekinteni: a listák újraindítását minden szakaszban és a listaszintek megadását. Vágjunk bele!

## Bevezetés az Aspose.Words Java-ba

Mielőtt elkezdenénk a listákkal dolgozni, ismerkedjünk meg az Aspose.Words for Java API-val. Ez az API eszközöket biztosít a fejlesztőknek Word-dokumentumok létrehozásához, módosításához és kezeléséhez Java környezetben. Sokoldalú megoldást kínál az egyszerű dokumentumgenerálástól az összetett formázásig és tartalomkezelésig terjedő feladatokhoz.

### környezet beállítása

Kezdésként győződjön meg arról, hogy az Aspose.Words for Java telepítve és beállítva van a fejlesztői környezetében. Letöltheti [itt](https://releases.aspose.com/words/java/). 

## Listák újraindítása minden szakaszban

Sok esetben előfordulhat, hogy a dokumentum minden egyes szakaszánál újra kell kezdeni a listákat. Ez hasznos lehet több szakaszból álló strukturált dokumentumok, például jelentések, kézikönyvek vagy tudományos dolgozatok létrehozásakor.

Íme egy lépésről lépésre útmutató arról, hogyan érheted el ezt az Aspose.Words for Java használatával:

### Dokumentum inicializálása: 
Kezdje egy új dokumentumobjektum létrehozásával.

```java
Document doc = new Document();
```

### Számozott lista hozzáadása: 
Számozott lista hozzáadása a dokumentumhoz. Az alapértelmezett számozási stílust fogjuk használni.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Listabeállítások konfigurálása: 
\Engedélyezze a lista újraindítását minden szakasznál.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Dokumentumkészítő beállítása: 
Hozz létre egy DocumentBuildert, hogy tartalmat adhass a dokumentumodhoz.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Listaelemek hozzáadása: 
Használj ciklust listaelemek hozzáadásához a dokumentumodhoz. A 15. elem után szakasztörést szúrunk be.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Dokumentum mentése: 
Mentse el a dokumentumot a kívánt beállításokkal.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

A következő lépéseket követve olyan dokumentumokat hozhat létre, amelyek listái minden szakasznál újraindulnak, így megőrizve a világos és rendezett tartalomszerkezetet.

## Listaszintek megadása

Az Aspose.Words for Java lehetővé teszi a listaszintek megadását, ami különösen hasznos, ha különböző listaformátumokra van szükség a dokumentumon belül. Nézzük meg, hogyan teheti ezt meg:

### Dokumentum inicializálása: 
Hozz létre egy új dokumentumobjektumot.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Számozott lista létrehozása: 
Számozott lista sablon alkalmazása a Microsoft Wordből.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Listaszintek megadása: 
Iterálj végig a különböző listaszinteken, és adj hozzá tartalmat.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Lista létrehozása felsorolásjellel: 
Most hozzunk létre egy felsorolásjeles listát.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Felsorolási szintek megadása: 
A számozott listához hasonlóan itt is megadhatók a szintek és adható hozzá a tartalom.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Leállítási lista formázása: 
A lista formázásának leállításához állítsa a listát null értékre.

```java
builder.getListFormat().setList(null);
```

### Dokumentum mentése: 
Mentse el a dokumentumot.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

A következő lépéseket követve egyéni listaszintekkel rendelkező dokumentumokat hozhat létre, amelyek lehetővé teszik a dokumentumokban található listák formázásának szabályozását.

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
        // Az IsRestartAtEachSection csak akkor kerül kiírásra, ha a megfelelőség magasabb, mint az OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Számozott lista létrehozása a Microsoft Word listasablonjainak egyike alapján
        // és alkalmazza azt a dokumentumszerkesztő aktuális bekezdésére.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Kilenc szint van ezen a listán, próbáljuk ki mindet.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Listajeles lista létrehozása a Microsoft Word listasablonjainak egyike alapján
        // és alkalmazza azt a dokumentumszerkesztő aktuális bekezdésére.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Ez egy módja a lista formázásának leállítására.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Hozz létre egy listát egy sablon alapján.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Az első lista újbóli felhasználásához újra kell kezdenünk a számozást az eredeti listaformázás másolatának létrehozásával.
        List list2 = doc.getLists().addCopy(list1);
        // Az új listát bármilyen módon módosíthatjuk, beleértve egy új rajtszám beállítását is.
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

Gratulálunk! Megtanultad, hogyan kell hatékonyan dolgozni listákkal az Aspose.Words for Java programban. A listák kulcsfontosságúak a dokumentumok tartalmának rendszerezéséhez és megjelenítéséhez. Akár minden szakaszban újra kell kezdened a listákat, akár meg kell adnod a lista szintjeit, az Aspose.Words for Java biztosítja a professzionális megjelenésű dokumentumok létrehozásához szükséges eszközöket.

Mostantól magabiztosan használhatja ezeket a funkciókat a dokumentumgenerálási és formázási feladatok fejlesztéséhez. Ha bármilyen kérdése van, vagy további segítségre van szüksége, ne habozzon kapcsolatba lépni a ...-val. [Aspose közösségi fórum](https://forum.aspose.com/) támogatásért.

## GYIK

### Hogyan telepíthetem az Aspose.Words-öt Java-hoz?
Az Aspose.Words Java-hoz letölthető innen: [itt](https://releases.aspose.com/words/java/) és kövesse a dokumentációban található telepítési utasításokat.

### Testreszabhatom a listák számozási formátumát?
Igen, az Aspose.Words for Java kiterjedt lehetőségeket kínál a listaszámozási formátumok testreszabásához. A részletekért tekintse meg az API dokumentációját.

### Kompatibilis az Aspose.Words for Java a legújabb Word dokumentumszabványokkal?
Igen, az Aspose.Words for Java beállítható úgy, hogy megfeleljen a különféle Word dokumentumszabványoknak, beleértve az ISO 29500 szabványt is.

### Létrehozhatok összetett dokumentumokat táblázatokkal és képekkel az Aspose.Words for Java használatával?
Abszolút! Az Aspose.Words for Java támogatja a fejlett dokumentumformázást, beleértve a táblázatokat, képeket és egyebeket. Példákért tekintse meg a dokumentációt.

### Hol szerezhetek ideiglenes licencet az Aspose.Words for Java-hoz?
Ideiglenes jogosítványt szerezhet [itt](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}