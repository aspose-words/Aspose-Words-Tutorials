---
title: Visa Dölj bokmärkt innehåll i Word-dokument
linktitle: Visa Dölj bokmärkt innehåll i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du visar och döljer bokmärkt innehåll i Word-dokument med Aspose.Words för .NET med denna detaljerade steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Visa Dölj bokmärkt innehåll i Word-dokument

## Introduktion

Är du redo att dyka in i dokumenthanteringens värld med Aspose.Words för .NET? Oavsett om du är en utvecklare som vill automatisera dokumentuppgifter eller bara någon som är nyfiken på att hantera Word-filer programmatiskt, är du på rätt plats. Idag ska vi utforska hur man visar och döljer bokmärkt innehåll i ett Word-dokument med Aspose.Words för .NET. Den här steg-för-steg-guiden gör dig till ett proffs på att kontrollera innehållssynlighet baserat på bokmärken. Låt oss komma igång!

## Förutsättningar

Innan vi hoppar in i det nitty-gritty, finns det några saker du behöver:

1. Visual Studio: Alla versioner som är kompatibla med .NET.
2.  Aspose.Words för .NET: Ladda ner det[här](https://releases.aspose.com/words/net/).
3. Grundläggande förståelse för C#: Om du kan skriva ett enkelt "Hello World"-program är du bra att gå.
4. Ett Word-dokument med bokmärken: Vi kommer att använda ett exempeldokument med bokmärken för den här handledningen.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta säkerställer att vi har alla verktyg vi behöver för vår uppgift.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Med dessa namnutrymmen på plats är vi alla redo att börja vår resa.

## Steg 1: Konfigurera ditt projekt

Okej, låt oss kicka igång genom att ställa in vårt projekt i Visual Studio.

### Skapa ett nytt projekt

Öppna Visual Studio och skapa ett nytt Console App-projekt (.NET Core). Döp det till något catchy, som "BookmarkVisibilityManager".

### Lägg till Aspose.Words för .NET

Du måste lägga till Aspose.Words för .NET till ditt projekt. Du kan göra detta via NuGet Package Manager.

1. Gå till Verktyg > NuGet Package Manager > Hantera NuGet Packages for Solution.
2. Sök efter "Aspose.Words".
3. Installera paketet.

Stor! Nu när vårt projekt är satt upp, låt oss gå vidare till att ladda vårt dokument.

## Steg 2: Ladda dokumentet

Vi måste ladda Word-dokumentet som innehåller bokmärkena. För den här handledningen använder vi ett exempeldokument med namnet "Bookmarks.docx".

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Detta kodavsnitt anger sökvägen till din dokumentkatalog och laddar dokumentet i`doc` objekt.

## Steg 3: Visa/dölj bokmärkt innehåll

Nu kommer den roliga delen – att visa eller dölja innehållet baserat på bokmärken. Vi skapar en metod som heter`ShowHideBookmarkedContent` att hantera detta.

Här är metoden som växlar synligheten för bokmärkt innehåll:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Uppdelning av metoden

-  Bokmärkshämtning:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` hämtar bokmärket.
- Nodgenomgång: Vi korsar noderna inom bokmärket.
-  Visibility Toggle: Om noden är en`Run` (en sammanhängande serie text), ställer vi in dess`Hidden` egendom.

## Steg 4: Tillämpa metoden

Med vår metod på plats, låt oss använda den för att visa eller dölja innehåll baserat på ett bokmärke.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Denna kodrad kommer att dölja innehållet i bokmärket som heter "MyBookmark1".

## Steg 5: Spara dokumentet

Slutligen, låt oss spara vårt modifierade dokument.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Detta sparar dokumentet med de ändringar vi har gjort.

## Slutsats

Och där har du det! Du har precis lärt dig hur du visar och döljer bokmärkt innehåll i ett Word-dokument med Aspose.Words för .NET. Det här kraftfulla verktyget gör dokumentmanipulering till en lek, oavsett om du automatiserar rapporter, skapar mallar eller bara pysslar med Word-filer. Glad kodning!

## FAQ's

### Kan jag växla mellan flera bokmärken samtidigt?
 Ja, du kan ringa`ShowHideBookmarkedContent` metod för varje bokmärke du vill växla.

### Påverkar dokumentets struktur att dölja innehåll?
Nej, att dölja innehåll påverkar bara dess synlighet. Innehållet finns kvar i dokumentet.

### Kan jag använda den här metoden för andra typer av innehåll?
Denna metod växlar specifikt textkörningar. För andra innehållstyper måste du ändra nodgenomgångslogiken.

### Är Aspose.Words för .NET gratis?
 Aspose.Words erbjuder en gratis provperiod[här](https://releases.aspose.com/) , men en fullständig licens krävs för produktionsanvändning. Du kan köpa den[här](https://purchase.aspose.com/buy).

### Hur kan jag få support om jag stöter på problem?
 Du kan få stöd från Aspose-communityt[här](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
