---
category: general
date: 2026-10-26
description: Maak een leeg Word‑document in C# en leer hoe je een groepsvorm invoegt,
  vervolgens een rechthoekvorm aan de groep toevoegt. Deze gids behandelt stap‑voor‑stap
  het groeperen van meerdere vormen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: nl
lastmod: 2026-10-26
og_description: Maak een leeg Word‑document in C# en zie hoe je een groep invoegt,
  daarna een rechthoekvorm toevoegt. Beheers het groeperen van meerdere vormen met
  een compleet codevoorbeeld.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Maak een leeg Word‑document en groepeer meerdere vormen – C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een leeg Word‑document te maken en meerdere vormen te groeperen
url: /nl/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word-document te maken en meerdere vormen te groeperen

Als je programmatically een **blank Word document** moet maken, laat deze tutorial je precies zien hoe. Je ziet hoe je een groepsvorm invoegt, en vervolgens een **add rectangle** aan die groep toevoegt, waardoor de volledige workflow van een leeg document tot een gegroepeerde tekening wordt behandeld.

Werken met Word‑bestanden betekent vaak dat je verschillende tekeningen samen moet rangschikken — denk aan een diagram bestaande uit meerdere vormen. Aan het einde van deze gids kun je **group multiple shapes** uitvoeren, een **rectangle shape** invoegen, en begrijpen **how to insert group** en **how to add rectangle** op een nette, herbruikbare manier.

## Wat je nodig hebt

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
* **Aspose.Words for .NET** NuGet‑pakket (`Install-Package Aspose.Words`)
* Een basisbegrip van C# en de Visual Studio IDE (elke IDE werkt)

> **Pro tip:** Aspose.Words werkt volledig offline; je hebt geen internetverbinding nodig nadat het pakket is geïnstalleerd.

## Stap 1: Maak een leeg Word‑document

De eerste handeling is het instantieren van een leeg `Document`‑object. Dit object vertegenwoordigt het **blank Word document** dat je later zult verrijken met vormen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is:* Een `Document` zonder secties of alinea's is nog steeds een geldig .docx‑bestand. Beginnen met een schone lei garandeert dat er geen verborgen opmaak interfereert met de vormen die je later toevoegt.

## Stap 2: Voeg een groepsvorm in (how to insert group)

Een **group shape** fungeert als een container die andere tekenobjecten kan bevatten. In Aspose.Words maak je deze aan met `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Waarom een groep gebruiken?* Groeperen stelt je in staat om meerdere vormen tegelijk te verplaatsen, roteren of van grootte te wijzigen als één eenheid. Dit is essentieel voor diagrammen waarbij elementen uitgelijnd moeten blijven.

## Stap 3: Voeg een rechthoekvorm in (insert rectangle shape)

Voeg nu een rechthoek toe aan het document. De `InsertShape`‑methode retourneert een `Shape`‑object dat je later aan de groep kunt koppelen.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Waarom een rechthoek?* Rechthoeken zijn het meest voorkomende bouwblok voor stroomdiagrammen, UI‑mock‑ups en placeholder‑graphics. De afmetingen worden uitgedrukt in points (1 pt ≈ 1/72 inch).

## Stap 4: Voeg de rechthoek toe aan de groep (how to add rectangle)

Een vorm die met `InsertShape` is gemaakt, bevindt zich direct in de document‑body. Om deze onderdeel van de groep te maken, roep je `AppendChild` aan op de `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Wat er onder de motorkap gebeurt?* `AppendChild` verplaatst het rechthoek‑knooppunt van het hoofd‑verhaal van het document naar de interne collectie van de groep, waarbij de grootte en positie behouden blijven ten opzichte van de oorsprong van de groep.

## Stap 5: Sla het document op

Schrijf tenslotte het bestand naar schijf. Je kunt de resulterende `.docx` openen in Microsoft Word om de gegroepeerde rechthoek te zien.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Edge case:** Als je van plan bent meer vormen (bijv. cirkels, lijnen) aan dezelfde groep toe te voegen, herhaal dan **Stap 3** en **Stap 4** voor elke nieuwe vorm vóór het opslaan. De groep past automatisch de omvattende rechthoek aan om alle kinderen te omvatten.

## Hoe meerdere vormen te groeperen – voorbeeld uitbreiden

Hieronder staat een kort fragment dat een tweede vorm (een ellips) aan dezelfde groep toevoegt, waarmee **group multiple shapes** in één document wordt gedemonstreerd.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Wanneer je `GroupedShapeExample.docx` opent, zie je dat de rechthoek en ellips samen bewegen wanneer je de groep in Word selecteert.

## Veelgestelde vragen en probleemoplossing

| Vraag | Antwoord |
|----------|--------|
| **Heb ik een licentie nodig voor Aspose.Words?** | Een gratis evaluatie werkt zonder licentie, maar voegt een watermerk toe. Voor productie, pas een licentie toe om het watermerk te verwijderen en volledige prestaties te ontgrendelen. |
| **Kan ik vormen nauwkeurig positioneren?** | Ja. Na het invoegen van een vorm kun je de eigenschappen `Shape.Left`, `Shape.Top`, `Shape.Width` en `Shape.Height` instellen. |
| **Wat als de rechthoek verdwijnt na het opslaan?** | Zorg ervoor dat je `group.AppendChild(rectangle)` *na* het invoegen van de rechthoek aanroept. De vorm eerst aan de document‑body toevoegen en vervolgens naar de groep verplaatsen is vereist. |
| **Is het mogelijk om vormen over verschillende secties te groeperen?** | Nee. Alle vormen in een groep moeten tot hetzelfde verhaal (sectie) behoren. Maak aparte groepen per sectie indien nodig. |

## Samenvatting

Je weet nu hoe je **create blank Word document**, **insert group**, **add rectangle**, en **group multiple shapes** kunt uitvoeren met Aspose.Words voor .NET. Het volledige, uitvoerbare voorbeeld hierboven kan worden gekopieerd naar een console‑applicatie en direct worden uitgevoerd.

## Volgende stappen

* Experimenteer met **insert rectangle shape** groottes en kleuren (`rectangle.FillColor = Color.LightBlue;`).  
* Verken andere vormtypen (`ShapeType.Polygon`, `ShapeType.Line`) om je diagrammen te verrijken.  
* Leer hoe je de uiteindelijke `.docx` naar PDF kunt converteren (`doc.Save("output.pdf");`) voor distributie.  
* Duik in **how to add rectangle** voor bestaande documenten die al tekst bevatten — gebruik `DocumentBuilder.MoveTo` om de groep te positioneren waar je die nodig hebt.

Voel je vrij om de code aan te passen aan je eigen rapportage‑ of diagram‑generatiebehoeften. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een leeg Word-document te maken en vormen te groeperen in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Hoe vormen te groeperen in Word en vormen toe te voegen aan een Word-document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Hoe een rechthoekvorm te maken en vormen te groeperen in Word met Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}