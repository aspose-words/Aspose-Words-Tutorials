---
"description": "Leer hoe u datum- en tijdwaarden toevoegt aan de assen van een grafiek met behulp van Aspose.Words voor .NET in deze uitgebreide stapsgewijze handleiding."
"linktitle": "Datum- en tijdwaarden toevoegen aan de as van een grafiek"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Datum- en tijdwaarden toevoegen aan de as van een grafiek"
"url": "/nl/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Datum- en tijdwaarden toevoegen aan de as van een grafiek

## Invoering

Het maken van grafieken in documenten kan een krachtige manier zijn om gegevens te visualiseren. Bij het werken met tijdreeksgegevens is het toevoegen van datum- en tijdwaarden aan de assen van een grafiek cruciaal voor de duidelijkheid. In deze tutorial leiden we je door het proces van het toevoegen van datum- en tijdwaarden aan de assen van een grafiek met behulp van Aspose.Words voor .NET. Deze stapsgewijze handleiding helpt je bij het opzetten van je omgeving, het schrijven van de code en het begrijpen van elk onderdeel van het proces. Laten we beginnen!

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende voorwaarden voldoet:

1. Visual Studio of een andere .NET IDE: U hebt een ontwikkelomgeving nodig om uw .NET-code te schrijven en uit te voeren.
2. Aspose.Words voor .NET: U moet de Aspose.Words voor .NET-bibliotheek geïnstalleerd hebben. U kunt deze downloaden van [hier](https://releases.aspose.com/words/net/).
3. Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u een basiskennis hebt van C#-programmering.
4. Een geldige Aspose-licentie: U kunt een tijdelijke licentie verkrijgen bij [hier](https://purchase.aspose.com/temporary-license/).

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde naamruimten in uw project hebt geïmporteerd. Deze stap is cruciaal voor toegang tot de Aspose.Words-klassen en -methoden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Stap 1: Stel uw documentenmap in

Eerst moet je de directory definiëren waar je document wordt opgeslagen. Dit is belangrijk voor het ordenen van je bestanden en het correct uitvoeren van je code.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Maak een nieuw document en DocumentBuilder

Maak vervolgens een nieuw exemplaar van de `Document` klasse en een `DocumentBuilder` object. Deze objecten helpen u bij het samenstellen en bewerken van uw document.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: Een grafiek in het document invoegen

Voeg nu een grafiek in uw document in met behulp van de `DocumentBuilder` object. In dit voorbeeld gebruiken we een kolomdiagram, maar u kunt ook andere typen kiezen.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Stap 4: Bestaande series wissen

Verwijder alle bestaande reeksen in de grafiek om ervoor te zorgen dat u met een schone lei begint. Deze stap is essentieel voor aangepaste gegevens.

```csharp
chart.Series.Clear();
```

## Stap 5: Datum- en tijdwaarden toevoegen aan de reeks

Voeg uw datum- en tijdwaarden toe aan de grafiekreeks. Deze stap omvat het maken van arrays voor datums en bijbehorende waarden.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Stap 6: De X-as configureren

Stel de schaal en de vinkjes voor de X-as in. Zo worden uw datums correct en met de juiste tussenpozen weergegeven.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Stap 7: Sla het document op

Sla ten slotte uw document op in de opgegeven directory. Deze stap rondt het proces af en uw document zou nu een grafiek moeten bevatten met datum- en tijdwaarden op de X-as.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Conclusie

Het toevoegen van datum- en tijdwaarden aan de assen van een grafiek in een document is een eenvoudig proces met Aspose.Words voor .NET. Door de stappen in deze tutorial te volgen, kunt u duidelijke en informatieve grafieken maken die tijdreeksgegevens effectief visualiseren. Of u nu rapporten, presentaties of een document voorbereidt dat gedetailleerde gegevensrepresentatie vereist, Aspose.Words biedt de tools die u nodig hebt om te slagen.

## Veelgestelde vragen

### Kan ik andere grafiektypen gebruiken met Aspose.Words voor .NET?

Ja, Aspose.Words ondersteunt verschillende grafiektypen, waaronder lijn-, staaf-, cirkel- en meer.

### Hoe kan ik het uiterlijk van mijn grafiek aanpassen?

U kunt het uiterlijk aanpassen door de eigenschappen van het diagram te openen en stijlen, kleuren en meer in te stellen.

### Is het mogelijk om meerdere reeksen aan een grafiek toe te voegen?

Absoluut! U kunt meerdere reeksen aan uw grafiek toevoegen door de `Series.Add` methode meerdere keren met verschillende gegevens uitvoeren.

### Wat als ik de grafiekgegevens dynamisch wil bijwerken?

U kunt de grafiekgegevens dynamisch bijwerken door de reeks- en aseigenschappen programmatisch te manipuleren op basis van uw vereisten.

### Waar kan ik meer gedetailleerde documentatie vinden voor Aspose.Words voor .NET?

Meer gedetailleerde documentatie vindt u hier [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}