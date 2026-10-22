---
category: general
date: 2026-07-19
description: Gruppera former i Word med Aspose.Words. Lär dig hur du lägger till en
  rektangel, definierar en ellips och infogar en form i Word-dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: sv
lastmod: 2026-07-19
og_description: Gruppera former i Word med Aspose.Words. Behärska att lägga till rektangelform,
  definiera ellipsform och infoga former i Word-dokument.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Gruppera former i Word – Steg‑för‑steg C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Gruppera former i Word med Aspose.Words – Komplett C#‑guide
url: /sv/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group Shapes in Word – Complete C# Guide

Har du någonsin funderat på hur du **grupperar former i Word** utan att trassla med användargränssnittet? Du är inte ensam. Oavsett om du genererar kontrakt, flyers eller diagram programatiskt, kan det spara dig timmar av manuellt arbete att **lägga till rektangel‑form**, **definiera ellips‑form**, och sedan **gruppera former i Word**.

I den här handledningen går vi igenom ett verkligt exempel med **Aspose.Words for .NET**. När du är klar vet du exakt hur du **infogar form i Word**, kombinerar dem och skapar ett polerat dokument som du kan skicka till kunder eller teammedlemmar.

---

## What You’ll Need

Innan vi dyker ner, se till att du har följande:

- **Aspose.Words for .NET** (senaste versionen, t.ex. 24.9). Du kan hämta det från NuGet med `Install-Package Aspose.Words`.
- En .NET‑utvecklingsmiljö (Visual Studio 2022 eller VS Code med C#‑tillägget fungerar bra).
- Grundläggande kunskap om C#‑syntax – inget avancerat, bara de vanliga `using`‑satserna och objekt‑skapandet.

Det är allt. Inga extra bibliotek, ingen COM‑interop, bara ren hanterad kod.

---

## How to Group Shapes in Word Using Aspose.Words

Nedan följer en steg‑för‑steg‑genomgång som speglar den kod du redan har. Varje steg förklarar **varför** vi gör det, inte bara **vad** raden gör, så att du kan anpassa mönstret till vilken form du än vill.

### Step 1: Set Up the Document and Builder

Vi börjar med att skapa ett tomt `Document` och en `DocumentBuilder`. Buildern är vårt “penna” som låter oss infoga innehåll där vi behöver det.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why?** `Document`‑objektet representerar hela .docx‑filen, medan `DocumentBuilder` erbjuder ett bekvämt API för att infoga noder (som former) utan att behöva hantera det underliggande nodträdet.

### Step 2: Add Rectangle Shape (add rectangle shape)

Nu **lägger vi till rektangel‑form** i dokumentet. Vi sätter storlek, position och fyllningsfärg så att den sticker ut.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Du kan ändra `FillColor` till vilken `System.Drawing.Color` du föredrar. Detta är användbart när du behöver färgkodade sektioner i en rapport.

### Step 3: Define Ellipse Shape (define ellipse shape)

Därefter **definierar vi ellips‑form**. Notera den andra `ShapeType` och förskjutningen (`Left = 120`) så att ellipsen hamnar bredvid rektangeln.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Why this matters:** Genom att positionera former explicit styr du hur de ser ut innan du grupperar dem. Om du förlitar dig på automatisk layout kan gruppering bli felplacerad.

### Step 4: (Optional) Insert Individual Shapes for Preview

Om du vill se varje form innan gruppering kan du **infoga form i Word** var för sig. Detta steg är valfritt men praktiskt för felsökning.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Kommentera bort dessa två rader när du är säker på att formerna ser rätt ut; annars får du dubbla visuella element efter gruppering.

### Step 5: How to Group Shapes – Create a GroupShape

Här kommer kärnan i handledningen: **hur man grupperar former**. Vi skapar ett `GroupShape`, fäster vår rektangel och ellips, och bestämmer hur gruppen beter sig gentemot omgivande text.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explanation:** `GroupShape` är i princip en mini‑canvas som håller andra former. Genom att sätta `WrapType` till `Inline` flyttar hela gruppen som en enhet när du lägger till eller tar bort text.

### Step 6: Insert the Grouped Shape into the Document (insert shape into word)

Nu **infogar vi form i Word** – men den här gången är det den grupperade behållaren, inte de enskilda delarna.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **What happens under the hood?** Anropet `InsertNode` lägger till `GroupShape` i dokumentets nodsamling. Eftersom gruppen redan innehåller rektangeln och ellipsen visas de tillsammans som ett objekt.

### Step 7: Save the Document

Till sist skriver vi filen till disk. Du kan ändra sökvägen så den passar ditt projekt.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Result:** Öppna `GroupShape.docx` i Microsoft Word så ser du en ljusblå rektangel och en korallfärgad ellips som är låsta ihop. Att dra den ena flyttar den andra – exakt vad “group shapes in word” lovar.

---

## Visual Confirmation

Nedan är en mock‑up av hur de grupperade formerna ser ut i Word‑filen.  

![Skärmdump av grupperade former i ett Word‑dokument skapat med Aspose.Words](grouped_shapes_placeholder.png "gruppera former i Word")

*Alt‑texten i bilden innehåller huvudnyckelordet för tillgänglighet och SEO.*

---

## Common Questions & Edge Cases

### What if I need more than two shapes?

Fortsätt bara att anropa `groupShape.AppendChild(yourNewShape);` innan du infogar gruppen. API‑et har ingen gräns för antalet underordnade former.

### Can I rotate or resize the whole group?

Absolut. `GroupShape` ärver från `Shape`, så du kan sätta egenskaper som `RotationAngle`, `Width` eller `Height` på själva gruppen, och alla underordnade former följer med.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### How do I change the group’s background colour?

Använd `groupShape.FillColor`. Detta fyller den osynliga omgivningsrutan; det kan vara praktiskt för att markera.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Does this work with older Word formats (.doc)?

`Aspose.Words` kan också spara till `.doc` – byt bara filändelsen i `Save`. Dock stöds vissa avancerade formfunktioner (som gruppering) fullt ut endast i OOXML‑formatet `.docx`.

---

## Full Working Example

Kopiera‑klistra in följande block i en ny konsolapp för att se hela processen i aktion. Inga delar saknas; detta är ett **komplett, körbart exempel**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Expected output:** När du öppnar `GroupShape.docx` ser du ett enda grupperat objekt bestående av en ljusblå rektangel och en ljus‑korallfärgad ellips, perfekt placerade sida‑vid‑sida.

---

## Recap

Vi har precis gått igenom allt du behöver för att **gruppera former i Word** med Aspose.Words:

1. Skapa ett dokument och en builder.  
2. **Lägg till rektangel‑form** och **definiera ellips‑form** med explicita dimensioner.  
3. (Valfritt) **infoga form i Word** för en snabb förhandsgranskning.  
4. Använd `GroupShape` för **hur man grupperar former** – lägg till varje barn, sätt omslag och infoga.  
5. Spara filen och verifiera resultatet.

## What Should You Learn Next?

De följande handledningarna täcker närliggande ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}