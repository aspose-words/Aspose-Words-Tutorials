---
title: Kopiera bokmärkt text i Word-dokument
linktitle: Kopiera bokmärkt text i Word-dokument
second_title: Aspose.Words Document Processing API
description: Kopiera enkelt bokmärkt text mellan Word-dokument med Aspose.Words för .NET. Lär dig hur med denna steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kopiera bokmärkt text i Word-dokument

## Introduktion

Har du någonsin funnit dig själv behöva kopiera specifika avsnitt från ett Word-dokument till ett annat? Nåväl, du har tur! I den här handledningen går vi igenom hur du kopierar bokmärkt text från ett Word-dokument till ett annat med Aspose.Words för .NET. Oavsett om du bygger en dynamisk rapport eller automatiserar dokumentgenerering, kommer den här guiden att förenkla processen för dig.

## Förutsättningar

Innan vi dyker in, se till att du har följande:

-  Aspose.Words för .NET Library: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklingsmiljö.
- Grundläggande kunskaper i C#: Bekantskap med C#-programmering och .NET framework.

## Importera namnområden

För att börja, se till att du har de nödvändiga namnrymden importerade i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Steg 1: Ladda källdokumentet

Först och främst måste du ladda källdokumentet som innehåller den bokmärkta texten du vill kopiera.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Här,`dataDir` är sökvägen till din dokumentkatalog, och`Bookmarks.docx` är källdokumentet.

## Steg 2: Identifiera bokmärket

Identifiera sedan bokmärket du vill kopiera från källdokumentet.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Ersätta`"MyBookmark1"` med det faktiska namnet på ditt bokmärke.

## Steg 3: Skapa destinationsdokumentet

Skapa nu ett nytt dokument där den bokmärkta texten kommer att kopieras.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Steg 4: Importera bokmärkt innehåll

 För att säkerställa att stilarna och formateringen bevaras, använd`NodeImporter` för att importera det bokmärkta innehållet från källdokumentet till måldokumentet.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Steg 5: Definiera metoden AppendBookmarkedText

Här händer magin. Definiera en metod för att hantera kopieringen av den bokmärkta texten:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Steg 6: Spara destinationsdokumentet

Spara slutligen måldokumentet för att verifiera det kopierade innehållet.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Slutsats

Och det är det! Du har framgångsrikt kopierat bokmärkt text från ett Word-dokument till ett annat med Aspose.Words för .NET. Den här metoden är kraftfull för att automatisera dokumenthanteringsuppgifter, vilket gör ditt arbetsflöde mer effektivt och strömlinjeformat.

## FAQ's

### Kan jag kopiera flera bokmärken samtidigt?
Ja, du kan iterera genom flera bokmärken och använda samma metod för att kopiera vart och ett.

### Vad händer om bokmärket inte hittas?
 De`Range.Bookmarks` egendom kommer tillbaka`null`, så se till att du hanterar det här fallet för att undvika undantag.

### Kan jag behålla formateringen av det ursprungliga bokmärket?
 Absolut! Använder`ImportFormatMode.KeepSourceFormatting` säkerställer att den ursprungliga formateringen bevaras.

### Finns det en gräns för storleken på den bokmärkta texten?
Det finns ingen specifik gräns, men prestandan kan variera med extremt stora dokument.

### Kan jag kopiera text mellan olika Word-dokumentformat?
Ja, Aspose.Words stöder olika Word-format, och metoden fungerar över dessa format.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
