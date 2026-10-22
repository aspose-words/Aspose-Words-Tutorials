---
category: general
date: 2026-08-04
description: Spara docx‑fil programatiskt samtidigt som du lägger till en rektangelform
  och grupperar former i Word. Lär dig att ange formens dimensioner och skapa en textruta
  programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: sv
lastmod: 2026-08-04
og_description: Spara docx-fil med C# genom att lägga till en rektangelform, gruppera
  former i Word, ange formens dimensioner och skapa en textruta programatiskt.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Spara docx-fil med grupperade former i Word – C# steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Spara docx-fil med grupperade former i Word med C#
url: /sv/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara docx-fil med grupperade former i Word med C#

Om du behöver **save docx file** som innehåller flera former arrangerade tillsammans, visar den här guiden hur du gör det med C#. Du kommer att lära dig hur du **add rectangle shape**, grupperar flera former i ett Word‑dokument, **set shape dimensions**, och **create textbox programmatically**. Lösningen fungerar med den senaste Aspose.Words for .NET och körs på .NET 6 eller senare.

Tutorialen går igenom varje steg, från projektuppsättning till det sista `doc.Save`‑anropet. I slutet har du ett återanvändbart kodsnutt som du kan klistra in i vilket konsol‑ eller ASP.NET‑projekt som helst. Inga externa skript eller manuell redigering av DOCX‑filen krävs.

## Förutsättningar

* .NET 6 SDK (eller nyare) installerat.
* En giltig licens för **Aspose.Words for .NET** (gratis provversion fungerar för testning).
* Visual Studio 2022, VS Code eller någon IDE som kan bygga .NET‑projekt.

Koden använder endast Aspose.Words‑namnrymden, så inga extra NuGet‑paket behövs.

## Spara docx-fil med grupperade former i Word

Kärnan i lösningen är att bygga en `GroupShape` som innehåller en rektangel och en textruta, sedan infoga gruppen i dokumentet och anropa `doc.Save`. Följande avsnitt delar upp processen i hanterbara delar.

### 1. Skapa ett nytt dokument och en builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta steg är viktigt* – Ett nytt `Document`‑objekt representerar en tom *.docx*-fil. `DocumentBuilder` tillhandahåller hög‑nivå‑metoder som `InsertNode`, som vi kommer att använda för att placera gruppformen.

### 2. Lägg till rektangel-form i en grupp

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Varför detta steg är viktigt* – **add rectangle shape**‑operationen visar hur man definierar ett visuellt element med exakt storlek och position. Rektangeln finns inuti `group`, så när gruppen flyttas senare flyttas rektangeln automatiskt.

### 3. Gruppera former i Word‑dokument

`GroupShape`‑klassen samlar flera ritobjekt. Gruppering är användbart när du vill behandla flera objekt som en enhet (t.ex. flytta, rotera eller kopiera dem tillsammans).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Varför vi grupperar* – Gruppering minskar layoutkomplexiteten. Istället för att placera varje form individuellt på sidan justerar du gruppens `Left`, `Top`, `Width` och `Height` en gång.

### 4. Ställ in formens dimensioner för exakt layout

Både gruppen och dess underordnade former behöver explicita dimensioner; annars använder Word standardstorlekar som kanske inte matchar din design.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Varför vi sätter dimensioner* – Precisa mått säkerställer att rektangeln och textrutan inte överlappar oavsiktligt och att den slutgiltiga **save docx file** matchar den avsedda layouten.

### 5. Skapa textruta programatiskt i gruppen

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Varför detta steg är viktigt* – **create textbox programmatically**‑segmentet visar hur man bäddar in rik text i en form. Genom att använda ett `Paragraph` och `Run` får du full kontroll över formatering senare.

### 6. Infoga gruppform och **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Varför detta sista steg är viktigt* – `InsertNode`‑anropet placerar de grupperade formerna exakt där builder‑markören befinner sig. `doc.Save`‑metoden utför **save docx file**‑operationen och skriver ett fullständigt Word‑dokument till disk.

> **Resultat:** När du öppnar *GroupShape.docx* i Microsoft Word visas en rektangel till vänster och en textruta till höger, båda låsta tillsammans i en enda grupp. Du kan flytta gruppen som en enhet, ändra storlek på den eller applicera ytterligare formatering.

## Fullt, körbart exempel

Kopiera koden nedan till ett nytt konsolprojekt (`dotnet new console`) och kör `dotnet run`. Programmet skapar `GroupShape.docx` i projektets utdata‑mapp.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Förväntad output

* En fil med namnet **GroupShape.docx** visas i utdata‑katalogen.
* När du öppnar filen visas en rektangulär form till vänster och en textruta som innehåller “Grouped text” till höger, båda låsta tillsammans.
* Att markera någon av formerna flyttar hela gruppen, vilket bekräftar att **group shapes word**‑funktionaliteten fungerar som avsett.

## Vanliga variationer och kantfall

| Situation | Rekommendation |
|-----------|----------------|
| Behöver mer än två former | Lägg till ytterligare `Shape`‑objekt till `group` innan du anropar `builder.InsertNode`. |
| Vill att gruppen ska visas på en specifik sida | Flytta builder‑markören med `builder.MoveToDocumentEnd()` eller `builder.MoveToPage(pageNumber)`. |
| Kräver olika enheter (t.ex. centimeter) | Använd `ConvertUtil.InchToPoint(1.0)` för att konvertera tum till punkter, den enhet som Word förväntar sig. |
| Vill att textrutan ska omsluta text | Ställ in `textBox.TextBoxWrap = TextBoxWrapType.Square` efter att textrutan skapats. |
| Arbetar med äldre .NET Framework‑versioner | Samma API fungerar med .NET Framework 4.7+, men se till att referera rätt Aspose.Words‑version. |

**Proffstips:** Ställ alltid in gruppens `Width` och `Height` *efter* att alla underordnade former har lagts till. Detta garanterar att gruppen helt omsluter sitt innehåll och förhindrar beskärning när dokumentet öppnas i Word.

## Slutsats

Du vet nu hur du **save docx file** samtidigt som du **add rectangle shape**, **group shapes word**, **set shape dimensions** och **create textbox programmatically** med Aspose.Words for .NET. Det kompletta exemplet visar ett rent, återanvändbart mönster som du kan anpassa till mer komplexa layouter, såsom diagram, bilder,

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}