---
category: general
date: 2026-04-10
description: hoe schaduw op een vorm instellen in C# – leer hoe je een slagschaduw
  toepast, transparantie wijzigt, vervaging aanpast en vormschaduw toevoegt met Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: nl
og_description: hoe schaduw op een vorm in C# instellen – deze tutorial laat zien
  hoe je een slagschaduw toepast, transparantie wijzigt, vervaging aanpast en vormschaduw
  toevoegt met duidelijke codevoorbeelden.
og_title: hoe je een schaduw op een vorm instelt in C# – Complete gids
tags:
- Aspose.Words
- C#
- Document Automation
title: Hoe je een schaduw op een vorm in C# instelt – stapsgewijze handleiding
url: /nl/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hoe je een schaduw instelt op een vorm in C# – Complete gids

Heb je je ooit afgevraagd **hoe je een schaduw instelt** op een vorm wanneer je programmatisch een Word‑document bouwt? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze een subtiele slagschaduw nodig hebben voor een tekstvak, een logo of een call‑out‑vak, en de API‑documentatie is wat schaars.  

In deze tutorial lopen we het volledige proces door: van het laden van een `.docx`, het ophalen van de eerste `Shape`, tot het toepassen van een slagschaduw, het aanpassen van de transparantie, het wijzigen van de vervagingsradius en uiteindelijk het precies positioneren ervan. Aan het einde heb je een herbruikbare code‑snippet die werkt met Aspose.Words .NET 2023 of later, en begrijp je *waarom* elke eigenschap belangrijk is.

## Wat je nodig hebt

- **Aspose.Words for .NET** (NuGet‑pakket `Aspose.Words`) – de bibliotheek die ons de `Document`, `Shape` en `ShadowFormat`‑klassen geeft.  
- **.NET 6+** (of .NET Framework 4.7.2) – elke recente runtime volstaat.  
- Een simpel Word‑bestand (`input.docx`) dat al minstens één vorm bevat, zoals een tekstvak.  
- Visual Studio, VS Code of je favoriete IDE.

Dat is alles. Geen extra third‑party tools, geen COM‑interop, alleen pure C#.

![how to set shadow example](image-placeholder.png){:alt="hoe je een schaduw instelt op een vorm in een Word‑document"}

## Hoe je een schaduw instelt – Overzicht

Het kernidee achter **hoe je een schaduw instelt** is het manipuleren van het `ShadowFormat`‑object dat op een `Shape` zit. Beschouw `ShadowFormat` als een mini‑“stylesheet” voor de schaduw zelf: het vertelt de renderer of de schaduw zichtbaar is, welke kleur hij moet hebben, hoe transparant hij is, hoe wazig, en waar hij zich bevindt ten opzichte van de vorm.  

Hieronder staat het *complete* uitvoerbare programma. Kopieer‑en‑plak het gerust in een console‑app, druk op **F5**, en zie de schaduw verschijnen in het opgeslagen `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Waarom deze instellingen belangrijk zijn

- **Visible** – Zonder deze vlag aan te zetten, worden alle andere eigenschappen genegeerd.  
- **Color** – Een donkergrijs bootst een typische UI‑slagschaduw na; je kunt elke `Color` gebruiken.  
- **Transparency** – 0.3 geeft een *zachte* uitstraling terwijl de vorm nog leesbaar blijft.  
- **Size** – Regelt de vervaging; een waarde van 6 is meestal voldoende voor een professioneel gevoel.  
- **Distance & Angle** – Samen definiëren ze de *offset*; 2 pts op 45° levert een subtiele diagonale schaduw op.

Dat is de essentie van **hoe je een schaduw instelt**. Vervolgens splitsen we elk onderdeel zodat je **slagschaduw kunt toepassen**, **transparantie kunt wijzigen**, **vervaging kunt aanpassen**, en **vormschaduw kunt toevoegen** in isolatie.

---

## Slagschaduw toepassen op een vorm

Wanneer mensen vragen “hoe **pas ik slagschaduw toe** in C#?”, hebben ze vaak alleen de zichtbaarheid‑schakelaar en een kleur nodig. Het volgende fragment isoleert die twee regels:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Als je richt op oudere Word‑versies (2003‑2007), houd je dan aan standaardkleuren. Sommige exotische ARGB‑waarden kunnen door de legacy‑renderer worden genegeerd.

---

## Hoe je de transparantie van de schaduw wijzigt

Transparantie wordt uitgedrukt als een **float tussen 0 en 1**. Een waarde van **0** betekent een volledig ondoorzichtige schaduw; **1** maakt hem onzichtbaar. De meeste designers kiezen rond **0.2‑0.4** voor een natuurlijke look.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Randgevallen

- **Negatieve waarden** – Aspose.Words zal ze naar 0 afkappen, maar het is beter om invoer te valideren.  
- **Waarden > 1** – Afgekapt naar 1, waardoor de schaduw effectief verdwijnt.  

Als je gebruikers een percentage wilt laten kiezen, converteer het dan eerst:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Hoe je de vervaging (Size) van de schaduw aanpast

De **Size**‑eigenschap regelt de vervagingsradius. Grotere getallen produceren een zachtere, meer gediffuseerde schaduw. Het wordt gemeten in punten (pt), niet in pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Wanneer een kleine vs. grote vervaging te gebruiken

- **Kleine vervaging (2‑4 pt)** – Goed voor UI‑style callouts waar je een scherpe rand wilt.  
- **Grote vervaging (8‑12 pt)** – Werkt goed voor afgedrukte rapporten of wanneer de vorm ver van de achtergrond staat.

---

## Vormschaduw toevoegen – Positionering en richting

Het laatste onderdeel van **vormschaduw toevoegen** is de offset. Twee eigenschappen werken samen:

| Eigenschap | Betekenis |
|------------|-----------|
| **Distance** | Hoe ver de schaduw van de vorm zit (in punten). |
| **Angle**    | Richting van de offset (0° = rechts, 90° = omlaag, 180° = links, 270° = omhoog). |

Voorbeeld dat een subtiele rechtsonder‑schaduw creëert:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Je kunt experimenteren met hoeken om licht te simuleren dat vanuit verschillende bronnen komt. Een veelgebruikte truc is de gebruiker een “lichtbron” laten kiezen in een dropdown en die te vertalen naar een hoekwaarde.

---

## Volledig werkend voorbeeld (Alle stappen gecombineerd)

Hieronder staat hetzelfde programma als eerder, maar met **extra commentaar** dat de logica glashelder maakt. Kopieer dit naar `Program.cs` en voer het uit; het uitvoerbestand bevat een tekstvak met een perfect afgestemde schaduw.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Verwacht resultaat:** Open `output.docx`. Het eerste tekstvak toont een donkergrijze, 30 % transparante schaduw die licht vervaagd is (size = 6) en 2 pt offset heeft onder een hoek van 45°. Het effect is subtiel maar merkbaar—precies wat de meeste UI‑designers nastreven.

---

## Veelgestelde vragen & valkuilen

- **“Werkt dit ook met afbeeldingen?”**  
  Ja. Elke `Shape`—of het nu een tekstvak, afbeelding of auto‑shape is—heeft een `ShadowFormat`. Vervang simpelweg de logica voor het ophalen van de vorm door de juiste index of naam.

- **“Wat als het document meerdere vormen bevat?”**  
  Loop door `doc.GetChildNodes(NodeType.Shape, true)` en pas dezelfde instellingen op elke vorm toe. Je kunt ook filteren op `shape.Name` of `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}