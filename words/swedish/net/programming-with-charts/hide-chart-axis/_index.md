---
title: Dölj diagramaxeln i ett Word-dokument
linktitle: Dölj diagramaxeln i ett Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du döljer diagramaxeln i ett Word-dokument med Aspose.Words för .NET med vår detaljerade, steg-för-steg handledning.
weight: 10
url: /sv/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dölj diagramaxeln i ett Word-dokument

## Introduktion

Att skapa dynamiska och visuellt tilltalande Word-dokument innebär ofta att man införlivar diagram och grafer. Ett sådant scenario kan kräva att diagramaxeln döljs för en renare presentation. Aspose.Words för .NET tillhandahåller ett omfattande och lättanvänt API för sådana uppgifter. Denna handledning guidar dig genom stegen för att dölja en diagramaxel i ett Word-dokument med Aspose.Words för .NET.

## Förutsättningar

Innan vi dyker in i handledningen, se till att du har följande förutsättningar:

-  Aspose.Words för .NET: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Alla IDE som stöder .NET-utveckling, till exempel Visual Studio.
- .NET Framework: Se till att du har .NET Framework installerat på din dator.
- Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# kommer att vara fördelaktigt.

## Importera namnområden

För att börja arbeta med Aspose.Words för .NET måste du importera de nödvändiga namnrymden i ditt projekt. Så här kan du göra det:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Låt oss dela upp processen i enkla steg som är lätta att följa.

## Steg 1: Initiera Document and DocumentBuilder

Det första steget innebär att skapa ett nytt Word-dokument och initiera DocumentBuilder-objektet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 I det här steget definierar vi sökvägen där dokumentet ska sparas. Vi skapar sedan en ny`Document` föremål och ett`DocumentBuilder` objekt för att börja bygga vårt dokument.

## Steg 2: Infoga ett diagram

 Därefter kommer vi att infoga ett diagram i dokumentet med hjälp av`DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Här infogar vi ett kolumndiagram med specificerade mått. De`InsertChart` metod returnerar en`Shape` objekt som innehåller diagrammet.

## Steg 3: Rensa befintlig serie

Innan vi lägger till ny data i diagrammet måste vi rensa alla befintliga serier.

```csharp
chart.Series.Clear();
```

Det här steget säkerställer att alla standarddata i diagrammet tas bort, vilket ger plats för de nya data som vi kommer att lägga till härnäst.

## Steg 4: Lägg till seriedata

Låt oss nu lägga till vår egen dataserie i diagrammet.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

I det här steget lägger vi till en serie med titeln "Aspose Series 1" med motsvarande kategorier och värden.

## Steg 5: Göm Y-axeln

 För att dölja diagrammets Y-axel ställer vi helt enkelt in`Hidden` egenskapen för Y-axeln till`true`.

```csharp
chart.AxisY.Hidden = true;
```

Denna kodrad döljer Y-axeln, vilket gör den osynlig i diagrammet.

## Steg 6: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Detta kommando sparar Word-dokumentet med diagrammet till den angivna sökvägen.

## Slutsats

Grattis! Du har framgångsrikt lärt dig hur du döljer en diagramaxel i ett Word-dokument med Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att manipulera Word-dokument programmatiskt. Genom att följa dessa steg kan du skapa anpassade och professionella dokument med minimal ansträngning.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt API för att skapa, redigera, konvertera och manipulera Word-dokument i .NET-applikationer.

### Kan jag dölja både X- och Y-axeln i ett diagram?
 Ja, du kan dölja båda axlarna genom att ställa in`Hidden` bådas egendom`AxisX` och`AxisY` till`true`.

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?
 Ja, du kan få en gratis provperiod[här](https://releases.aspose.com/).

### Var kan jag hitta mer dokumentation?
 Du kan hitta detaljerad dokumentation om Aspose.Words för .NET[här](https://reference.aspose.com/words/net/).

### Hur kan jag få support för Aspose.Words för .NET?
 Du kan få stöd från Aspose-communityt[här](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
