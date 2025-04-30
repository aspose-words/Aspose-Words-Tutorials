---
"description": "Ismerje meg, hogyan köthet dinamikusan XML-adatokat strukturált dokumentumcímkékhez Wordben az Aspose.Words for .NET használatával. Kövesse lépésről lépésre szóló útmutatónkat."
"linktitle": "Strukturált dokumentum címketartomány kezdete XML-megfeleltetés"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Strukturált dokumentum címketartomány kezdete XML-megfeleltetés"
"url": "/hu/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Strukturált dokumentum címketartomány kezdete XML-megfeleltetés

## Bevezetés

Szerettél volna dinamikusan XML adatokat beszúrni egy Word dokumentumba? Nos, szerencséd van! Az Aspose.Words for .NET gyerekjátékká teszi ezt a feladatot. Ebben az oktatóanyagban mélyrehatóan elmerülünk a strukturált dokumentumcímke-tartomány kezdete XML leképezésben. Ez a funkció lehetővé teszi, hogy egyéni XML részeket köts tartalomvezérlőkhöz, biztosítva, hogy a dokumentum tartalma zökkenőmentesen frissüljön az XML adatokkal. Készen állsz arra, hogy dokumentumaidat dinamikus remekművekké alakítsd.

## Előfeltételek

Mielőtt belevágnánk a kódolásba, győződjünk meg róla, hogy minden szükséges dolog megvan:

1. Aspose.Words .NET könyvtárhoz: Győződjön meg róla, hogy a legújabb verzióval rendelkezik. Letöltheti [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármilyen más C#-ot támogató IDE.
3. C# alapismeretek: A C# programozásban való jártasság elengedhetetlen.
4. Word-dokumentum: Egy minta Word-dokumentum, amellyel dolgozhatsz.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy hozzáférjünk az Aspose.Words for .NET összes szükséges osztályához és metódusához.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Minden projektnek kell egy alap, igaz? Itt beállítjuk a dokumentumkönyvtár elérési útját.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a Word dokumentumot

Ezután betöltjük a Word dokumentumot. Ez az a dokumentum, amelybe beillesztjük az XML adatainkat.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## 3. lépés: Egyéni XML-rész hozzáadása

Létre kell hoznunk egy XML részt, amely tartalmazza a beszúrni kívánt adatokat, és hozzá kell adnunk a dokumentum CustomXmlPart gyűjteményéhez. Ez az egyéni XML rész fog adatforrásként szolgálni a strukturált dokumentumcímkéinkhez.

### XML rész létrehozása

Először generáljon egy egyedi azonosítót az XML részhez, és definiálja annak tartalmát.

```csharp
// Hozz létre egy adatokat tartalmazó XML részt, és add hozzá a dokumentum CustomXmlPart gyűjteményéhez.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Az XML rész tartalmának ellenőrzése

Annak érdekében, hogy az XML rész helyesen legyen hozzáadva, kinyomtatjuk a tartalmát.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## 4. lépés: Strukturált dokumentumcímke létrehozása

A strukturált dokumentumcímke (SDT) egy tartalomvezérlő, amely XML-részhez tud kötődni. Itt létrehozunk egy SDT-t, amely megjeleníti az egyéni XML-részünk tartalmát.

Először is, keresse meg az SDT tartomány kezdetét a dokumentumban.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## 5. lépés: XML-megfeleltetés beállítása az SDT-hez

Most itt az ideje, hogy az XML részünket az SDT-hez kössük. Egy XML megfeleltetés beállításával meghatározzuk, hogy az XML adatok melyik része jelenjen meg az SDT-ben.

Az XPath az XML-részben megjeleníteni kívánt konkrét elemre mutat. Itt a másodikra mutatunk. `<text>` elem a `<root>` elem.

```csharp
// Állítson be egy megfeleltetést a StructuredDocumentTag-hez
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## 6. lépés: A dokumentum mentése

Végül mentse el a dokumentumot, hogy működés közben lássa a változtatásokat. A Word-dokumentumban található SDT mostantól megjeleníti a megadott XML-tartalmat.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Következtetés

És íme! Sikeresen leképeztél egy XML részt egy strukturált dokumentumcímkéhez egy Word dokumentumban az Aspose.Words for .NET segítségével. Ez a hatékony funkció lehetővé teszi, hogy könnyedén hozz létre dinamikus és adatvezérelt dokumentumokat. Akár jelentéseket, számlákat vagy bármilyen más dokumentumtípust generálsz, az XML leképezés jelentősen leegyszerűsítheti a munkafolyamatot.

## GYIK

### Mi az a strukturált dokumentumcímke a Wordben?
A strukturált dokumentumcímkék, más néven tartalomvezérlők, a Word-dokumentumokban található meghatározott típusú tartalmak tárolói. Használhatók adatok kötésére, szerkesztés korlátozására, vagy a felhasználók dokumentumkészítésben való eligazítására.

### Hogyan frissíthetem dinamikusan az XML rész tartalmát?
Az XML rész tartalmát a következő módosításával frissítheti: `xmlPartContent` karakterláncot, mielőtt hozzáadná a dokumentumhoz. Egyszerűen frissítse a karakterláncot az új adatokkal, és adja hozzá a `CustomXmlParts` gyűjtemény.

### Köthetek több XML részt különböző SDT-khez ugyanabban a dokumentumban?
Igen, több XML-részt is köthetsz különböző SDT-khez ugyanabban a dokumentumban. Minden SDT-nek lehet saját egyedi XML-része és XPath-megfeleltetése.

### Lehetséges összetett XML struktúrákat SDT-kre képezni?
Teljesen! Komplex XML struktúrákat leképezhet SDT-kké részletes XPath kifejezések használatával, amelyek pontosan a kívánt elemekre mutatnak az XML részben.

### Hogyan távolíthatok el egy XML részt egy dokumentumból?
XML részt a következő meghívásával távolíthatsz el: `Remove` módszer a `CustomXmlParts` gyűjtés, átadva a `xmlPartId` az eltávolítani kívánt XML részből.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}