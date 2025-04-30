---
"description": "Lär dig hur du delar upp tabeller i Word-dokument med Aspose.Words för .NET. Vår steg-för-steg-guide gör tabellhanteringen enkel och effektiv."
"linktitle": "Delad tabell"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Delad tabell"
"url": "/sv/net/programming-with-tables/split-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Delad tabell

## Introduktion

Har du någonsin arbetat med en stor tabell i ett Word-dokument och önskat att du kunde dela upp den i två mindre, mer hanterbara tabeller? Idag ska vi gå in på exakt hur du kan uppnå detta med Aspose.Words för .NET. Oavsett om du arbetar med omfattande datatabeller eller komplexa dokumentstrukturer kan dela upp tabeller bidra till att förbättra läsbarheten och organisationen. Låt oss utforska steg-för-steg-processen för att dela en tabell med Aspose.Words för .NET.

## Förkunskapskrav

Innan vi går in i handledningen, se till att du har följande:

1. Aspose.Words för .NET-biblioteket: Se till att du har laddat ner och installerat Aspose.Words för .NET-biblioteket. Du kan hämta det från [Aspose-utgåvorsida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Konfigurera en utvecklingsmiljö med stöd för .NET Framework, till exempel Visual Studio.
3. Exempeldokument: Förbered ett Word-dokument (`Tables.docx`) med minst en tabell för att tillämpa delningsoperationen.

## Importera namnrymder

Importera först de nödvändiga namnrymderna till ditt projekt. Detta ger dig åtkomst till klasserna och metoderna som tillhandahålls av Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Ladda dokumentet

Låt oss börja med att ladda dokumentet som innehåller tabellen du vill dela. Se till att ange rätt sökväg till dokumentet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Steg 2: Identifiera tabellen som ska delas

Identifiera och hämta sedan tabellen du vill dela. I det här exemplet riktar vi in oss på den första tabellen i dokumentet.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Välj raden att dela vid

Bestäm raden där du vill dela tabellen. Här delar vi tabellen vid den tredje raden (inklusive).

```csharp
Row row = firstTable.Rows[2];
```

## Steg 4: Skapa en ny tabellbehållare

Skapa en ny tabellbehållare för att lagra de rader som ska flyttas från den ursprungliga tabellen.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Steg 5: Infoga den nya tabellbehållaren

Infoga den nya tabellbehållaren direkt efter den ursprungliga tabellen i dokumentet.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Steg 6: Lägg till ett buffertparagraf

Lägg till ett buffertparagraf mellan de två tabellerna för att säkerställa att de förblir separata.

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

Spara slutligen det ändrade dokumentet med tabellerna uppdelade.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt dela upp en tabell i ett Word-dokument med hjälp av Aspose.Words för .NET. Den här metoden hjälper dig att hantera stora tabeller mer effektivt, vilket förbättrar läsbarheten och organisationen av dina dokument. Testa och se hur det förenklar ditt arbete med tabeller i Word-dokument.

## Vanliga frågor

### Kan jag dela en tabell på flera rader?
Ja, du kan dela en tabell på flera rader genom att upprepa processen för varje delningspunkt.

### Vad händer med formateringen av den ursprungliga tabellen?
Den nya tabellen ärver formateringen från den ursprungliga tabellen. Eventuella specifika formateringsändringar kan tillämpas på den nya tabellen efter behov.

### Är det möjligt att sammanfoga tabeller igen?
Ja, du kan sammanfoga tabeller genom att flytta rader från en tabell till en annan med liknande metoder.

### Fungerar den här metoden med kapslade tabeller?
Ja, Aspose.Words för .NET stöder även operationer på kapslade tabeller.

### Kan jag automatisera den här processen för flera dokument?
Absolut! Du kan skapa ett skript eller en applikation för att automatisera tabelldelningsprocessen för flera dokument.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}