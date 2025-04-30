---
"description": "Lär dig hur du skapar och formaterar tabeller i Word-dokument med Aspose.Words för .NET med den här detaljerade steg-för-steg-guiden."
"linktitle": "Formaterad tabell"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Formaterad tabell"
"url": "/sv/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formaterad tabell

## Introduktion

Att skapa och formatera tabeller i Word-dokument programmatiskt kan verka som en svår uppgift, men med Aspose.Words för .NET blir det enkelt och hanterbart. I den här handledningen går vi igenom hur du skapar en formaterad tabell i ett Word-dokument med Aspose.Words för .NET. Vi går igenom allt från att konfigurera din miljö till att spara ditt dokument med en vackert formaterad tabell.

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET-biblioteket: Ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.

## Importera namnrymder

Innan du skriver själva koden måste du importera de nödvändiga namnrymderna:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Konfigurera din dokumentkatalog

Först måste du definiera sökvägen där ditt dokument ska sparas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara dokumentet.

## Steg 2: Initiera dokumentet och DocumentBuilder

Initiera nu ett nytt dokument och ett DocumentBuilder-objekt.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

De `DocumentBuilder` är en hjälpklass som förenklar processen att skapa dokument.

## Steg 3: Starta tabellen

Börja sedan skapa tabellen med hjälp av `StartTable` metod.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Det är nödvändigt att infoga en cell för att påbörja tabellen.

## Steg 4: Tillämpa tabellomfattande formatering

Du kan använda formatering som påverkar hela tabellen. Till exempel, ställa in vänsterindraget:

```csharp
table.LeftIndent = 20.0;
```

## Steg 5: Formatera rubrikraden

Ange höjd, justering och andra egenskaper för rubrikraden.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

I det här steget får vi rubrikraden att sticka ut genom att ange bakgrundsfärg, teckenstorlek och justering.

## Steg 6: Infoga ytterligare rubrikceller

Infoga fler celler för rubrikraden:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Steg 7: Formatera brödtextraderna

Efter att du har konfigurerat rubriken, formatera tabellens brödtext:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Steg 8: Infoga brödtextrader

Infoga brödtextraderna med innehåll:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Upprepa för ytterligare rader:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Steg 9: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Detta skapar och sparar ett Word-dokument med den formaterade tabellen.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du skapa en välformaterad tabell i ett Word-dokument med hjälp av Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att programmatiskt manipulera Word-dokument, vilket sparar tid och ansträngning.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att skapa, redigera och konvertera Word-dokument programmatiskt.

### Kan jag använda olika färger för olika rader?
Ja, du kan använda olika formateringar, inklusive färger, på olika rader eller celler.

### Är Aspose.Words för .NET gratis?
Aspose.Words för .NET är ett betalt bibliotek, men du kan få ett [gratis provperiod](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words för .NET?
Du kan få stöd från [Aspose communityforum](https://forum.aspose.com/c/words/8).

### Kan jag skapa andra typer av dokument med Aspose.Words för .NET?
Ja, Aspose.Words för .NET stöder olika dokumentformat, inklusive PDF, HTML och TXT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}