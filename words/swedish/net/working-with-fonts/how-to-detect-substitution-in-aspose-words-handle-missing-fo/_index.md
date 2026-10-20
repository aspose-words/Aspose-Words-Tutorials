---
category: general
date: 2026-04-24
description: Hur man upptäcker ersättning av saknade teckensnitt i Aspose.Words med
  C#. Denna guide visar hur du på ett pålitligt sätt hanterar saknade teckensnitt
  med FontSettings‑varningar.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: sv
og_description: Hur man upptäcker ersättning av saknade teckensnitt i Aspose.Words
  med C#. Lär dig hantera saknade teckensnitt med hjälp av FontSettings-varningar.
og_title: Hur man upptäcker ersättning i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Hur man upptäcker substitution i Aspose.Words – Hantera saknade teckensnitt
url: /sv/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man upptäcker substitution i Aspose.Words – Hantera saknade teckensnitt

Har du någonsin undrat **hur man upptäcker substitution** när ett dokument försöker använda ett teckensnitt som inte är installerat på din server? Det är ett vanligt problem, särskilt när du genererar PDF‑ eller Word‑filer i en automatiserad pipeline. Den goda nyheten är att Aspose.Words ger dig en inbyggd krok för att exakt identifiera den situationen, och du kan också **hantera saknade teckensnitt** på ett smidigt sätt.

I den här handledningen går vi igenom ett verkligt exempel som visar **hur man upptäcker substitution** via `FontSettings.Warning`‑händelsen, och vi förklarar hur du **hanterar saknade teckensnitt** utan att avbryta ditt bearbetningsflöde. När du är klar har du ett färdigt kodexempel, en tydlig förståelse för varför varje rad är viktig, och några tips för att undvika vanliga fallgropar.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även på .NET Framework)  
- Aspose.Words för .NET (NuGet‑paketet `Aspose.Words`) – version 23.11 eller nyare  
- Ett exempel‑dokument som refererar till ett teckensnitt du inte har installerat (t.ex. `MissingFont.docx`)  
- Visual Studio, VS Code eller någon C#‑IDE du föredrar  

Ingen extra konfiguration krävs utöver att lägga till NuGet‑paketet.

---

## Så upptäcker du substitution med FontSettings

Kärnan i **hur man upptäcker substitution** ligger i `FontSettings.Warning`‑händelsen. När Aspose.Words inte kan hitta ett efterfrågat teckensnitt, utlöser det en varning av typen `WarningType.FontSubstitution`. Genom att prenumerera på denna händelse får du en realtidsavisering, komplett med det ursprungliga teckensnittets namn och det teckensnitt som användes som reserv.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Varför detta fungerar:**  
- `LoadOptions.FontSettings` talar om för Aspose.Words att använda det `FontSettings`‑objekt du just skapade.  
- Att prenumerera på `Warning` ger dig en enda plats att övervaka *alla* teckensnittrelaterade problem, inte bara saknade teckensnitt.  
- `WarningType.FontSubstitution`‑filtret säkerställer att du bara reagerar på det exakta scenario du är intresserad av – själva essensen av **hur man upptäcker substitution**.

### Förväntad utskrift

Att köra koden ovan med ett dokument som refererar till ett icke‑existerande teckensnitt kommer att skriva ut något liknande:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Om dokumentet endast använder installerade teckensnitt förblir konsolen tyst – en tydlig signal att **hur man upptäcker substitution** lyckades utan falska larm.

---

## Hantera saknade teckensnitt på ett smidigt sätt

Att upptäcka en substitution är bara halva striden; du behöver också en strategi för att **hantera saknade teckensnitt** så att slutresultatet ser ut som avsett. Nedan följer tre praktiska tillvägagångssätt som du kan kombinera.

### 1. Tillhandahåll en reservteckensnittsmapp

Aspose.Words kan söka i ytterligare kataloger efter teckensnitt. Genom att peka den mot en mapp som innehåller de vanligaste teckensnitten du förväntar dig, minskar du risken för någon substitution alls.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Varför:** När det ursprungliga teckensnittet saknas har Aspose.Words nu en känd uppsättning alternativ, vilket ofta ger ett mer förutsägbart visuellt resultat.

### 2. Ersätt saknade teckensnitt programmässigt

Om du vill ha full kontroll kan du ersätta det saknade teckensnittet med ett specifikt efter det upptäckts.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Varför:** Detta talar om för motorn exakt vilka teckensnitt som ska provas, så att du kan upprätthålla företagets varumärkesprofil eller tillgänglighetsstandarder.

### 3. Logga och avbryt (när substitution är oacceptabelt)

Ibland betyder ett saknat teckensnitt att dokumentet är ogiltigt för ditt användningsområde (t.ex. juridiska formulär). I ett sådant scenario kan du kasta ett undantag så snart en substitution inträffar.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Varför:** Omedelbar misslyckande förhindrar fel i efterföljande steg, såsom feljusterade tabeller eller brutna signaturer.

---

## Fullt fungerande exempel – alla steg kombinerade

Nedan är ett enda, kopiera‑och‑klistra‑klart program som demonstrerar **hur man upptäcker substitution** *och* flera sätt att **hantera saknade teckensnitt**. Känn dig fri att kommentera bort de sektioner du inte behöver.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Vad du kan förvänta dig:**  
- Om `MissingFont.docx` refererar till ett teckensnitt som inte finns på maskinen, skriver konsolen ut substitutionsvarningen.  
- Den sparade `Processed.docx` använder reservteckensnittet du konfigurerade (eller bibliotekets standard).  
- Inga ohanterade undantag visas såvida du inte medvetet avbryter vid substitution.

---

## Vanliga frågor & edge‑cases

| Fråga | Svar |
|----------|--------|
| *Vad händer om dokumentet innehåller många saknade teckensnitt?* | Varningshändelsen utlöses för **varje** substitution, så du får flera rader. Du kan samla dem i en lista för en sammanfattningsrapport. |
| *Fungerar detta med PDF‑konvertering?* | Absolut. Samma `FontSettings` respekteras när du anropar `doc.Save("out.pdf")`. Substitutionsvarningen utlöses fortfarande, så du kan verifiera PDF:ens visuella integritet. |
| *Kan jag upptäcka substitution efter att dokumentet redan har lästs in?* | Inte direkt. Varningen utlöses **under** inläsning eller sparning. Om du behöver analys efter inläsning, samla varningarna i en samling under inläsningsfasen. |
| *Vad händer med anpassade teckensnitt som är inbäddade i DOCX‑filen?* | Inbäddade teckensnitt anses vara närvarande, så ingen substitution sker. Om det inbäddade teckensnittet är korrupt, utlöser Aspose.Words fortfarande en varning, som du kan fånga på samma sätt. |
| *Finns det någon prestandapåverkan?* | Minimal. Varningskontrollen är resurssnål; den verkliga kostnaden är att ladda dokumentet. Att lägga till en teckensnittsmapp kan öka söktiden något, men bara vid första inläsning. |

---

## Pro‑tips & fallgropar att undvika

- **Pro‑tips:** Ange alltid `recursive: true` när du pekar på en mapp med många teckensnitt; annars ignoreras undermappar.  
- **Se upp för:** Skiftlägeskänslighet på Linux. Teckensnittsnamn är skiftlägesokänsliga på Windows men inte på Linux, så använd det exakta namnet eller lägg till båda varianterna.  
- **Kom ihåg:** Om du kör i en containeriserad miljö, se till att teckensnittsmappen är en del av avbilden eller monterad vid körning.  
- **Tips:** Spara varningar i en `List<string>` om du behöver presentera en sammanfattning för slutanvändare eller logga dem till ett övervakningssystem.  

---

## Slutsats

Vi har gått igenom **hur man upptäcker substitution** av saknade teckensnitt i Aspose.Words, visat dig flera sätt att **hantera saknade teckensnitt**, och levererat ett komplett, körbart exempel som du kan lägga in i vilket .NET‑projekt som helst. Genom att utnyttja `FontSettings.Warning`‑händelsen får du realtidsinsikt i teckensnittsproblem, och med reservmappar eller explicita substitutionsregler håller du ditt resultat exakt som du förväntar dig.

Redo för nästa steg? Prova att utöka lösningen så att den automatiskt bäddar in reservteckensnittet i den genererade PDF‑filen, eller koppla varningshanteraren till en centraliserad loggtjänst för storskaliga dokumentpipelines. Mönstren vi diskuterade idag – händelsedriven upptäckt, smidig reserv, och explicit felhantering – gäller för många andra Aspose‑API:er, så du är nu rustad att tackla teckensnittsrelaterade utmaningar över hela linjen.

Har du fler frågor om teckensnittshantering, PDF‑konvertering eller Aspose.Words‑knep? Lägg en kommentar nedan, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}