---
title: Formaat Aantal Gegevenslabels In Een Grafiek
linktitle: Formaat Aantal Gegevenslabels In Een Grafiek
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u gegevenslabels in diagrammen kunt opmaken met Aspose.Words voor .NET met deze stapsgewijze handleiding. Verbeter uw Word-documenten moeiteloos.
weight: 10
url: /nl/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formaat Aantal Gegevenslabels In Een Grafiek

## Invoering

Het maken van boeiende en informatieve documenten omvat vaak het opnemen van grafieken met goed geformatteerde gegevenslabels. Als u een .NET-ontwikkelaar bent die uw Word-documenten wilt verbeteren met geavanceerde grafieken, is Aspose.Words voor .NET een fantastische bibliotheek om u daarbij te helpen. Deze tutorial leidt u stap voor stap door het proces van het formatteren van nummerlabels in een grafiek met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat u aan de slag gaat met de code, moet u aan een aantal voorwaarden voldoen:

-  Aspose.Words voor .NET: Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt geïnstalleerd. Als u deze nog niet hebt geïnstalleerd, kunt u[download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: U dient een .NET-ontwikkelomgeving in te stellen. Visual Studio wordt sterk aanbevolen.
- Basiskennis van C#: Kennis van C#-programmering is essentieel, aangezien deze tutorial het schrijven en begrijpen van C#-code inhoudt.
-  Tijdelijke licentie: Om Aspose.Words zonder enige beperking te gebruiken, kunt u een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/).

Laten we nu eens kijken naar het stapsgewijze proces voor het opmaken van nummerlabels in een grafiek.

## Naamruimten importeren

Allereerst moeten we de benodigde naamruimten importeren om te werken met Aspose.Words voor .NET. Voeg de volgende regels toe bovenaan uw C#-bestand:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Stap 1: Stel uw documentenmap in

Voordat u kunt beginnen met het manipuleren van uw Word-document, moet u de directory opgeven waar uw document wordt opgeslagen. Dit is essentieel voor de opslagbewerking later.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw documentenmap.

## Stap 2: Initialiseer het document en DocumentBuilder

 De volgende stap is het initialiseren van een nieuwe`Document` en een`DocumentBuilder` . De`DocumentBuilder` is een hulpklasse waarmee we de inhoud van het document kunnen samenstellen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: Een grafiek in het document invoegen

 Laten we nu een grafiek in het document invoegen met behulp van de`DocumentBuilder`In deze tutorial gebruiken we een lijndiagram als voorbeeld.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Hier voegen we een lijndiagram in met een specifieke breedte en hoogte en stellen we de grafiektitel in.

## Stap 4: Standaardreeks wissen en nieuwe reeks toevoegen

Standaard bevat de grafiek een aantal vooraf gegenereerde series. We moeten deze wissen en onze eigen series met specifieke datapunten toevoegen.

```csharp
// Standaard gegenereerde series verwijderen.
chart.Series.Clear();

// Voeg een nieuwe reeks toe met aangepaste datapunten.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Stap 5: Gegevenslabels inschakelen

Om de gegevenslabels in de grafiek weer te geven, moeten we ze voor onze reeks inschakelen.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Stap 6: Gegevenslabels opmaken

De kern van deze tutorial is het formatteren van de datalabels. We kunnen verschillende nummerformaten toepassen op elk datalabel afzonderlijk.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Valutaformaat
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Datumnotatie
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Percentage-indeling
```

 Bovendien kunt u de opmaak van een gegevenslabel koppelen aan een broncel. Wanneer gekoppeld,`NumberFormat` wordt teruggezet naar algemeen en overgenomen van de broncel.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Stap 7: Sla het document op

Sla het document ten slotte op in de opgegeven map.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Hiermee wordt uw document met de opgegeven naam opgeslagen en blijft uw grafiek met opgemaakte gegevenslabels behouden.

## Conclusie

Het formatteren van gegevenslabels in een diagram met Aspose.Words voor .NET kan de leesbaarheid en professionaliteit van uw Word-documenten aanzienlijk verbeteren. Door deze stapsgewijze handleiding te volgen, zou u nu een diagram moeten kunnen maken, gegevensreeksen moeten kunnen toevoegen en de gegevenslabels moeten kunnen formatteren om aan uw behoeften te voldoen. Aspose.Words voor .NET is een krachtige tool die uitgebreide aanpassing en automatisering van Word-documenten mogelijk maakt, waardoor het een onschatbare hulpbron is voor .NET-ontwikkelaars.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch maken, bewerken en converteren van Word-documenten met behulp van C#.

### Kan ik andere soorten grafieken opmaken met Aspose.Words voor .NET?
Ja, Aspose.Words voor .NET ondersteunt verschillende grafiektypen, waaronder staaf-, kolom-, cirkeldiagrammen en meer.

### Hoe krijg ik een tijdelijke licentie voor Aspose.Words voor .NET?
 kunt een tijdelijke licentie verkrijgen[hier](https://purchase.aspose.com/temporary-license/).

### Is het mogelijk om gegevenslabels te koppelen aan broncellen in Excel?
Ja, u kunt gegevenslabels koppelen aan broncellen, zodat de getalnotatie van de broncel kan worden overgenomen.

### Waar kan ik meer gedetailleerde documentatie vinden voor Aspose.Words voor .NET?
 U kunt uitgebreide documentatie vinden[hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
