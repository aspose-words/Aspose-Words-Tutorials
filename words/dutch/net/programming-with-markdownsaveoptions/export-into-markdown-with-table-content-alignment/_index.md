---
"description": "Leer hoe je Word-documenten met uitgelijnde tabellen naar Markdown exporteert met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding voor perfecte Markdown-tabellen."
"linktitle": "Exporteren naar Markdown met uitlijning van tabelinhoud"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Exporteren naar Markdown met uitlijning van tabelinhoud"
"url": "/nl/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exporteren naar Markdown met uitlijning van tabelinhoud

## Invoering

Hallo! Heb je je ooit afgevraagd hoe je je Word-document kunt exporteren naar Markdown-formaat met perfect uitgelijnde tabellen? Of je nu een ontwikkelaar bent die aan documentatie werkt of gewoon een Markdown-fan bent, deze gids is voor jou. We duiken in de fijne kneepjes van het gebruik van Aspose.Words voor .NET om dit te bereiken. Klaar om je Word-tabellen om te zetten in netjes uitgelijnde Markdown-tabellen? Laten we beginnen!

## Vereisten

Voordat we in de code duiken, zijn er een paar dingen die je moet regelen:

1. Aspose.Words voor .NET-bibliotheek: Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt. U kunt deze downloaden van de [Aspose Releases Pagina](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Stel uw ontwikkelomgeving in. Visual Studio is een populaire keuze voor .NET-ontwikkeling.
3. Basiskennis van C#: Kennis van C# is essentieel omdat we code in deze taal gaan schrijven.
4. Voorbeeld Word-document: Zorg dat u een Word-document heeft dat u kunt gebruiken voor tests.

## Naamruimten importeren

Voordat we beginnen met coderen, importeren we de benodigde naamruimten. Deze geven ons toegang tot de Aspose.Words-klassen en -methoden die we gaan gebruiken.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Initialiseer Document en DocumentBuilder

Het eerste wat we moeten doen, is een nieuw Word-document maken en een `DocumentBuilder` object om te beginnen met het samenstellen van ons document.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Maak een nieuw document.
Document doc = new Document();

// Initialiseer DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Cellen invoegen en inhoud uitlijnen

Vervolgens voegen we een aantal cellen in ons document in en stellen we de uitlijning ervan in. Dit is cruciaal om ervoor te zorgen dat de Markdown-export de juiste uitlijning behoudt.

```csharp
// Voeg een cel in en stel de uitlijning rechts in.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Voeg een andere cel in en stel de uitlijning in op het midden.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Stap 3: Stel de uitlijning van de tabelinhoud in voor Markdown-export

Nu is het tijd om de `MarkdownSaveOptions` om de uitlijning van de tabelinhoud in het geëxporteerde Markdown-bestand te regelen. We slaan het document op met verschillende uitlijningsinstellingen om te zien hoe het werkt.

```csharp
// Maak een MarkdownSaveOptions-object.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Document opslaan met linkse uitlijning.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Wijzig de uitlijning naar rechts en sla deze op.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Wijzig de uitlijning naar gecentreerd en sla deze op.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Stap 4: Automatische uitlijning van tabelinhoud gebruiken

De `Auto` De uitlijningsoptie neemt de uitlijning over van de eerste alinea in de corresponderende tabelkolom. Dit kan handig zijn wanneer u gemengde uitlijningen in één tabel hebt.

```csharp
// Stel de uitlijning in op Automatisch.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Document opslaan met automatische uitlijning.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Conclusie

En voilà! Het exporteren van Word-documenten naar Markdown met uitgelijnde tabellen met Aspose.Words voor .NET is een fluitje van een cent als je eenmaal weet hoe het moet. Deze krachtige bibliotheek maakt het eenvoudig om de opmaak en uitlijning van je tabellen te beheren, zodat je Markdown-documenten er precies zo uitzien als je wilt. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, wijzigen, converteren en exporteren.

### Kan ik verschillende uitlijningen instellen voor verschillende kolommen in dezelfde tabel?
Ja, door gebruik te maken van de `Auto` Met de uitlijningsoptie kunt u verschillende uitlijningen gebruiken op basis van de eerste alinea in elke kolom.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?
Ja, Aspose.Words voor .NET vereist een licentie voor volledige functionaliteit. U kunt een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor evaluatie.

### Is het mogelijk om andere documentelementen te exporteren naar Markdown met behulp van Aspose.Words?
Ja, Aspose.Words ondersteunt het exporteren van verschillende elementen, zoals koppen, lijsten en afbeeldingen, naar Markdown-formaat.

### Waar kan ik ondersteuning krijgen als ik problemen ondervind?
U kunt ondersteuning krijgen van de [Aspose.Words Ondersteuningsforum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}