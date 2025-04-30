---
"description": "Lär dig hur du formaterar tabeller och celler med olika kantlinjer med Aspose.Words för .NET. Förbättra dina Word-dokument med anpassade tabellformat och cellskuggning."
"linktitle": "Formatera tabell och cell med olika kantlinjer"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Formatera tabell och cell med olika kantlinjer"
"url": "/sv/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatera tabell och cell med olika kantlinjer

## Introduktion

Har du någonsin försökt få dina Word-dokument att se mer professionella ut genom att anpassa kantlinjerna för tabeller och celler? Om inte, så väntar dig en riktig njutning! Den här handledningen guidar dig genom processen att formatera tabeller och celler med olika kantlinjer med Aspose.Words för .NET. Tänk dig att ha möjligheten att ändra utseendet på dina tabeller med bara några få rader kod. Nyfiken? Låt oss dyka in och utforska hur du enkelt kan uppnå detta.

## Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar på plats:
- Grundläggande förståelse för C#-programmering.
- Visual Studio installerat på din dator.
- Aspose.Words för .NET-biblioteket. Om du inte har installerat det än kan du ladda ner det. [här](https://releases.aspose.com/words/net/).
- En giltig Aspose-licens. Du kan få en gratis provperiod eller en tillfällig licens från [här](https://purchase.aspose.com/temporary-license/).

## Importera namnrymder

För att arbeta med Aspose.Words för .NET måste du importera nödvändiga namnrymder till ditt projekt. Lägg till följande med hjälp av direktiv högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Steg 1: Initiera dokumentet och DocumentBuilder

Först måste du skapa ett nytt dokument och initiera DocumentBuilder, vilket hjälper till att bygga dokumentinnehållet. 

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

## Steg 3: Ställ in tabellkanter

Ange kantlinjer för hela tabellen. Detta steg säkerställer att alla celler i tabellen har en enhetlig kantlinjestil om inget annat anges.

```csharp
// Ställ in ramarna för hela tabellen.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Steg 4: Använd cellskuggning

Använd skuggning på cellerna för att göra dem visuellt distinkta. I det här exemplet ställer vi in den första cellens bakgrundsfärg till röd.


```csharp
// Ställ in cellskuggning för den här cellen.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Steg 5: Infoga en annan cell med annan skuggning

Infoga den andra cellen och använd en annan skuggningsfärg. Detta gör tabellen mer färgglad och lättare att läsa.

```csharp
builder.InsertCell();
// Ange en annan cellskuggning för den andra cellen.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Steg 6: Rensa cellformatering

Rensa cellformateringen från tidigare operationer för att säkerställa att nästa celler inte ärver samma format.


```csharp
// Rensa cellformateringen från tidigare operationer.
builder.CellFormat.ClearFormatting();
```

## Steg 7: Anpassa kantlinjer för specifika celler

Anpassa ramarna för specifika celler för att få dem att sticka ut. Här ställer vi in större ramar för den första cellen i den nya raden.

```csharp
builder.InsertCell();
// Skapa större ramar för den första cellen i den här raden. Detta kommer att vara annorlunda
// jämfört med de gränser som angetts för tabellen.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Steg 8: Infoga sista cell

Infoga den sista cellen och se till att dess formatering är avmarkerad, så att den använder tabellens standardformat.

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

Och där har du det! Du har precis lärt dig hur du formaterar tabeller och celler med olika kantlinjer med Aspose.Words för .NET. Genom att anpassa tabellkantlinjer och cellskuggning kan du avsevärt förbättra dina dokuments visuella attraktionskraft. Så experimentera med olika stilar och få dina dokument att sticka ut!

## Vanliga frågor

### Kan jag använda olika kantstilar för varje cell?
Ja, du kan ange olika kantstilar för varje cell genom att använda `CellFormat.Borders` egendom.

### Hur kan jag ta bort alla ramar från en tabell?
Du kan ta bort alla ramar genom att ställa in ramstilen till `LineStyle.None`.

### Är det möjligt att ange olika kantfärger för varje cell?
Absolut! Du kan anpassa kantfärgen för varje cell med hjälp av `CellFormat.Borders.Color` egendom.

### Kan jag använda bilder som cellbakgrunder?
Även om Aspose.Words inte direkt stöder bilder som cellbakgrunder, kan du infoga en bild i en cell och justera dess storlek för att täcka cellområdet.

### Hur sammanfogar jag celler i en tabell?
Du kan sammanfoga celler med hjälp av `CellFormat.HorizontalMerge` och `CellFormat.VerticalMerge` egenskaper.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}