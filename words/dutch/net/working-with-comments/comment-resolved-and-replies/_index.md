---
title: Commentaar opgelost en antwoorden
linktitle: Commentaar opgelost en antwoorden
second_title: Aspose.Words API voor documentverwerking
description: Automatiseer het oplossen en beantwoorden van opmerkingen in Word-documenten met Aspose.Words voor .NET. Inclusief stapsgewijze handleiding.
weight: 10
url: /nl/net/working-with-comments/comment-resolved-and-replies/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Commentaar opgelost en antwoorden

## Invoering

Als u met Word-documenten werkt, hebt u waarschijnlijk te maken gehad met opmerkingen. Ze zijn geweldig voor samenwerking, maar het beheren ervan kan een gedoe zijn. Met Aspose.Words voor .NET kunt u het proces van het oplossen en beantwoorden van opmerkingen automatiseren. Deze gids leidt u door de stappen om dat te doen.

## Vereisten

Voordat u begint, moet u ervoor zorgen dat u het volgende bij de hand hebt:

1.  Aspose.Words voor .NET: U kunt het downloaden van[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Ingesteld met .NET Framework.
3. Basiskennis van C#: Kennis van de syntaxis en concepten.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Dit zorgt ervoor dat alle klassen en methoden die we nodig hebben direct beschikbaar zijn.

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

Laten we het proces opsplitsen in simpele, makkelijk te volgen stappen. Elke stap helpt je de code en de functionaliteit ervan te begrijpen.

## Stap 1: Laad het document

 Om te beginnen laadt u het Word-document met de opmerkingen. Gebruik de`Document` klasse hiervoor.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

 Deze regel code initialiseert een nieuwe`Document` object met het pad naar uw Word-document.

## Stap 2: opmerkingen ophalen

 Vervolgens moeten we alle opmerkingen in het document krijgen. We gebruiken de`GetChildNodes` methode om een verzameling op te halen`Comment` knooppunten.

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

Deze code haalt alle opmerkingen in het document op en slaat ze op in een`NodeCollection`.

## Stap 3: Toegang tot de bovenliggende opmerking

Voor ons voorbeeld richten we ons op de eerste opmerking in de verzameling. Dit wordt onze bovenliggende opmerking.

```csharp
Comment parentComment = (Comment)comments[0];
```

 Hier casten we het eerste knooppunt in de verzameling naar een`Comment` voorwerp.

## Stap 4: Loop door antwoorden

 Laten we nu door de antwoorden op de bovenliggende opmerking heen lopen. We gebruiken een`foreach` lus om over elk antwoord te itereren.

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

In deze lus printen we de ID van de vooroudercommentaar en de status ervan (of deze is voltooid of niet). Vervolgens markeren we elk antwoord als voltooid.

## Stap 5: Sla het document op

Sla ten slotte het gewijzigde document op in uw map.

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

Deze code slaat de wijzigingen op in een nieuw document, zodat uw oorspronkelijke bestand ongewijzigd blijft.

## Conclusie

Het verwerken van opmerkingen in Word-documenten hoeft geen handmatige klus te zijn. Met Aspose.Words voor .NET kunt u het proces automatiseren, wat tijd bespaart en fouten vermindert. Volg deze handleiding om opmerkingen in uw documenten efficiënt op te lossen en te beantwoorden.

## Veelgestelde vragen

### Kan ik andere opmerkingengerelateerde taken automatiseren met Aspose.Words voor .NET?  
Ja, u kunt verschillende taken automatiseren, zoals het toevoegen, verwijderen en wijzigen van opmerkingen.

### Is Aspose.Words voor .NET compatibel met .NET Core?  
Ja, Aspose.Words voor .NET ondersteunt zowel .NET Framework als .NET Core.

### Hoe kan ik een gratis proefversie van Aspose.Words voor .NET krijgen?  
 U kunt een gratis proefversie downloaden van[hier](https://releases.aspose.com/).

### Kan ik Aspose.Words voor .NET gebruiken om met andere documenttypen te werken?  
Ja, Aspose.Words ondersteunt verschillende formaten, waaronder DOCX, PDF, HTML en meer.

### Waar kan ik gedetailleerde documentatie vinden voor Aspose.Words voor .NET?  
 U kunt de documentatie raadplegen[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
