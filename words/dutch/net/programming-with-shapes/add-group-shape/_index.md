---
title: Groepsvorm toevoegen
linktitle: Groepsvorm toevoegen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u groepsvormen toevoegt aan Word-documenten met Aspose.Words voor .NET met deze uitgebreide, stapsgewijze zelfstudie.
weight: 10
url: /nl/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepsvorm toevoegen

## Invoering

Het maken van complexe documenten met rijke visuele elementen kan soms een ontmoedigende taak zijn, vooral als het gaat om groepsvormen. Maar vrees niet! Aspose.Words voor .NET vereenvoudigt dit proces en maakt het zo makkelijk als een fluitje van een cent. In deze tutorial leiden we je door de stappen om groepsvormen toe te voegen aan je Word-documenten. Klaar om erin te duiken? Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1.  Aspose.Words voor .NET: U kunt het downloaden van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere IDE die compatibel is met .NET.
3. Basiskennis van C#: Kennis van C#-programmering is een pluspunt.

## Naamruimten importeren

Om te beginnen moeten we de benodigde namespaces importeren in ons project. Deze namespaces bieden toegang tot de klassen en methoden die nodig zijn voor het manipuleren van Word-documenten met Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Stap 1: Initialiseer het document

Laten we eerst een nieuw Word-document initialiseren. Zie dit als het maken van een leeg canvas waar we onze groepsvormen aan toevoegen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Hier,`EnsureMinimum()` voegt een minimale set knooppunten toe die nodig zijn voor het document.

## Stap 2: Het GroupShape-object maken

 Vervolgens moeten we een`GroupShape`object. Dit object zal dienen als een container voor andere vormen, waardoor we ze kunnen groeperen.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Stap 3: Vormen toevoegen aan de GroupShape

 Laten we nu individuele vormen toevoegen aan onze`GroupShape` container. We beginnen met een accentrandvorm en voegen vervolgens een actieknopvorm toe.

### Een accentrandvorm toevoegen

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Met dit codefragment wordt een accentrandvorm gemaakt met een breedte en hoogte van 100 eenheden en wordt deze toegevoegd aan de`GroupShape`.

### Een actieknopvorm toevoegen

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Hier maken we een actieknopvorm, positioneren deze en voegen deze toe aan onze`GroupShape`.

## Stap 4: Definieer de GroupShape-dimensies

 Om ervoor te zorgen dat onze vormen goed binnen de groep passen, moeten we de afmetingen van de`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Dit definieert de breedte en hoogte van de`GroupShape` als 200 eenheden en stelt de coördinaatgrootte dienovereenkomstig in.

## Stap 5: De GroupShape in het document invoegen

 Laten we nu onze`GroupShape` in het document met behulp van`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` biedt een eenvoudige manier om knooppunten, waaronder vormen, aan het document toe te voegen.

## Stap 6: Sla het document op

Sla het document ten slotte op in de door u opgegeven map.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

En daar heb je het! Je document met groepsvormen is klaar.

## Conclusie

Het toevoegen van groepsvormen aan uw Word-documenten hoeft geen ingewikkeld proces te zijn. Met Aspose.Words voor .NET kunt u eenvoudig vormen maken en bewerken, waardoor uw documenten visueel aantrekkelijker en functioneler worden. Volg de stappen in deze tutorial en u bent binnen no time een pro!

## Veelgestelde vragen

### Kan ik meer dan twee vormen aan een GroupShape toevoegen?
 Ja, u kunt zoveel vormen toevoegen als u nodig hebt aan een`GroupShape` . Gebruik gewoon de`AppendChild` methode voor elke vorm.

### Is het mogelijk om de vormen binnen een GroupShape te stylen?
 Absoluut! Elke vorm kan individueel worden gestyled met behulp van de eigenschappen die beschikbaar zijn in de`Shape` klas.

### Hoe positioneer ik de GroupShape in het document?
 U kunt de`GroupShape` door het instellen van zijn`Left` En`Top` eigenschappen.

### Kan ik tekst toevoegen aan de vormen in de GroupShape?
 Ja, u kunt tekst aan vormen toevoegen met behulp van de`AppendChild` methode om een toe te voegen`Paragraph` bevattend`Run` knooppunten met tekst.

### Is het mogelijk om vormen dynamisch te groeperen op basis van gebruikersinvoer?
Ja, u kunt dynamisch vormen maken en groeperen op basis van gebruikersinvoer door de eigenschappen en methoden dienovereenkomstig aan te passen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
