---
category: general
date: 2026-03-25
description: Skapa PDF-dokument i C# och lär dig hur du lägger till en rektangel,
  sätter fyllningsfärg, justerar formens storlek och ställer in formens transparens
  på bara några steg.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: sv
og_description: Skapa PDF-dokument i C# och se hur du lägger till en rektangel, ställer
  in dess fyllningsfärg, storlek och transparens för ett polerat PDF-utdata.
og_title: Skapa PDF-dokument med en rektangelform – C#-handledning
tags:
- C#
- PDF
- Aspose.Words
title: Skapa PDF-dokument med en rektangel – Fullständig C#-guide
url: /sv/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa PDF-dokument med en rektangel‑form – Fullständig C#‑guide

Har du någonsin behövt **skapa PDF-dokument** som innehåller en anpassad form, men varit osäker på var du ska börja? Du är inte ensam. Oavsett om du bygger en rapportgenerator eller en marknadsföringsflyer, kan möjligheten att programatiskt rita en rektangel, sätta dess fyllningsfärg, justera dess storlek och till och med justera dess transparens göra dina PDF‑filer mycket mer professionella.

I den här handledningen går vi igenom ett komplett, färdigt körbart C#‑exempel som **skapar ett PDF-dokument**, **lägger till en rektangel‑form**, **sätter fyllningsfärgen**, **definierar formens storlek** och **ställer in formens transparens** för en subtil yttre skugga. När du är klar har du en enda PDF‑fil (`shadow.pdf`) som du kan öppna för att se resultatet.

> **Pro tip:** Samma tillvägagångssätt fungerar med andra formtyper (ellipse, linje osv.) – byt bara `ShapeType.RECTANGLE` mot den du behöver.

---

## Vad du behöver

| Förutsättning | Varför det är viktigt |
|---------------|-----------------------|
| **.NET 6+** (eller .NET Framework 4.6+) | Aspose.Words‑biblioteket riktar sig mot moderna runtime‑miljöer. |
| **Aspose.Words for .NET** NuGet‑paket | Tillhandahåller `Document`, `Shape`, `ShadowEffect` och relaterade klasser. |
| **En C#‑IDE** (Visual Studio, Rider, VS Code) | Gör felsökning och körning av exemplet enkelt. |
| **Grundläggande C#‑kunskaper** | Du förstår syntaxen utan att behöva gå på djupet. |

Du kan installera biblioteket via kommandoraden:

```bash
dotnet add package Aspose.Words
```

Det är allt – inga extra DLL‑filer, inga inhemska beroenden. När paketet är på plats kommer koden nedan att kompilera och köras.

---

## Steg‑för‑steg‑implementering

Nedan delar vi upp processen i fem logiska steg. Varje steg har en tydlig rubrik (så att AI‑modeller kan indexera dem) och ett kort kodblock som du kan kopiera‑och‑klistra direkt.

### ## 1. Skapa PDF-dokument och förbered duken

Det allra första vi gör är att instansiera ett `Document`. Tänk på det som en tom duk som så småningom blir din PDF‑fil.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Varför?** `Document` innehåller alla sektioner, stycken och former. Att börja med ett rent objekt garanterar att inga dolda artefakter från tidigare körningar finns med.

### ## 2. Lägg till rektangel‑form – sätt fyllningsfärg och formens storlek

Nu skapar vi en rektangel, ger den en ljusgul fyllning och definierar dess dimensioner. Detta täcker både **add rectangle shape**, **set fill color** samt **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Obs:** Bredd/höjd mäts i punkter (1 punkt = 1/72 tum). Justera dessa siffror för att passa din layout.

### ## 3. Applicera en yttre skugga och ställ in formens transparens

Skuggor ger djup, och att kontrollera deras opacitet är kärnan i **set shape transparency**. Nedan konfigurerar vi en grå yttre skugga med 30 % transparens.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Varför sätta transparens?** En 30 % transparent skugga ser subtil ut och förhindrar att rektangeln ser “platt” ut på sidan.

### ## 4. Infoga formen i dokumentets kropp

Vi placerar nu rektangeln i det första stycket i dokumentets första sektion. Detta steg binder ihop allt.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Edge case:** Om du behöver formen på en ny sida, lägg till `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` innan du lägger till formen.

### ## 5. Spara dokumentet som en PDF‑fil

Till sist sparar vi den minnesbaserade strukturen till en fysisk PDF‑fil. Filen skrivs till den mapp du anger.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

När du kör programmet skapas en fil med namnet `shadow.pdf`. När du öppnar den ser du en gul rektangel med en mjuk grå skugga förskjuten 4 punkter – exakt vad vår kod beskriver.

> **Förväntat resultat:** En enkel‑sidig PDF där rektangeln sitter nära sidans övre‑vänstra hörn, fylld med gult, 200 × 100 punkter stor, och kastar en halvtransparent yttre skugga.

---

## Fullt fungerande exempel (Klar‑för‑kopiering)

Nedan är hela källfilen, redo att klistras in i ett nytt konsolprojekt.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tips:** Ersätt `YOUR_DIRECTORY` med en absolut sökväg som `C:\Temp` eller en relativ sökväg som `.\output`. Programmet skapar mappen om den inte redan finns.

---

## Vanliga frågor (FAQ)

**Q: Kan jag ändra rektangelns position på sidan?**  
A: Absolut. Ställ in `rectangle.Left` och `rectangle.Top` (båda mäts i punkter) innan du lägger till den i stycket.

**Q: Vad händer om jag vill ha en transparent fyllning istället för en transparent skugga?**  
A: Använd `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – det första argumentet är alfa‑kanalen (0‑255), där 128 ger cirka 50 % transparens.

**Q: Fungerar detta med .NET Core?**  
A: Ja. Aspose.Words stödjer .NET Standard 2.0+, så du kan köra samma kod på .NET 6, .NET 7 eller .NET Framework 4.6+.

**Q: Hur kan jag lägga till flera former?**  
A: Upprepa bara steg 2‑4 för varje form, eventuellt infoga dem i olika stycken eller sektioner.

---

## Slutsats

Vi har precis **skapat ett PDF-dokument** från grunden, **lagt till en rektangel‑form**, **satt dess fyllningsfärg**, **definierat dess storlek** och **justerat formens transparens** för att uppnå en polerad skuggeffekt. Exempelkoden är självständig, körs på under en minut och demonstrerar de grundläggande koncept du behöver för mer avancerade PDF‑layouter.

Redo för nästa utmaning? Prova att byta rektangeln mot en form med rundade hörn, bädda in en bild i formen, eller generera automatiskt en innehållsförteckning. Samma API låter dig lager på lager med text, bilder och vektorer – så himlen är gränsen.

Om du fann den här guiden användbar, ge den ett stjärnmärke på GitHub, dela den med en kollega, eller lämna en kommentar med dina egna varianter. Happy coding! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Skärmbild som visar den skapade PDF‑filen med en gul rektangel och grå yttre skugga")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}