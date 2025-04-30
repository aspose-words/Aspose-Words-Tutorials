---
"description": "Leer hoe u systeem- en aangepaste lettertypemappen in Word-documenten instelt met Aspose.Words voor .NET, zodat uw documenten correct worden weergegeven in verschillende omgevingen."
"linktitle": "Stel lettertypemappen in Systeem en aangepaste map"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Stel lettertypemappen in Systeem en aangepaste map"
"url": "/nl/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Stel lettertypemappen in Systeem en aangepaste map

## Invoering

Stel je voor dat je een document met een uniek lettertype aan het maken bent, maar ontdekt dat de lettertypen op een andere computer niet correct worden weergegeven. Frustrerend, toch? Dit is waar het configureren van lettertypemappen om de hoek komt kijken. Met Aspose.Words voor .NET kun je systeem- en aangepaste lettertypemappen definiëren om ervoor te zorgen dat je documenten er altijd uitzien zoals bedoeld. Laten we eens kijken hoe je dit kunt bereiken.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

- Aspose.Words voor .NET-bibliotheek: als u dat nog niet heeft gedaan, download het dan [hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Een IDE zoals Visual Studio.
- Basiskennis van C#: Kennis van C# helpt u de codevoorbeelden te volgen.

## Naamruimten importeren

Importeer eerst de benodigde naamruimten in uw project:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces nu opdelen in eenvoudige stappen.

## Stap 1: Het document laden

Om te beginnen laadt u uw Word-document in een Aspose.Words-bestand. `Document` object. Dit is het document waarin u de lettertypemappen wilt instellen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 2: Initialiseer lettertype-instellingen

Maak een nieuw exemplaar van `FontSettings`Met dit object kunt u lettertypebronnen beheren.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Stap 3: Systeemlettertypebronnen ophalen

Haal de standaard systeemlettertypebronnen op. Op een Windows-computer is dit meestal de map "Windows\Fonts".

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Stap 4: Een aangepaste lettertypemap toevoegen

Voeg een aangepaste map toe met uw extra lettertypen. Dit is handig als u specifieke lettertypen niet in de systeemlettertypenmap hebt geïnstalleerd.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Stap 5: Lettertypebronnen bijwerken

Converteer de lijst met lettertypebronnen terug naar een array en stel deze in op de `FontSettings` voorwerp.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Stap 6: Lettertype-instellingen toepassen op document

Pas ten slotte de geconfigureerde toe `FontSettings` aan uw document toe en sla het op in het door u gewenste formaat, bijvoorbeeld PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusie

En voilà! Door deze stappen te volgen, zorgt u ervoor dat uw Word-documenten de juiste lettertypen gebruiken, of het nu systeemlettertypen zijn of aangepaste lettertypen die in een specifieke map zijn opgeslagen. Deze configuratie helpt de integriteit van de weergave van uw document in verschillende omgevingen te behouden.

## Veelgestelde vragen

### Wat gebeurt er als een lettertype ontbreekt in zowel de systeem- als de aangepaste mappen?

Aspose.Words gebruikt een standaardlettertype om het ontbrekende lettertype te vervangen, zodat het document leesbaar blijft.

### Kan ik meerdere aangepaste lettertypemappen toevoegen?

Ja, u kunt meerdere aangepaste lettertypemappen toevoegen door het proces van het maken te herhalen `FolderFontSource` objecten en deze toe te voegen aan de lijst met lettertypebronnen.

### Is het mogelijk om netwerkpaden te gebruiken voor aangepaste lettertypemappen?

Ja, u kunt een netwerkpad opgeven in de `FolderFontSource` constructeur.

### Welke bestandsformaten ondersteunt Aspose.Words voor het opslaan van documenten?

Aspose.Words ondersteunt verschillende formaten, waaronder DOCX, PDF, HTML en meer.

### Hoe ga ik om met meldingen over lettertypevervanging?

U kunt meldingen over lettertypevervanging afhandelen met behulp van de `FontSettings` klas `FontSubstitutionWarning` evenement.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}