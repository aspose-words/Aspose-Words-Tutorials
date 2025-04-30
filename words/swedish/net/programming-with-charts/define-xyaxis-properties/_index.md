---
"description": "Lär dig hur du definierar XY-axelegenskaper i ett diagram med Aspose.Words för .NET med den här steg-för-steg-guiden. Perfekt för .NET-utvecklare."
"linktitle": "Definiera XY-axelegenskaper i ett diagram"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Definiera XY-axelegenskaper i ett diagram"
"url": "/sv/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definiera XY-axelegenskaper i ett diagram

## Introduktion

Diagram är ett kraftfullt verktyg för att visualisera data. När du behöver skapa professionella dokument med dynamiska diagram är Aspose.Words för .NET ett ovärderligt bibliotek. Den här artikeln guidar dig genom processen att definiera XY-axelegenskaper i ett diagram med hjälp av Aspose.Words för .NET, och bryter ner varje steg för att säkerställa tydlighet och enkel förståelse.

## Förkunskapskrav

Innan du börjar med kodningen finns det några förutsättningar du behöver ha på plats:

1. Aspose.Words för .NET: Se till att du har biblioteket Aspose.Words för .NET. Du kan [ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du behöver en integrerad utvecklingsmiljö (IDE) som Visual Studio.
3. .NET Framework: Se till att din utvecklingsmiljö är konfigurerad för .NET-utveckling.
4. Grundläggande kunskaper i C#: Den här guiden förutsätter att du har grundläggande förståelse för C#-programmering.

## Importera namnrymder

Till att börja med behöver du importera de nödvändiga namnrymderna i ditt projekt. Detta säkerställer att du har tillgång till alla klasser och metoder som krävs för att skapa och manipulera dokument och diagram.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Vi kommer att dela upp processen i enkla steg, där varje steg fokuserar på en specifik del av att definiera XY-axelns egenskaper i ett diagram.

## Steg 1: Initiera dokumentet och DocumentBuilder

Först måste du initiera ett nytt dokument och en `DocumentBuilder` objektet. Det `DocumentBuilder` hjälper till att infoga innehåll i dokumentet.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga ett diagram

Nästa steg är att infoga ett diagram i dokumentet. I det här exemplet använder vi ett ytdiagram. Du kan anpassa diagrammets dimensioner efter behov.

```csharp
// Infoga diagram
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Steg 3: Rensa standardserien och lägg till anpassade data

Som standard kommer diagrammet att ha några fördefinierade serier. Vi rensar dessa och lägger till våra anpassade dataserier.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Steg 4: Definiera X-axelns egenskaper

Nu är det dags att definiera egenskaperna för X-axeln. Detta inkluderar att ställa in kategorityp, anpassa axelkorsningen och justera skalmarkeringar och etiketter.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Mätt i visningsenheter för Y-axeln (hundratal).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Steg 5: Definiera Y-axelns egenskaper

På samma sätt ställer du in egenskaperna för Y-axeln. Detta inkluderar att ställa in skalmarkörens position, större och mindre enheter, visningsenhet och skalning.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Steg 6: Spara dokumentet

Spara slutligen dokumentet i den angivna katalogen. Detta genererar Word-dokumentet med det anpassade diagrammet.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Slutsats

Att skapa och anpassa diagram i Word-dokument med Aspose.Words för .NET är enkelt när du väl förstår stegen. Den här guiden har guidat dig genom processen att definiera XY-axelegenskaper i ett diagram, från att initiera dokumentet till att spara slutprodukten. Med dessa färdigheter kan du skapa detaljerade, professionellt utseende diagram som förbättrar dina dokument.

## Vanliga frågor

### Vilka typer av diagram kan jag skapa med Aspose.Words för .NET?
Du kan skapa olika typer av diagram, inklusive ytdiagram, stapeldiagram, linjediagram, cirkeldiagram och mer.

### Hur installerar jag Aspose.Words för .NET?
Du kan ladda ner Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/) och följ de medföljande installationsanvisningarna.

### Kan jag anpassa utseendet på mina diagram?
Ja, Aspose.Words för .NET tillåter omfattande anpassning av diagram, inklusive färger, teckensnitt och axelegenskaper.

### Finns det en gratis testversion av Aspose.Words för .NET?
Ja, du kan få en gratis provperiod [här](https://releases.aspose.com/).

### Var kan jag hitta fler handledningar och dokumentation?
Du hittar fler handledningar och detaljerad dokumentation på [Dokumentationssida för Aspose.Words för .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}