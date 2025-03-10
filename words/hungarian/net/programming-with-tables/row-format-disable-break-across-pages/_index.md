---
title: Sorformátum Az oldalak közötti törés letiltása
linktitle: Sorformátum Az oldalak közötti törés letiltása
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan tilthatja le a sortöréseket a Word-dokumentumok oldalain az Aspose.Words for .NET használatával a táblázat olvashatóságának és formázásának megőrzése érdekében.
weight: 10
url: /hu/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sorformátum Az oldalak közötti törés letiltása

## Bevezetés

Amikor Word dokumentumokban táblázatokkal dolgozik, érdemes lehet biztosítani, hogy a sorok ne törjenek oldalakra, ami elengedhetetlen lehet a dokumentumok olvashatóságának és formázásának megőrzéséhez. Az Aspose.Words for .NET egyszerű módot kínál az oldalak közötti sortörések letiltására.

Ebben az oktatóanyagban végigvezetjük a sortörések letiltásának folyamatán egy Word-dokumentumban az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
- Aspose.Words for .NET könyvtár telepítve.
- Word dokumentum több oldalra kiterjedő táblázattal.

## Névterek importálása

Először is importálja a szükséges névtereket a projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: Töltse be a dokumentumot

Töltse be a több oldalas táblázatot tartalmazó dokumentumot.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 2. lépés: Nyissa meg a táblázatot

Nyissa meg a dokumentum első táblázatát. Ez azt feltételezi, hogy a módosítani kívánt tábla a dokumentum első táblája.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 3. lépés: Tiltsa le az oldalak közötti törést minden sorban

 Lapozzon végig a táblázat minden során, és állítsa be a`AllowBreakAcrossPages`tulajdonát`false`. Ez biztosítja, hogy a sorok ne törjenek szét az oldalakon.

```csharp
// Az oldalak közötti törés letiltása a táblázat összes sorában.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## 4. lépés: Mentse el a dokumentumot

Mentse el a módosított dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan lehet letiltani a sortöréseket egy Word-dokumentum oldalain az Aspose.Words for .NET használatával. A fent vázolt lépések követésével biztosíthatja, hogy a táblázat sorai sértetlenek maradjanak, és ne oszlanak szét az oldalakon, megőrizve a dokumentum olvashatóságát és formázását.

## GYIK

### Letilthatom a sortörést az oldalak között egy adott sorban az összes sor helyett?  
 Igen, letilthatja a sortöréseket adott soroknál, ha eléri a kívánt sort, és beállítja azt`AllowBreakAcrossPages`tulajdonát`false`.

### Működik ez a módszer egyesített cellákat tartalmazó táblázatoknál?  
 Igen, ez a módszer összevont cellákat tartalmazó táblázatoknál működik. Az ingatlan`AllowBreakAcrossPages` a teljes sorra vonatkozik, függetlenül a cellaegyesítéstől.

### Működni fog ez a módszer, ha a tábla egy másik táblába van beágyazva?  
Igen, a beágyazott táblákat ugyanúgy elérheti és módosíthatja. Győződjön meg róla, hogy megfelelően hivatkozik a beágyazott táblára annak indexe vagy egyéb tulajdonságai alapján.

### Hogyan ellenőrizhetem, hogy egy sor lehetővé teszi-e az oldalak közötti törést?  
 Ellenőrizheti, hogy egy sor lehetővé teszi-e az oldalak közötti törést, ha eléri a`AllowBreakAcrossPages` tulajdona a`RowFormat` és ellenőrzi az értékét.

### Van rá mód, hogy ezt a beállítást a dokumentum összes táblájára alkalmazzuk?  
Igen, végignézheti a dokumentum összes táblázatát, és mindegyikre alkalmazhatja ezt a beállítást.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
