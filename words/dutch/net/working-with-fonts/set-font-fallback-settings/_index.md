---
title: Stel de instellingen voor het terugvallen van lettertypen in
linktitle: Stel de instellingen voor het terugvallen van lettertypen in
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u de lettertype-fallbackinstellingen in Aspose.Words voor .NET instelt. Deze uitgebreide handleiding zorgt ervoor dat alle tekens in uw documenten correct worden weergegeven.
weight: 10
url: /nl/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Stel de instellingen voor het terugvallen van lettertypen in

## Invoering

Bij het werken met documenten die verschillende tekstelementen bevatten, zoals verschillende talen of speciale tekens, is het cruciaal om ervoor te zorgen dat deze elementen correct worden weergegeven. Aspose.Words voor .NET biedt een krachtige functie genaamd Font Fallback Settings, die helpt bij het definiëren van regels voor het vervangen van lettertypen wanneer het oorspronkelijke lettertype bepaalde tekens niet ondersteunt. In deze handleiding onderzoeken we hoe u Font Fallback Settings instelt met Aspose.Words voor .NET in een stapsgewijze zelfstudie.

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

- Basiskennis van C#: Kennis van de programmeertaal C# en het .NET Framework.
-  Aspose.Words voor .NET: Downloaden en installeren vanaf de[downloadlink](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Een omgeving zoals Visual Studio om uw code te schrijven en uit te voeren.
-  Voorbeeld document: Heb een voorbeeld document (bijv.`Rendering.docx`) klaar om te testen.
- XML-regels voor lettertype-fallback: maak een XML-bestand waarin de lettertype-fallbackregels worden gedefinieerd.

## Naamruimten importeren

Om Aspose.Words te gebruiken, moet u de benodigde naamruimten importeren. Dit geeft toegang tot verschillende klassen en methoden die nodig zijn voor documentverwerking.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Stap 1: Definieer de documentdirectory

Definieer eerst de directory waar uw document is opgeslagen. Dit is essentieel voor het vinden en verwerken van uw document.

```csharp
// Het pad naar de documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Laad het document

 Laad uw document in een Aspose.Words`Document` object. Met deze stap kunt u programmatisch met het document werken.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 3: Configureer lettertype-instellingen

 Maak een nieuwe`FontSettings` object en laad de font fallback-instellingen van een XML-bestand. Dit XML-bestand bevat de regels voor font fallback.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Stap 4: Lettertype-instellingen toepassen op het document

 Wijs de geconfigureerde toe`FontSettings`aan het document. Dit zorgt ervoor dat de regels voor lettertype-fallback worden toegepast bij het renderen van het document.

```csharp
doc.FontSettings = fontSettings;
```

## Stap 5: Sla het document op

Sla ten slotte het document op. De font fallback-instellingen worden gebruikt tijdens de opslagbewerking om correcte fontvervanging te garanderen.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML-bestand: regels voor lettertype-fallback

Hier ziet u een voorbeeld van hoe uw XML-bestand met de fallback-regels voor lettertypen eruit moet zien:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Conclusie

Door deze stappen te volgen, kunt u effectief Font Fallback Settings instellen en gebruiken in Aspose.Words voor .NET. Dit zorgt ervoor dat uw documenten alle tekens correct weergeven, zelfs als het originele lettertype bepaalde tekens niet ondersteunt. Het implementeren van deze instellingen zal de kwaliteit en leesbaarheid van uw documenten aanzienlijk verbeteren.

## Veelgestelde vragen

### V1: Wat is Font Fallback?

Met Font Fallback kunt u lettertypen vervangen als het oorspronkelijke lettertype bepaalde tekens niet ondersteunt. Zo wordt gezorgd voor een correcte weergave van alle tekstelementen.

### V2: Kan ik meerdere fallback-lettertypen opgeven?

Ja, u kunt meerdere fallback-lettertypen opgeven in de XML-regels. Aspose.Words controleert elk lettertype in de opgegeven volgorde totdat er een wordt gevonden die het teken ondersteunt.

### V3: Waar kan ik Aspose.Words voor .NET downloaden?

 Je kunt het downloaden van de[Aspose downloadpagina](https://releases.aspose.com/words/net/).

### V4: Hoe maak ik het XML-bestand voor de fallback-regels voor lettertypen?

Het XML-bestand kan worden gemaakt met elke teksteditor. Het moet de structuur volgen die wordt getoond in het voorbeeld in deze tutorial.

### V5: Is er ondersteuning beschikbaar voor Aspose.Words?

 Ja, u kunt ondersteuning vinden op de[Aspose.Words ondersteuningsforum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
