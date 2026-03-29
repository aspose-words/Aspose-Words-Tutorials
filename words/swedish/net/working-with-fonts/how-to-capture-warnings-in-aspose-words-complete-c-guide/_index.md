---
category: general
date: 2026-03-28
description: Hur man fångar varningar när man laddar en DOCX med Aspose.Words och
  får varningsmeddelanden för saknade teckensnitt. Lär dig att hantera saknade teckensnitt
  effektivt.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: sv
og_description: Hur man fångar varningar när man laddar en DOCX med Aspose.Words,
  får varningsmeddelanden och hanterar saknade teckensnitt med praktiska kodexempel.
og_title: Hur man fångar varningar i Aspose.Words – Komplett C#‑guide
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man fångar varningar i Aspose.Words – Komplett C#‑guide
url: /sv/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man fångar varningar i Aspose.Words – Komplett C#-guide

Har du någonsin undrat **hur man fångar varningar** som dyker upp när du laddar ett Word-dokument med Aspose.Words? Kanske ser du märkliga teckensnittsändringar och du behöver veta exakt varför. Kort sagt kan du koppla in i bibliotekets varningssystem, **hämta varningsmeddelanden**, och till och med **hantera saknade teckensnitt** innan de förstör din layout.  

I den här handledningen går vi igenom ett verkligt scenario: att ladda en DOCX, samla varje varning som motorn avger, och skriva ut detaljer om eventuell teckensnittssubstitution som sker. När du är klar har du ett färdigt kodexempel, förstår “varför” bakom varje steg, och vet hur du kan utöka metoden för dina egna projekt.

## Vad du kommer att lära dig

- Hur man konfigurerar `LoadOptions` så att varningar fångas automatiskt.  
- Det exakta sättet att **hämta varningsmeddelanden** från `WarningInfoCollection`.  
- Hur man identifierar och reagerar på **saknade teckensnitt** via flaggan `WarningType.FontSubstitution`.  
- Tips för felsökning av kantfall, såsom dokument med inbäddade teckensnitt eller anpassade teckensnittsmappar.  

Inga externa referenser behövs – allt du behöver finns här.

---

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.7+).  
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`).  
- Ett exempel‑DOCX (`input.docx`) som antingen saknar vissa teckensnitt eller använder teckensnitt som inte är installerade på din maskin.  

Det är allt. Om du redan är bekväm med C# och Visual Studio kan du kopiera‑klistra in koden och köra den omedelbart.

---

## Steg 1: Förbered Load‑alternativ och en varnings‑callback

Det första Aspose.Words gör när du anropar `new Document(path, loadOptions)` är att parsra filen. Under parsning kan den stöta på saknade teckensnitt, ej stödda funktioner eller föråldrad markup. För att fånga dessa händelser behöver du ett **varnings‑callback**‑objekt.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Varför detta är viktigt:** Utan en callback loggar Aspose.Words tyst varningar till konsolen (eller kastar bort dem), vilket lämnar dig blind för teckensnittssubstitutioner som kan påverka layouten. Genom att tillhandahålla en dedikerad `WarningInfoCollection` får du full insyn.

> **Pro tip:** Om du bara bryr dig om teckensnittsrelaterade varningar kan du filtrera senare – men att samla *alla* varningar ger dig ett säkerhetsnät för framtida problem.

---

## Steg 2: Ladda dokumentet med de konfigurerade alternativen

Nu när callbacken är klar, ladda filen. `Document`‑konstruktorn kommer automatiskt att anropa callbacken för eventuella problem den hittar.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Vad som händer under huven?** Aspose.Words parsar Open XML, löser stilar och försöker mappa varje teckensnittsreferens till ett system‑installerat teckensnitt. Om ingen matchning hittas skapar den ett `WarningInfo`‑objekt av typen `FontSubstitution`.

---

## Steg 3: Hämta och inspektera de insamlade varningarna

Efter att laddningen är klar innehåller din `warningCollector` nu varje varning som inträffade. Låt oss plocka ut dem och fokusera på teckensnittssubstitutionsmeddelanden.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Exempel på utskrift** (din konsol kan visa något liknande):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Om du vill ha *alla* varningar, ta bara bort `if`‑kontrollen eller logga `warning.Type` för varje post.

---

## Steg 4: Hantera saknade teckensnitt – mer än bara loggning

Att samla varningar är användbart, men ofta behöver du **hantera saknade teckensnitt** programatiskt. Här är två vanliga strategier:

### 4.1 Ersätt saknade teckensnitt med ett specifikt reservteckensnitt

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Nu kommer alla saknade teckensnitt att bytas ut mot *Calibri* istället för bibliotekets standardreserv.

### 4.2 Bädda in ett ersättningsteckensnitt dynamiskt

Om du har en anpassad teckensnittfil (t.ex. `MyFallback.ttf`) kan du registrera den vid körning:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Denna metod är praktisk när du distribuerar ett specifikt företags­teckensnitt med din applikation.

> **Edge case:** Dokument som redan bäddar in det erforderliga teckensnittet kommer att ignorera systemets substitutionsregler. I det scenariot blir varningssamlingen tom för det teckensnittet, vilket är exakt vad du vill.

---

## Steg 5: Fullt fungerande exempel (Kopiera‑klistra redo)

Nedan är ett självständigt program som demonstrerar allt från början till slut. Byt bara ut `YOUR_DIRECTORY/input.docx` mot sökvägen till din testfil.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Vad du kan förvänta dig**

- Konsolen skriver ut varje teckensnittssubstitutionsvarning, föregången med en varnings‑emoji för synlighet.  
- Utdata‑DOCX (`output.docx`) använder *Calibri* där ett saknat teckensnitt upptäcktes.  
- Inga ohanterade undantag – varningssystemet hanterar elegant alla okända teckensnitt.

---

## Vanliga frågor & svar

**Q: Kommer detta att fungera med PDF‑filer som genereras från Word?**  
A: Ja. Aspose.Words behandlar PDF som ett annat utdataformat. Varningsinsamlingen sker under *load*-fasen, så den är oberoende av den slutgiltiga exporten.

**Q: Vad händer om jag behöver fånga varningar för **alla** dokumentoperationer (spara, konvertera, osv.)?**  
A: Du kan återanvända samma `WarningInfoCollection` genom att tilldela den till `Document.WarningCallback` efter att dokumentet har instansierats. Varje efterföljande operation kommer att lägga till nya poster i samma samling.

**Q: Påverkar varnings‑callbacken prestanda?**  
A: Nästan inget. Samlingen lagrar bara objekt; såvida du inte bearbetar tusentals varningar i en tight loop märker du ingen märkbar fördröjning.

**Q: Hur kan jag undertrycka varningar jag inte bryr mig om?**  
A: Implementera en egen klass som ärver `IWarningCallback` och filtrera inne i `Warning`‑metoden. Den inbyggda `WarningInfoCollection` lagrar bara, den filtrerar inte.

---

## Proffstips & fallgropar

- **Pro tip:** Inspektera alltid `Warning.Description` – den innehåller det exakta teckensnittsnamnet som saknades. Detta kan hjälpa dig avgöra om du ska leverera teckensnittet med din app.  
- **Se upp för inbäddade teckensnitt:** Om källdokumentet redan bäddar in det behövda teckensnittet kommer Aspose.Words inte att avge en substitutionsvarning, även om teckensnittet inte är installerat lokalt.  
- **Trådsäkerhet:** `WarningInfoCollection` är inte trådsäker. Om du laddar flera dokument samtidigt, ge varje tråd sin egen samling.  
- **Versionskontroll:** Varnings‑API:et har varit stabilt sedan Aspose.Words 20.8. Se till att du använder en recent version för att undvika att missa nyare varningstyper.

---

## Slutsats

Vi har gått igenom **hur man fångar varningar** från Aspose.Words, demonstrerat hur man **hämtar varningsmeddelanden**, och visat praktiska sätt att **hantera saknade teckensnitt** genom reservteckensnitt eller anpassade teckensnittsmappar. Det fullständiga exemplet är redo att klistras in i vilket .NET‑projekt som helst, och koncepten skalar till större automatiseringspipeline.

Nästa steg kan vara att utforska:

- Använda `Document.WarningCallback` för att fånga varningar under **spara**‑operationer.  
- Logga varningar till en fil eller telemetrisystem för produktionsövervakning.  
- Utöka callbacken för att automatiskt ersätta saknade teckensnitt med varumärkesspecifika typsnitt.

Känn dig fri att experimentera—byt ut reservteckensnittet, lägg till fler dokument i batchen, eller integrera varningssamlaren i en CI‑pipeline som flaggar teckensnittsrelaterade regressioner. Lycka till med kodningen, och må dina dokument alltid renderas exakt som du förväntar dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}