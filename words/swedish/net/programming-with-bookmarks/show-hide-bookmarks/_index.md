---
title: Visa Göm bokmärken i Word-dokument
linktitle: Visa Göm bokmärken i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du dynamiskt visar eller döljer bokmärken i ett Word-dokument med Aspose.Words för .NET med vår steg-för-steg-guide. Perfekt för utvecklare.
weight: 10
url: /sv/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Visa Göm bokmärken i Word-dokument

## Introduktion

Har du någonsin sett att du behöver dölja eller visa vissa delar av ditt Word-dokument dynamiskt? Nåväl, du har tur! Med Aspose.Words för .NET kan du enkelt hantera synligheten av bokmärkt innehåll i dina dokument. Denna handledning kommer att leda dig genom processen att visa och dölja bokmärken i ett Word-dokument med Aspose.Words för .NET. Vi kommer att dela upp koden steg för steg, så oavsett om du är en erfaren utvecklare eller nybörjare, kommer du att tycka att den här guiden är lätt att följa.

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att du har allt du behöver:

1.  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Om inte kan du ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering kommer att vara fördelaktigt.
4. Ett Word-dokument: Ett exempel på Word-dokument med bokmärken.

## Importera namnområden

Innan du börjar med koden måste du importera de nödvändiga namnrymden. Lägg till följande i början av din C#-fil:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Steg 1: Ladda ditt dokument

Först och främst måste du ladda Word-dokumentet som innehåller bokmärkena. Så här kan du göra det:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Förklaring

- dataDir: Detta är katalogsökvägen där ditt Word-dokument finns.
-  Dokumentdokument: Detta initierar en ny instans av`Document` klass med din angivna fil.

## Steg 2: Visa eller dölj bokmärkt innehåll

Därefter kommer vi att definiera en metod för att visa eller dölja det bokmärkta innehållet. Här är hela metoden:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "sant" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Förklaring

- Bokmärke bm: Hämtar bokmärket från dokumentet.
- DocumentBuilder Builder: Hjälper till att navigera och ändra dokumentet.
- Fältfält: Infogar ett OM-fält för att kontrollera bokmärkets skick.
- Nod currentNode: Går igenom noderna för att hitta fältets början och slut.

## Steg 3: Kör funktionen Visa/Göm

 Nu måste du ringa`ShowHideBookmarkedContent` metod, skicka dokumentet, bokmärkets namn och synlighetsflaggan:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Förklaring

- doc: Ditt dokumentobjekt.
- "MyBookmark1": Namnet på bokmärket du vill visa/dölja.
- false: Synlighetsflaggan (sant för att visa, falskt för att dölja).

## Steg 4: Spara ditt dokument

Spara slutligen det ändrade dokumentet:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Förklaring

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Sökvägen och namnet på det nya dokumentet där ändringarna kommer att sparas.

## Slutsats

Och där har du det! Du har framgångsrikt lärt dig hur du visar och döljer bokmärken i ett Word-dokument med Aspose.Words för .NET. Denna teknik kan vara otroligt användbar för att dynamiskt generera dokument med villkorligt innehåll.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt.

### Hur får jag Aspose.Words för .NET?
 Du kan ladda ner Aspose.Words för .NET från[här](https://releases.aspose.com/words/net/). En gratis provperiod är också tillgänglig.

### Kan jag använda den här metoden för andra typer av bokmärken?
Ja, den här metoden kan anpassas för att hantera synligheten för alla bokmärken i ditt Word-dokument.

### Vad händer om mitt dokument inte innehåller det angivna bokmärket?
Om bokmärket inte finns kommer metoden att ge ett fel. Se till att bokmärket finns innan du försöker visa/dölja det.

### Hur kan jag få support om jag stöter på problem?
 Du kan få stöd från Aspose-communityt[här](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
