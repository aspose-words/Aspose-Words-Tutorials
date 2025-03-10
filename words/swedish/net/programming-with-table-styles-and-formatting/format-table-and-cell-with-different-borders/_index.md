---
title: Formatera Tabell Och Cell Med Olika Kanter
linktitle: Formatera Tabell Och Cell Med Olika Kanter
second_title: Aspose.Words Document Processing API
description: Lär dig hur du formaterar tabeller och celler med olika ramar med Aspose.Words för .NET. Förbättra dina Word-dokument med anpassade tabellstilar och cellskuggning.
weight: 10
url: /sv/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatera Tabell Och Cell Med Olika Kanter

## Introduktion

Har du någonsin försökt få dina Word-dokument att se mer professionella ut genom att anpassa kanterna på tabeller och celler? Om inte, är du i för en njutning! Denna handledning kommer att leda dig genom processen att formatera tabeller och celler med olika kanter med Aspose.Words för .NET. Föreställ dig att du har makten att ändra utseendet på dina tabeller med bara några rader kod. Nyfiken? Låt oss dyka in och utforska hur du enkelt kan uppnå detta.

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar på plats:
- En grundläggande förståelse för C#-programmering.
- Visual Studio installerat på din dator.
-  Aspose.Words för .NET-bibliotek. Om du inte har installerat det ännu kan du ladda ner det[här](https://releases.aspose.com/words/net/).
-  En giltig Aspose-licens. Du kan få en gratis provperiod eller en tillfällig licens från[här](https://purchase.aspose.com/temporary-license/).

## Importera namnområden

För att arbeta med Aspose.Words för .NET måste du importera de nödvändiga namnrymden till ditt projekt. Lägg till följande med hjälp av direktiv överst i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Steg 1: Initiera Document and DocumentBuilder

Först måste du skapa ett nytt dokument och initiera DocumentBuilder, vilket hjälper dig att bygga dokumentinnehållet. 

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Börja skapa en tabell

Använd sedan DocumentBuilder för att börja skapa en tabell och infoga den första cellen.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Steg 3: Ställ in bordsgränser

Ställ in gränserna för hela bordet. Detta steg säkerställer att alla celler i tabellen har en konsekvent ramstil om inget annat anges.

```csharp
// Ställ in gränserna för hela bordet.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Steg 4: Använd cellskuggning

Applicera skuggning på cellerna för att göra dem visuellt distinkta. I det här exemplet ställer vi in den första cellens bakgrundsfärg till röd.


```csharp
// Ställ in cellskuggningen för den här cellen.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Steg 5: Infoga en annan cell med annan skuggning

Sätt in den andra cellen och använd en annan skuggfärg. Detta gör tabellen mer färgstark och lättare att läsa.

```csharp
builder.InsertCell();
// Ange en annan cellskuggning för den andra cellen.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Steg 6: Rensa cellformatering

Rensa cellformateringen från tidigare operationer för att säkerställa att nästa celler inte ärver samma stilar.


```csharp
// Rensa cellformateringen från tidigare operationer.
builder.CellFormat.ClearFormatting();
```

## Steg 7: Anpassa gränser för specifika celler

Anpassa gränserna för specifika celler för att få dem att sticka ut. Här kommer vi att sätta större ramar för den första cellen i den nya raden.

```csharp
builder.InsertCell();
// Skapa större ramar för den första cellen i denna rad. Detta kommer att bli annorlunda
// jämfört med gränserna för tabellen.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Steg 8: Infoga sista cell

Infoga den sista cellen och se till att dess formatering är rensad, så att den använder tabellens standardstilar.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Steg 9: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Slutsats

Och där har du det! Du har precis lärt dig hur du formaterar tabeller och celler med olika ramar med Aspose.Words för .NET. Genom att anpassa bordskanter och cellskuggning kan du avsevärt förbättra dina dokuments visuella tilltalande. Så fortsätt, experimentera med olika stilar och få dina dokument att sticka ut!

## FAQ's

### Kan jag använda olika kantstilar för varje cell?
 Ja, du kan ställa in olika kantstilar för varje cell genom att använda`CellFormat.Borders` egendom.

### Hur kan jag ta bort alla kanter från en tabell?
 Du kan ta bort alla kanter genom att ställa in kantstilen till`LineStyle.None`.

### Är det möjligt att ställa in olika kantfärger för varje cell?
 Absolut! Du kan anpassa kantfärgen för varje cell med hjälp av`CellFormat.Borders.Color` egendom.

### Kan jag använda bilder som cellbakgrund?
Även om Aspose.Words inte direkt stöder bilder som cellbakgrunder, kan du infoga en bild i en cell och justera dess storlek för att täcka cellområdet.

### Hur slår jag ihop celler i en tabell?
 Du kan slå samman celler med hjälp av`CellFormat.HorizontalMerge` och`CellFormat.VerticalMerge` fastigheter.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
