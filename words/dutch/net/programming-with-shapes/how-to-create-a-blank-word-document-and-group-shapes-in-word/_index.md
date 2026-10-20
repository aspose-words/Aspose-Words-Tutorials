---
category: general
date: 2026-10-20
description: Leer hoe je een leeg Word‑document maakt, vormen groepeert in Word, de
  vulkleur van een vorm instelt en het omlooptype inline gebruikt, met een volledig
  C#‑voorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: nl
lastmod: 2026-10-20
og_description: Maak een leeg Word‑document, groepeer vormen in Word en stel de vulkleur
  van de vorm in met wrap‑type inline met behulp van Aspose.Words en C#. Volg de volledige
  tutorial.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Maak een leeg Word‑document en groepeer vormen in Word – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een leeg Word‑document te maken en vormen te groeperen in Word met Aspose.Words
url: /nl/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een leeg Word‑document en groepeer je vormen in Word

Als je een **leeg Word‑document** moet maken dat meerdere vormen bevat die als één eenheid functioneren, laat deze gids je precies zien hoe. Je ziet hoe je **vormen groepeert in Word**, de vulkleur van een vorm instelt en **wrap type inline** toepast — alles met een beknopt, uitvoerbaar C#‑programma.

De tutorial loopt je door elke regel code, legt uit waarom elke stap belangrijk is en belicht veelvoorkomende valkuilen. Aan het einde heb je een .docx‑bestand dat een rechthoek en een tekstvak gegroepeerd toont, klaar voor verdere automatisering.

## Wat je zult leren

* Hoe je een leeg Word‑bestand initialiseert met Aspose.Words.
* De juiste manier om een **GroupShape** te maken en onderliggende vormen toe te voegen.
* Technieken voor **set shape fill color** en het positioneren te controleren.
* Het gebruik van **wrap type inline** zodat de groep zich gedraagt als één inline‑object.
* Hoe je het resultaat opslaat en verifieert.

Ervaring met Aspose.Words is niet vereist, maar je moet vertrouwd zijn met basis C#‑syntaxis en Visual Studio (of een andere IDE) geïnstalleerd hebben.

## Vereisten

| Vereiste | Reden |
|----------|-------|
| .NET 6.0 or later | Levert de runtime voor het C#‑project. |
| Aspose.Words for .NET (latest version) | Levert de `Document`, `DocumentBuilder` en vormklassen die in het voorbeeld worden gebruikt. |
| A writable folder path | De `doc.Save`‑aanroep heeft een geldige map nodig om het uitvoerbestand te schrijven. |
| Basic C# knowledge | Stelt je in staat de code te volgen en aan te passen voor je eigen scenario's. |

Installeer Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Stap 1: Maak een leeg Word‑document

De eerste handeling is om een **leeg Word‑document** te **maken**. De `Document`‑klasse van Aspose.Words vertegenwoordigt een Word‑bestand in het geheugen, en `DocumentBuilder` biedt een handige API om het te bewerken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: Beginnen met een schoon document garandeert dat de groepsvorm die je toevoegt de enige inhoud zal zijn, waardoor verificatie eenvoudig wordt.

## Stap 2: Definieer een groepsvorm met wrap type inline

Een **GroupShape** fungeert als een container voor andere vormen. Het instellen van zijn `WrapType` op `Inline` zorgt ervoor dat de groep zich gedraagt als één inline‑object in de alinea‑stroom.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Waarom dit belangrijk is*: Het gebruik van **wrap type inline** voorkomt dat de groep wegzweeft van de omringende tekst, wat essentieel is wanneer je wilt dat de groep als één eenheid beweegt.

## Stap 3: Voeg een rechthoek toe en stel de vulkleur van de vorm in

Een rechthoek is een veelvoorkomend visueel element. De `Shape`‑constructor neemt een `ShapeType`; daarna geven we de afmetingen en vulkleur op.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Waarom dit belangrijk is*: De eigenschap `FillColor` toont **set shape fill color** in de praktijk, waardoor de rechthoek een lichtblauwe achtergrond krijgt die opvalt in het uiteindelijke document.

## Stap 4: Voeg een tekstvak toe – hoe je vormen effectief groepeert

Een tekstvak biedt bewerkbare tekst binnen de groep. Positioneer het relatief aan het coördinatensysteem van de groep door de `Top`‑eigenschap aan te passen.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Waarom dit belangrijk is*: Deze stap beantwoordt **how to group shapes** — door elke onderliggende vorm toe te voegen aan dezelfde `GroupShape`‑instantie. De `Top`‑offset zorgt ervoor dat het tekstvak onder de rechthoek verschijnt, wat precieze lay-outcontrole demonstreert.

## Stap 5: Voeg de voltooide groepsvorm in het document in

Nu de groep beide onderliggende vormen bevat, voeg je deze in op de huidige builder‑positie.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Waarom dit belangrijk is*: Het invoegen van de groep als één node garandeert dat Word de rechthoek en het tekstvak als één logisch object behandelt, waardoor hun relatieve posities tijdens het bewerken behouden blijven.

## Stap 6: Sla het document op en verifieer de output

Schrijf tenslotte het document naar schijf. Vervang `YOUR_DIRECTORY` door een echt pad op jouw machine.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Wanneer je `GroupShape.docx` opent in Microsoft Word, zou je een lichtblauwe rechthoek moeten zien met een tekstvak gelabeld “Grouped text” direct eronder geplaatst. Het selecteren van een van beide vormen selecteert de hele groep, wat bevestigt dat **group shapes in Word** werkt zoals bedoeld.

### Verwacht resultaat

* Een .docx‑bestand dat één alinea bevat.
* Binnen de alinea een inline‑groep die eruitziet als één samengesteld object.
* De rechthoek is gevuld met lichtblauw, en het tekstvak toont “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Schermafbeelding van een leeg Word‑document met een gegroepeerde rechthoek en tekstvak gemaakt met Aspose.Words"}

## Veelgestelde vragen en afhandeling van randgevallen

### Wat als ik wil dat de groep zweeft in plaats van inline te zijn?

Vervang `WrapType.Inline` door `WrapType.TopBottom` (of een andere `WrapType`‑enumwaarde). Zwevende groepen kunnen onafhankelijk van de alinea‑stroom worden gepositioneerd, maar ze verliezen de automatische inline‑uitlijning.

### Kan ik meer vormen toevoegen, zoals cirkels of afbeeldingen?

Ja. Maak extra `Shape`‑objecten met `ShapeType.Ellipse` of `ShapeType.Image`, configureer hun eigenschappen en roep `group.AppendChild(newShape)` aan. De groep zal automatisch uitbreiden om de nieuwe grenzen te omvatten als je `group.Bounds` dienovereenkomstig bijwerkt.

### Hoe wijzig ik de totale grootte van de groep nadat kinderen zijn toegevoegd?

Pas `group.Bounds` aan nadat alle kinderen zijn toegevoegd, of bereken programmatically de unie van de kind‑grenzen. Dit zorgt ervoor dat het hit‑test‑gebied van de groep overeenkomt met de visuele inhoud.

### Wat als de uitvoermap niet bestaat?

Aspose.Words throws a `DirectoryNotFoundException`. Create the directory first:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Werkt dit met .NET Framework in plaats van .NET Core?

Alle gebruikte API’s (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) zijn beschikbaar in de .NET Framework‑versie van Aspose.Words, dus dezelfde code werkt ongewijzigd.

## Pro‑tips

* **Performance tip** – Hergebruik één `DocumentBuilder`‑instantie bij het invoegen van veel groepen; het maken van een nieuwe builder per groep voegt overhead toe.
* **Visual consistency** – Stel `rectangle.StrokeColor` in op dezelfde kleur als `FillColor` voor een naadloze uitstraling, of zet `rectangle.LineWidth = 0` om de rand te verbergen.
* **Debugging** – Roep `doc.UpdatePageLayout()` aan vóór het opslaan als je veel vormen wijzigt; dit dwingt Word om de lay-out opnieuw te berekenen en kan onverwachte afsnijding voorkomen.

## Conclusie

Je weet nu hoe je een **leeg Word‑document** maakt, **vormen groepeert in Word**, **vulkleur van een vorm instelt**, en **wrap type inline** toepast met Aspose.Words voor .NET. Het volledige voorbeeld toont de standaardaanpak voor het bouwen van samengestelde grafische elementen die zich gedragen als één object in Word.

Van hieruit kun je verder verkennen:

* Het toevoegen van extra vormen zoals afbeeldingen of grafieken.
* Experimenteren met verschillende `WrapType`‑waarden voor zwevende groepen.
* Het automatiseren van batch‑generatie van gegroepeerde diagrammen over meerdere documenten.

Voel je vrij de code aan te passen aan je eigen automatiseringsscenario's, en deel je resultaten in de reacties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeg Word‑document maken met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Hoe PDF opslaan vanuit Word met inline‑vormen – Complete gids](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}