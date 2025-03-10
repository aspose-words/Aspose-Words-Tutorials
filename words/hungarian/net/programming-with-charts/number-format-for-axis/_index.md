---
title: Számformátum A tengelyhez egy diagramon
linktitle: Számformátum A tengelyhez egy diagramon
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan formázhatja a diagram tengelyszámait az Aspose.Words for .NET használatával. Fokozatmentesen fokozza dokumentuma olvashatóságát és professzionalizmusát.
weight: 10
url: /hu/net/programming-with-charts/number-format-for-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Számformátum A tengelyhez egy diagramon

## Bevezetés

Szia! Dolgozott már diagramokkal a dokumentumaiban, és azt kívánta, bárcsak formázhatná a tengelyén lévő számokat, hogy professzionálisabbnak tűnjenek? Nos, szerencséd van! Ebben az oktatóanyagban részletesen megvizsgáljuk, hogyan érheti el ezt az Aspose.Words for .NET használatával. Ez a hatékony könyvtár lehetővé teszi a Word-dokumentumok olyan egyszerű kezelését, mint a torta. Ma pedig arra összpontosítunk, hogy ezeket a diagramtengelyeket egyedi számformátumokkal alakítsuk át.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy mindennel megvan, amire szüksége van. Íme egy gyors ellenőrző lista:

-  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy kompatibilis .NET-keretrendszer van telepítve.
- Fejlesztési környezet: Az olyan IDE, mint a Visual Studio, tökéletesen működik.
- Alapvető C# ismerete: Ez segít követni a kódolási példákat.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a projektbe. Ez olyan, mintha egy ház építése előtt alapoznánk meg. Adja hozzá a következőket a kódfájl tetején található direktívák használatával:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Most bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre.

## 1. lépés: A dokumentum beállítása

Címsor: Inicializálja a dokumentumot

Először is létre kell hoznia egy új dokumentumot és egy dokumentumkészítőt. Tekintsd ezt a lépést úgy, mint a vászon és az ecset előkészítése a remekmű elkészítése előtt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt,`dataDir` a dokumentumkönyvtár elérési útja, ahová a végső fájlt menteni fogja.`Document` és`DocumentBuilder` az Aspose.Words osztályai, amelyek segítenek a Word dokumentumok létrehozásában és kezelésében.

## 2. lépés: Diagram beszúrása

Címsor: Diagram hozzáadása a dokumentumhoz

Ezután adjunk hozzá egy diagramot a dokumentumhoz. Itt kezdődik a varázslat. Beszúrunk egy oszlopdiagramot, amely üres vászonként fog működni.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 A`InsertChart` metódus meghatározott típusú (jelen esetben oszlop) és méretű diagramot szúr be a dokumentumba.

## 3. lépés: A diagramsorozat testreszabása

Címsor: Töltse fel diagramját adatokkal

Most hozzá kell adnunk néhány adatot a diagramunkhoz. Ez a lépés hasonló a diagram kitöltéséhez értelmes információkkal.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

 Itt adunk hozzá egy új sorozatot, az „Aspose Series 1” nevet, öt adatponttal. A`Series.Clear` módszer biztosítja, hogy minden már meglévő adatot eltávolítsanak az új sorozatunk hozzáadása előtt.

## 4. lépés: A tengelyszámok formázása

Rovat: Szépítsd a tengelyszámaidat

Végül formázzuk meg a számokat az Y tengelyen, hogy jobban olvashatóak legyenek. Ez olyan, mintha az utolsó simításokat helyezné el a műalkotásokon.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

 A`FormatCode` tulajdonság lehetővé teszi, hogy egyéni formátumot állítson be a tengelyen lévő számokhoz. Ebben a példában`#,##0`biztosítja, hogy a nagy számok ezres vesszővel együtt jelenjenek meg.

## 5. lépés: A dokumentum mentése

Rovat: Mentse meg remekművét

Most, hogy minden be van állítva, ideje elmenteni a dokumentumot. Ez a lépés a munkája nagy feltárása.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

 Itt, a`Save` metódus elmenti a dokumentumot a megadott elérési útra a fájlnévvel`WorkingWithCharts.NumberFormatForAxis.docx`.

## Következtetés

És megvan! Sikeresen formázta a diagram Y tengelyén lévő számokat az Aspose.Words for .NET használatával. Ez nemcsak professzionálisabbá teszi a diagramokat, hanem javítja az olvashatóságot is. Az Aspose.Words számos olyan funkciót kínál, amelyek segítségével lenyűgöző Word-dokumentumokat hozhat létre programozottan. Tehát miért nem fedezhet fel többet, és nézze meg, mit tehet még?

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, kezelését és konvertálását.

### A tengelyszámokon kívül formázhatom a diagram más aspektusait is?
Teljesen! Az Aspose.Words for .NET segítségével formázhatja a címeket, címkéket, és még a diagram megjelenését is testreszabhatja.

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?
 Igen, kaphat a[ingyenes próbaverzió itt](https://releases.aspose.com/).

### Használhatom az Aspose.Words for .NET-et a C#-on kívül más .NET-nyelvekkel is?
Igen, az Aspose.Words for .NET kompatibilis bármely .NET nyelvvel, beleértve a VB.NET-et és az F#-ot is.

### Hol találok részletesebb dokumentációt?
 A részletes dokumentáció elérhető a[Aspose.Words for .NET dokumentációs oldal](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
