---
category: general
date: 2026-03-27
description: Skapa Word‑dokument i C# och lär dig hur du lägger till en form, applicerar
  skugga på formen och ställer in skuggavståndet. Steg‑för‑steg‑guide för Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: sv
og_description: Skapa ett Word‑dokument i C# med en rektangelform och anpassad skugga.
  Följ den kompletta handledningen för att ställa in skuggavstånd och stil.
og_title: Skapa Word-dokument i C# – Lägg till form med skugga
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa Word-dokument i C# – Lägg till form med skugga
url: /sv/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument C# – Lägg till form med skugga

Har du någonsin behövt **create word document c#** som innehåller en snyggt stylad rektangel? Kanske bygger du en rapportmall och vill ha en subtil drop‑shadow för att få layouten att sticka ut. I den här handledningen går vi igenom precis det – hur man lägger till en form, applicerar skugga på formen och till och med justerar skuggavståndet med Aspose.Words.

Vi börjar med ett tomt dokument, lägger in en rektangel, ger den en förinställd skugga och avslutar med att spara filen. När du är klar har du en färdig .docx som du kan öppna i Word och se effekten omedelbart. Inga externa verktyg, bara ren C#-kod.

## Förutsättningar

- .NET 6 (eller någon recent .NET Framework) installerat.
- Visual Studio 2022 eller VS Code med C#-tillägg.
- Aspose.Words för .NET NuGet-paket (`Aspose.Words` version 23.12 eller senare).  
  Du kan lägga till det via Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

Det är allt – inga extra DLL:er eller COM-interoperabilitet krävs.

## Steg 1: Initiera ett nytt dokument och en builder – *create word document c#* grunderna

Först behöver vi ett `Document`-objekt som representerar Word-filen och en `DocumentBuilder` för att redigera den.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Varför detta steg är viktigt:** `Document`-klassen är behållaren för alla Word-delar (sidor, stilar, bilder). Buildern är ett hög‑nivå API som abstraherar bort låg‑nivå nodmanipulation, vilket gör det enkelt att **create word document c#** utan att behöva hantera XML direkt.

## Steg 2: Infoga en rektangel‑form – *how to create rectangle*

Nu placerar vi en rektangel på sidan. Storleken anges i punkter (1 pt ≈ 1/72 tum).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Proffstips:** Om du behöver en annan form, byt bara `ShapeType.Rectangle` mot `ShapeType.Ellipse`, `ShapeType.Triangle` osv. Samma kod fungerar för **how to add shape** av vilken typ som helst.

## Steg 3: Applicera en förinställd skugga och finjustera den – *apply shadow to shape*

Aspose.Words levereras med flera förinställda skuggformat. Vi kommer att använda `Preset1` och sedan anpassa avstånd, oskärpa, transparens och färg.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Varför anpassa skuggan?** `Distance`‑egenskapen styr hur långt skuggan sitter från rektangeln – tänk på det som “lyftet” du ser i en 3‑D‑rendering. Att ändra `BlurRadius` mjukar upp kanterna, medan `Transparency` låter dig skapa ett subtilt, professionellt utseende. Detta uppfyller kravet **set shadow distance** och visar hur du **apply shadow to shape** på ett flexibelt sätt.

## Steg 4: Spara dokumentet – *create word document c#* slutförande

Till sist skriver du dokumentet till disk. Justera sökvägen till en mapp du har skrivbehörighet till.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öppna den resulterande filen i Microsoft Word, så ser du en ljusblå rektangel med en mjuk grå skugga förskjuten med 5 pt. Det är det visuella beviset på att du framgångsrikt **create word document c#** med en stylad form.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="exempel på create word document c# som visar rektangel med skugga"}

## Valfria variationer & kantfall

| Scenario | Vad som ska ändras | Varför det är viktigt |
|----------|--------------------|-----------------------|
| **Olika skuggstil** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Ger dig ett mer dramatiskt utseende utan extra kod. |
| **Ingen förinställning – anpassad skugga** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Full kontroll över riktning och djup. |
| **Flera former** | Call `builder.InsertShape` again before saving. | Användbart för komplexa mallar med ikoner, logotyper osv. |
| **Kompatibilitet med äldre Aspose-versioner** | Use `ShadowEffect` class (available in v20.x). | Säkerställer att din kod körs på legacy projects. |
| **Spara som PDF** | `document.Save("ShadowShape.pdf");` | Same shadow rendering appears in PDF output. |

> **Vanlig fråga:** *Vad händer om skuggan inte visas i Word?*  
> Se till att du använder en recent version of Aspose.Words (≥ 22.9). Äldre versioner hade begränsat stöd för skuggor. Verifiera också att dokumentet öppnas i en recent version of Word (2016+).

## Fullt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Det inkluderar alla `using`‑direktiv, kommentarer och felhantering för en smidig upplevelse.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Kör programmet, navigera till `C:\Temp\ShadowShape.docx`, och du kommer att se rektangeln med den exakta skuggan vi konfigurerade.

## Sammanfattning & nästa steg

- Du vet nu hur man **create word document c#**, infogar en rektangel och **apply shadow to shape** med en anpassad **set shadow distance**.  
- Exemplet använder Aspose.Words, som abstraherar bort OpenXML-komplexiteten och garanterar konsekvent rendering över Word-versioner.  
- Vill du gå längre? Prova att kombinera flera former, lägga till text i rektangeln eller exportera samma dokument som PDF för att se hur skuggan översätts.

### Relaterade ämnen du kan utforska

- **How to add shape** till ett sidhuvud/sidfot för varumärkesprofilering.  
- Använda **Aspose.Words** för att programatiskt infoga diagram och tabeller.  
- Anpassa **shadow effects** på bilder istället för vektorformer.  
- Automatisera massgenerering av dokument för fakturor eller certifikat.

Känn dig fri att experimentera, bryta koden och sedan bygga om den – det är det snabbaste sättet att internalisera koncepten. Om du stöter på problem, lämna en kommentar nedan eller kolla den officiella Aspose.Words-dokumentationen för djupare API‑insikter.

Lycka till med kodandet, och njut av att göra dina Word-filer lite mer polerade!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}