---
title: Lägg till datum och tid till axeln i ett diagram
linktitle: Lägg till datum och tid till axeln i ett diagram
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till datum- och tidsvärden till ett diagrams axel med Aspose.Words för .NET i den här omfattande steg-för-steg-guiden.
weight: 10
url: /sv/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till datum och tid till axeln i ett diagram

## Introduktion

Att skapa diagram i dokument kan vara ett kraftfullt sätt att visualisera data. När man hanterar tidsseriedata är det avgörande att lägga till datum- och tidsvärden till axeln i ett diagram för tydligheten. I den här handledningen går vi igenom processen att lägga till datum- och tidsvärden till ett diagrams axel med Aspose.Words för .NET. Den här steg-för-steg-guiden hjälper dig att ställa in din miljö, skriva koden och förstå varje del av processen. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar på plats:

1. Visual Studio eller någon .NET IDE: Du behöver en utvecklingsmiljö för att skriva och köra din .NET-kod.
2.  Aspose.Words for .NET: Du bör ha Aspose.Words for .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.aspose.com/words/net/).
3. Grundläggande kunskaper om C#: Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmering.
4.  En giltig Aspose-licens: Du kan få en tillfällig licens från[här](https://purchase.aspose.com/temporary-license/).

## Importera namnområden

Till att börja med, se till att du har de nödvändiga namnrymden importerade i ditt projekt. Detta steg är avgörande för att komma åt Aspose.Words-klasserna och -metoderna.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Steg 1: Konfigurera din dokumentkatalog

Först måste du definiera katalogen där ditt dokument ska sparas. Detta är viktigt för att organisera dina filer och se till att din kod körs korrekt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument och DocumentBuilder

 Skapa sedan en ny instans av`Document` klass och a`DocumentBuilder` objekt. Dessa objekt hjälper dig att bygga och manipulera ditt dokument.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga ett diagram i dokumentet

 Infoga nu ett diagram i ditt dokument med hjälp av`DocumentBuilder` objekt. I det här exemplet använder vi ett kolumndiagram, men du kan också välja andra typer.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Steg 4: Rensa befintliga serier

Rensa alla befintliga serier i diagrammet för att säkerställa att du börjar med ett tomt blad. Detta steg är viktigt för anpassade data.

```csharp
chart.Series.Clear();
```

## Steg 5: Lägg till datum- och tidsvärden till serien

Lägg till dina datum- och tidsvärden i diagramserien. Detta steg innebär att skapa matriser för datum och motsvarande värden.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Steg 6: Konfigurera X-axeln

Ställ in skalning och bock för X-axeln. Detta säkerställer att dina datum visas korrekt och med lämpliga intervall.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Steg 7: Spara dokumentet

Slutligen, spara ditt dokument i den angivna katalogen. Detta steg avslutar processen, och ditt dokument bör nu innehålla ett diagram med datum- och tidsvärden på X-axeln.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Slutsats

Att lägga till datum- och tidsvärden till axeln i ett diagram i ett dokument är en enkel process med Aspose.Words för .NET. Genom att följa stegen som beskrivs i denna handledning kan du skapa tydliga och informativa diagram som effektivt visualiserar tidsseriedata. Oavsett om du förbereder rapporter, presentationer eller andra dokument som kräver detaljerad datarepresentation, tillhandahåller Aspose.Words de verktyg du behöver för att lyckas.

## FAQ's

### Kan jag använda andra diagramtyper med Aspose.Words för .NET?

Ja, Aspose.Words stöder olika diagramtyper, inklusive linje, stapel, cirkel och mer.

### Hur kan jag anpassa utseendet på mitt diagram?

Du kan anpassa utseendet genom att komma åt diagrammets egenskaper och inställningsstilar, färger och mer.

### Är det möjligt att lägga till flera serier i ett diagram?

 Absolut! Du kan lägga till flera serier till ditt diagram genom att anropa`Series.Add` metod flera gånger med olika data.

### Vad händer om jag behöver uppdatera diagramdata dynamiskt?

Du kan uppdatera diagramdata dynamiskt genom att manipulera serie- och axelegenskaperna programmatiskt baserat på dina krav.

### Var kan jag hitta mer detaljerad dokumentation för Aspose.Words för .NET?

 Du kan hitta mer detaljerad dokumentation[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
