---
title: Táblázat generálása Datatable-ból
linktitle: Táblázat generálása Datatable-ból
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan hozhat létre táblázatot DataTable-ből az Aspose.Words for Java használatával. Hozzon létre professzionális Word dokumentumokat formázott táblázatokkal könnyedén.
weight: 11
url: /hu/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Táblázat generálása Datatable-ból

## Bevezetés

táblázatok dinamikus adatforrásokból történő létrehozása sok alkalmazásban gyakori feladat. Függetlenül attól, hogy jelentéseket, számlákat vagy adatösszesítéseket hoz létre, ha egy táblázatot programozottan tölt fel adatokkal, sok időt és erőfeszítést takaríthat meg. Ebben az oktatóanyagban megvizsgáljuk, hogyan hozhat létre táblázatot DataTable-ből az Aspose.Words for Java használatával. A folyamatot kezelhető lépésekre bontjuk, így biztosítva, hogy az egyes részeket világosan megértse.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy mindennel rendelkezünk, ami a kezdéshez szükséges:

1.  Java Development Kit (JDK): Győződjön meg arról, hogy a JDK telepítve van a gépen. Letöltheti a[Oracle webhely](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words for Java: Szüksége lesz az Aspose.Words könyvtárra. A legújabb verziót innen töltheti le[Aspose kiadási oldala](https://releases.aspose.com/words/java/).

3. IDE: Az olyan integrált fejlesztési környezet (IDE), mint az IntelliJ IDEA vagy az Eclipse, megkönnyíti a kódolást.

4. Alapvető Java ismerete: A Java programozási koncepciók ismerete segít jobban megérteni a kódrészleteket.

5. Mintaadatok: Ebben az oktatóanyagban egy „List of people.xml” nevű XML-fájlt használunk az adatforrás szimulálására. Létrehozhatja ezt a fájlt mintaadatokkal teszteléshez.

## 1. lépés: Hozzon létre egy új dokumentumot

Először is létre kell hoznunk egy új dokumentumot, ahol a táblázatunk található. Ez a vászon munkánk számára.

```java
Document doc = new Document();
```

 Itt példányosítunk egy újat`Document` objektum. Ez szolgál majd munkadokumentumunkként, ahol elkészítjük a táblázatunkat.

## 2. lépés: Inicializálja a DocumentBuilder programot

 Ezután a`DocumentBuilder` osztályba, amivel könnyebben kezelhetjük a dokumentumot.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 A`DocumentBuilder` Az objektum módszereket biztosít táblázatok, szövegek és egyéb elemek dokumentumba való beillesztésére.

## 3. lépés: Állítsa be az oldaltájolást

Mivel arra számítunk, hogy táblázatunk széles lesz, az oldaltájolást fekvőre állítjuk.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Ez a lépés döntő fontosságú, mert biztosítja, hogy asztalunk szépen elférjen az oldalon anélkül, hogy levágnánk.

## 4. lépés: Töltse be az adatokat XML-ből

 Most be kell töltenünk adatainkat az XML fájlból a`DataTable`. Innen származnak adataink.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 Itt beolvassuk az XML-fájlt, és lekérjük az első táblát az adatkészletből. Ez`DataTable` tárolja a dokumentumunkban megjeleníteni kívánt adatokat.

## 5. lépés: Importálja a táblát a DataTable alkalmazásból

Most jön az izgalmas rész: adataink importálása a dokumentumba táblázatként.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 A módszert hívjuk`importTableFromDataTable` , áthaladva a`DocumentBuilder` , a miénk`DataTable`, és egy logikai érték, amely jelzi, hogy szerepeljen-e az oszlopfejlécek.

## 6. lépés: alakítsa ki az asztal stílusát

Ha megvan az asztalunk, alkalmazhatunk némi stílust, hogy jól nézzen ki.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Ez a kód előre meghatározott stílust alkalmaz a táblázatra, javítva annak vizuális vonzerejét és olvashatóságát.

## 7. lépés: Távolítsa el a nem kívánt sejteket

Ha van olyan oszlopa, amelyet nem szeretne megjeleníteni, például egy képoszlopot, könnyen eltávolíthatja.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Ez a lépés biztosítja, hogy táblázatunk csak a releváns információkat tartalmazza.

## 8. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumunkat a generált táblázattal.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Ez a sor menti a dokumentumot a megadott könyvtárba, lehetővé téve az eredmények áttekintését.

## Az importTableFromDataTable metódus

 Nézzük meg közelebbről a`importTableFromDataTable` módszer. Ez a módszer felelős a táblaszerkezet létrehozásáért és adatokkal való feltöltéséért.

### 1. lépés: Indítsa el a táblázatot

Először is el kell indítanunk egy új táblát a dokumentumban.

```java
Table table = builder.startTable();
```

Ez inicializál egy új táblát a dokumentumunkban.

### 2. lépés: Oszlopcímek hozzáadása

 Ha oszlopfejléceket szeretnénk szerepeltetni, akkor ellenőrizzük a`importColumnHeadings` zászló.

```java
if (importColumnHeadings) {
    // Tárolja az eredeti formázást
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Állítsa be a címsor formázását
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Oszlopnevek beszúrása
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Az eredeti formázás visszaállítása
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

 Ez a kódblokk formázza a címsort, és beszúrja az oszlopok nevét a`DataTable`.

### 3. lépés: Töltse fel a táblázatot adatokkal

 Most végigpörgetjük az egyes sorokat`DataTable` adatok beszúrásához a táblázatba.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

Ebben a részben különböző adattípusokat kezelünk, a dátumokat megfelelően formázzuk, míg más adatokat szövegként beszúrunk.

### 4. lépés: Zárja be a táblázatot

Végül az összes adat beszúrása után befejezzük a táblázatot.

```java
builder.endTable();
```

 Ez a sor jelzi táblázatunk végét, lehetővé téve a`DocumentBuilder` tudni, hogy befejeztük ezt a részt.

## Következtetés

És megvan! Sikeresen megtanulta, hogyan hozhat létre táblázatot DataTable-ből az Aspose.Words for Java használatával. Ezeket a lépéseket követve könnyedén hozhat létre dinamikus táblázatokat a dokumentumokban különböző adatforrások alapján. Akár jelentéseket, akár számlákat készít, ez a módszer leegyszerűsíti a munkafolyamatot és javítja a dokumentumkészítési folyamatot.

## GYIK

### Mi az Aspose.Words for Java?
Az Aspose.Words for Java egy hatékony könyvtár Word-dokumentumok programozott létrehozásához, kezeléséhez és konvertálásához.

### Használhatom ingyenesen az Aspose.Words-t?
 Igen, az Aspose ingyenes próbaverziót kínál. Letöltheti innen[itt](https://releases.aspose.com/).

### Hogyan alakíthatom ki a táblázatokat az Aspose.Words-ben?
Stílusokat alkalmazhat a könyvtár által biztosított előre meghatározott stílusazonosítók és opciók használatával.

### Milyen típusú adatokat illeszthetek be a táblázatokba?
Különféle adattípusokat, például szöveget, számokat és dátumokat szúrhat be, amelyek ennek megfelelően formázhatók.

### Hol kaphatok támogatást az Aspose.Words számára?
 Támogatást találhat és kérdéseket tehet fel a[Aspose fórum](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
