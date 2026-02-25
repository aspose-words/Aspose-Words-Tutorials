---
category: general
date: 2026-02-24
description: Maak een rechthoekvorm in C# met Aspose.Words, voeg een schaduw toe aan
  de vorm en sla het document op als PDF. Leer hoe je een schaduw toevoegt en hoe
  je een PDF opslaat in enkele minuten.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: nl
og_description: Maak een rechthoekvorm in C# met Aspose.Words, voeg vervolgens een
  schaduw toe aan de vorm en sla het document op als PDF – een volledige, stapsgewijze
  handleiding.
og_title: Maak een rechthoekvorm, voeg schaduw toe & sla PDF op
tags:
- Aspose.Words
- C#
- PDF generation
title: Maak rechthoekvorm, voeg schaduw toe & sla PDF op
url: /nl/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

shortcodes unchanged.

Then heading "# Create rectangle shape, add shadow & save PDF" -> Dutch: "# Rechthoekvorm maken, schaduw toevoegen & PDF opslaan"

Then paragraph.

Let's translate step by step.

I'll produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken, schaduw toevoegen & PDF opslaan

Altijd al een **rechthoekvorm** willen maken in een Word‑document, maar ook een mooie slagschaduw en een PDF‑output nodig had? Je bent niet de enige. In veel rapportage‑ of facturatie‑projecten maakt de visuele afwerking—zoals een subtiele schaduw—het verschil tussen “gewoon een bestand” en een “professioneel document”.

In deze tutorial lopen we precies dat door: met **Aspose.Words for .NET** een rechthoekvorm maken, schaduw aan de vorm toevoegen en tenslotte **het document opslaan als PDF**. Aan het einde heb je een kant‑klaar C#‑console‑applicatie die een PDF met een gearceerde rechthoek produceert, en begrijp je hoe je de schaduw kunt aanpassen of de exportopties kunt wijzigen.

## Wat je nodig hebt

- .NET 6 SDK (of een recente .NET‑versie) – de API werkt even goed op .NET Framework 4.x.  
- Aspose.Words for .NET NuGet‑pakket (`Aspose.Words`) – installeer het met `dotnet add package Aspose.Words`.  
- Een code‑editor – Visual Studio, VS Code of Rider volstaat.  

Geen extra licentiestappen voor dit voorbeeld; de gratis evaluatiemodus is voldoende om de PDF‑output te zien.

## Stap 1: Het project opzetten en namespaces importeren

Allereerst maken we een console‑project en halen we de klassen binnen die we nodig hebben.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Waarom dit belangrijk is:* `Document` en `DocumentBuilder` geven ons het canvas, terwijl `Shape` en `ShadowFormat` ons laten tekenen en de rechthoek stylen. Ze vooraf importeren houdt de latere code overzichtelijk.

## Stap 2: **Rechthoekvorm maken** met de gewenste afmetingen

Nu maken we daadwerkelijk een leeg document en voegen we een rechthoek in. Let op dat de `InsertShape`‑methode een `Shape`‑object retourneert dat we meteen kunnen stylen.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Uitleg*: De grootte wordt uitgedrukt in punten (1 pt = 1/72 in). Pas de getallen aan om bij je lay‑out te passen. We geven de vorm ook een lichtblauwe vulling zodat de schaduw goed zichtbaar is.

## Stap 3: **Schaduw aan vorm toevoegen** – het effect fijn afstellen

Een schaduw is niet alleen “aan/uit”. Je kunt de kleur, vervaging, afstand, richting en zelfs transparantie regelen. Hieronder een praktische configuratie die goed werkt voor de meeste rapporten.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Waarom je deze waarden zou kunnen wijzigen:*  
- **BlurRadius** – verhogen voor een dromerig effect, verlagen voor een scherpe rand.  
- **Direction** – 0° wijst naar rechts, 90° naar beneden, 180° naar links, enz. Roteren om bij je paginalay‑out te passen.  
- **Transparency** – `0` voor een solide schaduw, `0.5` voor half‑transparant, enz.

### Hoe je schaduw toevoegt – alternatieve benaderingen

Als je een **meerdere‑lagen schaduw** nodig hebt (bijv. een donkere buitenste schaduw plus een lichtere binnenste), kun je een tweede vorm maken, die offsetten en een andere `ShadowFormat` instellen. Of, voor een snelle “geen‑vervaging” look, `BlurRadius = 0` gebruiken.

## Stap 4: **Document opslaan als PDF** – de uiteindelijke export

Met de rechthoek en zijn schaduw klaar, is de laatste stap het bestand wegschrijven als PDF. Aspose.Words verzorgt de conversie intern; je roept simpelweg `Save` aan met het gewenste formaat.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tip*: Als je PDF‑compliance (PDF/A, PDF/X) moet regelen of lettertypen wilt insluiten, gebruik dan een overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Dat is in één zin het **hoe je pdf opslaat**‑deel.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑plakken in `Program.cs`. Het compileert en draait direct (zorg er alleen voor dat de output‑map bestaat).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Verwacht resultaat

Open de gegenereerde `ShadowRectangle.pdf`. Je ziet één pagina met een lichtblauwe rechthoek, een zachte grijze schaduw die 45° naar rechtsonder is verschoven, en schone randen. De PDF moet leesbaar zijn in elke moderne lezer (Adobe Acrobat, Edge, Chrome).

![Rechthoekvorm maken met schaduw in PDF](/images/shadow-rectangle.png "Rechthoekvorm maken met schaduw")

*(De alt‑tekst van de afbeelding bevat het primaire zoekwoord voor SEO.)*

## Veelgestelde vragen & edge‑case handling

**Wat als de schaduw verdwijnt in de PDF?**  
Zorg dat je een recente versie van Aspose.Words gebruikt (≥23.3). Oudere builds hadden een bug waardoor bepaalde schaduweigenschappen werden genegeerd tijdens PDF‑conversie.

**Kan ik de schaduwkleur aanpassen aan mijn huisstijl?**  
Zeker—vervang gewoon `System.Drawing.Color.Gray` door elke gewenste `Color`, bijvoorbeeld `Color.FromArgb(128, 0, 0, 255)` voor een half‑transparante blauwe tint.

**Hoe voeg ik een schaduw toe aan andere vormen (ellipse, ster, enz.)?**  
Dezelfde `ShadowFormat` werkt voor elk `Shape`‑object. Nadat je de vorm hebt gemaakt, haal je zijn `ShadowFormat` op en stel je de eigenschappen in.

**Wat betreft DPI‑ of schaalproblemen?**  
PDF‑rendering respecteert de puntgrootte van de vorm. Als je een hogere resolutie nodig hebt (bijv. voor afdrukken), pas dan de afmetingen van de vorm aan of stel `PdfSaveOptions.ImageResolution` in.

**Kan ik exporteren naar andere formaten, zoals PNG?**  
Ja—roep gewoon `document.Save("output.png", SaveFormat.Png)` aan. De schaduw wordt op dezelfde manier gerenderd.

## Pro‑tips & best practices

- **Hergebruik de builder**: Als je meerdere vormen toevoegt, houd dan één `DocumentBuilder`‑instantie; dat is goedkoper dan er steeds nieuwe te maken.  
- **Batch‑opslaan**: Bij het genereren van veel PDF’s in een lus, hergebruik het `PdfSaveOptions`‑object om herhaalde allocaties te vermijden.  
- **Testen**: Open altijd de PDF na het opslaan om te verifiëren dat de schaduw verschijnt zoals verwacht. Sommige PDF‑viewers renderen schaduwen net iets anders; Adobe Acrobat is de meest betrouwbare referentie.  
- **Prestaties**: Voor grote documenten kun je de automatische paginabreaks van `DocumentBuilder.InsertShape` uitschakelen door `builder.PageSetup.DifferentFirstPageHeaderFooter = false` te zetten als je die niet nodig hebt.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **een rechthoekvorm te maken**, **schaduw aan de vorm toe te voegen**, en **het document op te slaan als PDF** met Aspose.Words for .NET. De code is compact, de concepten zijn uitgelegd, en je hebt nu een stevige basis om te experimenteren met andere vormen, schaduwstijlen en exportopties.  

Volgende stap? Probeer de rechthoek te vervangen door een afgeronde‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}