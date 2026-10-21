---
category: general
date: 2026-03-06
description: Skapa en rektangel i Word och lägg till skugga på formen med Aspose.Words.
  Lär dig hur du infogar en rektangel i Word och hur du lägger till skugga på formen
  i C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: sv
og_description: Skapa rektangelform i Word och lägg till skugga på formen med Aspose.Words.
  Steg‑för‑steg‑guide om hur du infogar en rektangel i Word och hur du lägger till
  skugga på formen.
og_title: Skapa en rektangel med skugga i Word med Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Skapa rektangelform med skugga i Word med Aspose.Words
url: /sv/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform med skugga i Word med Aspose.Words

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument men varit osäker på hur du ger det ett polerat utseende? Du är inte ensam—de flesta utvecklare stöter på samma problem när de först försöker lägga till visuellt flair i automatiserade dokument. Den goda nyheten? Med Aspose.Words för .NET kan du både **create rectangle shape** och **add shape shadow** på bara några rader C#.

I den här handledningen går vi igenom exakt **how to insert rectangle in Word**, och visar sedan **how to add shadow to shape** så att den poppar upp från sidan. I slutet har du en färdig‑att‑spara `Shadow.docx` som du kan öppna i Word och se en gråtonad rektangel med en mjuk drop‑shadow. Inga extra bildfiler, ingen manuell justering—bara kod.

## Vad du kommer att lära dig

- Den exakta C#‑koden som behövs för att **create rectangle shape** med Aspose.Words.  
- Hur du aktiverar och konfigurerar en skugga med `Shadow`‑objektet.  
- Varför varje egenskap är viktig (t.ex. `Transparency`, `Blur`, `Angle`).  
- Vanliga fallgropar (enheter, versionskompatibilitet) och snabba lösningar.  
- Ett komplett, copy‑and‑paste‑klart program som du kan köra idag.

### Förutsättningar

- .NET 6+ (eller .NET Framework 4.7+).  
- Aspose.Words för .NET 23.10 eller senare (NuGet‑paketet är `Aspose.Words`).  
- Grundläggande kunskap om C# och Visual Studio (eller någon IDE du föredrar).  

Om du redan har dessa, låt oss hoppa rakt in.

---

## Steg 1: Ställ in projektet och importera namnrymder

Först, skapa en ny konsolapp (eller återanvänd en befintlig) och lägg till Aspose.Words‑NuGet‑paketet:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Importera sedan de nödvändiga namnrymderna i din `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Proffstips:** Om du riktar in dig på .NET 6+ kan du aktivera globala `using`‑direktiv för att undvika att upprepa dessa rader i varje fil.

---

## Steg 2: **Create rectangle shape** i ett tomt Word‑dokument

Vi börjar med ett nytt `Document`‑objekt och en `DocumentBuilder` för att manipulera det. Builderns `InsertShape`‑metod är där magin sker.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Varför 200 × 100 punkter? I Word motsvarar en punkt 1/72 tum, så rektangeln blir ungefär 2,8 × 1,4 tum—tillräckligt stor för att märkas men inte överväldigande. Du kan ändra dessa siffror efter ditt layoutbehov; kom bara ihåg att de mäts i **points**, inte pixlar.

---

## Steg 3: **Add shape shadow** – konfigurera utseendet

Nu när vi har en rektangel, låt oss ge den en subtil grå skugga. `Shadow`‑objektet finns på `Shape` och exponerar flera praktiska egenskaper.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Vad varje egenskap gör

| Egenskap | Effekt | Typiska värden |
|----------|--------|----------------|
| **Enabled** | Slår på/av skuggan | `true` eller `false` |
| **Color** | Basfärg för skuggan | Any `System.Drawing.Color` |
| **Transparency** | Opacitet (0 = solid, 1 = osynlig) | 0.0 – 1.0 |
| **Blur** | Mjukhet på kanten | 0 – 10 (higher = softer) |
| **Distance** | Avstånd mellan form och skugga | 0 – 20 points |
| **Angle** | Riktning som ljuset verkar komma från | 0 – 360 degrees |
| **Size** | Skala på skuggan relativt formen | 0 – 200 % |

> **Varför bry sig om dessa inställningar?**  
> Finjustering av skuggan låter dig matcha företagets varumärkesriktlinjer (t.ex. en subtil 20 % transparens för ett professionellt utseende) utan att behöva använda externa bildredigerare.

---

## Steg 4: Spara dokumentet och verifiera resultatet

Till sist, skriv filen till disk. Du kan välja vilken mapp du vill; ersätt bara `YOUR_DIRECTORY` med en riktig sökväg.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Öppna `Shadow.docx` i Microsoft Word så bör du se en grå rektangel med en mjuk drop‑shadow förskjuten med 45° vinkel. Den visuella effekten får formen att kännas “lyftad” från sidan—precis vad du förväntar dig av en polerad rapport eller faktura.

---

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan copy‑paste in i `Program.cs`. Inga delar saknas; det kompileras och körs som det är.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Förväntat resultat

- **Fil:** `Shadow.docx` placerad i projektets körningsmapp.  
- **Visuell:** En enda rektangel centrerad på sidan, fylld med standardvitt, och en grå skugga förskjuten 4 punkter nedåt‑höger, lätt suddad för ett naturligt utseende.

---

## Vanliga frågor & edge‑cases

### 1. Vad händer om jag behöver en annan enhet (t.ex. centimeter)?

Aspose.Words arbetar i punkter, men du kan konvertera centimeter till punkter med den enkla formeln:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Fungerar detta med äldre versioner av Aspose.Words?

`Shadow`‑API:et introducerades i version 14.0. Om du använder en äldre version måste du uppgradera via NuGet. Resten av koden (skapande av former) har varit stabil i många år, så du kommer inte att stöta på breaking changes.

### 3. Kan jag lägga till en skugga på andra former (t.ex. cirklar)?

Absolut—varje `Shape`‑objekt exponerar en `Shadow`‑egenskap. Byt bara `ShapeType.Rectangle` mot `ShapeType.Ellipse` eller `ShapeType.Cloud`, och tillämpa sedan samma skuggeinställningar.

### 4. Vad händer om jag behöver en färgad skugga (t.ex. blå för ett varumärke)?

Byt `Color.Gray` mot vilken `Color` du vill:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Kom ihåg att justera `Transparency` så att färgen inte blir för dominerande.

---

## 🎨 Visuell sammanfattning

![skapa rektangelform med skugga i Word med Aspose.Words](image-placeholder.png "skapa rektangelform med skugga i Word med Aspose.Words")

*Alt text: skapa rektangelform med skugga i Word med Aspose.Words*

Skärmdumpen (platshållare) visar det färdiga dokumentet—endast rektangeln och dess mjuka grå skugga.

---

## Slutsats

Du vet nu hur du **create rectangle shape** i en Word‑fil, **add shape shadow**, och finjusterar varje visuellt aspekt med Aspose.Words för .NET. Det korta programmet vi byggde täcker hela arbetsflödet—from

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}