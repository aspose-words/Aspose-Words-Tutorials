---
category: general
date: 2026-09-08
description: Lär dig hur du skapar ett tomt Word‑dokument, infogar en rektangel och
  grupperar flera former med C#. Följ den här steg‑för‑steg‑guiden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: sv
lastmod: 2026-09-08
og_description: Skapa ett tomt Word-dokument, infoga en rektangelform och gruppera
  flera former i C#. Den här handledningen guidar dig genom hela processen.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Skapa ett tomt Word‑dokument med grupperade former i C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hur man skapar ett tomt Word‑dokument med grupperade former
url: /sv/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word-dokument med grupperade former

Om du behöver **skapa ett tomt Word-dokument** som innehåller anpassade grafik, visar den här guiden exakt hur du gör. Du kommer att lära dig att **infoga rektangelform**, **gruppa flera former** och **lägga till former i gruppen** med Aspose.Words för .NET.

Ett tomt dokument ger dig en ren canvas, och att gruppera former låter dig flytta, ändra storlek eller rotera dem som en enhet. Denna handledning täcker varje steg—från att initiera dokumentet till att spara den slutliga filen—så att du kan kopiera koden till ditt eget projekt och se omedelbara resultat.

## Vad du behöver

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
* En giltig Aspose.Words för .NET-licens (den kostnadsfria utvärderingen fungerar för testning)
* En IDE som Visual Studio 2022 eller Visual Studio Code
* Grundläggande kunskap om C#-syntax

Inga ytterligare NuGet-paket krävs utöver `Aspose.Words`.

## Hur man skapar ett tomt Word-dokument

Det första steget är att instansiera ett `Document`-objekt. Detta objekt representerar en tom `.docx`-fil som du kan redigera med en `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`-konstruktorn skapar ett **tomt Word-dokument** i minnet. `DocumentBuilder` tillhandahåller ett flytande API för att infoga text, bilder och ritobjekt.

## Infoga rektangelform i dokumentet

Nästa steg, lägg till en rektangelform. Rektangeln kommer att vara det första barnet i gruppen som vi skapar senare.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Att anropa `InsertShape` med `ShapeType.Rectangle` **infogar en rektangelform** vid den aktuella markörpositionen. Bredden och höjden anges i punkter (1 pt ≈ 1/72 tum).

## Gruppera flera former tillsammans

En `GroupShape` fungerar som en behållare. Alla barnformer i gruppen flyttas och transformeras tillsammans. Skapa först gruppen, och lägg sedan till rektangeln vi just byggde.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape`-metoden placerar en tom grupp vid builderns markör. Genom att lägga till rektangeln **grupperar vi flera former**—rektangeln blir en del av gruppens interna nodsamling.

## Lägg till former i gruppen och spara filen

Lägg nu till en andra form—en ellips—för att demonstrera hur flera objekt delar samma behållare. Spara sedan dokumentet.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`InsertShape`-anropet **lägger till former i gruppen** när du lägger till den returnerade `Shape` till `GroupShape`. Att spara `Document` skriver en `.docx`-fil som du kan öppna i Microsoft Word, LibreOffice eller någon kompatibel visare.

### Förväntat resultat

När du öppnar *GroupShapeDemo.docx* kommer du att se en tom sida med ett grupperat objekt som innehåller en ljusblå rektangel och en rosa ellips. Att markera gruppen låter dig flytta båda formerna tillsammans, vilket bekräftar att **gruppera flera former** fungerade som avsett.

## Varför använda en GroupShape?

* **Atomära transformationer** – Skalning, rotation eller förflyttning av gruppen påverkar alla barn lika.
* **Logisk organisering** – Håller relaterad grafik tillsammans, vilket gör dokumentstrukturen enklare att underhålla.
* **Prestanda** – Rendering av en enda behållare är ofta snabbare än att hantera många oberoende former.

Om du senare behöver ändra ett enskilt barn kan du hämta det från `group.ChildNodes` via index eller via dess `Name`-egenskap.

## Vanliga variationer och kantfall

| Scenario                                 | Hur du anpassar koden                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Olika formtyper**                | Byt ut `ShapeType.Rectangle` eller `ShapeType.Ellipse` mot någon annan `ShapeType` |
| **Lägga till text i en form**           | Använd `Shape.TextPath.Text = "Hello"` efter att ha infogat formen                    |
| **Ställa in rotationsvinkel**             | `group.Rotation = 45;` (degrees)                                                 |
| **Spara som PDF istället för DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Applicera en kantlinje på gruppen**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Pro‑tips

* **Namnge dina former** – `rectangle.Name = "MyRect";` gör det enklare att hitta dem senare.
* **Använd relativ positionering** – Ställ in `group.RelativeHorizontalPosition` till `RelativeHorizontalPosition.Page` om du vill att gruppen ska förbli förankrad till sidmarginalerna.
* **Frigör resurser** – Omge `Document` med ett `using`-block när du arbetar i större applikationer för att snabbt frigöra ohanterat minne.

## Fullständig källkod för snabb kopiera‑klistra

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kopiera koden till ett nytt konsolprojekt, återställ `Aspose.Words` NuGet-paketet och kör. Utdatafilen visas i projektets `bin/Debug/net6.0` (eller motsvarande) mapp.

## Nästa steg

Nu när du kan **skapa ett tomt Word-dokument**, **infoga rektangelform**, och **gruppa flera former**, kan du utforska:

* Lägga till **textrutor** i en grupp för att skapa märkta diagram.
* Exportera den grupperade grafiken till en bild med `doc.Save("image.png", SaveFormat.Png)`.
* Kombinera grupper med tabeller för rikligt formaterade rapporter.

Experimentera med olika formegenskaper, grupphierarkier och exportformat för att fullt utnyttja Aspose.Words ritningsfunktioner.

--- 

*Kom ihåg*: att gruppera former är ett kraftfullt sätt att hålla dina Word-dokument organiserade och din kod underhållbar. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Infoga former i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}