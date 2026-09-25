---
category: general
date: 2026-02-24
description: Lär dig hur du använder Aspose Load Options för att återställa korrupta
  DOCX-filer, konvertera docx till markdown och konvertera Word till PDF med LaTeX‑ekvationer.
draft: false
keywords:
- aspose load options
- convert docx to markdown
- convert word to pdf
- recover corrupted docx
- export equations as latex
language: sv
og_description: Behärska Aspose Load Options för att återställa korrupta DOCX, konvertera
  docx till markdown och exportera ekvationer som LaTeX samtidigt som du genererar
  PDF/UA‑2-filer.
og_title: Aspose‑laddningsalternativ – Konvertera DOCX till Markdown och PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: Aspose laddningsalternativ – Konvertera DOCX till Markdown och PDF
url: /sv/net/programming-with-loadoptions/aspose-load-options-convert-docx-to-markdown-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Konvertera DOCX till Markdown & PDF

Har du någonsin undrat hur **aspose load options** låter dig rädda en trasig Word‑fil och omvandla den till ren Markdown eller en kompatibel PDF? Du är inte ensam. Många utvecklare stöter på problem när en DOCX kommer korrupt, eller när ekvationer försvinner under konverteringen. I den här handledningen går vi igenom en komplett, klar‑till‑kör C#‑lösning som inte bara *återställer korrupta docx* utan också **convert docx to markdown** och **convert word to pdf** medan **export equations as latex**.

Vi kommer att gå igenom allt från att konfigurera återhämtningsläget till att ladda upp extraherade bilder till en molnbucket, och slutligen producera en PDF/UA‑2‑fil som uppfyller tillgänglighetsstandarder. När du är klar har du en enda kodbas som hanterar båda transformationerna med bara några rader konfiguration.

> **Vad du får:**  
> • Ett robust sätt att läsa in vilken DOCX som helst, även om den är delvis skadad.  
> • Markdown‑utmatning som behåller OfficeMath‑ekvationer som LaTeX.  
> • PDF/UA‑2‑utmatning med flytande former bevarade som inline‑taggar.  
> • En återanvändbar bild‑uppladdnings‑callback för molnlagring.

---

## Förutsättningar

- **Aspose.Words for .NET** (v23.12 eller nyare).  
- .NET 6+ (något nyligen SDK fungerar).  
- Ett molnlagrings‑SDK du föredrar (exemplet använder en platshållarmetod).  
- Grundläggande kunskap om C# och Visual Studio eller VS Code.

Om du ännu inte har installerat Aspose.Words, kör:

```bash
dotnet add package Aspose.Words
```

---

## Steg 1: Läs in dokumentet med Aspose Load Options

Det första du behöver är ett pålitligt sätt att öppna en potentiellt trasig DOCX. Det är här **aspose load options** glänser – de låter dig instruera biblioteket att försöka återhämta sig istället för att kasta ett undantag.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Configure LoadOptions to recover corrupted documents.
LoadOptions loadOptions = new LoadOptions
{
    // RecoveryMode.Recover tells Aspose to salvage as much as possible.
    RecoveryMode = RecoveryMode.Recover
};

// Load the source file. Replace the path with your own.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Varför detta är viktigt:**  
När en Word‑fil är trunkerad eller innehåller felaktig XML avbryter standardläsaren. Genom att aktivera `RecoveryMode.Recover` parsar Aspose det den kan, hoppar över de trasiga delarna och ger dig fortfarande ett användbart `Document`‑objekt. Detta är ryggraden i scenariot *recover corrupted docx*.

---

## Steg 2: Konfigurera Markdown‑konvertering (Exportera ekvationer som LaTeX)

Nu när dokumentet finns i minnet kan vi ställa in hur det ska sparas som Markdown. Två saker är kritiska:

1. **OfficeMathExportMode.LaTeX** – säkerställer att alla matematiska ekvationer blir LaTeX‑snuttar, vilket bevarar deras semantik.  
2. **ResourceSavingCallback** – en hook som låter oss ladda upp extraherade bilder till en molnbucket istället för att skriva dem lokalt.

```csharp
using Aspose.Words.Saving;

// Prepare Markdown save options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This converts OfficeMath objects to LaTeX.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Hook to upload images to the cloud.
    ResourceSavingCallback = new CloudImageCallback()
};

// Save as Markdown.
document.Save("YOUR_DIRECTORY/result.md", markdownOptions);
```

**Proffstips:** Om du inte behöver LaTeX, byt `OfficeMathExportMode` till `Image`. Men för vetenskapliga dokument är LaTeX mycket mer portabelt.

---

## Steg 3: Implementera molnbild‑callbacken

Aspose anropar `IResourceSavingCallback.ResourceSaving` för varje extern resurs (bilder, diagram osv.). Nedan är en minimal implementation som låtsas ladda upp strömmen till ett CDN och returnerar en publik URL.

```csharp
using Aspose.Words.Saving;
using System.IO;

public class CloudImageCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Upload the image stream to your cloud storage and get a URL.
        string url = UploadToCloud(args.Stream, args.FileName);

        // Point the Markdown image reference to the CDN URL.
        args.Uri = url;

        // Prevent Aspose from writing a local copy.
        args.KeepOriginalDocumentUri = false;
    }

    private string UploadToCloud(Stream data, string name)
    {
        // Replace this stub with your actual SDK call.
        // For demo purposes we just return a placeholder.
        return $"https://cdn.example.com/{name}";
    }
}
```

**Vad händer om du inte har en molnbucket?**  
Du kan helt enkelt sätta `args.Uri = $"images/{args.FileName}"` och låta Aspose skriva filerna bredvid Markdown‑filen. Callback‑metoden ger dig full kontroll.

---

## Steg 4: Konfigurera PDF‑konvertering (Konvertera Word till PDF med UA‑2‑kompatibilitet)

När samma dokument ska bli en PDF, särskilt en som måste uppfylla tillgänglighetsstandarder, erbjuder Aspose `PdfSaveOptions`. Två inställningar är avgörande för en ren konvertering:

- **Compliance = PdfCompliance.PdfUa2** – producerar en PDF/UA‑2‑fil, ISO‑standarden för tillgängliga PDF‑filer.  
- **ExportFloatingShapesAsInlineTag = true** – behåller flytande former (som textrutor) i rätt ordning.

```csharp
using Aspose.Words.Saving;

// Prepare PDF save options.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // Enforce PDF/UA‑2 compliance.
    Compliance = PdfCompliance.PdfUa2,

    // Preserve layout of floating shapes.
    ExportFloatingShapesAsInlineTag = true
};

// Save as PDF.
document.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
```

**Varför detta fungerar:**  
Genom att sätta `Compliance` får Aspose inbäddat nödvändiga taggar, alternativ text och strukturelement. Flaggan `ExportFloatingShapesAsInlineTag` ser till att former som annars skulle flyta över text förankras inline, vilket förhindrar layoutöverraskningar i den slutgiltiga PDF‑filen.

---

## Steg 5: Fullt end‑to‑end‑exempel

Här är hela programmet som du kan kopiera och klistra in i en konsolapp.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

namespace AsposeDocxConversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load with recovery.
            LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 2️⃣ Convert to Markdown (export equations as LaTeX, upload images).
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                ResourceSavingCallback = new CloudImageCallback()
            };
            doc.Save("YOUR_DIRECTORY/result.md", mdOptions);
            Console.WriteLine("✅ Markdown saved.");

            // 3️⃣ Convert to PDF/UA‑2 (preserve floating shapes).
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                Compliance = PdfCompliance.PdfUa2,
                ExportFloatingShapesAsInlineTag = true
            };
            doc.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
            Console.WriteLine("✅ PDF/UA‑2 saved.");
        }
    }

    // Callback for uploading images.
    public class CloudImageCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string url = UploadToCloud(args.Stream, args.FileName);
            args.Uri = url;
            args.KeepOriginalDocumentUri = false;
        }

        private string UploadToCloud(Stream data, string name)
        {
            // Insert real SDK code here.
            return $"https://cdn.example.com/{name}";
        }
    }
}
```

**Förväntad utmatning:**  
När du kör programmet skapas två filer i `YOUR_DIRECTORY`:

- `result.md` – ett Markdown‑dokument där varje ekvation visas som `$$\LaTeX$$` och bildlänkar pekar på `https://cdn.example.com/...`.  
- `result.pdf` – en PDF/UA‑2‑kompatibel fil som kan öppnas i Adobe Reader med tillgänglighetskontrollen godkänd.

Du kan öppna Markdown‑filen i vilken editor som helst eller skicka den till en static‑site‑generator, och PDF‑filen kan distribueras till användare som behöver ett tillgängligt format.

---

## Vanliga frågor & kantfall

| Fråga | Svar |
|----------|--------|
| **Vad händer om DOCX-filen är helt oläslig?** | Även med `RecoveryMode.Recover` kan en helt korrupt fil kasta `FileCorruptedException`. Omge laddningsanropet med en `try/catch` och falla tillbaka till en användarvänlig fel­sida. |
| **Kan jag ändra bildformatet under uppladdning?** | Ja. Inuti `UploadToCloud` kan du använda ett bildbehandlingsbibliotek (t.ex. ImageSharp) för att ändra storlek eller konvertera till WebP innan du skickar till CDN:n. |
| **Behöver jag en licens för Aspose.Words?** | Den kostnadsfria provversionen fungerar för upp till 20 sidor. För produktion tar en kommersiell licens bort utvärderingsvattenstämpeln och låser upp alla funktioner. |
| **Vad händer om jag vill behålla ekvationer som bilder istället för LaTeX?** | Byt `OfficeMathExportMode` till `Image` i `MarkdownSaveOptions`. Callback‑funktionen får då PNG‑strömmar som du kan ladda upp. |
| **Hur lägger jag till anpassad metadata i PDF‑filen?** | Använd `pdfOptions.CustomProperties.Add("Author", "Your Name")` innan du anropar `Save`. |

---

## 🎯 Sammanfattning

Vi har just demonstrerat hur **aspose load options** ger dig möjlighet att **recover corrupted docx**, **convert docx to markdown** och **convert word to pdf** samtidigt som du **export equations as latex**. Tillvägagångssättet är modulärt: du kan byta bild‑uppladdnings‑callback, ändra efterlevnadsnivå eller till och med lägga till ett DOCX‑till‑HTML‑steg med liknande alternativ.

Nästa steg du kan utforska:

- Integrera denna pipeline i ett ASP .NET Core‑API så att användare kan ladda upp filer och få både Markdown och PDF direkt.  
- Ersätt den platshållande CDN‑URL:en med Azure Blob Storage eller Amazon S3‑SDK‑anrop.  
- Lägg till ett efterbearbetningssteg som kör en Markdown‑linter för att säkerställa ren utmatning.  

Känn dig fri att experimentera – kanske lägger du till en tabell‑till‑CSV‑export eller ett anpassat PDF‑sidfot. Aspose.Words‑API:et är tillräckligt flexibelt för de flesta dokument‑automatiseringsscenarier.

**Happy coding!** Om du stöter på problem, lämna en kommentar nedan eller kontakta Aspose‑community‑forumen.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}