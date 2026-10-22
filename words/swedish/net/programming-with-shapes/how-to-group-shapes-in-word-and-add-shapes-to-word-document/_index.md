---
category: general
date: 2026-08-07
description: Hur man grupperar former i Word med Aspose.Words och lägger till former
  i ett Word‑dokument med C#. Följ den här steg‑för‑steg‑guiden för ren, återanvändbar
  kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: sv
lastmod: 2026-08-07
og_description: Hur man grupperar former i Word med Aspose.Words för .NET. Denna handledning
  visar hur du lägger till former i ett Word-dokument, grupperar dem och sparar filen
  med tydlig C#‑kod.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Hur man grupperar former i Word – snabb C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hur man grupperar former i Word och lägger till former i ett Word‑dokument
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word och lägger till former i Word‑dokument

Om du behöver **hur man grupperar former i Word**, så guidar den här artikeln dig genom hela processen med Aspose.Words för .NET. Du kommer också att lära dig **lägga till former i Word‑dokument** med några få rader C#‑kod, så att resultatet är redo för alla rapporterings‑ eller mallningsscenarier.

Handledningen täcker allt du behöver: nödvändiga NuGet‑paket, en komplett källfil och en förklaring av varför varje steg är viktigt. När du är klar kan du generera en DOCX som innehåller en rektangel och en ellips sammanslagna till en enda gruppform.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon IDE som stödjer .NET)  
* Aspose.Words för .NET NuGet‑paket (`Aspose.Words`) – den kostnadsfria provversionen fungerar för testning, men en licens tar bort utvärderingsvattenstämplar  

Dessa objekt är de enda externa beroendena för **lägga till former i Word‑dokument**.

## Hur man grupperar former i Word

Kärnan i lösningen är att skapa enskilda former, placera dem på sidan och sedan omsluta dem i en `GroupShape`. Följande steg speglar den logiska ordningen i koden.

### Steg 1: Skapa ett dokument och en builder

Ett `Document`‑objekt representerar hela DOCX‑filen. `DocumentBuilder` tillhandahåller ett bekvämt API för att redigera dokumentet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: `Document` är behållaren för alla Word‑element. `DocumentBuilder` håller reda på den aktuella markörpositionen, vilket krävs när du senare infogar den grupperade formen.

### Steg 2: Lägg till rektangelformen

En rektangel skapas genom att ange `ShapeType.Rectangle`. Bredd, höjd och placering anges i punkter (1 pt ≈ 1/72 tum).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Varför detta är viktigt*: Att sätta `StrokeColor` gör formen synlig när dokumentet öppnas. Du kan också fylla formen med `FillColor` om ett solid inre krävs.

### Steg 3: Lägg till ellipsformen

Ellipsen använder `ShapeType.Ellipse`. Dess storlek och position är oberoende av rektangeln, vilket låter dig styra den slutliga layouten av gruppen.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Varför detta är viktigt*: Genom att placera ellipsen på `Left = 120` överlappar den inte rektangeln, vilket gör gruppen visuellt distinkt.

### Steg 4: Gruppera de två formerna

`GroupShape` fungerar som en behållare som behandlar sina barn som ett enda objekt. Detta är den väsentliga operationen för **hur man grupperar former i Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Varför detta är viktigt*: Gruppering gör att du kan flytta, ändra storlek eller rotera båda formerna tillsammans. Alla transformationer som appliceras på `groupShape` propageras till dess barn.

### Steg 5: Infoga den grupperade formen i dokumentet

`DocumentBuilder.InsertNode` placerar `GroupShape` på den aktuella markörpositionen. Eftersom vi inte har flyttat buildern visas gruppen i början av den första sidan.

```csharp
builder.InsertNode(groupShape);
```

*Varför detta är viktigt*: Att infoga noden direkt undviker behovet av ett separat stycke eller en tabellcell. Gruppen blir en del av dokumentflödet.

### Steg 6: Spara dokumentet

Till sist skriv DOCX‑filen till disk. Använd en fullständig sökväg som ditt program har skrivbehörighet till.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Varför detta är viktigt*: `doc.Save` slutför alla ändringar. Den resulterande filen kan öppnas i Microsoft Word, LibreOffice eller någon annan visare som stödjer DOCX.

## Komplett källfil

Kopiera koden nedan till ett nytt konsolprojekt (`dotnet new console`) och kör det. Programmet skapar en fil med namnet `GroupShape.docx` som innehåller en grupperad rektangel och ellips.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Förväntat resultat

Öppna `GroupShape.docx`. Du kommer att se ett enda visuellt objekt som innehåller en blå rektangel till vänster och en grön ellips till höger. När du markerar objektet i Word markeras båda formerna samtidigt – ett bevis på att **hur man grupperar former i Word** lyckades.

## Vanliga frågor och kantfall

* **Kan jag lägga till fler än två former?**  
  Ja. Anropa `groupShape.AppendChild` för varje ytterligare `Shape` innan du infogar gruppen.

* **Vad händer om jag behöver rotera gruppen?**  
  Sätt `groupShape.RotationAngle = 45;` (vinkel i grader) efter att gruppen har byggts.

* **Behöver jag anropa `doc.UpdatePageLayout()`?**  
  Nej för detta scenario. Layouten uppdateras automatiskt när dokumentet sparas.

* **Hur påverkar licensieringen koden?**  
  Med en giltig Aspose.Words‑licens (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) innehåller det genererade dokumentet ingen utvärderingsvattenstämpel.

## Slutsats

Du vet nu **hur man grupperar former i Word** och **lägger till former i Word‑dokument** med Aspose.Words för .NET. Handledningen gick igenom att skapa ett dokument, definiera enskilda former, gruppera dem, infoga gruppen och spara filen.  

Från och med nu kan du experimentera med:

* Lägga till textrutor eller bilder i gruppen  
* Ändra fyllningsfärger, linjestilar eller skuggeffekter  
* Gruppera former i tabeller eller sidhuvuden  

Dessa utökningar låter dig bygga sofistikerade Word‑mallar programatiskt samtidigt som koden förblir ren och underhållbar. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}