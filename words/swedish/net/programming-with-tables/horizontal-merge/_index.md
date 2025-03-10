---
title: Horisontell sammanfogning
linktitle: Horisontell sammanfogning
second_title: Aspose.Words Document Processing API
description: Lär dig hur du sammanfogar celler horisontellt i ett Word-dokument med Aspose.Words för .NET med denna detaljerade, steg-för-steg handledning.
weight: 10
url: /sv/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horisontell sammanfogning

## Introduktion

Hej där! Är du redo att dyka in i Aspose.Words-världen för .NET? Idag ska vi ta itu med en superanvändbar funktion: horisontell sammanslagning i tabeller. Det här kanske låter lite tekniskt, men oroa dig inte, jag har din rygg. I slutet av den här handledningen kommer du att vara ett proffs på att slå samman celler i dina Word-dokument programmatiskt. Så, låt oss kavla upp ärmarna och sätta igång!

## Förutsättningar

Innan vi hoppar in i det knasiga, finns det några saker du måste ha på plats:

1. Aspose.Words for .NET Library: Om du inte redan har gjort det, ladda ner Aspose.Words for .NET-biblioteket. Du kan ta tag i den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö inrättad, som Visual Studio.
3. Grundläggande kunskaper i C#: En grundläggande förståelse för C#-programmering kommer att vara fördelaktigt.

När du har ordnat dessa är du redo att gå!

## Importera namnområden

Innan vi dyker in i koden, låt oss se till att vi har de nödvändiga namnrymden importerade. I ditt C#-projekt, se till att inkludera:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Okej, låt oss bryta ner processen för att horisontellt slå samman tabellceller i ett Word-dokument med Aspose.Words för .NET.

## Steg 1: Konfigurera ditt dokument

 Först och främst måste vi skapa ett nytt Word-dokument och initiera`DocumentBuilder`:

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Detta kodavsnitt skapar ett nytt dokument och förbereder`DocumentBuilder` för handling.

## Steg 2: Infoga den första cellen

Därefter börjar vi med att infoga den första cellen och markera den för horisontell sammanslagning:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Här infogar vi en ny cell och ställer in dess`HorizontalMerge`egendom till`CellMerge.First`, vilket indikerar att denna cell är början på en sammanslagen cellsekvens.

## Steg 3: Infoga den sammanslagna cellen

Nu infogar vi cellen som kommer att slås samman med den föregående:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Den här cellen är inställd att slås samman med föregående cell med hjälp av`CellMerge.Previous` . Lägg märke till hur vi avslutar raden med`builder.EndRow()`.

## Steg 4: Infoga ej sammanslagna celler

För att illustrera skillnaden, låt oss infoga ett par ej sammanslagna celler:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Här infogar vi två celler utan horisontell sammanslagning. Detta visar hur celler beter sig när de inte ingår i en sammanslagen sekvens.

## Steg 5: Avsluta tabellen

Till sist avslutar vi tabellen och sparar dokumentet:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Detta kodavsnitt kompletterar tabellen och sparar dokumentet i den angivna katalogen.

## Slutsats

Och där har du det! Du har precis bemästrat konsten att horisontellt slå samman celler i ett Word-dokument med Aspose.Words för .NET. Genom att följa dessa steg kan du enkelt skapa komplexa tabellstrukturer. Fortsätt att experimentera och utforska funktionerna i Aspose.Words för att göra dina dokument så dynamiska och flexibla som du behöver. Glad kodning!

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, redigera och manipulera Word-dokument programmatiskt i .NET-applikationer.

### Kan jag slå samman celler vertikalt med Aspose.Words för .NET?
 Ja, du kan också slå samman celler vertikalt genom att använda`CellFormat.VerticalMerge` egendom.

### Är Aspose.Words för .NET gratis att använda?
 Aspose.Words för .NET erbjuder en gratis provperiod, men för full funktionalitet måste du köpa en licens. Du kan få en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).

### Hur kan jag lära mig mer om Aspose.Words för .NET?
 Du kan utforska den detaljerade dokumentationen[här](https://reference.aspose.com/words/net/).

### Var kan jag få support för Aspose.Words för .NET?
 För eventuella frågor eller problem kan du besöka Asposes supportforum[här](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
