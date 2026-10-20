---
category: general
date: 2026-08-20
description: Lär dig hur du ställer in egenskapen “hidden” för en form i Aspose.Words
  för C#. Den här guiden visar hur du infogar en bild och döljer formen så att den
  aldrig visas i användargränssnittet eller utskriftsresultatet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: sv
lastmod: 2026-08-20
og_description: Ställ in egenskapen “hidden” för en form i Aspose.Words med C#. Infoga
  en bild, dölj formen och se till att den aldrig visas i UI eller utskriftsresultat.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Ställ in den dolda egenskapen för en form i Aspose.Words – komplett C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Hur man ställer in formens dolda egenskap i Aspose.Words för C#
url: /sv/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sätter shape hidden property i Aspose.Words för C#

Om du behöver **set shape hidden property** i ett Word‑dokument visar den här handledningen de exakta stegen med Aspose.Words för .NET. Oavsett om du bygger en mallmotor, genererar rapporter eller bäddar in en logotyp som måste förbli osynlig, kommer du att lära dig hur du infogar en bild och döljer shape så att den aldrig visas i UI‑gränssnittet eller utskriftsresultatet.

I den här guiden täcker vi också **insert image into document**, förklarar varför det är viktigt att dölja en shape för utskrift, och går igenom den kompletta, körbara koden. Inga externa referenser krävs—kopiera bara, klistra in och kör.

## Förutsättningar

* .NET 6.0 eller senare (den senaste Aspose.Words‑versionen riktar sig mot .NET 6+)
* En giltig Aspose.Words för .NET‑licens (eller använd gratis utvärderingsläge)
* Visual Studio 2022 eller någon C#‑IDE du föredrar
* En bildfil (t.ex. `logo.png`) placerad i en mapp som du kan referera till från koden

## Steg 1: Skapa ett nytt Document och DocumentBuilder

`DocumentBuilder`‑klassen är ingångspunkten för att programatiskt bygga Word‑innehåll. Den låter dig infoga stycken, tabeller och shapes såsom bilder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta steg?*  
Att skapa ett `Document` ger dig en minnesrepresentation av en .docx‑fil, medan `DocumentBuilder` tillhandahåller det flytande API‑et som infogar objekt. Utan dessa objekt kan du inte placera en shape i dokumentet.

## Steg 2: Infoga bilden som en shape

Aspose.Words behandlar varje bild som en `Shape`. Metoden `InsertImage` returnerar den `Shape`‑instansen, som du senare kan manipulera.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Varför detta steg?*  
Att använda `InsertImage` lägger inte bara till bilden i textflödet utan ger dig också en referens (`picture`) som du kan konfigurera. Detta är avgörande för **C# shape hidden property** som vi kommer att sätta härnäst.

## Steg 3: Ställ in shape hidden property

`Hidden`‑egenskapen styr om shape deltar i UI och utskrift. Att sätta den till `true` gör shape osynlig i Word‑UI och garanterar att den inte skrivs ut.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Varför detta steg?*  
När en shape är markerad som dold behandlar Word den som en kommentar—närvarande i dokumentstrukturen men aldrig renderad. Detta är kärnan i **set shape hidden property**.

## Steg 4: Spara dokumentet

Slutligen skriver du dokumentet till disk. Du kan välja vilket format som helst som stöds av Aspose.Words (`.docx`, `.pdf`, `.html`, etc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Varför detta steg?*  
Sparandet slutför de minnesbaserade ändringarna. När du öppnar den resulterande `.docx` i Microsoft Word visas ingen synlig bild, och PDF‑exporten bekräftar att shape aldrig visas i utskriftsresultatet.

## Fullt, körbart exempel

När allt sätts ihop, här är det kompletta programmet som du kan kompilera och köra:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Förväntat resultat**

* Att öppna `HiddenImageDocument.docx` i Microsoft Word visar ingen synlig bild.
* Att exportera eller skriva ut dokumentet (eller öppna PDF‑filen) visar också ingen bild.
* Den dolda shape finns fortfarande i dokumentets XML, vilket du kan verifiera genom att öppna `.docx` som en zip och inspektera `word/document.xml` – du kommer att se ett `<w:pict>`‑element med `w:hidden="true"`.

## Vanliga variationer och edge‑cases

| Situation | Vad man ska göra | Varför det är viktigt |
|-----------|-------------------|-----------------------|
| **Bildfil saknas** | Omge `InsertImage` med en `try/catch` och hantera `FileNotFoundException`. | Förhindrar att applikationen kraschar och låter dig logga ett tydligt fel. |
| **Flera dolda shapes** | Anropa `picture.Hidden = true` för varje `Shape` du infogar, eller iterera över `doc.GetChildNodes(NodeType.Shape, true)`. | Säkerställer att varje oönskat visuellt element förblir osynligt. |
| **Behöver shape synlig endast i redigeringsläge** | Sätt `picture.Hidden = false` efter redigering, och växla tillbaka innan sparning. | Gör att du kan arbeta med shape i UI samtidigt som slutresultatet hålls rent. |
| **Utskrift på äldre Word‑versioner** | Verifiera dokumentet med Word 2010 eller senare; den dolda flaggan stöds i alla moderna versioner. | Säkerställer kompatibilitet för din användarbas. |
| **Använda ett annat filformat (t.ex. PDF direkt)** | `Hidden`‑flaggan fungerar på samma sätt; Aspose.Words respekterar den under PDF‑konvertering. | Bekräftar att **prevent shape from printing** fungerar för alla exportmål. |

## Pro‑tips: Verifiera den dolda flaggan programatiskt

Om du behöver bekräfta att en shape är dold innan sparning kan du inspektera egenskapen:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Denna enkla kontroll är användbar i automatiserade pipelines där du måste garantera efterlevnad av dokumentgenereringspolicyer.

## Slutsats

Du vet nu hur du **set shape hidden property** i Aspose.Words för C#. Genom att infoga en bild, sätta `picture.Hidden = true` och spara dokumentet, hålls shape ute ur UI och visas aldrig i utskriftsresultatet. Denna teknik är viktig när du behöver platshållare, vattenstämplar eller varumärkeselement som ska förbli osynliga för slutanvändare.

### Vad blir nästa?

* Utforska andra shape‑egenskaper såsom `picture.WrapType`, `picture.Rotation` och `picture.RelativeHorizontalPosition`.
* Lär dig hur du **hide shape in Aspose.Words** villkorsstyrt baserat på användarinput eller konfiguration.
* Kombinera dolda shapes med **insert image into document**‑loopar för att generera dynamiska, osynliga markörer för senare bearbetning (t.ex. mail‑merge‑fält).

Känn dig fri att experimentera med olika bildformat, dokumentlayouter och exportmål. Att dölja shapes ger dig fin‑granulär kontroll över vad dina läsare faktiskt ser—och vad som förblir bakom kulisserna. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangel‑shape i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Skapa grupp‑shape i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Infoga inline‑bild i Word‑dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}