---
title: Bladwijzertekst toevoegen in Word-document
linktitle: Bladwijzertekst toevoegen in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u bladwijzertekst toevoegt aan een Word-document met Aspose.Words voor .NET met deze stapsgewijze handleiding. Perfect voor ontwikkelaars.
weight: 10
url: /nl/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bladwijzertekst toevoegen in Word-document

## Invoering

Hallo! Heb je ooit geprobeerd om tekst toe te voegen van een bladwijzersectie in een Word-document en vond je het lastig? Je hebt geluk! Deze tutorial leidt je door het proces met Aspose.Words voor .NET. We delen het op in eenvoudige stappen, zodat je het gemakkelijk kunt volgen. Laten we erin duiken en die bladwijzertekst toevoegen als een pro!

## Vereisten

Voordat we beginnen, controleren we of je alles hebt wat je nodig hebt:

-  Aspose.Words voor .NET: Zorg dat je het hebt geïnstalleerd. Zo niet, dan kun je[download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Elke .NET-ontwikkelomgeving zoals Visual Studio.
- Basiskennis van C#: Het is handig om de basisconcepten van C#-programmering te begrijpen.
- Word-document met bladwijzers: een Word-document met bladwijzers, waaruit we tekst gaan toevoegen.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Zo zorgen we ervoor dat we alle tools die we nodig hebben binnen handbereik hebben.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Laten we het voorbeeld opsplitsen in gedetailleerde stappen.

## Stap 1: Laad het document en initialiseer variabelen

Oké, laten we beginnen met het laden van ons Word-document en het initialiseren van de variabelen die we nodig hebben.

```csharp
// Laad de bron- en doeldocumenten.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initialiseer de documentimporter.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Zoek de bladwijzer in het brondocument.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Stap 2: Identificeer de begin- en eindalinea's

Laten we nu de paragrafen lokaliseren waar de bladwijzer begint en eindigt. Dit is cruciaal omdat we de tekst binnen deze grenzen moeten verwerken.

```csharp
// Dit is de alinea die het begin van de bladwijzer bevat.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Dit is de alinea die het einde van de bladwijzer bevat.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Stap 3: Valideer de paragrafenouders

We moeten ervoor zorgen dat de begin- en eindparagrafen dezelfde ouder hebben. Dit is een eenvoudig scenario om de zaken overzichtelijk te houden.

```csharp
// Beperk ons tot een redelijk eenvoudig scenario.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Stap 4: Identificeer het knooppunt dat gestopt moet worden

Vervolgens moeten we het knooppunt bepalen waar we stoppen met het kopiëren van tekst. Dit is het knooppunt direct na de laatste alinea.

```csharp
// We willen alle alinea's kopiëren van de beginalinea tot en met de eindalinea,
// Het knooppunt waar we stoppen, bevindt zich dus ná de laatste alinea.
Node endNode = endPara.NextSibling;
```

## Stap 5: Voeg bladwijzertekst toe aan het doeldocument

Laten we ten slotte door de knooppunten van de beginalinea tot het knooppunt na de eindalinea lopen en deze aan het doeldocument toevoegen.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Hiermee wordt een kopie van het huidige knooppunt gemaakt en geïmporteerd (geldig gemaakt) in de context
    // van het bestemmingsdocument. Importeren betekent stijlen en lijst-ID's correct aanpassen.
    Node newNode = importer.ImportNode(curNode, true);

    // Voeg het geïmporteerde knooppunt toe aan het doeldocument.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Sla het doeldocument op met de bijgevoegde tekst.
dstDoc.Save("appended_document.docx");
```

## Conclusie

En daar heb je het! Je hebt succesvol tekst toegevoegd van een bladwijzersectie in een Word-document met Aspose.Words voor .NET. Deze krachtige tool maakt documentmanipulatie een fluitje van een cent, en nu heb je nog een trucje in petto. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik tekst uit meerdere bladwijzers in één keer toevoegen?
Ja, u kunt het proces voor elke bladwijzer herhalen en de tekst dienovereenkomstig toevoegen.

### Wat als de begin- en eindalinea's verschillende ouders hebben?
Het huidige voorbeeld gaat ervan uit dat ze dezelfde ouder hebben. Voor verschillende ouders is een complexere afhandeling vereist.

### Kan ik de originele opmaak van de bijgevoegde tekst behouden?
 Absoluut! De`ImportFormatMode.KeepSourceFormatting` zorgt ervoor dat de originele opmaak behouden blijft.

### Is het mogelijk om tekst toe te voegen aan een specifieke positie in het doeldocument?
Ja, u kunt de tekst aan elke positie toevoegen door naar het gewenste knooppunt in het doeldocument te navigeren.

### Wat moet ik doen als ik tekst uit een bladwijzer aan een nieuwe sectie wil toevoegen?
U kunt een nieuwe sectie in het doeldocument maken en de tekst daar toevoegen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
