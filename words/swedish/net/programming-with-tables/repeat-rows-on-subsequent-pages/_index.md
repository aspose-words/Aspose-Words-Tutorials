---
"description": "Lär dig hur du skapar Word-dokument med upprepade tabellrubrikrader med Aspose.Words för .NET. Följ den här guiden för att säkerställa professionella och välgjorda dokument."
"linktitle": "Upprepa rader på efterföljande sidor"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Upprepa rader på efterföljande sidor"
"url": "/sv/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Upprepa rader på efterföljande sidor

## Introduktion

Att skapa ett Word-dokument programmatiskt kan vara en skrämmande uppgift, särskilt när du behöver behålla formateringen över flera sidor. Har du någonsin försökt skapa en tabell i Word, bara för att inse att dina rubrikrader inte upprepas på efterföljande sidor? Frukta inte! Med Aspose.Words för .NET kan du enkelt se till att dina tabellrubriker upprepas på varje sida, vilket ger dina dokument ett professionellt och polerat utseende. I den här handledningen guidar vi dig genom stegen för att uppnå detta med hjälp av enkla kodexempel och detaljerade förklaringar. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Du kan ladda ner det [här](https://releases.aspose.com/words/net/).
2. .NET Framework installerat på din dator.
3. Visual Studio eller någon annan IDE som stöder .NET-utveckling.
4. Grundläggande förståelse för C#-programmering.

Se till att du har installerat Aspose.Words för .NET och konfigurerat din utvecklingsmiljö innan du fortsätter.

## Importera namnrymder

För att börja måste du importera de nödvändiga namnrymderna i ditt projekt. Lägg till följande med hjälp av direktiv högst upp i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dessa namnrymder inkluderar de klasser och metoder som krävs för att manipulera Word-dokument och tabeller.

## Steg 1: Initiera dokumentet

Först skapar vi ett nytt Word-dokument och ett `DocumentBuilder` att bygga vårt bord.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Denna kod initierar ett nytt dokument och en `DocumentBuilder` objekt, vilket hjälper till att bygga dokumentstrukturen.

## Steg 2: Starta tabellen och definiera rubrikrader

Nästa steg är att skapa tabellen och definiera rubrikraderna som vi vill upprepa på efterföljande sidor.

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

Här börjar vi ett nytt bord, dukar `HeadingFormat` egendom till `true` för att indikera att raderna är rubriker och definiera cellernas justering och bredd.

## Steg 3: Lägg till datarader i tabellen

Nu ska vi lägga till flera datarader i vår tabell. Dessa rader kommer inte att upprepas på efterföljande sidor.

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

Denna loop infogar 50 rader med data i tabellen, med två kolumner i varje rad. `HeadingFormat` är inställd på `false` för dessa rader, eftersom de inte är rubrikrader.

## Steg 4: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Detta sparar dokumentet med det angivna namnet i din dokumentkatalog.

## Slutsats

Och där har du det! Med bara några få rader kod kan du skapa ett Word-dokument med tabeller som har upprepade rubrikrader på efterföljande sidor med hjälp av Aspose.Words för .NET. Detta förbättrar inte bara läsbarheten i dina dokument utan säkerställer också ett konsekvent och professionellt utseende. Nu kan du prova detta i dina projekt!

## Vanliga frågor

### Kan jag anpassa rubrikraderna ytterligare?
Ja, du kan lägga till ytterligare formatering på rubrikraderna genom att ändra egenskaperna för `ParagraphFormat`, `RowFormat`och `CellFormat`.

### Är det möjligt att lägga till fler kolumner i tabellen?
Absolut! Du kan lägga till så många kolumner som behövs genom att infoga fler celler i `InsertCell` metod.

### Hur kan jag få andra rader att upprepas på efterföljande sidor?
För att få en rad att upprepas, ställ in `RowFormat.HeadingFormat` egendom till `true` för den specifika raden.

### Kan jag använda den här metoden för befintliga tabeller i ett dokument?
Ja, du kan ändra befintliga tabeller genom att komma åt dem via `Document` objekt och tillämpa liknande formatering.

### Vilka andra tabellformateringsalternativ finns tillgängliga i Aspose.Words för .NET?
Aspose.Words för .NET erbjuder ett brett utbud av tabellformateringsalternativ, inklusive cellsammanslagning, kantlinjer och tabelljustering. Kolla in [dokumentation](https://reference.aspose.com/words/net/) för mer information.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}