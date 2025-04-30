---
"description": "Leer hoe u standaardopties voor gegevenslabels in een grafiek instelt met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding om moeiteloos grafieken te maken en aan te passen."
"linktitle": "Standaardopties instellen voor gegevenslabels in een grafiek"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Standaardopties instellen voor gegevenslabels in een grafiek"
"url": "/nl/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Standaardopties instellen voor gegevenslabels in een grafiek

## Invoering

Hallo! Ben je enthousiast om de wereld van documentautomatisering in te duiken? Vandaag gaan we onderzoeken hoe je Aspose.Words voor .NET kunt gebruiken om programmatisch prachtige documenten te maken. Aspose.Words is een krachtige bibliotheek waarmee je Word-documenten eenvoudig kunt bewerken. In deze tutorial richten we ons op het instellen van standaardopties voor gegevenslabels in een grafiek. Of je nu een ervaren ontwikkelaar bent of een beginner, deze handleiding leidt je door elke stap, zodat je in een mum van tijd aan de slag kunt.

## Vereisten

Voordat we beginnen, zorgen we ervoor dat je alles hebt wat je nodig hebt om deze tutorial te volgen. Hier is een korte checklist:

- Visual Studio of een andere .NET-compatibele IDE: dit is de plek waar u uw code schrijft en uitvoert.
- Aspose.Words voor .NET: Je kunt [download de nieuwste versie](https://releases.aspose.com/words/net/) en installeer het in uw project.
- Basiskennis van C#-programmering: Hoewel deze gids geschikt is voor beginners, is een beetje kennis van C# nuttig.
- .NET Framework geïnstalleerd: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
- Een tijdelijke licentie voor Aspose. Woorden: Koop er een [hier](https://purchase.aspose.com/temporary-license/) om de volledige functionaliteit te ontgrendelen.

Zodra je aan deze voorwaarden hebt voldaan, zijn we klaar voor de start!

## Naamruimten importeren

Laten we eerst ons project opzetten en de benodigde naamruimten importeren. Deze naamruimten zijn cruciaal voor toegang tot de Aspose.Words-functionaliteit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Stap 1: Een nieuw document maken


De reis begint met het maken van een nieuw document en het initialiseren van een `DocumentBuilder`. De `DocumentBuilder` klasse biedt een set methoden om de inhoud van het document eenvoudig te manipuleren.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Een nieuw document maken
Document doc = new Document();

// DocumentBuilder initialiseren
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Uitleg

In deze stap hebben we het document en de builder ingesteld die we zullen gebruiken om onze inhoud in te voegen en op te maken. `dataDir` variabele bevat het pad waar we ons definitieve document opslaan.

## Stap 2: Een grafiek invoegen

Vervolgens voegen we een cirkeldiagram toe aan ons document. `InsertChart` methode van de `DocumentBuilder` klasse maakt dit supergemakkelijk.

```csharp
// Een cirkeldiagram invoegen
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Toegang tot het grafiekobject
Chart chart = shape.Chart;
```

### Uitleg

Hier voegen we een cirkeldiagram in ons document in. `InsertChart` De methode vereist het grafiektype, de breedte en de hoogte als parameters. Nadat we de grafiek hebben ingevoegd, hebben we toegang tot het grafiekobject om deze verder te bewerken.

## Stap 3: Pas de grafiekserie aan

Nu wissen we alle bestaande reeksen in de grafiek en voegen we onze eigen reeks toe. Deze reeks vertegenwoordigt onze datapunten.

```csharp
// Bestaande grafiekreeksen wissen
chart.Series.Clear();

// Nieuwe series toevoegen aan de grafiek
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Uitleg

In deze stap zorgen we ervoor dat onze grafiek leeg is door alle bestaande reeksen te wissen. Vervolgens voegen we een nieuwe reeks toe met aangepaste categorieën en waarden, die in onze cirkeldiagram worden weergegeven.

## Stap 4: Standaardopties voor gegevenslabels instellen

Gegevenslabels zijn cruciaal om uw grafiek informatief te maken. We stellen opties in om percentages en waarden weer te geven en het scheidingsteken aan te passen.

```csharp
// Toegang tot de verzameling gegevenslabels
ChartDataLabelCollection labels = series.DataLabels;

// Opties voor gegevenslabels instellen
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Uitleg

Hier hebben we toegang tot de `DataLabels` Eigenschap van onze serie om de weergave en informatie op elk gegevenslabel aan te passen. We hebben ervoor gekozen om zowel het percentage als de waarde weer te geven, aanhaallijnen te verbergen en een aangepaste scheidingsteken in te stellen.

## Stap 5: Sla het document op

Ten slotte slaan we ons document op in de opgegeven directory. Deze stap zorgt ervoor dat al onze wijzigingen naar een bestand worden geschreven.

```csharp
// Sla het document op
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Uitleg

In deze laatste stap slaan we ons document op met behulp van de `Save` methode. Het document wordt opgeslagen in de map die is opgegeven door `dataDir`, met de naam "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Conclusie

En voilà! Je hebt met succes een Word-document met een aangepast cirkeldiagram gemaakt met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het eenvoudig om het maken en bewerken van documenten te automatiseren, wat je tijd en moeite bespaart. Of je nu rapporten, facturen of andere soorten documenten genereert, Aspose.Words staat voor je klaar.

Voel je vrij om de [Aspose.Words-documentatie](https://reference.aspose.com/words/net/) voor meer functies en voorbeelden. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik Aspose.Words gratis gebruiken?
U kunt Aspose.Words gratis gebruiken met een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) of verken de functies ervan met behulp van de [gratis proefperiode](https://releases.aspose.com/).

### Hoe krijg ik ondersteuning voor Aspose.Words?
U kunt ondersteuning krijgen via de [Aspose.Words ondersteuningsforum](https://forum.aspose.com/c/words/8).

### Kan ik andere soorten grafieken toevoegen?
Ja, Aspose.Words ondersteunt verschillende grafiektypen, zoals staaf-, lijn- en kolomdiagrammen. Controleer de [documentatie](https://reference.aspose.com/words/net/) voor meer details.

### Is Aspose.Words compatibel met .NET Core?
Ja, Aspose.Words is compatibel met .NET Core. Meer informatie vindt u in de [documentatie](https://reference.aspose.com/words/net/).

### Hoe kan ik een licentie voor Aspose.Words aanschaffen?
U kunt een licentie kopen bij de [Aspose-winkel](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}