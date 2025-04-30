---
"description": "Ismerje meg, hogyan tilthatja le a sortöréseket a Word-dokumentumok oldalain az Aspose.Words for .NET használatával a táblázatok olvashatóságának és formázásának megőrzése érdekében."
"linktitle": "Sorformátum Oldalak közötti sortörés letiltása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Sorformátum Oldalak közötti sortörés letiltása"
"url": "/hu/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sorformátum Oldalak közötti sortörés letiltása

## Bevezetés

Amikor Word-dokumentumokban táblázatokkal dolgozik, érdemes lehet biztosítani, hogy a sorok ne törjenek meg oldalak között, ami elengedhetetlen a dokumentumok olvashatóságának és formázásának megőrzéséhez. Az Aspose.Words for .NET egyszerű módszert kínál a sortörések letiltására az oldalak között.

Ebben az oktatóanyagban végigvezetünk azon, hogyan tilthatod le a sortöréseket az oldalakon egy Word-dokumentumban az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételekkel rendelkezünk:
- Aspose.Words for .NET könyvtár telepítve.
- Egy Word dokumentum, amelyben egy több oldalas táblázat található.

## Névterek importálása

Először importáld a szükséges névtereket a projektedbe:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: A dokumentum betöltése

Töltse be a több oldalas táblázatot tartalmazó dokumentumot.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 2. lépés: Hozzáférés a táblázathoz

Nyissa meg a dokumentum első táblázatát. Ez feltételezi, hogy a módosítani kívánt táblázat a dokumentum első táblázata.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 3. lépés: Oldalak közötti tördelés letiltása az összes sorban

Végigmegyünk a táblázat minden során, és beállítjuk a `AllowBreakAcrossPages` ingatlan `false`Ez biztosítja, hogy a sorok ne törjenek meg oldalak között.

```csharp
// Az oldalak közötti tördelés letiltása a táblázat összes sorában.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## 4. lépés: A dokumentum mentése

Mentse el a módosított dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan tiltható le a sortörések oldalak közötti váltása egy Word-dokumentumban az Aspose.Words for .NET használatával. A fent vázolt lépéseket követve biztosíthatja, hogy a táblázat sorai érintetlenek maradjanak, és ne oszoljanak szét az oldalak között, megőrizve a dokumentum olvashatóságát és formázását.

## GYIK

### Letilthatom a sortöréseket az oldalakon egy adott sorban az összes sor helyett?  
Igen, letilthatja a sortöréseket bizonyos sorokhoz a kívánt sor eléréséhez és a hozzá tartozó beállításához. `AllowBreakAcrossPages` ingatlan `false`.

### Ez a módszer működik egyesített cellákat tartalmazó táblázatok esetén?  
Igen, ez a metódus működik egyesített cellákat tartalmazó táblázatok esetén. A tulajdonság `AllowBreakAcrossPages` a teljes sorra vonatkozik, a cellaegyesítéstől függetlenül.

### Működni fog ez a módszer, ha a tábla egy másik táblába van beágyazva?  
Igen, a beágyazott táblázatokat ugyanúgy elérheti és módosíthatja. Győződjön meg arról, hogy helyesen hivatkozik a beágyazott táblázatra az indexe vagy más tulajdonságai alapján.

### Hogyan tudom ellenőrizni, hogy egy sor lehetővé teszi-e az oldalak közötti tördelést?  
Ellenőrizheti, hogy egy sor lehetővé teszi-e az oldalak közötti tördelést, ha megnyitja a `AllowBreakAcrossPages` a tulajdona `RowFormat` és ellenőrzi az értékét.

### Van mód arra, hogy ezt a beállítást egy dokumentum összes táblázatára alkalmazzam?  
Igen, végigmehetsz a dokumentum összes táblázatán, és mindegyikre alkalmazhatod ezt a beállítást.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}