---
title: Exporteer tekstinvoerformulierveld als tekst
linktitle: Exporteer tekstinvoerformulierveld als tekst
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u tekstinvoervelden als platte tekst kunt exporteren met Aspose.Words voor .NET met deze uitgebreide, stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exporteer tekstinvoerformulierveld als tekst

## Invoering

Dus, je duikt in de wereld van Aspose.Words voor .NET? Geweldige keuze! Als je wilt leren hoe je een tekstinvoerformulierveld exporteert als tekst, dan ben je hier aan het juiste adres. Of je nu net begint of je vaardigheden aan het opfrissen bent, deze gids leidt je door alles wat je moet weten. Laten we beginnen, zullen we?

## Vereisten

Voordat we in de details duiken, willen we ervoor zorgen dat je alles bij de hand hebt om het proces soepel te kunnen volgen:

-  Aspose.Words voor .NET: Download en installeer de nieuwste versie van[hier](https://releases.aspose.com/words/net/).
- IDE: Visual Studio of een andere C#-ontwikkelomgeving.
- Basiskennis van C#: inzicht in de basissyntaxis van C# en concepten van objectgeoriënteerd programmeren.
- Document: Een voorbeeld van een Word-document (`Rendering.docx`) met tekstinvoerformuliervelden.

## Naamruimten importeren

Allereerst moet u de benodigde namespaces importeren. Dit zijn de bouwstenen die ervoor zorgen dat alles naadloos werkt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Oké, nu onze naamruimten klaar zijn, kunnen we aan de slag!

## Stap 1: Het project instellen

Voordat we met de code beginnen, controleren we eerst of ons project correct is ingesteld.

## Het project creëren

1. Open Visual Studio: begin met het openen van Visual Studio of uw favoriete C#-ontwikkelomgeving.
2.  Maak een nieuw project: Navigeer naar`File > New > Project` . Selecteer`Console App (.NET Core)` of enig ander relevant projecttype.
3.  Geef uw project een naam: Geef uw project een betekenisvolle naam, bijvoorbeeld`AsposeWordsExportExample`.

## Aspose.Words toevoegen

1.  NuGet-pakketten beheren: Klik met de rechtermuisknop op uw project in de Solution Explorer en selecteer`Manage NuGet Packages`.
2.  Zoek naar Aspose.Words: Zoek in de NuGet Package Manager naar`Aspose.Words`.
3.  Aspose.Words installeren: Klik op`Install` om de Aspose.Words-bibliotheek aan uw project toe te voegen.

## Stap 2: Laad het Word-document

Nu ons project is opgezet, laden we het Word-document met de tekstvelden.

1. Geef de documentmap op: definieer het pad naar de map waarin uw document is opgeslagen.
2.  Laad het document: Gebruik de`Document` klasse om uw Word-document te laden.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 3: De exportdirectory voorbereiden

Voordat we exporteren, zorgen we ervoor dat onze exportdirectory gereed is. Dit is waar ons HTML-bestand en afbeeldingen worden opgeslagen.

1. Definieer de exportmap: geef het pad op waar de geëxporteerde bestanden worden opgeslagen.
2. Controleer en maak de map schoon: zorg ervoor dat de map bestaat en leeg is.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Stap 4: Configureer opslagopties

Hier gebeurt de magie. We moeten onze opslagopties instellen om het tekstinvoerformulierveld te exporteren als platte tekst.

1.  Opties voor opslaan maken: een nieuwe initialiseren`HtmlSaveOptions` voorwerp.
2.  Optie Exporttekst instellen: Configureer de`ExportTextInputFormFieldAsText`eigendom van`true`.
3. Map met afbeeldingen instellen: Definieer de map waarin de afbeeldingen worden opgeslagen.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Stap 5: Sla het document op als HTML

Laten we ten slotte het Word-document opslaan als een HTML-bestand met behulp van onze geconfigureerde opslagopties.

1. Definieer het uitvoerpad: geef het pad op waar het HTML-bestand wordt opgeslagen.
2.  Document opslaan: Gebruik de`Save` methode van de`Document`klasse om het document te exporteren.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusie

En daar heb je het! Je hebt met succes een tekstinvoerformulierveld geëxporteerd als platte tekst met Aspose.Words voor .NET. Deze handleiding zou je een duidelijke, stapsgewijze aanpak moeten hebben gegeven om deze taak te volbrengen. Vergeet niet, oefening baart kunst, dus blijf experimenteren met verschillende opties en instellingen om te zien wat je nog meer kunt doen met Aspose.Words.

## Veelgestelde vragen

### Kan ik andere typen formuliervelden op dezelfde manier exporteren?

 Ja, u kunt andere typen formuliervelden exporteren door verschillende eigenschappen van de`HtmlSaveOptions` klas.

### Wat als mijn document afbeeldingen bevat?

 De afbeeldingen worden opgeslagen in de opgegeven afbeeldingenmap. Zorg ervoor dat u de`ImagesFolder` eigendom in de`HtmlSaveOptions`.

### Heb ik een licentie nodig voor Aspose.Words?

 Ja, u kunt een gratis proefperiode krijgen[hier](https://releases.aspose.com/) of koop een licentie[hier](https://purchase.aspose.com/buy).

### Kan ik de geëxporteerde HTML aanpassen?

 Absoluut! Aspose.Words biedt verschillende opties om de HTML-uitvoer aan te passen. Raadpleeg de[documentatie](https://reference.aspose.com/words/net/) voor meer informatie.

### Is Aspose.Words compatibel met .NET Core?

Ja, Aspose.Words is compatibel met .NET Core, .NET Framework en andere .NET-platformen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
