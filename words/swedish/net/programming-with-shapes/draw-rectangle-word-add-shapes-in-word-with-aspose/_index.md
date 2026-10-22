---
category: general
date: 2026-07-29
description: Rita en rektangel i Word med Aspose.Words. Lär dig hur du lägger till
  en rektangelform, lägger till en linjeform och hanterar flera former i ett enda
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: sv
lastmod: 2026-07-29
og_description: rita rektangel i Word med Aspose.Words. Följ den här steg‑för‑steg‑guiden
  för att lägga till en rektangel, lägga till en linje och arbeta med flera former
  i Word utan ansträngning.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: rita rektangel i Word – Mästra att lägga till former i Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: rita rektangel i Word – Lägg till former i Word med Aspose
url: /sv/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Komplett guide för att lägga till former i Word

Har du någonsin undrat hur man **draw rectangle word** dokument utan att öppna UI varje gång? Du är inte ensam. Många utvecklare behöver generera Word‑filer i farten, och det enklaste sättet är att låta ett bibliotek göra det tunga arbetet. I den här handledningen visar vi exakt **how to add shapes**—specifikt en rektangel och en linje—med Aspose.Words för .NET, och vi håller fokus på frasen *draw rectangle word* så att du aldrig går vilse.

Tänk på det som en mini‑konststudio som lever i din kod. I slutet kommer du att kunna **add rectangle shape**, **add line shape**, och till och med kombinera dem till **multiple shapes word**‑grupper. Inget UI, ingen manuell hackning, bara ren, repeterbar C#.

## Vad du kommer att lära dig

- Skapa ett nytt Word‑dokument med Aspose.Words.  
- Skapa en **GroupShape** som kan hålla flera objekt.  
- **Add rectangle shape** och **add line shape** i den gruppen.  
- Infoga de grupperade formerna i dokumentets kropp.  
- Spara filen och se resultatet omedelbart.  

Om du är bekväm med grundläggande C# och har en kopia av Aspose.Words, är du redo. Inga extra NuGet‑paket utöver kärnbiblioteket behövs.

> **Pro tip:** Aspose.Words fungerar med .NET 6, .NET 7 och .NET Framework 4.6+. Välj den runtime som matchar ditt projekt.

![draw rectangle word exempel](https://example.com/placeholder-image.png "draw rectangle word – grupperade former i en Word‑fil")

## draw rectangle word – Ställa in dokumentet

Innan vi kan **draw rectangle word** behöver vi en ren duk. Klassen `Document` är den duken; `DocumentBuilder` är vår pensel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

De två raderna ovan ger oss ett färskt, minnes‑`.docx`. Ingenting har skrivits till disk ännu, vilket betyder att vi kan experimentera utan att skräpa ner filsystemet.

## How to Add Shapes – Skapa en GroupShape‑behållare

När du vill att **multiple shapes word** ska fungera som en enhet—flytta tillsammans, rotera tillsammans—paketerar du dem i en `GroupShape`. Tänk på en grupp som en mapp som innehåller andra former.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Varför en grupp? För att du senare kanske vill **add rectangle shape** och **add line shape** och sedan flytta dem tillsammans. Utan en grupp skulle du behöva ompositionera varje form individuellt.

## add rectangle shape – Infoga en rektangel i gruppen

Nu när behållaren finns, låt oss **add rectangle shape**. En rektangel är en `Shape` vars `ShapeType` är `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Observera att värdena `Left` och `Top` är relativa till gruppens ursprung, inte sidan. Detta gör det enkelt att placera former exakt. Rektangeln kommer att visas nära gruppens övre‑vänstra hörn.

## add line shape – Lägga till en linje i samma grupp

En linje är bara en annan `Shape`, men dess `ShapeType` är `Line`. Vi placerar den under rektangeln.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Eftersom linjens höjd är noll bestämmer `Top`‑egenskapen var linjen sitter vertikalt. `Width` styr hur lång linjen sträcker sig horisontellt.

## multiple shapes word – Infoga gruppen i dokumentets kropp

Vi har en grupp som nu innehåller **add rectangle shape** och **add line shape**. Det sista steget är att släppa hela grejen i dokumentet.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` placerar gruppen exakt där `DocumentBuilder` för närvarande är positionerad. Om du behöver den i ett specifikt stycke, flytta byggaren med `builder.MoveToParagraph(index)` först.

## Saving the Result – Se draw rectangle word‑utdata

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Öppna den genererade filen i Microsoft Word så ser du en enda grupp som innehåller en rektangel och en linje. Du kan klicka på gruppen, dra den runt, eller till och med ändra storlek—alla formerna flyttar sig tillsammans. Det är kraften i **multiple shapes word**.

### Förväntat resultat

- En `.docx`‑fil med namnet `GroupShape.docx`.  
- En sida med en grupperad rektangel (120 × 80 pt) nära övre‑vänstra hörnet.  
- En horisontell linje (150 pt lång) placerad precis under rektangeln.  
- Båda formerna kan väljas som ett enda objekt.

Om du dubbelklickar på gruppen låter Word dig redigera varje form individuellt—perfekt för finjustering.

## Vanliga frågor & specialfall

**Vad händer om jag behöver mer än två former?**  
Fortsätt bara anropa `group.AppendChild(yourShape)` för varje ytterligare objekt. Gruppen kan hålla valfritt antal former, vilket gör den idealisk för komplexa diagram.

**Kan jag ändra fyllningsfärgen på rektangeln?**  
Absolut. Efter att ha skapat rektangeln, sätt `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Detta fungerar för alla former som stödjer fyllning.

**Måste jag sätta `Height = 0` för en linje?**  
Ja, för en rak horisontell linje bör höjden vara noll. För en vertikal linje, sätt `Width = 0` och ge `Height` ett positivt värde.

**Fungerar detta med .doc‑filer (Word 97‑2003)?**  
Aspose.Words kan spara till det äldre `.doc`‑formatet, men vissa moderna formfunktioner kan vara begränsade. Håll dig till `.docx` för fullständig trohet.

**Hur roterar jag hela gruppen?**  
Du kan sätta `group.Rotation = 45;` (grader) innan du infogar den. Rotationen gäller för varje underordnad form.

## Sammanfattning – Hur man lägger till former i Word programatiskt

- **draw rectangle word** börjar med att skapa ett `Document` och `DocumentBuilder`.  
- Bygg en **GroupShape** för att hålla **multiple shapes word**.  
- **add rectangle shape** och **add line shape** läggs till i gruppen.  
- Infoga gruppen i kroppen med `builder.InsertNode`.  
- Spara filen och öppna den för att verifiera det visuella resultatet.

Det är hela arbetsflödet, inbäddat i en enda, lättläst kodlista.

## Nästa steg & relaterade ämnen

Nu när du vet **how to add shapes**, överväg att utforska:

- **add rectangle shape** med rundade hörn (`ShapeType.Rectangle` + `CornerRadius`).  
- Styla linjer med olika streckmönster (`line.LineFormat.DashStyle`).  
- Bädda in bilder tillsammans med former för rikare rapporter.  
- Använda **multiple shapes word** för att bygga flödesscheman eller enkla UML‑diagram.  

Varje av dessa ämnen bygger naturligt på den grund vi lagt ut här, och de följer alla samma mönster: skapa former, konfigurera dem och gruppera dem om det behövs.

---

Lycka till med kodningen! Om du stöter på problem eller har ett coolt användningsfall att dela, lämna en kommentar nedan. Din feedback hjälper oss alla att bemästra konsten med **draw rectangle word** och mer.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangel‑form i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa rektangel‑form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}