---
title: Egyéni Xml-részhez leképezve táblázat ismétlődő szakasz létrehozása
linktitle: Egyéni Xml-részhez leképezve táblázat ismétlődő szakasz létrehozása
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan hozhat létre egy ismétlődő szakaszt egy CustomXmlPart-hoz leképezve egy táblázatot egy Word-dokumentumban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Egyéni Xml-részhez leképezve táblázat ismétlődő szakasz létrehozása

## Bevezetés

Ebben az oktatóanyagban egy olyan ismétlődő szakaszt tartalmazó táblázat létrehozásának folyamatát mutatjuk be, amely egy egyéni XML-részhez van leképezve az Aspose.Words for .NET használatával. Ez különösen hasznos a strukturált adatokon alapuló dokumentumok dinamikus generálásához.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1.  Aspose.Words for .NET könyvtár telepítve. Letöltheti a[Aspose honlapja](https://releases.aspose.com/words/net/).
2. A C# és XML alapvető ismerete.

## Névterek importálása

Ügyeljen arra, hogy a szükséges névtereket tartalmazza a projektben:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuilder-t

 Először hozzon létre egy új dokumentumot, és inicializálja a`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Egyéni XML-alkatrész hozzáadása

Adjon hozzá egy egyéni XML részt a dokumentumhoz. Ez az XML tartalmazza azokat az adatokat, amelyeket le akarunk képezni a táblánkra:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## 3. lépés: A táblázatszerkezet létrehozása

 Ezután használja a`DocumentBuilder` a táblázat fejlécének létrehozásához:

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

 Hozzon létre a`StructuredDocumentTag` (SDT) az ismétlődő szakaszhoz, és leképezi az XML adatokra:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## 5. lépés: Ismétlődő szakaszelem létrehozása

Hozzon létre egy SDT-t az ismétlődő szakaszelemhez, és adja hozzá az ismétlődő szakaszhoz:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## 6. lépés: XML adatok leképezése táblázatcellákra

Hozzon létre SDT-ket a címhez és a szerzőhöz, rendelje hozzá őket az XML-adatokhoz, és fűzze hozzá a sorhoz:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## 7. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Következtetés

Az alábbi lépések végrehajtásával sikeresen létrehozott egy táblát, amely ismétlődő szakaszt tartalmaz egy egyéni XML-részhez az Aspose.Words for .NET használatával. Ez lehetővé teszi a strukturált adatokon alapuló dinamikus tartalomgenerálást, rugalmasabbá és hatékonyabbá téve a dokumentumkészítést.

## GYIK

### Mi az a StructuredDocumentTag (SDT)?
Az SDT, más néven tartalomvezérlő, egy korlátozott terület a dokumentumban, amely strukturált adatok tárolására szolgál.

### Használhatok más adattípusokat az egyéni XML részben?
Igen, egyéni XML-részét bármilyen adattípussal strukturálhatja, és ennek megfelelően leképezheti őket.

### Hogyan adhatok további sorokat az ismétlődő szakaszhoz?
Az ismétlődő szakasz automatikusan megismétli a sorszerkezetet a leképezett XML-útvonal minden eleméhez.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
