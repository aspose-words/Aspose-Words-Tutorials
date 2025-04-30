---
"description": "Leer hoe u tabellen met absolute, relatieve en automatische breedte-instellingen maakt in Aspose.Words voor .NET met deze stapsgewijze handleiding."
"linktitle": "Voorkeursbreedte-instellingen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Voorkeursbreedte-instellingen"
"url": "/nl/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voorkeursbreedte-instellingen

## Invoering

Tabellen zijn een krachtige manier om informatie in uw Word-documenten te ordenen en te presenteren. Wanneer u met tabellen werkt in Aspose.Words voor .NET, hebt u verschillende opties om de breedte van tabelcellen in te stellen, zodat ze perfect aansluiten op de lay-out van uw document. Deze handleiding begeleidt u bij het maken van tabellen met de gewenste breedte-instellingen in Aspose.Words voor .NET, met de nadruk op absolute, relatieve en automatische formaatopties. 

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u het volgende hebt:

1. Aspose.Words voor .NET: Zorg ervoor dat Aspose.Words voor .NET in uw ontwikkelomgeving is geïnstalleerd. U kunt het downloaden. [hier](https://releases.aspose.com/words/net/).

2. .NET-ontwikkelomgeving: Zorg dat u een .NET-ontwikkelomgeving instelt, zoals Visual Studio.

3. Basiskennis van C#: Kennis van C#-programmering helpt u de codefragmenten en voorbeelden beter te begrijpen.

4. Aspose.Words-documentatie: Raadpleeg de [Aspose.Words-documentatie](https://reference.aspose.com/words/net/) voor gedetailleerde API-informatie en verdere lectuur.

## Naamruimten importeren

Voordat u begint met coderen, moet u de benodigde naamruimten in uw C#-project importeren:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Deze naamruimten bieden toegang tot de kernfunctionaliteiten van Aspose.Words en het Table-object, zodat u documenttabellen kunt bewerken.

Laten we het proces voor het maken van een tabel met verschillende voorkeursbreedte-instellingen opsplitsen in duidelijke, beheersbare stappen.

## Stap 1: Initialiseer het document en de DocumentBuilder

Kop: Een nieuw document en DocumentBuilder maken

Uitleg: Begin met het maken van een nieuw Word-document en een `DocumentBuilder` bijvoorbeeld. De `DocumentBuilder` klasse biedt een eenvoudige manier om inhoud aan uw document toe te voegen.

```csharp
// Definieer het pad om het document op te slaan.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Maak een nieuw document.
Document doc = new Document();

// Maak een DocumentBuilder voor dit document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier geeft u de map op waar het document wordt opgeslagen en initialiseert u de `Document` En `DocumentBuilder` objecten.

## Stap 2: Voeg de eerste tabelcel in met absolute breedte

Voeg de eerste cel in de tabel in met een vaste breedte van 40 punten. Dit zorgt ervoor dat deze cel altijd een breedte van 40 punten behoudt, ongeacht de tabelgrootte.

```csharp
// Voeg een cel van absolute grootte in.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In deze stap begint u met het maken van de tabel en voegt u een cel met een absolute breedte in. `PreferredWidth.FromPoints(40)` methode stelt de breedte van de cel in op 40 punten, en `Shading.BackgroundPatternColor` past een lichtgele achtergrondkleur toe.

## Stap 3: Voeg een cel van relatieve grootte in

Voeg een andere cel in met een breedte die 20% van de totale breedte van de tabel bedraagt. Deze relatieve grootte zorgt ervoor dat de cel zich proportioneel aanpast aan de breedte van de tabel.

```csharp
// Voeg een cel met relatieve (procent) grootte in.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

De breedte van deze cel bedraagt 20% van de totale breedte van de tabel, waardoor de cel kan worden aangepast aan verschillende schermformaten of documentindelingen.

### Stap 4: Een automatisch aangepaste cel invoegen

Voeg ten slotte een cel in waarvan de grootte automatisch wordt aangepast op basis van de resterende beschikbare ruimte in de tabel.

```csharp
// Voeg een cel in die automatisch de juiste grootte heeft.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. De size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` Met deze instelling kan deze cel groter of kleiner worden, afhankelijk van de ruimte die overblijft nadat de andere cellen zijn berekend. Dit zorgt ervoor dat de tabelindeling er evenwichtig en professioneel uitziet.

## Stap 5: Het document afronden en opslaan

Nadat u alle cellen hebt ingevoegd, maakt u de tabel af en slaat u het document op in het door u opgegeven pad.

```csharp
// Sla het document op.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Met deze stap wordt de tabel gefinaliseerd en wordt het document opgeslagen met de bestandsnaam "WorkingWithTables.PreferredWidthSettings.docx" in de door u aangewezen map.

## Conclusie

Het maken van tabellen met gewenste breedte-instellingen in Aspose.Words voor .NET is eenvoudig zodra u de verschillende beschikbare opties voor formaatbepaling begrijpt. Of u nu vaste, relatieve of automatische celbreedtes nodig hebt, Aspose.Words biedt de flexibiliteit om verschillende tabelindelingen efficiënt af te handelen. Door de stappen in deze handleiding te volgen, kunt u ervoor zorgen dat uw tabellen goed gestructureerd en visueel aantrekkelijk zijn in uw Word-documenten.

## Veelgestelde vragen

### Wat is het verschil tussen absolute en relatieve celbreedtes?
Absolute celbreedtes zijn vast en veranderen niet, terwijl relatieve breedtes worden aangepast op basis van de totale breedte van de tabel.

### Kan ik negatieve percentages gebruiken voor relatieve breedtes?
Nee, negatieve percentages zijn niet geldig voor celbreedtes. Alleen positieve percentages zijn toegestaan.

### Hoe werkt de functie voor automatisch aanpassen van het formaat?
Met automatische aanpassing van de grootte wordt de breedte van de cel aangepast, zodat de resterende ruimte in de tabel wordt opgevuld nadat de grootte van andere cellen is aangepast.

### Kan ik verschillende stijlen toepassen op cellen met verschillende breedte-instellingen?
Ja, u kunt verschillende stijlen en opmaak toepassen op cellen, ongeacht hun breedte-instellingen.

### Wat gebeurt er als de totale breedte van de tabel kleiner is dan de som van alle celbreedtes?
De tabel past de breedte van de cellen automatisch aan zodat deze binnen de beschikbare ruimte passen. Hierdoor kunnen sommige cellen kleiner worden.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}