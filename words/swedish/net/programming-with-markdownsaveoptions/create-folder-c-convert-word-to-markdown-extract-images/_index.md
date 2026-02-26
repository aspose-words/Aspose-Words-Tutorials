---
category: general
date: 2026-02-26
description: Skapa mapp C#‑handledning som visar hur man konverterar Word till markdown,
  extraherar bilder från docx och kopierar ström till fil – allt i ett steg.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: sv
og_description: Create folder C#‑handledning guidar dig genom att konvertera Word
  till markdown, extrahera bilder från docx och kopiera ström till fil med tydliga
  kodexempel.
og_title: Skapa mapp C# – Konvertera Word till Markdown och extrahera bilder
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Skapa mapp C# – Konvertera Word till Markdown och extrahera bilder
url: /sv/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

.

Let's assemble.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa mapp C# – Konvertera Word till Markdown & Extrahera bilder

Har du någonsin behövt **create folder C#** samtidigt som du konverterar ett Word‑dokument till markdown och drar ut varje bild? Du är inte ensam som kliar dig i huvudet över detta. I många automationspipelines hamnar du med att jonglera filsystemuppgifter, formatkonvertering och binär datahantering — allt i ett.  

I den här guiden går vi igenom en komplett, körbar lösning som gör exakt det: den skapar en mål katalog, konverterar en `.docx` till markdown, extraherar varje inbäddad bild och använder **copy stream to file**‑logik så att bilderna hamnar där du vill ha dem. Inga externa skript, inga manuella steg. Bara ren C# och Aspose.Words‑biblioteket.

> **Vad du får**  
> * En tydlig mappstruktur redo för markdown och resurser  
> * En markdown‑fil som refererar till de extraherade bilderna korrekt  
> * Fullständig källkod som du kan släppa in i vilket .NET‑projekt som helst  

Innan vi dyker ner, se till att du har:

* .NET 6.0 (eller senare) SDK installerat – koden använder moderna språkfunktioner.  
* En licens för **Aspose.Words for .NET** (gratis provversion fungerar för testning).  
* Visual Studio 2022 eller din föredragna editor.  

Om du undrar *varför* du skulle vilja extrahera bilder istället för att bädda in dem, tänk på statiska webbplatsgeneratorer: de älskar markdown med relativa bildvägar, och att hålla resurserna i en dedikerad mapp gör allt prydligt och cache‑vänligt.

---

## Skapa mapp C# och förbered utdata‑struktur

Det första vi behöver är en plats på disken där allt ska ligga. Detta steg är där **create folder C#**‑åtgärden sker, och det är förvånansvärt enkelt tack vare `Directory.CreateDirectory`. Metoden är idempotent — den kastar inte ett undantag om mappen redan finns, vilket sparar oss från extra kontroller.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**Varför detta är viktigt:**  
Att skapa mapparna i förväg garanterar att de senare sparstegen inte misslyckas med `DirectoryNotFoundException`. Det ger dig också en förutsägbar layout: `output/markdown` för `.md`‑filen och `output/MyImages` för varje bild vi drar ut.

> **Proffstips:** Om du kör programmet upprepade gånger kan du vilja rensa bildmappen först (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) för att undvika föråldrade filer.

---

## Konvertera Word till Markdown med Aspose.Words

Nu när katalogträdet är klart, låt oss omvandla Word‑dokumentet till markdown. Aspose.Words gör det tunga arbetet — ingen krångel med OpenXML eller tredjepartskonverterare.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**Vad händer under huven?**  
`MarkdownSaveOptions` instruerar Aspose att generera markdown‑syntax. Som standard skulle biblioteket lägga bilder i samma mapp som markdown‑filen med automatiskt genererade namn. Genom att tillhandahålla en `ResourceSavingCallback` avbryter vi det beteendet och **copy stream to file** på en plats vi väljer.

---

## Extrahera bilder från DOCX och spara dem

Callback‑klassen implementerar `IResourceSavingCallback`. Inuti får vi ett `ResourceSavingArgs`‑objekt som innehåller den ursprungliga bildströmmen och det föreslagna filnamnet. Vi skriver sedan den strömmen till disk, byter namn på filen om vi vill, och meddelar Aspose att vi har hanterat den.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Så här kommer markdown att se ut

Efter konverteringen kommer den genererade `output.md` att innehålla rader som:

```markdown
![Image 1](MyImages/img_picture1.png)
```

Eftersom vi ändrade `args.ResourceFileName` till en relativ sökväg pekar markdownen direkt på den mapp vi skapade. Detta är exakt vad statiska webbplatsgeneratorer förväntar sig.

**Hantering av kantfall:**  
*Om dokumentet innehåller dubbla bildnamn*, så undviker prefixet `img_` plus det ursprungliga namnet vanligtvis kollisioner, men du kan också lägga till ett GUID (`Guid.NewGuid()`) för absolut unikhet.

---

## Kopiera ström till fil – hantera bilddata

Du kanske undrar varför vi inte bara anropar `File.WriteAllBytes`. Svaret ligger i **strömflexibilitet**. `args.Stream` kan vara ett minnesström, ett nätverksström eller någon annan implementation. Genom att använda `CopyTo` förblir vi agnostiska och låter .NET hantera buffertstorlekar effektivt.

Här är en kompakt hjälpfunktion om du någonsin behöver kopiera en generisk ström någon annanstans:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

Du kan ersätta den inlinjekopieringen i `ImageSavingCallback` med ett anrop till `CopyStreamToFile` om du föredrar ett single‑responsibility‑tillvägagångssätt.

---

## Fullt körbart exempel

När du sätter ihop alla bitarna får du ett självständigt program som du kan köra från kommandoraden:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**Förväntat resultat**

* `output/markdown/output.md` – en markdown‑fil vars bildreferenser ser ut som `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – en PNG/JPEG‑fil per bild som ursprungligen fanns i `input.docx`.  

Öppna markdown‑filen i någon visare (VS Code, GitHub eller en statisk webbplatsgenerator) så kommer du att se bilderna renderade exakt där de hörde hemma i det ursprungliga Word‑dokumentet.

---

## Vanliga frågor & felsökning

| Fråga | Svar |
|----------|--------|
| **Vad händer om mål‑mappen redan har filer?** | `Directory.CreateDirectory` skriver inte över. Om du behöver en ren körning, ta bort

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}