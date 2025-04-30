---
"description": "Leer hoe u de zwevende positie van tabellen in Word-documenten kunt bepalen met Aspose.Words voor .NET met behulp van onze gedetailleerde, stapsgewijze handleiding."
"linktitle": "Zwevende tafelpositie"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Zwevende tafelpositie"
"url": "/nl/net/programming-with-tables/floating-table-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zwevende tafelpositie

## Invoering

Ben je klaar om te duiken in de wereld van het manipuleren van tabelposities in Word-documenten met Aspose.Words voor .NET? Maak je klaar, want vandaag gaan we ontdekken hoe je de zwevende positie van tabellen eenvoudig kunt bepalen. We maken van jou in een mum van tijd een echte wizard voor tabelpositionering!

## Vereisten

Voordat we aan deze spannende reis beginnen, moeten we ervoor zorgen dat we alles hebben wat we nodig hebben:

1. Aspose.Words voor .NET-bibliotheek: Zorg ervoor dat u de nieuwste versie hebt. Zo niet, [download het hier](https://releases.aspose.com/words/net/).
2. .NET Framework: Zorg ervoor dat uw ontwikkelomgeving is ingesteld met .NET.
3. Ontwikkelomgeving: Visual Studio of een andere gewenste IDE.
4. Een Word-document: Zorg dat u een Word-document bij de hand hebt dat een tabel bevat.

## Naamruimten importeren

Om te beginnen moet u de benodigde naamruimten in uw .NET-project importeren. Dit is het fragment dat u bovenaan uw C#-bestand moet opnemen:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Stapsgewijze handleiding

Laten we het proces nu opdelen in eenvoudige, begrijpelijke stappen.

## Stap 1: Het document laden

Allereerst moet je je Word-document laden. Dit is waar je tabel staat.

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Stel je voor dat je Word-document een canvas is en je tabel een kunstwerk erop. Ons doel is om dit kunstwerk precies op de gewenste plek op het canvas te plaatsen.

## Stap 2: Toegang tot de tabel

Vervolgens moeten we de tabel in het document benaderen. Meestal werk je met de eerste tabel in de hoofdtekst van het document.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Beschouw deze stap als het zoeken naar de tabel waarmee u wilt werken in een fysiek document. U moet precies weten waar deze zich bevindt om wijzigingen aan te kunnen brengen.

## Stap 3: Horizontale positie instellen

Laten we nu de horizontale positie van de tabel instellen. Dit bepaalt hoe ver de tabel van de linkerrand van het document wordt geplaatst.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

Stel je dit voor als het horizontaal verplaatsen van de tabel over je document. `AbsoluteHorizontalDistance` is de exacte afstand vanaf de linkerrand.

## Stap 4: Verticale uitlijning instellen

We moeten ook de verticale uitlijning van de tabel instellen. Dit centreert de tabel verticaal ten opzichte van de omringende tekst.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Stel je voor dat je een schilderij aan de muur hangt. Je wilt ervoor zorgen dat het verticaal gecentreerd is voor een esthetische aantrekkingskracht. Deze stap zorgt daarvoor.

## Stap 5: Sla het gewijzigde document op

Nadat u de tabel hebt gepositioneerd, slaat u uw gewijzigde document op.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Dit is hetzelfde als op 'Opslaan' klikken in je bewerkte document. Al je wijzigingen blijven nu behouden.

## Conclusie

En voilà! Je hebt zojuist geleerd hoe je de zwevende positie van tabellen in een Word-document kunt bepalen met Aspose.Words voor .NET. Met deze vaardigheden kun je ervoor zorgen dat je tabellen perfect gepositioneerd zijn om de leesbaarheid en esthetiek van je documenten te verbeteren. Blijf experimenteren en ontdek de uitgebreide mogelijkheden van Aspose.Words voor .NET.

## Veelgestelde vragen

### Kan ik de verticale afstand van de tabel tot de bovenkant van de pagina instellen?

Ja, u kunt de `AbsoluteVerticalDistance` Eigenschap om de verticale afstand van de tabel tot de bovenrand van de pagina in te stellen.

### Hoe kan ik de tabel rechts in het document uitlijnen?

Om de tabel rechts uit te lijnen, kunt u de `HorizontalAlignment` eigenschap van de tabel om `HorizontalAlignment.Right`.

### Is het mogelijk om meerdere tabellen in hetzelfde document anders te positioneren?

Absoluut! Je kunt posities voor meerdere tabellen individueel openen en instellen door te itereren door de `Tables` verzameling in het document.

### Kan ik relatieve positionering gebruiken voor horizontale uitlijning?

Ja, Aspose.Words ondersteunt relatieve positionering voor zowel horizontale als verticale uitlijningen met behulp van eigenschappen zoals `RelativeHorizontalAlignment`.

### Ondersteunt Aspose.Words zwevende tabellen in verschillende secties van een document?

Ja, u kunt zwevende tabellen in verschillende secties positioneren door de specifieke sectie en de bijbehorende tabellen in uw document te openen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}