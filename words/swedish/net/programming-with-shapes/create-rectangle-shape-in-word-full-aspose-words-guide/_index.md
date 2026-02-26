---
category: general
date: 2026-02-26
description: Skapa en rektangel i Word med Aspose.Words och lär dig hur du lägger
  till en form i Word, applicerar skugga på formen och ställer in formens transparens
  på några minuter.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: sv
og_description: Skapa en rektangulär form i Word med Aspose.Words. Lär dig att lägga
  till en form i Word, applicera skugga på formen och snabbt ställa in formens transparens.
og_title: Skapa rektangelform i Word – Fullständig Aspose.Words‑guide
tags:
- Aspose.Words
- C#
- Word Automation
title: Skapa rektangelform i Word – Fullständig Aspose.Words‑guide
url: /sv/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

headings, paragraphs, list items, table headers? Table headers are property names, keep as is. The column "What It Controls" maybe translate? But it's a header in table; it's text. Should translate to Swedish: "Vad den styr". "Typical Values" -> "Typiska värden". Keep property names unchanged.

Also code block placeholders remain unchanged.

We need to translate bullet points, etc.

Let's produce final content.

Be careful with markdown links: none present except maybe none. There are no links.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangel‑form i Word – Fullständig Aspose.Words‑guide

Har du någonsin behövt **skapa rektangel‑form** i ett Word‑dokument men inte vetat var du ska börja? Du är inte ensam – många utvecklare stöter på samma hinder när de automatiserar rapporter eller fakturor. I den här handledningen går vi igenom ett komplett, färdigt exempel som visar hur du **lägger till form i Word**, applicerar en subtil skugga och styr formens transparens, allt med Aspose.Words för .NET.

När du är klar med guiden har du en `.docx`‑fil som innehåller en ren rektangel med en polerad skugga – perfekt för varumärkesprofilering, call‑outs eller bara för att göra ditt dokument lite mer professionellt. Inga externa verktyg behövs, bara några rader C#.

## Vad du behöver

- **Aspose.Words for .NET** (senaste versionen i början av 2026). Du kan hämta den från NuGet (`Install-Package Aspose.Words`).
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code med C#‑tillägget).
- Grundläggande kunskap om C#‑syntax – inget avancerat, bara vanliga `using`‑satser och objekt‑skapande.

Om du redan har detta, bra – låt oss sätta igång.

## Skapa rektangel‑form – huvudsteg

Nedan är hela källkoden. Kopiera‑klistra in den i ett nytt konsolprojekt, tryck **F5**, så kommer `ShadowDemo.docx` att dyka upp i den mapp du anger.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Varför detta fungerar

- **`Document`** är ingångspunkten; den representerar hela Word‑filen.
- **`Shape`** med `ShapeType.Rectangle` talar om för Aspose att vi vill ha ett rektangulärt ritobjekt.
- Att sätta **`Width`** och **`Height`** ger formen en bestämd storlek; annars blir den en liten platshållare.
- **`Shadow`**‑objektet låter oss finjustera varje visuellt aspekt: oskärpa, avstånd, riktning, färg, transparens och spridning. Det är kärnan i *apply shadow to shape*.
- Slutligen injicerar **`AppendChild`** formen i dokumentets första stycke, vilket är det enklaste sättet att *add shape to Word* utan att behöva hantera tabeller eller sidhuvuden.

När du öppnar `ShadowDemo.docx` ser du en grå rektangel som sitter bekvämt i dokumentet, med en skugga som lutar ner‑höger i en 45°‑vinkel. Skuggan är inte ett massivt block; oskärporaden mjukar upp kanterna och transparensen får den att se ut som en naturlig drop‑shadow snarare än en hård överlagring.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(Bilden ovan visar slutresultatet av kodsnutten.)*

## Lägg till form i Word‑dokument – placeringsalternativ

Exemplet använder **första stycket** eftersom det är det snabbaste sättet att se något på skärmen. I verkliga scenarier kan du vilja:

- Infoga formen i ett specifikt **section** eller **header/footer**.
- Placera den i en **table cell** för justering med tabulär data.
- Omge den med **text wrapping**‑alternativ (t.ex. `WrapType.Square`) så att omgivande text flyter runt rektangeln.

Här är en snabb variant som placerar formen i ett nytt stycke med en anpassad stil:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Proffstips:* Lägg alltid till formen **efter** att du har konfigurerat dess egenskaper; annars kan du behöva anropa `UpdateLayout` för att uppdatera det visuella utseendet.

## Applicera skugga på formen – finjustera utseendet

Skuggor kan dramatiskt förändra ett dokuments estetik. Klassen `Shadow` exponerar flera egenskaper:

| Property      | What It Controls                                   | Typical Values |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | Softness of the shadow edges                      | 2.0 – 10.0      |
| `Distance`    | How far the shadow is offset from the shape        | 1.0 – 8.0       |
| `Direction`   | Angle in degrees (0 = left, 90 = up)              | 0 – 360         |
| `Color`       | Shadow colour (any `System.Drawing.Color`)        | Gray, Black, Custom |
| `Transparency`| Opacity (0 = fully opaque, 1 = invisible)        | 0.0 – 0.5       |
| `Spread`      | Expansion of the shadow before blur is applied    | 0.0 – 1.0       |

Om du vill ha ett **diskret, professionellt utseende**, håll `BlurRadius` runt 4‑6 och `Transparency` nära 0.2, precis som i koden ovan. För en **dramatiskt effekt**, öka `Distance` till 6, sätt `Direction` till 135°, och sänk `Transparency` till 0.05.

## Ställ in formens transparens och skuggspridning

Transparens handlar inte bara om skuggan; du kan också göra själva rektangeln delvis genomskinlig:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Att kombinera en halvtransparent fyllning med en mjuk skugga ger ofta en modern UI‑känsla – utmärkt för dashboards eller design‑mock‑ups som är inbäddade i rapporter.

### Edge Cases to Watch

1. **Older Word versions** (pre‑2007) don’t support some shadow properties. If you target `.doc` files, consider simplifying the shadow (e.g., set `BlurRadius` to 0).
2. **High DPI displays** may render the shadow slightly differently. Test on the target environment if visual fidelity is critical.
3. **Overlapping shapes**—Aspose renders shadows in the order they’re added. Insert shapes from back to front to avoid unwanted occlusion.

## Spara och verifiera resultatet

Metoden `Document.Save` upptäcker automatiskt utdataformatet från filändelsen. För en **`.docx`**‑fil får du Open XML‑formatet, som de flesta moderna Word‑program förstår. Om du behöver en **PDF**‑version med samma visuella stil, byt bara filändelsen:

```csharp
document.Save("ShadowDemo.pdf");
```

När du öppnar den genererade `ShadowDemo.docx` (eller `ShadowDemo.pdf`) bör du se en ren **rektangel med skugga**, vilket bekräftar att du framgångsrikt har *create rectangle shape* och *apply shadow to shape* med Aspose.Words.

## Vanliga frågor

**Q: Kan jag använda en annan form, som en ellips?**  
A: Absolut. Byt `ShapeType.Rectangle` mot `ShapeType.Ellipse` (eller någon annan `ShapeType`‑enum). Skugg‑egenskaperna förblir desamma.

**Q: Vad händer om jag vill att rektangeln ska vara klickbar?**  
A: Du kan tilldela en hyperlänk till formen:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Fungerar detta på .NET 6+?**  
A: Ja. Aspose.Words 23.11 och senare stödjer fullt ut .NET 6, .NET 7 och .NET 8. Referera bara till rätt NuGet‑paket.

**Q: Hur ändrar jag skugg‑färgen så den matchar mitt varumärke?**  
A: Använd vilken `System.Drawing.Color` du vill:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Sammanfattning

Vi har gått igenom allt du behöver för att **create rectangle shape** i ett Word‑dokument, **add shape to Word**, **apply shadow to shape** och **set shape transparency**. Den kompletta, körbara koden finns högst upp på sidan, och förklaringarna bör ge dig tillräckligt självförtroende för att justera storlekar, färger och skugg‑parametrar för vilket projekt som helst.

Redo för nästa steg? Prova att experimentera med:

- Flera former lagerade tillsammans för en badge‑effekt.
- Dynamisk storlek baserad på dokumentinnehåll (t.ex. beräkna bredd från en tabellkolumn).
- Exportera dokumentet till PDF eller HTML samtidigt som du bevarar skuggan.

Känn dig fri att lämna en kommentar om du stöter på problem, eller dela dina egna varianter på temat “rektangel med skugga”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}