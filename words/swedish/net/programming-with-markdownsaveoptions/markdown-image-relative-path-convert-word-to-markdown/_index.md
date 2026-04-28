---
category: general
date: 2026-04-28
description: Lär dig hur du ställer in en relativ sökväg för markdown‑bilder när du
  konverterar Word till markdown, extraherar bilder från Word och skapar en resurser‑mapp
  för exporterade bilder.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: sv
og_description: Ställ in en relativ bildväg i markdown när du konverterar Word till
  markdown, extraherar bilder från Word och skapar en resursmapp för exporterade bilder.
og_title: markdown bild relativ sökväg – Konvertera Word till Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: markdown‑bild relativ sökväg – Konvertera Word till Markdown
url: /sv/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – Konvertera Word till Markdown

Har du någonsin behövt en **markdown image relative path** när du **convert Word to markdown**? Du är inte ensam. De flesta utvecklare stöter på ett problem när den genererade Markdown pekar på bilder i en platt mapp, vilket bryter den relativa länkstrukturen du förväntar dig i en statisk webbplats eller ett GitHub‑repo.

I den här handledningen går vi igenom en komplett, end‑to‑end‑lösning som **extraherar bilder från Word**, **skapar en resources‑mapp**, och skriver om bildreferenserna så att de använder en ren *markdown image relative path*. När du är klar har du en färdig att publicera `.md`‑fil och en prydligt organiserad `Resources`‑katalog som innehåller varje bild som extraherats från den ursprungliga `.docx`‑filen.

> **Vad du får:** ett enda C#‑program (utan externa skript), en tydlig förklaring av *varför* varje del är viktig, och ett antal praktiska tips som du kan kopiera‑klistra in i dina egna projekt.

---

## Förutsättningar

Innan vi dyker in i koden, se till att du har:

- **.NET 6.0** eller senare installerat (du kan också rikta in dig på .NET Framework 4.7+, men .NET 6 är den bästa versionen för nya projekt).
- **Aspose.Words for .NET** (det senaste NuGet‑paketet vid skrivtillfället, version 23.12). Installera det med:
  ```bash
  dotnet add package Aspose.Words
  ```
- Ett Word‑dokument som faktiskt innehåller bilder—vi kallar det `WithImages.docx`.
- En mapp där du vill att den genererade markdown‑filen och bilderna ska ligga, t.ex. `C:\Projects\MarkdownExport`.

Inga ytterligare bibliotek krävs; allt annat hanteras av Aspose.Words.

---

## Steg 1: Ladda källdokumentet Word (utgångspunkten för convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Varför detta är viktigt:* Att ladda dokumentet ger oss åtkomst till det interna nodträdet, som inkluderar bilddelarna vi senare behöver för att **export images from docx**. Om laddningen misslyckas körs ingen av de efterföljande stegen, så dubbelkolla sökvägen och filbehörigheterna.

---

## Steg 2: Konfigurera `MarkdownSaveOptions` med en anpassad callback (hjärtat i create resources folder)

`ResourceSavingCallback` låter oss ingripa varje gång Aspose.Words vill skriva en bildfil. Inuti callbacken kommer vi att **create a Resources sub‑folder** och justera referensen så att den genererade markdown‑filen använder en *markdown image relative path*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Observera att vi skickade `resourcesFolder` till callback‑konstruktorn—detta gör mappens sökväg flexibel och undviker hårdkodade strängar i hela koden.

---

## Steg 3: Implementera callbacken som **creates resources folder** och skriver om sökvägen

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Varför detta fungerar:* `args.Stream` innehåller de råa bildbytarna. Genom att kopiera dem till en fil i vår `Resources`‑mapp **export images from docx** säkert. Sedan ersätter vi `args.ResourceFileName` med en relativ URL (`Resources/image.png`). När Aspose.Words senare skriver markdown‑filen injicerar den exakt den strängen, vilket ger oss den önskade *markdown image relative path*.

---

## Steg 4: Verifiera den genererade Markdown (hur det slutliga resultatet ser ut)

Öppna `Doc.md` i en textredigerare. Du bör se något liknande:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

Det viktiga är att varje bildreferens pekar på `Resources/...` – det är den **markdown image relative path** vi eftersträvade.

![markdown image relative path example](example.png "markdown image relative path example")

*Tips:* Om du öppnar markdown‑filen i en visare som respekterar relativa länkar (VS Code‑förhandsgranskning, GitHub eller en statisk webbplatsgenerator), kommer bilderna att visas korrekt utan någon extra konfiguration.

---

## Steg 5: Vanliga fallgropar och pro‑tips

| Problem | Varför det händer | Hur man åtgärdar det |
|---------|-------------------|----------------------|
| Bilder hamnar i rotmappen istället för `Resources` | Callbacken var inte ansluten eller `args.ResourceFileName` överskrevdes inte. | Dubbelkolla att `ResourceSavingCallback` är satt **före** anropet `doc.Save`. |
| Filnamn innehåller otillåtna tecken | Word namnger ibland bilder med mellanslag eller Unicode‑symboler. | Använd `Path.GetInvalidFileNameChars()` för att sanera `args.ResourceFileName` i callbacken. |
| Stora dokument tar lång tid att bearbeta | Varje bild skrivs synkront. | Byt till asynkron I/O (`await args.Stream.CopyToAsync(fileStream)`) om du kör på .NET 6+ och behöver prestanda. |
| Relativa sökvägar går sönder när markdown‑filen flyttas | Sökvägen är relativ till markdown‑filens plats. | Behåll `Doc.md` och `Resources`‑mappen tillsammans, eller justera callbacken för att använda ett annat relativt prefix (t.ex. `../assets`). |

---

## Steg 6: Utöka lösningen (vad om du behöver mer kontroll?)

- **Multiple output formats:** Ersätt `MarkdownSaveOptions` med `HtmlSaveOptions` eller `PdfSaveOptions` samtidigt som du behåller samma callback—Aspose.Words kommer att anropa den för varje bild oavsett format.
- **Custom image naming:** Om du vill byta namn på bilder (t.ex. `figure-01.png`), ändra `args.ResourceFileName` i callbacken innan du skriver filen.
- **Embedding images as Base64:** Sätt `args.ResourceFileName` till en data‑URI (`data:image/png;base64,...`) och hoppa över filskrivningen. Detta är praktiskt för markdown‑exporter i en enda fil.

---

## Slutsats

Du har nu ett fullt funktionellt C#‑program som **converts Word to markdown**, **extracts images from word**, **creates a resources folder**, och garanterar en ren **markdown image relative path** för varje bild. Koden är självständig, fungerar med den senaste versionen av Aspose.Words, och kan enkelt läggas in i vilket .NET‑projekt som helst med minimal ansträngning.

Nästa steg? Prova att mata in den genererade markdown‑filen i en statisk webbplatsgenerator som Hugo eller Jekyll, eller experimentera med callbacken för att bädda in bilder direkt som Base64‑strängar. Om du stöter på kantfall—t.ex. SVG‑bilder eller ovanligt stora filer—titta tillbaka på tabellen “Vanliga fallgropar”; en liten justering löser oftast problemet.

Lycka till med kodandet, och må din markdown alltid peka på rätt mapp!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}