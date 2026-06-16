---
category: general
date: 2026-05-01
description: Hoe schaduw op een vorm verplaatsen in Aspose.Words met C#. Leer hoe
  je schaduw aan een vorm toevoegt, de vervaging aanpast, transparantie instelt en
  de schaduw roteert in enkele minuten.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: nl
og_description: Hoe je een schaduw op een vorm verplaatst in Aspose.Words met C#.
  Deze tutorial laat zien hoe je een schaduw aan een vorm toevoegt, de vervaging aanpast,
  transparantie instelt en de schaduw roteert.
og_title: Hoe schaduw te verplaatsen in Aspose.Words – Complete C#-gids
tags:
- Aspose.Words
- C#
- Document Automation
title: Hoe de schaduw te verplaatsen in Aspose.Words – Complete C#-gids
url: /nl/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Schaduw Verplaatsen in Aspose.Words – Complete C# Gids

Heb je je ooit afgevraagd **hoe je schaduw verplaatst** op een vorm in een Word‑document zonder Word handmatig te openen? In mijn dagelijkse werk heb ik vaak een vorm‑schaduw programmatisch moeten aanpassen—of het nu gaat om een gepolijste rapportage of een dynamisch sjabloon. Het goede nieuws? Met Aspose.Words kun je dit in een handvol regels doen, en je leert ook **schaduw toevoegen aan vorm**, **hoe je vervaging wijzigt**, **hoe je transparantie instelt**, en **hoe je schaduw roteert** in één keer.

In deze tutorial lopen we een real‑world scenario door: een bestaand DOCX‑bestand laden dat al een vorm bevat, de positie, zachtheid, opacity en richting van de schaduw aanpassen, en tenslotte het resultaat opslaan. Aan het einde heb je een herbruikbare snippet die je in elk .NET‑project kunt plakken, en begrijp je waarom elke eigenschap belangrijk is.

## Voorvereisten – Wat je nodig hebt voordat je begint

- **Aspose.Words for .NET** (versie 23.12 of later). Je kunt het via NuGet ophalen met `Install-Package Aspose.Words`.
- Een .NET 6+ ontwikkelomgeving (Visual Studio, VS Code, Rider—wat je maar prefereert).
- Een invoer‑Word‑bestand (`input.docx`) dat al minstens één vorm bevat (een rechthoek, cirkel of afbeelding volstaat).
- Basiskennis van C#‑syntaxis—niets ingewikkelds.

Als je een van deze mist, pauzeer even en installeer de bibliotheek; de rest van de gids gaat ervan uit dat het pakket al is gerefereerd.

## Stap 1: Het Document Laden en de Doelform Vinden – **Hoe je Schaduw Verplaatst** Begint Hier

Het eerste wat we doen is het bron‑document laden en de vorm zoeken die we willen aanpassen. Aspose.Words behandelt elk object (alinea’s, tabellen, vormen) als een knoop in een boom, zodat we er direct op kunnen queryen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Waarom dit belangrijk is:** Het document één keer laden en dezelfde `Document`‑instantie hergebruiken is efficiënt. De `GetChild`‑aanroep is veilig omdat hij `null` retourneert als de index buiten bereik ligt, waardoor we ontbrekende vormen netjes kunnen afhandelen.

## Stap 2: De Vervagingsstraal Aanpassen – Master **Hoe je Vervaging Wijzigt**

Een zachte schaduw oogt professioneel, terwijl een harde rand goedkoop kan lijken. De eigenschap `BlurRadius` regelt de zachtheid in punten (1 pt ≈ 1/72 inch). Laten we deze verhogen naar 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Pro tip:** De standaardvervaging is 0,5 pt. Alles boven 5 pt valt meestal op, maar pas op dat je het niet te groot maakt—dan kan de vorm loskomen van de pagina.

## Stap 3: Transparantie Instellen – Het Antwoord op **Hoe je Transparantie Instelt**

Transparantie bepaalt hoe doorschijnend de schaduw is. Een waarde van `0` betekent volledig ondoorzichtig; `1` betekent volledig onzichtbaar. Voor een subtiel effect gebruiken we `0.3` (30 % transparant).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Waarom je dit zou kunnen willen:** Als de vorm donker is, kan een volledig ondoorzichtige schaduw de onderliggende tekst verdrinken. Transparantie aanpassen houdt het document leesbaar terwijl je toch diepte toevoegt.

## Stap 4: De Schaduw Verplaatsen – De Kern van **Hoe je Schaduw Verplaatst**

De eigenschap `Distance` bepaalt hoe ver de schaduw van de vorm wordt verschoven, gemeten in punten. Een grotere afstand duwt de schaduw verder weg, wat een dramatischer effect geeft.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Wat als je een heel kleine offset nodig hebt?** Een `Distance` van `0` plaatst de schaduw direct achter de vorm, wat handig kan zijn voor reliëf‑effecten.

## Stap 5: De Lichtbron Roteren – Oplossen **Hoe je Schaduw Roteert**

Schaduwen vallen niet alleen recht naar beneden; ze volgen de hoek van de lichtbron. De eigenschap `Angle` (in graden) roteert de schaduw rond de vorm. Laten we hem 45° kantelen.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Snelle proef:** Probeer `90` voor een rechts‑vallende schaduw of `-30` voor een links‑hellende. De visuele verandering is direct merkbaar.

## Stap 6: Het Document Opslaan – Het Resultaat Zien van **Schaduw Toevoegen aan Vorm**

Nu we de schaduw hebben aangepast, schrijven we het document terug naar de schijf. Je kunt het origineel overschrijven of een nieuw bestand maken; het voorbeeld gebruikt een nieuw uitvoerbestand.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Verwacht resultaat:** Open `output.docx`. De schaduw van de vorm zal zachter, iets verschoven, halfdoorzichtig en onder een hoek van 45° verschijnen. Als je het naast `input.docx` zet, is het verschil onmiskenbaar.

### Volledig Werkend Voorbeeld (Klaar om te Kopiëren‑Plakken)

Hieronder staat het volledige programma in één blok. Plak het in een nieuw console‑project, vervang `YOUR_DIRECTORY` door een echte map‑pad, en voer uit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Veelgestelde Vragen & Randgevallen

### Wat als het document meerdere vormen bevat?

Je kunt door alle vormen itereren:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Kan ik een schaduw toevoegen aan een vorm die er nog geen heeft?

Absoluut. Het `ShadowFormat`‑object is altijd aanwezig; je hoeft het alleen maar in te schakelen:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Werkt dit met afbeeldingen en SmartArt?

Ja. Elke knoop die afgeleid is van `Shape`—inclusief afbeeldingen, grafieken en SmartArt—heeft een `ShadowFormat`. Dezelfde eigenschappen zijn van toepassing.

### Hoe regel ik de kleur van de schaduw?

Gebruik de eigenschap `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Compatibiliteitszorgen?

Aspose.Words 23.12+ ondersteunt .NET 6, .NET Core 3.1 en .NET Framework 4.6.2+. De getoonde API is stabiel over deze versies heen.

## Conclusie

We hebben zojuist **hoe je schaduw verplaatst** op een vorm met Aspose.Words behandeld, en onderweg ook **schaduw toevoegen aan vorm**, **hoe je vervaging wijzigt**, **hoe je transparantie instelt**, en **hoe je schaduw roteert** gedemonstreerd. Het complete, uitvoerbare voorbeeld laat je elke vorm‑schaduw in enkele seconden aanpassen, waardoor je documenten een gepolijste, professionele uitstraling krijgen zonder ooit Word te openen.

Klaar voor de volgende stap? Probeer deze schaduw‑aanpassingen te combineren met **conditionele opmaak**—bijvoorbeeld alleen een diepere schaduw toepassen op koppen of op grafieken die een bepaalde grootte overschrijden. Of verken **gradient fills** voor de vorm zelf om een echt opvallend ontwerp te creëren.

Als je ergens vastloopt, laat dan een reactie achter. Veel programmeerplezier, en moge je schaduwen altijd precies vallen waar jij ze wilt!

![Diagram dat het effect van het verplaatsen van een schaduw op een vorm toont – voorbeeld hoe je schaduw verplaatst](https://example.com/images/shadow-demo.png "voorbeeld hoe je schaduw verplaatst")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}