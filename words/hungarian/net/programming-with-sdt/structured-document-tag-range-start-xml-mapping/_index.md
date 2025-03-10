---
title: Strukturált dokumentumcímke-tartomány Indítsa el az Xml-leképezést
linktitle: Strukturált dokumentumcímke-tartomány Indítsa el az Xml-leképezést
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan köthet dinamikusan XML-adatokat a Word strukturált dokumentumcímkéihez az Aspose.Words for .NET használatával. Kövesse lépésenkénti útmutatónkat.
weight: 10
url: /hu/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Strukturált dokumentumcímke-tartomány Indítsa el az Xml-leképezést

## Bevezetés

Szeretett volna XML adatokat dinamikusan beszúrni egy Word dokumentumba? Nos, szerencséd van! Az Aspose.Words for .NET segítségével ez a feladat gyerekjáték. Ebben az oktatóanyagban a strukturált dokumentumcímke-tartomány kezdeti XML-leképezésének mélyére merülünk. Ezzel a funkcióval egyéni XML-részeket köthet a tartalomvezérlőkhöz, így biztosítva, hogy a dokumentumtartalom zökkenőmentesen frissüljön az XML-adatokkal. Készen áll arra, hogy dokumentumait dinamikus remekművekké alakítsa.

## Előfeltételek

Mielőtt belevágnánk a kódolási részbe, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:

1.  Aspose.Words for .NET Library: Győződjön meg arról, hogy a legújabb verzióval rendelkezik. Letöltheti[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Visual Studio vagy bármely más C#-t támogató IDE.
3. C# alapismeretek: A C# programozás ismerete elengedhetetlen.
4. Word-dokumentum: minta Word-dokumentum, amellyel dolgozni.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy hozzáférhessünk az Aspose.Words for .NET összes szükséges osztályához és metódusához.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Minden projekthez kell egy alap, nem? Itt beállítjuk a dokumentumkönyvtár elérési útját.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a Word-dokumentumot

Ezután betöltjük a Word dokumentumot. Ez az a dokumentum, amelybe beillesztjük XML-adatainkat.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## 3. lépés: Egyéni XML-alkatrész hozzáadása

Létre kell hoznunk egy XML részt, amely tartalmazza a beszúrni kívánt adatokat, és hozzáadnunk kell a dokumentum CustomXmlPart gyűjteményéhez. Ez az egyéni XML rész szolgál majd adatforrásként strukturált dokumentumcímkéinkhez.

### XML rész létrehozása

Először hozzon létre egy egyedi azonosítót az XML részhez, és határozza meg a tartalmát.

```csharp
// Hozzon létre egy XML részt, amely adatokat tartalmaz, és adja hozzá a dokumentum CustomXmlPart gyűjteményéhez.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Ellenőrizze az XML-rész tartalmát

Az XML-rész helyes hozzáadásának biztosítása érdekében kinyomtatjuk a tartalmát.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## 4. lépés: Strukturált dokumentumcímke létrehozása

Structured Document Tag (SDT) egy tartalomvezérlő, amely XML-részhez tud kapcsolódni. Itt létrehozunk egy SDT-t, amely megjeleníti az egyéni XML-részünk tartalmát.

Először keresse meg az SDT tartomány kezdetét a dokumentumban.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## 5. lépés: Állítsa be az XML-leképezést az SDT-hez

Most itt az ideje, hogy az XML-részünket az SDT-hez kötjük. Az XML-leképezés beállításával megadjuk, hogy az XML adatok melyik része jelenjen meg az SDT-ben.

 Az XPath az XML-rész adott elemére mutat, amelyet meg akarunk jeleníteni. Itt a másodikra mutatunk`<text>` elemen belül`<root>` elem.

```csharp
// Állítson be hozzárendelést a StructuredDocumentTag-hez
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## 6. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot, hogy megtekinthesse a változásokat. A Word dokumentumban lévő SDT most megjeleníti a megadott XML-tartalmat.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Következtetés

És megvan! Sikeresen leképezett egy XML-részt egy Word-dokumentum strukturált dokumentumcímkéjére az Aspose.Words for .NET használatával. Ezzel a hatékony funkcióval könnyedén hozhat létre dinamikus és adatvezérelt dokumentumokat. Akár jelentéseket, számlákat vagy bármilyen más dokumentumtípust készít, az XML-leképezés jelentősen leegyszerűsítheti a munkafolyamatot.

## GYIK

### Mi az a strukturált dokumentumcímke a Wordben?
A strukturált dokumentumcímkék, más néven tartalomvezérlők, a Word-dokumentumok meghatározott típusú tartalomtárolói. Használhatók adatok kötésére, szerkesztés korlátozására vagy a felhasználók útmutatására a dokumentumok létrehozásában.

### Hogyan frissíthetem dinamikusan az XML-rész tartalmát?
 Az XML-rész tartalmát a módosításával frissítheti`xmlPartContent` karakterláncot, mielőtt hozzáadná a dokumentumhoz. Egyszerűen frissítse a karakterláncot az új adatokkal, és adja hozzá a`CustomXmlParts` gyűjtemény.

### Köthetek több XML-részt különböző SDT-khez ugyanabban a dokumentumban?
Igen, ugyanabban a dokumentumban több XML-részt is köthet különböző SDT-khez. Minden SDT-nek lehet saját egyedi XML része és XPath leképezése.

### Leképezhető-e bonyolult XML-struktúrák SDT-kre?
Teljesen! Összetett XML-struktúrákat SDT-kre képezhet le részletes XPath-kifejezések használatával, amelyek pontosan mutatnak az XML-rész kívánt elemeire.

### Hogyan távolíthatok el egy XML részt a dokumentumból?
 Az XML-részt a`Remove` módszer a`CustomXmlParts` gyűjtemény, átadva a`xmlPartId` az eltávolítani kívánt XML-részről.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
