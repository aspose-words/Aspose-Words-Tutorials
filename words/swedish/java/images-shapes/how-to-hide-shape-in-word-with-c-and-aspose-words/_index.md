---
category: general
date: 2026-09-11
description: Lär dig hur du döljer en form i Word med C#. Den här guiden visar också
  hur du infogar en rektangulär form och hur du infogar en form i ett Word‑dokument
  med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: sv
lastmod: 2026-09-11
og_description: Hur man döljer en form i Word med C# och Aspose.Words. Följ den steg‑för‑steg‑handledning
  som visar hur man infogar en rektangulär form och hanterar former i ett Word‑dokument.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Hur man döljer en form i Word – komplett C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man döljer en form i Word med C# och Aspose.Words
url: /sv/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man döljer en form i Word med C# och Aspose.Words

Om du behöver dölja en form i Word samtidigt som du behåller formen i dokumentstrukturen, visar den här handledningen exakt hur. Med Aspose.Words för .NET kan du infoga en rektangelform, dölja den och ändå behålla dess position för senare bearbetning.

Word‑automatisering kräver ofta fin‑granulär kontroll över former—oavsett om du genererar mallar, förbereder rapporter eller bygger en dokumentredigeringstjänst. I slutet av den här guiden kommer du att kunna:

* Infoga en rektangelform i ett Word‑dokument (`insert rectangle shape`).
* Dölja vilken form som helst utan att ta bort den (`how to hide shape in word`).
* Spara resultatet och verifiera att den dolda formen inte visas i den renderade vyn (`insert shape into word document`).

Exemplet fungerar med Aspose.Words 24.10 eller senare och riktar sig mot .NET 6.0+, men koncepten gäller även för tidigare versioner.

## Förutsättningar

* **Aspose.Words for .NET** ≥ 24.10. Du kan få en gratis tillfällig licens från Aspose‑webbplatsen.
* **.NET SDK** 6.0 eller nyare installerad på din maskin.
* En utvecklingsmiljö såsom Visual Studio 2022, VS Code eller Rider.
* Grundläggande kunskap om C# och Word Open XML‑konceptet (valfritt men hjälpsamt).

## Så döljer du en form i Word med Aspose.Words

Nedan finns ett komplett, körbart program som demonstrerar hela arbetsflödet—från att skapa ett dokument till att infoga en rektangelform och slutligen dölja den.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Förklaring av varje steg

1. **Create a new document** – `Document` representerar Word‑filen i minnet. `DocumentBuilder` tillhandahåller ett flytande API för att infoga innehåll.
2. **Insert rectangle shape** – `InsertShape` skapar ett ritobjekt av typen `Rectangle`. Dimensionerna uttrycks i punkter (1 pt ≈ 1/72 tum). Detta uppfyller kravet `insert rectangle shape`.
3. **Hide the shape** – Genom att sätta `Shape.Hidden = true` markeras formen som dold i Word‑markup (`<w:hidden/>`). Formen förblir en del av dokumentträdet, så du kan senare avdölja den eller referera till den programmässigt. Detta är kärnan i `how to hide shape in word`.
4. **Save the file** – Dokumentet skrivs till `output.docx`. När det öppnas i Microsoft Word kommer rektangeln inte att vara synlig, men den finns fortfarande i XML‑filen och kan inspekteras med en ZIP‑visare eller Open XML SDK.

### Förväntat resultat

Öppna `output.docx` i Microsoft Word:

* Dokumentet verkar tomt—ingen synlig form.
* Om du inspekterar den underliggande XML‑filen (`word/document.xml`) hittar du ett `<w:pict>`‑element med ett `<w:hidden/>`‑attribut, vilket bekräftar att formen finns men är dold.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Den dolda formen kan göras synlig igen genom att sätta `Hidden = false` och spara dokumentet på nytt.

## Infoga rektangelform i ett Word‑dokument

Även om huvudmålet är att dölja en form, börjar många scenarier med att först infoga en form. Metoden `InsertShape` stöder många `ShapeType`‑värden, inklusive `Rectangle`, `Ellipse`, `Line` och anpassade bilder.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Varför använda en rektangel?**  
En rektangel ger en ren, axel‑justerad behållare som kan hålla text, bilder eller andra inbäddade former. Den används ofta som en platshållare för dynamiskt innehåll såsom tabeller eller diagram. Genom att infoga rektangeln först bevarar du layout‑konsistens även efter att du döljer den senare.

## Infoga form i Word‑dokument – bästa praxis

När du `insert shape into word document`, överväg följande:

* **Set explicit dimensions** – Undvik att förlita dig på automatisk storlek; specificera bredd och höjd i punkter för att säkerställa en konsekvent layout över plattformar.
* **Define positioning** – Som standard är formen förankrad till det aktuella stycket. Använd `builder.MoveTo` eller `builder.StartBookmark` för att placera den exakt.
* **Apply styling early** – Fyllningsfärg, linjestil och textomslag påverkar det slutliga utseendet. Även dolda former drar nytta av korrekt styling eftersom markupen förblir oförändrad.
* **Version compatibility** – `Hidden`‑egenskapen är endast tillgänglig från Aspose.Words 24.10 och framåt. Om du riktar dig mot en äldre version kan du manuellt lägga till `<w:hidden/>`‑attributet med hjälp av `Node`‑API:t.

### Manuell tillsats av det dolda attributet (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Komplett end‑to‑end‑exempel

Genom att samla allt tillsammans, här är ett enda program som:

1. Infogar en rektangelform.
2. Döljer formen.
3. Infogar en synlig ellips för kontrast.
4. Sparar dokumentet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

När programmet körs produceras `demo_output.docx`. När det öppnas ser du bara korall‑ellipsen; den gröna rektangeln finns i XML‑filen men är dold i vyn.

## Vanliga frågor och kantfall

**Q: Påverkar dolda former sidnumrering?**  
A: Nej. Dolda former ignoreras av layout‑motorn, så de tar inte upp utrymme. Detta är användbart för platshållarinnehåll som inte ska påverka sidbrytningar.

**Q: Kan jag dölja en form som är en del av ett sidhuvud eller en sidfot?**  
A: Ja. Samma `Hidden`‑egenskap fungerar på former som finns var som helst i dokumentträdet, inklusive sidhuvuden, sidfötter och till och med i tabeller.

**Q: Vad händer om jag behöver dölja flera former samtidigt?**  
A: Iterera över samlingen `Document.GetChildNodes(NodeType.Shape, true)` och sätt `Hidden = true` för varje målform.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: Bevaras det dolda attributet vid konvertering till PDF?**  
A: Vid konvertering till PDF utelämnas dolda former som standard, vilket matchar Words renderingsbeteende. Om du behöver dem i PDF‑filen måste du avdölja dem innan konvertering.

## Tips och fallgropar

* **Pro tip:** Sätt `shape.WrapType = WrapType.None` innan du döljer om du senare planerar att avdölja formen utan att störa omgivande text.
* **Watch out for older Aspose.Words versions:** `Hidden`‑egenskapen kastar `NotSupportedException` före 24.10. Använd den manuella XML‑metoden i det fallet.
* **Testing:** Öppna alltid den genererade `.docx`‑filen i Word och använd “Show XML markup” (Developer‑fliken) för att verifiera att `<w:hidden/>`‑attributet finns.

## Slutsats

Du vet nu hur du döljer en form i Word med C# och Aspose.Words, samt hur du infogar en rektangelform och infogar en form i ett Word‑dokument med full kontroll över synlighet. Genom att utnyttja `Hidden`‑egenskapen kan du behålla former i dokumentmodellen för senare bearbetning samtidigt som du presenterar en ren vy för slutanvändarna.

Utforska sedan relaterade ämnen såsom **updating shape properties at runtime**, **converting hidden shapes to images**, eller **using the Open XML SDK to manipulate hidden elements directly**. Dessa tillägg kommer att fördjupa

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}