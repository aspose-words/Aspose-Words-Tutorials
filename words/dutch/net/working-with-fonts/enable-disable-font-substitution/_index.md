---
"description": "Leer hoe u lettertypevervanging in Word-documenten kunt in- of uitschakelen met Aspose.Words voor .NET. Zorg ervoor dat uw documenten er op alle platforms consistent uitzien."
"linktitle": "Lettertypevervanging inschakelen/uitschakelen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Lettertypevervanging inschakelen/uitschakelen"
"url": "/nl/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypevervanging inschakelen/uitschakelen

## Invoering

Heb je ooit een situatie meegemaakt waarin je zorgvuldig gekozen lettertypen in een Word-document werden vervangen wanneer je het op een andere computer bekeek? Vervelend, toch? Dit gebeurt door lettertypevervanging, een proces waarbij het systeem een ontbrekend lettertype vervangt door een beschikbaar lettertype. Maar maak je geen zorgen! Met Aspose.Words voor .NET kun je lettertypevervanging eenvoudig beheren en beheren. In deze tutorial leiden we je door de stappen om lettertypevervanging in je Word-documenten in of uit te schakelen, zodat je documenten er altijd precies zo uitzien als je wilt.

## Vereisten

Voordat we de stappen starten, controleren we of u alles hebt wat u nodig hebt:

- Aspose.Words voor .NET: Download de nieuwste versie [hier](https://releases.aspose.com/words/net/).
- Visual Studio: elke versie die .NET ondersteunt.
- Basiskennis van C#: Hiermee kunt u de codevoorbeelden beter volgen.

## Naamruimten importeren

Om te beginnen, zorg ervoor dat je de benodigde naamruimten in je project hebt geïmporteerd. Voeg deze bovenaan je C#-bestand toe:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces nu opdelen in eenvoudige, beheersbare stappen.

## Stap 1: Stel uw project in

Maak eerst een nieuw project aan in Visual Studio en voeg een verwijzing toe naar de Aspose.Words voor .NET-bibliotheek. Als u dit nog niet hebt gedaan, download het dan van de [Aspose-website](https://releases.aspose.com/words/net/).

## Stap 2: Laad uw document

Laad vervolgens het document waarmee u wilt werken. Zo doet u dat:

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw documentmap. Deze code laadt het document in het geheugen zodat u het kunt bewerken.

## Stap 3: Lettertype-instellingen configureren

Laten we nu een `FontSettings` object om de instellingen voor lettertypevervanging te beheren:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Stap 4: Standaardlettertypevervanging instellen

Stel de standaardlettertypevervanging in op een lettertype naar keuze. Dit lettertype wordt gebruikt als het originele lettertype niet beschikbaar is:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In dit voorbeeld gebruiken we Arial als standaardlettertype.

## Stap 5: Vervangen van lettertype-info uitschakelen

Om het vervangen van lettertype-info uit te schakelen (waardoor het systeem ontbrekende lettertypen niet kan vervangen door beschikbare lettertypen), gebruikt u de volgende code:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Stap 6: Lettertype-instellingen toepassen op het document

Pas deze instellingen nu toe op uw document:

```csharp
doc.FontSettings = fontSettings;
```

## Stap 7: Sla uw document op

Sla ten slotte je gewijzigde document op. Je kunt het in elk gewenst formaat opslaan. Voor deze tutorial slaan we het op als PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusie

En voilà! Door deze stappen te volgen, kunt u eenvoudig lettertypevervanging in uw Word-documenten beheren met Aspose.Words voor .NET. Zo behoudt u de gewenste uitstraling van uw documenten, ongeacht waar u ze bekijkt.

## Veelgestelde vragen

### Kan ik andere lettertypen dan Arial gebruiken ter vervanging?

Absoluut! U kunt elk lettertype dat op uw systeem beschikbaar is specificeren door de lettertypenaam in de `DefaultFontName` eigendom.

### Wat gebeurt er als het opgegeven standaardlettertype niet beschikbaar is?

Als het standaardlettertype niet beschikbaar is, gebruikt Aspose.Words een terugvalmechanisme van het systeem om een geschikt vervangend lettertype te vinden.

### Kan ik lettertypevervanging weer inschakelen nadat ik het heb uitgeschakeld?

Ja, je kunt de `Enabled` eigendom van `FontInfoSubstitution` terug naar `true` als u lettertypevervanging weer wilt inschakelen.

### Is er een manier om te controleren welke lettertypen worden vervangen?

Ja, Aspose.Words biedt methoden om lettertypevervanging te registreren en te volgen, zodat u kunt zien welke lettertypen worden vervangen.

### Kan ik deze methode gebruiken voor andere documentformaten dan DOCX?

Zeker! Aspose.Words ondersteunt verschillende formaten en u kunt deze lettertype-instellingen toepassen op elk ondersteund formaat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}