---
title: Standaardinstantie lettertypemappen instellen
linktitle: Standaardinstantie lettertypemappen instellen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u lettertypemappen instelt voor de standaardinstantie in Aspose.Words voor .NET met deze stapsgewijze tutorial. Pas uw Word-documenten moeiteloos aan.
weight: 10
url: /nl/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Standaardinstantie lettertypemappen instellen

## Invoering

Hallo, mede-programmeur! Als je met Word-documenten in .NET werkt, weet je waarschijnlijk hoe belangrijk het is om je lettertypen precies goed te hebben. Vandaag duiken we in hoe je lettertypemappen instelt voor de standaardinstantie met Aspose.Words voor .NET. Stel je voor dat je al je aangepaste lettertypen binnen handbereik hebt, zodat je documenten er precies zo uitzien als je ze voor ogen hebt. Klinkt geweldig, toch? Laten we beginnen!

## Vereisten

Voordat we in de details duiken, willen we eerst controleren of je alles hebt wat je nodig hebt:
-  Aspose.Words voor .NET: Zorg ervoor dat u de bibliotheek hebt geïnstalleerd. Zo niet, dan kunt u[download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
- Basiskennis van C#: U moet vertrouwd zijn met C#-programmering.
- Lettertypemap: Een map met uw aangepaste lettertypen.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Dit helpt bij het benaderen van de klassen en methoden die nodig zijn voor het instellen van de fonts-map.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces opsplitsen in eenvoudige, begrijpelijke stappen.

## Stap 1: Definieer de gegevensdirectory

Elke grote reis begint met een enkele stap, en die van ons begint met het definiëren van de directory waar uw document is opgeslagen. Dit is waar Aspose.Words naar uw Word-document zal zoeken.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Hier, vervang`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw documentdirectory. Dit is waar uw brondocument zich bevindt en waar de uitvoer wordt opgeslagen.

## Stap 2: Stel de lettertypemap in

 Laten we Aspose.Words nu vertellen waar je je aangepaste lettertypen kunt vinden. Dit doe je door de lettertypenmap in te stellen met behulp van de`FontSettings.DefaultInstance.SetFontsFolder` methode.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 In deze lijn,`"C:\\MyFonts\\"` is het pad naar uw aangepaste lettertypemap. De tweede parameter,`true`, geeft aan dat de lettertypen in deze map recursief moeten worden gescand.

## Stap 3: Laad uw document

 Met de lettertypemap ingesteld, is de volgende stap het laden van uw Word-document in Aspose.Words. Dit doet u met behulp van de`Document` klas.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Hier,`dataDir + "Rendering.docx"` verwijst naar het volledige pad van uw Word-document. Zorg ervoor dat uw document zich in de opgegeven directory bevindt.

## Stap 4: Sla het document op

De laatste stap is om uw document op te slaan nadat u de lettertypemap hebt ingesteld. Dit zorgt ervoor dat uw aangepaste lettertypen correct worden toegepast in de uitvoer.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Deze regel slaat uw document op als een PDF met de aangepaste lettertypen toegepast. Het uitvoerbestand bevindt zich in dezelfde directory als uw brondocument.

## Conclusie

En daar heb je het! Het instellen van lettertypemappen voor de standaardinstantie in Aspose.Words voor .NET is een fluitje van een cent als je het opsplitst in eenvoudige stappen. Door deze handleiding te volgen, kun je ervoor zorgen dat je Word-documenten er precies zo uitzien als je wilt, met al je aangepaste lettertypen op hun plek. Dus ga je gang, probeer het eens en laat je documenten schitteren!

## Veelgestelde vragen

### Kan ik meerdere lettertypemappen instellen?
 Ja, u kunt meerdere lettertypemappen instellen met behulp van de`SetFontsFolders` methode die een array van mappaden accepteert.

### Welke bestandsformaten ondersteunt Aspose.Words voor het opslaan van documenten?
Aspose.Words ondersteunt verschillende formaten, waaronder DOCX, PDF, HTML, EPUB en meer.

### Is het mogelijk om online lettertypen te gebruiken in Aspose.Words?
Nee, Aspose.Words ondersteunt momenteel alleen lokale lettertypebestanden.

### Hoe kan ik ervoor zorgen dat mijn aangepaste lettertypen in de opgeslagen PDF worden ingesloten?
 Door de`FontSettings` Als de lettertypen correct zijn ingelezen en beschikbaar zijn, zal Aspose.Words ze in de PDF-uitvoer insluiten.

### Wat gebeurt er als een lettertype niet in de opgegeven map wordt gevonden?
Aspose.Words gebruikt een terugvallettertype als het opgegeven lettertype niet wordt gevonden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
