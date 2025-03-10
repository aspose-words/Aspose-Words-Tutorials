---
title: Vorm invoegen
linktitle: Vorm invoegen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u vormen in Word-documenten kunt invoegen en bewerken met Aspose.Words voor .NET met onze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vorm invoegen

## Invoering

Als het aankomt op het maken van visueel aantrekkelijke en goed gestructureerde Word-documenten, kunnen vormen een cruciale rol spelen. Of u nu pijlen, vakken of zelfs complexe aangepaste vormen toevoegt, de mogelijkheid om deze elementen programmatisch te manipuleren biedt ongeëvenaarde flexibiliteit. In deze tutorial onderzoeken we hoe u vormen in Word-documenten kunt invoegen en manipuleren met Aspose.Words voor .NET.

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

1.  Aspose.Words voor .NET: Download en installeer de nieuwste versie van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een geschikte .NET-ontwikkelomgeving, zoals Visual Studio.
3. Basiskennis van C#: Kennis van de programmeertaal C# en basisconcepten.

## Naamruimten importeren

Om te beginnen moet u de benodigde naamruimten importeren in uw C#-project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Stap 1: Stel uw project in

Voordat u vormen kunt invoegen, moet u uw project instellen en de Aspose.Words voor .NET-bibliotheek toevoegen.

1. Een nieuw project maken: open Visual Studio en maak een nieuw C# Console Application-project.
2. Voeg Aspose.Words voor .NET toe: installeer de Aspose.Words voor .NET-bibliotheek via NuGet Package Manager.

```bash
Install-Package Aspose.Words
```

## Stap 2: Initialiseer het document

Eerst moet u een nieuw document en een documentbuilder initialiseren, die u helpt bij het samenstellen van het document.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Een nieuw document initialiseren
Document doc = new Document();

// Initialiseer een DocumentBuilder om het document te helpen bouwen
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: Een vorm invoegen

Laten we nu een vorm in het document invoegen. We beginnen met het toevoegen van een eenvoudig tekstvak.

```csharp
// Een tekstvakvorm in het document invoegen
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Draai de vorm
shape.Rotation = 30.0;
```

In dit voorbeeld voegen we een tekstvak in op de positie (100, 100) met een breedte en hoogte van elk 50 eenheden. We roteren de vorm ook met 30 graden.

## Stap 4: Voeg een andere vorm toe

Laten we nog een vorm aan het document toevoegen, dit keer zonder de positie te specificeren.

```csharp
// Voeg een andere tekstvakvorm toe
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Draai de vorm
secondShape.Rotation = 30.0;
```

Met dit codefragment wordt een ander tekstvak ingevoegd met dezelfde afmetingen en rotatie als het eerste, maar zonder de positie ervan op te geven.

## Stap 5: Sla het document op

 Nadat u de vormen hebt toegevoegd, is de laatste stap het opslaan van het document. We gebruiken de`OoxmlSaveOptions` om het opslagformaat te specificeren.

```csharp
// Definieer opslagopties met naleving
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Sla het document op
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusie

En daar heb je het! Je hebt met succes vormen ingevoegd en gemanipuleerd in een Word-document met Aspose.Words voor .NET. Deze tutorial behandelde de basis, maar Aspose.Words biedt veel meer geavanceerde functies voor het werken met vormen, zoals aangepaste stijlen, connectoren en groepsvormen.

 Voor meer gedetailleerde informatie, bezoek de[Aspose.Words voor .NET-documentatie](https://reference.aspose.com/words/net/).

## Veelgestelde vragen

### Hoe voeg ik verschillende soorten vormen in?
Je kunt de`ShapeType` in de`InsertShape` Methode om verschillende soorten vormen in te voegen, zoals cirkels, rechthoeken en pijlen.

### Kan ik tekst toevoegen aan de vormen?
 Ja, u kunt de`builder.Write` Methode om tekst toe te voegen aan de vormen nadat u ze hebt ingevoegd.

### Is het mogelijk om de vormen te stylen?
 Ja, u kunt de vormen stylen door eigenschappen in te stellen zoals`FillColor`, `StrokeColor` , En`StrokeWeight`.

### Hoe positioneer ik vormen ten opzichte van andere elementen?
 Gebruik de`RelativeHorizontalPosition` En`RelativeVerticalPosition` Eigenschappen om vormen te positioneren ten opzichte van andere elementen in het document.

### Kan ik meerdere vormen groeperen?
 Ja, met Aspose.Words voor .NET kunt u vormen groeperen met behulp van de`GroupShape` klas.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
