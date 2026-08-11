---
category: general
date: 2026-08-10
description: Skapa Word-dokument programatiskt med Aspose.Words, lär dig hur du grupperar
  flera former i Word, lägger till en rektangel i Word och skapar en gruppform i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: sv
lastmod: 2026-08-10
og_description: Skapa Word‑dokument programatiskt med Aspose.Words. Den här guiden
  visar hur du grupperar flera former i Word, lägger till en rektangel i Word och
  bäddar in en ren‑textinnehållskontroll, allt i C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Skapa Word-dokument programatiskt – gruppera former i C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Skapa Word-dokument programatiskt och gruppera former i C#
url: /sv/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt och gruppera former i C#

Om du behöver **create word document programmatically**, den här handledningen visar hur du bygger en DOCX-fil med Aspose.Words och **group multiple shapes word** tillsammans. Vi kommer också att gå igenom **add rectangle to word** och **how to create group shape** som innehåller både en rektangel och en ellips, plus en plain‑text StructuredDocumentTag för användarinmatning.

Du får slutligen en färdig Word-fil som innehåller en grupperad rektangel‑ellips-form och en innehållskontroll där en användare kan skriva ett namn. Ingen manuell redigering i Word krävs efter att koden har körts.

## Vad du behöver

- .NET 6.0 eller senare (exemplet riktar sig mot .NET 6, men alla nyare .NET‑versioner fungerar)
- En Aspose.Words for .NET‑licens (gratis provversion fungerar för testning)
- Visual Studio 2022 eller någon C#‑IDE du föredrar
- Grundläggande kunskap om C#‑syntax

## Skapa Word-dokument programatiskt – övergripande arbetsflöde

Processen består av tre logiska faser:

1. **Initialize** ett `Document` och en `DocumentBuilder` – grunden för alla Word‑filer du genererar.
2. **Build a group shape** som innehåller en rektangel och en ellips – demonstrerar **group multiple shapes word** och **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – en plain‑text innehållskontroll som låter slutanvändare fylla i data, vilket illustrerar **add rectangle to word** som en del av det övergripande dokumentlayouten.

Nedan följer den kompletta, körbara koden följt av en steg‑för‑steg‑genomgång.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Steg 1 – Initiera dokumentet och byggaren
`Document`‑objektet representerar hela DOCX‑filen, medan `DocumentBuilder` erbjuder ett bekvämt API för att lägga till innehåll. Att initiera dem är det första kravet när du **create word document programmatically**.

> **Pro tip:** Om du planerar att återanvända samma dokument i flera operationer, behåll en enda `DocumentBuilder`‑instans för att undvika onödig objekt‑skapande.

### Steg 2 – Skapa en gruppform‑behållare
En `Shape` med `ShapeType.Group` fungerar som en duk som kan hålla andra former. Att sätta `Width` och `Height` definierar omgivningsrutan för gruppen. Detta är kärnan i **how to create group shape** i Aspose.Words.

> **Edge case:** Om gruppens bredd är mindre än den kombinerade bredden av dess barn, kommer barnen att beskäras. Se alltid till att gruppen är tillräckligt stor för att rymma varje barnform.

### Steg 3 – Lägg till en rektangel i Word
En rektangel skapas med `ShapeType.Rectangle`. Dess `Left`‑ och `Top`‑egenskaper placerar den relativt gruppens ursprung. Detta steg demonstrerar **add rectangle to word** och visar hur du kan kontrollera exakt placering.

> **Common mistake:** Att glömma att sätta `Left`/`Top` gör att rektangeln visas vid gruppens standardursprung (0,0), vilket kan överlappa andra barn.

### Steg 4 – Lägg till en ellips (cirkel) i gruppen
En ellips läggs till på samma sätt som rektangeln, men med `ShapeType.Ellipse`. `Left = 210` flyttar den till höger om rektangeln och skapar ett visuellt distinkt par former i samma grupp.

> **Why use a group?** Gruppering låter dig flytta, rotera eller ändra storlek på båda formerna tillsammans med en enda operation senare, vilket bevarar deras relativa layout.

### Steg 5 – Infoga den färdiga gruppformen i dokumentet
`builder.InsertNode(groupShape)` placerar hela gruppen vid den aktuella markörpositionen. Eftersom gruppen redan innehåller sina barn behöver du inga extra infognings‑anrop för rektangeln eller ellipsen.

### Steg 6 – Skapa en plain‑text StructuredDocumentTag (SDT)
En StructuredDocumentTag är en innehållskontroll som slutanvändare kan fylla i när dokumentet öppnas i Word. Att sätta `Title = "CustomerName"` ger kontrollen en meningsfull identifierare, vilket är användbart för senare dataextraktion.

> **Why a plain‑text SDT?** Den begränsar inmatning till plain text, vilket förhindrar oavsiktlig formatering som kan störa efterföljande bearbetning.

### Steg 7 – Spara dokumentet
`doc.Save("GroupAndSDT.docx")` skriver filen till disk. Den resulterande DOCX‑filen innehåller de grupperade formerna och SDT:n. När du öppnar filen i Microsoft Word visas en rektangel bredvid en cirkel, båda valbara som ett enda objekt, följt av en platshållare “Enter name here …”.

#### Förväntat resultat
- En fil med namnet **GroupAndSDT.docx** i körningsmappen.
- I Word: en grupperad form (rektangel + ellips) som du kan flytta som en enhet.
- Direkt under gruppen, en gråtonad innehållskontroll som uppmanar användaren att skriva ett namn.

## Ytterligare varianter och bästa praxis

### Använda olika formtyper
Du kan ersätta `ShapeType.Rectangle` eller `ShapeType.Ellipse` med någon annan `ShapeType` (t.ex. `ShapeType.Polygon`, `ShapeType.Line`). Gruppningslogiken förblir identisk.

### Ställa in fyllningsfärg och kanter
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Att lägga till fyllning och linje förbättrar den visuella distinktionen, särskilt när dokumentet delas med icke‑tekniska intressenter.

### Rotera hela gruppen
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Att rotera gruppen är mer effektivt än att rotera varje barn individuellt.

### Exportera till PDF
Om du behöver en PDF‑version, anropa helt enkelt:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Alla grupperade former och SDT:n (renderad som ett textfält) kommer att visas i PDF‑filen.

## Vanliga fallgropar och hur man undviker dem

| Symptom | Orsak | Lösning |
|---------|-------|--------|

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa tomt Word-dokument med skuggad rektangelform – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}