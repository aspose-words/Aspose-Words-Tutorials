---
title: Upprepa rader på efterföljande sidor
linktitle: Upprepa rader på efterföljande sidor
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar Word-dokument med upprepade tabellrubriker med Aspose.Words för .NET. Följ den här guiden för att säkerställa professionella och polerade dokument.
weight: 10
url: /sv/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Upprepa rader på efterföljande sidor

## Introduktion

Att skapa ett Word-dokument programmatiskt kan vara en skrämmande uppgift, särskilt när du behöver behålla formateringen över flera sidor. Har du någonsin försökt skapa en tabell i Word, bara för att inse att dina rubrikrader inte upprepas på efterföljande sidor? Var inte rädd! Med Aspose.Words för .NET kan du enkelt se till att dina tabellrubriker upprepas på varje sida, vilket ger dina dokument ett professionellt och polerat utseende. I den här handledningen går vi igenom stegen för att uppnå detta med enkla kodexempel och detaljerade förklaringar. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET: Du kan ladda ner det[här](https://releases.aspose.com/words/net/).
2. .NET Framework installerat på din dator.
3. Visual Studio eller någon annan IDE som stöder .NET-utveckling.
4. Grundläggande förståelse för C#-programmering.

Se till att du har installerat Aspose.Words för .NET och ställt in din utvecklingsmiljö innan du fortsätter.

## Importera namnområden

Till att börja med måste du importera de nödvändiga namnrymden i ditt projekt. Lägg till följande med hjälp av direktiv överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dessa namnrymder inkluderar de klasser och metoder som krävs för att manipulera Word-dokument och tabeller.

## Steg 1: Initiera dokumentet

 Låt oss först skapa ett nytt Word-dokument och ett`DocumentBuilder` att bygga vårt bord.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Denna kod initierar ett nytt dokument och en`DocumentBuilder` objekt, vilket hjälper till att bygga dokumentstrukturen.

## Steg 2: Starta tabellen och definiera rubrikrader

Därefter startar vi tabellen och definierar rubrikraderna som vi vill upprepa på efterföljande sidor.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

 Här startar vi ett nytt bord, ställer upp`HeadingFormat`egendom till`true` för att indikera att raderna är rubriker, och definiera justeringen och bredden på cellerna.

## Steg 3: Lägg till datarader i tabellen

Nu lägger vi till flera datarader i vår tabell. Dessa rader kommer inte att upprepas på efterföljande sidor.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

 Denna loop infogar 50 rader med data i tabellen, med två kolumner i varje rad. De`HeadingFormat` är inställd på`false` för dessa rader, eftersom de inte är rubrikrader.

## Steg 4: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Detta sparar dokumentet med det angivna namnet i din dokumentkatalog.

## Slutsats

Och där har du det! Med bara några rader kod kan du skapa ett Word-dokument med tabeller som har upprepade rubrikrader på efterföljande sidor med Aspose.Words för .NET. Detta förbättrar inte bara läsbarheten för dina dokument utan säkerställer också ett konsekvent och professionellt utseende. Nu, fortsätt och prova detta i dina projekt!

## FAQ's

### Kan jag anpassa rubrikraderna ytterligare?
 Ja, du kan använda ytterligare formatering på rubrikraderna genom att ändra egenskaperna för`ParagraphFormat`, `RowFormat` , och`CellFormat`.

### Är det möjligt att lägga till fler kolumner i tabellen?
 Absolut! Du kan lägga till så många kolumner som behövs genom att infoga fler celler i`InsertCell` metod.

### Hur kan jag få andra rader att upprepas på efterföljande sidor?
 För att få en rad att upprepa, ställ in`RowFormat.HeadingFormat`egendom till`true` för den specifika raden.

### Kan jag använda den här metoden för befintliga tabeller i ett dokument?
 Ja, du kan ändra befintliga tabeller genom att komma åt dem via`Document` objekt och tillämpa liknande formatering.

### Vilka andra tabellformateringsalternativ finns i Aspose.Words för .NET?
 Aspose.Words för .NET erbjuder ett brett utbud av tabellformateringsalternativ, inklusive cellsammanslagning, gränsinställningar och tabelljustering. Kolla in[dokumentation](https://reference.aspose.com/words/net/) för mer information.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
