---
title: Expandera formatering på celler och rad från stil
linktitle: Expandera formatering på celler och rad från stil
second_title: Aspose.Words Document Processing API
description: Lär dig hur du utökar formateringen på celler och rader från stilar i Word-dokument med Aspose.Words för .NET. Steg-för-steg-guide ingår.
weight: 10
url: /sv/net/programming-with-table-styles-and-formatting/expand-formatting-on-cells-and-row-from-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Expandera formatering på celler och rad från stil

## Introduktion

Har du någonsin funnit att du behöver använda konsekvent stil över tabeller i dina Word-dokument? Att manuellt justera varje cell kan vara tråkigt och risk för fel. Det är där Aspose.Words för .NET kommer väl till pass. Denna handledning guidar dig genom processen att utöka formateringen på celler och rader från en tabellstil, vilket säkerställer att dina dokument ser snygga och professionella ut utan extra krångel.

## Förutsättningar

Innan vi går in i de nitty-gritty detaljerna, se till att du har följande på plats:

-  Aspose.Words för .NET: Du kan ladda ner det[här](https://releases.aspose.com/words/net/).
- Visual Studio: Alla senaste versioner fungerar.
- Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering är viktigt.
- Exempeldokument: Ha ett Word-dokument med en tabell redo, eller så kan du använda det som finns i kodexemplet.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta kommer att säkerställa att alla nödvändiga klasser och metoder är tillgängliga för användning i vår kod.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Låt oss nu dela upp processen i enkla steg som är lätta att följa.

## Steg 1: Ladda ditt dokument

I det här steget laddar vi Word-dokumentet som innehåller tabellen du vill formatera. 

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

## Steg 2: Gå till tabellen

Därefter måste vi komma åt den första tabellen i dokumentet. Den här tabellen kommer att vara i fokus för våra formateringsoperationer.

```csharp
// Hämta den första tabellen i dokumentet.
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Hämta den första cellen

Låt oss nu hämta den första cellen i den första raden i tabellen. Detta kommer att hjälpa oss att visa hur cellens formatering ändras när stilar utökas.

```csharp
// Få den första cellen i den första raden i tabellen.
Cell firstCell = table.FirstRow.FirstCell;
```

## Steg 4: Kontrollera initial cellskuggning

Innan vi tillämpar någon formatering, låt oss kontrollera och skriva ut den ursprungliga skuggfärgen för cellen. Detta kommer att ge oss en baslinje att jämföra med efter stilexpansionen.

```csharp
// Skriv ut den ursprungliga cellskuggningsfärgen.
Color cellShadingBefore = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading before style expansion: " + cellShadingBefore);
```

## Steg 5: Expandera tabellstilar

 Här händer magin. Vi ringer`ExpandTableStylesToDirectFormatting` metod för att tillämpa tabellstilarna direkt på cellerna.

```csharp
// Utöka tabellstilarna till direktformatering.
doc.ExpandTableStylesToDirectFormatting();
```

## Steg 6: Kontrollera slutlig cellskuggning

Slutligen kommer vi att kontrollera och skriva ut cellens skuggfärg efter att ha utökat stilarna. Du bör se den uppdaterade formateringen tillämpad från tabellformatet.

```csharp
// Skriv ut cellskuggningsfärgen efter stilexpansion.
Color cellShadingAfter = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading after style expansion: " + cellShadingAfter);
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt utöka formateringen av celler och rader från stilar i dina Word-dokument med Aspose.Words för .NET. Detta sparar inte bara tid utan säkerställer också konsekvens i dina dokument. Glad kodning!

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt API som gör det möjligt för utvecklare att skapa, redigera, konvertera och manipulera Word-dokument programmatiskt.

### Varför skulle jag behöva utöka formateringen från stilar?
Om du utökar formateringen från stilar säkerställs att stilen appliceras direkt på cellerna, vilket gör det lättare att underhålla och uppdatera dokumentet.

### Kan jag tillämpa dessa steg på flera tabeller i ett dokument?
Absolut! Du kan gå igenom alla tabeller i ditt dokument och tillämpa samma steg på var och en.

### Finns det något sätt att återställa de utökade stilarna?
När formatmallar har expanderats appliceras de direkt på cellerna. För att återgå måste du ladda om dokumentet eller återanvända stilarna manuellt.

### Fungerar den här metoden med alla versioner av Aspose.Words för .NET?
 Ja, den`ExpandTableStylesToDirectFormatting` metod är tillgänglig i de senaste versionerna av Aspose.Words för .NET. Kontrollera alltid[dokumentation](https://reference.aspose.com/words/net/) för de senaste uppdateringarna.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
