---
title: Maateenheid
linktitle: Maateenheid
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u de maateenheidfunctie in Aspose.Words voor .NET configureert om de documentopmaak te behouden tijdens ODT-conversie.
weight: 10
url: /nl/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maateenheid

## Invoering

Hebt u ooit uw Word-documenten naar verschillende formaten moeten converteren, maar had u een specifieke meeteenheid nodig voor uw lay-out? Of u nu met inches, centimeters of punten werkt, het is cruciaal om ervoor te zorgen dat uw document zijn integriteit behoudt tijdens het conversieproces. In deze tutorial laten we u zien hoe u de meeteenheidfunctie in Aspose.Words voor .NET configureert. Deze krachtige functie zorgt ervoor dat de opmaak van uw document precies zo behouden blijft als u nodig hebt bij het converteren naar ODT (Open Document Text)-formaat.

## Vereisten

Voordat u aan de slag gaat met de code, zijn er een paar dingen die u nodig hebt:

1. Aspose.Words voor .NET: Zorg ervoor dat u de nieuwste versie van Aspose.Words voor .NET hebt geïnstalleerd. Als u deze nog niet hebt, kunt u deze downloaden van[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een IDE zoals Visual Studio om uw C#-code te schrijven en uit te voeren.
3. Basiskennis van C#: Als u de basisbeginselen van C# begrijpt, kunt u de tutorial beter volgen.
4. Een Word-document: Zorg dat u een voorbeeld van een Word-document bij de hand hebt dat u kunt gebruiken voor de conversie.

## Naamruimten importeren

Voordat we beginnen met coderen, moeten we ervoor zorgen dat we de benodigde namespaces hebben geïmporteerd. Voeg deze toe met behulp van directives bovenaan uw codebestand:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Stel uw documentenmap in

Eerst moet u het pad naar uw documentdirectory definiëren. Dit is waar uw Word-document zich bevindt en waar het geconverteerde bestand wordt opgeslagen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Vervangen`"YOUR DOCUMENTS DIRECTORY"` met het daadwerkelijke pad naar uw directory. Dit zorgt ervoor dat uw code weet waar uw Word-document te vinden is.

## Stap 2: Laad het Word-document

 Vervolgens moet u het Word-document laden dat u wilt converteren. Dit doet u met behulp van de`Document` klas van Aspose.Words.

```csharp
// Laad het Word-document
Document doc = new Document(dataDir + "Document.docx");
```

Zorg ervoor dat uw Word-document, met de naam 'Document.docx', zich in de opgegeven map bevindt.

## Stap 3: Configureer de meeteenheid

 Laten we nu de meeteenheid voor de ODT-conversie configureren. Dit is waar de magie gebeurt. We zullen de`OdtSaveOptions` inches als meeteenheid gebruiken.

```csharp
// Configuratie van back-upopties met de functie "Meeteenheid"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 In dit voorbeeld stellen we de meeteenheid in op inches. U kunt ook andere eenheden kiezen, zoals`OdtSaveMeasureUnit.Centimeters` of`OdtSaveMeasureUnit.Points` afhankelijk van uw wensen.

## Stap 4: Converteer het document naar ODT

 Ten slotte zullen we het Word-document converteren naar het ODT-formaat met behulp van de geconfigureerde`OdtSaveOptions`.

```csharp
// Converteer het document naar ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Met deze regel code wordt het geconverteerde document opgeslagen in de opgegeven directory, met de nieuwe maateenheid toegepast.

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig de meeteenheidfunctie in Aspose.Words voor .NET configureren om ervoor te zorgen dat de lay-out van je document behouden blijft tijdens de conversie. Of je nu met inches, centimeters of punten werkt, deze tutorial heeft je laten zien hoe je eenvoudig de controle over de opmaak van je document kunt nemen.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch werken met Word-documenten. Het stelt ontwikkelaars in staat om Word-documenten te maken, te wijzigen, te converteren en te verwerken zonder dat Microsoft Word nodig is.

### Kan ik andere meeteenheden dan inches gebruiken?
 Ja, Aspose.Words voor .NET ondersteunt andere meeteenheden zoals centimeters en punten. U kunt de gewenste eenheid opgeven met behulp van de`OdtSaveMeasureUnit` opsomming.

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?
 Ja, u kunt een gratis proefversie van Aspose.Words voor .NET downloaden van[hier](https://releases.aspose.com/).

### Waar kan ik documentatie vinden voor Aspose.Words voor .NET?
 U kunt uitgebreide documentatie voor Aspose.Words voor .NET raadplegen op[deze link](https://reference.aspose.com/words/net/).

### Hoe kan ik ondersteuning krijgen voor Aspose.Words voor .NET?
 Voor ondersteuning kunt u het Aspose.Words forum bezoeken op[deze link](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
