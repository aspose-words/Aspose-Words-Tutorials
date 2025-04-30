---
"description": "Kopieer moeiteloos tekst met bladwijzers tussen Word-documenten met Aspose.Words voor .NET. Leer hoe met deze stapsgewijze handleiding."
"linktitle": "Kopieer bladwijzertekst in Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Kopieer bladwijzertekst in Word-document"
"url": "/nl/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kopieer bladwijzertekst in Word-document

## Invoering

Heb je ooit specifieke secties van het ene Word-document naar het andere moeten kopiëren? Dan heb je geluk! In deze tutorial laten we je zien hoe je gemarkeerde tekst van het ene Word-document naar het andere kopieert met Aspose.Words voor .NET. Of je nu een dynamisch rapport maakt of de documentgeneratie automatiseert, deze handleiding maakt het proces een stuk eenvoudiger.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

- Aspose.Words voor .NET-bibliotheek: U kunt het downloaden van [hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere .NET-ontwikkelomgeving.
- Basiskennis van C#: Kennis van C#-programmering en het .NET Framework.

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde naamruimten in uw project hebt geïmporteerd:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Stap 1: Laad het brondocument

Allereerst moet u het brondocument laden dat de bladwijzertekst bevat die u wilt kopiëren.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Hier, `dataDir` is het pad naar uw documentenmap, en `Bookmarks.docx` is het bron document.

## Stap 2: Identificeer de bladwijzer

Selecteer vervolgens de bladwijzer die u wilt kopiëren uit het brondocument.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Vervangen `"MyBookmark1"` met de werkelijke naam van uw bladwijzer.

## Stap 3: Het doeldocument maken

Maak nu een nieuw document waarin de bladwijzertekst wordt gekopieerd.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Stap 4: Importeer gemarkeerde inhoud

Om ervoor te zorgen dat de stijlen en opmaak behouden blijven, gebruikt u `NodeImporter` om de gemarkeerde inhoud van het brondocument naar het doeldocument te importeren.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Stap 5: Definieer de AppendBookmarkedText-methode

Hier gebeurt de magie. Definieer een methode om het kopiëren van de gemarkeerde tekst af te handelen:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Stap 6: Sla het doeldocument op

Sla ten slotte het doeldocument op om de gekopieerde inhoud te controleren.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Conclusie

En dat is alles! Je hebt met succes bladwijzertekst van het ene Word-document naar het andere gekopieerd met Aspose.Words voor .NET. Deze methode is krachtig voor het automatiseren van documentbewerkingstaken, waardoor je workflow efficiënter en gestroomlijnder wordt.

## Veelgestelde vragen

### Kan ik meerdere bladwijzers tegelijk kopiëren?
Ja, u kunt door meerdere bladwijzers bladeren en dezelfde methode gebruiken om elke bladwijzer te kopiëren.

### Wat gebeurt er als de bladwijzer niet wordt gevonden?
De `Range.Bookmarks` eigendom zal terugkeren `null`Zorg er dus voor dat u dit geval zo afhandelt dat er geen uitzonderingen ontstaan.

### Kan ik de opmaak van de originele bladwijzer behouden?
Absoluut! Gebruik `ImportFormatMode.KeepSourceFormatting` Zorgt ervoor dat de originele opmaak behouden blijft.

### Is er een limiet aan de grootte van de gemarkeerde tekst?
Er is geen specifieke limiet, maar de prestaties kunnen variëren bij extreem grote documenten.

### Kan ik tekst kopiëren tussen verschillende Word-documentformaten?
Ja, Aspose.Words ondersteunt verschillende Word-formaten en de methode werkt met al deze formaten.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}