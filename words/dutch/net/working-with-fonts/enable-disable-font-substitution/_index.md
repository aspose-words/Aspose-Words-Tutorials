---
title: Lettertypevervanging inschakelen/uitschakelen
linktitle: Lettertypevervanging inschakelen/uitschakelen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u lettertypevervanging in Word-documenten kunt in- of uitschakelen met Aspose.Words voor .NET. Zorg ervoor dat uw documenten er op alle platforms consistent uitzien.
weight: 10
url: /nl/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypevervanging inschakelen/uitschakelen

## Invoering

Heb je ooit een situatie meegemaakt waarin je zorgvuldig gekozen lettertypen in een Word-document werden vervangen wanneer je ze op een andere computer bekeek? Vervelend, toch? Dit gebeurt door lettertypevervanging, een proces waarbij het systeem een ontbrekend lettertype vervangt door een beschikbaar lettertype. Maar maak je geen zorgen! Met Aspose.Words voor .NET kun je lettertypevervanging eenvoudig beheren en controleren. In deze tutorial leiden we je door de stappen om lettertypevervanging in je Word-documenten in of uit te schakelen, zodat je documenten er altijd uitzien zoals je wilt.

## Vereisten

Voordat we met de stappen beginnen, controleren we of u alles bij de hand hebt:

-  Aspose.Words voor .NET: Download de nieuwste versie[hier](https://releases.aspose.com/words/net/).
- Visual Studio: elke versie die .NET ondersteunt.
- Basiskennis van C#: Hiermee kunt u de codevoorbeelden beter volgen.

## Naamruimten importeren

Om te beginnen, zorg ervoor dat u de benodigde namespaces in uw project hebt geïmporteerd. Voeg deze toe bovenaan uw C#-bestand:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces nu opsplitsen in eenvoudige, beheersbare stappen.

## Stap 1: Stel uw project in

Stel eerst een nieuw project in Visual Studio in en voeg een verwijzing toe naar de Aspose.Words for .NET-bibliotheek. Als u dat nog niet hebt gedaan, downloadt u het van de[Aspose-website](https://releases.aspose.com/words/net/).

## Stap 2: Laad uw document

Laad vervolgens het document waarmee u wilt werken. Dit is hoe u dat doet:

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw documentdirectory. Deze code laadt het document in het geheugen zodat u het kunt manipuleren.

## Stap 3: Configureer lettertype-instellingen

 Laten we nu een`FontSettings` object om de instellingen voor lettertypevervanging te beheren:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Stap 4: Standaardlettertypevervanging instellen

Stel de standaard lettertypevervanging in op een lettertype naar keuze. Dit lettertype wordt gebruikt als het originele lettertype niet beschikbaar is:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In dit voorbeeld gebruiken we Arial als standaardlettertype.

## Stap 5: Schakel lettertype-infovervanging uit

Om de vervanging van lettertype-informatie uit te schakelen, waardoor het systeem ontbrekende lettertypen niet kan vervangen door beschikbare lettertypen, gebruikt u de volgende code:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Stap 6: Lettertype-instellingen toepassen op het document

Pas nu deze instellingen toe op uw document:

```csharp
doc.FontSettings = fontSettings;
```

## Stap 7: Sla uw document op

Sla ten slotte uw gewijzigde document op. U kunt het opslaan in elk gewenst formaat. Voor deze tutorial slaan we het op als PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig lettertypevervanging in je Word-documenten beheren met Aspose.Words voor .NET. Dit zorgt ervoor dat je documenten hun beoogde look en feel behouden, ongeacht waar ze worden bekeken.

## Veelgestelde vragen

### Kan ik andere lettertypen dan Arial gebruiken ter vervanging?

 Absoluut! U kunt elk lettertype opgeven dat beschikbaar is op uw systeem door de lettertypenaam in de`DefaultFontName` eigendom.

### Wat gebeurt er als het opgegeven standaardlettertype niet beschikbaar is?

Als het standaardlettertype niet beschikbaar is, gebruikt Aspose.Words een systeemmechanisme om een geschikt vervangend lettertype te vinden.

### Kan ik lettertypevervanging weer inschakelen nadat ik het heb uitgeschakeld?

 Ja, u kunt de`Enabled` eigendom van`FontInfoSubstitution` terug naar`true` als u lettertypevervanging weer wilt inschakelen.

### Is er een manier om te controleren welke lettertypen worden vervangen?

Ja, Aspose.Words biedt methoden om lettertypevervanging te registreren en bij te houden, zodat u kunt zien welke lettertypen worden vervangen.

### Kan ik deze methode gebruiken voor andere documentformaten dan DOCX?

Zeker! Aspose.Words ondersteunt verschillende formaten en u kunt deze lettertype-instellingen op elk ondersteund formaat toepassen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
