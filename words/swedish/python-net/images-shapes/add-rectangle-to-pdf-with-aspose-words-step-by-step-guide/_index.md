---
category: general
date: 2026-03-01
description: Lägg till en rektangel i PDF snabbt med Aspose.Words. Lär dig att infoga
  en form i PDF, lägga till grafik i PDF och skapa ett PDF-dokument programatiskt
  med en anpassad skugga.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: sv
og_description: Lägg till rektangel i PDF med Aspose.Words. Denna handledning visar
  hur man infogar en form i en PDF, lägger till grafik i PDF och skapar ett PDF‑dokument
  programmässigt i C#.
og_title: Lägg till rektangel i PDF med Aspose.Words – Komplett guide
tags:
- pdf
- aspnet
- csharp
- graphics
title: Lägg till rektangel i PDF med Aspose.Words – Steg‑för‑steg‑guide
url: /sv/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till rektangel i PDF med Aspose.Words – Komplett guide

Har du någonsin behövt **add rectangle to PDF** men varit osäker på vilket API‑anrop som gör jobbet? Du är inte ensam—utvecklare frågar ständigt, “Hur infogar jag en shape PDF och ändå håller filen lätt?” Den goda nyheten är att Aspose.Words gör det enkelt. I den här handledningen går vi igenom hela processen, från att skapa ett PDF‑dokument programatiskt till att styla rektangeln med en skugga.

Vi kommer också att strö in några extra godbitar: du lär dig hur du **add graphics to PDF**, ser de exakta stegen för **insert shape PDF**, och avslutar med ett färdigt exempel som **creates PDF with shape**. Inga externa referenser, bara en självständig lösning som du kan kopiera‑klistra idag.

## Förutsättningar

Innan vi sätter igång, se till att du har:

- .NET 6.0 eller senare (Aspose.Words fungerar med .NET Standard 2.0+)
- En giltig Aspose.Words for .NET‑licens eller en temporär utvärderingsnyckel
- Visual Studio 2022 (eller någon annan IDE du föredrar)
- Grundläggande C#‑kunskaper—inget avancerat, bara förmågan att köra en konsolapp

Det är allt. Om du har detta är du redo att köra.

## Steg 1: Skapa ett PDF‑dokument programatiskt

Det första du gör när du vill **add rectangle to PDF** är att starta ett tomt dokument. Tänk på `Document`‑klassen som en tom duk; allt du lägger till senare lever där inne.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Varför börja med ett tomt dokument? För att det garanterar full kontroll över varje element—inga dolda sidhuvuden eller sidfötter att kämpa med senare.

## Steg 2: Initiera en DocumentBuilder för att insert shape PDF

En `DocumentBuilder` är din ritpensel. Den vet hur man placerar text, bilder och, avgörande för oss, former. Utan den skulle du behöva manipulera nodträdet på låg nivå själv—en mardröm för de flesta utvecklare.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Observera att vi ännu inte har lagt till några sidor. Buildern skapar automatiskt en sida första gången du infogar något, vilket håller koden prydlig.

## Steg 3: Insert a rectangle shape – kärnan i “add rectangle to PDF”

Nu kommer den roliga delen: att infoga rektangeln. Metoden `InsertShape` stöder dussintals `ShapeType`‑värden; vi väljer `ShapeType.Rectangle` och ger den en storlek på 200 × 100 punkter.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Vid detta tillfälle innehåller PDF‑filen redan en enkel rektangel. Om du öppnar filen nu ser du en enkel ruta i det övre vänstra hörnet på första sidan. Det är grunden för **add graphics to PDF**.

## Steg 4: Style the rectangle – lägga till en anpassad skugga

En rektangel utan stil är tråkig. Låt oss ge den en subtil drop‑shadow så den *poppar* när PDF‑filen renderas. Objektet `ShadowFormat` styr allt från suddradie till opacitet.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Varför bry sig om en skugga? Förutom den estetiska förbättringen kan en skugga hjälpa till att särskilja överlappande grafik—något du kan behöva när du **add graphics to PDF** i mer komplexa rapporter.

## Steg 5: Spara filen – slutför “create PDF with shape”-arbetsflödet

Den sista raden skriver allt till disk. Aspose.Words väljer automatiskt rätt PDF‑version och bäddar in nödvändiga resurser.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Öppna `ShapeWithShadow.pdf` så ser du en snyggt skuggad rektangel som stolt sitter på sidan. Det är hela flödet för **create pdf document programmatically**, packat i under 30 kodrader.

## Fullt fungerande exempel – create PDF with shape från början till slut

Nedan är det kompletta programmet som du kan kopiera‑klistra in i ett nytt Console App‑projekt. Det inkluderar alla `using`‑satser, `Main`‑metoden och en kort kommentar för framtida referens.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Förväntat resultat:** en enkelsidig PDF där en 200 × 100‑punkts rektangel sitter nära det övre vänstra hörnet, prydd med en mjuk, 45‑gradig skugga. Öppna filen i någon PDF‑visare för att verifiera.

## Vanliga frågor & kantfall

### Fungerar detta med andra formtyper?
Absolut. Byt ut `ShapeType.Rectangle` mot `ShapeType.Ellipse`, `ShapeType.Triangle` eller någon av de 150+ alternativ som Aspose.Words stödjer. Samma `ShadowFormat`‑egenskaper gäller.

### Vad om jag behöver rektangeln på en specifik sida?
Efter att ha infogat formen kan du flytta den till en annan sida genom att justera builderns `CurrentPage`‑egenskap innan du anropar `InsertShape`. Till exempel:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Kan jag ändra rektangelns fyllningsfärg?
Självklart. Använd egenskapen `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Hur påverkar detta filstorleken?
Att lägga till en enkel form och en skugga adderar bara några kilobytes. Om du börjar stapla många grafiska element, överväg att komprimera bilder eller använda vektorbaserade former för att hålla PDF‑filen slank.

### Krävs en licens för produktion?
Aspose.Words fungerar i utvärderingsläge, men den genererade PDF‑filen kommer att innehålla ett vattenmärke. Köp en licens för obegränsad användning och för att ta bort vattenmärket.

## Tips & tricks (Pro‑nivå)

- **Batch‑insertion:** Om du behöver dussintals rektanglar, loopa över en samling koordinater och återanvänd samma `DocumentBuilder`—prestandan förblir linjär.
- **Layering:** Sätt `rect.WrapType = WrapType.Inline` om du vill att rektangeln ska flyta med text, eller `WrapType.Square` för att låta texten omsluta den.
- **PDF/A‑kompatibilitet:** Anropa `doc.CompatibilityOptions.OptimizeForPdfA = true;` innan du sparar om du behöver ett arkivvänligt PDF‑format.

## Visuell sammanfattning

![lägg till rektangel i pdf exempel](https://example.com/rectangle-shadow.png "lägg till rektangel i pdf exempel")

Bilden illustrerar den slutgiltiga PDF‑layouten: en ren rektangel med en subtil skugga, exakt vad vår kod producerar.

## Slutsats

Du vet nu **how to add rectangle to PDF** med Aspose.Words, hur du **insert shape PDF**, och hur du **add graphics to PDF** med anpassad styling—allt medan du **creating PDF document programmatically** och avslutar med ett **create PDF with shape**‑exempel som du kan återanvända imorgon.  

Nästa steg är att byta ut rektangeln mot en logotyp, eller kombinera flera former för att bygga ett enkelt diagram. Du kan också utforska textomslag, rotation eller till och med bädda in en hyperlänk i formen. API‑et är så rikt att du kan förvandla en statisk PDF till en interaktiv, grafik‑rik rapport utan att någonsin lämna C#.

Känn dig fri att experimentera, och om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}