---
title: Voorkeursbreedte-instellingen
linktitle: Voorkeursbreedte-instellingen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u tabellen met absolute, relatieve en automatische breedte-instellingen maakt in Aspose.Words voor .NET met deze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Voorkeursbreedte-instellingen

## Invoering

Tabellen zijn een krachtige manier om informatie in uw Word-documenten te organiseren en presenteren. Wanneer u met tabellen werkt in Aspose.Words voor .NET, hebt u verschillende opties om de breedte van tabelcellen in te stellen om ervoor te zorgen dat ze perfect passen bij de lay-out van uw document. Deze gids leidt u door het proces van het maken van tabellen met voorkeursbreedte-instellingen met behulp van Aspose.Words voor .NET, met de nadruk op absolute, relatieve en automatische formaatopties. 

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u het volgende heeft:

1.  Aspose.Words voor .NET: Zorg ervoor dat u Aspose.Words voor .NET in uw ontwikkelomgeving hebt geïnstalleerd. U kunt het downloaden[hier](https://releases.aspose.com/words/net/).

2. .NET-ontwikkelomgeving: Zorg dat u een .NET-ontwikkelomgeving hebt ingesteld, zoals Visual Studio.

3. Basiskennis van C#: Kennis van C#-programmering helpt u de codefragmenten en voorbeelden beter te begrijpen.

4.  Aspose.Words-documentatie: Raadpleeg de[Aspose.Words-documentatie](https://reference.aspose.com/words/net/) voor gedetailleerde API-informatie en verdere lectuur.

## Naamruimten importeren

Voordat u begint met coderen, moet u de benodigde naamruimten importeren in uw C#-project:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Deze naamruimten bieden toegang tot de kernfunctionaliteiten van Aspose.Words en het Table-object, zodat u documenttabellen kunt bewerken.

Laten we het proces voor het maken van een tabel met verschillende voorkeursbreedte-instellingen opsplitsen in duidelijke, beheersbare stappen.

## Stap 1: Initialiseer het document en DocumentBuilder

Kop: Een nieuw document en DocumentBuilder maken

 Uitleg: Begin met het maken van een nieuw Word-document en een`DocumentBuilder` voorbeeld. De`DocumentBuilder` Met de klasse kunt u op een eenvoudige manier inhoud aan uw document toevoegen.

```csharp
// Definieer het pad om het document op te slaan.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Maak een nieuw document.
Document doc = new Document();

// Maak een DocumentBuilder voor dit document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier geeft u de map op waar het document wordt opgeslagen en initialiseert u de`Document` En`DocumentBuilder` objecten.

## Stap 2: Voeg de eerste tabelcel in met absolute breedte

Voeg de eerste cel in de tabel in met een vaste breedte van 40 punten. Dit zorgt ervoor dat deze cel altijd een breedte van 40 punten behoudt, ongeacht de tabelgrootte.

```csharp
// Voeg een cel van absolute grootte in.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In deze stap begint u met het maken van de tabel en voegt u een cel met een absolute breedte in.`PreferredWidth.FromPoints(40)` methode stelt de breedte van de cel in op 40 punten, en`Shading.BackgroundPatternColor` past een lichtgele achtergrondkleur toe.

## Stap 3: Voeg een cel van relatieve grootte in

Voeg een andere cel in met een breedte die 20% is van de totale breedte van de tabel. Deze relatieve grootte zorgt ervoor dat de cel proportioneel wordt aangepast aan de breedte van de tabel.

```csharp
// Voeg een cel met een relatieve (procent) grootte in.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

De breedte van deze cel bedraagt 20% van de totale breedte van de tabel, waardoor deze kan worden aangepast aan verschillende schermformaten of documentindelingen.

### Stap 4: Een automatisch aangepaste cel invoegen

Voeg ten slotte een cel in waarvan de grootte automatisch wordt aangepast op basis van de resterende beschikbare ruimte in de tabel.

```csharp
// Voeg een cel in die automatisch de juiste grootte krijgt.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 De`PreferredWidth.Auto` instelling laat deze cel uitzetten of inkrimpen op basis van de ruimte die overblijft nadat de andere cellen zijn meegerekend. Dit zorgt ervoor dat de tabelindeling er evenwichtig en professioneel uitziet.

## Stap 5: Het document afronden en opslaan

Zodra u alle cellen hebt ingevoegd, maakt u de tabel af en slaat u het document op in het door u opgegeven pad.

```csharp
// Sla het document op.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Met deze stap wordt de tabel afgerond en wordt het document opgeslagen met de bestandsnaam 'WorkingWithTables.PreferredWidthSettings.docx' in de door u aangewezen map.

## Conclusie

Het maken van tabellen met voorkeursbreedte-instellingen in Aspose.Words voor .NET is eenvoudig zodra u de verschillende beschikbare opties voor formaat begrijpt. Of u nu vaste, relatieve of automatische celbreedtes nodig hebt, Aspose.Words biedt de flexibiliteit om verschillende tabelindelingsscenario's efficiënt te verwerken. Door de stappen in deze handleiding te volgen, kunt u ervoor zorgen dat uw tabellen goed gestructureerd en visueel aantrekkelijk zijn in uw Word-documenten.

## Veelgestelde vragen

### Wat is het verschil tussen absolute en relatieve celbreedtes?
Absolute celbreedtes zijn vast en veranderen niet, terwijl relatieve breedtes worden aangepast op basis van de totale breedte van de tabel.

### Kan ik negatieve percentages gebruiken voor relatieve breedtes?
Nee, negatieve percentages zijn niet geldig voor celbreedtes. Alleen positieve percentages zijn toegestaan.

### Hoe werkt de functie voor automatisch formaat aanpassen?
Met automatische aanpassing van de grootte wordt de breedte van de cel aangepast, zodat de resterende ruimte in de tabel wordt opgevuld nadat de grootte van andere cellen is aangepast.

### Kan ik verschillende stijlen toepassen op cellen met verschillende breedte-instellingen?
Ja, u kunt verschillende stijlen en opmaak toepassen op cellen, ongeacht de breedte-instellingen.

### Wat gebeurt er als de totale breedte van de tabel kleiner is dan de som van alle celbreedtes?
De tabel past automatisch de breedte van de cellen aan, zodat deze binnen de beschikbare ruimte passen. Hierdoor kunnen sommige cellen kleiner worden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
