---
title: Document invoegen bij samenvoeging
linktitle: Document invoegen bij samenvoeging
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u documenten in samenvoegvelden kunt invoegen met Aspose.Words voor .NET in deze uitgebreide, stapsgewijze zelfstudie.
weight: 10
url: /nl/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document invoegen bij samenvoeging

## Invoering

Welkom in de wereld van documentautomatisering met Aspose.Words voor .NET! Heb je je ooit afgevraagd hoe je dynamisch documenten in specifieke velden in een hoofddocument kunt invoegen tijdens een samenvoegbewerking? Nou, dan ben je hier aan het juiste adres. Deze tutorial leidt je stap voor stap door het proces van het invoegen van documenten in samenvoegvelden met Aspose.Words voor .NET. Het is alsof je een puzzel in elkaar zet, waarbij elk stukje perfect op zijn plaats valt. Dus, laten we erin duiken!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1.  Aspose.Words voor .NET: Je kunt[Download hier de nieuwste versie](https://releases.aspose.com/words/net/) . Als u een licentie moet aanschaffen, kunt u dat doen[hier](https://purchase.aspose.com/buy) . Als alternatief kunt u een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) of probeer het eens met een[gratis proefperiode](https://releases.aspose.com/).
2. Ontwikkelomgeving: Visual Studio of een andere C# IDE.
3. Basiskennis van C#: Als u bekend bent met C#-programmering, is deze tutorial een fluitje van een cent.

## Naamruimten importeren

Allereerst moet u de benodigde namespaces importeren. Deze zijn als het ware de bouwstenen van uw project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Laten we het proces opsplitsen in beheersbare stappen. Elke stap bouwt voort op de vorige, wat leidt tot een complete oplossing.

## Stap 1: Uw directory instellen

Voordat u documenten kunt invoegen, moet u het pad naar uw documentenmap definiëren. Dit is waar uw documenten worden opgeslagen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Het hoofddocument laden

Vervolgens laadt u het hoofddocument. Dit document bevat de samenvoegvelden waar andere documenten worden ingevoegd.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Stap 3: De callback voor het samenvoegen van velden instellen

Om het samenvoegingsproces te verwerken, moet u een callbackfunctie instellen. Deze functie is verantwoordelijk voor het invoegen van documenten in de opgegeven samenvoegvelden.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Stap 4: De samenvoegbewerking uitvoeren

Nu is het tijd om de mail merge uit te voeren. Dit is waar de magie gebeurt. U specificeert het merge-veld en het document dat in dit veld moet worden ingevoegd.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Stap 5: Het document opslaan

Nadat de samenvoeging is voltooid, slaat u het gewijzigde document op. Dit nieuwe document heeft de ingevoegde inhoud precies waar u het wilt hebben.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Stap 6: De callback-handler maken

De callback handler is een klasse die speciale verwerking uitvoert voor het samenvoegveld. Het laadt het document dat is opgegeven in de veldwaarde en voegt het in het huidige samenvoegveld in.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Stap 7: Het document invoegen

Met deze methode wordt het opgegeven document in de huidige alinea of tabelcel ingevoegd.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Conclusie

En daar heb je het! Je hebt met succes documenten in specifieke velden ingevoegd tijdens een mail merge-bewerking met Aspose.Words voor .NET. Deze krachtige functie kan je een hoop tijd en moeite besparen, vooral als je met grote hoeveelheden documenten werkt. Zie het als een persoonlijke assistent die al het zware werk voor je doet. Dus ga je gang en probeer het eens. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik meerdere documenten in verschillende samenvoegvelden invoegen?
Ja, dat kan. Geef gewoon de juiste samenvoegvelden en bijbehorende documentpaden op in de`MailMerge.Execute` methode.

### Is het mogelijk om het ingevoegde document anders op te maken dan het hoofddocument?
 Absoluut! Je kunt de`ImportFormatMode` parameter in de`NodeImporter` om de opmaak te beheren.

### Wat als de samenvoegveldnaam dynamisch is?
U kunt dynamische samenvoegveldnamen verwerken door ze als parameters door te geven aan de callbackhandler.

### Kan ik deze methode gebruiken met verschillende bestandsformaten?
Ja, Aspose.Words ondersteunt verschillende bestandsformaten, waaronder DOCX, PDF en meer.

### Hoe ga ik om met fouten tijdens het invoegen van documenten?
Implementeer foutverwerking in uw callback-handler om eventuele uitzonderingen te beheren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
