---
title: Pas een enkel grafiekgegevenspunt in een grafiek aan
linktitle: Pas een enkel grafiekgegevenspunt in een grafiek aan
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u afzonderlijke diagramgegevenspunten kunt aanpassen met Aspose.Words voor .NET in een gedetailleerde stapsgewijze handleiding. Verbeter uw diagrammen met unieke markeringen en formaten.
weight: 10
url: /nl/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pas een enkel grafiekgegevenspunt in een grafiek aan

## Invoering

Heb je je ooit afgevraagd hoe je je grafieken kunt laten opvallen met unieke datapunten? Nou, vandaag is je geluksdag! We duiken in het aanpassen van een enkel diagramdatapunt met Aspose.Words voor .NET. Maak je klaar voor een rit door een stapsgewijze tutorial die niet alleen informatief is, maar ook leuk en gemakkelijk te volgen.

## Vereisten

Voordat we beginnen, willen we ervoor zorgen dat u alle essentiële zaken op orde heeft:

-  Aspose.Words voor .NET-bibliotheek: zorg ervoor dat u de nieuwste versie hebt.[Download het hier](https://releases.aspose.com/words/net/).
- .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
- Basiskennis van C#: Een basiskennis van C#-programmering is nuttig.
- Integrated Development Environment (IDE): Visual Studio wordt aanbevolen.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren om aan de slag te gaan:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Stap 1: Initialiseer het document en DocumentBuilder

Oké, laten we beginnen met het initialiseren van een nieuw document en een DocumentBuilder. Dit wordt het canvas voor onze grafiek.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier,`dataDir` is het directorypad waar u uw document opslaat. De`DocumentBuilder` klasse helpt bij het samenstellen van het document.

## Stap 2: Een grafiek invoegen

Laten we nu een lijndiagram in het document invoegen. Dit wordt onze speeltuin voor het aanpassen van datapunten.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 De`InsertChart` methode neemt het grafiektype, de breedte en de hoogte als parameters. In dit geval voegen we een lijndiagram in met een breedte van 432 en een hoogte van 252.

## Stap 3: Toegang tot grafiekreeksen

Nu is het tijd om de series binnen onze grafiek te benaderen. Een grafiek kan meerdere series hebben en elke serie bevat datapunten.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Hier bekijken we de eerste twee reeksen in onze grafiek. 

## Stap 4: Datapunten aanpassen

Hier gebeurt de magie! Laten we specifieke datapunten binnen onze serie aanpassen.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

We halen de datapunten op uit de eerste serie. Laten we deze punten nu aanpassen.

### Gegevenspunt 00 aanpassen

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Voor`dataPoint00`, we stellen een explosie in (handig voor cirkeldiagrammen), veranderen het markeringssymbool in een cirkel en stellen de markeringsgrootte in op 15.

### Gegevenspunt 01 aanpassen

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Voor`dataPoint01`, veranderen we het markeringssymbool in een ruit en stellen we de markeringsgrootte in op 20.

### Pas gegevenspunt in serie 1 aan

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 Voor het derde gegevenspunt in`series1`, we stellen het zo in dat het wordt omgekeerd als de waarde negatief is, we veranderen het markeringssymbool in een ster en we stellen de markeringsgrootte in op 20.

## Stap 5: Sla het document op

Laten we ten slotte ons document met alle aanpassingen opslaan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Deze regel slaat het document op in de door u opgegeven map met de naam`WorkingWithCharts.SingleChartDataPoint.docx`.

## Conclusie

En daar heb je het! Je hebt met succes individuele datapunten in een diagram aangepast met Aspose.Words voor .NET. Door een paar eigenschappen aan te passen, kun je je diagrammen veel informatiever en visueel aantrekkelijker maken. Experimenteer dus met verschillende markeringen en formaten om te zien wat het beste werkt voor jouw gegevens.

## Veelgestelde vragen

### Kan ik datapunten in andere soorten diagrammen aanpassen?

Absoluut! U kunt datapunten aanpassen in verschillende grafiektypen, waaronder staafdiagrammen, cirkeldiagrammen en meer. Het proces is vergelijkbaar voor verschillende grafiektypen.

### Is het mogelijk om aangepaste labels aan datapunten toe te voegen?

 Ja, u kunt aangepaste labels toevoegen aan datapunten met behulp van de`ChartDataPoint.Label` eigenschap. Hiermee kunt u meer context bieden voor elk gegevenspunt.

### Hoe kan ik een gegevenspunt uit een reeks verwijderen?

 U kunt een gegevenspunt verwijderen door de zichtbaarheid ervan op onwaar in te stellen met behulp van`dataPoint.IsVisible = false`.

### Kan ik afbeeldingen gebruiken als markeringen voor datapunten?

Hoewel Aspose.Words het niet ondersteunt om afbeeldingen rechtstreeks als markeringen te gebruiken, kunt u wel aangepaste vormen maken en deze als markeringen gebruiken.

### Is het mogelijk om datapunten in de grafiek te animeren?

Aspose.Words voor .NET ondersteunt geen animatie voor diagramgegevenspunten. U kunt echter wel geanimeerde diagrammen maken met andere hulpmiddelen en deze in uw Word-documenten insluiten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
