---
"description": "Lär dig hur du skapar en tabell med ett upprepande avsnitt mappat till en CustomXmlPart i ett Word-dokument med hjälp av Aspose.Words för .NET."
"linktitle": "Skapa tabellupprepande sektion mappad till anpassad XML-del"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Skapa tabellupprepande sektion mappad till anpassad XML-del"
"url": "/sv/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tabellupprepande sektion mappad till anpassad XML-del

## Introduktion

I den här handledningen går vi igenom processen att skapa en tabell med ett upprepande avsnitt som mappas till en anpassad XML-del med hjälp av Aspose.Words för .NET. Detta är särskilt användbart för att dynamiskt generera dokument baserade på strukturerad data.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:
1. Aspose.Words för .NET-biblioteket är installerat. Du kan ladda ner det från [Aspose webbplats](https://releases.aspose.com/words/net/).
2. Grundläggande förståelse för C# och XML.

## Importera namnrymder

Se till att inkludera nödvändiga namnrymder i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Steg 1: Initiera dokumentet och DocumentBuilder

Skapa först ett nytt dokument och initiera ett `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Lägg till anpassad XML-del

Lägg till en anpassad XML-del i dokumentet. Denna XML-fil innehåller de data vi vill mappa till vår tabell:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Steg 3: Skapa tabellstrukturen

Använd sedan `DocumentBuilder` för att skapa tabellrubriken:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Steg 4: Skapa upprepande avsnitt

Skapa en `StructuredDocumentTag` (SDT) för det upprepande avsnittet och mappa det till XML-data:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Steg 5: Skapa upprepande sektionsobjekt

Skapa en SDT för det upprepande avsnittsobjektet och lägg till det i det upprepande avsnittet:

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

Genom att följa dessa steg har du skapat en tabell med ett upprepande avsnitt mappat till en anpassad XML-del med hjälp av Aspose.Words för .NET. Detta möjliggör dynamisk innehållsgenerering baserat på strukturerad data, vilket gör dokumentskapandet mer flexibelt och kraftfullt.

## Vanliga frågor

### Vad är en StructuredDocumentTag (SDT)?
En SDT, även känd som en innehållskontroll, är ett begränsat område i ett dokument som används för att innehålla strukturerad data.

### Kan jag använda andra datatyper i den anpassade XML-delen?
Ja, du kan strukturera din anpassade XML-del med valfria datatyper och mappa dem därefter.

### Hur lägger jag till fler rader i det upprepande avsnittet?
Det upprepande avsnittet replikerar automatiskt radstrukturen för varje objekt i den mappade XML-sökvägen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}