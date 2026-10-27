---
category: general
date: 2026-08-07
description: Hur man skapar innehållskontroll i C# med Aspose.Words – lär dig hur
  du lägger till SDT, ställer in platshållare, skriver standardtext och infogar en
  vanlig textkontroll.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: sv
lastmod: 2026-08-07
og_description: Hur man skapar innehållskontroll i C# med Aspose.Words. Denna handledning
  visar hur man lägger till SDT, ställer in platshållare, skriver standardtext och
  infogar en vanlig textkontroll.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Hur man skapar innehållskontroll i C# – komplett Aspose.Words-guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Hur man skapar innehållskontroll i C# med Aspose.Words
url: /sv/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar innehållskontroll i C# med Aspose.Words

Om du behöver **how to create content control** i ett Word‑dokument programatiskt, visar den här guiden exakt det. Du kommer att se hur du lägger till en SDT, sätter en platshållare, skriver standardtext och infogar en ren‑text‑kontroll — allt med Aspose.Words för .NET.

Handledningen täcker varje steg från projektuppsättning till att spara den slutliga `.docx`‑filen. I slutet kommer du att kunna generera dokument som innehåller fullt konfigurerade innehållskontroller, redo för efterföljande bearbetning eller användarinteraktion.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- En Aspose.Words för .NET‑licens eller en tillfällig evalueringsnyckel
- Visual Studio 2022 (eller någon IDE som stödjer C#)
- Grundläggande kunskap om C#‑syntax

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Så skapar du innehållskontroll – steg 1: sätt upp projektet

Skapa en ny konsolapplikation och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Processen **how to create content control** börjar med ett nytt `Document`‑objekt. Detta objekt representerar Word‑filen du kommer att manipulera.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Proffstips:** Behåll `DocumentBuilder`‑instansen levande under hela dokumentets livscykel; att återskapa den onödigt lägger till extra belastning.

## Så lägger du till SDT – steg 2: infoga en ren‑text Structured Document Tag

En SDT (Structured Document Tag) är det tekniska namnet för en innehållskontroll. För att **how to add sdt**, instansiera en `StructuredDocumentTag` med önskad typ.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

`SdtType.PlainText`‑alternativet skapar en enkel textruta som användare kan redigera. Att sätta `Title` hjälper dig att hitta kontrollen när du senare behöver hämta eller ändra dess innehåll.

## Så sätter du platshållare – steg 3: konfigurera platshållartext

En platshållare guidar slutanvändaren genom att visa exempeltext innan de skriver något. För att **how to set placeholder**, tilldela `PlaceholderName`‑egenskapen.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

När dokumentet öppnas i Microsoft Word visas den gråa platshållartexten inuti kontrollen tills användaren anger ett värde.

## Så skriver du standardtext – steg 4: lägg till initialt innehåll i SDT:n

Om du vill att kontrollen ska innehålla fördefinierat innehåll måste du flytta byggaren in i SDT:n och skriva texten. Detta demonstrerar **how to write default text**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

Anropet till `MoveTo` ändrar markörens position till insidan av SDT:n. Efter `Write` visar kontrollen “John Doe” som sitt initiala värde.

## Infoga ren‑text‑kontroll – steg 5: spara dokumentet

Slutligen sparas dokumentet till disk. Detta slutför operationen **insert plain text control**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du öppnar `CustomerNameControl.docx` i Word kommer du att se en ren‑text‑innehållskontroll med titeln **CustomerName**, som visar platshållaren “Enter name here” och standardtexten “John Doe”.

### Förväntat resultat

- En `.docx`‑fil på skrivbordet med namnet `CustomerNameControl.docx`.
- Inuti filen, en enda innehållskontroll som innehåller texten **John Doe**.
- Platshållartexten visas i ljusgrått tills användaren skriver ett nytt värde.

## Ytterligare variationer och kantfall

### Lägga till flera innehållskontroller

Du kan upprepa stegen **how to add sdt** för att infoga flera kontroller i samma dokument. Skapa bara en ny `StructuredDocumentTag` för varje fält och flytta byggaren därefter.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Läsa en platshållare programatiskt

Om du behöver verifiera att en platshållare har satts korrekt, inspektera `PlaceholderName`‑egenskapen:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Använda andra SDT‑typer

Aspose.Words stödjer rullgardinslistor, datumväljare och rich‑text‑kontroller. Ersätt `SdtType.PlainText` med `SdtType.DropDownList` eller `SdtType.RichText` för att ändra kontrolltypen.

## Vanliga fallgropar och hur du undviker dem

| Symptom | Orsak | Lösning |
|---------|-------|-----|
| Platshållaren visas aldrig | Dokumentet sparades innan platshållaren tilldelades | Se till att `PlaceholderName` är satt **innan** du anropar `Save`. |
| Standardtext saknas | Buildern flyttades inte in i SDT:n | Anropa `builder.MoveTo(sdt)` innan `builder.Write`. |
| Kontrollens titel är tom | `Title`‑egenskapen är inte satt | Tilldela alltid en meningsfull `Title` för senare hämtning. |

## Slutsats

Du vet nu **how to create content control** i C# med Aspose.Words, inklusive **how to add sdt**, **how to set placeholder**, **how to write default text** och **insert plain text control**. Det kompletta exemplet kompileras till en färdig‑att‑använda Word‑fil som demonstrerar varje koncept.

Härifrån kan du utforska mer avancerade scenarier såsom att binda innehållskontroller till XML‑data, hantera upprepande sektioner eller konvertera dokumentet till PDF samtidigt som kontrollerna bevaras. Varje av dessa ämnen bygger direkt på de grunder som behandlades i den här handledningen.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}