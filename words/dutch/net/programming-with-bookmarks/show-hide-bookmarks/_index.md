---
title: Toon bladwijzers verbergen in Word-document
linktitle: Toon bladwijzers verbergen in Word-document
second_title: Aspose.Words-API voor documentverwerking
description: Leer hoe u bladwijzers in een Word-document dynamisch kunt weergeven of verbergen met Aspose.Words voor .NET met onze stapsgewijze handleiding. Ideaal voor ontwikkelaars.
weight: 10
url: /nl/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Toon bladwijzers verbergen in Word-document

## Invoering

Ooit gemerkt dat u bepaalde delen van uw Word-document dynamisch moest verbergen of weergeven? Nou, je hebt geluk! Met Aspose.Words voor .NET kunt u eenvoudig de zichtbaarheid van inhoud met bladwijzers in uw documenten beheren. Deze zelfstudie leidt u door het proces van het weergeven en verbergen van bladwijzers in een Word-document met behulp van Aspose.Words voor .NET. We zullen de code stap voor stap opsplitsen, dus of u nu een doorgewinterde ontwikkelaar of een nieuweling bent, deze handleiding is gemakkelijk te volgen.

## Vereisten

Voordat we in de code duiken, zorgen we ervoor dat je alles hebt wat je nodig hebt:

1.  Aspose.Words voor .NET: Zorg ervoor dat de Aspose.Words voor .NET-bibliotheek is geïnstalleerd. Zo niet, dan kunt u deze downloaden[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: een IDE zoals Visual Studio.
3. Basiskennis van C#: Bekendheid met programmeren in C# is een voordeel.
4. Een Word-document: een voorbeeld van een Word-document met bladwijzers.

## Naamruimten importeren

Voordat u met de code begint, moet u de benodigde naamruimten importeren. Voeg het volgende toe aan het begin van uw C#-bestand:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Stap 1: Laad uw document

Allereerst moet u het Word-document laden dat de bladwijzers bevat. Hier ziet u hoe u het kunt doen:

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Uitleg

- dataDir: Dit is het mappad waar uw Word-document zich bevindt.
-  Documentdocument: Hiermee wordt een nieuw exemplaar van het`Document` klasse met het door u opgegeven bestand.

## Stap 2: Toon of verberg bladwijzerinhoud

Vervolgens definiëren we een methode om de inhoud met bladwijzer weer te geven of te verbergen. Hier is de volledige methode:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD-bladwijzer}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Uitleg

- Bladwijzer bm: Haalt de bladwijzer op uit het document.
- DocumentBuilder-builder: Helpt bij het navigeren en wijzigen van het document.
- Veldveld: Voegt een IF-veld in om de staat van de bladwijzer te controleren.
- Knooppunt currentNode: Doorloopt de knooppunten om het begin en einde van het veld te vinden.

## Stap 3: Voer de functie Show/Hide uit

 Nu moet je de`ShowHideBookmarkedContent` methode, waarbij het document, de bladwijzernaam en de zichtbaarheidsvlag worden doorgegeven:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Uitleg

- doc: uw documentobject.
- "MyBookmark1": De naam van de bladwijzer die u wilt tonen/verbergen.
- false: de zichtbaarheidsvlag (true voor tonen, false voor verbergen).

## Stap 4: Bewaar uw document

Sla ten slotte het gewijzigde document op:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Uitleg

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": het pad en de naam van het nieuwe document waar de wijzigingen worden opgeslagen.

## Conclusie

En daar heb je het! U hebt met succes geleerd hoe u bladwijzers in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze techniek kan ongelooflijk handig zijn voor het dynamisch genereren van documenten met voorwaardelijke inhoud.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor documentverwerking waarmee ontwikkelaars Word-documenten programmatisch kunnen maken, wijzigen en converteren.

### Hoe verkrijg ik Aspose.Words voor .NET?
 U kunt Aspose.Words voor .NET downloaden van[hier](https://releases.aspose.com/words/net/). Er is ook een gratis proefversie beschikbaar.

### Kan ik deze methode gebruiken voor andere soorten bladwijzers?
Ja, deze methode kan worden aangepast om de zichtbaarheid van bladwijzers in uw Word-document te beheren.

### Wat moet ik doen als mijn document de opgegeven bladwijzer niet bevat?
Als de bladwijzer niet bestaat, genereert de methode een fout. Zorg ervoor dat de bladwijzer bestaat voordat u deze probeert weer te geven/verbergen.

### Hoe kan ik ondersteuning krijgen als ik problemen tegenkom?
 U kunt ondersteuning krijgen van de Aspose-gemeenschap[hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
