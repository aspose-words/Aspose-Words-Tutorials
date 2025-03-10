---
title: Ontwar rijbladwijzers in Word-document
linktitle: Ontwar rijbladwijzers in Word-document
second_title: Aspose.Words-API voor documentverwerking
description: Ontwar eenvoudig verwarde rijbladwijzers in uw Word-documenten met Aspose.Words voor .NET. Deze gids leidt u door het proces voor een schoner en veiliger bladwijzerbeheer.
weight: 10
url: /nl/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ontwar rijbladwijzers in Word-document

## Invoering

Bent u ooit een situatie tegengekomen waarbij het verwijderen van een rij in een Word-document door een bladwijzer andere bladwijzers in aangrenzende rijen in de war brengt? Dit kan ongelooflijk frustrerend zijn, vooral als je met complexe tabellen werkt. Gelukkig biedt Aspose.Words voor .NET een krachtige oplossing: het ontwarren van rijbladwijzers. 

Deze gids leidt u door het proces van het ontwarren van rijbladwijzers in uw Word-documenten met behulp van Aspose.Words voor .NET. We zullen de code opsplitsen in gemakkelijk te begrijpen stappen en het doel van elke functie uitleggen, zodat u die vervelende bladwijzerproblemen met vertrouwen kunt aanpakken.

## Vereisten

Voordat je erin duikt, heb je een paar dingen nodig:

1.  Aspose.Words voor .NET: Deze commerciële bibliotheek biedt functionaliteiten voor het programmatisch werken met Word-documenten. 2. U kunt een gratis proefversie downloaden van[downloadlink](https://releases.aspose.com/words/net/) of koop een licentie bij[kopen](https://purchase.aspose.com/buy).
3. AC# ontwikkelomgeving: Visual Studio of een andere C# IDE zal perfect werken.
4. Een Word-document met rijbladwijzers: We gebruiken een voorbeelddocument met de naam 'Tabelkolombladwijzers.docx' voor demonstratiedoeleinden.

## Naamruimten importeren

De eerste stap bestaat uit het importeren van de benodigde naamruimten in uw C#-project. Deze naamruimten bieden toegang tot de klassen en functionaliteiten die we gaan gebruiken vanuit Aspose.Words voor .NET:

```csharp
using Aspose.Words;
using System;
```

## Stap 1: Laad het Word-document

 We beginnen met het laden van het Word-document met de verwarde rijbladwijzers. De`Document` klasse verwerkt documentmanipulatie in Aspose.Words. Zo laadt u het document:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Vervang door uw documentlocatie
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Vergeet niet te vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad naar uw bestand "Tabelkolom bookmarks.docx".

## Stap 2: Ontwar rijbladwijzers

 Dit is waar de magie gebeurt! De`Untangle` functie zorgt voor het ontwarren van de rijbladwijzers. Laten we de functionaliteit ervan opsplitsen:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Haal de bovenliggende rij op van zowel de bladwijzer als het bladwijzereinde
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Controleer of rijen geldig en aangrenzend zijn
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Verplaats het bladwijzereinde naar de laatste alinea van de laatste cel van de bovenste rij
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Hier volgt een stapsgewijze uitleg van wat de code doet:

 We doorlopen alle bladwijzers in het document met behulp van a`foreach` lus.
Voor elke bladwijzer halen we de bovenliggende rij op van zowel de bladwijzerstart (`bookmark.BookmarkStart`) en het bladwijzereinde (`bookmark.BookmarkEnd` ) met behulp van de`GetAncestor` methode.
Vervolgens controleren we of beide rijen worden gevonden (`row1 != null`En`row2 != null`) en als het aangrenzende rijen zijn (`row1.NextSibling == row2`). Dit zorgt ervoor dat we alleen bladwijzers wijzigen die zich over aangrenzende rijen uitstrekken.
Als aan de voorwaarden is voldaan, verplaatsen we het eindknooppunt van de bladwijzer naar het einde van de laatste alinea in de laatste cel van de bovenste rij (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) om ze effectief te ontwarren.

## Stap 3: Rij per bladwijzer verwijderen

 Nu de bladwijzers zijn ontward, kunnen we veilig rijen verwijderen met behulp van hun bladwijzernamen. De`DeleteRowByBookmark` functie voert deze taak uit:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Hier is een overzicht van deze functie:

We nemen de bladwijzernaam (`bookmarkName`) als invoer.
 We halen het bijbehorende bladwijzerobject op met behulp van`doc.Range.Bookmarks[bookmarkName]`.
We krijgen dan de bovenliggende rij van de bladwijzer die we gaan gebruiken`GetAncestor` (vergelijkbaar met de`Untangle` functie).
Ten slotte controleren we of de bladwijzer en rij bestaan (`bookmark != null` En

## Stap 4: Controleer het ontwarren

 Terwijl de`Untangle` functie de veiligheid van andere bladwijzers moet garanderen, het is altijd een goede gewoonte om dit te verifiëren. Zo kunnen we controleren of het ontwarringsproces niet per ongeluk het einde van een andere bladwijzer heeft verwijderd:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Dit codefragment controleert of het einde van de bladwijzer met de naam 'ROW1' nog steeds bestaat nadat de rij met de bladwijzer 'ROW2' is verwijderd. Als deze nul is, wordt er een uitzondering gegenereerd, wat aangeeft dat er een probleem is met het ontwarringsproces. 

## Stap 5: Bewaar het document

 Tenslotte, na het ontwarren van de bladwijzers en mogelijk het verwijderen van rijen, slaat u het gewijzigde document op met behulp van de`Save` methode:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Hierdoor wordt het document met de ontwarde bladwijzers en eventuele verwijderde rijen opgeslagen onder een nieuwe bestandsnaam "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Conclusie

 Door deze stappen te volgen en gebruik te maken van de`Untangle`functie kunt u rijbladwijzers in uw Word-documenten effectief ontwarren met Aspose.Words voor .NET. Dit zorgt ervoor dat het verwijderen van rijen op basis van bladwijzers geen onbedoelde gevolgen heeft voor andere bladwijzers in aangrenzende rijen. Vergeet niet om tijdelijke aanduidingen zoals`"YOUR DOCUMENT DIRECTORY"` met uw daadwerkelijke paden en bestandsnamen.

## Veelgestelde vragen

### Is Aspose.Words voor .NET gratis?

 Aspose.Words voor .NET is een commerciële bibliotheek met een gratis proefversie. Je kunt het downloaden van[downloadlink](https://releases.aspose.com/words/net/).

### Kan ik rijbladwijzers handmatig ontwarren in Word?

Hoewel het technisch mogelijk is, kan het handmatig ontwarren van bladwijzers in Word vervelend en foutgevoelig zijn. Aspose.Words voor .NET automatiseert dit proces, waardoor u tijd en moeite bespaart.

###  Wat gebeurt er als de`Untangle` function encounters an error?

De code bevat een uitzonderingshandler die een uitzondering genereert als het ontwarringsproces per ongeluk het einde van een andere bladwijzer verwijdert. U kunt deze foutafhandeling aanpassen aan uw specifieke behoeften.

### Kan ik deze code gebruiken om bladwijzers in niet-aangrenzende rijen te ontwarren?

Momenteel richt de code zich op het ontwarren van bladwijzers die zich over aangrenzende rijen uitstrekken. Het aanpassen van de code om niet-aangrenzende rijen te verwerken zou extra logica vereisen om die scenario's te identificeren en af te handelen.

### Zijn er beperkingen aan het gebruik van deze aanpak?

Bij deze benadering wordt ervan uitgegaan dat bladwijzers goed gedefinieerd zijn binnen tabelcellen. Als bladwijzers buiten cellen of op onverwachte locaties worden geplaatst, werkt het ontwarringsproces mogelijk niet zoals bedoeld.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
