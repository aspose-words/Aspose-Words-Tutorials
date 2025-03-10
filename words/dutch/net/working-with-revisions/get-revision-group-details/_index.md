---
title: Gegevens van revisiegroep ophalen
linktitle: Gegevens van revisiegroep ophalen
second_title: Aspose.Words API voor documentverwerking
description: Haal eenvoudig revisiegroepdetails op in Word-documenten met Aspose.Words voor .NET met deze stapsgewijze handleiding. Perfect voor .NET-ontwikkelaars.
weight: 10
url: /nl/net/working-with-revisions/get-revision-group-details/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gegevens van revisiegroep ophalen

## Invoering

Heb je ooit de behoefte gehad om je te verdiepen in de details van revisies in een Word-document? Misschien werk je samen aan een project en moet je wijzigingen nauwkeurig bijhouden. Nou, gesp je vast, want we gaan zo beginnen aan een geweldige tutorial over hoe je revisiegroepdetails kunt ophalen met Aspose.Words voor .NET. Aan het einde van deze gids ben je een pro in het extraheren en weergeven van revisiedetails, waardoor je documentbeheer een fluitje van een cent wordt.

## Vereisten

Voordat we aan deze codeeravontuur beginnen, willen we ervoor zorgen dat je alles hebt wat je nodig hebt:
-  Aspose.Words voor .NET: Zorg dat je de nieuwste versie hebt geïnstalleerd. Zo niet, dan kun je deze downloaden[hier](https://releases.aspose.com/words/net/).
- .NET-omgeving: Zorg ervoor dat u een werkende .NET-ontwikkelomgeving hebt ingesteld. Visual Studio is een geweldige optie.
- Een Word-document met revisies: voor deze tutorial gebruiken we een voorbeeld van een Word-document met revisies (`Revisions.docx`).

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren in uw project. Dit is cruciaal om toegang te krijgen tot de Aspose.Words-functionaliteit.

```csharp
using Aspose.Words;
using System;
```

Oké, laten we dit stap voor stap opsplitsen. Elke stap begeleidt u door het proces van het verkrijgen van revisiegroepdetails met Aspose.Words voor .NET.

## Stap 1: Laad het Word-document

De eerste stap is om uw Word-document te laden. Dit is waar uw revisies worden opgeslagen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Revisions.docx");
```

 Vervang in dit fragment`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw document. Deze code laadt de`Revisions.docx` bestand in de`doc` voorwerp.

## Stap 2: Toegang tot de revisiecollectie

 Laten we nu de revisies in het document bekijken. Aspose.Words biedt een`Revisions` verzameling waar we doorheen kunnen itereren.

```csharp
foreach (Revision revision in doc.Revisions)
{
    // Verwerk elke revisie
}
```

Deze lus doorloopt elke revisie in het document, zodat we details kunnen extraheren.

## Stap 3: Revisiedetails extraheren

Binnen de lus kunnen we verschillende details over elke revisie extraheren, zoals het type, de auteur, de datum en de tekst.

```csharp
foreach (Revision revision in doc.Revisions)
{
    Console.WriteLine("Type: " + revision.RevisionType);
    Console.WriteLine("Author: " + revision.Author);
    Console.WriteLine("Date: " + revision.DateTime);
    Console.WriteLine("Revision text: " + revision.ParentNode.ToString(SaveFormat.Text));
}
```

Met deze code worden het revisietype, de auteur, de datum en de tekst op de console weergegeven.

## Stap 4: Controleer op revisiegroep

Soms worden revisies gegroepeerd. We moeten controleren of een revisie tot een groep behoort en de tekst van de groep weergeven als dat zo is.

```csharp
foreach (Revision revision in doc.Revisions)
{
    string groupText = revision.Group != null
        ? "Revision group text: " + revision.Group.Text
        : "The revision does not belong to any group";

    Console.WriteLine(groupText);
}
```

Met dit fragment wordt de groepstekst afgedrukt als de revisie deel uitmaakt van een groep of wordt aangegeven dat de revisie niet tot een groep behoort.

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig gedetailleerde informatie over revisies in een Word-document krijgen met Aspose.Words voor .NET. Deze krachtige tool maakt het een fluitje van een cent om wijzigingen te beheren en te volgen, zodat je collaboratieve projecten soepel verlopen.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Het is een krachtige .NET-bibliotheek voor het programmatisch maken, bewerken, converteren en afdrukken van Word-documenten.

### Kan ik Aspose.Words voor .NET gebruiken met andere .NET-talen?
Absoluut! Je kunt het gebruiken met elke .NET-taal, inclusief C#, VB.NET en ASP.NET.

### Hoe kan ik een gratis proefversie van Aspose.Words voor .NET krijgen?
 U kunt een gratis proefperiode krijgen[hier](https://releases.aspose.com/).

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?
 Ja, Aspose.Words voor .NET vereist een licentie voor volledige functionaliteit. U kunt er een kopen[hier](https://purchase.aspose.com/buy) of een tijdelijke licentie krijgen[hier](https://purchase.aspose.com/temporary-license/).

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?
 Gedetailleerde documentatie is beschikbaar[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
