---
title: Skapa tabellupprepande avsnitt mappas till anpassad XML-del
linktitle: Skapa tabellupprepande avsnitt mappas till anpassad XML-del
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar en tabell med ett upprepande avsnitt mappat till en CustomXmlPart i ett Word-dokument med Aspose.Words för .NET.
weight: 10
url: /sv/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tabellupprepande avsnitt mappas till anpassad XML-del

## Introduktion

I den här handledningen går vi igenom processen att skapa en tabell med ett upprepande avsnitt som är mappat till en anpassad XML-del med Aspose.Words för .NET. Detta är särskilt användbart för att dynamiskt generera dokument baserat på strukturerad data.

## Förutsättningar

Innan vi börjar, se till att du har följande:
1.  Aspose.Words för .NET-biblioteket installerat. Du kan ladda ner den från[Aspose hemsida](https://releases.aspose.com/words/net/).
2. En grundläggande förståelse för C# och XML.

## Importera namnområden

Se till att inkludera nödvändiga namnutrymmen i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Steg 1: Initiera Document and DocumentBuilder

 Skapa först ett nytt dokument och initiera ett`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Lägg till anpassad XML-del

Lägg till en anpassad XML-del till dokumentet. Denna XML innehåller de data vi vill mappa till vår tabell:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Steg 3: Skapa tabellstrukturen

 Använd sedan`DocumentBuilder` för att skapa tabellhuvudet:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Steg 4: Skapa Repeterande avsnitt

 Skapa en`StructuredDocumentTag` (SDT) för det upprepande avsnittet och mappa det till XML-data:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Steg 5: Skapa ett återkommande avsnitt

Skapa en SDT för det upprepade avsnittet och lägg till det i det upprepade avsnittet:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Steg 6: Mappa XML-data till tabellceller

Skapa SDT:er för titeln och författaren, mappa dem till XML-data och lägg till dem på raden:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Steg 7: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Slutsats

Genom att följa dessa steg har du framgångsrikt skapat en tabell med ett upprepande avsnitt mappat till en anpassad XML-del med Aspose.Words för .NET. Detta möjliggör dynamisk innehållsgenerering baserat på strukturerad data, vilket gör dokumentskapandet mer flexibelt och kraftfullt.

## FAQ's

### Vad är en StructuredDocumentTag (SDT)?
En SDT, även känd som en innehållskontroll, är en avgränsad region i ett dokument som används för att innehålla strukturerad data.

### Kan jag använda andra datatyper i den anpassade XML-delen?
Ja, du kan strukturera din anpassade XML-del med alla datatyper och mappa dem därefter.

### Hur lägger jag till fler rader i det upprepade avsnittet?
Det upprepande avsnittet replikerar automatiskt radstrukturen för varje objekt i den mappade XML-sökvägen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
