---
"description": "Lär dig hur du inaktiverar radbrytningar över sidor i Word-dokument med Aspose.Words för .NET för att bibehålla tabellläsbarhet och formatering."
"linktitle": "Radformat Inaktivera brytning över sidor"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Radformat Inaktivera brytning över sidor"
"url": "/sv/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Radformat Inaktivera brytning över sidor

## Introduktion

När du arbetar med tabeller i Word-dokument kan det vara bra att se till att rader inte bryts över sidor, vilket kan vara viktigt för att bibehålla läsbarheten och formateringen i dina dokument. Aspose.Words för .NET erbjuder ett enkelt sätt att inaktivera radbrytningar över sidor.

den här handledningen går vi igenom processen för att inaktivera radbrytningar mellan sidor i ett Word-dokument med hjälp av Aspose.Words för .NET.

## Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar:
- Aspose.Words för .NET-biblioteket installerat.
- Ett Word-dokument med en tabell som sträcker sig över flera sidor.

## Importera namnrymder

Importera först de nödvändiga namnrymderna i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Ladda dokumentet

Ladda dokumentet som innehåller tabellen som sträcker sig över flera sidor.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Steg 2: Åtkomst till tabellen

Åtkomst till den första tabellen i dokumentet. Detta förutsätter att tabellen du vill ändra är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Inaktivera sidbrytning för alla rader

Gå igenom varje rad i tabellen och ställ in `AllowBreakAcrossPages` egendom till `false`Detta säkerställer att rader inte bryts över sidor.

```csharp
// Inaktivera sidbrytning för alla rader i tabellen.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Steg 4: Spara dokumentet

Spara det ändrade dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Slutsats

I den här handledningen visade vi hur man inaktiverar radbrytningar över sidor i ett Word-dokument med hjälp av Aspose.Words för .NET. Genom att följa stegen som beskrivs ovan kan du säkerställa att dina tabellrader förblir intakta och inte delas upp över sidor, vilket bibehåller dokumentets läsbarhet och formatering.

## Vanliga frågor

### Kan jag inaktivera radbrytningar över sidor för en specifik rad istället för alla rader?  
Ja, du kan inaktivera radbrytningar för specifika rader genom att öppna önskad rad och ställa in dess `AllowBreakAcrossPages` egendom till `false`.

### Fungerar den här metoden för tabeller med sammanslagna celler?  
Ja, den här metoden fungerar för tabeller med sammanfogade celler. Egenskapen `AllowBreakAcrossPages` gäller för hela raden, oavsett cellsammanslagning.

### Kommer den här metoden att fungera om tabellen är kapslad inuti en annan tabell?  
Ja, du kan komma åt och ändra kapslade tabeller på samma sätt. Se till att du refererar korrekt till den kapslade tabellen med dess index eller andra egenskaper.

### Hur kan jag kontrollera om en rad tillåter brytning över sidor?  
Du kan kontrollera om en rad tillåter brytning mellan sidor genom att öppna `AllowBreakAcrossPages` egendomen tillhörande `RowFormat` och kontrollerar dess värde.

### Finns det något sätt att tillämpa den här inställningen på alla tabeller i ett dokument?  
Ja, du kan loopa igenom alla tabeller i dokumentet och tillämpa den här inställningen på var och en.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}