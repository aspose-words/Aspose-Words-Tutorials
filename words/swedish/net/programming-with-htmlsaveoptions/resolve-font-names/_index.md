---
"description": "Lär dig hur du tolkar teckensnittsnamn i Word-dokument när du konverterar till HTML med Aspose.Words för .NET. Steg-för-steg-guide med detaljerade förklaringar."
"linktitle": "Lös upp typsnittsnamn"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lös upp typsnittsnamn"
"url": "/sv/net/programming-with-htmlsaveoptions/resolve-font-names/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lös upp typsnittsnamn

## Introduktion

Hej där, kodare! Om du någonsin har brottats med teckensnittsproblem när du sparar Word-dokument som HTML, är du inte ensam. Teckensnitt kan vara knepiga, men oroa dig inte; jag hjälper dig. Idag dyker vi ner i hur du löser teckensnittsnamn i dina Word-dokument med Aspose.Words för .NET. Den här guiden guidar dig genom processen steg för steg och säkerställer att dina teckensnitt ser precis rätt ut i HTML-format.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET: Om du inte redan har gjort det kan du ladda ner det [här](https://releases.aspose.com/words/net/).
2. Giltig licens: Du kan köpa en licens [här](https://purchase.aspose.com/buy) eller skaffa ett tillfälligt körkort [här](https://purchase.aspose.com/temporary-license/).
3. Grundläggande kunskaper i C# och .NET: Den här handledningen förutsätter att du är bekväm med grundläggande programmeringskoncept i C#.
4. Visual Studio: Alla versioner som stöder .NET Framework.

Nu när vi har våra förutsättningar sorterade, låt oss hoppa in i handlingen!

## Importera namnrymder

Innan vi börjar koda, se till att du har importerat de nödvändiga namnrymderna till ditt projekt. Detta är avgörande för att komma åt Aspose.Words-funktioner.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera dokumentkatalogen

Först och främst, låt oss ställa in sökvägen till din dokumentkatalog. Det är här ditt Word-dokument finns och där du sparar dina resultat.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Förklaring:
Här, `dataDir` innehåller sökvägen till din dokumentkatalog. Ersätt `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen på ditt system.

## Steg 2: Ladda Word-dokumentet

Nästa steg är att ladda Word-dokumentet som vi vill bearbeta. Dokumentet ska innehålla de teckensnitt du vill använda.

```csharp
Document doc = new Document(dataDir + "Missing font.docx");
```

Förklaring:
Vi skapar en `Document` objektet och ladda Word-dokumentet med namnet "Saknad font.docx" från vår `dataDir`.

## Steg 3: Konfigurera HTML-sparalternativ

Nu ska vi konfigurera alternativen för att spara dokumentet som HTML. Här ser vi till att teckensnittsnamnen tolkas korrekt.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

Förklaring:
Vi skapar en instans av `HtmlSaveOptions` med `SaveFormat.Html`Den `PrettyFormat` alternativet gör HTML-utdata mer läsbar, och `ResolveFontNames` säkerställer att teckensnittsnamn är lösta.

## Steg 4: Spara dokumentet som HTML

Slutligen sparar vi dokumentet som en HTML-fil med hjälp av de konfigurerade sparalternativen.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
```

Förklaring:
Vi kallar `Save` metod på `Document` objektet, och anger sökvägen för utdata och de alternativ för sparning som vi konfigurerat. Detta genererar en HTML-fil med teckensnittsnamnen upplösta.

## Slutsats

Och där har du det! Genom att följa dessa steg har du lyckats lösa typsnittsnamn när du konverterar ett Word-dokument till HTML med Aspose.Words för .NET. Detta säkerställer inte bara att dina typsnitt visas korrekt utan gör också att din HTML-utskrift ser elegant och professionell ut. Lycka till med kodningen!

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt.

### Hur installerar jag Aspose.Words för .NET?
Du kan ladda ner Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/)Följ installationsanvisningarna i dokumentationen.

### Kan jag använda Aspose.Words för .NET utan licens?
Ja, men det kommer att ha vissa begränsningar. För full funktionalitet kan du köpa en licens [här](https://purchase.aspose.com/buy) eller skaffa ett tillfälligt körkort [här](https://purchase.aspose.com/temporary-license/).

### Varför visas inte mina teckensnitt korrekt i HTML?
Detta kan hända om teckensnitten inte tolkas korrekt under konverteringen. `ResolveFontNames = true` i `HtmlSaveOptions` kan hjälpa till att åtgärda det här problemet.

### Var kan jag få support för Aspose.Words för .NET?
Du kan få stöd från [Aspose.Words supportforum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}