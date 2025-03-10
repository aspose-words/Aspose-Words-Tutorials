---
title: Radformat Inaktivera Break Across Pages
linktitle: Radformat Inaktivera Break Across Pages
second_title: Aspose.Words Document Processing API
description: Lär dig hur du inaktiverar radbrytningar över sidor i Word-dokument med Aspose.Words för .NET för att bibehålla tabellläsbarhet och formatering.
weight: 10
url: /sv/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radformat Inaktivera Break Across Pages

## Introduktion

När du arbetar med tabeller i Word-dokument vill du kanske se till att rader inte delas över sidor, vilket kan vara viktigt för att bibehålla läsbarheten och formateringen av dina dokument. Aspose.Words för .NET ger ett enkelt sätt att inaktivera radbrytningar över sidor.

I den här handledningen går vi igenom processen att inaktivera radbrytningar över sidor i ett Word-dokument med Aspose.Words för .NET.

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar:
- Aspose.Words för .NET-biblioteket installerat.
- Ett Word-dokument med en tabell som sträcker sig över flera sidor.

## Importera namnområden

Importera först de nödvändiga namnrymden i ditt projekt:

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

## Steg 2: Gå till tabellen

Öppna den första tabellen i dokumentet. Detta förutsätter att tabellen du vill ändra är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Inaktivera Breaking Across Pages för alla rader

 Gå igenom varje rad i tabellen och ställ in`AllowBreakAcrossPages`egendom till`false`. Detta säkerställer att rader inte bryts över sidorna.

```csharp
// Inaktivera delning över sidor för alla rader i tabellen.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Steg 4: Spara dokumentet

Spara det ändrade dokumentet i din angivna katalog.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Slutsats

I den här självstudien visade vi hur man inaktiverar radbrytningar över sidor i ett Word-dokument med Aspose.Words för .NET. Genom att följa stegen som beskrivs ovan kan du säkerställa att dina tabellrader förblir intakta och inte delas på sidor, vilket bibehåller dokumentets läsbarhet och formatering.

## FAQ's

### Kan jag inaktivera radbrytningar över sidor för en specifik rad istället för alla rader?  
 Ja, du kan inaktivera radbrytningar för specifika rader genom att komma åt önskad rad och ställa in dess`AllowBreakAcrossPages`egendom till`false`.

### Fungerar den här metoden för tabeller med sammanslagna celler?  
 Ja, den här metoden fungerar för tabeller med sammanslagna celler. Fastigheten`AllowBreakAcrossPages` gäller för hela raden, oavsett cellsammanslagning.

### Kommer den här metoden att fungera om tabellen är kapslad i en annan tabell?  
Ja, du kan komma åt och ändra kapslade tabeller på samma sätt. Se till att du refererar den kapslade tabellen på rätt sätt genom dess index eller andra egenskaper.

### Hur kan jag kontrollera om en rad tillåter brytning över sidor?  
 Du kan kontrollera om en rad tillåter brytning över sidor genom att gå till`AllowBreakAcrossPages` egendom av`RowFormat` och kontrollera dess värde.

### Finns det något sätt att tillämpa den här inställningen på alla tabeller i ett dokument?  
Ja, du kan gå igenom alla tabeller i dokumentet och tillämpa den här inställningen på var och en.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
