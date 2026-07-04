---
category: general
date: 2026-05-26
description: Maak een Word‑document in C# met Aspose.Words, voeg een rechthoekvorm
  toe, stel de vulkleur in en voeg een schaduweffect toe – stapsgewijze handleiding.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: nl
og_description: Maak een Word-document in C# met Aspose.Words. Leer hoe je een rechthoekvorm
  invoegt, de vulkleur instelt en een schaduweffect toevoegt.
og_title: Word-document maken – Rechthoekvorm en schaduw invoegen in C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Word-document maken – Rechthoekvorm en schaduw invoegen in C#
url: /nl/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑document maken – Rechthoekvorm en schaduw invoegen in C#

Heb je je ooit afgevraagd hoe je **een Word‑document** programmatisch kunt maken zonder Microsoft Word eerst te openen? Je bent niet de enige. In veel automatiseringsscenario’s—denk aan facturen, contracten of bulk‑rapportgeneratie—heb je een betrouwbare manier nodig om een .docx‑bestand te creëren, een vorm erin te plaatsen, deze een kleur te geven en misschien zelfs een schaduw voor die gepolijste uitstraling.

In deze tutorial lopen we precies dat door: met Aspose.Words voor .NET **een Word‑document maken**, **een rechthoekvorm invoegen**, een vulling toepassen en **een schaduw toevoegen**. Aan het einde heb je een kant‑klaar bestand dat je in elke downstream‑workflow kunt gebruiken.  

We behandelen ook **hoe je een vorm flexibel kunt invoegen**, en waarom **hoe je vulling instelt** belangrijk is voor visuele consistentie. Geen poespas, alleen de code die je kunt kopiëren‑plakken en uitvoeren.

## Prerequisites

Voordat we beginnen, zorg dat je het volgende hebt:

- .NET 6+ (of .NET Framework 4.7+) geïnstalleerd.
- Een geldige Aspose.Words voor .NET‑licentie (of een tijdelijke evaluatiesleutel).
- Visual Studio, Rider of een andere C#‑IDE naar keuze.
- Basiskennis van C#‑syntaxis—niets ingewikkelds nodig.

Heb je dat? Geweldig, laten we starten.

## Step 1 – Create Word Document

Het eerste wat je nodig hebt is een leeg documentobject. Dit is het canvas waarop alles andere leeft.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` vertegenwoordigt het .docx‑bestand in het geheugen, terwijl `DocumentBuilder` ons een handige API biedt om tekst, tabellen en vormen in te voegen. **Een Word‑document maken** op deze manier is direct—geen UI, geen COM‑interop, alleen pure .NET.

## Step 2 – Insert Rectangle Shape

Nu we een document hebben, laten we **een rechthoekvorm invoegen**. De methode `InsertShape` neemt een `ShapeType`‑enum, breedte en hoogte (in points). We gebruiken een rechthoek van 150 × 80 points, wat ongeveer 2 × 1 inch is.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Achter de schermen maakt Aspose een `Shape`‑object aan, voegt het toe aan de huidige alinea en geeft een referentie terug die je kunt stijlen. Dit is de kern van **hoe je een vorm invoegt**—slechts één regel code, maar ongelooflijk krachtig.

## Step 3 – How to Set Fill

Een vorm zonder vulling is onzichtbaar op een witte pagina. Laten we hem een aangename lichtblauwe achtergrond geven.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Je kunt ook verlopen, texturen of zelfs een afbeelding als vulling gebruiken, maar een effen kleur houdt het voorbeeld simpel. Dit toont **hoe je vulling instelt** op elke vorm die je maakt, zodat de visuele cue die je lezers verwachten aanwezig is.

## Step 4 – How to Add Shadow

Schaduwen geven diepte en laten de vorm opvallen. Aspose.Words biedt een `ShadowFormat`‑object waarin je de zichtbaarheid kunt schakelen, een kleur kunt kiezen en blur, afstand en hoek kunt afstemmen.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Waarom juist deze waarden? Een hoek van 45° geeft een natuurlijke lichtbron rechts‑boven, een bescheiden blur houdt de schaduw subtiel, en een korte afstand voorkomt dat de vorm er los van lijkt te staan. Voel je vrij om te experimenteren—bijvoorbeeld een hoek van 135° laat de schaduw naar links‑onder vallen.

## Step 5 – Save the Document

Het werk is klaar; nu schrijven we het bestand naar schijf. Kies elk pad dat je wilt; zorg er alleen voor dat de map bestaat.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Wanneer je `ShadowShape.docx` opent in Microsoft Word, zie je een lichtblauwe rechthoek met een zachte grijze schaduw—precies wat we hebben geprogrammeerd.

## Full Working Example

Alles bij elkaar, hier is het complete, copy‑paste‑klare programma:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Expected Result

- Een bestand genaamd **ShadowShape.docx** verschijnt in de doelmap.
- Bij openen in Word zie je een lichtblauwe rechthoek gecentreerd op de eerste pagina.
- De rechthoek werpt een grijze schaduw onder een hoek van 45°, wat een subtiel 3‑D‑effect geeft.

## Common Questions & Edge Cases

**Wat als ik een andere vorm nodig heb?**  
Vervang `ShapeType.Rectangle` door een andere enum‑waarde (`Ellipse`, `Star`, `Arrow`, enz.). De rest van de code blijft hetzelfde.

**Kan ik tekst in de vorm plaatsen?**  
Ja—na het aanmaken van de vorm roep je `shape.AppendChild(new Paragraph(doc))` aan en voeg je vervolgens een `Run` met je tekst toe. Vergeet niet de `shape.TextBox`‑eigenschappen in te stellen als je tekstomloop wilt.

**Wat met DPI of meeteenheden?**  
Aspose werkt in points (1 pt = 1/72 inch). Als je centimeters verkiest, vermenigvuldig dan met 28,35 (aangezien 1 cm ≈ 28,35 pt).

**Heb ik een licentie nodig om dit te laten werken?**  
De evaluatieversie voegt een watermerk toe op de eerste pagina. Een geldige licentie verwijdert dit en ontgrendelt de volledige API.

## Tips & Gotchas

- **Pro tip:** Roep `builder.MoveToDocumentEnd()` aan voordat je een vorm invoegt als je deze helemaal aan het einde van het document wilt plaatsen.
- **Let op:** Opslaan in een alleen‑lezen map veroorzaakt een `UnauthorizedAccessException`. Zorg dat je applicatie schrijfrechten heeft.
- **Performance‑opmerking:** Voor bulk‑generatie (honderden documenten) kun je één `Document`‑instantie als sjabloon hergebruiken en klonen met `doc.Clone(true)` om herhaalde initialisatie‑overhead te vermijden.

## Conclusion

Je weet nu hoe je **een Word‑document maakt**, **een rechthoekvorm invoegt**, **vulling instelt** en **schaduw toevoegt** met Aspose.Words voor .NET. Het bovenstaande fragment is een zelfstandige oplossing die je in elk C#‑project kunt plaatsen, of het nu een console‑app, een web‑API of een achtergrondservice is.

Vanaf hier kun je verder verkennen:

- Meerdere vormen met verschillende kleuren toevoegen.
- Verlopen of afbeelding‑vullingen gebruiken (`shape.FillColor = ...` → `shape.FillPattern`).
- Vormen combineren met tabellen voor complexe rapportlay‑outs.

Probeer het, pas de parameters aan, en zie hoe je geautomatiseerde Word‑bestanden er professioneler uitzien met slechts een paar regels code. Veel programmeerplezier!

## Related Tutorials

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}