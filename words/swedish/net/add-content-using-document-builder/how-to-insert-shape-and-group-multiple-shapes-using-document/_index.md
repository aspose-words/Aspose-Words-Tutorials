---
category: general
date: 2026-11-15
description: Lär dig hur du infogar en form i ett Word‑dokument och grupperar flera
  former med Aspose.Words DocumentBuilder. Inkluderar exempel på att infoga en rektangel
  och att infoga flera former.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: sv
lastmod: 2026-11-15
og_description: Hur man infogar en form i en Word‑fil med Aspose.Words. Denna guide
  täcker gruppering av flera former, infogning av rektangelform och att lägga till
  flera former effektivt.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Hur man infogar en form och grupperar flera former med DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Hur man infogar en form och grupperar flera former med DocumentBuilder i C#
url: /sv/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar form och grupperar flera former med DocumentBuilder i C#

Om du behöver veta **how to insert shape** i ett Word‑dokument med Aspose.Words, visar den här guiden de exakta stegen. Du kommer också att lära dig hur du **group multiple shapes** så att de beter sig som ett enda objekt, och hur du **insert rectangle shape** tillsammans med annan grafik.

Dokumentautomatisering kräver ofta att man lägger till flera grafik‑element—diagram, logotyper, förklarande rutor—och samtidigt håller dem organiserade. I slutet av den här handledningen kommer du att kunna **insert multiple shapes**, placera dem i en grupp och spara en ren, återanvändbar layout.

## Förutsättningar

* .NET 6.0 eller senare installerat  
* Visual Studio 2022 (eller någon C#‑IDE)  
* En Aspose.Words för .NET‑licens eller en gratis utvärderingsnyckel  
* Grundläggande kunskap om C# och Aspose.Words `DocumentBuilder`‑klassen  

Du behöver **inte** några andra tredjepartsbibliotek; allt som behövs är en del av Aspose.Words.

## Steg 1: Installera Aspose.Words via NuGet

Öppna ditt projekt i Visual Studio och kör följande kommando i Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Paketet innehåller klasserna `DocumentBuilder`, `Shape` och `GroupShape` som används i hela den här handledningen.

## Steg 2: Skapa en DocumentBuilder‑instans – grunden för **how to insert shape**

Den första handlingsbara kodraden är att skapa en `DocumentBuilder`. Detta objekt ger dig direkt åtkomst till dokumentträdet, så att du kan placera former exakt där du vill ha dem.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Varför detta är viktigt*: `DocumentBuilder` håller ett markör (”infogningspunkten”). Varje efterföljande `Insert...`‑anrop använder den markören, vilket är anledningen till att vi senare flyttar den in i en `GroupShape` för att hålla alla former tillsammans.

## Steg 3: **Insert rectangle shape** – den första grafiken du kommer att lägga till

En rektangel är en vanlig platshållare för tabeller, bilder eller förklarande rutor. Använd `InsertShape` med `ShapeType.Rectangle` och ange bredd och höjd i punkter (1 pt ≈ 1/72 tum).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Rektangeln visas på den aktuella markörens plats. Du kan anpassa dess fyllning, linjestil eller text senare om så behövs.

## Steg 4: Infoga en annan form – en ellips för visuell variation

Att lägga till mer än en form demonstrerar **insert multiple shapes**. Ellipsen kommer att placeras efter rektangeln i dokumentflödet.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Vid detta tillfälle innehåller dokumentet två oberoende former. Om du flyttar markören eller lägger till text, förblir formerna där de infördes.

## Steg 5: **Group multiple shapes** så att de fungerar som en enhet

Gruppering är avgörande när du behöver flytta, rotera eller formatera flera grafik‑element tillsammans. Följande kod skapar en `GroupShape`, flyttar builderns markör inuti den och infogar sedan samma former igen—denna gång blir de barn till gruppen.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Varför använda en grupp?

* **En‑punktstransformation** – rotera eller ändra storlek på hela gruppen med ett anrop.  
* **Logisk organisering** – Word‑dokumentträdet speglar gruppering, vilket gör senare redigeringar enklare.  
* **Konsistent layout** – att flytta gruppen behåller de relativa positionerna för dess barn intakta.

### Lägg till fler former – utöka **insert multiple shapes** i gruppen

Du kan fortsätta anropa `InsertShape` medan markören är kvar inne i `GroupShape`. Till exempel, för att lägga till en triangel:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Varje anrop respekterar gruppkontexten, så triangeln blir automatiskt en del av samma grupperade uppsättning.

## Steg 6: Spara dokumentet och verifiera resultatet

När alla former har placerats, sparas dokumentet till en `.docx`‑fil. När du öppnar filen i Microsoft Word (eller någon kompatibel visare) bör du se två separata former följda av en grupperad uppsättning som innehåller samma rektangel, ellips och triangel.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Förväntat resultat

* **De två första formerna** – en rektangel och en ellips placerade oberoende på sidan.  
* **Grupperad block** – en rektangel, en ellips och en triangel som rör sig tillsammans när du klickar på någon av dem i Word.

Du kan testa gruppering genom att markera någon form i gruppen; Word kommer att markera hela samlingen, vilket bekräftar att **group multiple shapes**‑operationen lyckades.

## Vanliga fallgropar och pro‑tips

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| Shapes appear outside the intended page | The builder’s cursor was not moved into the `GroupShape` before inserting. | Always call `builder.MoveTo(group)` **before** any `InsertShape` calls that belong to the group. |
| Group disappears after saving | The group was inserted without being added to the document’s node collection. | Use `builder.InsertNode(group)` immediately after creating the `GroupShape`. |
| Unexpected size because of document DPI | Aspose.Words uses points; if you think in pixels you may get mismatched dimensions. | Convert pixels to points (`points = pixels * 72 / 96`) or work directly in points. |
| Shapes overlap unintentionally | No explicit positioning was set; Word places them sequentially. | Set `Shape.Left` and `Shape.Top` after insertion to control exact placement. |

**Pro‑tips:** Efter gruppering kan du hämta gruppens `Shapes`‑samling (`group.Shapes`) för att iterera, byta namn eller tillämpa massformatering.

## Steg 7: Utöka exemplet – vad kommer härnäst?

Nu när du vet **how to insert shape**, **insert rectangle shape** och **group multiple shapes**, kan du utforska:

* **Animera grupperade former** – ange rotations‑ eller vändnings‑egenskaper på gruppen.  
* **Applicera stilar** – använd `Shape.FillColor`, `Shape.LineFormat` eller `Shape.TextBox` för att lägga till etiketter.  
* **Exportera till PDF** – samma grupperade layout renderas korrekt när du anropar `doc.Save("output.pdf")`.  

Alla dessa tillägg återanvänder samma `DocumentBuilder`‑arbetsflöde, vilket håller din kod ren och underhållbar.

## Slutsats

Denna handledning demonstrerade **how to insert shape** i ett Word‑dokument med Aspose.Words, hur man **insert rectangle shape**, och hur man **group multiple shapes** så att de beter sig som ett enda objekt. Genom att följa den steg‑för‑steg‑koden kan du på ett pålitligt sätt **insert multiple shapes**, organisera dem i grupper och programatiskt producera professionella dokument.

Känn dig fri att experimentera med olika formtyper, färger och grupptransformationer. När du är redo, integrera mönstret i större rapporterings‑ eller mallningslösningar för att automatisera komplexa dokumentlayouter. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga former i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Hur man skapar och infogar ellips‑ och rektangelformer i en gruppform i ett Word-dokument med Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Hur man grupperar former i ett Word-dokument med Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}