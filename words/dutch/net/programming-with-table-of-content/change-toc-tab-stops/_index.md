---
title: Wijzig Toc Tab Stops in Word Document
linktitle: Wijzig Toc Tab Stops in Word Document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u TOC-tabstops in Word-documenten kunt wijzigen met Aspose.Words voor .NET. Deze stapsgewijze handleiding helpt u een professioneel ogende inhoudsopgave te maken.
weight: 10
url: /nl/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wijzig Toc Tab Stops in Word Document

## Invoering

Heb je je ooit afgevraagd hoe je de inhoudsopgave (TOC) in je Word-documenten kunt opfleuren? Misschien wil je dat die tabstops perfect uitgelijnd zijn voor een professionele touch. Je bent op de juiste plek! Vandaag duiken we diep in hoe je TOC-tabstops kunt wijzigen met Aspose.Words voor .NET. Blijf hangen en ik beloof je dat je met alle knowhow naar huis gaat om je TOC er flitsend en netjes uit te laten zien.

## Vereisten

Voordat we beginnen, willen we ervoor zorgen dat u alles heeft wat u nodig hebt:

1.  Aspose.Words voor .NET: Je kunt[download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere C#-compatibele IDE.
3. Een Word-document: specifiek een document dat een inhoudsopgave bevat.

Heb je dat allemaal? Geweldig! Laten we gaan.

## Naamruimten importeren

Allereerst moet u de benodigde namespaces importeren. Dit is vergelijkbaar met het inpakken van uw tools voordat u een project start.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Laten we dit proces opsplitsen in eenvoudige, verteerbare stappen. We gaan door het laden van het document, het aanpassen van de TOC-tabstops en het opslaan van het bijgewerkte document.

## Stap 1: Laad het document

Waarom? We moeten toegang hebben tot het Word-document dat de inhoudsopgave bevat die we willen wijzigen.

Hoe? Hier is een eenvoudig stukje code om je op weg te helpen:

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Laad het document met de inhoudsopgave
Document doc = new Document(dataDir + "Table of contents.docx");
```

Stel je voor dat je document een taart is, en dat we er wat glazuur op gaan doen. De eerste stap is om die taart uit de doos te halen.

## Stap 2: Identificeer TOC-paragrafen

Waarom? We moeten de paragrafen die de inhoudsopgave vormen, nauwkeurig bepalen. 

Hoe? Loop door de paragrafen en controleer hun stijlen:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // TOC-paragraaf gevonden
    }
}
```

Zie het als het scannen van een menigte om je vrienden te vinden. Hier zoeken we naar paragrafen die zijn opgemaakt als TOC-items.

## Stap 3: Wijzig de tabstops

Waarom? Dit is waar de magie gebeurt. Het veranderen van tabstops geeft uw TOC een schonere look.

Hoe? Verwijder de bestaande tabstop en voeg een nieuwe toe op een gewijzigde positie:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Het is alsof je de meubels in je woonkamer aanpast tot ze precies goed voelen. We tweaken die tabstops tot ze perfect zijn.

## Stap 4: Sla het gewijzigde document op

Waarom? Om ervoor te zorgen dat al uw harde werk wordt opgeslagen en kan worden bekeken of gedeeld.

Hoe? Sla het document op met een nieuwe naam om het origineel intact te houden:

```csharp
// Sla het gewijzigde document op
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

En voilà! Je inhoudsopgave heeft nu de tabstops precies waar je ze wilt hebben.

## Conclusie

Het wijzigen van TOC-tabstops in een Word-document met Aspose.Words voor .NET is eenvoudig zodra u het opsplitst. Door uw document te laden, de TOC-paragrafen te identificeren, de tabstops aan te passen en het document op te slaan, kunt u een gepolijste en professionele look bereiken. Vergeet niet, oefening baart kunst, dus blijf experimenteren met verschillende tabstopposities om de exacte lay-out te krijgen die u wenst.

## Veelgestelde vragen

### Kan ik tabstops voor verschillende inhoudsopgaveniveaus afzonderlijk aanpassen?
Ja, dat kan! Controleer gewoon voor elk specifiek TOC-niveau (Toc1, Toc2, etc.) en pas het dienovereenkomstig aan.

### Wat als mijn document meerdere inhoudsopgaven heeft?
De code scant alle paragrafen in inhoudsopgavestijl en wijzigt dus alle inhoudsopgaven in het document.

### Is het mogelijk om meerdere tabstops toe te voegen aan een TOC-item?
 Absoluut! U kunt zoveel tabstops toevoegen als nodig is door de`para.ParagraphFormat.TabStops` verzameling.

### Kan ik de uitlijning van de tabstop en de stijl van de opvulstreep wijzigen?
Ja, u kunt verschillende uitlijningen en opvulstijlen opgeven wanneer u een nieuwe tabstop toevoegt.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?
 Ja, u hebt een geldige licentie nodig om Aspose.Words voor .NET te gebruiken na de proefperiode. U kunt een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) of[koop er een](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
