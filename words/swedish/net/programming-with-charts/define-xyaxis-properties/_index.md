---
title: Definiera XY-axelegenskaper i ett diagram
linktitle: Definiera XY-axelegenskaper i ett diagram
second_title: Aspose.Words Document Processing API
description: Lär dig hur du definierar XY-axelegenskaper i ett diagram med Aspose.Words för .NET med denna steg-för-steg-guide. Perfekt för .NET-utvecklare.
weight: 10
url: /sv/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definiera XY-axelegenskaper i ett diagram

## Introduktion

Diagram är ett kraftfullt verktyg för att visualisera data. När du behöver skapa professionella dokument med dynamiska diagram är Aspose.Words för .NET ett ovärderligt bibliotek. Den här artikeln kommer att leda dig genom processen att definiera XY-axelegenskaper i ett diagram med Aspose.Words för .NET, och bryta ner varje steg för att säkerställa klarhet och enkel förståelse.

## Förutsättningar

Innan du dyker in i kodningen finns det några förutsättningar du måste ha på plats:

1. Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket. Du kan[ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du behöver en integrerad utvecklingsmiljö (IDE) som Visual Studio.
3. .NET Framework: Se till att din utvecklingsmiljö är inställd för .NET-utveckling.
4. Grundläggande kunskaper om C#: Den här guiden förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnområden

Till att börja med måste du importera de nödvändiga namnrymden i ditt projekt. Detta säkerställer att du har tillgång till alla klasser och metoder som krävs för att skapa och manipulera dokument och diagram.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Vi kommer att dela upp processen i enkla steg, var och en fokuserar på en specifik del av att definiera XY-axelns egenskaper i ett diagram.

## Steg 1: Initiera Document and DocumentBuilder

 Först måste du initiera ett nytt dokument och ett`DocumentBuilder` objekt. De`DocumentBuilder` hjälper till att infoga innehåll i dokumentet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga ett diagram

Därefter infogar du ett diagram i dokumentet. I det här exemplet använder vi ett områdesdiagram. Du kan anpassa måtten på diagrammet efter behov.

```csharp
// Infoga diagram
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Steg 3: Rensa standardserier och lägg till anpassade data

Som standard kommer diagrammet att ha några fördefinierade serier. Vi rensar dessa och lägger till vår anpassade dataserie.

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

Nu är det dags att definiera egenskaperna för X-axeln. Detta inkluderar att ställa in kategoritypen, anpassa axelkorsningen och justera bockmarkeringar och etiketter.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //Mätt i displayenheter för Y-axeln (hundratals).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Steg 5: Definiera Y-axelns egenskaper

På samma sätt kommer du att ställa in egenskaperna för Y-axeln. Detta inkluderar inställning av bocketikettens position, större och mindre enheter, displayenhet och skalning.

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

Slutligen, spara dokumentet i din angivna katalog. Detta kommer att generera Word-dokumentet med det anpassade diagrammet.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Slutsats

Att skapa och anpassa diagram i Word-dokument med Aspose.Words för .NET är enkelt när du förstår stegen. Den här guiden har lett dig genom processen att definiera XY-axelegenskaper i ett diagram, från initialisering av dokumentet till att spara den slutliga produkten. Med dessa färdigheter kan du skapa detaljerade, professionellt utseende diagram som förbättrar dina dokument.

## FAQ's

### Vilka typer av diagram kan jag skapa med Aspose.Words för .NET?
Du kan skapa olika typer av diagram, inklusive område, stapel, linje, cirkel och mer.

### Hur installerar jag Aspose.Words för .NET?
 Du kan ladda ner Aspose.Words för .NET från[här](https://releases.aspose.com/words/net/)och följ installationsanvisningarna.

### Kan jag anpassa utseendet på mina diagram?
Ja, Aspose.Words för .NET tillåter omfattande anpassning av diagram, inklusive färger, teckensnitt och axelegenskaper.

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?
 Ja, du kan få en gratis provperiod[här](https://releases.aspose.com/).

### Var kan jag hitta fler handledningar och dokumentation?
 Du kan hitta fler handledningar och detaljerad dokumentation på[Aspose.Words för .NET dokumentationssida](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
