---
category: general
date: 2026-10-26
description: Skapa ett tomt Word‑dokument i C# och lär dig hur du infogar en gruppform,
  sedan lägger du till en rektangelform i gruppen. Denna guide täcker hur du grupperar
  flera former steg för steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: sv
lastmod: 2026-10-26
og_description: Skapa ett tomt Word‑dokument i C# och se hur du infogar en grupp,
  sedan lägger till en rektangel. Bemästra gruppering av flera former med ett komplett
  kodexempel.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Skapa ett tomt Word‑dokument och gruppera flera former – C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man skapar ett tomt Word‑dokument och grupperar flera former
url: /sv/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word-dokument och grupperar flera former

Om du behöver **create blank Word document** programatiskt, visar den här handledningen exakt hur. Du kommer att se hur du infogar en gruppform, sedan **add rectangle** till den gruppen, vilket täcker hela arbetsflödet från ett tomt dokument till en grupperad ritning.

Att arbeta med Word-filer innebär ofta att arrangera flera ritningar tillsammans — tänk på ett diagram gjort av flera former. I slutet av den här guiden kommer du att kunna **group multiple shapes**, infoga en **rectangle shape**, och förstå **how to insert group** och **how to add rectangle** på ett rent, återanvändbart sätt.

## Vad du behöver

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
* **Aspose.Words for .NET** NuGet‑paket (`Install-Package Aspose.Words`)
* Grundläggande förståelse för C# och Visual Studio‑IDE:n (alla IDE:er fungerar)

> **Pro tip:** Aspose.Words körs helt offline; du behöver ingen internetanslutning efter att paketet har installerats.

## Steg 1: Skapa ett tomt Word-dokument

Den första operationen är att instansiera ett tomt `Document`‑objekt. Detta objekt representerar det **blank Word document** som du senare kommer att berika med former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt:* Ett `Document` utan några sektioner eller stycken är fortfarande en giltig .docx‑fil. Att börja från ett rent blad garanterar att ingen dold formatering stör de former du kommer att lägga till senare.

## Steg 2: Infoga en gruppform (how to insert group)

En **group shape** fungerar som en behållare som kan hålla andra ritningsobjekt. I Aspose.Words skapar du den med `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Varför använda en grupp?* Gruppering låter dig flytta, rotera eller ändra storlek på flera former som en enhet. Detta är avgörande för diagram där element måste förbli justerade.

## Steg 3: Infoga en rektangelform (insert rectangle shape)

Lägg nu till en rektangel i dokumentet. Metoden `InsertShape` returnerar ett `Shape`‑objekt som du senare kan fästa på gruppen.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Varför en rektangel?* Rektanglar är den vanligaste byggstenen för flödesscheman, UI‑mock‑ups och platshållargrafik. Dimensionerna uttrycks i punkter (1 pt ≈ 1/72 tum).

## Steg 4: Lägg till rektangeln i gruppen (how to add rectangle)

En form skapad med `InsertShape` finns direkt i dokumentkroppen. För att göra den till en del av gruppen, anropa `AppendChild` på `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Vad händer under huven?* `AppendChild` flyttar rektangelns nod från dokumentets huvudberättelse till gruppens interna samling, och bevarar dess storlek och position i förhållande till gruppens ursprung.

## Steg 5: Spara dokumentet

Slutligen skriver du filen till disk. Du kan öppna den resulterande `.docx` i Microsoft Word för att se den grupperade rektangeln.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Edge case:** Om du avser att lägga till fler former (t.ex. cirklar, linjer) till samma grupp, upprepa **Step 3** och **Step 4** för varje ny form innan du sparar. Gruppen kommer automatiskt att justera sin omgivande ruta för att omfatta alla barn.

## Så grupperar du flera former – utöka exemplet

Nedan är ett snabbt kodsnutt som lägger till en andra form (en ellips) till samma grupp, vilket demonstrerar **group multiple shapes** i ett enda dokument.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

När du öppnar `GroupedShapeExample.docx` kommer du att se rektangeln och ellipsen röra sig tillsammans när du markerar gruppen i Word.

## Vanliga frågor och felsökning

| Question | Answer |
|----------|--------|
| **Behöver jag en licens för Aspose.Words?** | En gratis utvärdering fungerar utan licens, men den lägger till ett vattenmärke. För produktion, tillämpa en licens för att ta bort vattenmärket och låsa upp full prestanda. |
| **Kan jag placera former exakt?** | Ja. Efter att ha infogat en form kan du sätta egenskaperna `Shape.Left`, `Shape.Top`, `Shape.Width` och `Shape.Height`. |
| **Vad händer om rektangeln försvinner efter sparning?** | Se till att du anropar `group.AppendChild(rectangle)` *efter* att ha infogat rektangeln. Att först lägga till formen i dokumentkroppen och sedan flytta den till gruppen är obligatoriskt. |
| **Är det möjligt att gruppera former över olika sektioner?** | Nej. Alla former i en grupp måste tillhöra samma berättelse (sektion). Skapa separata grupper per sektion om det behövs. |

## Sammanfattning

Du vet nu hur du **create blank Word document**, **insert group**, **add rectangle** och **group multiple shapes** med Aspose.Words för .NET. Det kompletta, körbara exemplet ovan kan kopieras in i en konsolapp och köras omedelbart.

## Nästa steg

* Experimentera med storlekar och färger för **insert rectangle shape** (`rectangle.FillColor = Color.LightBlue;`).  
* Utforska andra formtyper (`ShapeType.Polygon`, `ShapeType.Line`) för att berika dina diagram.  
* Lär dig hur du konverterar den slutgiltiga `.docx` till PDF (`doc.Save("output.pdf");`) för distribution.  
* Gå djupare på **how to add rectangle** i befintliga dokument som redan innehåller text — använd `DocumentBuilder.MoveTo` för att placera gruppen där du behöver den.

Känn dig fri att anpassa koden för dina egna rapporterings- eller diagramgenereringsbehov. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar ett tomt Word-dokument och grupperar former i C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Hur man grupperar former i Word och lägger till former i Word-dokument](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Hur man skapar en rektangelform och grupperar former i Word med Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}