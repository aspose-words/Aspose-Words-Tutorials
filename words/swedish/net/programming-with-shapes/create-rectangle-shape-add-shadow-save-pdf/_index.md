---
category: general
date: 2026-02-24
description: Skapa en rektangelform i C# med Aspose.Words, lägg till skugga på formen
  och spara dokumentet som PDF. Lär dig hur du lägger till skugga och hur du sparar
  PDF på några minuter.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: sv
og_description: Skapa en rektangelform i C# med Aspose.Words, lägg sedan till skugga
  på formen och spara dokumentet som PDF – en komplett steg‑för‑steg‑guide.
og_title: Skapa rektangelform, lägg till skugga och spara PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Skapa rektangel, lägg till skugga och spara PDF
url: /sv/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform, lägg till skugga & spara PDF

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument men också vilja ha en fin skuggning och en PDF‑utmatning? Du är inte ensam. I många rapport‑ eller fakturagenereringsprojekt gör den visuella poleringen—som en subtil skugga—skillnaden mellan “bara en fil till” och “professionellt dokument.”  

I den här handledningen går vi igenom exakt det: med **Aspose.Words for .NET** för att skapa en rektangelform, lägga till skugga på formen och slutligen **save document as PDF**. När du är klar har du en färdig‑att‑köra C#‑konsolapp som producerar en PDF med en skuggad rektangel, och du förstår hur du justerar skuggan eller ändrar exportalternativen.

## Vad du behöver

- .NET 6 SDK (eller någon nyare .NET‑version) – API‑et fungerar likadant på .NET Framework 4.x också.  
- Aspose.Words for .NET NuGet‑paket (`Aspose.Words`) – installera det med `dotnet add package Aspose.Words`.  
- En kodredigerare – Visual Studio, VS Code eller Rider räcker.  

Inga extra licenssteg behövs för detta exempel; det fria utvärderingsläget räcker för att se PDF‑utmatningen.

## Steg 1: Ställ in projektet och importera namnrymder

Först och främst, låt oss skapa ett konsolprojekt och importera de klasser vi kommer att behöva.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Varför detta är viktigt:* `Document` och `DocumentBuilder` ger oss duken, medan `Shape` och `ShadowFormat` låter oss rita och formatera rektangeln. Att importera dem i förväg håller den senare koden prydlig.

## Steg 2: **Create rectangle shape** med önskade dimensioner

Nu skapar vi faktiskt ett tomt dokument och infogar en rektangel. Lägg märke till hur `InsertShape`‑metoden returnerar ett `Shape`‑objekt som vi omedelbart kan formatera.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Förklaring*: Storleken anges i punkter (1 pt = 1/72 tum). Justera siffrorna för att passa din layout. Vi ger också formen en ljusblå fyllning för att få skuggan att framträda.

## Steg 3: **Add shadow to shape** – finjustera effekten

En skugga är inte bara “på/av”. Du kan styra dess färg, oskärpa, avstånd, riktning och till och med transparens. Här är en praktisk konfiguration som fungerar bra för de flesta rapporter.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Varför du kan vilja ändra dessa värden:*  
- **BlurRadius** – öka för en drömlik effekt, minska för en skarp kant.  
- **Direction** – 0° pekar åt höger, 90° neråt, 180° åt vänster osv. Rotera för att matcha din sidlayout.  
- **Transparency** – sätt till `0` för en solid skugga, `0.5` för halvtransparent osv.

### Så lägger du till skugga – alternativa tillvägagångssätt

Om du behöver en **multiple‑layer shadow** (t.ex. en mörkare yttre skugga plus en ljusare inre), kan du skapa en andra form, förskjuta den och sätta ett annat `ShadowFormat`. Eller, för ett snabbt “utan‑oskärpa”‑utseende, sätt `BlurRadius = 0`.

## Steg 4: **Save document as PDF** – den slutgiltiga exporten

När rektangeln och dess skugga är klara är sista steget att skriva filen som en PDF. Aspose.Words hanterar konverteringen internt; du anropar bara `Save` med önskat format.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tips*: Om du behöver styra PDF‑kompatibilitet (PDF/A, PDF/X) eller bädda in teckensnitt, använd en överlagring:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Det är **how to save pdf**‑delen i ett nötskal.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i `Program.cs`. Det kompileras och körs som det är (se bara till att mål‑mappen finns).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Förväntat resultat

Öppna den genererade `ShadowRectangle.pdf`. Du kommer att se en enda sida med en ljusblå rektangel, en mjuk grå skugga förskjuten 45° ned‑höger, och rena kanter. PDF‑filen bör kunna visas i någon modern läsare (Adobe Acrobat, Edge, Chrome).

![Create rectangle shape with shadow in PDF](/images/shadow-rectangle.png "Create rectangle shape with shadow")

*(Bildens alt‑text innehåller huvudnyckelordet för SEO.)*

## Vanliga frågor & hantering av edge‑case

**Vad händer om skuggan försvinner i PDF‑filen?**  
Se till att du använder en recent version of Aspose.Words (≥23.3). Äldre builds hade en bugg där vissa shadow properties ignorerades under PDF‑konverteringen.

**Kan jag ändra skuggans färg för att matcha mitt varumärke?**  
Absolut—byt bara ut `System.Drawing.Color.Gray` mot vilken `Color` du vill, t.ex. `Color.FromArgb(128, 0, 0, 255)` för en semi‑transparent blå.

**Hur lägger jag till en skugga på andra former (ellips, stjärna, osv.)?**  
Samma `ShadowFormat` fungerar för alla `Shape`‑objekt. Efter att du skapat formen, hämta dess `ShadowFormat` och sätt egenskaperna.

**Vad händer med DPI‑ eller skalningsproblem?**  
PDF‑renderingen respekterar formens punktstorlek. Om du behöver en högre upplösning (för utskrift), justera formens dimensioner därefter eller sätt `PdfSaveOptions.ImageResolution`.

**Kan jag exportera till andra format, som PNG?**  
Ja—anropa bara `document.Save("output.png", SaveFormat.Png)`. Skuggan renderas på samma sätt.

## Pro‑tips & bästa praxis

- **Reuse the builder**: Om du lägger till flera former, behåll en enda `DocumentBuilder`‑instans; det är billigare än att skapa många.
- **Batch saving**: När du genererar många PDF‑filer i en loop, återanvänd `PdfSaveOptions`‑objektet för att undvika upprepade allokeringar.
- **Testing**: Öppna alltid PDF‑filen efter sparning för att verifiera att skuggan visas som förväntat. Vissa PDF‑visare renderar skuggor något annorlunda; Adobe Acrobat är den mest pålitliga referensen.
- **Performance**: För stora dokument, inaktivera `DocumentBuilder.InsertShape`s automatiska sidbrytningar genom att sätta `builder.PageSetup.DifferentFirstPageHeaderFooter = false` om du inte behöver det.

## Slutsats

Vi har gått igenom allt du behöver för att **create rectangle shape**, **add shadow to shape**, och **save document as PDF** med Aspose.Words for .NET. Koden är kompakt, koncepten är förklarade, och du har nu en solid grund för att experimentera med andra former, skuggstilar och exportalternativ.  

Nästa steg? Prova att byta ut rektangeln mot en rundad‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}