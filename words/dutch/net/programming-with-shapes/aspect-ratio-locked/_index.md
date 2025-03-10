---
title: Beeldverhouding vergrendeld
linktitle: Beeldverhouding vergrendeld
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u de beeldverhouding van vormen in Word-documenten kunt vergrendelen met Aspose.Words voor .NET. Volg deze stapsgewijze handleiding om uw afbeeldingen en vormen proportioneel te houden.
weight: 10
url: /nl/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beeldverhouding vergrendeld

## Invoering

Heb je je ooit afgevraagd hoe je de perfecte verhoudingen van afbeeldingen en vormen in je Word-documenten kunt behouden? Soms moet je ervoor zorgen dat je afbeeldingen en vormen niet vervormd raken wanneer je de grootte wijzigt. Dit is waar het vergrendelen van de beeldverhouding van pas komt. In deze tutorial onderzoeken we hoe je de beeldverhouding voor vormen in Word-documenten instelt met Aspose.Words voor .NET. We splitsen het op in eenvoudig te volgen stappen, zodat je deze vaardigheden met vertrouwen op je projecten kunt toepassen.

## Vereisten

Voordat we in de code duiken, leggen we eerst uit wat je nodig hebt om te beginnen:

- Aspose.Words voor .NET-bibliotheek: U moet Aspose.Words voor .NET geïnstalleerd hebben. Als u dat nog niet hebt gedaan, kunt u[download het hier](https://releases.aspose.com/words/net/).
- Development Environment: Zorg ervoor dat u een .NET development environment hebt ingesteld. Visual Studio is een populaire keuze.
- Basiskennis van C#: enige kennis van C#-programmering is nuttig.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Deze namespaces geven ons toegang tot de klassen en methoden die we nodig hebben om met Word-documenten en -vormen te werken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Stap 1: Stel uw documentenmap in

 Voordat we beginnen met het manipuleren van vormen, moeten we een directory instellen waar onze documenten worden opgeslagen. Voor de eenvoud gebruiken we een tijdelijke aanduiding`YOUR DOCUMENT DIRECTORY`Vervang dit door het daadwerkelijke pad naar uw documentmap.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Maak een nieuw document

Vervolgens maken we een nieuw Word-document met Aspose.Words. Dit document dient als canvas voor het toevoegen van vormen en afbeeldingen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier maken we een instantie van de`Document` klasse en gebruik een`DocumentBuilder` om ons te helpen de inhoud van het document te maken.

## Stap 3: Een afbeelding invoegen

 Laten we nu een afbeelding in ons document invoegen. We gebruiken de`InsertImage` methode van de`DocumentBuilder`klasse. Zorg ervoor dat u een afbeelding in de opgegeven directory hebt.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Vervangen`dataDir + "Transparent background logo.png"` met het pad naar uw afbeeldingsbestand.

## Stap 4: Vergrendel de beeldverhouding

Zodra de afbeelding is ingevoegd, kunnen we de beeldverhouding vergrendelen. Het vergrendelen van de beeldverhouding zorgt ervoor dat de verhoudingen van de afbeelding constant blijven bij het wijzigen van de grootte.

```csharp
shape.AspectRatioLocked = true;
```

 Instelling`AspectRatioLocked` naar`true` zorgt ervoor dat de afbeelding zijn oorspronkelijke beeldverhouding behoudt.

## Stap 5: Sla het document op

Ten slotte slaan we het document op in de opgegeven directory. Deze stap schrijft alle wijzigingen die we hebben aangebracht naar het documentbestand.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusie

Gefeliciteerd! U hebt succesvol geleerd hoe u de beeldverhouding voor vormen in Word-documenten instelt met Aspose.Words voor .NET. Door deze stappen te volgen, kunt u ervoor zorgen dat uw afbeeldingen en vormen hun verhoudingen behouden, waardoor uw documenten er professioneel en gepolijst uitzien. Experimenteer gerust met verschillende afbeeldingen en vormen om te zien hoe de functie voor het vergrendelen van de beeldverhouding in verschillende scenario's werkt.

## Veelgestelde vragen

### Kan ik de beeldverhouding ontgrendelen nadat ik deze heb vergrendeld?
Ja, u kunt de beeldverhouding ontgrendelen door`shape.AspectRatioLocked = false`.

### Wat gebeurt er als ik de grootte van een afbeelding wijzig met een vergrendelde beeldverhouding?
De afbeelding wordt proportioneel vergroot of verkleind, waarbij de oorspronkelijke breedte-hoogteverhouding behouden blijft.

### Kan ik dit toepassen op andere vormen dan afbeeldingen?
Absoluut! De aspect ratio locking feature kan worden toegepast op elke vorm, inclusief rechthoeken, cirkels en meer.

### Is Aspose.Words voor .NET compatibel met .NET Core?
Ja, Aspose.Words voor .NET ondersteunt zowel .NET Framework als .NET Core.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?
 U kunt uitgebreide documentatie vinden[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
