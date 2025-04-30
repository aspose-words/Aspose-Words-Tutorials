---
"description": "Leer hoe je naadloos een Word-document in een ander kunt invoegen met Aspose.Words voor .NET met onze gedetailleerde, stapsgewijze handleiding. Perfect voor ontwikkelaars die documentverwerking willen stroomlijnen."
"linktitle": "Document invoegen bij vervangen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Document invoegen bij vervangen"
"url": "/nl/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Document invoegen bij vervangen

## Invoering

Hé, documentmeesters! Heb je ooit tot over je oren in de code gezeten en geprobeerd uit te zoeken hoe je het ene Word-document naadloos in het andere kunt invoegen? Geen zorgen, want vandaag duiken we in de wereld van Aspose.Words voor .NET om die taak een fluitje van een cent te maken. We doorlopen een gedetailleerde, stapsgewijze handleiding over het gebruik van deze krachtige bibliotheek om documenten op specifieke punten tijdens een zoek-en-vervangbewerking in te voegen. Klaar om een Aspose.Words-wizard te worden? Laten we beginnen!

## Vereisten

Voordat we met de code aan de slag gaan, zijn er een paar dingen die je moet regelen:

- Visual Studio: Zorg ervoor dat Visual Studio op uw computer is geïnstalleerd. Als u het nog niet hebt, kunt u het downloaden van [hier](https://visualstudio.microsoft.com/).
- Aspose.Words voor .NET: Je hebt de Aspose.Words-bibliotheek nodig. Deze kun je vinden in de [Aspose-website](https://releases.aspose.com/words/net/).
- Basiskennis van C#: Met een basiskennis van C# en .NET kunt u deze tutorial gemakkelijk volgen.

Oké, nu we dat gehad hebben, kunnen we aan de slag met de code!

## Naamruimten importeren

Allereerst moeten we de benodigde naamruimten importeren om met Aspose.Words te kunnen werken. Dit is vergelijkbaar met het verzamelen van al je tools voordat je een project start. Voeg deze toe met behulp van richtlijnen bovenaan je C#-bestand:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nu we onze randvoorwaarden op orde hebben, kunnen we het proces opsplitsen in kleine stapjes. Elke stap is cruciaal en brengt ons dichter bij ons doel.

## Stap 1: De documentenmap instellen

Eerst moeten we de directory specificeren waar onze documenten worden opgeslagen. Dit is vergelijkbaar met het voorbereiden van de grote voorstelling.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het pad naar uw map. Dit is waar uw documenten leven en ademen.

## Stap 2: Laad het hoofddocument

Vervolgens laden we het hoofddocument waarin we een ander document willen invoegen. Zie dit als onze hoofdfase waar alle actie plaatsvindt.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Deze code laadt het hoofddocument vanuit de opgegeven directory.

## Stap 3: Zoek- en vervangopties instellen

Om de specifieke locatie te vinden waar we ons document willen invoegen, gebruiken we de zoek-en-vervangfunctie. Dit is vergelijkbaar met het gebruiken van een kaart om de exacte locatie voor onze nieuwe toevoeging te vinden.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Hier stellen we de richting in op achterwaarts en specificeren we een aangepaste callback-handler die we hierna zullen definiëren.

## Stap 4: De vervangingsbewerking uitvoeren

Nu vertellen we het hoofddocument om te zoeken naar een specifieke tijdelijke aanduidingstekst en deze door niets te vervangen, terwijl we onze aangepaste callback gebruiken om een ander document in te voegen.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Deze code voert de zoek- en vervangbewerking uit en slaat vervolgens het bijgewerkte document op.

## Stap 5: Een aangepaste vervangende callback-handler maken

Onze aangepaste callback-handler is waar het allemaal gebeurt. Deze handler definieert hoe het invoegen van documenten wordt uitgevoerd tijdens de zoek- en vervangbewerking.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Voeg een document in na de alinea met de overeenkomende tekst.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Verwijder de alinea met de overeenkomende tekst.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Hier laden we het document dat moet worden ingevoegd en roepen we vervolgens een hulpmethode aan om de invoeging uit te voeren.

## Stap 6: Definieer de methode Document invoegen

Het laatste stukje van onze puzzel is de methode waarmee het document daadwerkelijk op de opgegeven locatie wordt ingevoegd.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Controleer of de invoegbestemming een alinea of tabel is
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Maak een NodeImporter om knooppunten uit het brondocument te importeren
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Loop door alle knooppunten op blokniveau in de secties van het brondocument
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Sla de laatste lege alinea van een sectie over
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importeer en voeg het knooppunt in de bestemming in
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Deze methode zorgt ervoor dat de knooppunten uit het document worden geïmporteerd en op de juiste plaats in het hoofddocument worden geplaatst.

## Conclusie

En voilà! Een uitgebreide handleiding voor het invoegen van één document in een ander met Aspose.Words voor .NET. Door deze stappen te volgen, kunt u eenvoudig taken voor het samenstellen en bewerken van documenten automatiseren. Of u nu een documentbeheersysteem bouwt of gewoon uw workflow voor documentverwerking wilt stroomlijnen, Aspose.Words is uw vertrouwde partner.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch bewerken van Word-documenten. Hiermee kunt u Word-documenten eenvoudig maken, wijzigen, converteren en verwerken.

### Kan ik meerdere documenten tegelijk invoegen?
Ja, u kunt de callback-handler aanpassen om meerdere invoegingen te verwerken door over een verzameling documenten te itereren.

### Is er een gratis proefperiode beschikbaar?
Absoluut! Je kunt een gratis proefversie downloaden van [hier](https://releases.aspose.com/).

### Hoe krijg ik ondersteuning voor Aspose.Words?
U kunt ondersteuning krijgen door de [Aspose.Words forum](https://forum.aspose.com/c/words/8).

### Kan ik de opmaak van het ingevoegde document behouden?
Ja, de `NodeImporter` Met de klasse kunt u opgeven hoe opmaak wordt verwerkt bij het importeren van knooppunten van het ene document naar het andere.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}