---
category: general
date: 2026-08-23
description: Lär dig hur du grupperar former i C# med Aspose.Words. Guiden täcker
  också hur du infogar en rektangelform och lägger till former i Word för komplexa
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: sv
lastmod: 2026-08-23
og_description: Hur man grupperar former i C# med Aspose.Words. Följ den här kompletta
  handledningen för att infoga en rektangel, lägga till former i Word och gruppera
  flera former på ett effektivt sätt.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Hur man grupperar former i C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Hur man grupperar former i C# med Aspose.Words
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i C# med Aspose.Words

Om du behöver **how to group shapes** i ett Word‑dokument programatiskt, visar den här handledningen de exakta stegen med Aspose.Words för .NET. Oavsett om du bygger en rapportgenerator, en mallmotor eller ett diagramverktyg, kommer du att lära dig hur du startar en grupp, infogar en rektangelform och lägger till shapes word‑level innehåll utan att lämna koden.

Du kommer också att se hur du **group multiple shapes** tillsammans, vilket är viktigt när du vill flytta, rotera eller formatera en samling objekt som en enda enhet. Exemplet nedan fungerar med den senaste Aspose.Words 24.x‑utgåvan och kräver endast .NET 6 eller senare.

## Förutsättningar

- .NET 6 SDK (eller någon .NET‑version som stöds av Aspose.Words)
- Visual Studio 2022 eller VS Code
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)
- Grundläggande kunskap om C# och Aspose.Words‑objektmodellen

> **Pro tip:** Använd den kostnadsfria evalueringslicensen från Aspose för att undvika vattenstämpelbegränsningar under testning.

## Så grupperar du former med Aspose.Words

Nedan är ett komplett, körbart program som demonstrerar **how to start group**, lägger till en rektangel och avslutar gruppen. Koden följer samma logiska flöde som kodsnutten du angav, men den lägger till kontext, felhantering och kommentarer för tydlighet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Varför varje steg är viktigt

| Steg | Syfte | Hur det relaterar till nyckelorden |
|------|-------|------------------------------------|
| **Skapa ett nytt tomt dokument** | Tillhandahåller en ren arbetsyta för formoperationer. | Förbereder för **add shapes word** senare. |
| **Initialize DocumentBuilder** | Buildern är det primära API‑et för att infoga objekt. | Behövs innan du kan **how to start group**. |
| **StartGroupShape** | Startar en logisk behållare; alla efterföljande former blir medlemmar i denna grupp. | Svarar direkt på **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Placera enskilda former i gruppen. Rektangel‑anropet uppfyller **insert rectangle shape**; textformen uppfyller **add shapes word**. | Demonstrerar **group multiple shapes**. |
| **EndGroupShape** | Avslutar gruppen så att du kan flytta eller formatera den som en enhet. | Fullbordar arbetsflödet **how to group shapes**. |

## Infoga en rektangel‑form – djupare genomgång

`InsertShape`‑metoden accepterar en `ShapeType`‑enum, bredd och höjd. För att **insert rectangle shape** med anpassad formatering kan du utöka exemplet:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** Formatering säkerställer att rektangeln framträder när gruppen senare flyttas. Det visar också att formegenskaper kan sättas *innan* gruppen stängs.

## Lägga till Word‑nivå‑former (add shapes word)

Om du behöver bädda in text direkt i en form—vanligtvis kallad “WordArt” eller “textlåda”—använd `ShapeType.TextPlainText`. Efter infogning kan du skriva text i formen med `DocumentBuilder.Writeln` eller genom att komma åt formens `TextBox`‑egenskap:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Det uppfyller nyckelordet **add shapes word** och visar hur text kan följa med gruppen.

## Gruppera flera former – praktiska scenarier

När du **group multiple shapes**, kan du behandla dem som ett enda objekt för positionering, rotation eller skalning. Till exempel, efter att gruppen har stängts kan du flytta hela gruppen:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Eller rotera gruppen:

```csharp
group.Rotation = 45; // degrees
```

Dessa operationer är endast möjliga eftersom formerna delar samma föräldragrupp.

## Hantera kantfall

1. **Nested groups** – Aspose.Words tillåter grupper inom grupper. För att skapa en nästlad grupp, anropa `StartGroupShape` igen innan du anropar `EndGroupShape` för den inre gruppen.  
2. **Empty groups** – Om du startar en grupp men aldrig infogar en form, kommer `EndGroupShape` fortfarande att skapa en tom behållare. Detta är ofarligt men kan öka filstorleken något.  
3. **Compatibility** – Den genererade DOCX‑filen fungerar med Word 2010 och senare. Äldre versioner kan ignorera grupperingens metadata, så testa alltid med den avsedda Word‑versionen.

## Fullständig källkod för referens

Spara följande som `Program.cs` i ett .NET‑konsolprojekt. Koden kompileras och körs utan ändringar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Förväntat resultat

När du öppnar `GroupedShapes.docx` i Microsoft Word visas:

- En ljus‑korall rektangel, en ellips och en textruta—alla visuellt bundna tillsammans.  
- Att markera någon del av gruppen markerar också hela gruppen (en enda omgivningsruta visas).  
- Att flytta eller rotera gruppen flyttar alla tre formerna tillsammans.

## Vanliga frågor

**Q: Kan jag gruppera former som redan finns i dokumentet?**  
A: Ja. Hämta de befintliga `Shape`‑objekten, anropa `builder.StartGroupShape()`, återinfoga dem med `builder.InsertShape(existingShape)`, och anropa sedan `EndGroupShape()`.

**Q: Påverkar gruppering den underliggande XML‑en?**  
A: Aspose.Words lägger till ett `<w:grpSp>`‑element som innehåller varje forms `<w:sp>`‑nod. Detta är fullt kompatibelt med Office Open XML‑specifikationen.

**Q: Vad händer om jag behöver avgruppera senare?**  
A: Det finns inget direkt “ungroup”-API, men du kan iterera genom gruppens barnformer (`group.GroupShape.Children`) och kopiera dem till dokumentkroppen.

## Nästa steg

Nu när du vet **how to group shapes**, kan du överväga att utforska dessa relaterade ämnen:

- **Apply complex formatting to grouped shapes** – lär dig hur du ställer in gradientfyllningar, skuggeffekter och linjestilar.  
- **Export grouped shapes as images** – använd `Shape.GetShapeRenderer().Save(...)` för att rasterisera en grupp.  
- **Create dynamic diagrams** – kombinera data‑driven positionering med gruppering för att automatiskt generera flödesscheman.

Var och en av dessa bygger på grunden som täcks här och hjälper dig skapa rikare, mer interaktiva Word‑dokument.

---

*Lycklig kodning! Om du fann den här guiden användbar, dela den med kollegor eller ge stjärna till repot som innehåller exempelprojektet.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}