---
title: Gebiedsdiagram invoegen in een Word-document
linktitle: Gebiedsdiagram invoegen in een Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een vlakdiagram in een document invoegt met Aspose.Words voor .NET. Voeg reeksgegevens toe en sla het document met het diagram op.
weight: 10
url: /nl/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gebiedsdiagram invoegen in een Word-document

## Invoering

Welkom bij deze stapsgewijze handleiding over het invoegen van een vlakdiagram in een Word-document met Aspose.Words voor .NET. Of u nu een doorgewinterde ontwikkelaar bent of net begint, deze tutorial leidt u door alles wat u moet weten om verbluffende en informatieve vlakdiagrammen te maken in uw Word-documenten. We behandelen de vereisten, laten u zien hoe u de benodigde naamruimten importeert en begeleiden u door elke stap van het proces met duidelijke, eenvoudig te volgen instructies.

## Vereisten

Voordat we beginnen, willen we er zeker van zijn dat u alles bij de hand hebt om te beginnen:

1.  Aspose.Words voor .NET: Zorg ervoor dat je Aspose.Words voor .NET hebt geïnstalleerd. Je kunt het downloaden[hier](https://releases.aspose.com/words/net/).
2. .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
3. IDE: Een Integrated Development Environment (IDE) zoals Visual Studio om uw code te schrijven en uit te voeren.
4. Basiskennis van C#: Een basiskennis van C#-programmering is nuttig.

Zodra u aan deze vereisten voldoet, kunt u beginnen met het maken van prachtige vlakdiagrammen in uw Word-documenten.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze naamruimten bieden de klassen en methoden die nodig zijn om met Word-documenten en grafieken te werken in Aspose.Words voor .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Nu we de essentiële naamruimten hebben geïmporteerd, gaan we verder met het maken van ons document en het stapsgewijs invoegen van een vlakdiagram.

## Stap 1: Maak een nieuw Word-document

Laten we beginnen met het maken van een nieuw Word-document. Dit wordt de basis waar we ons gebiedsdiagram invoegen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 In deze stap initialiseren we een nieuwe`Document` object dat ons Word-document vertegenwoordigt.

## Stap 2: Gebruik DocumentBuilder om een grafiek in te voegen

 Vervolgens gebruiken we de`DocumentBuilder` klasse om een vlakdiagram in ons document in te voegen.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

 Hier creëren we een`DocumentBuilder` object en gebruik het om een gebiedsdiagram met specifieke afmetingen (432x252) in ons document in te voegen.

## Stap 3: Toegang tot het grafiekobject

 Nadat we de grafiek hebben ingevoegd, moeten we toegang krijgen tot de`Chart` object om ons vlakdiagram aan te passen.

```csharp
Chart chart = shape.Chart;
```

 Deze regel code haalt de`Chart` object uit de vorm die we zojuist hebben ingevoegd.

## Stap 4: Voeg seriegegevens toe aan de grafiek

Nu is het tijd om wat data toe te voegen aan onze grafiek. We voegen een serie toe met data en bijbehorende waarden.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

In deze stap voegen we een reeks toe met de naam 'Aspose Series 1' met een set datums en bijbehorende waarden.

## Stap 5: Sla het document op

Ten slotte slaan we ons document op met het ingevoegde vlakdiagram.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Met deze coderegel wordt het document opgeslagen in de opgegeven map met de opgegeven bestandsnaam.

## Conclusie

Gefeliciteerd! U hebt met succes een vlakdiagram ingevoegd in een Word-document met Aspose.Words voor .NET. Deze handleiding heeft u door elke stap geleid, van het instellen van uw omgeving tot het opslaan van het uiteindelijke document. Met Aspose.Words voor .NET kunt u een grote verscheidenheid aan diagrammen en andere complexe elementen in uw Word-documenten maken, waardoor uw rapporten en presentaties dynamischer en informatiever worden.

## Veelgestelde vragen

### Kan ik Aspose.Words voor .NET gebruiken met andere .NET-talen?
Ja, Aspose.Words voor .NET ondersteunt andere .NET-talen, zoals VB.NET.

### Is het mogelijk om het uiterlijk van de grafiek aan te passen?
Absoluut! Aspose.Words voor .NET biedt uitgebreide opties om het uiterlijk van uw grafieken aan te passen.

### Kan ik meerdere grafieken aan één Word-document toevoegen?
Ja, u kunt zoveel grafieken in één Word-document invoegen als u nodig hebt.

### Ondersteunt Aspose.Words voor .NET andere grafiektypen?
Ja, Aspose.Words voor .NET ondersteunt verschillende grafiektypen, waaronder staaf-, lijn-, cirkeldiagrammen en meer.

### Waar kan ik een tijdelijke licentie voor Aspose.Words voor .NET krijgen?
 U kunt een tijdelijke vergunning verkrijgen bij[hier](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
