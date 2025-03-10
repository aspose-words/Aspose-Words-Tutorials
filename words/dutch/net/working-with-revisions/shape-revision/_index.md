---
title: Vorm herziening
linktitle: Vorm herziening
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u vormwijzigingen in Word-documenten verwerkt met Aspose.Words voor .NET met deze uitgebreide gids. Leer wijzigingen bijhouden, vormen invoegen en meer.
weight: 10
url: /nl/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vorm herziening

## Invoering

Het programmatisch bewerken van Word-documenten kan een ontmoedigende taak zijn, vooral als het gaat om het verwerken van vormen. Of u nu rapporten maakt, sjablonen ontwerpt of gewoon het maken van documenten automatiseert, de mogelijkheid om vormrevisies bij te houden en te beheren is cruciaal. Aspose.Words voor .NET biedt een krachtige API om dit proces naadloos en efficiënt te maken. In deze tutorial duiken we in de details van het herzien van vormen in Word-documenten, zodat u de tools en kennis hebt om uw documenten eenvoudig te beheren.

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:

-  Aspose.Words voor .NET: Zorg ervoor dat u de Aspose.Words-bibliotheek hebt geïnstalleerd. U kunt[download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: U dient een ontwikkelomgeving in te stellen, zoals Visual Studio.
- Basiskennis van C#: Kennis van de programmeertaal C# en basisconcepten van objectgeoriënteerd programmeren.
- Word-document: een Word-document om mee te werken. U kunt er ook zelf een maken tijdens de tutorial.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Deze geven ons toegang tot de klassen en methoden die nodig zijn voor het verwerken van Word-documenten en -vormen.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Stap 1: Uw documentenmap instellen

Voordat we met vormen gaan werken, moeten we het pad naar onze documentdirectory definiëren. Dit is waar we onze aangepaste documenten opslaan.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Een nieuw document maken

Laten we een nieuw Word-document maken waarin we vormen gaan invoegen en bewerken.

```csharp
Document doc = new Document();
```

## Stap 3: Een inline-vorm invoegen

We beginnen met het invoegen van een inline-vorm in ons document zonder revisies bij te houden. Een inline-vorm is een vorm die met de tekst meestroomt.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Stap 4: Beginnen met het bijhouden van revisies

Om wijzigingen in ons document bij te houden, moeten we revisietracking inschakelen. Dit is essentieel voor het identificeren van wijzigingen die aan vormen zijn aangebracht.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Stap 5: Een andere vorm met revisies invoegen

Nu revisietracking is ingeschakeld, voegen we een andere vorm in. Deze keer worden alle wijzigingen bijgehouden.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Stap 6: Vormen ophalen en wijzigen

We kunnen alle vormen in het document ophalen en ze naar behoefte aanpassen. Hier halen we de vormen op en verwijderen de eerste.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Stap 7: Het document opslaan

Nadat we onze wijzigingen hebben aangebracht, moeten we het document opslaan. Dit zorgt ervoor dat alle revisies en wijzigingen worden opgeslagen.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Stap 8: Vormverplaatsingsrevisies verwerken

Wanneer een vorm wordt verplaatst, houdt Aspose.Words dit bij als een revisie. Dit betekent dat er twee instanties van de vorm zijn: één op de oorspronkelijke locatie en één op de nieuwe locatie.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusie

En daar heb je het! Je hebt succesvol geleerd hoe je vormwijzigingen in Word-documenten kunt verwerken met Aspose.Words voor .NET. Of je nu documentsjablonen beheert, rapporten automatiseert of gewoon wijzigingen bijhoudt, deze vaardigheden zijn van onschatbare waarde. Door deze stapsgewijze handleiding te volgen, heb je niet alleen de basis onder de knie, maar ook inzicht gekregen in meer geavanceerde documentverwerkingstechnieken.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, wijzigen en converteren met behulp van C#.

### Kan ik wijzigingen in andere elementen in een Word-document bijhouden?
Ja, Aspose.Words voor .NET ondersteunt het bijhouden van wijzigingen in verschillende elementen, waaronder tekst, tabellen en meer.

### Hoe kan ik een gratis proefversie van Aspose.Words voor .NET krijgen?
 U kunt een gratis proefversie van Aspose.Words voor .NET krijgen[hier](https://releases.aspose.com/).

### Is het mogelijk om revisies programmatisch te accepteren of te weigeren?
Ja, Aspose.Words voor .NET biedt methoden om revisies programmatisch te accepteren of te weigeren.

### Kan ik Aspose.Words voor .NET gebruiken met andere .NET-talen dan C#?
Absoluut! Aspose.Words voor .NET kan worden gebruikt met elke .NET-taal, inclusief VB.NET en F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
