---
title: Standaardlettertype opgeven bij rendering
linktitle: Standaardlettertype opgeven bij rendering
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een standaardlettertype opgeeft bij het renderen van Word-documenten met Aspose.Words voor .NET. Zorg voor een consistente weergave van het document op alle platforms.
weight: 10
url: /nl/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Standaardlettertype opgeven bij rendering

## Invoering

Ervoor zorgen dat uw Word-documenten correct worden weergegeven op verschillende platforms kan een uitdaging zijn, vooral als het gaat om lettertypecompatibiliteit. Een manier om een consistent uiterlijk te behouden, is door een standaardlettertype op te geven bij het weergeven van uw documenten naar PDF of andere formaten. In deze tutorial onderzoeken we hoe u een standaardlettertype instelt met Aspose.Words voor .NET, zodat uw documenten er geweldig uitzien, ongeacht waar ze worden bekeken.

## Vereisten

Voordat we in de code duiken, bespreken we eerst wat je nodig hebt om deze tutorial te kunnen volgen:

- Aspose.Words voor .NET: Zorg ervoor dat u de nieuwste versie hebt geïnstalleerd. U kunt het downloaden[hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere .NET-ontwikkelomgeving.
- Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u bekend bent met C#-programmering.

## Naamruimten importeren

Om te beginnen moet u de benodigde namespaces importeren. Hiermee krijgt u toegang tot de klassen en methoden die nodig zijn om met Aspose.Words te werken.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces voor het opgeven van een standaardlettertype opsplitsen in eenvoudig te volgen stappen.

## Stap 1: Stel uw documentenmap in

Definieer eerst het pad naar uw documentdirectory. Dit is waar uw invoer- en uitvoerbestanden worden opgeslagen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Laad uw document

Laad vervolgens het document dat u wilt renderen. In dit voorbeeld gebruiken we een bestand met de naam "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 3: Configureer lettertype-instellingen

 Maak een exemplaar van`FontSettings` en specificeer het standaardlettertype. Als het gedefinieerde lettertype niet kan worden gevonden tijdens het renderen, gebruikt Aspose.Words het dichtstbijzijnde beschikbare lettertype op de machine.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Stap 4: Lettertype-instellingen toepassen op het document

Wijs de geconfigureerde lettertype-instellingen toe aan uw document.

```csharp
doc.FontSettings = fontSettings;
```

## Stap 5: Sla het document op

Sla het document ten slotte op in het gewenste formaat. In dit geval slaan we het op als PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Conclusie

Door deze stappen te volgen, kunt u ervoor zorgen dat uw Word-documenten worden weergegeven met een opgegeven standaardlettertype, zodat consistentie op verschillende platforms behouden blijft. Dit kan met name handig zijn voor documenten die veel worden gedeeld of worden bekeken op systemen met verschillende lettertypebeschikbaarheid.


## Veelgestelde vragen

### Waarom moet ik een standaardlettertype opgeven in Aspose.Words?
Door een standaardlettertype op te geven, zorgt u ervoor dat uw document er op verschillende platforms consistent uitziet, zelfs als de oorspronkelijke lettertypen niet beschikbaar zijn.

### Wat gebeurt er als het standaardlettertype niet wordt gevonden tijdens het renderen?
Aspose.Words gebruikt het dichtstbijzijnde lettertype dat op de computer beschikbaar is om het uiterlijk van het document zo goed mogelijk te behouden.

### Kan ik meerdere standaardlettertypen opgeven?
 Nee, u kunt slechts één standaardlettertype opgeven. U kunt echter lettertypevervanging voor specifieke gevallen afhandelen met behulp van de`FontSettings` klas.

### Is Aspose.Words voor .NET compatibel met alle versies van Word-documenten?
Ja, Aspose.Words voor .NET ondersteunt een breed scala aan Word-documentformaten, waaronder DOC, DOCX, RTF en meer.

### Waar kan ik ondersteuning krijgen als ik problemen ondervind?
 U kunt ondersteuning krijgen van de Aspose-community en ontwikkelaars op de[Aspose.Words Ondersteuningsforum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
