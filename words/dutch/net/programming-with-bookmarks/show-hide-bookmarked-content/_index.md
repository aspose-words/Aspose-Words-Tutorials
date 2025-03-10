---
title: Toon Verberg gemarkeerde inhoud in Word-document
linktitle: Toon Verberg gemarkeerde inhoud in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u bladwijzerinhoud in Word-documenten kunt weergeven en verbergen met Aspose.Words voor .NET met deze gedetailleerde, stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Toon Verberg gemarkeerde inhoud in Word-document

## Invoering

Klaar om te duiken in de wereld van documentmanipulatie met Aspose.Words voor .NET? Of u nu een ontwikkelaar bent die documenttaken wil automatiseren of gewoon nieuwsgierig bent naar het programmatisch verwerken van Word-bestanden, u bent hier aan het juiste adres. Vandaag gaan we onderzoeken hoe u bladwijzerinhoud in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze stapsgewijze handleiding maakt u een pro in het beheren van de zichtbaarheid van inhoud op basis van bladwijzers. Laten we beginnen!

## Vereisten

Voordat we in de details duiken, heb je een paar dingen nodig:

1. Visual Studio: elke versie die compatibel is met .NET.
2.  Aspose.Words voor .NET: Download het[hier](https://releases.aspose.com/words/net/).
3. Basiskennis van C#: Als u een eenvoudig "Hallo Wereld"-programma kunt schrijven, kunt u aan de slag.
4. Een Word-document met bladwijzers: Voor deze tutorial gebruiken we een voorbeelddocument met bladwijzers.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Dit zorgt ervoor dat we alle tools hebben die we nodig hebben voor onze taak.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Nu deze naamruimten zijn ingesteld, zijn we klaar om aan onze reis te beginnen.

## Stap 1: Uw project instellen

Oké, laten we beginnen met het instellen van ons project in Visual Studio.

### Een nieuw project maken

Open Visual Studio en maak een nieuw Console App (.NET Core)-project. Geef het een pakkende naam, zoals 'BookmarkVisibilityManager'.

### Aspose.Words voor .NET toevoegen

U moet Aspose.Words voor .NET toevoegen aan uw project. U kunt dit doen via NuGet Package Manager.

1. Ga naar Extra > NuGet Package Manager > NuGet-pakketten beheren voor oplossing.
2. Zoek naar "Aspose.Words".
3. Installeer het pakket.

Geweldig! Nu ons project is ingesteld, gaan we verder met het laden van ons document.

## Stap 2: Het document laden

We moeten het Word-document laden dat de bladwijzers bevat. Voor deze tutorial gebruiken we een voorbeelddocument met de naam "Bookmarks.docx".

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Met dit codefragment wordt het pad naar uw documentdirectory ingesteld en wordt het document in de map geladen.`doc` voorwerp.

## Stap 3: Toon/verberg gemarkeerde inhoud

Nu komt het leuke gedeelte: de content tonen of verbergen op basis van bladwijzers. We maken een methode genaamd`ShowHideBookmarkedContent` om hiermee om te gaan.

Dit is de methode om de zichtbaarheid van gemarkeerde inhoud in of uit te schakelen:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Uitsplitsing van de methode

-  Bladwijzer ophalen:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` haalt de bladwijzer op.
- Knooppuntdoorkruising: We doorkruisen de knooppunten binnen de bladwijzer.
-  Zichtbaarheidsschakelaar: Als het knooppunt een`Run` (een aaneengesloten tekstgedeelte), we stellen het in`Hidden` eigendom.

## Stap 4: De methode toepassen

Nu we de methode hebben geïmplementeerd, kunnen we deze gebruiken om inhoud weer te geven of te verbergen op basis van een bladwijzer.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Met deze coderegel wordt de inhoud van de bladwijzer met de naam "MyBookmark1" verborgen.

## Stap 5: Het document opslaan

Laten we tot slot ons gewijzigde document opslaan.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Hiermee wordt het document opgeslagen met de wijzigingen die we hebben aangebracht.

## Conclusie

En daar heb je het! Je hebt zojuist geleerd hoe je bladwijzerinhoud in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze krachtige tool maakt het manipuleren van documenten een fluitje van een cent, of je nu rapporten automatiseert, sjablonen maakt of gewoon aan Word-bestanden sleutelt. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik meerdere bladwijzers tegelijk in- en uitschakelen?
 Ja, u kunt de`ShowHideBookmarkedContent` methode voor elke bladwijzer die u wilt in- of uitschakelen.

### Heeft het verbergen van inhoud invloed op de structuur van het document?
Nee, het verbergen van content heeft alleen invloed op de zichtbaarheid. De content blijft in het document.

### Kan ik deze methode gebruiken voor andere soorten content?
Deze methode schakelt specifiek tekstruns in. Voor andere contenttypen moet u de node traversal logica aanpassen.

### Is Aspose.Words voor .NET gratis?
 Aspose.Words biedt een gratis proefperiode aan[hier](https://releases.aspose.com/) , maar voor productiegebruik is een volledige licentie vereist. U kunt het kopen[hier](https://purchase.aspose.com/buy).

### Hoe kan ik ondersteuning krijgen als ik problemen ondervind?
 U kunt ondersteuning krijgen van de Aspose-community[hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
