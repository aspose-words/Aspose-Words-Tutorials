---
title: Document invoegen bij vervangen
linktitle: Document invoegen bij vervangen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u naadloos een Word-document in een ander kunt invoegen met Aspose.Words voor .NET met onze gedetailleerde, stapsgewijze handleiding. Perfect voor ontwikkelaars die documentverwerking willen stroomlijnen.
weight: 10
url: /nl/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document invoegen bij vervangen

## Invoering

Hallo, documentmeesters! Heb je ooit tot je knieën in de code gezeten om te proberen uit te vinden hoe je het ene Word-document naadloos in het andere kunt invoegen? Wees niet bang, want vandaag duiken we in de wereld van Aspose.Words voor .NET om die taak een fluitje van een cent te maken. We nemen je mee in een gedetailleerde, stapsgewijze handleiding over hoe je deze krachtige bibliotheek kunt gebruiken om documenten op specifieke punten in te voegen tijdens een zoek- en vervangbewerking. Ben je klaar om een Aspose.Words-wizard te worden? Laten we beginnen!

## Vereisten

Voordat we met de code aan de slag gaan, zijn er een paar dingen die je moet regelen:

-  Visual Studio: Zorg ervoor dat Visual Studio op uw machine is geïnstalleerd. Als u het nog niet hebt, kunt u het downloaden van[hier](https://visualstudio.microsoft.com/).
-  Aspose.Words voor .NET: U hebt de Aspose.Words-bibliotheek nodig. U kunt deze verkrijgen via de[Aspose-website](https://releases.aspose.com/words/net/).
- Basiskennis van C#: Een basiskennis van C# en .NET helpt u bij het volgen van deze tutorial.

Oké, nu we dat gedaan hebben, kunnen we aan de slag met wat code!

## Naamruimten importeren

Allereerst moeten we de benodigde namespaces importeren om met Aspose.Words te werken. Dit is alsof je al je tools verzamelt voordat je een project start. Voeg deze toe met behulp van directives bovenaan je C#-bestand:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nu we onze vereisten op orde hebben, kunnen we het proces opsplitsen in kleine stapjes. Elke stap is cruciaal en brengt ons dichter bij ons doel.

## Stap 1: De documentenmap instellen

Eerst moeten we de directory specificeren waar onze documenten worden opgeslagen. Dit is alsof we het podium klaarzetten voor de grote voorstelling.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het pad naar uw directory. Dit is waar uw documenten zullen leven en ademen.

## Stap 2: Laad het hoofddocument

Vervolgens laden we het hoofddocument waarin we een ander document willen invoegen. Zie dit als onze hoofdfase waar alle actie zal plaatsvinden.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Deze code laadt het hoofddocument vanuit de opgegeven directory.

## Stap 3: Zoek- en vervangopties instellen

Om de specifieke locatie te vinden waar we ons document willen invoegen, gebruiken we de zoek- en vervangfunctionaliteit. Dit is alsof je een kaart gebruikt om de exacte plek voor onze nieuwe toevoeging te vinden.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Hier stellen we de richting in op achterwaarts en specificeren we een aangepaste callbackhandler die we hierna zullen definiëren.

## Stap 4: Voer de vervangingsbewerking uit

Nu vertellen we ons hoofddocument om te zoeken naar een specifieke tijdelijke aanduidingstekst en deze door niets te vervangen, terwijl we onze aangepaste callback gebruiken om een ander document in te voegen.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Deze code voert de zoek- en vervangbewerking uit en slaat vervolgens het bijgewerkte document op.

## Stap 5: Maak een aangepaste vervangende callback-handler

Onze aangepaste callback-handler is waar de magie gebeurt. Deze handler definieert hoe de documentinvoeging wordt uitgevoerd tijdens de zoek- en vervangbewerking.

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

Deze methode zorgt ervoor dat de knooppunten uit het document die ingevoegd moeten worden, worden geïmporteerd en op de juiste plaats in het hoofddocument worden geplaatst.

## Conclusie

En daar heb je het! Een uitgebreide handleiding voor het invoegen van één document in een ander met Aspose.Words voor .NET. Door deze stappen te volgen, kun je eenvoudig taken voor het samenstellen en manipuleren van documenten automatiseren. Of je nu een documentbeheersysteem bouwt of gewoon je documentverwerkingsworkflow wilt stroomlijnen, Aspose.Words is je trouwe hulpje.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch manipuleren van Word-documenten. Hiermee kunt u Word-documenten eenvoudig maken, wijzigen, converteren en verwerken.

### Kan ik meerdere documenten tegelijk invoegen?
Ja, u kunt de callback-handler aanpassen om meerdere invoegingen te verwerken door over een verzameling documenten te itereren.

### Is er een gratis proefversie beschikbaar?
 Absoluut! U kunt een gratis proefversie downloaden van[hier](https://releases.aspose.com/).

### Hoe krijg ik ondersteuning voor Aspose.Words?
 U kunt ondersteuning krijgen door de[Aspose.Words-forum](https://forum.aspose.com/c/words/8).

### Kan ik de opmaak van het ingevoegde document behouden?
 Ja, de`NodeImporter` Met de klasse kunt u opgeven hoe opmaak wordt verwerkt bij het importeren van knooppunten van het ene document naar het andere.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
