---
category: general
date: 2026-09-21
description: Lär dig hur du skapar ett tomt Word‑dokument, lägger till en enkel textkontroll,
  anger platshållartext och sparar docx‑filen med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save docx file
- add plain text control
language: sv
lastmod: 2026-09-21
og_description: Skapa ett tomt Word‑dokument, lägg till en enkel textkontroll, ange
  platshållartext och spara docx‑filen med Aspose.Words. Följ den här kompletta handledningen.
og_image_alt: Screenshot showing a blank Word document created to set placeholder
  text in a text control
og_title: Skapa ett tomt Word‑dokument och lägg till en textkontroll – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create a blank Word document, add a plain text control,
    set placeholder text, and save the docx file using Aspose.Words.
  headline: How to create a blank Word document with a text control
  type: TechArticle
tags:
- Aspose.Words
- Word automation
- .NET
- Document generation
title: Hur man skapar ett tomt Word‑dokument med en textkontroll
url: /sv/java/document-manipulation/how-to-create-a-blank-word-document-with-a-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word‑dokument med en textkontroll

Om du behöver **skapa ett tomt Word‑dokument** programmässigt, visar den här guiden exakt hur du gör. Du får se hur du lägger till en plain‑text‑kontroll, sätter platshållartext och slutligen **sparar docx‑filen** på disk.

I avsnitten nedan lär du dig hela arbetsflödet, från att initiera dokumentet till att verifiera att platshållaren visas när filen öppnas i Microsoft Word. Stegen fungerar med Aspose.Words .NET 2024‑R2, men koncepten gäller för alla .NET‑bibliotek för dokumentgenerering.

## Vad du behöver

- .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.8)  
- Aspose.Words for .NET (NuGet‑paket `Aspose.Words`)  
- En IDE såsom Visual Studio eller VS Code  
- Grundläggande kunskaper i C#  

> **Pro tip:** Installera NuGet‑paketet med `dotnet add package Aspose.Words` för att hålla ditt projekt organiserat.

## Steg 1: Skapa ett tomt Word‑dokument

Den första operationen är att instansiera ett tomt `Document`. Detta objekt representerar ett **tomt Word‑dokument** som inte innehåller några sektioner, stycken eller formatmallar.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Create a new blank document
Document doc = new Document();
```

Att skapa ett tomt dokument ger dig en ren canvas, vilket är viktigt när du vill ha full kontroll över layouten för insatta kontroller.

## Steg 2: Lägg till en plain‑text‑kontroll

En plain‑text Structured Document Tag (SDT) fungerar som en innehållskontroll i Word. Den låter dig påtvinga en specifik datatyp och visa en ledtråd när fältet är tomt.

```csharp
using Aspose.Words.Markup;

// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag at block level
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Block);
```

Metoden `InsertStructuredDocumentTag` returnerar ett `StructuredDocumentTag`‑objekt, som du kan konfigurera ytterligare. Att lägga till en **plain text‑kontroll** på blocknivå säkerställer att kontrollen beter sig som ett eget stycke, vilket gör den enkel att formatera senare.

## Steg 3: Sätt platshållartext för kontrollen

Platshållartext guidar användaren att ange rätt information. I Word visas detta som ljusgrå text tills användaren skriver något.

```csharp
// Set a title (used for identification in the Word UI)
sdt.Title = "CustomerName";

// Set the placeholder that the user sees
sdt.PlaceholderName = "Enter name";
```

Här **sätter vi platshållartext** med egenskapen `PlaceholderName`. Egenskapen `Title` är valfri men användbar för programmatisk åtkomst senare, särskilt om du behöver lokalisera kontrollen i ett större dokument.

## Steg 4: Lägg till vanligt innehåll efter kontrollen

Ofta behöver du fortsätta skriva efter kontrollen. Metoden `DocumentBuilder.Writeln` lägger till ett nytt stycke med den angivna texten.

```csharp
// Write a normal paragraph after the SDT
builder.Writeln("After the SDT");
```

Detta visar att dokumentet förblir redigerbart efter att kontrollen har satts in, och du kan fritt blanda vanliga stycken med innehållskontroller.

## Steg 5: Spara docx‑filen

Till sist sparar du det minnesbaserade dokumentet till en fysisk fil. Metoden `Save` bestämmer automatiskt formatet utifrån filändelsen.

```csharp
// Save the document to a .docx file
string outputPath = @"C:\Temp\SDTExample.docx";
doc.Save(outputPath);
```

Efter att programmet har körts, öppna `SDTExample.docx` i Microsoft Word. Du kommer att se ett tomt dokument med en **plain text‑kontroll** som visar “Enter name” som platshållartext, följt av raden “After the SDT”.

### Förväntat resultat

När filen öppnas:

1. Den första raden är en gråtonad platshållare med texten **Enter name** inuti en innehållskontrollruta.  
2. Den andra raden visar **After the SDT** som ett normalt stycke.

Om du skriver ett namn och trycker på **Enter**, försvinner platshållaren, vilket bekräftar att kontrollen fungerar som avsett.

## Vanliga varianter och specialfall

| Situation | Vad som ska ändras |
|-----------|--------------------|
| **Flera platshållare** | Anropa `InsertStructuredDocumentTag` flera gånger och tilldela olika `Title`/`PlaceholderName`‑värden. |
| **Inline‑kontroll** | Använd `MarkupLevel.Inline` istället för `MarkupLevel.Block`. |
| **Rich‑text‑kontroll** | Byt ut `StructuredDocumentTagType.PlainText` mot `StructuredDocumentTagType.RichText`. |
| **Spara till en ström** | Använd `doc.Save(stream, SaveFormat.Docx)` när du behöver skicka filen via HTTP. |

> **Observera:** Att försöka sätta `PlaceholderName` på en `RichText`‑SDT kastar ett `ArgumentException`. Endast plain‑text‑kontroller stöder platshållare.

## Fullt fungerande exempel

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document
        Document doc = new Document();

        // Step 2: Prepare a builder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a plain‑text control (SDT)
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, MarkupLevel.Block);

        // Step 4: Set title and placeholder text
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Step 5: Add normal content after the control
        builder.Writeln("After the SDT");

        // Step 6: Save the document
        string path = @"C:\Temp\SDTExample.docx";
        doc.Save(path);

        Console.WriteLine($"Document saved to {path}");
    }
}
```

När programmet körs skapas filen som beskrivs i avsnittet *Förväntat resultat* ovan.

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument**, **lägger till en plain text‑kontroll**, **sätter platshållartext** och **sparar docx‑filen** med Aspose.Words. Denna end‑to‑end‑lösning låter dig generera Word‑mallar som guidar användare med tydliga ledtrådar, vilket gör dokumentautomatisering både pålitlig och användarvänlig.

**Nästa steg**

- Utforska **lägg till plain text‑kontroll**‑varianter såsom inline‑kontroller eller rich‑text‑taggar.  
- Kombinera flera platshållare för att bygga fullständiga formulär (t.ex. adressblock, datum).  
- Använd `DocumentBuilder` för att applicera stilar eller slå ihop data från en databas, och utöka arbetsflödet **spara docx‑fil**.

Känn dig fri att experimentera med olika platshållarvärden och kontrolltyper – dokumentgenerering är ett kraftfullt sätt att automatisera rapporter, kontrakt och alla återkommande Word‑utdata. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}