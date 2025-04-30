---
"description": "Leer hoe u bladwijzerinhoud in Word-documenten kunt weergeven en verbergen met Aspose.Words voor .NET met deze gedetailleerde, stapsgewijze handleiding."
"linktitle": "Toon/verberg gemarkeerde inhoud in Word-document"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Toon/verberg gemarkeerde inhoud in Word-document"
"url": "/nl/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Toon/verberg gemarkeerde inhoud in Word-document

## Invoering

Klaar om de wereld van documentmanipulatie met Aspose.Words voor .NET te betreden? Of je nu een ontwikkelaar bent die documenttaken wil automatiseren of gewoon nieuwsgierig bent naar het programmatisch verwerken van Word-bestanden, je bent hier aan het juiste adres. Vandaag onderzoeken we hoe je bladwijzers in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze stapsgewijze handleiding maakt van jou een expert in het beheren van de zichtbaarheid van content op basis van bladwijzers. Laten we beginnen!

## Vereisten

Voordat we in de details duiken, heb je een paar dingen nodig:

1. Visual Studio: elke versie die compatibel is met .NET.
2. Aspose.Words voor .NET: Download het [hier](https://releases.aspose.com/words/net/).
3. Basiskennis van C#: Als je een eenvoudig "Hallo wereld"-programma kunt schrijven, kun je aan de slag.
4. Een Word-document met bladwijzers: voor deze tutorial gebruiken we een voorbeelddocument met bladwijzers.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Zo beschikken we over alle tools die we nodig hebben voor onze taak.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Nu deze naamruimten zijn ingesteld, kunnen we aan onze reis beginnen.

## Stap 1: Uw project instellen

Oké, laten we beginnen met het instellen van ons project in Visual Studio.

### Een nieuw project maken

Open Visual Studio en maak een nieuw Console App (.NET Core)-project. Geef het een pakkende naam, bijvoorbeeld 'BookmarkVisibilityManager'.

### Aspose.Words toevoegen voor .NET

Je moet Aspose.Words voor .NET aan je project toevoegen. Dit kun je doen via NuGet Package Manager.

1. Ga naar Extra > NuGet Package Manager > NuGet-pakketten beheren voor oplossing.
2. Zoek naar "Aspose.Words".
3. Installeer het pakket.

Geweldig! Nu ons project is ingesteld, kunnen we verder met het laden van ons document.

## Stap 2: Het document laden

We moeten het Word-document met de bladwijzers laden. Voor deze tutorial gebruiken we een voorbeelddocument met de naam 'Bladwijzers.docx'.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Met dit codefragment wordt het pad naar uw documentmap ingesteld en wordt het document in de map geladen. `doc` voorwerp.

## Stap 3: Toon/verberg gemarkeerde inhoud

Nu komt het leuke gedeelte: de inhoud weergeven of verbergen op basis van bladwijzers. We maken een methode genaamd `ShowHideBookmarkedContent` om hiermee om te gaan.

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

- Bladwijzer ophalen: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` haalt de bladwijzer op.
- Knooppuntdoorkruising: We doorkruisen de knooppunten binnen de bladwijzer.
- Zichtbaarheidsschakelaar: Als het knooppunt een `Run` (een aaneengesloten tekstgedeelte), we stellen het in `Hidden` eigendom.

## Stap 4: De methode toepassen

Nu we de methode hebben geïmplementeerd, kunnen we deze gebruiken om inhoud weer te geven of te verbergen op basis van een bladwijzer.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Met deze regel code wordt de inhoud van de bladwijzer met de naam "MyBookmark1" verborgen.

## Stap 5: Het document opslaan

Laten we tot slot ons gewijzigde document opslaan.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Hiermee wordt het document opgeslagen met de wijzigingen die we hebben aangebracht.

## Conclusie

En voilà! Je hebt net geleerd hoe je bladwijzerinhoud in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze krachtige tool maakt documentbewerking een fluitje van een cent, of je nu rapporten automatiseert, sjablonen maakt of gewoon aan Word-bestanden sleutelt. Veel plezier met programmeren!

## Veelgestelde vragen

### Kan ik meerdere bladwijzers tegelijk in- of uitschakelen?
Ja, u kunt de `ShowHideBookmarkedContent` voor elke bladwijzer die u wilt in- of uitschakelen.

### Heeft het verbergen van inhoud invloed op de structuur van het document?
Nee, het verbergen van inhoud heeft alleen invloed op de zichtbaarheid. De inhoud blijft in het document.

### Kan ik deze methode gebruiken voor andere soorten content?
Deze methode schakelt specifiek tekstuitvoeringen in of uit. Voor andere inhoudstypen moet u de logica voor het doorlopen van knooppunten aanpassen.

### Is Aspose.Words voor .NET gratis?
Aspose.Words biedt een gratis proefperiode aan [hier](https://releases.aspose.com/), maar voor productiegebruik is een volledige licentie vereist. U kunt deze aanschaffen [hier](https://purchase.aspose.com/buy).

### Hoe kan ik ondersteuning krijgen als ik problemen ondervind?
Je kunt ondersteuning krijgen van de Aspose-community [hier](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}