---
"description": "Ismerje meg, hogyan hozhat létre ismétlődő szakaszt tartalmazó táblázatot egy Word-dokumentumban, amely CustomXmlPart elemhez van leképezve az Aspose.Words for .NET használatával."
"linktitle": "Egyéni XML-alkatrészhez rendelt ismétlődő szakasz táblázat létrehozása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Egyéni XML-alkatrészhez rendelt ismétlődő szakasz táblázat létrehozása"
"url": "/hu/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Egyéni XML-alkatrészhez rendelt ismétlődő szakasz táblázat létrehozása

## Bevezetés

Ebben az oktatóanyagban végigvezetjük egy ismétlődő szakaszt tartalmazó táblázat létrehozásának folyamatán, amely egy egyéni XML-részhez van leképezve az Aspose.Words for .NET használatával. Ez különösen hasznos strukturált adatokon alapuló dokumentumok dinamikus generálásához.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:
1. Az Aspose.Words for .NET könyvtár telepítve van. Letöltheti innen: [Aspose weboldal](https://releases.aspose.com/words/net/).
2. C# és XML alapismeretek.

## Névterek importálása

Győződjön meg róla, hogy a projektben szerepelnek a szükséges névterek:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## 1. lépés: A Document és a DocumentBuilder inicializálása

Először hozz létre egy új dokumentumot, és inicializáld a `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Egyéni XML-rész hozzáadása

Adjon hozzá egy egyéni XML részt a dokumentumhoz. Ez az XML tartalmazza azokat az adatokat, amelyeket a táblázatunkhoz szeretnénk rendelni:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## 3. lépés: A táblázat szerkezetének létrehozása

Ezután használja a `DocumentBuilder` a táblázat fejlécének létrehozásához:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## 4. lépés: Ismétlődő szakasz létrehozása

Hozz létre egy `StructuredDocumentTag` (SDT) az ismétlődő szakaszhoz, és megfeleltetjük az XML-adatoknak:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## 5. lépés: Ismétlődő szakaszelem létrehozása

Hozzon létre egy SDT-t az ismétlődő szakasz eleméhez, és adja hozzá az ismétlődő szakaszhoz:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## 6. lépés: XML adatok leképezése táblázatcellákra

Hozz létre SDT-ket a címhez és a szerzőhöz, képezd le őket az XML adatokhoz, és fűzd hozzá a sorhoz:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## 7. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Következtetés

A következő lépéseket követve sikeresen létrehozott egy táblázatot egy ismétlődő szakaszból álló táblázattal, amely egy egyéni XML-részhez van leképezve az Aspose.Words for .NET használatával. Ez lehetővé teszi a dinamikus tartalomgenerálást strukturált adatok alapján, így a dokumentumkészítés rugalmasabb és hatékonyabb.

## GYIK

### Mi az a StructuredDocumentTag (SDT)?
Az SDT, más néven tartalomvezérlő, egy dokumentumban található, határolt régió, amely strukturált adatok tárolására szolgál.

### Használhatok más adattípusokat az egyéni XML részben?
Igen, az egyéni XML-részt bármilyen adattípussal strukturálhatja, és ennek megfelelően leképezheti azokat.

### Hogyan adhatok hozzá további sorokat az ismétlődő szakaszhoz?
Az ismétlődő szakasz automatikusan replikálja a leképezett XML-elérési út minden elemének sorszerkezetét.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}