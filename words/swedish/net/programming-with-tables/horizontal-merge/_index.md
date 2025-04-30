---
"description": "Lär dig hur du horisontellt sammanfogar celler i ett Word-dokument med Aspose.Words för .NET med den här detaljerade steg-för-steg-handledningen."
"linktitle": "Horisontell sammanslagning"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Horisontell sammanslagning"
"url": "/sv/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horisontell sammanslagning

## Introduktion

Hej där! Redo att dyka in i Aspose.Words värld för .NET? Idag ska vi ta itu med en superanvändbar funktion: horisontell sammanfogning i tabeller. Det här kanske låter lite tekniskt, men oroa dig inte, jag hjälper dig. I slutet av den här handledningen kommer du att vara ett proffs på att sammanfoga celler i dina Word-dokument programmatiskt. Så, låt oss kavla upp ärmarna och sätta igång!

## Förkunskapskrav

Innan vi går in på detaljerna finns det några saker du behöver ha på plats:

1. Aspose.Words för .NET-biblioteket: Om du inte redan har gjort det, ladda ner Aspose.Words för .NET-biblioteket. Du kan hämta det. [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö konfigurerad, till exempel Visual Studio.
3. Grundläggande kunskaper i C#: Grundläggande förståelse för C#-programmering är meriterande.

När du har fått ordning på allt detta är du redo att åka!

## Importera namnrymder

Innan vi går in i koden, låt oss se till att vi har importerat de nödvändiga namnrymderna. Se till att inkludera följande i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Okej, låt oss gå igenom processen för att horisontellt sammanfoga tabellceller i ett Word-dokument med hjälp av Aspose.Words för .NET.

## Steg 1: Konfigurera ditt dokument

Först och främst måste vi skapa ett nytt Word-dokument och initiera det. `DocumentBuilder`:

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Detta kodavsnitt skapar ett nytt dokument och förbereder `DocumentBuilder` för handling.

## Steg 2: Infoga den första cellen

Nästa steg är att infoga den första cellen och markera den för horisontell sammanfogning:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Här infogar vi en ny cell och ställer in dess `HorizontalMerge` egendom till `CellMerge.First`, vilket indikerar att den här cellen är början på en sammanslagen cellsekvens.

## Steg 3: Infoga den sammanslagna cellen

Nu infogar vi cellen som ska slås samman med den föregående:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Den här cellen är inställd på att slås samman med föregående cell med hjälp av `CellMerge.Previous`Lägg märke till hur vi avslutar raden med `builder.EndRow()`.

## Steg 4: Infoga osammanslagna celler

För att illustrera skillnaden, låt oss infoga ett par osammanslagna celler:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Här infogar vi två celler utan horisontell sammanslagning. Detta visar hur celler beter sig när de inte är en del av en sammanslagen sekvens.

## Steg 5: Färdigställande av tabellen

Slutligen avslutar vi tabellen och sparar dokumentet:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Det här kodavsnittet kompletterar tabellen och sparar dokumentet i den angivna katalogen.

## Slutsats

Och där har du det! Du har precis bemästrat konsten att horisontellt sammanfoga celler i ett Word-dokument med hjälp av Aspose.Words för .NET. Genom att följa dessa steg kan du enkelt skapa komplexa tabellstrukturer. Fortsätt experimentera och utforska Aspose.Words funktioner för att göra dina dokument så dynamiska och flexibla som du behöver. Lycka till med kodningen!

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, redigera och manipulera Word-dokument programmatiskt i .NET-applikationer.

### Kan jag sammanfoga celler vertikalt med Aspose.Words för .NET?
Ja, du kan också sammanfoga celler vertikalt genom att använda `CellFormat.VerticalMerge` egendom.

### Är Aspose.Words för .NET gratis att använda?
Aspose.Words för .NET erbjuder en gratis provperiod, men för full funktionalitet måste du köpa en licens. Du kan få en tillfällig licens. [här](https://purchase.aspose.com/temporary-license/).

### Hur kan jag lära mig mer om Aspose.Words för .NET?
Du kan utforska den detaljerade dokumentationen [här](https://reference.aspose.com/words/net/).

### Var kan jag få support för Aspose.Words för .NET?
För eventuella frågor eller problem kan du besöka Asposes supportforum [här](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}