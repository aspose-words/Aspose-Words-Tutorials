---
title: Lägg till bokmärkt text i Word-dokument
linktitle: Lägg till bokmärkt text i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till bokmärkt text i ett Word-dokument med Aspose.Words för .NET med denna steg-för-steg-guide. Perfekt för utvecklare.
weight: 10
url: /sv/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till bokmärkt text i Word-dokument

## Introduktion

Hej där! Har du någonsin försökt lägga till text från ett bokmärkt avsnitt i ett Word-dokument och tyckt att det var svårt? Du har tur! Denna handledning kommer att leda dig genom processen med Aspose.Words för .NET. Vi delar upp det i enkla steg så att du enkelt kan följa med. Låt oss dyka in och lägga till den bokmärkta texten som ett proffs!

## Förutsättningar

Innan vi börjar, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Se till att du har det installerat. Om inte, kan du[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Vilken .NET-utvecklingsmiljö som helst som Visual Studio.
- Grundläggande kunskaper om C#: Att förstå grundläggande C#-programmeringskoncept kommer att hjälpa.
- Word-dokument med bokmärken: Ett Word-dokument med bokmärken som vi använder för att lägga till text från.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta kommer att säkerställa att vi har alla verktyg vi behöver till hands.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Låt oss dela upp exemplet i detaljerade steg.

## Steg 1: Ladda dokumentet och initiera variabler

Okej, låt oss börja med att ladda vårt Word-dokument och initiera de variabler vi behöver.

```csharp
// Ladda käll- och måldokumenten.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initiera dokumentimportören.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Hitta bokmärket i källdokumentet.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Steg 2: Identifiera start- och slutstyckena

Låt oss nu hitta styckena där bokmärket börjar och slutar. Detta är avgörande eftersom vi måste hantera texten inom dessa ramar.

```csharp
// Detta är stycket som innehåller början av bokmärket.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Detta är stycket som innehåller slutet av bokmärket.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Steg 3: Validera paragrafföräldrar

Vi måste se till att start- och slutstyckena har samma förälder. Detta är ett enkelt scenario för att hålla saker rakt på sak.

```csharp
// Begränsa oss till ett ganska enkelt scenario.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Steg 4: Identifiera noden som ska stoppas

Därefter måste vi bestämma noden där vi ska sluta kopiera text. Detta kommer att vara noden omedelbart efter slutstycket.

```csharp
// Vi vill kopiera alla stycken från startstycket till (och inklusive) slutstycket,
// därför är noden där vi stannar en efter slutstycket.
Node endNode = endPara.NextSibling;
```

## Steg 5: Lägg till bokmärkt text till destinationsdokument

Låt oss slutligen gå igenom noderna från startstycket till noden efter slutstycket och lägga till dem i måldokumentet.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Detta skapar en kopia av den aktuella noden och importerar den (gör den giltig) i sammanhanget
    // av destinationsdokumentet. Importering innebär att anpassa stilar och listidentifierare korrekt.
    Node newNode = importer.ImportNode(curNode, true);

    // Lägg till den importerade noden till måldokumentet.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Spara måldokumentet med den bifogade texten.
dstDoc.Save("appended_document.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt lagt till text från ett bokmärkt avsnitt i ett Word-dokument med Aspose.Words för .NET. Det här kraftfulla verktyget gör dokumentmanipulering till en lek, och nu har du ytterligare ett trick i rockärmen. Glad kodning!

## FAQ's

### Kan jag lägga till text från flera bokmärken på en gång?
Ja, du kan upprepa processen för varje bokmärke och lägga till texten därefter.

### Vad händer om start- och slutstyckena har olika föräldrar?
Det aktuella exemplet förutsätter att de har samma förälder. För olika föräldrar krävs en mer komplex hantering.

### Kan jag behålla den ursprungliga formateringen av den bifogade texten?
 Absolut! De`ImportFormatMode.KeepSourceFormatting` säkerställer att den ursprungliga formateringen bevaras.

### Är det möjligt att lägga till text till en specifik position i måldokumentet?
Ja, du kan lägga till texten på valfri position genom att navigera till önskad nod i måldokumentet.

### Vad händer om jag behöver lägga till text från ett bokmärke till ett nytt avsnitt?
Du kan skapa ett nytt avsnitt i måldokumentet och lägga till texten där.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
