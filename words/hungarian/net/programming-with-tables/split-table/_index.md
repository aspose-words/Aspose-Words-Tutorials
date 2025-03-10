---
title: Osztott táblázat
linktitle: Osztott táblázat
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan oszthat fel táblázatokat Word dokumentumokban az Aspose.Words for .NET használatával. Lépésről lépésre mutató útmutatónk egyszerűvé és hatékonysá teszi a táblázatkezelést.
weight: 10
url: /hu/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Osztott táblázat

## Bevezetés

Előfordult már, hogy egy Word-dokumentumban egy nagy táblázattal dolgozik, és azt kívánta, bárcsak két kisebb, jobban kezelhető táblázatra oszthatná? Nos, ma belemerülünk abba, hogy pontosan hogyan érheti el ezt az Aspose.Words for .NET használatával. Legyen szó kiterjedt adattáblázatokról vagy összetett dokumentumstruktúrákról, a táblázatok felosztása javíthatja az olvashatóságot és a rendszerezést. Nézzük meg lépésről lépésre a tábla felosztásának folyamatát az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belevágnánk az oktatóanyagba, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET Library: Győződjön meg arról, hogy letöltötte és telepítette az Aspose.Words for .NET könyvtárat. Beszerezheti a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Hozzon létre egy fejlesztői környezetet .NET-keretrendszer támogatással, például a Visual Studio-val.
3. Mintadokumentum: Készítsen Word dokumentumot (`Tables.docx`) legalább egy táblázattal a felosztási művelet alkalmazásához.

## Névterek importálása

Először is importálja a szükséges névtereket a projektbe. Ez lehetővé teszi az Aspose.Words által biztosított osztályok és metódusok elérését.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: Töltse be a dokumentumot

Kezdjük a felosztani kívánt táblázatot tartalmazó dokumentum betöltésével. Ügyeljen arra, hogy a dokumentum helyes elérési útját adja meg.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## 2. lépés: Határozza meg a felosztandó táblázatot

Ezután azonosítsa és kérje le a felosztani kívánt táblát. Ebben a példában a dokumentum első táblázatát célozzuk meg.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## 3. lépés: Válassza ki a sort a felosztáshoz

Határozza meg azt a sort, ahol a táblázatot fel szeretné osztani. Itt felosztjuk a táblázatot a harmadik sorban (beleértve).

```csharp
Row row = firstTable.Rows[2];
```

## 4. lépés: Hozzon létre egy új táblázattárolót

Hozzon létre egy új táblázattárolót az eredeti táblából áthelyezett sorok tárolására.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## 5. lépés: Helyezze be az új asztali tárolót

Helyezze be az új táblázattárolót közvetlenül az eredeti táblázat után a dokumentumba.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## 6. lépés: Puffer bekezdés hozzáadása

Adjon hozzá egy puffer bekezdést a két tábla közé, hogy biztosítsa, hogy különállóak maradjanak.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## 7. lépés: Helyezze át a sorokat az új táblázatba

Helyezze át a sorokat az eredeti táblából az új táblázattárolóba. Ez a ciklus addig folytatódik, amíg a megadott sort (beleértve) el nem helyezi.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## 8. lépés: Mentse el a dokumentumot

Végül mentse el a módosított dokumentumot felosztott táblázatokkal.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Következtetés

És megvan! Az alábbi lépések követésével egyszerűen feloszthat egy táblázatot egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a megközelítés segít a nagy táblák hatékonyabb kezelésében, javítva a dokumentumok olvashatóságát és rendszerezését. Próbálja ki, és nézze meg, hogyan egyszerűsíti le a Word dokumentumok táblázataival végzett munkát.

## GYIK

### Feloszthatok egy táblázatot több sorra?
Igen, feloszthat egy táblázatot több sorra, ha megismétli a folyamatot minden felosztási pontra.

### Mi történik az eredeti táblázat formázásával?
Az új tábla örökli az eredeti tábla formázását. Bármilyen formázási módosítás szükség szerint alkalmazható az új táblára.

### Lehetséges a táblák összevonása?
Igen, összevonhat táblázatokat, ha sorokat helyez át egyik táblázatból a másikba hasonló módszerekkel.

### Működik ez a módszer beágyazott táblákkal?
Igen, az Aspose.Words for .NET támogatja a beágyazott táblákon végzett műveleteket is.

### Automatizálhatom ezt a folyamatot több dokumentum esetében?
Teljesen! Létrehozhat egy szkriptet vagy alkalmazást a több dokumentum táblázatfelosztási folyamatának automatizálásához.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
