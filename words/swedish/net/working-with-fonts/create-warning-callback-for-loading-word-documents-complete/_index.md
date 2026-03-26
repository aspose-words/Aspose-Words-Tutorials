---
category: general
date: 2026-03-25
description: Skapa varningsåteruppringning för att ladda Word‑dokument och upptäcka
  saknade teckensnitt. Lär dig hur du konfigurerar teckensnittsinställningar i Aspose.Words
  för .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: sv
og_description: Skapa varningsåteruppringning för att ladda Word-dokument samtidigt
  som du upptäcker saknade teckensnitt. Denna guide visar hur du konfigurerar teckensnittsinställningar
  i Aspose.Words.
og_title: Skapa varningsåteruppringning – Ladda Word‑dokument och upptäck saknade
  teckensnitt
tags:
- Aspose.Words
- C#
- Font handling
title: Skapa varningscallback för inläsning av Word-dokument – Komplett guide
url: /sv/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa varningsåteruppringning – Ladda Word‑dokument & upptäck saknade teckensnitt

Har du någonsin behövt **skapa en varningsåteruppringning** när du laddar ett Word‑dokument och undrat varför vissa teckensnitt bara försvinner? Du är inte ensam. I många företagsapplikationer orsakar saknade teckensnitt layoutkatastrofer, och utan en korrekt återuppringning kanske du aldrig ens märker problemet.  

Den goda nyheten? Med Aspose.Words för .NET kan du **ladda Word‑dokument**, **upptäcka saknade teckensnitt** och **konfigurera teckensnittsinställningar** i bara några få snygga kodrader. I den här handledningen går vi igenom ett komplett, körbart exempel, förklarar varför varje del är viktig och visar hur du verifierar att varningsåteruppringningen gör sitt jobb.

> **Vad du får med dig**  
> * Ett komplett C#‑program som laddar en DOCX, rapporterar eventuella teckensnittsersättningar och låter dig anpassa sökvägar för teckensnitt.  
> * Förståelse för klasserna `FontSettings`, `LoadOptions` och `IWarningCallback`.  
> * Tips för att hantera kant‑fall som inbäddade teckensnitt eller systemomfattande teckensnittsmappar.

---

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.7.2+) med en C#‑kompilator.  
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`).  
- En exempel‑Word‑fil (`input.docx`) som använder minst ett teckensnitt som inte är installerat på maskinen (t.ex. *Calibri Light* i en minimal Windows‑container).  
- Grundläggande kunskap om C#‑konsolappar.

Inga ytterligare bibliotek krävs; allt levereras med Aspose.Words.

---

## Steg 1: Skapa varningsåteruppringning för att upptäcka saknade teckensnitt

Den **primära** delen av detta pussel är en klass som implementerar `IWarningCallback`. Aspose.Words kommer att anropa denna återuppringning när den stöter på en situation som motiverar en varning – teckensnittsersättning är den vanligaste.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Varför detta är viktigt** – Utan en återuppringning måste du gå igenom loggar i efterhand. Genom att hantera varningar i realtid kan du besluta om du vill avbryta laddningen, ersätta det saknade teckensnittet med ett reservteckensnitt, eller helt enkelt logga problemet för senare granskning.

---

## Steg 2: Konfigurera FontSettings för anpassad teckensnittshantering

Innan vi faktiskt laddar dokumentet kan vi vilja tala om för Aspose.Words var det ska leta efter teckensnitt som saknas på systemet. Det är här `FontSettings` kommer in.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Varför detta är viktigt** – Genom att peka Aspose.Words på en mapp som innehåller de saknade teckensnitten undviker du ofta ersättning helt och hållet. När det inte är möjligt ger ett rimligt standardteckensnitt (som *Arial*) dokumentet läsbarhet.

---

## Steg 3: Ladda Word‑dokument med den konfigurerade varningsåteruppringningen

Nu knyter vi ihop allt: vi skapar `LoadOptions`, kopplar in våra `FontSettings` och `FontWarningHandler` och laddar slutligen dokumentet.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Varför detta är viktigt** – `LoadOptions` är den enda platsen där du konfigurerar *hur* ett dokument läses. Genom att tillhandahålla både teckensnittskonfigurationen och varningsåteruppringningen säkerställer vi att varje saknat teckensnitt både söks på rätt ställen **och** rapporteras omedelbart.

---

## Steg 4: Verifiera resultatet – vad bör du se?

Kör programmet i en konsol. Om `input.docx` använder ett teckensnitt som inte är installerat och inte heller finns i `C:\SharedFonts`, får du något liknande:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Om alla teckensnitt är tillgängliga visas varningsraden helt enkelt aldrig. Denna omedelbara återkopplingsslinga är ovärderlig i automatiserade dokument‑bearbetningspipelines där tysta teckensnittsersättningar kan bryta varumärkesriktlinjer.

---

## Steg 5: Vanliga fallgropar och bästa praxis‑tips

| Fallgrop | Så undviker du den |
|----------|--------------------|
| **Glömt att referera `Aspose.Words.Fonts`** | Se till att du har `using Aspose.Words.Fonts;` högst upp; annars klagar kompilatorn på saknade typer. |
| **Fel sökväg till teckensnittsmapp** | Dubbelkolla sökvägen och sätt `recursive: true` om du har undermappar. Använd `Path.GetFullPath` för felsökning. |
| **Flera varningsåteruppringningar** | Aspose.Words hedrar bara den sista `WarningCallback` du tilldelar. Håll en enda hanterare som delegaterar om du behöver mer komplex logik. |
| **Kör på en server utan UI** | Konsolutskrifter fungerar, men för webbappar vill du kanske logga till en fil eller ett övervakningssystem istället för `Console.WriteLine`. |
| **Stora dokument ger prestandaproblem** | Återanvänd en enda `FontSettings`‑instans över flera laddningar; att skapa den upprepade gånger kan vara kostsamt. |

**Pro‑tips:** Om du behöver *samla* varningar för senare analys, lagra dem i en `List<string>` i hanteraren istället för att skriva ut dem direkt.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Du kan sedan inspektera `handler.Messages` efter att dokumentet har laddats.

---

## Steg 6: Utöka lösningen – vad om jag behöver bädda in ett reservteckensnitt?

Ibland vill du att det saknade teckensnittet ska *bäddas in* i den genererade PDF‑filen så att nedströms‑visare ser exakt samma utseende. Efter att ha laddat dokumentet kan du tvinga inbäddning:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Detta kodstycke visar hur samma **konfigurera teckensnitt**‑metod kan utökas bortom enbart laddning.

---

## Fullt körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i ett nytt Console‑App‑projekt. Det innehåller alla delar som diskuterats ovan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Förväntad utskrift** (när ett saknat teckensnitt finns):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Om ingen ersättning sker visas bara framgångsmeddelandena.

---

## Slutsats

Vi har just **skapat en varningsåteruppringning** som på ett pålitligt sätt **upptäcker saknade teckensnitt** medan vi **laddar ett Word‑dokument** med Aspose.Words, och vi har visat hur man **konfigurerar teckensnittinställningar** för att styra var biblioteket letar efter teckensnitt och vilket reservteckensnitt som ska användas. Genom att koppla ihop `FontSettings` och `LoadOptions` får du full insyn i teckensnittsrelaterade problem – inga fler tysta layout‑buggar.

Nästa steg? Prova att byta ut `FontWarningHandler` mot en logger som skriver till en databas, eller experimentera med **teckensnittsersättningsregler** för att mappa specifika saknade teckensnitt till varumärkesgodkända alternativ. Du kan också utforska **dynamisk teckensnittsladdning** från molnlagring om din app körs i en containeriserad miljö.

Har du frågor om ett särskilt kantfall – som att hantera OpenType‑funktioner eller krypterade DOCX‑filer? Lämna en kommentar nedan, och lycka till med kodandet!  

---

![Skapa varningsåteruppringning diagram](https://example.com/images/create-warning-callback.png "Skapa varningsåteruppringning diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}