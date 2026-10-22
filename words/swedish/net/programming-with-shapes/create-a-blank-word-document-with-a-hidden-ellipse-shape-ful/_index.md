---
category: general
date: 2026-07-29
description: Skapa ett tomt Word‑dokument och lär dig hur du döljer en form, skapar
  ett dolt objekt och skapar en ellipsform med Aspose.Words i C#. Steg‑för‑steg‑kod
  inkluderad.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: sv
lastmod: 2026-07-29
og_description: Skapa ett tomt Word‑dokument och dölj formen omedelbart. Lär dig att
  skapa ett dolt objekt och rita en ellipsform med Aspose.Words i C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Skapa ett tomt Word-dokument med en dold ellipsform – C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Skapa ett tomt Word‑dokument med en dold ellipsform – Fullständig C#‑guide
url: /sv/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument med en dold ellipsform – Fullständig C#-guide

Har du någonsin behövt skapa ett **tomt Word-dokument** och sedan dölja en form i det? Kanske genererar du en mall där vissa markörer måste förbli osynliga tills ett senare steg. I den här handledningen går vi igenom exakt **hur man döljer en form**, hur man **skapar ett dolt objekt**, och till och med hur man **skapar en ellipsform** med Aspose.Words för .NET. I slutet har du ett färdigt C#‑snutt som producerar en DOCX‑fil som innehåller en osynlig ellips.

## Vad du kommer att lära dig

- Initiera ett nytt tomt Word-dokument med Aspose.Words.  
- Skapa en ellipsform, ange dess dimensioner och placera den på sidan.  
- Markera formen som dold så att den aldrig visas på skärmen eller i utskrift.  
- Spara resultatet till disk och verifiera att det dolda objektet verkligen är osynligt.  

Inga externa bibliotek utöver Aspose.Words krävs, och koden fungerar med version 24.10 eller nyare (egenskapen `Hidden` introducerades i den releasen). Låt oss komma igång.

![Diagram av en dold ellips i ett tomt Word-dokument](https://example.com/hidden-ellipse.png "Dold ellipsform infogad i ett tomt Word-dokument")

## Skapa ett tomt Word-dokument och infoga en dold ellipsform

Det första steget är att skapa ett helt nytt dokument. Tänk på `Document` som en tom duk; `DocumentBuilder` är din pensel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Varför börja med ett tomt dokument?**  
> En ren start garanterar att inget befintligt innehåll stör den dolda formen du ska lägga till. Det gör också exemplet enklare att kopiera‑klistra in i vilket projekt som helst.

## Så döljer du en form: Ställ in egenskapen Hidden

Aspose.Words 24.10 introducerade `Hidden`‑flaggan på `Shape`. När den är satt till `true` behandlar Word formen som en kommentar—helt osynlig i användargränssnittet och vid utskrift.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Proffstips:** Om du senare behöver avslöja formen programatiskt, växla helt enkelt `ellipseShape.Hidden = false;` och spara dokumentet igen.

## Skapa dolt objekt: Infoga formen i dokumentet

Nu när ellipsen är förberedd och dold, infogar vi den på builderns aktuella markörposition. Builderns position är som standard i början av det första stycket, vilket är perfekt för ett tomt dokument.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Vad händer om du behöver formen på en specifik sida?**  
> Flytta buildern till önskad sida först (`builder.MoveToDocumentEnd();` eller `builder.MoveToPage(pageNumber);`) innan du anropar `InsertNode`.

## Spara dokumentet som innehåller den dolda formen

Till sist skriver vi filen till disk. Resultatet blir en standard‑DOCX som vilken ordbehandlare som helst kan öppna—förutom att ellipsen förblir osynlig.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Förväntat resultat:** Öppna `HiddenShape.docx` i Microsoft Word. Du kommer inte att se några grafik, men filstorleken blir något större än ett helt tomt dokument eftersom den dolda ellipsen lagras i XML‑filen.

## Verifiera den dolda ellipsen programatiskt (valfritt)

Om du vill dubbelkolla att formen verkligen är dold kan du läsa in den sparade filen och inspektera formens `Hidden`‑egenskap:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Att köra detta kodstycke skriver ut `True`, vilket bekräftar att det dolda objektet överlevde spara‑läs‑cykeln.

## Kantfall och vanliga frågor

### Vad händer om mål‑Word‑versionen inte stödjer dolda former?

`Hidden`‑flaggan är en del av Office Open XML‑specifikationen och respekteras av Word 2007+ och LibreOffice. Äldre format (t.ex. `.doc`) ignorerar flaggan, så spara alltid som `.docx` när du behöver pålitlig dold funktion.

### Kan jag dölja andra typer av objekt (bilder, tabeller)?

Ja. Alla noder som är avledda från `Shape`—inklusive bilder, textrutor och till och med SmartArt—exponerar `Hidden`‑egenskapen. Sätt den bara till `true` innan infogning.

### Påverkar dold form dokumentets prestanda?

Obetydligt. Formen lagras som XML‑markup, och Word hoppar över rendering av dolda objekt under layouten. Om du bäddar in många dolda objekt ökar filstorleken, men rendering förblir snabb.

### Hur skiljer sig detta från att använda ett bokmärke eller en kommentar som markör?

Bokmärken är osynliga av design, men de är avsedda för navigering, inte visuella platshållare. Kommentarer visas i marginalen. En dold form ger dig ett visuellt objekt (storlek, position) som du senare kan avslöja eller manipulera, vilket är praktiskt i mallscenarier.

## Fullständigt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Det innehåller alla using‑direktiv, skapandet av den dolda ellipsen och ett verifieringssteg.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

När programmet körs skapas `HiddenEllipse.docx` i körningsmappen. Öppna den—du ser en helt vanlig tom sida, men den dolda ellipsen lever tyst inuti.

## Sammanfattning

Vi har gått igenom hur man **skapar ett tomt Word‑dokument**, **döljer en form**, **skapar ett dolt objekt**, och **skapar en ellipsform** med bara några få C#‑rader. Den viktigaste insikten är `Hidden`‑egenskapen på `Shape`, som förvandlar vilket visuellt element som helst till en osynlig markör utan att bryta Word‑kompatibiliteten.

## Vad blir nästa steg?

- **Styla den dolda formen** (fyllningsfärg, linjestil) så att den ser exakt ut som avsett när du senare avslöjar den.  
- **Kombinera dolda former med bokmärken** för att bygga dynamiska mallar som kan slås på eller av.  
- **Utforska andra formtyper**—rektanglar, pilar eller till och med anpassade SVG‑vägar—genom att byta `ShapeType.Ellipse`.  

Känn dig fri att experimentera: ändra storleken, flytta positionen eller infoga flera dolda ellipser. Samma mönster fungerar för vilken Aspose.Words‑form som helst som du vill hålla dold.

Om du stöter på problem eller har idéer för att utöka detta mönster, lämna en kommentar nedanför. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa tomt Word-dokument med skuggad rektangel‑form – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangel‑form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}