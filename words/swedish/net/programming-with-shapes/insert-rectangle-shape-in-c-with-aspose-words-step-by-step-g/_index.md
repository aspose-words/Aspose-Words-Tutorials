---
category: general
date: 2026-08-07
description: Infoga rektangelform i C# med Aspose.Words och lär dig hur du döljer
  formen, anger fyllningsfärg och lägger till rektangelformen i ett Word‑dokument
  på ett effektivt sätt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: sv
lastmod: 2026-08-07
og_description: Infoga rektangelform i ett Word‑dokument med C#. Lär dig hur du döljer
  formen, anger fyllningsfärg och lägger till rektangelformen med Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Infoga rektangel‑form i C# – komplett Aspose.Words‑handledning
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Infoga rektangel‑form i C# med Aspose.Words – steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga rektangelform i C# med Aspose.Words – steg‑för‑steg guide

Om du behöver **infoga rektangelform** i ett Word‑dokument från C#, visar den här guiden exakt hur du gör det. Du kommer att se hur du anger fyllningsfärgen, döljer formen så att den inte visas i den slutliga layouten, och sparar filen—allt med bara några rader kod.

I de följande avsnitten täcker vi allt du behöver veta: förutsättningar, den kompletta kodlistan, förklaringar för varje steg, och tips för vanliga variationer såsom att göra formen synlig igen eller använda en annan färg. I slutet kommer du att kunna **lägga till rektangelform** i vilken .docx‑fil som helst programatiskt.

## Förutsättningar

* **Aspose.Words for .NET** (version 23.10 eller senare). Du kan installera det via NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK eller senare installerat på din maskin.
* En grundläggande förståelse för C# och Visual Studio (eller någon IDE du föredrar).

Inga ytterligare bibliotek krävs—API:erna för former är en del av kärnpaketet Aspose.Words.

## Infoga rektangelform med Aspose.Words

Kärnan i lösningen är ett kort, självständigt program som skapar ett tomt dokument, infogar en rektangel, färgar den, döljer den och sedan sparar filen. Nedan finns hela källkoden med inline‑kommentarer som förklarar *varför* bakom varje rad.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Vad varje steg gör

| Steg | Orsak |
|------|--------|
| **Create a new document** | Ger en ren arbetsyta; du kan också ladda ett befintligt .docx genom att skicka en filsökväg till `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` är den hög‑nivå hjälparen som låter dig infoga text, tabeller och former utan att behöva hantera lågnivå nodträd. |
| **Insert rectangle shape** | `InsertShape`‑metoden returnerar ett `Shape`‑objekt som du kan anpassa ytterligare (storlek, position, kantlinjer osv.). |
| **Set fill color** | `FillColor`‑egenskapen styr den inre färgen; du kan använda vilket `Color`‑värde som helst (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, osv.). |
| **Hide the shape** | `Hidden = true` instruerar Word att ignorera formen under layouten samtidigt som den behålls i dokumentets XML. Detta är det vanliga sättet att lagra osynliga objekt. |
| **Save the document** | Sparar ändringarna till en .docx‑fil. Den sparade filen kommer att innehålla den dolda rektangelformen. |

## Hur man anger fyllningsfärg för en form

Att ändra fyllningsfärgen är så enkelt som att tilldela ett `System.Drawing.Color` till `FillColor`‑egenskapen. Om du behöver en anpassad nyans, använd `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Varför detta är viktigt*: Fyllningsfärgen lagras i formens XML (`<w:fill>`‑attribut). När formen är dold finns färgen fortfarande kvar, vilket kan vara användbart för efterföljande bearbetning (t.ex. extrahera metadata baserat på färgkoder).

## Hur man döljer en form i det slutliga dokumentet

`Hidden`‑flaggan är en boolesk egenskap på `Shape`‑klassen. Att sätta den till `true` säkerställer att formen ignoreras av Word‑layoutmotorn.

```csharp
rectangleShape.Hidden = true;
```

**Vanliga fallgropar**

* **Hidden vs. Visible** – Om du senare behöver att formen ska visas, sätt helt enkelt `Hidden = false`.
* **Compatibility** – Äldre versioner av Word (före 2007) kan hantera dolda ritobjekt annorlunda. Aspose.Words upprätthåller kompatibilitet genom att lagra flaggan i rätt OOXML‑element.

## Hur man infogar en form programatiskt

Även om exemplet använder en rektangel, fungerar samma `InsertShape`‑metod för många andra former (ellips, triangel, linje osv.). Det första argumentet är ett `ShapeType`‑enum‑värde:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tips**: Om du behöver placera formen på en specifik plats på sidan, använd `builder.MoveTo` för att sätta infogningspunkten innan du anropar `InsertShape`.

## Lägg till rektangelform i ett befintligt dokument

Ofta kommer du att förbättra en mall snarare än att börja från början. Ersätt steg 1 med:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Alla efterföljande steg förblir identiska, och rektangeln kommer att läggas till där byggarens markör är placerad (vanligtvis i slutet av dokumentet som standard).

## Hantera kantfall och variationer

### 1. Göra formen synlig igen

Om en senare del av ditt arbetsflöde behöver visa den dolda rektangeln, kan du växla flaggan:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Lägga till en kantlinje (stroke)

En dold form kan fortfarande ha en synlig kantlinje när du bestämmer dig för att visa den. Ställ in egenskaperna `LineColor` och `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Positionera rektangeln absolut

För exakt layoutkontroll, byt formens `WrapType` till `WrapType.Inline` (standard) eller `WrapType.TopBottom` och justera `Left`/`Top`‑egenskaperna:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Använda en annan måttenhet

Aspose.Words arbetar i punkter (1 pt = 1/72 tum). Om du föredrar centimeter, konvertera först:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Komplett körbart exempel

Nedan är det *fullständiga* programmet som du kan kopiera, klistra in och köra. Det inkluderar alla nödvändiga `using`‑direktiv och använder absoluta sökvägar som du bör justera för din miljö.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntat resultat**: Filen `HiddenRectangleShape.docx` öppnas i Microsoft Word utan *synlig form*, men den dolda rektangeln finns i dokumentets XML. Du kan verifiera dess existens genom att öppna .docx‑filen som ett zip‑arkiv och inspektera `word/document.xml` för ett `<w:shape>`‑element med attributen `w:fill="yellow"` och `w:hidden="true"`.

## Slutsats

Du vet nu hur du **infogar rektangelform** i ett Word‑dokument med C# och Aspose.Words, hur du **anger fyllningsfärg**, och hur du **döljer formen** så att den förblir osynlig i den slutliga layouten. Samma mönster fungerar för andra formtyper, anpassade färger och befintliga mallar. Experimentera med kantlinjer, absolut positionering och olika måttenheter för att anpassa formen efter dina exakta krav.

### Nästa steg

* Utforska **how to insert shape** i tabeller eller sidhuvuden/sidfötter för vattenstämplar.
* Kombinera **add rectangle shape** med innehållskontroller för att skapa dynamiska platshållare.
* Granska Aspose.Words’ **shape manipulation** API för avancerade funktioner som rotation, gradientfyllningar och SVG‑import.

Känn dig fri att anpassa koden till ditt eget projekt, och låt oss veta i kommentarerna vilken formrelaterad utmaning du löste härnäst!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}