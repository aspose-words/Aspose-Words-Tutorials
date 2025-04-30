---
"description": "Leer hoe u de beeldverhouding van vormen in Word-documenten kunt vergrendelen met Aspose.Words voor .NET. Volg deze stapsgewijze handleiding om uw afbeeldingen en vormen in de juiste verhouding te houden."
"linktitle": "Beeldverhouding vergrendeld"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Beeldverhouding vergrendeld"
"url": "/nl/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Beeldverhouding vergrendeld

## Invoering

Heb je je ooit afgevraagd hoe je de perfecte verhoudingen van afbeeldingen en vormen in je Word-documenten kunt behouden? Soms moet je ervoor zorgen dat je afbeeldingen en vormen niet vervormd raken bij het aanpassen van het formaat. Hierbij komt het vergrendelen van de beeldverhouding goed van pas. In deze tutorial laten we zien hoe je de beeldverhouding voor vormen in Word-documenten instelt met Aspose.Words voor .NET. We leggen het uit in eenvoudig te volgen stappen, zodat je deze vaardigheden vol vertrouwen in je projecten kunt toepassen.

## Vereisten

Voordat we in de code duiken, leggen we eerst uit wat je nodig hebt om te beginnen:

- Aspose.Words voor .NET-bibliotheek: U moet Aspose.Words voor .NET geïnstalleerd hebben. Als u dat nog niet gedaan hebt, kunt u dat doen. [download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Zorg ervoor dat u een .NET-ontwikkelomgeving hebt ingesteld. Visual Studio is een populaire keuze.
- Basiskennis van C#: enige kennis van C#-programmering is nuttig.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze naamruimten geven ons toegang tot de klassen en methoden die we nodig hebben om met Word-documenten en -vormen te werken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Stap 1: Stel uw documentenmap in

Voordat we beginnen met het bewerken van vormen, moeten we een map aanmaken waar onze documenten worden opgeslagen. Voor de eenvoud gebruiken we een tijdelijke aanduiding. `YOUR DOCUMENT DIRECTORY`Vervang dit door het daadwerkelijke pad naar uw documentenmap.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Een nieuw document maken

Vervolgens maken we een nieuw Word-document met Aspose.Words. Dit document dient als canvas voor het toevoegen van vormen en afbeeldingen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier maken we een instantie van de `Document` klasse en gebruik een `DocumentBuilder` om ons te helpen de inhoud van het document te maken.

## Stap 3: Een afbeelding invoegen

Laten we nu een afbeelding in ons document invoegen. We gebruiken de `InsertImage` methode van de `DocumentBuilder` klasse. Zorg ervoor dat er een afbeelding in de opgegeven map staat.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Vervangen `dataDir + "Transparent background logo.png"` met het pad naar uw afbeeldingsbestand.

## Stap 4: Vergrendel de beeldverhouding

Zodra de afbeelding is ingevoegd, kunnen we de beeldverhouding vergrendelen. Door de beeldverhouding te vergrendelen, blijven de verhoudingen van de afbeelding constant bij het wijzigen van de grootte.

```csharp
shape.AspectRatioLocked = true;
```

Instelling `AspectRatioLocked` naar `true` zorgt ervoor dat de afbeelding de oorspronkelijke beeldverhouding behoudt.

## Stap 5: Sla het document op

Ten slotte slaan we het document op in de opgegeven directory. Deze stap schrijft alle wijzigingen die we hebben aangebracht naar het documentbestand.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusie

Gefeliciteerd! Je hebt succesvol geleerd hoe je de beeldverhouding voor vormen in Word-documenten instelt met Aspose.Words voor .NET. Door deze stappen te volgen, zorg je ervoor dat je afbeeldingen en vormen hun verhoudingen behouden, waardoor je documenten er professioneel en verzorgd uitzien. Experimenteer gerust met verschillende afbeeldingen en vormen om te zien hoe de functie voor het vergrendelen van de beeldverhouding in verschillende scenario's werkt.

## Veelgestelde vragen

### Kan ik de beeldverhouding ontgrendelen nadat ik deze heb vergrendeld?
Ja, u kunt de beeldverhouding ontgrendelen door `shape.AspectRatioLocked = false`.

### Wat gebeurt er als ik de grootte van een afbeelding wijzig met een vergrendelde beeldverhouding?
De afbeelding wordt proportioneel vergroot of verkleind, waarbij de oorspronkelijke breedte-hoogteverhouding behouden blijft.

### Kan ik dit toepassen op andere vormen dan afbeeldingen?
Absoluut! De functie voor het vergrendelen van de beeldverhouding kan op elke vorm worden toegepast, inclusief rechthoeken, cirkels en meer.

### Is Aspose.Words voor .NET compatibel met .NET Core?
Ja, Aspose.Words voor .NET ondersteunt zowel .NET Framework als .NET Core.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?
U kunt uitgebreide documentatie vinden [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}