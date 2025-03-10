---
title: Kösse az SDT-t az egyéni Xml-részhez
linktitle: Kösse az SDT-t az egyéni Xml-részhez
second_title: Aspose.Words Document Processing API
description: Ebben a lépésenkénti oktatóanyagban megtudhatja, hogyan köthet strukturált dokumentumcímkéket (SDT-k) egyéni XML-részekhez a Word dokumentumokban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-sdt/bind-sdt-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kösse az SDT-t az egyéni Xml-részhez

## Bevezetés

Az egyéni XML-adatokkal kölcsönhatásba lépő dinamikus Word-dokumentumok létrehozása jelentősen növelheti alkalmazásai rugalmasságát és funkcionalitását. Az Aspose.Words for .NET robusztus szolgáltatásokat nyújt a strukturált dokumentumcímkék (SDT) egyéni XML-részekhez való kötésére, lehetővé téve az adatokat dinamikusan megjelenítő dokumentumok létrehozását. Ebben az oktatóanyagban lépésről lépésre végigvezetjük az SDT-nek egy egyéni XML-részhez kötésének folyamatán. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

-  Aspose.Words for .NET: Letöltheti a legújabb verziót innen[Aspose.Words .NET kiadásokhoz](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármely más kompatibilis .NET IDE.
- Alapvető C# ismerete: C# programozási nyelv és .NET keretrendszer ismerete.

## Névterek importálása

Az Aspose.Words for .NET hatékony használatához importálnia kell a szükséges névtereket a projektbe. Adja hozzá a következőket a kódfájl tetején található direktívák használatával:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Saving;
```

Bontsuk le a folyamatot kezelhető lépésekre, hogy könnyebben követhető legyen. Minden lépés a feladat egy meghatározott részét fedi le.

## 1. lépés: Inicializálja a dokumentumot

Először is létre kell hoznia egy új dokumentumot, és be kell állítania a környezetet.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializáljon egy új dokumentumot
Document doc = new Document();
```

Ebben a lépésben egy új dokumentumot inicializálunk, amely az egyéni XML-adatainkat és az SDT-t fogja tárolni.

## 2. lépés: Adjon hozzá egyéni XML-részt

Ezután hozzáadunk egy egyéni XML részt a dokumentumhoz. Ez a rész tartalmazza majd az SDT-hez kötni kívánt XML adatokat.

```csharp
// Adjon hozzá egy egyéni XML részt a dokumentumhoz
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(Guid.NewGuid().ToString("B"), "<root><text>Hello, World!</text></root>");
```

Itt létrehozunk egy új egyéni XML részt egyedi azonosítóval, és hozzáadunk néhány minta XML adatot.

## 3. lépés: Strukturált dokumentumcímke (SDT) létrehozása

Az Egyéni XML rész hozzáadása után létrehozunk egy SDT-t az XML adatok megjelenítéséhez.

```csharp
//Strukturált dokumentumcímke (SDT) létrehozása
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Block);
doc.FirstSection.Body.AppendChild(sdt);
```

Létrehozunk egy PlainText típusú SDT-t, és hozzáfűzzük a dokumentumtörzs első részéhez.

## 4. lépés: Kösse az SDT-t az egyéni XML-részhez

Most az SDT-t az egyéni XML részhez kötjük egy XPath kifejezés segítségével.

```csharp
// Kösse az SDT-t az egyéni XML-részhez
sdt.XmlMapping.SetMapping(xmlPart, "/root[1]/text[1]", "");
```

 Ez a lépés leképezi az SDT-t a`<text>` elemen belül`<root>` Egyéni XML részünk csomópontja.

## 5. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumot a megadott könyvtárba.

```csharp
// Mentse el a dokumentumot
doc.Save(dataDir + "WorkingWithSdt.BindSDTtoCustomXmlPart.doc");
```

Ez a parancs elmenti a dokumentumot a kötött SDT-vel a kijelölt könyvtárba.

## Következtetés

Gratulálok! Sikeresen kötött egy SDT-t egy egyéni XML-részhez az Aspose.Words for .NET használatával. Ez a hatékony funkció lehetővé teszi dinamikus dokumentumok létrehozását, amelyek egyszerűen frissíthetők új adatokkal az XML-tartalom egyszerű módosításával. Akár jelentéseket készít, akár sablonokat hoz létre, vagy automatizálja a dokumentum-munkafolyamatokat, az Aspose.Words for .NET olyan eszközöket kínál, amelyekkel megkönnyítheti és hatékonyabbá teheti feladatait.

## GYIK

### Mi az a strukturált dokumentumcímke (SDT)?
strukturált dokumentumcímke (SDT) egy tartalomvezérlő elem a Word dokumentumokban, amellyel dinamikus adatok köthetők össze, így a dokumentumok interaktívak és adatvezéreltek.

### Köthetek több SDT-t különböző XML-részekhez egyetlen dokumentumban?
Igen, ugyanabban a dokumentumban több SDT-t is köthet különböző XML-részekhez, lehetővé téve összetett adatvezérelt sablonok létrehozását.

### Hogyan frissíthetem az XML-adatokat az egyéni XML-részben?
 Frissítheti az XML-adatokat a`CustomXmlPart` objektumot, és közvetlenül módosíthatja annak XML-tartalmát.

### Lehetséges az SDT-ket XML attribútumokhoz kötni elemek helyett?
Igen, az SDT-ket XML-attribútumokhoz kötheti a megfelelő XPath-kifejezés megadásával, amely megcélozza a kívánt attribútumot.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Az Aspose.Words for .NET webhelyről átfogó dokumentációt találhat a következő címen[Aspose.Words Dokumentáció](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
