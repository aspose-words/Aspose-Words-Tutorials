---
"description": "Leer hoe u verticale ankerposities voor tekstvakken in Word-documenten instelt met Aspose.Words voor .NET. Inclusief eenvoudige stapsgewijze handleiding."
"linktitle": "Verticale anker"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Verticale anker"
"url": "/nl/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verticale anker

## Invoering

Heb je ooit de behoefte gehad om precies te bepalen waar tekst in een tekstvak in een Word-document moet verschijnen? Misschien wil je je tekst verankeren aan de boven-, midden- of onderkant van het tekstvak? Zo ja, dan ben je hier aan het juiste adres! In deze tutorial laten we zien hoe je Aspose.Words voor .NET gebruikt om de verticale verankering van tekstvakken in Word-documenten in te stellen. Zie verticale verankering als de toverstaf die je tekst precies op de gewenste plek in de container plaatst. Klaar om aan de slag te gaan? Aan de slag!

## Vereisten

Voordat we dieper ingaan op verticale verankering, moet u een aantal zaken regelen:

1. Aspose.Words voor .NET: Zorg ervoor dat de Aspose.Words voor .NET-bibliotheek is geïnstalleerd. Als u deze nog niet hebt, kunt u deze downloaden. [download het hier](https://releases.aspose.com/words/net/).
2. Visual Studio: in deze zelfstudie gaan we ervan uit dat u Visual Studio of een andere .NET IDE gebruikt voor het coderen.
3. Basiskennis van C#: Kennis van C# en .NET helpt u de cursus soepel te volgen.

## Naamruimten importeren

Om te beginnen moet je de benodigde naamruimten importeren in je C#-code. Dit is waar je je applicatie vertelt waar de klassen en methoden die je gaat gebruiken te vinden zijn. Zo doe je dat:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Deze naamruimten bieden de klassen die u nodig hebt om met documenten en vormen te werken.

## Stap 1: Initialiseer het document

Allereerst moet je een nieuw Word-document maken. Zie dit als het opzetten van je canvas voordat je begint met schilderen.

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier, `Document` is jouw lege canvas, en `DocumentBuilder` is uw penseel waarmee u vormen en tekst toevoegt.

## Stap 2: Een tekstvakvorm invoegen

Laten we nu een tekstvak aan ons document toevoegen. Dit is waar je tekst komt te staan. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

In dit voorbeeld, `ShapeType.TextBox` specificeert de gewenste vorm en `200, 200` zijn de breedte en hoogte van het tekstvak in punten.

## Stap 3: Plaats het verticale anker

Hier gebeurt het wonder! Je kunt de verticale uitlijning van de tekst in het tekstvak instellen. Dit bepaalt of de tekst aan de boven-, midden- of onderkant van het tekstvak wordt verankerd.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

In dit geval, `TextBoxAnchor.Bottom` zorgt ervoor dat de tekst aan de onderkant van het tekstvak wordt verankerd. Als u de tekst wilt centreren of uitlijnen met de bovenkant, gebruikt u `TextBoxAnchof.Center` or `TextBoxAnchor.Top`, respectievelijk.

## Stap 4: Tekst toevoegen aan het tekstvak

Nu is het tijd om wat inhoud aan je tekstvak toe te voegen. Zie het als het invullen van je canvas met de laatste hand.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Hier, `MoveTo` zorgt ervoor dat de tekst in het tekstvak wordt ingevoegd en `Write` voegt de eigenlijke tekst toe.

## Stap 5: Sla het document op

De laatste stap is het opslaan van je document. Dit is vergelijkbaar met het inlijsten van je voltooide schilderij.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Conclusie

En voilà! Je hebt net geleerd hoe je de verticale uitlijning van tekst in een tekstvak in een Word-document kunt bepalen met Aspose.Words voor .NET. Of je tekst nu bovenaan, in het midden of onderaan wilt verankeren, deze functie geeft je nauwkeurige controle over de lay-out van je document. Dus de volgende keer dat je de tekstplaatsing van je document moet aanpassen, weet je precies wat je moet doen!

## Veelgestelde vragen

### Wat is verticale verankering in een Word-document?
Met verticale verankering bepaalt u waar de tekst in een tekstvak wordt geplaatst, bijvoorbeeld boven, in het midden of onder.

### Kan ik andere vormen dan tekstvakken gebruiken?
Ja, u kunt verticale verankering gebruiken bij andere vormen, maar tekstvakken worden het meest gebruikt.

### Hoe verander ik het ankerpunt nadat ik het tekstvak heb gemaakt?
U kunt het ankerpunt wijzigen door de `VerticalAnchor` eigenschap op het tekstvakvormobject.

### Is het mogelijk om tekst te verankeren in het midden van het tekstvak?
Absoluut! Gebruik gewoon `TextBoxAnchor.Center` om de tekst verticaal in het tekstvak te centreren.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
Bekijk de [Aspose.Words-documentatie](https://reference.aspose.com/words/net/) voor meer informatie en handleidingen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}