---
title: Krijg revisietypen van woorden
linktitle: Krijg revisietypen van woorden
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u revisietypen van woorden in een Word-document kunt krijgen met Aspose.Words voor .NET. Deze stapsgewijze handleiding helpt u om documentrevisies efficiënt af te handelen.
weight: 10
url: /nl/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Krijg revisietypen van woorden

## Invoering

Heb je ooit tot je knieën in een zee van documentrevisies gestaan en je afgevraagd wie wat en wanneer heeft verplaatst? Je bent niet de enige. Het verwerken van documentrevisies kan een vervelende taak zijn, vooral als het om uitgebreide documenten gaat. Maar maak je geen zorgen! Met Aspose.Words voor .NET kun je deze revisies eenvoudig identificeren en beheren. In deze gids leiden we je stapsgewijs door het proces om revisietypen van woorden in een Word-document te krijgen met Aspose.Words voor .NET. Dus, gesp je vast en laten we erin duiken!

## Vereisten

Voordat we aan de slag gaan met de code, heb je een paar dingen nodig:

1.  Aspose.Words voor .NET-bibliotheek: Als u dat nog niet hebt gedaan, download het dan van[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
3. Basiskennis van C#: Kennis van de programmeertaal C# is nuttig.
4.  Een Word-document met revisies: zorg ervoor dat u een`.docx`bestand met bijgehouden wijzigingen om de code te testen.

## Naamruimten importeren

Om te beginnen moet u de benodigde namespaces importeren in uw C#-project. Hiermee krijgt u toegang tot de functionaliteiten die Aspose.Words voor .NET biedt.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Laten we het voorbeeld opsplitsen in meerdere stappen, zodat u het beter kunt begrijpen en implementeren.

## Stap 1: Stel uw documentenmap in

Allereerst moet u het pad naar uw documentenmap definiëren. Dit is waar uw Word-document met revisies zich bevindt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw documentenmap.

## Stap 2: Laad uw Word-document

Vervolgens moet u het Word-document in uw project laden. Dit document moet de revisies bevatten die u wilt analyseren.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Zorg ervoor dat het bestand`Revisions.docx` bestaat in de opgegeven directory.

## Stap 3: Toegang tot de alineaverzameling

Nu uw document is geladen, moet u de paragrafen in de eerste sectie van de hoofdtekst van het document openen. Dit helpt u door elke paragraaf te itereren om te controleren op revisies.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Stap 4: Loop door de paragrafen en controleer op revisies

Hier gebeurt de magie. Je itereert door elke paragraaf en controleert of deze is verplaatst (verwijderd of ingevoegd).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Deze lus gaat door elke paragraaf en gebruikt de`IsMoveFromRevision` En`IsMoveToRevision` Eigenschappen om te bepalen of de alinea is verplaatst (verwijderd) of verplaatst (ingevoegd).

## Conclusie

En daar heb je het! Met slechts een paar regels code kun je eenvoudig de typen revisies in je Word-document identificeren met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het verwerken van documentrevisies een fluitje van een cent, zodat je je kunt richten op belangrijkere taken. 

## Veelgestelde vragen

### Kan ik Aspose.Words voor .NET gebruiken om wijzigingen bij te houden die door specifieke gebruikers zijn aangebracht?

Ja, Aspose.Words voor .NET biedt functionaliteit om toegang te krijgen tot revisiedetails, inclusief de auteur van de wijzigingen.

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?

 Absoluut! Je kunt een gratis proefversie krijgen[hier](https://releases.aspose.com/).

### Hoe kan ik een tijdelijke licentie voor Aspose.Words voor .NET aanvragen?

 U kunt een tijdelijke vergunning aanvragen en aanvragen bij[hier](https://purchase.aspose.com/temporary-license/).

### Waar kan ik meer gedetailleerde documentatie vinden voor Aspose.Words voor .NET?

 Gedetailleerde documentatie is beschikbaar op de[Aspose-website](https://reference.aspose.com/words/net/).

### Kan ik Aspose.Words voor .NET gebruiken in een niet-commercieel project?

Ja, Aspose.Words voor .NET kan worden gebruikt in zowel commerciële als niet-commerciële projecten. Controleer wel de licentievoorwaarden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
