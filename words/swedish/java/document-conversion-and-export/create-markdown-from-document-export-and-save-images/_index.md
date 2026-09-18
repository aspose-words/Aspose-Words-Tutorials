---
category: general
date: 2026-02-18
description: Skapa markdown från dokument med enkla steg för att exportera dokumentet
  till markdown och spara bilder i en undermapp. Lär dig hur du sparar dokumentet
  som markdown i C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: sv
og_description: Skapa markdown från dokument i C# och lär dig hur du exporterar dokumentet
  till markdown samtidigt som du sparar bilder i en undermapp. Följ steg‑för‑steg‑guiden.
og_title: Skapa markdown från dokument – exportera och spara bilder
tags:
- C#
- Aspose.Words
- Markdown export
title: Skapa markdown från dokument – exportera och spara bilder
url: /sv/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa markdown från dokument – Exportera och spara bilder

Har du någonsin behövt **create markdown from document** men varit osäker på hur du håller de inbäddade bilderna prydliga? Du är inte ensam. I många projekt genererar vi rapporter, manualer eller bloggutkast programatiskt, och det sista vi vill ha är en röra av bildfiler utspridda i utdata‑mappen.  

I den här handledningen går vi igenom en komplett, färdig‑att‑köra‑lösning som **exports document to markdown**, lagrar varje bild i en dedikerad *md‑resources* undermapp och slutligen **saves document as markdown** med Aspose.Words för .NET API. I slutet har du en enda metod du kan klistra in i vilken C#‑kodbas som helst, samt ett antal tips för att hantera kantfall.

> **Snabb överblick:**  
> • Ställ in `MarkdownSaveOptions`  
> • Tillhandahåll en `IResourceSavingCallback` som dirigerar bilder till en undermapp  
> • Anropa `Document.Save` med de konfigurerade alternativen  

Om du är nyfiken på varför vi väljer en callback istället för efterbearbetning, fortsätt läsa – resonemanget förklaras steg för steg.

---

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.7+)  
- Aspose.Words för .NET (NuGet‑paket `Aspose.Words`)  
- Ett käll‑`Document`‑objekt (kan vara .docx, .pdf, .rtf, etc.)  

Inga ytterligare bibliotek krävs; callback‑API:et är inbyggt i Aspose.Words.

---

## Steg 1: Skapa markdown från dokument – konfigurera sparalternativ

Det första vi gör är att instansiera `MarkdownSaveOptions`. Detta objekt talar om för Aspose.Words hur konverteringen ska bete sig, till exempel vilken Markdown‑variant som ska användas, om bilder ska bäddas in som Base64 och var de genererade filerna ska placeras.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Varför detta är viktigt:**  
> Utan att explicit skapa `MarkdownSaveOptions` faller biblioteket tillbaka på standardinställningarna som bäddar in bilder direkt i Markdown‑filen som Base64‑strängar. Det gör filen enorm och undergräver syftet med en ren *images*‑mapp.

---

## Steg 2: Exportera dokument till markdown och definiera resurshantering

Nu talar vi om för spararen **var** varje bild ska placeras. `IResourceSavingCallback`‑gränssnittet ger oss en krok som triggas för varje resurs (bild, SVG, etc.) som upptäcks under exporten. Inuti callback‑en:

1. Säkerställ att mål‑mappen finns (`md-resources/`).  
2. Sätt `OutputFileName` till mappen plus det ursprungliga resursnamnet.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Vanlig fråga:** *Vad händer om jag vill bädda in bilder istället för att spara dem?*  
> Hoppa bara över callback‑en eller sätt `args.OutputFileName = null;` – spararen kommer automatiskt att bädda in bilden som en Base64‑sträng.

> **Kantfall:** Vissa äldre dokument innehåller duplicerade bildnamn. Callback‑en ovan kommer att skriva över den tidigare filen. För att undvika det kan du lägga till ett GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Steg 3: Spara dokument som markdown och verifiera sparade bilder

Med alternativen fullt konfigurerade är det sista anropet en enradare som skriver Markdown‑filen och de associerade bilderna till disk.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Om allt går bra ser du:

- `MyReport.md` – Markdown‑representationen av ditt källdokument.  
- `md-resources/` – en mapp bredvid .md‑filen som innehåller varje extraherad bild (t.ex. `image001.png`, `image002.jpg`).  

**Exempel på Markdown‑snutt** (auto‑genererad av Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Proffstips:** Öppna den genererade `.md`‑filen i VS Code eller någon Markdown‑förhandsgranskare; bilderna bör renderas omedelbart eftersom de relativa sökvägarna matchar mappstrukturen.

---

## Fullt, körbart exempel

Nedan är ett självständigt konsolprogram som du kan klistra in i ett nytt .NET‑projekt och köra. Det skapar ett enkelt Word‑dokument, lägger till en bild och **creates markdown from document** samtidigt som bilden lagras i en undermapp.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Vad du bör se** efter körning:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Öppna `ExportedDoc.md` – bildreferensen pekar på `md-resources/sample-image.png`, och bilden visas korrekt i vilken Markdown‑visare som helst.

---

## Vanliga varianter

| Scenario | Hur du anpassar koden |
|----------|------------------------|
| **Hoppa över bildexport** (bädda in som Base64) | Utelämna `ResourceSavingCallback` helt, eller sätt `args.OutputFileName = null;` i callback‑en. |
| **Ändra bildformat** (t.ex. alla PNG) | Inuti callback‑en, modifiera `args.ResourceFileName` och konvertera eventuellt strömmen innan du skriver. |
| **Anpassat mappnamn** | Ersätt `"md-resources/"` med någon relativ eller absolut sökväg du föredrar. |
| **Flera dokument i en batch** | Loopa över en samling `Document`‑objekt, återanvänd samma `MarkdownSaveOptions`‑instans (se bara till att mappen rensas eller får ett unikt namn per körning). |

---

## Slutsats

Vi har just visat dig **how to create markdown from document**, **export document to markdown**, och **save images to subfolder** med ett rent, callback‑drivet tillvägagångssätt. De viktigaste slutsatserna är:

- Använd `MarkdownSaveOptions` för fin‑granulär kontroll över exporten.  
- Implementera `IResourceSavingCallback` för att dirigera bilder till en dedikerad mapp och hålla din Markdown prydlig.  
- Samma mönster fungerar för andra resurstyper (SVG, ljud) – inspektera bara `args.ResourceType`.  

Nästa steg kan vara att utforska **saving document as markdown** med anpassade rubrikstilar, eller integrera denna rutin i ett ASP.NET Web API som returnerar ett ZIP‑arkiv med `.md`‑filen och dess resurser. Oavsett vad, så har du nu byggstenarna i din verktygslåda.

Har du frågor, eller har du upptäckt ett kantfall vi inte täckte? Lämna en kommentar nedan, och lycka till med kodandet!

---

![skapa markdown från dokument exempel](placeholder.png "skapa markdown från dokument exempel")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}