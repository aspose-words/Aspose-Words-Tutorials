---
"description": "Lär dig hur du visar och döljer bokmärkt innehåll i Word-dokument med Aspose.Words för .NET med den här detaljerade steg-för-steg-guiden."
"linktitle": "Visa Dölj Bokmärkt Innehåll I Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Visa Dölj Bokmärkt Innehåll I Word-dokument"
"url": "/sv/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Visa Dölj Bokmärkt Innehåll I Word-dokument

## Introduktion

Redo att dyka in i dokumenthanteringens värld med Aspose.Words för .NET? Oavsett om du är en utvecklare som vill automatisera dokumentuppgifter eller bara är nyfiken på att hantera Word-filer programmatiskt, har du kommit rätt. Idag ska vi utforska hur man visar och döljer bokmärkt innehåll i ett Word-dokument med hjälp av Aspose.Words för .NET. Den här steg-för-steg-guiden gör dig till ett proffs på att kontrollera innehållssynlighet baserat på bokmärken. Nu sätter vi igång!

## Förkunskapskrav

Innan vi går in på det allra viktigaste finns det några saker du behöver:

1. Visual Studio: Alla versioner som är kompatibla med .NET.
2. Aspose.Words för .NET: Ladda ner det [här](https://releases.aspose.com/words/net/).
3. Grundläggande förståelse för C#: Om du kan skriva ett enkelt "Hello World"-program är du redo att köra.
4. Ett Word-dokument med bokmärken: Vi kommer att använda ett exempeldokument med bokmärken för den här handledningen.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta säkerställer att vi har alla verktyg vi behöver för vår uppgift.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Med dessa namnrymder på plats är vi redo att påbörja vår resa.

## Steg 1: Konfigurera ditt projekt

Okej, låt oss sätta igång genom att konfigurera vårt projekt i Visual Studio.

### Skapa ett nytt projekt

Öppna Visual Studio och skapa ett nytt Console App-projekt (.NET Core). Ge det något iögonfallande namn, som "BookmarkVisibilityManager".

### Lägg till Aspose.Words för .NET

Du måste lägga till Aspose.Words för .NET i ditt projekt. Du kan göra detta via NuGet Package Manager.

1. Gå till Verktyg > NuGet-pakethanterare > Hantera NuGet-paket för lösningen.
2. Sök efter "Aspose.Words".
3. Installera paketet.

Toppen! Nu när vårt projekt är klart, låt oss gå vidare till att ladda vårt dokument.

## Steg 2: Ladda dokumentet

Vi behöver ladda Word-dokumentet som innehåller bokmärkena. I den här handledningen använder vi ett exempeldokument med namnet "Bookmarks.docx".

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Det här kodavsnittet anger sökvägen till din dokumentkatalog och laddar dokumentet i `doc` objekt.

## Steg 3: Visa/dölj bokmärkt innehåll

Nu kommer den roliga delen – att visa eller dölja innehållet baserat på bokmärken. Vi skapar en metod som heter `ShowHideBookmarkedContent` att hantera detta.

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

### Fördelning av metoden

- Hämtning av bokmärken: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` hämtar bokmärket.
- Nodtraversering: Vi passerar noderna inom bokmärket.
- Synlighetsväxling: Om noden är en `Run` (en sammanhängande textsekvens), vi ställer in dess `Hidden` egendom.

## Steg 4: Tillämpa metoden

Med vår metod på plats, låt oss tillämpa den för att visa eller dölja innehåll baserat på ett bokmärke.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Den här kodraden kommer att dölja innehållet i bokmärket med namnet "MittBokmärke1".

## Steg 5: Spara dokumentet

Slutligen, låt oss spara vårt modifierade dokument.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Detta sparar dokumentet med de ändringar vi har gjort.

## Slutsats

Och där har du det! Du har precis lärt dig hur du visar och döljer bokmärkt innehåll i ett Word-dokument med hjälp av Aspose.Words för .NET. Det här kraftfulla verktyget gör dokumenthantering till en barnlek, oavsett om du automatiserar rapporter, skapar mallar eller bara experimenterar med Word-filer. Lycka till med kodningen!

## Vanliga frågor

### Kan jag växla mellan flera bokmärken samtidigt?
Ja, du kan ringa `ShowHideBookmarkedContent` metod för varje bokmärke du vill växla.

### Påverkar döljning av innehåll dokumentets struktur?
Nej, att dölja innehåll påverkar bara dess synlighet. Innehållet finns kvar i dokumentet.

### Kan jag använda den här metoden för andra typer av innehåll?
Den här metoden växlar specifikt mellan textkörningar. För andra innehållstyper måste du ändra nodens genomgångslogik.

### Är Aspose.Words för .NET gratis?
Aspose.Words erbjuder en gratis provperiod [här](https://releases.aspose.com/), men en fullständig licens krävs för produktionsanvändning. Du kan köpa den [här](https://purchase.aspose.com/buy).

### Hur kan jag få support om jag stöter på problem?
Du kan få stöd från Aspose-communityn [här](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}