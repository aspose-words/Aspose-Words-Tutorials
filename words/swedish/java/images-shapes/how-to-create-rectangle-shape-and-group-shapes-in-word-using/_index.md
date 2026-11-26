---
category: general
date: 2026-11-18
description: Lär dig hur du skapar en rektangelform i ett Word‑dokument med C#. Guiden
  täcker också hur du ställer in formens storlek, formens position och grupperar former
  i Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: sv
lastmod: 2026-11-18
og_description: Skapa en rektangelform i en Word‑fil med C# och lär dig att ange formens
  dimensioner, placera formen och gruppera former i Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Skapa rektangelform och gruppera former i Word med C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man skapar rektangelform och grupperar former i Word med C#
url: /sv/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar rektangelform och grupperar former i Word med C#

Om du behöver **skapa rektangelform** i ett Word‑dokument visar den här handledningen en komplett, färdig‑att‑köra‑lösning. Du kommer att se hur du ställer in formens storlek, formens position och grupperar former i Word så att de beter sig som ett enda objekt.

Att arbeta med former är ett vanligt krav när man genererar rapporter, fakturor eller diagram programatiskt. I slutet av den här guiden kommer du att kunna generera en `.docx`‑fil som innehåller en rektangel, en ellips och en grupperad behållare – allt skapat med Aspose.Words för .NET.

## Förutsättningar

- .NET 6.0 SDK eller senare (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)
- En kodredigerare eller IDE (Visual Studio, VS Code, Rider, etc.)

Inga ytterligare bibliotek krävs.

## Hur man skapar rektangelform och grupperar former i Word

De grundläggande stegen är:

1. **Skapa ett tomt dokument** och en `DocumentBuilder`.
2. **Infoga en `GroupShape`** som kommer att hålla de enskilda formerna.
3. **Skapa en rektangelform**, ange dess dimensioner och lägg till den i gruppen.
4. **Skapa en ellipsform**, ange dess storlek och position och lägg till den i gruppen.
5. **Spara** dokumentet.

Varje steg förklaras nedan, och den kompletta källkoden följer förklaringen.

### Steg 1: Initiera dokumentet och byggaren

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela Word‑filen, medan `DocumentBuilder` tillhandahåller ett flytande API för att infoga innehåll. Att initiera dem är obligatoriskt innan du kan lägga till några former.

### Steg 2: Infoga en gruppform

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

En `GroupShape` fungerar som en behållare; alla underordnade former rör sig tillsammans. Detta är det rekommenderade sättet att **gruppera former i Word** när du behöver gemensamma transformationer (t.ex. flytta, rotera eller radera).

### Steg 3: Skapa rektangeln och ange dess storlek

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Här **skapar vi en rektangelform** och **anger formens storlek** genom att tilldela `Width` och `Height`. I Aspose.Words uttrycks storlekar i punkter (1 pt ≈ 1/72 tum). Att ange dimensionerna explicit säkerställer att rektangeln visas exakt som avsett.

### Steg 4: Skapa ellipsen, ange dimensioner och placera den

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**Ange formens dimensioner** för ellipsen är identiska för bredd och höjd, vilket ger en perfekt cirkel. `Left`‑egenskapen visar **ange formens position**: ellipsen börjar 120 pt till höger om gruppens ursprung, så den överlappar inte rektangeln.

### Steg 5: Spara dokumentet

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Spara skriver Word‑filen till disk. Du kan öppna `GroupShape.docx` i Microsoft Word för att verifiera att rektangeln och ellipsen är grupperade och placerade korrekt.

## Ställa in formens dimensioner och storlek – djupare titt

- **Punkter vs. tum**: 72 pt = 1 in. Om du föredrar tum, multiplicera med 72 (t.ex. `2.5 * 72` för 2,5 in).
- **Automatisk skalning**: Om du utelämnar `Width` eller `Height` använder formen sin standardstorlek. Ange explicit **formens storlek** för att undvika oväntade layoutresultat.
- **Bildförhållande**: För former som `Ellipse` behåller du `Width` och `Height` lika för att upprätthålla en cirkulär framtoning.

## Positionering av en form i Word

`Left`‑ och `Top`‑egenskaperna styr formens förskjutning inom sin behållare (gruppen eller sidan). Positiva värden flyttar formen åt höger/nedåt; negativa värden flyttar den åt vänster/upp. Vid gruppering är positionerna relativa till gruppens ursprung, vilket förenklar layoutberäkningar.

## Gruppera former i Word med Aspose.Words

Gruppering är avgörande när du vill att flera former ska fungera som en enhet. `GroupShape`‑objektet:

- Stöder `AppendChild` för att lägga till vilken `Shape` som helst (rektangel, ellips, bild, etc.).
- Gör det möjligt att flytta, rotera eller radera hela gruppen med ett enda anrop.
- Behåller underordnade formers positioner relativt till gruppen, vilket gör komplexa diagram enklare att hantera.

**Proffstips:** Efter att ha lagt till alla underordnade former kan du justera gruppens `Width`, `Height`, `Left` och `Top` för att omplacera hela samlingen i ett steg.

## Komplett körbart exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra. Det innehåller alla `using`‑direktiv, en `Main`‑metod och kommentarer som förklarar varje rad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Förväntat resultat:** Efter att programmet har körts visas `GroupShape.docx` i körningsmappen. När du öppnar den i Word visas en rektangel (100 pt × 50 pt) till vänster och en ellips (80 pt × 80 pt) placerad 120 pt till höger, båda inom ett enda grupperat objekt.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Skärmdump av ett Word‑dokument som visar en grupperad rektangel och ellipsform skapad med C#" }

*Bilden ovan illustrerar det slutgiltiga resultatet; rektangeln och ellipsen kan väljas som en grupp.*

## Vanliga frågor och specialfall

| Fråga | Svar |
|-------|------|
| **Kan jag lägga till fler än två former?** | Ja. Anropa `group.AppendChild(yourShape)` för varje ytterligare form. |
| **Vad händer om jag behöver rotera gruppen?** | Använd `group.RotationAngle = 45;` (grader) efter att ha lagt till alla underordnade. |
| **Hur ändrar jag gruppens bakgrundsfärg?** | Ställ in `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Fungerar detta med .doc‑filer?** | Aspose.Words stöder `.doc` och `.docx`. Samma kod fungerar; ändra bara filändelsen i `Save`. |
| **Finns det någon minnespåverkan när man grupperar många former?** | Gruppering i sig tillför minimal overhead. Huvudproblemet är det totala antalet former; håll det rimligt för stora dokument. |

## Slutsats

I den här handledningen lärde du dig hur man **skapar rektangelform** i en Word‑fil med C#, hur man **anger formens storlek**, **anger formens dimensioner**, **anger formens position**, och slutligen hur man **grupperar former i Word** med Aspose.Words. Det kompletta exemplet visar ett rent, underhållbart tillvägagångssätt som du kan utöka till mer komplexa diagram, grafer eller anpassade grafik.

Därefter kan du utforska:

- Lägga till text i former (`Shape.TextPath.Text = "Hello"`).
- Infoga bilder i en `GroupShape`.
- Exportera de grupperade formerna till PDF med `doc.Save("output.pdf")`.

Känn dig fri att experimentera med olika storlekar, positioner och ytterligare formtyper för att passa ditt projekts behov. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar rektangelform och grupperar former i Word med Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}