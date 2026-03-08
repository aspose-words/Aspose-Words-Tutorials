---
category: general
date: 2026-03-08
description: Anpassade teckensnittsinställningar låter dig ställa in teckensnittsinställningar,
  ladda ett Word‑dokument säkert och hantera saknade teckensnitt med Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: sv
og_description: Anpassade teckensnittsinställningar låter dig ställa in teckensnittsinställningar,
  ladda Word-dokument säkert och hantera saknade teckensnitt med Aspose.Words.
og_title: Anpassade teckensnittsinställningar i C# – Läs in Word och hantera saknade
  teckensnitt
tags:
- Aspose.Words
- C#
- Font Management
title: Anpassade teckensnittsinställningar i C# – Ladda Word & hantera saknade teckensnitt
url: /sv/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anpassade teckensnittsinställningar i C# – Ladda Word och hantera saknade teckensnitt

Har du någonsin funderat på hur **anpassade teckensnittsinställningar** fungerar när en Word‑fil refererar till teckensnitt du inte har installerade? Det är ett vanligt problem – ditt dokument ser bra ut på en maskin, men plötsligt byter varje stycke till ett reservteckensnitt på en annan.

Det goda nyheterna? Med Aspose.Words kan du **ställa in teckensnittsinställningar**, **ladda Word‑dokument** och **hantera saknade teckensnitt** i ett enda smidigt flöde. Nedan hittar du ett komplett, färdigt‑att‑köra exempel som visar exakt hur du gör, samt “varför” bakom varje steg.

## Vad du kommer att lära dig

I den här guiden går vi igenom:

* Skapa ett `LoadOptions`‑objekt och fästa en `FontSettings`‑instans.  
* Registrera en varnings‑callback så att du kan se vilka teckensnitt som ersätts.  
* Ladda en DOCX‑fil som eventuellt saknar teckensnitt och skriva ut ersättningsdetaljer till konsolen.  

När du är klar kan du distribuera din C#‑app med förtroende, med vetskapen om att varje saknad‑teckensnitt‑scenario loggas och kan åtgärdas senare.

> **Förutsättning:** Aspose.Words for .NET (v23.12 eller nyare) installerat via NuGet, samt grundläggande kunskaper om C#‑konsolappar.

---

## Anpassade teckensnittsinställningar – Konfigurera LoadOptions

Det första du behöver är ett `LoadOptions`‑objekt. Detta talar om för Aspose.Words hur den inkommande filen ska behandlas. Genom att tilldela en ny `FontSettings`‑instans ger vi biblioteket en plats att leta efter anpassade teckensnitt.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Varför detta är viktigt:**  
Om du hoppar över `FontSettings` faller Aspose.Words tillbaka på systemets standardteckensnittssamling. Det betyder att alla saknade teckensnitt tyst ersätts, och du får ingen information om vilka som byttes ut. Genom att skapa en explicit `FontSettings`‑behållare får du full kontroll över sökprocessen.

---

## Ställ in teckensnittsinställningar på LoadOptions

Nu när vi har ett `FontSettings`‑objekt kanske du undrar var du ska peka det. Vanligtvis lägger du till en mapp som innehåller de teckensnitt du levererar med din applikation:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Om du inte har en privat mapp kan du utelämna detta block – Aspose.Words kommer fortfarande att rapportera saknade teckensnitt via varnings‑callbacken.*

**Proffstips:** Använd flaggan `recursive: true` om dina teckensnitt är spridda över undermappar. Det sparar dig från att manuellt lägga till varje sökväg.

---

## Ladda Word-dokument med anpassade teckensnittsinställningar

Med alternativen förberedda är det en enkel match att ladda dokumentet. `Document`‑konstruktorn accepterar filsökvägen och de `LoadOptions` vi just byggt.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Vad händer under huven?**  
Aspose.Words parsar DOCX‑filen, kontrollerar varje `<w:font>`‑referens och konsulterar de `FontSettings` du levererat. Om ett teckensnitt inte hittas triggas en varning av typen `FontSubstitution`. Vår anpassade hanterare (visas nedan) fångar dessa varningar.

---

## Hantera saknade teckensnitt med varningsåteruppringning

`IWarningCallback`‑gränssnittet låter dig reagera på eventuella problem som uppstår under laddning. Att implementera det är enkelt:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

När dokumentet laddas kommer varje saknat teckensnitt att ge en rad som:

```
Font substituted: Arial -> Liberation Sans
```

**Varför du bör logga detta:**  
I produktion kan du omdirigera dessa meddelanden till en fil eller ett telemetrisystem, vilket gör det enkelt att identifiera vilka teckensnitt du behöver paketera eller licensiera.

---

## Fullt fungerande exempel

Nedan är ett självständigt konsolprogram som binder ihop allt. Kopiera‑klistra in det i ett nytt .NET Core‑konsolprojekt och kör **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Förväntad output** (förutsatt att `input.docx` använder ett teckensnitt du inte har):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Om alla teckensnitt finns kommer du bara att se den sista bekräftelseraden.

---

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Vad händer om jag behöver bädda in de saknade teckensnitten i PDF:en?** | Efter laddning, anropa `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` och aktivera inbäddning med `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Kan jag undertrycka varningarna istället för att logga dem?** | Ja – sätt `loadOptions.WarningCallback = null;` eller implementera callbacken så att den ignorerar icke‑teckensnittsvarningar. |
| **Fungerar detta med `.doc` och `.rtf`‑filer?** | Absolut. Samma `LoadOptions`‑objekt gäller för alla format som stöds av Aspose.Words. |
| **Är callbacken trådsäker?** | Callbacken körs på samma tråd som laddar dokumentet, så du kan säkert skriva till konsolen. För flertrådade scenarier, använd en samtidig samling eller ett loggningsramverk. |

---

## Proffstips & fallgropar

* **Proffstips:** Om du levererar ett teckensnitt som inte är installerat på målmaskinen, lägg till det i mappen du skickar till `SetFontsFolder`. Detta garanterar deterministisk rendering.  
* **Var uppmärksam på licensiering:** Vissa teckensnitt kräver kommersiella licenser för inbäddning. Kontrollera alltid teckensnittets EULA innan du paketerar det.  
* **Prestanda‑notering:** Att ladda stora bibliotek av teckensnitt kan sakta ner dokumentparsing. Håll mappen slank – inkludera bara de teckensnitt du faktiskt behöver.  
* **Edge case:** När ett dokument refererar till ett teckensnitt via dess *PostScript‑namn* istället för familjenamnet, löser Aspose.Words det fortfarande så länge teckensnittsfilen finns i sökvägen.

---

## Slutsats

Du har nu ett komplett, produktionsklart mönster för att använda **anpassade teckensnittsinställningar** i C#. Genom att konfigurera `LoadOptions`, registrera en varnings‑callback och eventuellt peka på en privat teckensnittsmapp, kan du **ställa in teckensnittsinställningar**, **ladda Word‑dokument** på ett pålitligt sätt.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}