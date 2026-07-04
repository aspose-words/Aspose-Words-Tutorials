---
category: general
date: 2026-05-29
description: Lär dig hur du ställer in FontSettings i Aspose.Words och hanterar saknade
  teckensnitt på ett smidigt sätt. Steg‑för‑steg‑guide med komplett kod och bästa
  praxis.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: sv
og_description: Hur du ställer in FontSettings i Aspose.Words och snabbt hanterar
  saknade teckensnitt. Följ den här guiden för en komplett, körbar lösning.
og_title: Hur man ställer in FontSettings – Hantera saknade teckensnitt
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Hur man ställer in FontSettings – Hantera saknade typsnitt
url: /sv/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så ställer du in FontSettings – Hantera saknade teckensnitt

Har du någonsin undrat **hur man ställer in FontSettings** när du arbetar med Aspose.Words och plötsligt stöter på ett dokument som refererar till ett teckensnitt du inte har installerat? Det är ett vanligt problem, särskilt när du bearbetar kundlevererade filer på en server som bara har ett minimalt teckensnittssortiment. Den goda nyheten? Du kan fånga dessa luckor och **hantera saknade teckensnitt** utan att din app kraschar eller producerar fula PDF‑filer.

I den här handledningen går vi igenom ett verkligt scenario: att ladda en DOCX som begär “Calibri” medan din Linux‑container bara levereras med “DejaVu Sans”. Du kommer att se exakt hur du konfigurerar FontSettings, prenumererar på ersättningsvarningar och tillhandahåller reservteckensnitt så att dokumentet renderas precis som författaren avsåg. Ingen onödig text—bara koden du kan klistra in i ditt projekt idag.

## Förutsättningar

- .NET 6.0 eller senare (API:et fungerar likadant på .NET Framework 4.7+)
- Aspose.Words för .NET 23.10 eller nyare (NuGet‑paketnamnet är `Aspose.Words`)
- Ett grundläggande C#‑utvecklingsmiljö (Visual Studio, Rider eller VS Code)

Om du har dem, låt oss dyka in.

## Steg 1: Skapa FontSettings och lyssna på ersättningshändelser

Kärnan i lösningen är objektet `FontSettings`. Genom att fästa en hanterare på dess `FontSubstitutionWarning`‑händelse får du en live‑rapport varje gång Aspose.Words måste ersätta ett saknat teckensnitt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Varför detta är viktigt:**  
När motorn inte kan hitta *Calibri* kan den tyst falla tillbaka på *Arial*. Genom att lyssna på varningen behåller du en transparent revisionsspår—perfekt för felsökning eller efterlevnadsrapportering.

> **Proffstips:** Om du kör detta på en CI‑server, skicka utdata till en loggfil så att du kan granska vilka teckensnitt som saknades efter ett batch‑körning.

## Steg 2: Anslut FontSettings till LoadOptions

`LoadOptions` är porten för att styra hur ett dokument parsas. Genom att tilldela de `FontSettings` vi just konfigurerat kommer varje efterföljande `Document`‑laddning att följa vår ersättningslogik.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Vad händer under huven?**  
Under `Document`‑konstruktorn läser Aspose.Words XML‑filen i DOCX, löser upp teckensnittreferenser och—om ett teckensnitt inte hittas—utlöser varningen vi satte upp tidigare. Utan detta hook skulle du aldrig veta att en ersättning har skett.

## Steg 3: Ladda dokumentet och (valfritt) definera reservteckensnitt

Nu hämtar vi äntligen filen till minnet. Om du redan har en mapp med reservteckensnitt (t.ex. en katalog med OpenType‑teckensnitt som levereras med din app), tala om för `FontSettings` var den ska leta. Detta steg är valfritt men ofta det renaste sättet att *hantera saknade teckensnitt*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Varning för kantfall:**  
Om dokumentet innehåller ett anpassat teckensnitt inbäddat som en binär ström, kommer Aspose.Words att använda det automatiskt—ingen ersättning behövs. Varningen utlöses endast för *saknade* systemteckensnitt.

### Verifiera resultatet

Efter laddning kanske du vill spara dokumentet som PDF eller Word för att bekräfta att allt ser rätt ut.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

När du kör programmet kommer konsolen att skriva ut rader som:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Om du ser dessa meddelanden har du framgångsrikt **hanterat saknade teckensnitt** och vet exakt vilka ersättningar som skedde.

## Steg 4: Avancerat – Anpassade regler för teckensnittsersättning (valfritt)

Ibland behöver du deterministisk mappning, t.ex. alltid ersätta *Times New Roman* med *Liberation Serif*. Detta kan du uppnå med `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Varför bry sig?**  
Explicita regler ger dig kontroll över typografin, vilket säkerställer varumärkeskonsekvens i genererade PDF‑filer, särskilt när du producerar marknadsföringsmaterial.

## Vanliga fallgropar & hur man undviker dem

| Fallgrop | Symtom | Lösning |
|----------|--------|---------|
| **Ingen varningsutdata** | Du tror att teckensnitten är i ordning men dokumentet ser felaktigt ut. | Se till att `FontSubstitutionWarning` är fäst **innan** dokumentet laddas. |
| **Reservteckensnittsmappen skannas inte** | Ersättningar faller fortfarande tillbaka på systemstandarder. | Anropa `SetFontsFolder(path, true)` med det andra argumentet `true` för att rekursivt söka i undermappar. |
| **Prestandaförlust vid stora batcher** | Laddning av 10 000 dokument blir långsam. | Cacha en enda `FontSettings`‑instans och återanvänd den mellan laddningar; undvik att skapa om den varje gång. |
| **Inbäddade teckensnitt ignoreras** | Du förväntade dig att ett anpassat inbäddat teckensnitt skulle användas, men en ersättning sker. | Verifiera att källdokumentet DOCX faktiskt inbäddar teckensnittet (kontrollera i Word → Arkiv → Info → Teckensnitt). |

## Fullständigt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Det demonstrerar allt från händelsehantering till att spara den slutgiltiga PDF‑filen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Förväntad konsolutdata** (exempel):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Kör programmet, öppna `Output.pdf`, och du kommer att se texten renderad med reservteckensnitten—inga saknade‑glyph‑rutor, inga krascher.

## Slutsats

Du har nu ett robust, produktionsklart mönster för **hur man ställer in FontSettings** i Aspose.Words och **hanterar saknade teckensnitt** på ett elegant sätt. Genom att koppla `FontSubstitutionWarning`‑händelsen, peka på en reservteckensnittskatalog och (vid behov) definiera explicita ersättningsregler får du full insyn och kontroll över typografin i automatiserade dokumentpipelines.

Vad blir nästa steg? Prova att lägga till en anpassad teckensnittssamling för varumärkesspecifika typsnitt, eller utforska `FontSourceBase`‑API:et för att ladda teckensnitt från en databas eller molnlagring. Samma principer gäller—anslut bara en annan källa till `FontSettings`.

Har du frågor om kantfall, som att hantera höger‑till‑vänster‑skript eller emoji‑teckensnitt? Lämna en kommentar nedan, och lycka till med kodandet!

## Vad bör du lära dig härnäst?

- [Hur man fångar teckensnitt i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hur man laddar DOCX och upptäcker saknade teckensnitt – Komplett C#‑guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}