---
title: Verticale anker
linktitle: Verticale anker
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u verticale ankerposities voor tekstvakken in Word-documenten instelt met Aspose.Words voor .NET. Inclusief eenvoudige stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verticale anker

## Invoering

Heb je ooit gemerkt dat je precies moest bepalen waar tekst in een tekstvak in een Word-document zou verschijnen? Misschien wil je dat je tekst aan de bovenkant, het midden of de onderkant van het tekstvak wordt verankerd? Dan ben je hier aan het juiste adres! In deze tutorial gaan we onderzoeken hoe je Aspose.Words voor .NET kunt gebruiken om het verticale anker van tekstvakken in Word-documenten in te stellen. Zie verticale verankering als de toverstaf die je tekst precies op de gewenste plek in de container plaatst. Klaar om erin te duiken? Laten we beginnen!

## Vereisten

Voordat we dieper ingaan op verticale verankering, moet u een aantal zaken regelen:

1.  Aspose.Words voor .NET: Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt geïnstalleerd. Als u deze nog niet hebt, kunt u[download het hier](https://releases.aspose.com/words/net/).
2. Visual Studio: in deze zelfstudie gaan we ervan uit dat u Visual Studio of een andere .NET IDE gebruikt voor het coderen.
3. Basiskennis van C#: Kennis van C# en .NET helpt u de cursus soepel te volgen.

## Naamruimten importeren

Om te beginnen moet u de benodigde namespaces importeren in uw C#-code. Dit is waar u uw applicatie vertelt waar de klassen en methoden die u gaat gebruiken te vinden zijn. Dit is hoe u dat doet:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Deze naamruimten bieden de klassen die u nodig hebt om met documenten en vormen te werken.

## Stap 1: Initialiseer het document

Allereerst moet u een nieuw Word-document maken. Zie dit als het opzetten van uw canvas voordat u begint met schilderen.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier,`Document` is jouw lege canvas, en`DocumentBuilder` is uw penseel waarmee u vormen en tekst kunt toevoegen.

## Stap 2: Een tekstvakvorm invoegen

Laten we nu een tekstvak aan ons document toevoegen. Dit is waar uw tekst zal leven. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 In dit voorbeeld,`ShapeType.TextBox` specificeert de vorm die u wenst, en`200, 200` zijn de breedte en hoogte van het tekstvak in punten.

## Stap 3: Plaats het verticale anker

Hier gebeurt de magie! U kunt de verticale uitlijning van de tekst in het tekstvak instellen. Dit bepaalt of de tekst aan de boven-, midden- of onderkant van het tekstvak wordt verankerd.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 In dit geval,`TextBoxAnchor.Bottom`zorgt ervoor dat de tekst aan de onderkant van het tekstvak wordt verankerd. Als u het gecentreerd of uitgelijnd aan de bovenkant wilt, gebruikt u`TextBoxAnchor.Center` of`TextBoxAnchor.Top`, respectievelijk.

## Stap 4: Voeg tekst toe aan het tekstvak

Nu is het tijd om wat content toe te voegen aan je tekstvak. Zie het als het vullen van je canvas met de laatste hand.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Hier,`MoveTo` zorgt ervoor dat de tekst in het tekstvak wordt ingevoegd en`Write` voegt de eigenlijke tekst toe.

## Stap 5: Sla het document op

De laatste stap is om uw document op te slaan. Dit is alsof u uw voltooide schilderij in een lijst stopt.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Conclusie

En daar heb je het! Je hebt zojuist geleerd hoe je de verticale uitlijning van tekst in een tekstvak in een Word-document kunt regelen met Aspose.Words voor .NET. Of je nu tekst aan de bovenkant, het midden of de onderkant wilt verankeren, deze functie geeft je nauwkeurige controle over de lay-out van je document. Dus de volgende keer dat je de tekstplaatsing van je document moet aanpassen, weet je precies wat je moet doen!

## Veelgestelde vragen

### Wat is verticale verankering in een Word-document?
Met verticale verankering bepaalt u waar de tekst in een tekstvak wordt geplaatst, bijvoorbeeld boven, in het midden of onder.

### Kan ik naast tekstvakken ook andere vormen gebruiken?
Ja, u kunt verticale verankering gebruiken met andere vormen, maar tekstvakken worden het meest gebruikt.

### Hoe verander ik het ankerpunt nadat ik het tekstvak heb gemaakt?
 U kunt het ankerpunt wijzigen door de`VerticalAnchor` eigenschap op het tekstvakvormobject.

### Is het mogelijk om tekst te verankeren in het midden van het tekstvak?
 Absoluut! Gebruik gewoon`TextBoxAnchor.Center` om de tekst verticaal in het tekstvak te centreren.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
 Bekijk de[Aspose.Words-documentatie](https://reference.aspose.com/words/net/) voor meer informatie en handleidingen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
