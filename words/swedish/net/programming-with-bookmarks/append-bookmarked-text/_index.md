---
"description": "Lär dig hur du lägger till bokmärkt text i ett Word-dokument med Aspose.Words för .NET med den här steg-för-steg-guiden. Perfekt för utvecklare."
"linktitle": "Lägg till bokmärkt text i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lägg till bokmärkt text i Word-dokument"
"url": "/sv/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till bokmärkt text i Word-dokument

## Introduktion

Hej! Har du någonsin försökt lägga till text från ett bokmärkt avsnitt i ett Word-dokument och tyckt att det var knepigt? Då har du tur! Den här handledningen guidar dig genom processen med Aspose.Words för .NET. Vi delar upp det i enkla steg så att du enkelt kan följa med. Nu kör vi och lägger till den bokmärkta texten som ett proffs!

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Se till att du har det installerat. Om inte, kan du [ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Valfri .NET-utvecklingsmiljö som Visual Studio.
- Grundläggande kunskaper i C#: Att förstå grundläggande C#-programmeringskoncept är till hjälp.
- Word-dokument med bokmärken: Ett Word-dokument med bokmärken som vi använder för att lägga till text från.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta säkerställer att vi har alla verktyg vi behöver nära till hands.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Låt oss dela upp exemplet i detaljerade steg.

## Steg 1: Ladda dokumentet och initiera variabler

Okej, låt oss börja med att ladda vårt Word-dokument och initiera de variabler vi behöver.

```csharp
// Ladda käll- och destinationsdokumenten.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initiera dokumentimportören.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Hitta bokmärket i källdokumentet.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Steg 2: Identifiera start- och slutstycken

Nu ska vi lokalisera styckena där bokmärket börjar och slutar. Detta är avgörande eftersom vi måste hantera texten inom dessa gränser.

```csharp
// Detta är stycket som innehåller början av bokmärket.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Detta är stycket som innehåller slutet av bokmärket.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Steg 3: Validera styckeöverordnade

Vi måste se till att början och slutet av styckena har samma förälder. Detta är ett enkelt scenario för att hålla det enkelt.

```csharp
// Begränsar oss till ett relativt enkelt scenario.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Steg 4: Identifiera noden som ska stoppas

Sedan måste vi bestämma noden där vi ska sluta kopiera text. Detta blir noden omedelbart efter det avslutande stycket.

```csharp
// Vi vill kopiera alla stycken från början till (och inklusive) slutet.
// därför är noden där vi stannar ett efter slutstycket.
Node endNode = endPara.NextSibling;
```

## Steg 5: Lägg till bokmärkt text i måldokument

Slutligen, låt oss loopa igenom noderna från startstycket till noden efter slutstycket och lägga till dem i destinationsdokumentet.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Detta skapar en kopia av den aktuella noden och importerar den (gör den giltig) i kontexten.
    // av destinationsdokumentet. Import innebär att justera format och listidentifierare korrekt.
    Node newNode = importer.ImportNode(curNode, true);

    // Lägg till den importerade noden i destinationsdokumentet.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Spara måldokumentet med den bifogade texten.
dstDoc.Save("appended_document.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt lagt till text från ett bokmärkt avsnitt i ett Word-dokument med hjälp av Aspose.Words för .NET. Det här kraftfulla verktyget gör dokumenthantering till en barnlek, och nu har du ytterligare ett knep i rockärmen. Lycka till med kodningen!

## Vanliga frågor

### Kan jag lägga till text från flera bokmärken samtidigt?
Ja, du kan upprepa processen för varje bokmärke och lägga till texten därefter.

### Vad händer om början och slutet av styckena har olika överordnade stycken?
Det aktuella exemplet förutsätter att de har samma förälder. För olika föräldrar krävs en mer komplex hantering.

### Kan jag behålla den ursprungliga formateringen av den bifogade texten?
Absolut! Den `ImportFormatMode.KeepSourceFormatting` säkerställer att den ursprungliga formateringen bevaras.

### Är det möjligt att lägga till text på en specifik position i destinationsdokumentet?
Ja, du kan lägga till texten på valfri position genom att navigera till önskad nod i måldokumentet.

### Vad händer om jag behöver lägga till text från ett bokmärke i ett nytt avsnitt?
Du kan skapa ett nytt avsnitt i måldokumentet och lägga till texten där.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}