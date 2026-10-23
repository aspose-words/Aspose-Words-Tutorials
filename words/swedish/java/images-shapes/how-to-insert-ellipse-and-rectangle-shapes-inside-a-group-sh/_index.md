---
category: general
date: 2026-10-23
description: Lär dig hur du infogar en ellips och hur du lägger till en rektangel
  i Word med Aspose.Words. Inkluderar att flytta markören till formen och hur du skapar
  en gruppform.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: sv
lastmod: 2026-10-23
og_description: Hur man infogar en ellips och hur man lägger till en rektangel i Word
  med Aspose.Words. Följ en steg‑för‑steg‑guide för att flytta markören till formen
  och skapa en gruppform.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Hur man infogar ellips‑ och rektangelformer i en gruppform i Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man infogar ellips- och rektangelformer i en gruppform med Aspose.Words
url: /sv/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar ellips‑ och rektangelformer i en gruppform med Aspose.Words

Om du behöver veta **hur man infogar ellips** i ett Word‑dokument programatiskt, visar den här guiden hela processen. Du kommer också att se **hur man lägger till rektangel**‑formen, lära dig att **flytta markören till formen**, och upptäcka **hur man skapar gruppform** som innehåller flera ritobjekt.

Word‑automatisering kräver ofta exakt placering av ritobjekt. I slutet av den här handledningen kan du generera en `.docx`‑fil som innehåller en grupperad rektangel och ellips, klar för vidare formatering eller export. Inga externa verktyg behövs förutom Aspose.Words för .NET‑biblioteket och en .NET‑utvecklingsmiljö.

## Förutsättningar

* .NET 6.0 eller senare installerat.
* Aspose.Words för .NET (NuGet‑paketet `Aspose.Words`) tillagt i ditt projekt.
* Grundläggande kunskap om C#‑syntax och Visual Studio (eller någon IDE).

Dessa krav säkerställer att koden kompileras utan ytterligare konfiguration.

## Hur man skapar gruppform i Word

En gruppform fungerar som en behållare som låter dig flytta, rotera eller formatera flera former som en enhet. Följande kod skapar en grupp med en specifik storlek (300 × 200 punkter) och förbereder dokumentet för vidare ritoperationer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Varför detta steg är viktigt*: Gruppformen definierar ett lokalt koordinatsystem. Alla former som läggs till efter att markören flyttats in i gruppen kommer att positioneras relativt gruppens ursprung, vilket gör layoutberäkningar enkla.

## Hur man lägger till rektangelform i Word

Nu när gruppen finns kan du **infoga rektangelform** i den. Rektangeln kommer att fungera som en bakgrund eller en visuell platshållare för annat innehåll.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Förklaring*: `MoveTo(group)` talar om för byggaren att den aktiva infogningspunkten är gruppformen. Utan att flytta markören skulle `InsertShape` lägga till rektangeln i dokumentets huvudkropp istället för i gruppen.

## Hur man infogar ellips

Med rektangeln på plats kan du nu demonstrera **hur man infogar ellips**. Ellipsen kommer att centreras inom samma grupp och överlappa rektangeln om så önskas.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Varför markören måste flyttas*: Varje anrop till `InsertShape` följer den aktuella markörens position. Att återanropa `MoveTo(group)` garanterar att ellipsen också blir ett barn till gruppen, vilket bevarar den avsedda hierarkin.

## Flytta markören till formen innan du infogar ytterligare objekt

Om du behöver lägga till fler former senare, **flytta alltid markören till formen** före varje infogning. Detta mönster undviker oavsiktlig placering utanför gruppen.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tips*: Återanvändning av `MoveTo(group)` är enkelt och förbättrar kodläsbarheten. Det gör också framtida underhåll enklare eftersom infogningskontexten är explicit.

## Spara dokumentet

Till sist sparas dokumentet till disk. Exemplet sparar filen som `GroupShape.docx` i en mapp du anger.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

När du öppnar den sparade filen i Microsoft Word kommer du att se en enda grupp som innehåller en rektangel och en ellips, båda korrekt placerade.

### Förväntat resultat

* En `.docx`‑fil med namnet `GroupShape.docx`.
* I dokumentet, ett grupperat ritobjekt med storleken 300 × 200 punkter.
* Inom gruppen:
  * En rektangel (100 × 50 punkter) placerad vid gruppens ursprung.
  * En ellips (80 × 80 punkter) som överlappar rektangeln.
  * Eventuella ytterligare former du lade till efter att ha flyttat markören.

## Vanliga variationer och kantfall

| Situation | Rekommenderat tillvägagångssätt |
|-----------|---------------------------------|
| **Olika enhetsstorlekar** | Aspose.Words använder punkter (1 pt = 1/72 tum). Konvertera centimeter eller tum till punkter innan du anropar `InsertShape`. |
| **Rotera former i gruppen** | Efter att en form har infogats, hämta dess `ShapeBase`‑objekt och sätt `ShapeBase.RotationAngle`. |
| **Lägga till text i en form** | Använd `ShapeBase.AppendChild(new Paragraph(document))` och lägg sedan till ett `Run` med önskad text. |
| **Spara till PDF istället för DOCX** | Anropa `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – grupphierarkin bevaras i PDF‑utdata. |

Dessa variationer visar att samma **hur man infogar ellips**‑logik kan anpassas för många verkliga scenarier.

## Pro‑tips

* **Återanvänd samma `DocumentBuilder`‑instans** – den minskar minnesbelastningen och håller dokumentets tillstånd konsekvent.
* **Validera formens dimensioner** – extremt stora bredd‑ eller höjder kan orsaka renderingsproblem i äldre Word‑versioner.
* **Gruppera innan formatering** – att applicera fyllningsfärger eller linjestilar på gruppen efter att alla barn har lagts till säkerställer enhetligt utseende.

## Slutsats

Du förstår nu **hur man infogar ellips** och **hur man lägger till rektangel**‑formen i en grupperad behållare i ett Word‑dokument med Aspose.Words. Genom att konsekvent **flytta markören till formen** före varje infogning behåller du en ren hierarki och undviker oavsiktlig placering. Det kompletta exemplet kompileras, körs och producerar en grupperad form som kan anpassas ytterligare eller exporteras.

Redo att utforska mer? Prova att kombinera denna teknik med **hur man skapar gruppform** för komplexa diagram, eller experimentera med **infoga rektangelform i Word** tillsammans med textrutor för rik rapportgenerering. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar rektangelform och gruppformer i Word med Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Hur man skapar ett tomt Word‑dokument och lägger till en dold ellipsform i C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Hur man skapar gruppform‑docx och lägger till interaktiva kontroller i C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}