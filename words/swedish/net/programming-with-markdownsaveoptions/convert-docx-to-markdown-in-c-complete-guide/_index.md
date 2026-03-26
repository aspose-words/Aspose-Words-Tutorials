---
category: general
date: 2026-03-25
description: Konvertera DOCX till Markdown snabbt samtidigt som du extraherar bilder
  från Word med Aspose.Words. Lär dig steg för steg med fullständig kod.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: sv
og_description: Konvertera DOCX till Markdown och extrahera bilder från Word med Aspose.Words.
  Följ den här kompletta handledningen för en färdig lösning.
og_title: Konvertera DOCX till Markdown i C# – Steg‑för‑steg guide
tags:
- Aspose.Words
- C#
- Markdown
title: Konvertera DOCX till Markdown i C# – Komplett guide
url: /sv/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera DOCX till Markdown med Aspose.Words

Har du någonsin behövt **konvertera DOCX till markdown** men varit osäker på hur du behåller de inbäddade bilderna intakta? Du är inte ensam – många utvecklare stöter på detta problem när de försöker flytta Word‑innehåll till en statisk‑sidgenerator eller ett dokumentations‑repo.  
Den goda nyheten är att Aspose.Words för .NET kan göra det tunga arbetet åt dig, och med en liten callback kan du också **extrahera bilder från Word**‑filer samtidigt.

I den här handledningen går vi igenom ett verkligt exempel som laddar en `.docx`, sparar den som en Markdown‑fil och skriver varje bild till en dedikerad mapp. I slutet har du en färdig körbar konsolapp som du kan släppa in i vilket .NET‑projekt som helst.

> **Proffstips:** Om du bara behöver texten och inte bryr dig om bilder kan du hoppa över `ResourceSavingCallback` helt – koden kommer fortfarande att producera ren Markdown.

## Vad du behöver

- **Aspose.Words for .NET** (senaste versionen, t.ex. 24.12). Du kan hämta den från NuGet: `Install-Package Aspose.Words`.
- **.NET 6.0** eller senare (API:et fungerar även på .NET Framework, men .NET 6 ger bästa prestanda).
- Ett enkelt konsolprojekt eller någon C#‑host du föredrar.
- En inmatnings‑Word‑fil (`input.docx`) som innehåller minst en bild så att vi kan se extraktionen i praktiken.

Det är allt – inga extra bibliotek, inga krångliga kommandoradsverktyg. Låt oss dyka ner.

![exempel på konvertering av docx till markdown](images/convert-docx-to-markdown.png)

*Bildtext: exempel på konvertering av docx till markdown*

## Steg 1 – Skapa projektet och lägg till Aspose.Words

För att hålla saker organiserade, skapa en ny konsolapp:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

Öppna `Program.cs` och rensa den automatiskt genererade koden. Vi klistrar in hela lösningen senare, men för nu bara se till att projektet bygger.

## Steg 2 – Läs in käll‑DOCX‑filen

Det första vi gör är att be Aspose.Words att läsa Word‑filen. Denna operation är **snabb** – biblioteket parsar dokumentstrukturen utan att öppna Word själv.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

Varför omsluter vi sökvägen med `Path.Combine`? Det gör koden portabel över Windows, macOS och Linux – något du kommer att uppskatta när du flyttar projektet till en CI‑pipeline.

## Steg 3 – Konfigurera Markdown‑spara‑alternativ med en resurs‑callback

När du ber Aspose.Words att spara som Markdown, bäddar det normalt in bilder som Base64‑strängar. Det är okej för små ikoner, men för större foton ökar det filstorleken kraftigt. Istället bifogar vi en **resurs‑sparande callback** som skriver varje bild till disk och uppdaterar Markdown‑länken.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

Observera att vi skickar `resourcesDir` till callback‑konstruktorn – detta håller sökvägslogiken utanför själva callbacken och gör klassen återanvändbar.

## Steg 4 – Implementera resurs‑sparande callbacken

Callbacken implementerar `IResourceSavingCallback`. För varje bild som Aspose.Words vill skriva, ger den oss ett `ResourceSavingArgs`‑objekt. Vi bestämmer **var** filen ska lagras, ger den ett unikt namn och säger sedan till motorn att hoppa över dess standard‑sparbeteende.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**Varför detta är viktigt:** Genom att sätta `args.Uri` styr vi exakt hur bilden kommer att refereras i den resulterande `.md`‑filen. Den relativa sökvägen `Resources/img_0.png` fungerar oavsett om du öppnar Markdown i VS Code, GitHub eller en statisk‑sidgenerator.

## Steg 5 – Spara dokumentet som Markdown

Nu sista delen: be Aspose.Words att skriva Markdown‑filen. Callbacken vi kopplat in kommer automatiskt att triggas för varje bild.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

När raden är klar kommer du att ha:

- `output.md` – en ren Markdown‑representation av det ursprungliga Word‑innehållet.
- mappen `Resources/` – som innehåller varje bild som extraherats från DOCX‑filen.

## Fullt fungerande exempel

Nedan är det **kompletta, klar‑för‑kopiering‑och‑klistra‑in** programmet. Ersätt `YOUR_DIRECTORY` med den absoluta eller relativa sökvägen som innehåller din `input.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### Förväntad output

Öppna `Output/output.md` i någon Markdown‑visare så bör du se något liknande:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources`‑mappen kommer att innehålla `img_0.png`, `img_1.jpg` osv., vilket matchar de bilder som ursprungligen var inbäddade i `input.docx`.

## Vanliga frågor (FAQ)

**Fungerar detta med .doc‑filer?**  
Ja. Aspose.Words kan läsa `.doc`, `.docx`, `.rtf` och många andra format. Ändra bara filändelsen i `inputPath`.

**Vad händer om jag behöver absoluta URL:er för bilderna?**  
Ersätt `args.Uri = $"Resources/{fileName}";` med något i stil med `args.Uri = $"https://mycdn.com/docs/{fileName}";`. Markdown‑filen kommer då att referera till den fjärrplatsen.

**Kan jag kontrollera bildkvalitet eller format?**  
Callbacken får den ursprungliga bildströmmen. Om du vill konvertera PNG till JPEG kan du ladda strömmen i `System.Drawing.Image`, omkoda och skriva de nya bytena innan du sätter `args.Uri`.

**Är `ResourceSavingCallback` trådsäker?**  
Aspose.Words anropar callbacken sekventiellt för varje resurs, så

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}