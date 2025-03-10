---
title: Verplaats knooppunt in bijgehouden document
linktitle: Verplaats knooppunt in bijgehouden document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u knooppunten in een bijgehouden Word-document verplaatst met Aspose.Words voor .NET met onze gedetailleerde, stapsgewijze handleiding. Perfect voor ontwikkelaars.
weight: 10
url: /nl/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verplaats knooppunt in bijgehouden document

## Invoering

Hallo, Aspose.Words-enthousiastelingen! Als u ooit een knooppunt in een Word-document moest verplaatsen terwijl u revisies bijhield, bent u hier aan het juiste adres. Vandaag duiken we in hoe u dit kunt bereiken met Aspose.Words voor .NET. U leert niet alleen het stapsgewijze proces, maar u krijgt ook een aantal tips en trucs om uw documentmanipulatie soepel en efficiënt te maken.

## Vereisten

Voordat we aan de slag gaan met code, controleren we eerst of je alles hebt wat je nodig hebt:

-  Aspose.Words voor .NET: Download het[hier](https://releases.aspose.com/words/net/).
- .NET-omgeving: Zorg ervoor dat u een compatibele .NET-ontwikkelomgeving hebt ingesteld.
- Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u basiskennis van C# hebt.

Alles ontvangen? Geweldig! Laten we verdergaan met de naamruimten die we moeten importeren.

## Naamruimten importeren

Allereerst moeten we de benodigde namespaces importeren. Deze zijn essentieel voor het werken met Aspose.Words en het verwerken van document nodes.

```csharp
using Aspose.Words;
using System;
```

Oké, laten we het proces opsplitsen in beheersbare stappen. Elke stap wordt gedetailleerd uitgelegd om ervoor te zorgen dat u begrijpt wat er op elk punt gebeurt.

## Stap 1: Initialiseer het document

 Om te beginnen moeten we een nieuw document initialiseren en een`DocumentBuilder` om enkele paragrafen toe te voegen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Enkele alinea's toevoegen
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Controleer het aantal eerste alinea's
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Stap 2: Begin met het bijhouden van revisies

Vervolgens moeten we revisies gaan bijhouden. Dit is cruciaal omdat we hiermee de wijzigingen in het document kunnen zien.

```csharp
// Begin met het bijhouden van revisies
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Stap 3: Verplaats knooppunten

Nu komt het kerngedeelte van onze taak: een knooppunt van de ene locatie naar de andere verplaatsen. We verplaatsen de derde paragraaf en plaatsen deze voor de eerste paragraaf.

```csharp
// Definieer het te verplaatsen knooppunt en het eindbereik ervan
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Verplaats de knooppunten binnen het gedefinieerde bereik
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Stap 4: Stop met het bijhouden van revisies

Zodra we de knooppunten hebben verplaatst, moeten we stoppen met het bijhouden van revisies.

```csharp
// Stop met het bijhouden van revisies
doc.StopTrackRevisions();
```

## Stap 5: Sla het document op

Laten we ten slotte ons gewijzigde document opslaan in de opgegeven directory.

```csharp
// Sla het gewijzigde document op
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Geef het aantal laatste alinea's weer
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Conclusie

En daar heb je het! Je hebt succesvol een knooppunt verplaatst in een bijgehouden document met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het eenvoudig om Word-documenten programmatisch te manipuleren. Of je nu wijzigingen maakt, bewerkt of bijhoudt, Aspose.Words heeft het allemaal. Dus ga je gang en probeer het eens. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?

Aspose.Words voor .NET is een klassenbibliotheek voor het programmatisch werken met Word-documenten. Hiermee kunnen ontwikkelaars Word-documenten maken, bewerken, converteren en afdrukken binnen .NET-toepassingen.

### Hoe kan ik revisies in een Word-document bijhouden met Aspose.Words?

 Om revisies bij te houden, gebruikt u de`StartTrackRevisions` methode op de`Document` object. Dit schakelt revisietracking in, waarbij alle wijzigingen in het document worden weergegeven.

### Kan ik meerdere knooppunten verplaatsen in Aspose.Words?

Ja, u kunt meerdere knooppunten verplaatsen door eroverheen te itereren en methoden te gebruiken zoals`InsertBefore` of`InsertAfter` om ze op de gewenste locatie te plaatsen.

### Hoe stop ik het bijhouden van revisies in Aspose.Words?

 Gebruik de`StopTrackRevisions` methode op de`Document` bezwaar maken tegen het stoppen van het bijhouden van revisies.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

 Gedetailleerde documentatie vindt u hier[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
