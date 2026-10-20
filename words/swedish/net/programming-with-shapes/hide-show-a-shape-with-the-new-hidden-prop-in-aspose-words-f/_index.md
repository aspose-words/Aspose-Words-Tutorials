---
category: general
date: 2026-10-20
description: Dölj/visa en form med den nya `Hidden`‑egenskapen i Aspose.Words för
  C#. Lär dig hur du växlar formens synlighet, hanterar kantfall och sparar resultatet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: sv
lastmod: 2026-10-20
og_description: Dölj/visa en form med den nya `Hidden`‑egenskapen i Aspose.Words för
  C#. Bemästra växling av formens synlighet och undvik vanliga fallgropar.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Dölj/visa en form med den nya `Hidden`‑egenskapen i Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Dölj/visa en form med den nya `Hidden`‑egenskapen i Aspose.Words för C#
url: /sv/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dölj/visa en form med den nya `Hidden`‑egenskapen i Aspose.Words för C#

Om du behöver **Dölja/visa en form med den nya `Hidden`‑egenskapen** i ett Word‑dokument, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. Oavsett om du genererar rapporter, bygger mallar eller rensar upp importerade dokument, sparar programmatisk kontroll av formens synlighet dig från manuellt redigering.

I den här handledningen kommer du att lära dig hur du laddar ett dokument, hittar en form, växlar `Hidden`‑egenskapen och sparar den ändrade filen. Stegen täcker också vanliga variationer såsom hantering av flera former och hantering av inbäddade kontra flytande grafik.

## Förutsättningar

* .NET 6.0 (eller senare) installerat – Aspose.Words stöder .NET Standard 2.0 och .NET Core.
* En licensierad kopia av **Aspose.Words for .NET** (gratis provversion fungerar för utforskning).
* En IDE såsom Visual Studio 2022 eller Visual Studio Code.
* Ett Word‑dokument (`input.docx`) som innehåller minst en form (t.ex. en bild, SmartArt eller en ritnings‑canvas).

## Steg 1: Ladda Word‑dokumentet

Den första operationen är att skapa ett `Document`‑objekt som representerar .docx‑filen på disken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Varför detta steg är viktigt*: `Document` är ingångspunkten för alla Aspose.Words‑operationer. Att ladda filen i minnet ger dig full åtkomst till dess nodträd, inklusive former.

## Steg 2: Hämta målformen

För att växla synlighet måste du få en referens till form‑noden. Exemplet nedan hämtar den första formen i dokumentet, men du kan anpassa logiken för att hitta former efter namn, typ eller index.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Varför detta steg är viktigt*: `GetChild` med `true` utför en djup sökning, vilket säkerställer att du hittar former även när de är inbäddade i tabeller eller sidhuvuden. Att kontrollera `null` förhindrar ett `NullReferenceException` när dokumentet inte innehåller några former.

## Steg 3: Dölj formen med `Hidden`‑egenskapen

Aspose.Words introducerade `Hidden`‑egenskapen för att styra om en form renderas eller skrivs ut. Att sätta den till `true` döljer formen; att sätta den till `false` gör formen synlig igen.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Om du behöver **visa** en tidigare dold form, tilldela helt enkelt `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Varför detta steg är viktigt*: `Hidden`‑egenskapen fungerar för både flytande och inbäddade former, och den integreras med Words inbyggda “Hidden”-formatering. Detta tillvägagångssätt är mer pålitligt än att ta bort formen eftersom noden förblir i dokumentträdet, vilket bevarar layout och referenser.

## Steg 4: Spara det ändrade dokumentet

Efter att ha justerat synligheten, skriv tillbaka ändringarna till en ny fil (eller skriv över originalet om så önskas).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Varför detta steg är viktigt*: `Save` serialiserar det in‑minnet‑nodträdet till ett .docx‑paket som Word kan öppna. Den dolda flaggan sparas, så när du öppnar filen i Microsoft Word visas formen enligt `Hidden`‑inställningen.

## Fullt, körbart exempel

Genom att sätta ihop alla steg får du ett självständigt program som du kan kopiera, kompilera och köra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Förväntad output** när du kör programmet:

```
Document saved. Shape hidden = True
```

Att öppna `ShapeHidden.docx` i Microsoft Word visar dokumentet utan den målade formen. Om du sätter `shape.Hidden = false;` innan du sparar, visas formen igen.

## Hantera flera former

Exemplet ovan fungerar för en enda form. Verkliga dokument innehåller ofta många grafikobjekt. Använd en loop för att dölja eller visa alla former som uppfyller ett villkor (t.ex. ett specifikt namn eller typ).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tips*: Filtrering efter `ShapeType` undviker oavsiktlig döljning av dekorativa element såsom textrutor eller SmartArt.

## Kantfall och bästa praxis

| Situation | Rekommenderad hantering |
|-----------|--------------------------|
| **Formen är i ett sidhuvud/sidfot** | Hämta först sidhuvud/sidfot‑noden och anropa sedan `GetChild(NodeType.Shape, …)` på det del‑dokumentet. |
| **Dokumentet innehåller inga former** | Kontrollera alltid `null` efter `GetChild` eller verifiera `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Du behöver bevara den dolda flaggan över olika Word‑versioner** | `Hidden`‑egenskapen lagras i formens XML som `<w:hidden/>`, vilket stöds av Word 2007 och senare. |
| **Prestanda med stora dokument** | Använd `doc.GetChildNodes(NodeType.Shape, true)` en gång och återanvänd samlingen istället för att anropa `GetChild` upprepade gånger. |

## Pro‑tips: Kombinera `Hidden` med `WrapType`

När en form är dold reserverar Word fortfarande det utrymme den skulle ta upp om du inte också ändrar dess omslag‑beteende. Att sätta `WrapType = WrapType.None` tar bort platshållarområdet.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Detta säkerställer att layouten kollapsar som om formen aldrig hade funnits, vilket är användbart för att generera rena rapporter.

## Slutsats

Du vet nu hur du **döljer/visar en form med den nya `Hidden`‑egenskapen** med Aspose.Words för C#. Lösningen täcker att ladda ett dokument, hitta en form, växla `Hidden`‑egenskapen och spara förändringen. Genom att följa bästa‑praxis‑tipsen — kontrollera `null`, hantera flera former och justera omslag‑inställningarna — kan du på ett pålitligt sätt styra formens synlighet i alla Word‑automatiseringsscenarier.

Redo att utforska mer? Överväg följande nästa steg:

* **Dölj/visa flera former** baserat på anpassad metadata (använder tekniken “programmerat dölja form”).
* **Kombinera `Hidden` med villkorligt innehåll** med Aspose.Words‑fält för dynamisk rapportgenerering.
* **Utforska andra nod‑egenskaper**, såsom `Visible` för diagramobjekt eller `IsDeleted` för stycke‑nivå kontroll.

Lycka till med kodandet, och njut av den fin‑granulerade kontroll som Aspose.Words erbjuder för formens synlighet i Word‑dokument!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [hur du döljer en form i Word med C# – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Hur du döljer en form i Word med C# – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Skapa ett tomt Word‑dokument med en dold ellips‑form – fullständig C#‑guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}