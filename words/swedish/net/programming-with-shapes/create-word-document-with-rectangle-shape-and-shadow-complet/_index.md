---
category: general
date: 2026-01-02
description: Skapa ett Word‑dokument med en rektangelform, ställ in formens fyllningsfärg
  och spara docx‑filen med Aspose.Words. Lär dig hur du skapar en rektangel med skugga
  på några minuter.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: sv
og_description: Skapa ett Word-dokument med en anpassad rektangel, ställ in dess fyllningsfärg,
  lägg till en skugga och spara som DOCX. Fullständig kod och förklaringar.
og_title: Skapa Word-dokument med rektangelform – Steg för steg
tags:
- Aspose.Words
- C#
- Document Generation
title: Skapa Word-dokument med rektangelform och skugga – Komplett guide
url: /sv/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument med rektangelform och skugga – Komplett guide

Har du någonsin undrat hur man **create word document** som innehåller en snyggt stylad rektangel? Kanske behöver du en platshållare för en logotyp, en färgad banner, eller bara en visuell markering i en rapport. I den här handledningen kommer vi att **add rectangle shape**, ge den en fyllningsfärg, applicera en subtil skugga, och slutligen **save docx file** – allt med Aspose.Words för .NET.

Du får med dig ett färdigt C#‑kodexempel som kan köras direkt, en tydlig förklaring av varje rad, och en rad tips som du kan återanvända i dina egna projekt. Inga onödiga utsvävningar, bara en praktisk lösning du kan kopiera‑klistra.

## Vad du behöver

- .NET 6 eller senare (koden fungerar även på .NET Framework)  
- Visual Studio 2022 (eller någon annan editor du föredrar)  
- **Aspose.Words** NuGet‑paket (`Install-Package Aspose.Words`)  

Om du redan har dem, toppen – låt oss dyka in.

## Steg 1 – Initiera ett nytt dokument (How to create word document)

Det första du måste göra är att **create word document** i minnet. Tänk på det som att öppna en tom duk där du senare kommer att rita din rektangel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Varför detta är viktigt:** `Document` representerar hela DOCX‑filen, medan `DocumentBuilder` är en bekväm hjälpare som låter dig infoga text, tabeller, bilder och former utan att manuellt hantera det underliggande nodträdet.

## Steg 2 – Infoga en rektangelform (Add rectangle shape)

Nu kommer vi att **add rectangle shape** till dokumentet. Metoden `InsertShape` tar formen typ och dess dimensioner i punkter (1 punkt = 1/72 tum).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tip:** Om du någonsin behöver skapa en annan geometri (ellips, triangel osv.), ändra bara `ShapeType.Rectangle` till det önskade enum‑värdet.

## Steg 3 – Konfigurera skuggan (Set shape fill color & shadow)

En skugga kan få en platt form att kännas mer tredimensionell. Här aktiverar vi skuggan och justerar dess utseende.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Varför dessa värden?** En måttlig oskärpedjup och ett avstånd på 5 punkter hindrar skuggan från att överväldiga formen, medan 45° efterliknar en ljuskälla som kommer från övre vänstra hörnet – en vanlig UI‑konvention.

## Steg 4 – Spara dokumentet (Save docx file)

Till sist **save docx file** till disk. Anpassa sökvägen efter din miljö.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

När du öppnar `ShadowDemo.docx` i Word bör du se en ljusblå rektangel med en mjuk grå skugga, precis som skärmbilden nedan.

![Skapa Word-dokument med rektangelform och skugga](https://example.com/images/rectangle-shadow.png "Skapa Word-dokument med rektangelform och skugga")

*Bildens alt‑text:* **Create Word Document** som visar en rektangelform med en skugga.

## Fullt, körklart exempel (How to create rectangle and save)

När vi sätter ihop allt, här är det kompletta programmet som du kan kopiera in i en konsolapp:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Förväntat resultat

- En fil med namnet **ShadowDemo.docx** visas i målmappen.  
- När du öppnar den i Microsoft Word visas en enda sida med texten “Shadow Demo” följt av en ljusblå rektangel.  
- Rektangeln kastar en mjuk grå skugga i 45° vinkel, vilket ger den en lätt 3‑D‑känsla.

## Vanliga frågor & specialfall

### Vad händer om jag behöver en annan storlek?

Ändra bara argumenten `200, 100` i `InsertShape`. Dessa siffror är bredden och höjden i punkter. För en kvadrat, använd identiska värden.

### Kan jag göra skuggan mer framträdande?

Öka `BlurRadius` för en mjukare kant, höj `Distance` för ett större avstånd, eller sänk `Transparency` (t.ex. `0.1`) för att göra den mörkare.

### Hur lägger jag till en kantlinje runt rektangeln?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Är detta kompatibelt med äldre versioner av Aspose.Words?

Ja. Klassen `ShadowFormat` har funnits sedan tidiga 2020‑utgåvor. Om du använder en mycket gammal version kan du behöva uppgradera för att få tillgång till alla egenskaper.

## Tips & fallgropar

- **Pro tip:** Se alltid till att frigöra stora dokument (`doc.Dispose()`) när du är klar, särskilt i webbapplikationer, för att frigöra inhemska resurser.  
- **Watch out for:** Att använda en relativ sökväg utan rätt behörigheter kan orsaka `UnauthorizedAccessException`. Föredra absoluta sökvägar eller säkerställ att app‑poolen har skrivbehörighet.  
- **Remember:** `FillColor`‑egenskapen accepterar vilken `System.Drawing.Color` som helst. Använd gärna `Color.FromArgb(255, 173, 216, 230)` för en anpassad pastellfärg.

## Nästa steg

Nu när du vet hur man **create word document**, **add rectangle shape**, **set shape fill color**, och **save docx file**, kan du experimentera vidare:

- Infoga flera former och arrangera dem med `RelativeHorizontalPosition` och `RelativeVerticalPosition`.  
- Kombinera rektangeln med text med `Shape.TextBox` för bildtexter.  
- Exportera samma dokument till PDF (`doc.Save("output.pdf")`) för distribution.

Om du är nyfiken på mer avancerad grafik, kolla in Aspose.Words stöd för **WordArt**, **charts**, och **inline images**. Alla följer samma mönster: skapa en nod, konfigurera dess egenskaper, och spara.

---

### TL;DR

- Använd `Document` och `DocumentBuilder` för att **create word document**.  
- Anropa `InsertShape(ShapeType.Rectangle, …)` för att **add rectangle shape**.  
- Ställ in `FillColor` för önskad bakgrund.  
- Aktivera `ShadowFormat` och justera dess egenskaper för ett polerat utseende.  
- Avsluta med `document.Save("yourPath.docx")` för att **save docx file**.

Lycka till med kodandet, och njut av att göra dina Word‑filer lite snyggare!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}