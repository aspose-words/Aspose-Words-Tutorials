---
category: general
date: 2026-03-01
description: Maak een Word‑document met Aspose.Words en leer hoe je een rechthoekvorm
  toevoegt, hoe je een schaduw toevoegt, hoe je transparantie instelt en hoe je een
  vorm maakt — allemaal in C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: nl
og_description: Maak een Word-document met Aspose.Words in C#. Leer hoe je een rechthoekvorm
  toevoegt, een buitenschaduw toepast en transparantie instelt in slechts een paar
  stappen.
og_title: Maak een Word-document met een rechthoekvorm en schaduw – Gids
tags:
- Aspose.Words
- C#
- Document Generation
title: Maak een Word‑document met een rechthoekvorm en schaduw – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document met een rechthoekvorm en schaduw – Stapsgewijze gids

Heb je ooit een **een Word-document maken** moeten maken dat een op maat gestylede rechthoek bevat? Misschien bouw je een rapporttemplate en wil je een subtiele slagschaduw om de lay-out meer te laten opvallen. Je bent niet de enige—ontwikkelaars vragen voortdurend: “Hoe voeg ik een rechthoekvorm en een schaduw programmatisch toe?” Het goede nieuws is dat je dit met Aspose.Words in een handvol regels kunt doen.

In deze tutorial lopen we het volledige proces door: van het aanmaken van een leeg Word‑bestand, tot het toevoegen van een rechthoekvorm, tot het configureren van een buitenste schaduw met transparantie. Aan het einde heb je een kant‑klaar `Shadow.docx` dat je in Word kunt openen en direct het effect ziet. Geen externe tools, geen ingewikkelde XML—alleen nette C#‑code en duidelijke uitleg.

## Wat je zult leren

- **Hoe shape te maken** objecten in een Word-document met Aspose.Words.
- **Hoe een rechthoekvorm toe te voegen** aan een alinea zonder bestaande inhoud te verstoren.
- **Hoe schaduw toe te voegen** (buitenste schaduw) en de kleur, offset, vervaging en transparantie te regelen.
- **Hoe transparantie in te stellen** op de schaduw zodat deze er professioneel uitziet.
- Tips, valkuilen en variaties die je in real‑world projecten nodig kunt hebben.

### Vereisten

- .NET 6.0 of later (de API werkt ook met .NET Framework 4.6+).
- Aspose.Words for .NET geïnstalleerd via NuGet (`Install-Package Aspose.Words`).
- Een basisbegrip van C#-syntaxis—niets bijzonders, alleen de gebruikelijke `using`-statements en objectcreatie.

> **Pro tip:** Als je Visual Studio gebruikt, schakel dan “nullable reference types” in om potentiële null‑reference bugs vroegtijdig te detecteren.

## Stap 1 – Maak een leeg Word-document

Om **een Word-document te maken** beginnen we met de `Document`-klasse. Beschouw het als een leeg canvas; je kunt later secties, alinea's, tabellen of vormen toevoegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Waarom hebben we een nieuw `Document`-instance nodig? Omdat elke shape, alinea of stijl leeft binnen een document object model (DOM). Beginnen met een schoon document garandeert dat de toegevoegde rechthoek geen interferentie veroorzaakt met bestaande inhoud.

## Stap 2 – Definieer de rechthoekvorm

Nu **hoe shape te maken** een rechthoek. De `Shape`-constructor neemt het eigenaar‑document en het shape‑type. We stellen ook de breedte en hoogte in punten in (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Je vraagt je misschien af: “Kan ik centimeters in plaats van punten gebruiken?” De API accepteert alleen punten, maar je kunt converteren: `points = centimeters * 28.35`. Deze kleine conversie is handig bij het uitlijnen van shapes op paginamarges.

## Stap 3 – Voeg een buitenste schaduw toe en stel transparantie in

Hier gebeurt de magie: **hoe schaduw toe te voegen** en **hoe transparantie in te stellen** op die schaduw. De `ShadowFormat`‑eigenschap geeft je volledige controle.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Waarom deze instellingen?**  
- **Transparency** laat de onderliggende paginatekstuur doorschijnen, waardoor de schaduw niet te zwaar lijkt.  
- **OffsetX/Y** creëren de illusie dat de shape van de pagina wordt opgelicht.  
- **BlurRadius** verzacht de randen—zonder deze zou de schaduw een harde rechthoek zijn, wat onnatuurlijk oogt.

Als je een dramatischer effect wilt, verhoog dan `OffsetX/Y` naar 10 en vergroot `BlurRadius` naar 8. Omgekeerd, voor een subtiele hint, houd ze op respectievelijk 2 en 2.

## Stap 4 – Voeg de shape in het document in

We voegen nu **rechthoekvorm toe** aan de eerste alinea van het document. Als het document geen inhoud heeft, wordt `FirstParagraph` automatisch voor je aangemaakt.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Wat als je de shape wilt plaatsen in een specifieke tabelcel of een latere alinea? Zoek gewoon dat node (`doc.GetChild(NodeType.Paragraph, index, true)`) en roep `AppendChild` daarop aan. Hetzelfde shape‑object kan gekloond worden als je meerdere exemplaren nodig hebt.

## Stap 5 – Sla het document op

Tot slot **maken we een Word-document** bestand op schijf. Gebruik een pad dat bij je omgeving past; het voorbeeld gebruikt een placeholder.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Wanneer je `Shadow.docx` opent in Microsoft Word, zie je een lichtgrijze rechthoek met een zachte buitenste schaduw die naar rechtsonder is verschoven. De 30 % transparantie van de schaduw zorgt ervoor dat deze de pagina niet domineert.

![Word-document maken met een rechthoekvorm met schaduw](image.png "Word-document maken met een rechthoekvorm met schaduw")

*Afbeeldings‑alt‑tekst: Word-document maken met een rechthoekvorm met schaduw*

## Volledige, kant‑klaar code

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie. Geen ontbrekende onderdelen, geen “zie docs voor meer”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Verwacht resultaat

- Een bestand met de naam **Shadow.docx** verschijnt in de doelmap.
- Het openen in Word toont een rechthoek (200 × 100 pt) met een donkergrijze buitenste schaduw.
- De schaduw is 5 pt horizontaal en verticaal verschoven, vervaagd, en 30 % transparant.

## Veelgestelde vragen & randgevallen

| Question | Answer |
|----------|--------|
| **Kan ik de schaduwkleur aanpassen aan mijn merk?** | Absoluut—vervang gewoon `System.Drawing.Color.DarkGray` door elke `Color` die je wilt, bijv. `Color.FromArgb(255, 0, 120, 215)` voor een blauwe accent. |
| **Wat als ik een binnenste schaduw nodig heb in plaats van een buitenste?** | Stel `ShadowFormat.Style = ShadowStyle.InnerShadow`. De rest van de eigenschappen werkt hetzelfde. |
| **Wordt transparantie ondersteund in oudere Word‑versies?** | Ja. Aspose.Words schrijft de juiste XML die Word 2007+ begrijpt. Oudere versies negeren mogelijk de transparantiewaarde maar tonen de schaduw wel. |
| **Kan ik meerdere shapes met verschillende schaduwen toevoegen?** | Zeker—maak gewoon nieuwe `Shape`‑instances, configureer elke schaduw onafhankelijk, en voeg ze toe aan de gewenste nodes. |
| **Hoe zit het met prestaties bij honderden shapes?** | Het maken van veel shapes kan het geheugenverbruik verhogen. Hergebruik één `Document`‑instance en voeg shapes toe in een lus; ruim tijdelijke objecten op als je tegen geheugenlimieten aanloopt. |

## Tips voor real‑world projecten

- **Batchgeneratie:** Bij het genereren van rapporten voor veel gebruikers, instantiate een enkele `Document`‑template en kloon deze voor elke iteratie. Vervang placeholders voordat je shapes toevoegt.
- **Dynamische afmetingen:** Gebruik paginadimensies (`document.FirstSection.PageSetup.PageWidth`) om de shape‑grootte relatief aan de pagina te berekenen, zodat de lay-out consistent blijft over verschillende papierformaten.
- **Testen:** Open altijd de gegenereerde `.docx` in Word na een wijziging van de schaduw‑parameters. Visuele feedback is sneller dan gokken.

## Volgende stappen

Nu je weet **hoe rechthoekvorm toe te voegen**, **hoe schaduw toe te voegen**, en **hoe transparantie in te stellen**, overweeg dan het volgende te verkennen:

- **Gradient fills** toevoegen aan shapes (`Shape.FillFormat`).
- **Afbeeldingen** insluiten in shapes voor watermerk‑effecten.
- **Tabellen** gebruiken om meerdere schaduw‑shapes in een raster uit te lijnen.
- Hetzelfde document exporteren naar PDF (`document.Save("output.pdf")`) terwijl je de schaduwen behoudt.

Elk van deze bouwt voort op dezelfde kernconcepten, zodat je je comfortabel voelt bij het uitbreiden van de code.

### Samenvatting

We begonnen met **een Word-document maken** met Aspose.Words, daarna **hoe shape te maken** een rechthoek, pasten **hoe schaduw toe te voegen** toe, pasten **hoe transparantie in te stellen** aan, en slaagden het resultaat op. Het volledige proces past in een compact, herbruikbaar patroon dat je kunt aanpassen aan elke automatiseringsscenario.

Voel je vrij om te experimenteren—verander kleuren, speel met offsets, of stapel meerdere shapes op elkaar. Als je tegen een probleem aanloopt, bekijk dan de bovenstaande secties opnieuw; ze zijn ontworpen als snelle referentie. Veel plezier met coderen, en moge je documenten er altijd gepolijst uitzien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}