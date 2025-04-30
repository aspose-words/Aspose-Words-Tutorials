---
"description": "Leer hoe u gegevenslabels in grafieken opmaakt met Aspose.Words voor .NET met deze stapsgewijze handleiding. Verbeter uw Word-documenten moeiteloos."
"linktitle": "Formaat van het aantal gegevenslabels in een grafiek"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Formaat van het aantal gegevenslabels in een grafiek"
"url": "/nl/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formaat van het aantal gegevenslabels in een grafiek

## Invoering

Het maken van boeiende en informatieve documenten vereist vaak het toevoegen van grafieken met goed opgemaakte gegevenslabels. Bent u een .NET-ontwikkelaar die uw Word-documenten wilt uitbreiden met geavanceerde grafieken? Aspose.Words voor .NET is een fantastische bibliotheek om u daarbij te helpen. Deze tutorial leidt u stap voor stap door het proces van het opmaken van numerieke labels in een grafiek met Aspose.Words voor .NET.

## Vereisten

Voordat u aan de slag gaat met de code, moet u aan een aantal voorwaarden voldoen:

- Aspose.Words voor .NET: Zorg ervoor dat de Aspose.Words voor .NET-bibliotheek is geïnstalleerd. Als u deze nog niet hebt geïnstalleerd, kunt u dit doen. [download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: U dient een .NET-ontwikkelomgeving te hebben. Visual Studio wordt sterk aanbevolen.
- Basiskennis van C#: Kennis van C#-programmering is essentieel, aangezien deze tutorial het schrijven en begrijpen van C#-code inhoudt.
- Tijdelijke licentie: Om Aspose.Words zonder enige beperking te gebruiken, kunt u een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/).

Laten we nu stap voor stap dieper ingaan op het opmaken van nummerlabels in een diagram.

## Naamruimten importeren

Allereerst moeten we de benodigde naamruimten importeren om met Aspose.Words voor .NET te kunnen werken. Voeg de volgende regels bovenaan je C#-bestand toe:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Stap 1: Stel uw documentenmap in

Voordat u uw Word-document kunt bewerken, moet u de map opgeven waar uw document wordt opgeslagen. Dit is essentieel voor de latere opslagbewerking.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw documentenmap.

## Stap 2: Initialiseer het document en de DocumentBuilder

De volgende stap is het initialiseren van een nieuwe `Document` en een `DocumentBuilder`. De `DocumentBuilder` is een hulpklasse waarmee we de inhoud van het document kunnen construeren.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: Een grafiek in het document invoegen

Laten we nu een grafiek in het document invoegen met behulp van de `DocumentBuilder`In deze tutorial gebruiken we een lijndiagram als voorbeeld.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Hier voegen we een lijndiagram in met een specifieke breedte en hoogte en stellen we de grafiektitel in.

## Stap 4: Standaardreeks wissen en nieuwe reeks toevoegen

Standaard bevat de grafiek een aantal vooraf gegenereerde reeksen. We moeten deze wissen en onze eigen reeksen met specifieke datapunten toevoegen.

```csharp
// Verwijder standaard gegenereerde series.
chart.Series.Clear();

// Voeg een nieuwe reeks toe met aangepaste datapunten.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Stap 5: Gegevenslabels inschakelen

Om de gegevenslabels in het diagram weer te geven, moeten we ze voor onze reeks inschakelen.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Stap 6: Gegevenslabels opmaken

De kern van deze tutorial is het opmaken van de gegevenslabels. We kunnen verschillende getalnotaties toepassen op elk afzonderlijk gegevenslabel.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Valutaformaat
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Datumnotatie
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Percentage-indeling
```

Bovendien kunt u de opmaak van een gegevenslabel koppelen aan een broncel. Wanneer deze gekoppeld is, `NumberFormat` wordt teruggezet naar algemeen en overgenomen van de broncel.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Stap 7: Sla het document op

Sla het document ten slotte op in de opgegeven directory.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Hiermee wordt uw document met de opgegeven naam opgeslagen en blijft uw grafiek met opgemaakte gegevenslabels behouden.

## Conclusie

Het opmaken van gegevenslabels in een grafiek met Aspose.Words voor .NET kan de leesbaarheid en professionaliteit van uw Word-documenten aanzienlijk verbeteren. Door deze stapsgewijze handleiding te volgen, zou u nu een grafiek moeten kunnen maken, gegevensreeksen moeten kunnen toevoegen en de gegevenslabels naar wens kunnen opmaken. Aspose.Words voor .NET is een krachtige tool die uitgebreide aanpassing en automatisering van Word-documenten mogelijk maakt, waardoor het een onmisbare tool is voor .NET-ontwikkelaars.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch maken, bewerken en converteren van Word-documenten met behulp van C#.

### Kan ik andere soorten grafieken opmaken met Aspose.Words voor .NET?
Ja, Aspose.Words voor .NET ondersteunt verschillende diagramtypen, waaronder staaf-, kolom-, cirkeldiagrammen en meer.

### Hoe krijg ik een tijdelijke licentie voor Aspose.Words voor .NET?
U kunt een tijdelijke licentie verkrijgen [hier](https://purchase.aspose.com/temporary-license/).

### Is het mogelijk om gegevenslabels te koppelen aan broncellen in Excel?
Ja, u kunt gegevenslabels koppelen aan broncellen, zodat de getalnotatie van de broncel kan worden overgenomen.

### Waar kan ik meer gedetailleerde documentatie vinden voor Aspose.Words voor .NET?
U kunt uitgebreide documentatie vinden [hier](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}