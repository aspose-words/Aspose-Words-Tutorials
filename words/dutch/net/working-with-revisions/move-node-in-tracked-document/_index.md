---
"description": "Leer hoe je knooppunten in een bijgehouden Word-document kunt verplaatsen met Aspose.Words voor .NET met onze gedetailleerde, stapsgewijze handleiding. Perfect voor ontwikkelaars."
"linktitle": "Knooppunt verplaatsen in bijgehouden document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Knooppunt verplaatsen in bijgehouden document"
"url": "/nl/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Knooppunt verplaatsen in bijgehouden document

## Invoering

Hallo Aspose.Words-fans! Als je ooit een knooppunt in een Word-document moest verplaatsen terwijl je revisies bijhield, ben je hier aan het juiste adres. Vandaag duiken we in hoe je dit kunt doen met Aspose.Words voor .NET. Je leert niet alleen het stapsgewijze proces, maar je krijgt ook tips en trucs om je documentbewerking soepel en efficiënt te laten verlopen.

## Vereisten

Voordat we met code aan de slag gaan, controleren we eerst of je alles hebt wat je nodig hebt:

- Aspose.Words voor .NET: Download het [hier](https://releases.aspose.com/words/net/).
- .NET-omgeving: zorg ervoor dat u een compatibele .NET-ontwikkelomgeving hebt ingesteld.
- Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u een basiskennis van C# hebt.

Alles gevonden? Geweldig! Laten we verdergaan met de naamruimten die we moeten importeren.

## Naamruimten importeren

Allereerst moeten we de benodigde naamruimten importeren. Deze zijn essentieel voor het werken met Aspose.Words en het verwerken van documentknooppunten.

```csharp
using Aspose.Words;
using System;
```

Oké, laten we het proces opsplitsen in beheersbare stappen. Elke stap wordt gedetailleerd uitgelegd, zodat je begrijpt wat er op elk punt gebeurt.

## Stap 1: Initialiseer het document

Om te beginnen moeten we een nieuw document initialiseren en een `DocumentBuilder` om een paar alinea's toe te voegen.

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

// Controleer het aantal alinea's in de eerste alinea
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Stap 2: Begin met het bijhouden van revisies

Vervolgens moeten we de revisies bijhouden. Dit is cruciaal, omdat we zo de wijzigingen in het document kunnen zien.

```csharp
// Begin met het bijhouden van revisies
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Stap 3: Verplaats knooppunten

Nu komt het kernonderdeel van onze taak: een knooppunt van de ene naar de andere locatie verplaatsen. We verplaatsen de derde alinea en plaatsen deze vóór de eerste alinea.

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

Ten slotte slaan we ons gewijzigde document op in de opgegeven directory.

```csharp
// Sla het gewijzigde document op
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Geef het laatste alinea-aantal weer
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Conclusie

En voilà! Je hebt met succes een knooppunt in een bijgehouden document verplaatst met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het eenvoudig om Word-documenten programmatisch te bewerken. Of je nu documenten maakt, bewerkt of wijzigingen bijhoudt, Aspose.Words helpt je verder. Dus ga je gang en probeer het eens. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?

Aspose.Words voor .NET is een klassenbibliotheek voor het programmatisch werken met Word-documenten. Hiermee kunnen ontwikkelaars Word-documenten maken, bewerken, converteren en afdrukken binnen .NET-applicaties.

### Hoe kan ik revisies in een Word-document bijhouden met Aspose.Words?

Om revisies bij te houden, gebruikt u de `StartTrackRevisions` methode op de `Document` object. Hiermee wordt het bijhouden van revisies ingeschakeld, zodat alle wijzigingen in het document worden weergegeven.

### Kan ik meerdere knooppunten verplaatsen in Aspose.Words?

Ja, u kunt meerdere knooppunten verplaatsen door eroverheen te itereren en methoden te gebruiken zoals `InsertBefofe` or `InsertAfter` om ze op de gewenste locatie te plaatsen.

### Hoe stop ik het bijhouden van revisies in Aspose.Words?

Gebruik de `StopTrackRevisions` methode op de `Document` bezwaar maken om het bijhouden van revisies te stoppen.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

Gedetailleerde documentatie vindt u hier [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}