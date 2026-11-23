---
category: general
date: 2026-11-22
description: Programmera fram ett Word‑dokument i C# och infoga en rektangel, infoga
  flera former och skriva former till Word med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: sv
lastmod: 2026-11-22
og_description: Skapa ett Word-dokument programatiskt i C# genom att infoga en rektangelform,
  infoga flera former och skriva former till Word med Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Skapa Word-dokument med former programatiskt i C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Skapa Word-dokument med former programatiskt i C#
url: /sv/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt med former i C#

Om du behöver **programatiskt skapa ett Word-dokument** som innehåller anpassade grafik, visar den här guiden hur du gör det med Aspose.Words för .NET. Du kommer att lära dig att infoga en rektangel, lägga till ytterligare former, gruppera dem och slutligen skriva formerna till Word—allt i några få rader C#.

Att skapa en Word-fil med grafik kräver inte längre manuell redigering eller makroskript. I slutet av den här handledningen har du en återanvändbar metod som producerar en `.docx`-fil som innehåller en rektangel och en ellips grupperade tillsammans, redo för vidare bearbetning eller rapportering.

## Vad du behöver

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- Aspose.Words för .NET (NuGet‑paketet `Aspose.Words`)
- En IDE som Visual Studio 2022 (vilken editor som helst som kan kompilera C# fungerar)

> **Proffstips:** Installera paketet med CLI‑kommandot `dotnet add package Aspose.Words` innan du börjar koda.

## Programatiskt skapa Word-dokument – översikt

Det övergripande flödet består av tre logiska faser:

1. **Initiera** ett nytt `Document` och en `DocumentBuilder`.  
2. **Infoga flera former** (en rektangel och en ellips) och placera dem i ett `GroupShape`.  
3. **Skriv former till Word** genom att spara `Document` till en `.docx`-fil.

Varje fas är kapslad i ett dedikerat steg nedan, så att du kan kopiera‑klistra koden direkt i ditt projekt.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programatiskt skapa Word-dokument med grupperade former"}

## Steg 1: Initiera dokumentet och byggaren

`Document`‑klassen representerar hela Word‑filen, medan `DocumentBuilder` erbjuder ett flytande API för att lägga till innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt:* Att skapa `Document` först ger dig en ren arbetsyta. `DocumentBuilder` spårar den aktuella infogningspunkten, vilket är avgörande när du senare fäster former till ett stycke‑hierarki.

## Steg 2: Infoga en gruppform‑behållare

Ett `GroupShape` låter dig behandla flera enskilda former som en enhet. Detta är användbart när du vill flytta eller ändra storlek på dem tillsammans.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Förklaring:* `InsertGroupShape` infogar en tom behållare och gör den automatiskt till den aktuella formen. Alla efterföljande forminfogningar kommer att läggas till i denna behållare tills du stänger gruppen.

## Infoga rektangel

Nu lägger vi till den första grafiken—en rektangel. Detta uppfyller kravet **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Rektangeln ärver gruppens formateringskontext, så den visas inuti `GroupShape`. Du kan också senare sätta linjefärg, fyllning eller text om så behövs.

## Infoga flera former

För att demonstrera funktionen **insert multiple shapes** lägger vi till en ellips direkt efter rektangeln. Du kan fortsätta lägga till ett godtyckligt antal former (t.ex. trianglar, stjärnor) innan du stänger gruppen.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Vid detta tillfälle innehåller gruppen två distinkta former: en rektangel och en ellips. Eftersom de delar samma förälder kan du flytta dem som en enhet.

## Steg 3: Fäst gruppformen till stycke‑hierarkin

Word-dokument lagrar innehåll i ett stycketräd. För att göra gruppen synlig i den slutliga filen måste vi fästa den till det aktuella stycket.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Varför detta steg krävs:* Utan att lägga till gruppen i ett stycke existerar formerna bara i minnet och utelämnas när dokumentet sparas.

## Steg 4: Spara dokumentet – skriv former till Word

Till sist sparar vi det minnes‑`Document` till disk. Detta uppfyller målet **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `GroupShape.docx` i Microsoft Word kommer du att se en rektangel och en ellips grupperade tillsammans, exakt som koden infogade.

### Förväntat resultat

- En fil med namnet **GroupShape.docx** placerad i projektets utdata‑mapp.
- I Word‑filen: ett enda stycke som innehåller en grupperad rektangel (100 pt × 50 pt) och en ellips (80 pt × 40 pt). Att markera någon av formerna markerar hela gruppen.

## Hantera vanliga kantfall

| Situation | Rekommendation |
|-----------|----------------|
| **Olika DPI eller sidstorlek** | Ange explicit `builder.PageSetup.PaperSize` innan du infogar former för att undvika oväntad skalning. |
| **Behov av exakt placering av former** | Använd `builder.MoveTo` för att flytta infogningspunkten, sätt sedan `groupShape.Left` och `groupShape.Top`‑egenskaperna (värdena är i punkter). |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument – Infoga rektangel och skugga i C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Skapa Word-dokument programatiskt och gruppera former i C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programatiskt skapa ett Word-dokument med en gruppform](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}