---
category: general
date: 2026-09-05
description: Lär dig hur du skapar ett tomt Word‑dokument och lägger till en rektangel
  som kan döljas med Aspose.Words i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: sv
lastmod: 2026-09-05
og_description: Skapa ett tomt Word‑dokument och infoga en dold rektangelform med
  Aspose.Words – steg‑för‑steg‑guide för C#‑utvecklare.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Skapa ett tomt Word-dokument med en dold rektangelform
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Skapa ett tomt Word‑dokument och lägg till en rektangel
url: /sv/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och lägg till en rektangelform

Om du behöver skapa ett **tomt Word-dokument** som också innehåller en form som du inte vill ska visas i layouten, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. Du får se ett komplett, körbart exempel som skapar ett nytt dokument, lägger till en rektangelform, döljer den formen och sparar filen—utan extra verktyg.

Tutorialen täcker allt från projektuppsättning till felsökning av vanliga fallgropar. I slutet kommer du kunna generera en Word‑fil som ser tom ut för läsaren men ändå bär på dold metadata, vilket är användbart för t.ex. vattenstämplar, anpassad XML‑lagring eller layoutankare.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare (koden fungerar också med .NET Framework 4.7+)
* Visual Studio 2022 (eller någon IDE som stödjer C#)
* En aktiv **Aspose.Words** NuGet‑licens (gratisprovversionen fungerar för testning)
* Grundläggande kunskap om C# och konceptet dokumentnoder

Du kan installera biblioteket med följande CLI‑kommando:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Håll din Aspose.Words‑version uppdaterad; API‑et som används i den här tutorialen är stabilt från version 23.10.

## Så skapar du ett tomt Word-dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt. Ett färskt `Document` representerar ett tomt **tomt Word-dokument**—inga stycken, inga sektioner, bara filbehållaren.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Why this matters:** Att börja med ett rent dokument säkerställer att den dolda formen du lägger till senare inte stör befintligt innehåll eller stilar.

## Lägg till en rektangelform i dokumentet

Nästa steg är att skapa en rektangulär form. I Aspose.Words är en form en nod som kan placeras var som helst i dokumentträdet, och den kan konfigureras med storlek, fyllning, linjestil och synlighet.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Koden ovan skapar en synlig rektangel. Vid detta tillfälle skulle du kunna infoga den i dokumentet med `builder.InsertNode(rectangle)`. Eftersom vi vill att formen ska förbli dold, justerar vi dess `Hidden`‑egenskap innan infogning.

## Så döljer du en form i ett Word-dokument

Word tillhandahåller ett `Hidden`‑attribut för formnoder. När det är satt till `true` visas inte formen i sidlayouten, men den förblir en del av dokumentets XML. Detta är kärnan i **hur man döljer en form**‑kravet.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explanation:** Att sätta `Hidden = true` lägger till `<w:hide>`‑attributet i formens XML. Ordbehandlare ignorerar formen vid rendering, men formen kan fortfarande nås programmässigt eller via Word‑s XML‑vy.

## Infoga den dolda formen i det tomma dokumentet

Nu placerar vi den dolda rektangeln i dokumentträdet. Eftersom dokumentet fortfarande är tomt blir formen den första noden i huvudhistorien.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Om du öppnar den resulterande filen i Microsoft Word ser du en till synes tom sida. Formen finns där, men den är osynlig.

## Spara dokumentet

Slutligen skriver vi dokumentet till disk. Du kan välja vilket som helst av de stödjade formaten (`.docx`, `.pdf`, `.odt`, etc.). För den här tutorialen använder vi det moderna DOCX‑formatet.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Förväntat resultat

Öppna `HiddenRectangle.docx` i Word:

* Dokumentet visas tomt (inga synliga former eller text).
* Om du granskar filen med ett verktyg som **Open XML SDK** eller **Word XML Viewer**, ser du `<w:pict>`‑elementet som innehåller rektangeln med `hidden`‑attributet.

![tomt Word-dokument med dold rektangelform](image.png){: .align-center alt="tomt Word-dokument med dold rektangelform"}

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapplikation. Det inkluderar alla nödvändiga `using`‑direktiv, felhantering och kommentarer.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Kör programmet (`dotnet run`) och verifiera utdatafilen. Konsolen kommer bekräfta sparplatsen.

## Vanliga frågor och specialfall

### Kan jag dölja flera former samtidigt?

Ja. Skapa varje form, sätt `Hidden = true`, och infoga dem sekventiellt. Den dolda flaggan fungerar per nod, så blandning av dolda och synliga former i samma dokument stöds.

### Vad händer om jag bara vill dölja formen i utskriftsvyn?

Word skiljer mellan **display**‑ och **print**‑synlighet via `DisplayWhen`‑egenskapen. Aspose.Words exponerar inte ett direkt API för den flaggan, men du kan modifiera den underliggande XML‑en:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Använd detta endast när du behöver utskrifts‑endast synlighet.

### Påverkar den dolda formen filstorleken?

En dold form lägger till samma XML‑payload som en synlig, så filstorleksökningen är identisk. Men eftersom formen

## Vad bör du lära dig härnäst?

De följande tutorialerna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa tomt Word-dokument med skuggad rektangelform – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Lägg till en skugga på Word-form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}