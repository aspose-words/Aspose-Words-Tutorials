---
title: Inhoudsbesturingselementen wijzigen
linktitle: Inhoudsbesturingselementen wijzigen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u gestructureerde documenttags in Word kunt wijzigen met Aspose.Words voor .NET. Werk tekst, vervolgkeuzelijsten en afbeeldingen stapsgewijs bij.
weight: 10
url: /nl/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhoudsbesturingselementen wijzigen

## Invoering

Als u ooit met Word-documenten hebt gewerkt en gestructureerde inhoudsbesturingselementen moest wijzigen, zoals platte tekst, vervolgkeuzelijsten of afbeeldingen, met Aspose.Words voor .NET, dan bent u hier aan het juiste adres! Structured Document Tags (SDT's) zijn krachtige tools die documentautomatisering eenvoudiger en flexibeler maken. In deze tutorial duiken we in hoe u deze SDT's kunt aanpassen aan uw behoeften. Of u nu tekst bijwerkt, vervolgkeuzelijsten wijzigt of afbeeldingen verwisselt, deze gids leidt u stap voor stap door het proces.

## Vereisten

Voordat we dieper ingaan op het aanpassen van inhoudsinstellingen, moet u ervoor zorgen dat u over het volgende beschikt:

1.  Aspose.Words voor .NET geïnstalleerd: Zorg ervoor dat u de Aspose.Words-bibliotheek hebt geïnstalleerd. Als dat niet het geval is, kunt u[download het hier](https://releases.aspose.com/words/net/).

2. Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u bekend bent met de basisconcepten van C#-programmeren.

3. Een .NET-ontwikkelomgeving: u moet een IDE zoals Visual Studio hebben ingesteld voor het uitvoeren van .NET-toepassingen.

4. Een voorbeelddocument: We gebruiken een voorbeeld Word-document met verschillende typen SDT's. U kunt degene uit het voorbeeld gebruiken of uw eigen maken.

5.  Toegang tot Aspose-documentatie: voor meer gedetailleerde informatie, bekijk de[Aspose.Words-documentatie](https://reference.aspose.com/words/net/).

## Naamruimten importeren

Om te beginnen met Aspose.Words moet u de relevante namespaces importeren in uw C#-project. Dit is hoe u dat doet:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Met deze naamruimten krijgt u toegang tot de klassen en methoden die nodig zijn voor het bewerken van gestructureerde documenttags in uw Word-documenten.

## Stap 1: Stel uw documentpad in

 Voordat u wijzigingen aanbrengt, moet u het pad naar uw document opgeven. Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad waar uw document is opgeslagen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Stap 2: Loop door gestructureerde documenttags

 Om SDT's te wijzigen, moet u eerst door alle SDT's in het document heen lopen. Dit doet u met behulp van de`GetChildNodes` methode om alle knooppunten van het type te verkrijgen`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Wijzig SDT's op basis van hun type
}
```

## Stap 3: Wijzig platte tekst SDT's

Als de SDT een platte tekst is, kunt u de inhoud ervan vervangen. Wis eerst de bestaande inhoud en voeg vervolgens nieuwe tekst toe.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Uitleg: Hier,`RemoveAllChildren()`wist de bestaande inhoud van de SDT. Vervolgens maken we een nieuwe`Paragraph` En`Run` object om de nieuwe tekst in te voegen.

## Stap 4: Wijzig de dropdownlijst-SDT's

 Voor SDT's met een vervolgkeuzelijst kunt u het geselecteerde item wijzigen door naar de`ListItems` collectie. Hier selecteren we het derde item in de lijst.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Uitleg: Dit codefragment selecteert het item op index 2 (derde item) uit de dropdownlijst. Pas de index aan op basis van uw behoeften.

## Stap 5: Wijzig de afbeelding-SDT's

Om een afbeelding binnen een foto-SDT bij te werken, kunt u de bestaande afbeelding vervangen door een nieuwe.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Uitleg: Deze code controleert of de vorm een afbeelding bevat en vervangt deze vervolgens door een nieuwe afbeelding die zich op de volgende locatie bevindt:`ImagesDir`.

## Stap 6: Sla uw gewijzigde document op

Nadat u alle benodigde wijzigingen hebt aangebracht, slaat u het gewijzigde document op onder een nieuwe naam. Zo blijft het originele document intact.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Uitleg: Hiermee slaat u het document op met een nieuwe bestandsnaam, zodat u het gemakkelijk kunt onderscheiden van het origineel.

## Conclusie

Het wijzigen van inhoudsbesturingselementen in een Word-document met Aspose.Words voor .NET is eenvoudig zodra u de betrokken stappen begrijpt. Of u nu tekst bijwerkt, dropdown-selecties wijzigt of afbeeldingen verwisselt, Aspose.Words biedt een robuuste API voor deze taken. Door deze tutorial te volgen, kunt u de gestructureerde inhoudsbesturingselementen van uw document effectief beheren en aanpassen, waardoor uw documenten dynamischer worden en beter aansluiten op uw behoeften.

## Veelgestelde vragen

1. Wat is een Structured Document Tag (SDT)?

SDT's zijn elementen in Word-documenten waarmee u de inhoud van documenten kunt beheren en opmaken, zoals tekstvakken, vervolgkeuzelijsten en afbeeldingen.

2. Hoe kan ik een nieuw dropdown-item toevoegen aan een SDT?

 Om een nieuw item toe te voegen, gebruikt u de`ListItems` eigenschap en voeg een nieuwe toe`SdtListItem` naar de collectie.

3. Kan ik Aspose.Words gebruiken om SDT's uit een document te verwijderen?

Ja, u kunt SDT's verwijderen door naar de knooppunten van het document te gaan en de gewenste SDT te verwijderen.

4. Hoe ga ik om met SDT's die genest zijn in andere elementen?

 Gebruik de`GetChildNodes` methode met geschikte parameters om toegang te krijgen tot geneste SDT's.

5. Wat moet ik doen als de SDT die ik wil wijzigen niet zichtbaar is in het document?

Zorg ervoor dat de SDT niet verborgen of beschermd is. Controleer de documentinstellingen en zorg ervoor dat uw code correct is gericht op het SDT-type.


### Voorbeeldbroncode voor het wijzigen van inhoudsbesturingselementen met behulp van Aspose.Words voor .NET 

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Dat is alles! U hebt met succes verschillende typen inhoudsbesturingselementen in uw Word-document gewijzigd met Aspose.Words voor .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
