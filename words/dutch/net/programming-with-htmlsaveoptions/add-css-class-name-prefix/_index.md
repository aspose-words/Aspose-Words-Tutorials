---
"description": "Leer hoe je een CSS-klassenaam-prefix toevoegt bij het opslaan van Word-documenten als HTML met Aspose.Words voor .NET. Inclusief stapsgewijze handleiding, codefragmenten en veelgestelde vragen."
"linktitle": "Voeg een CSS-klassenaamprefix toe"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Voeg een CSS-klassenaamprefix toe"
"url": "/nl/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een CSS-klassenaamprefix toe

## Invoering

Welkom! Duik je in de wereld van Aspose.Words voor .NET? Dan staat je iets bijzonders te wachten. Vandaag bekijken we hoe je een CSS-klassenaam-prefix kunt toevoegen wanneer je een Word-document als HTML opslaat met Aspose.Words voor .NET. Deze functie is superhandig als je conflicten tussen klassennamen in je HTML-bestanden wilt voorkomen.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

- Aspose.Words voor .NET: Als u het nog niet hebt geïnstalleerd, [download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Visual Studio of een andere C# IDE.
- Een Word-document: we gebruiken een document met de naam `Rendering.docx`Plaats het in uw projectmap.

## Naamruimten importeren

Zorg er eerst voor dat je de benodigde naamruimten in je C#-project hebt geïmporteerd. Voeg deze bovenaan je codebestand toe:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we nu eens naar de stapsgewijze handleiding gaan!

## Stap 1: Stel uw project in

Voordat we een CSS-klassenaamvoorvoegsel kunnen toevoegen, moeten we eerst ons project instellen.

### Stap 1.1: Een nieuw project maken

Start Visual Studio op en maak een nieuw Console App-project. Geef het een pakkende naam, zoals `AsposeCssPrefixExample`.

### Stap 1.2: Aspose.Words toevoegen voor .NET

Voeg Aspose.Words voor .NET toe aan je project via NuGet, als je dat nog niet hebt gedaan. Open de NuGet Package Manager Console en voer het volgende uit:

```bash
Install-Package Aspose.Words
```

Geweldig! Nu kunnen we beginnen met coderen.

## Stap 2: Laad uw document

Het eerste dat we moeten doen, is het Word-document laden dat we naar HTML willen converteren.

### Stap 2.1: Het documentpad definiëren

Stel het pad naar uw documentmap in. Voor deze tutorial gaan we ervan uit dat uw document zich in een map met de naam bevindt. `Documents` in uw projectmap.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Stap 2.2: Het document laden

Laten we nu het document laden met behulp van Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 3: Configureer HTML-opslagopties

Vervolgens moeten we de HTML-opslagopties configureren om een CSS-klassenaamprefix op te nemen.

### Stap 3.1: HTML-opslagopties maken

Instantieer de `HtmlSaveOptions` object en stel het CSS-stijlbladtype in op `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Stap 3.2: Stel het CSS-klassennaamvoorvoegsel in

Laten we nu de `CssClassNamePrefix` eigenschap aan het gewenste voorvoegsel. Voor dit voorbeeld gebruiken we `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Stap 4: Sla het document op als HTML

Ten slotte slaan we het document op als een HTML-bestand met onze geconfigureerde opties.


Geef het pad naar het HTML-uitvoerbestand op en sla het document op.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Stap 5: Controleer de uitvoer

Nadat u uw project hebt uitgevoerd, navigeert u naar uw `Documents` map. Je zou een HTML-bestand moeten vinden met de naam `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`Open dit bestand in een teksteditor of browser om te controleren of de CSS-klassen het voorvoegsel hebben `pfx_`.

## Conclusie

En voilà! Door deze stappen te volgen, heb je met succes een CSS-klassenaam-prefix toegevoegd aan je HTML-uitvoer met Aspose.Words voor .NET. Deze eenvoudige maar krachtige functie helpt je om schone en conflictvrije stijlen in je HTML-documenten te behouden.

## Veelgestelde vragen

### Kan ik voor elke opslagbewerking een ander voorvoegsel gebruiken?
Ja, u kunt het voorvoegsel elke keer dat u een document opslaat aanpassen door de `CssClassNamePrefix` eigendom.

### Ondersteunt deze methode inline CSS?
De `CssClassNamePrefix` De eigenschap werkt met externe CSS. Voor inline CSS heb je een andere aanpak nodig.

### Hoe kan ik andere HTML-opslagopties toevoegen?
U kunt verschillende eigenschappen van `HtmlSaveOptions` om uw HTML-uitvoer aan te passen. Controleer de [documentatie](https://reference.aspose.com/words/net/) voor meer details.

### Is het mogelijk om de HTML in een stream op te slaan?
Absoluut! Je kunt het document opslaan in een stream door het streamobject door te geven aan de `Save` methode.

### Hoe krijg ik ondersteuning als ik problemen ondervind?
U kunt ondersteuning krijgen van de [Aspose-forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}