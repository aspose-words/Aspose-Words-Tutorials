---
category: general
date: 2026-06-17
description: Hantera teckensnittsersättning i Aspose.Words och upptäck saknade teckensnitt
  snabbt med den här steg‑för‑steg‑handledningen för .NET‑utvecklare.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: sv
og_description: Hantera teckensnittssubstitution i Aspose.Words och lär dig hur du
  upptäcker saknade teckensnitt i dina dokument med tydliga kodexempel.
og_title: Hantera teckensnittssubstitution i Aspose.Words – Fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Hantera teckensnittsbyte i Aspose.Words – Komplett programmeringsguide
url: /sv/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hantera teckensnittssubstitution i Aspose.Words – Komplett programmeringsguide

Har du någonsin funderat på hur du **hanterar teckensnittssubstitution** när ett Word‑dokument refererar till ett teckensnitt som inte är installerat på servern? Du är inte ensam. I många verkliga applikationer – tänk fakturageneratorer eller automatiska rapporttjänster – orsakar saknade teckensnitt tysta återgångar som förstör layouten.  

Det goda nyheten är att Aspose.Words erbjuder ett inbyggt varningssystem som låter dig **upptäcka saknade teckensnitt** och reagera på det sätt du önskar. I den här handledningen går vi igenom hur du registrerar en varningshanterare, laddar ett dokument och plockar ut de exakta teckensnittssubstitutions‑händelserna du behöver känna till. I slutet ser du också hur du svarar på den klassiska frågan “**hur upptäcker man saknade teckensnitt?**” med ren, produktionsklar kod.

## Vad den här handledningen täcker

* Konfigurera Aspose.Words så att varningar avfyras för varje teckensnittssubstitution.  
* Fånga dessa varningar i en anpassad hanterare så att du kan logga, ersätta eller avbryta.  
* Använd den fångade datan för att **upptäcka saknade teckensnitt** innan dokumentet sparas eller renderas.  
* Tips för felsökning av kantfall – som när ett reservteckensnitt väljs tyst.  
* Ett komplett, körbart exempel som du kan klistra in i vilken .NET‑konsolapp som helst.

> **Förutsättningar** – Du behöver ett aktuellt .NET‑SDK (6.0+ fungerar bra), en giltig Aspose.Words for .NET‑licens (eller en temporär utvärderingsnyckel) och ett exempel‑DOCX‑dokument som medvetet refererar till ett teckensnitt du inte har installerat. Inga andra tredjepartsbibliotek krävs.

---

## ## Hantera teckensnittssubstitution med en anpassad varningshanterare

Aspose.Words skapar ett `WarningInfo`‑objekt varje gång det inte kan hitta ett begärt teckensnitt. Som standard ignoreras dessa varningar, vilket är anledningen till att du ofta aldrig märker en substitution. För att **hantera teckensnittssubstitution** ersätter du den standardvarningshanteraren med en som faktiskt gör något.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Varför detta fungerar

* `FontSettings.DefaultWarningHandler` är en global statisk egenskap – när du har satt den används **varje** Aspose.Words‑operation i den aktuella AppDomain‑en din delegat.  
* `WarningInfoCollectionHandler` får ett `WarningInfo`‑objekt som innehåller `WarningType` och en mänskligt läsbar `Description`. Filtrering på `WarningType.FontSubstitution` säkerställer att du bara ser de händelser du bryr dig om.  
* Att anropa `doc.Save` tvingar biblioteket att lösa alla teckensnitt, vilket är när varningarna avfyras. Om du bara behöver inspektera dokumentet utan att spara kan du istället anropa `doc.UpdatePageLayout()`.

**Förväntad konsolutskrift** (förutsatt att det saknade teckensnittet är “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Den raden är ditt bevis på att biblioteket **upptäckte saknade teckensnitt** och valde ett reservteckensnitt.

---

## ## Upptäck saknade teckensnitt innan rendering

Ibland vill du stoppa processen helt om ett obligatoriskt teckensnitt saknas – kanske för att varumärkesriktlinjer kräver exakt typografi. Varningshanteraren kan utökas för att samla alla meddelanden om saknade teckensnitt i en lista, varpå du kan fatta ett beslut.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Hur detta svarar på “hur upptäcker man saknade teckensnitt”

* Listan `missingFonts` fungerar som en huvudbok över varje substituerings‑händelse.  
* Efter `UpdatePageLayout` kan du inspektera listan och bestämma om du ska fortsätta, logga eller kasta ett undantag.  
* Detta mönster fungerar för alla utdataformat (PDF, HTML, bilder) eftersom varningssystemet är format‑agnostiskt.

---

## ## Avancerat tips: Ersätt saknade teckensnitt med ett specifikt reservteckensnitt

Om du har ett företags‑teckensnitt som måste användas kan du instruera Aspose.Words att automatiskt ersätta alla saknade teckensnitt med ditt reservteckensnitt. Detta är praktiskt när du vill att dokumentet ändå ska se acceptabelt ut utan manuell efterbehandling.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Placera kodsnutten **före** du laddar dokumentet. Nu kommer alla saknade teckensnitt – oavsett deras ursprungliga namn – att bytas ut mot “Calibri” (eller “Arial” om Calibri saknas). Du får fortfarande varningen, men dokumentet renderas med det teckensnitt du kontrollerar.

---

## ## Vanliga fallgropar & hur du undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|---------|
| **Varningar försvinner efter första anropet** | Den statiska `DefaultWarningHandler` skrivs över senare i appen. | Sätt hanteraren **en gång** vid applikationsstart, eller spara en referens och åter‑tilldela om du ändrar den. |
| **Endast det första saknade teckensnittet rapporteras** | Vissa API:er batchar varningar; du måste anropa `UpdatePageLayout` eller `Save` för att tömma kön. | Tvinga en layoutuppdatering eller spara i det format du avser att generera. |
| **Substitution sker fortfarande trots avbrytande** | Varningshanteraren körs *efter* att substitutionen redan har skett. | Använd hanteraren för att **logga** och sedan kasta ett undantag för att stoppa vidare bearbetning. |
| **Saknade teckensnitt i Linux‑containrar** | Linux saknar ofta Windows‑teckensnittskatalogen, vilket leder till många substitutioner. | Montera nödvändiga teckensnitt i containern eller använd `FontSettings.SetFontsFolder` för att peka på en egen teckensnittsmapp. |

---

## ## Upptäck teckensnittssubstitution i ett Web‑API‑scenario

Om du levererar dokument via ASP.NET Core vill du förmodligen inte skriva till konsolen. Samla i stället varningarna och returnera dem som en del av HTTP‑svaret.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Nu **upptäcker API‑et saknade teckensnitt** och returnerar en tydlig JSON‑payload innan någon PDF genereras. Detta är en praktisk illustration av “hur upptäcker man saknade teckensnitt” i en produktionsklar tjänst.

---

## ## Testa din implementation

1. **Skapa ett test‑DOCX** som refererar till ett teckensnitt du vet saknas på maskinen (t.ex. “Comic Sans MS” i en minimal Docker‑image).  
2. Kör konsol‑appen eller API‑endpointen.  
3. Verifiera att konsolen (eller HTTP‑svaret) listar varningsmeddelandet om substitution.  
4. Eventuellt, öppna den resulterande PDF‑filen och kontrollera teckensnittsegenskaperna – Aspose.Words bör visa det reservteckensnitt du konfigurerat.

Om du ser varningen men PDF‑filen ändå använder ett oväntat teckensnitt, dubbelkolla ordningen i `SubstitutionSettings`; den första matchen vinner.

---

## ## Slutsats

Vi har gått igenom allt du behöver för att **hantera teckensnittssubstitution** i Aspose.Words, från att registrera en varningshanterare till att programatiskt **upptäcka saknade teckensnitt** och till och med ersätta dem med ett företags‑teckensnitt. Genom att utnyttja det inbyggda varningssystemet får du full insyn i varje “teckensnitt ej hittat”‑händelse, vilket direkt svarar på frågan “**hur upptäcker man saknade teckensnitt?**” som varje utvecklare ställer sig när dokumentgenerering automatiseras.

Vad blir nästa steg? Prova att kombinera denna logik med **dynamisk teckensnittsladdning** (`FontSettings.SetFontsFolder`) för att stödja användaruppladdade teckensnitt i realtid, eller utöka varningshanteraren så att den skriver poster till en central loggtjänst som Serilog. Ju mer du instrumenterar teckensnittshanteringen, desto pålitligare blir din dokumentpipeline.

Har du ett knepigt teckensnittssubstitutions‑scenario du kämpar med? Lämna en kommentar nedan så felsöker vi tillsammans. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aktivera varningar för teckensnittssubstitution i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Hur man laddar DOCX och upptäcker saknade teckensnitt – Komplett C#‑guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}