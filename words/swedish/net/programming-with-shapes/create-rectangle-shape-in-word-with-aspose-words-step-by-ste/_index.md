---
category: general
date: 2025-12-29
description: Skapa en rektangel i ett Word‑dokument med Aspose.Words C#. Lär dig att
  ange formens transparens, ställa in skuggfärg och spara Word‑dokumentet enkelt.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: sv
og_description: Skapa en rektangelform i ett Word‑dokument med Aspose.Words C#. Denna
  guide visar hur du ställer in formens transparens, sätter skuggfärg och sparar Word‑dokumentet.
og_title: Skapa rektangel i Word – Komplett Aspose.Words-handledning
tags:
- Aspose.Words
- C#
- Word Automation
title: Skapa rektangelform i Word med Aspose.Words – Steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word – Komplett Aspose.Words‑handledning

Har du någonsin behövt **skapa rektangelform** i ett Word‑dokument men inte vetat var du ska börja? Du är inte ensam; många utvecklare stöter på detta när de automatiserar rapporter eller fakturor. I den här guiden går vi igenom exakt hur du skapar en rektangelform, ställer in formens transparens, sätter skuggfärg och slutligen **sparar Word‑dokumentet** med Aspose.Words för .NET.

Vi täcker allt från det första dokumentobjektet till den slutgiltiga `.docx`‑filen på disken, så att du i slutet kan **skapa Word‑dokument** programatiskt utan gissningar. Inga externa referenser, bara en självständig lösning som du kan kopiera‑klistra in i ditt projekt.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.7+)
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)
- Grundläggande kunskap om C#‑syntax
- En IDE du föredrar (Visual Studio, Rider, VS Code, osv.)

> **Proffstips:** Om du använder en gratis provversion av Aspose.Words kommer biblioteket att lägga till ett vattenmärke i utdatafilen. För produktion behöver du en giltig licens.

## Steg 1: Initiera dokumentet och byggaren

Det första vi gör är att skapa ett nytt, tomt Word‑dokument och en `DocumentBuilder` som låter oss infoga innehåll. Tänk på byggaren som en virtuell penna som ritar på sidan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Varför detta är viktigt:** Utan en `DocumentBuilder` skulle du behöva manipulera nodträdet på låg nivå direkt, vilket är felbenäget och svårare att läsa.

## Steg 2: Skapa rektangelform

Nu **skapar vi rektangelform**. Metoden `InsertShape` tar en `ShapeType`‑enum, bredd och höjd (i punkter). Det returnerade `Shape`‑objektet låter oss justera visuella egenskaper senare.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Vid detta tillfälle är rektangeln en solid svart ruta förankrad i det aktuella stycket. Du kan flytta den, ändra storlek eller till och med rotera den senare om du behöver.

![create rectangle shape with shadow](/images/rectangle-shadow.png "Ett Word‑dokument som visar en rektangelform med en grå skugga")

*Bildtext: skapa rektangelform med skugga i ett Word‑dokument*

## Steg 3: Ställ in formens transparens

Transparens är “genomskinlighetsnivån” för formens fyllning. Aspose.Words använder en `Transparency`‑egenskap som varierar från `0.0` (opak) till `1.0` (fullt genomskinlig). Här **ställer vi formens transparens** till 40 % så att den underliggande texten förblir läsbar.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Edge case:** Om du behöver en helt osynlig form men ändå vill att skuggan ska visas, sätt `Transparency` till `1.0` och ge formen en icke‑noll konturbredd.

## Steg 4: Konfigurera skuggan

En subtil drop‑shadow ger djup. Vi **sätter skuggfärgen** till en mellangrå, justerar dess oskärpa och förskjuter den några punkter både horisontellt och vertikalt.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Varför detta är viktigt:** En skugga som är för skarp eller för mörk kan se ut som ett tryckfel. Justera `Blur` och `Transparency` tills den känns naturlig.

## Steg 5: Spara Word‑dokumentet

Till sist **sparar vi Word‑dokumentet** till disk. Metoden `Save` bestämmer automatiskt filformatet utifrån filändelsen; `.docx` är det moderna OpenXML‑formatet.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Om mappen inte finns kommer Aspose.Words att kasta ett `ArgumentException`. Se till att sökvägen är giltig eller skapa katalogen i förväg.

## Fullt fungerande exempel

Nedan är det kompletta, körklara programmet som samlar alla stegen. Kopiera detta till ett nytt konsolprojekt och tryck **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Förväntat resultat

Öppna `ShadowRectangle.docx` i Microsoft Word. Du bör se en ljusgrå rektangel med en mjuk, lätt förskjuten skugga, båda renderade med 40 % transparens. Formen ligger på en tom sida, redo för ytterligare innehåll.

## Vanliga frågor & variationer

**Vad händer om jag behöver en annan form?**  
Byt ut `ShapeType.Rectangle` mot någon annan enum‑värde (`Ellipse`, `Triangle`, `Star`, osv.). Resten av koden förblir densamma.

**Kan jag ändra konturfärgen?**  
Ja – använd `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` och eventuellt sätt `rectangleShape.StrokeWeight = 1.5;`.

**Hur placerar jag formen på en specifik plats på sidan?**  
Sätt `rectangleShape.WrapType = WrapType.None;` och justera sedan `rectangleShape.Left` och `rectangleShape.Top` (värdena är i punkter).

**Är det möjligt att lägga till text i rektangeln?**  
Absolut. Efter att ha skapat formen kan du anropa `rectangleShape.AppendChild(new Paragraph(document))` och sedan lägga till ett `Run` med din text. Kom ihåg att sätta `rectangleShape.TextBox`‑egenskaper om du vill ha rikare formatering.

## Proffstips & fallgropar

- **Licensiera tidigt:** Om du glömmer att applicera en licens kommer Aspose.Words att infoga ett vattenmärke på första sidan, vilket kan vara förvirrande under testning.
- **Prestandatips:** När du genererar många dokument i en loop, återanvänd en enda `Document`‑instans och anropa `document.RemoveAllChildren();` efter varje sparning för att undvika onödig GC‑belastning.
- **Skuggans synlighet:** På lågupplösta skärmar kan en subtil skugga verka osynlig. Öka `Blur` eller `OffsetX/Y` för felsökning, och minska sedan igen för produktion.

## Nästa steg

Nu när du vet hur du **skapar rektangelform**, **ställer in formens transparens**, **sätter skuggfärg** och **sparar Word‑dokument**, kan du utöka handledningen:

- Lägg till flera former och gruppera dem.
- Infoga rektangeln i en tabellcell för en rapportlayout.
- Kombinera formen med `DocumentBuilder.InsertHtml` för att överlagra HTML‑formaterat innehåll.
- Utforska andra visuella effekter som `Glow` eller `Reflection` för rikare UI‑liknande dokument.

Experimentera, bryt saker, och förbättra sedan – programmatisk dokumentgenerering är en lekplats där visuell design möter kod.

---

*Lycka till med kodandet! Om du stöter på problem, lämna en kommentar nedan så hjälper vi dig att felsöka tillsammans.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}