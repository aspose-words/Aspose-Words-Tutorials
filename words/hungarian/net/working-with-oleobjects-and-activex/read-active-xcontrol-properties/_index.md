---
title: Olvassa el az Active XControl tulajdonságait a Word fájlból
linktitle: Olvassa el az Active XControl tulajdonságait a Word fájlból
second_title: Aspose.Words Document Processing API
description: A lépésenkénti útmutatóból megtudhatja, hogyan olvashatja ki az ActiveX-vezérlő tulajdonságait Word-fájlokból az Aspose.Words for .NET használatával. Fejlessze dokumentumautomatizálási készségeit.
weight: 10
url: /hu/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Olvassa el az Active XControl tulajdonságait a Word fájlból

## Bevezetés

A mai digitális korban az automatizálás kulcsfontosságú a termelékenység növelésében. Ha ActiveX-vezérlőket tartalmazó Word-dokumentumokkal dolgozik, előfordulhat, hogy különféle célokra el kell olvasnia azok tulajdonságait. Az ActiveX-vezérlők, például a jelölőnégyzetek és a gombok fontos adatokat tárolhatnak. Az Aspose.Words for .NET használatával hatékonyan kinyerheti és programozottan kezelheti ezeket az adatokat.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  Aspose.Words for .NET Library: Letöltheti innen[itt](https://releases.aspose.com/words/net/).
2. Visual Studio vagy bármely C# IDE: A kód írása és végrehajtása.
3. Word-dokumentum ActiveX-vezérlőkkel: például "ActiveX-vezérlők.docx".
4. C# alapismeretek: A C# programozás ismerete szükséges a követéshez.

## Névterek importálása

Először is importáljuk a szükséges névtereket az Aspose.Words for .NET használatához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## 1. lépés: Töltse be a Word-dokumentumot

A kezdéshez be kell töltenie az ActiveX-vezérlőket tartalmazó Word-dokumentumot.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## 2. lépés: Inicializáljon egy karakterláncot a tulajdonságok megtartásához

Ezután inicializáljon egy üres karakterláncot az ActiveX-vezérlők tulajdonságainak tárolásához.

```csharp
string properties = "";
```

## 3. lépés: Iteráljon alakzatokon keresztül a dokumentumban

Az ActiveX-vezérlők megtalálásához a dokumentum összes alakzatát át kell ismételnünk.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Az ActiveX-vezérlő feldolgozása
    }
}
```

## 4. lépés: A tulajdonságok kibontása az ActiveX-vezérlőkből

A cikluson belül ellenőrizze, hogy a vezérlő Forms2OleControl-e. Ha igen, öntse ki, és vonja ki a tulajdonságokat.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## 5. lépés: Számolja meg az összes ActiveX-vezérlőt

Az összes alakzat megismétlése után számolja meg a talált ActiveX-vezérlők teljes számát.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## 6. lépés: Jelenítse meg a Tulajdonságokat

Végül nyomtassa ki a kibontott tulajdonságokat a konzolra.

```csharp
Console.WriteLine("\n" + properties);
```

## Következtetés

És megvan! Sikeresen megtanulta, hogyan olvassa be az ActiveX-vezérlő tulajdonságait egy Word-dokumentumból az Aspose.Words for .NET használatával. Ez az oktatóanyag egy dokumentum betöltését, az alakzatok iterációját és az ActiveX-vezérlők tulajdonságainak kinyerését tárgyalta. Ha követi ezeket a lépéseket, automatizálhatja a fontos adatok kinyerését a Word-dokumentumokból, javítva ezzel a munkafolyamat hatékonyságát.

## GYIK

### Mik azok az ActiveX-vezérlők a Word dokumentumokban?
Az ActiveX-vezérlők Word dokumentumokba ágyazott interaktív objektumok, például jelölőnégyzetek, gombok és szövegmezők, amelyeket űrlapok létrehozására és feladatok automatizálására használnak.

### Módosíthatom az ActiveX-vezérlők tulajdonságait az Aspose.Words for .NET használatával?
Igen, az Aspose.Words for .NET lehetővé teszi az ActiveX-vezérlők tulajdonságainak programozott módosítását.

### Ingyenesen használható az Aspose.Words for .NET?
 Az Aspose.Words for .NET ingyenes próbaverziót kínál, de a további használathoz licencet kell vásárolnia. Ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/).

### Használhatom az Aspose.Words for .NET-et a C#-on kívül más .NET-nyelvekkel is?
Igen, az Aspose.Words for .NET bármely .NET nyelvvel használható, beleértve a VB.NET-et és az F#-ot is.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Részletes dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
