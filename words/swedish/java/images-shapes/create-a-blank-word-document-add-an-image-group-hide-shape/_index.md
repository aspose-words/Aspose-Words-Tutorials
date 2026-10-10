---
category: general
date: 2026-10-10
description: Skapa ett tomt Word‑dokument, infoga en bild i Word, lägg till en bildgrupp
  och dölj formen i den sparade filen. Följ den här steg‑för‑steg‑guiden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: sv
lastmod: 2026-10-10
og_description: Skapa ett tomt Word‑dokument, infoga en bild i Word, lägg till en
  bildgrupp och dölj formen. Denna guide visar den kompletta C#‑koden.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Skapa ett tomt Word-dokument, lägg till en bildgrupp, dölj form
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Skapa ett tomt Word‑dokument, lägg till en bildgrupp, dölj form
url: /sv/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument, lägg till en bildgrupp, dölj form

Om du behöver **skapa ett tomt Word-dokument** och senare dölja visuella element, visar den här handledningen exakt hur du gör. Du kommer att lära dig att infoga en bild i Word, lägga till en bildgrupp och dölja en form i Word-dokumentet i en enda återanvändbar C#-rutin.

Vi kommer att använda Aspose.Words for .NET‑biblioteket, som låter dig manipulera .docx‑filer utan att Microsoft Word är installerat. I slutet av den här guiden har du ett körbart program som producerar en Word‑fil som innehåller en dold bildgrupp, redo för vidare bearbetning eller villkorlig visning.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)
- En mapp på disken där du kan läsa en bildfil och skriva utdata‑dokumentet
- Grundläggande kunskap om C# och Visual Studio (eller någon annan IDE du föredrar)

## Skapa ett tomt Word-dokument med Aspose.Words

Det första steget är att **skapa ett tomt Word-dokument**. Aspose.Words tillhandahåller klassen `Document` som representerar en Word‑fil i minnet. Att instansiera den utan argument ger dig ett tomt dokument redo för innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt:* Att börja med ett tomt dokument säkerställer att ingen dold formatering eller kvarvarande sektioner stör den form du kommer att lägga till senare.

## Infoga bild i Word med DocumentBuilder

Nästa steg är att **infoga bild i Word** genom att först skapa en gruppform som ska hålla bilden. Gruppformer låter dig behandla flera ritobjekt som en enhet, vilket är användbart när du senare vill dölja eller flytta dem tillsammans.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Metoden `InsertGroupShape` skapar en tom behållare. Dimensionerna är i punkter (1 punkt = 1/72 tum). Justera storleken så att den matchar upplösningen på bilden du planerar att bädda in.

## Lägg till bildgrupp i dokumentet

Nu **lägger vi till bildgrupp** genom att flytta builderns markör in i den nyss skapade gruppen och infoga bilden. Alla efterföljande insättningar blir en del av gruppen.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tips:* Använd en absolut eller korrekt escapad relativ sökväg; annars kastar `InsertImage` ett `FileNotFoundException`.

## Dölj form i ett Word-dokument

Slutligen **döljer vi form i Word-dokumentet** genom att sätta gruppens egenskap `Hidden` till `true`. Dolda former visas inte när dokumentet öppnas i Word, men de finns kvar i filen och kan avslöjas programmässigt senare.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

När du öppnar *GroupHidden.docx* i Microsoft Word ser du en helt tom sida eftersom bildgruppen är dold. Filen innehåller fortfarande bilddata, som du kan avdöja senare med `group.Hidden = false` om så behövs.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i ett nytt konsolprojekt:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Förväntat resultat**

- En fil med namnet `GroupHidden.docx` visas i `YOUR_DIRECTORY`.
- När du öppnar filen i Word visas en tom sida.
- Den dolda bilden kan visas genom att ändra `group.Hidden = false` och spara om.

## Vanliga varianter och kantfall

| Situation | Hur du anpassar koden |
|-----------|----------------------|
| **Flera bilder** | Infoga ytterligare `InsertImage`‑anrop efter `builder.MoveTo(group)`. Alla bilder förblir i samma grupp och delar den dolda flaggan. |
| **Olika bildformat** | Aspose.Words stödjer PNG, JPEG, BMP, GIF, TIFF. Ändra bara filändelsen; ingen kodändring behövs. |
| **Villkorlig synlighet** | Spara en anpassad dokumentvariabel (`doc.Variables.Add("ShowImages", "true")`) och växla `group.Hidden` baserat på dess värde vid körning. |
| **Stora dokument** | Skapa gruppen på en specifik sida (`builder.InsertBreak(BreakType.PageBreak)`) innan du infogar gruppen för att undvika layoutförskjutningar. |
| **Kompatibilitet med äldre Word‑versioner** | Spara som `doc.Save("output.doc", SaveFormat.Doc)` om du behöver det äldre `.doc`‑formatet; dolda former beter sig på samma sätt. |

**Pro tip:** Sätt alltid `group.Hidden = true` *efter* att du har infogat alla underordnade element. Att ändra flaggan innan innehållet läggs till kan leda till att vissa element renderas oväntat i äldre Word‑versioner.

## Slutsats

Du vet nu hur du **skapar ett tomt Word-dokument**, **infogar bild i Word**, **lägger till bildgrupp** och **döljer form i Word-dokumentet** med Aspose.Words for .NET. Det kompletta exemplet demonstrerar varje steg från att initiera dokumentet till att spara en fil som innehåller en dold bildgrupp.

Nästa steg kan vara att utforska:

- Lägga till textrutor eller diagram i samma grupp
- Använda `DocumentBuilder.StartBookmark` / `EndBookmark` för att markera dolda sektioner
- Programmera växling av synlighet baserat på användarinmatning eller dokumentvariabler

Känn dig fri att experimentera med olika former, storlekar och synlighetsregler för att passa ditt automationsscenario. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa Word-dokument med flytande bild i .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Infoga inbäddad bild i Word-dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}