---
"description": "Leer hoe u maateenheden converteert in Aspose.Words voor .NET. Volg onze stapsgewijze handleiding om documentmarges, kopteksten en voetteksten in inches en punten in te stellen."
"linktitle": "Converteren tussen meeteenheden"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Converteren tussen meeteenheden"
"url": "/nl/net/programming-with-document-properties/convert-between-measurement-units/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Converteren tussen meeteenheden

## Invoering

Hallo! Werk je als ontwikkelaar met Word-documenten in Aspose.Words voor .NET? Zo ja, dan moet je vaak marges, kopteksten of voetteksten instellen in verschillende maateenheden. Het omrekenen tussen eenheden zoals inches en punten kan lastig zijn als je niet bekend bent met de functionaliteiten van de bibliotheek. In deze uitgebreide tutorial begeleiden we je bij het omrekenen tussen maateenheden met Aspose.Words voor .NET. Laten we die omrekeningen vereenvoudigen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Aspose.Words voor .NET-bibliotheek: als u dat nog niet heeft gedaan, download het dan [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
3. Basiskennis van C#: Als u de basisbeginselen van C# begrijpt, kunt u de cursus gemakkelijk volgen.
4. Aspose-licentie: Optioneel, maar aanbevolen voor volledige functionaliteit. U kunt een tijdelijke licentie aanschaffen. [hier](https://purchase.aspose.com/temporary-license/).

## Naamruimten importeren

Eerst moet je de benodigde naamruimten importeren. Dit is cruciaal voor toegang tot de klassen en methoden van Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

Laten we het proces van het converteren van maateenheden in Aspose.Words voor .NET eens bekijken. Volg deze gedetailleerde stappen om de marges en afstanden van je document in te stellen en aan te passen.

## Stap 1: Een nieuw document maken

Eerst moet u een nieuw document maken met Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hiermee wordt een nieuw Word-document geïnitialiseerd en een `DocumentBuilder` om het creëren en opmaken van inhoud te vergemakkelijken.

## Stap 2: Toegang tot pagina-instellingen

Om de marges, kopteksten en voetteksten in te stellen, moet u naar de `PageSetup` voorwerp.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

Hiermee krijgt u toegang tot verschillende eigenschappen voor de pagina-instelling, zoals marges, koptekstafstand en voettekstafstand.

## Stap 3: Converteer inches naar punten

Aspose.Words gebruikt standaard punten als maateenheid. Om marges in inches in te stellen, moet u inches naar punten converteren met behulp van de `ConvertUtil.InchToPoint` methode.

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

Hieronder volgt een overzicht van wat elke regel doet:
- Stelt de boven- en ondermarge in op 1 inch (omgezet naar punten).
- Stelt de linker- en rechtermarge in op 1,5 inch (omgezet naar punten).
- Stelt de afstanden tussen de kop- en voettekst in op 0,2 inch (omgerekend naar punten).

## Stap 4: Sla het document op

Sla ten slotte uw document op om er zeker van te zijn dat alle wijzigingen worden toegepast.

```csharp
doc.Save("ConvertedDocument.docx");
```

Hiermee slaat u uw document op met de opgegeven marges en afstanden in punten.

## Conclusie

En voilà! Je hebt met succes marges en afstanden in een Word-document geconverteerd en ingesteld met Aspose.Words voor .NET. Door deze stappen te volgen, kun je gemakkelijk verschillende eenheden omrekenen, waardoor je documentaanpassing een fluitje van een cent wordt. Blijf experimenteren met verschillende instellingen en ontdek de uitgebreide functionaliteiten die Aspose.Words biedt. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik andere eenheden, zoals centimeters, naar punten omzetten met Aspose.Words?
Ja, Aspose.Words biedt methoden zoals `ConvertUtil.CmToPoint` voor het omrekenen van centimeters naar punten.

### Is een licentie nodig om Aspose.Words voor .NET te gebruiken?
Hoewel u Aspose.Words zonder licentie kunt gebruiken, kunnen sommige geavanceerde functies beperkt zijn. Met een licentie bent u verzekerd van volledige functionaliteit.

### Hoe installeer ik Aspose.Words voor .NET?
Je kunt het downloaden van de [website](https://releases.aspose.com/words/net/) en volg de installatie-instructies.

### Kan ik verschillende eenheden instellen voor verschillende secties van een document?
Ja, u kunt de marges en andere instellingen voor verschillende secties aanpassen met behulp van de `Section` klas.

### Welke andere functies biedt Aspose.Words?
Aspose.Words ondersteunt een breed scala aan functies, waaronder documentconversie, samenvoeging en uitgebreide opmaakopties. Bekijk de [documentatie](https://reference.aspose.com/words/net/) voor meer details.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}