---
title: Delat bord
linktitle: Delat bord
second_title: Aspose.Words Document Processing API
description: Lär dig hur du delar tabeller i Word-dokument med Aspose.Words för .NET. Vår steg-för-steg-guide gör bordshanteringen enkel och effektiv.
weight: 10
url: /sv/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Delat bord

## Introduktion

Har du någonsin sett dig själv att arbeta med en stor tabell i ett Word-dokument och önskat att du kunde dela upp den i två mindre, mer lätthanterliga tabeller? Tja, idag dyker vi in i exakt hur du kan uppnå detta med Aspose.Words för .NET. Oavsett om du har att göra med omfattande datatabeller eller komplexa dokumentstrukturer, kan dela tabeller hjälpa till att förbättra läsbarheten och organisationen. Låt oss utforska steg-för-steg-processen för att dela en tabell med Aspose.Words för .NET.

## Förutsättningar

Innan vi hoppar in i handledningen, se till att du har följande:

1.  Aspose.Words for .NET Library: Se till att du har laddat ner och installerat Aspose.Words for .NET-biblioteket. Du kan få det från[Aspose releaser sida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Sätt upp en utvecklingsmiljö med stöd för .NET framework, som Visual Studio.
3. Exempeldokument: Förbered ett Word-dokument (`Tables.docx`) med minst en tabell för att tillämpa split-operationen.

## Importera namnområden

Importera först de nödvändiga namnrymden till ditt projekt. Detta låter dig komma åt klasserna och metoderna som tillhandahålls av Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Ladda dokumentet

Låt oss börja med att ladda dokumentet som innehåller tabellen du vill dela. Se till att ange rätt sökväg till ditt dokument.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Steg 2: Identifiera tabellen som ska delas

Identifiera och hämta sedan tabellen du vill dela. I det här exemplet riktar vi oss mot den första tabellen i dokumentet.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Välj raden att dela på

Bestäm raden där du vill dela tabellen. Här delar vi bordet på den tredje raden (inklusive).

```csharp
Row row = firstTable.Rows[2];
```

## Steg 4: Skapa en ny tabellbehållare

Skapa en ny tabellbehållare för att hålla raderna som ska flyttas från den ursprungliga tabellen.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Steg 5: Sätt i den nya bordsbehållaren

Infoga den nya tabellbehållaren direkt efter den ursprungliga tabellen i dokumentet.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Steg 6: Lägg till en buffertparagraf

Lägg till ett buffertstycke mellan de två tabellerna för att säkerställa att de förblir åtskilda.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Steg 7: Flytta rader till den nya tabellen

Flytta raderna från den ursprungliga tabellen till den nya tabellbehållaren. Denna loop fortsätter tills den angivna raden (inklusive) flyttas.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Steg 8: Spara dokumentet

Slutligen, spara det ändrade dokumentet med tabellerna delade.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt dela upp en tabell i ett Word-dokument med Aspose.Words för .NET. Detta tillvägagångssätt hjälper dig att hantera stora tabeller mer effektivt, vilket förbättrar läsbarheten och organisationen av dina dokument. Prova det och se hur det förenklar ditt arbete med tabeller i Word-dokument.

## FAQ's

### Kan jag dela ett bord på flera rader?
Ja, du kan dela en tabell på flera rader genom att upprepa processen för varje delningspunkt.

### Vad händer med formateringen av den ursprungliga tabellen?
Den nya tabellen ärver formateringen av den ursprungliga tabellen. Alla specifika formateringsändringar kan tillämpas på den nya tabellen efter behov.

### Är det möjligt att slå samman tabeller igen?
Ja, du kan slå samman tabeller genom att flytta rader från en tabell till en annan med liknande metoder.

### Fungerar den här metoden med kapslade tabeller?
Ja, Aspose.Words för .NET stöder även operationer på kapslade tabeller.

### Kan jag automatisera den här processen för flera dokument?
Absolut! Du kan skapa ett skript eller program för att automatisera tabelldelningsprocessen för flera dokument.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
