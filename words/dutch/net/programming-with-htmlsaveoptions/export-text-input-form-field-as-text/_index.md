---
"description": "Leer hoe u tekstinvoervelden als platte tekst kunt exporteren met Aspose.Words voor .NET met deze uitgebreide, stapsgewijze handleiding."
"linktitle": "Tekstinvoerformulierveld exporteren als tekst"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Tekstinvoerformulierveld exporteren als tekst"
"url": "/nl/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tekstinvoerformulierveld exporteren als tekst

## Invoering

Dus, je duikt in de wereld van Aspose.Words voor .NET? Een geweldige keuze! Als je wilt leren hoe je een tekstinvoerveld exporteert als tekst, ben je hier aan het juiste adres. Of je nu net begint of je vaardigheden wilt opfrissen, deze gids leidt je door alles wat je moet weten. Laten we beginnen, oké?

## Vereisten

Voordat we in de details duiken, willen we ervoor zorgen dat je alles hebt wat je nodig hebt om alles soepel te kunnen volgen:

- Aspose.Words voor .NET: Download en installeer de nieuwste versie van [hier](https://releases.aspose.com/words/net/).
- IDE: Visual Studio of een andere C#-ontwikkelomgeving.
- Basiskennis van C#: inzicht in de basissyntaxis van C# en conceptuele objectgeoriënteerd programmeren.
- Document: Een voorbeeld van een Word-document (`Rendering.docx`) met tekstinvoerformuliervelden.

## Naamruimten importeren

Allereerst moet je de benodigde naamruimten importeren. Deze zijn als het ware de bouwstenen die ervoor zorgen dat alles naadloos werkt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Oké, nu onze naamruimten klaar zijn, kunnen we aan de slag!

## Stap 1: Het project instellen

Voordat we met de code aan de slag gaan, controleren we of ons project correct is ingesteld.

## Het project creëren

1. Open Visual Studio: begin met het openen van Visual Studio of uw favoriete C#-ontwikkelomgeving.
2. Een nieuw project maken: Navigeer naar `File > New > Project`Selecteer `Console App (.NET Core)` of enig ander relevant projecttype.
3. Geef uw project een naam: Geef uw project een betekenisvolle naam, bijvoorbeeld: `AsposeWordsExportExample`.

## Aspose.Words toevoegen

1. NuGet-pakketten beheren: Klik met de rechtermuisknop op uw project in de Solution Explorer en selecteer `Manage NuGet Packages`.
2. Zoek naar Aspose.Words: Zoek in de NuGet Package Manager naar `Aspose.Words`.
3. Aspose.Words installeren: Klik op `Install` om de Aspose.Words-bibliotheek aan uw project toe te voegen.

## Stap 2: Laad het Word-document

Nu het project is ingesteld, kunnen we het Word-document laden dat de tekstvelden bevat.

1. Geef de documentmap op: definieer het pad naar de map waarin uw document is opgeslagen.
2. Laad het document: Gebruik de `Document` klasse om uw Word-document te laden.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 3: De exportmap voorbereiden

Voordat we exporteren, zorgen we ervoor dat onze exportmap klaar is. Dit is waar ons HTML-bestand en de afbeeldingen worden opgeslagen.

1. Definieer de exportmap: geef het pad op waar de geëxporteerde bestanden worden opgeslagen.
2. Controleer en maak de map schoon: zorg ervoor dat de map bestaat en leeg is.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Stap 4: Opties voor opslaan configureren

Hier gebeurt de magie. We moeten onze opslagopties zo instellen dat het tekstinvoerveld als platte tekst wordt geëxporteerd.

1. Opties voor opslaan maken: een nieuwe initialiseren `HtmlSaveOptions` voorwerp.
2. Optie Exporttekst instellen: Configureer de `ExportTextInputFormFieldAsText` eigendom van `true`.
3. Map met afbeeldingen instellen: Definieer de map waarin de afbeeldingen worden opgeslagen.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Stap 5: Sla het document op als HTML

Ten slotte slaan we het Word-document op als een HTML-bestand met behulp van onze geconfigureerde opslagopties.

1. Definieer het uitvoerpad: geef het pad op waar het HTML-bestand wordt opgeslagen.
2. Document opslaan: Gebruik de `Save` methode van de `Document` klasse om het document te exporteren.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusie

En voilà! Je hebt met succes een tekstinvoerveld geëxporteerd als platte tekst met Aspose.Words voor .NET. Deze handleiding zou je een duidelijke, stapsgewijze aanpak moeten hebben gegeven om deze taak uit te voeren. Onthoud: oefening baart kunst, dus blijf experimenteren met verschillende opties en instellingen om te zien wat je nog meer met Aspose.Words kunt doen.

## Veelgestelde vragen

### Kan ik andere typen formuliervelden op dezelfde manier exporteren?

Ja, u kunt andere typen formuliervelden exporteren door verschillende eigenschappen van de `HtmlSaveOptions` klas.

### Wat als mijn document afbeeldingen bevat?

De afbeeldingen worden opgeslagen in de opgegeven afbeeldingenmap. Zorg ervoor dat u de `ImagesFolder` eigendom in de `HtmlSaveOptions`.

### Heb ik een licentie nodig voor Aspose.Words?

Ja, u kunt een gratis proefperiode krijgen [hier](https://releases.aspose.com/) of koop een licentie [hier](https://purchase.aspose.com/buy).

### Kan ik de geëxporteerde HTML aanpassen?

Absoluut! Aspose.Words biedt verschillende opties om de HTML-uitvoer aan te passen. Raadpleeg de [documentatie](https://reference.aspose.com/words/net/) voor meer details.

### Is Aspose.Words compatibel met .NET Core?

Ja, Aspose.Words is compatibel met .NET Core, .NET Framework en andere .NET-platformen.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}