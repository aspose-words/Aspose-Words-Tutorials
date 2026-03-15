---
category: general
date: 2026-03-14
description: Hantera saknade teckensnitt snabbt med Aspose.Words. Lär dig hur du fångar
  varningar om teckensnittssubstitution, konfigurerar LoadOptions och undviker renderingsproblem.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: sv
og_description: Hantera saknade typsnitt i Aspose.Words med en varningssamling. Denna
  handledning visar steg för steg hur man upptäcker och loggar typsnittssubstitutioner.
og_title: Hantera saknade teckensnitt i Aspose.Words – Komplett C#‑guide
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Hantera saknade teckensnitt i Aspose.Words – Komplett C#‑guide
url: /sv/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hantera saknade teckensnitt i Aspose.Words – Komplett C#-guide

Har du någonsin behövt **hantera saknade teckensnitt** när du laddar ett Word‑dokument och undrat varför din PDF‑ eller bildutmatning ser felaktig ut? Du är inte ensam. Saknade teckensnittsfiler är en tyst problemkälla som kan förvandla en perfekt designad rapport till ett rörigt kaos.  

Den goda nyheten? Aspose.Words ger dig ett enkelt sätt att fånga dessa teckensnittssubstitutions‑händelser, logga dem och till och med byta in ett reservteckensnitt om du vill. I den här handledningen går vi igenom ett komplett, färdigt‑att‑köra‑exempel som visar exakt hur du ställer in en varningssamling, kopplar den till `LoadOptions` och laddar ett dokument som kan innehålla saknade teckensnitt.

När du är klar med den här guiden kommer du att kunna:

* Upptäcka varje teckensnittssubstitution som sker under dokumentladdning.  
* Skriva ut ett vänligt konsolmeddelande (eller skicka det till en logger) för varje saknat teckensnitt.  
* Utöka lösningen för att ersätta teckensnitt, om så behövs.  

**Förutsättningar** – du behöver:

* .NET 6.0 eller senare (koden fungerar även med .NET Core och .NET Framework).  
* Aspose.Words for .NET NuGet‑paketet (nuvarande version 23.11).  
* En Word‑fil som medvetet refererar till ett teckensnitt du inte har installerat – vi kallar den `doc-with-missing-font.docx`.  

Om du redan är bekväm med C# och har ett projekt uppsatt kan du hoppa rakt in i koden. Annars, fortsätt läsa; vi går igenom de små installationsstegen först.

---

## Varför hantering av saknade teckensnitt är viktigt

När Aspose.Words laddar ett dokument försöker det matcha varje glyf till ett teckensnitt som är installerat på maskinen. Om det inte hittar exakt teckensnitt ersätts det tyst med det närmaste matchande teckensnittet. Denna substitution kan förändra radhöjder, kerning och till och med få tecken att försvinna. Genom att fånga `WarningType.FontSubstitution`‑händelsen får du en tydlig bild av **vad** som byttes och **varför**, vilket är avgörande för:

* Att upprätthålla varumärkeskonsekvens (ditt företags teckensnitt måste visas exakt som designat).  
* Felsökning av PDF‑konverteringsproblem – ofta är en saknad teckensnittsfelkälla.  
* Att bygga automatiserade dokumentpipeline där du behöver flagga problematiska filer för manuell granskning.  

Nu när “varför” är klart, låt oss dyka ner i **hur**.

---

## Steg 1 – Ställ in varningssamlaren

Det första vi behöver är ett objekt som kan lyssna på Aspose.Words‑varningar. `DocumentWarnings` implementerar `IWarningCallback`, vilket låter oss reagera när biblioteket avger en varning.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Vad händer?**  
* `DocumentWarnings` är ett lätt omslag runt callback‑gränssnittet.  
* Lambda‑uttrycket kontrollerar `e.WarningType` så vi ignorerar orelaterade varningar (som föråldrade funktioner).  
* `e.WarningInfo` innehåller namnet på det saknade teckensnittet, vilket vi skriver ut till konsolen.  

*Proffstips*: Byt `Console.WriteLine` mot en strukturerad logger (Serilog, NLog) i produktion – på så sätt får du tidsstämplar och loggnivåer gratis.

---

## Steg 2 – Anslut samlaren till LoadOptions

`LoadOptions` är grindvakten för varje dokument du öppnar med Aspose.Words. Genom att tilldela vår `fontWarnings`‑instans till dess `WarningCallback`‑egenskap säkerställer vi att samlaren är aktiv under laddningsprocessen.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Varför använda LoadOptions?**  
Förutom varningar låter `LoadOptions` dig styra lösenordshantering, kodning och även anpassad resursladdning. Här fokuserar vi på varningsdelen, men samma mönster fungerar för andra callbacks.

---

## Steg 3 – Ladda dokumentet med de konfigurerade alternativen

Nu laddar vi äntligen dokumentet i minnet. Om något teckensnitt saknas kommer vår samlare att triggas och du ser en konsollinje för varje substitution.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Om du kör detta kodsnutt med ett dokument som refererar till exempelvis *Calibri Light* medan din testmaskin bara har *Calibri*, får du en utskrift liknande:

```
Font 'Calibri Light' was substituted.
```

Det är hela detekteringsloopen – enkel men kraftfull.

---

## Steg 4 – (Valfritt) Ersätt saknade teckensnitt med ett känt substitut

Ibland vill du inte bara logga problemet; du vill tvinga ett reservteckensnitt så att den renderade utskriften ser konsekvent ut. Aspose.Words låter dig tillhandahålla ett anpassat `FontSettings`‑objekt som mappar saknade teckensnitt till ett ersättnings­teckensnitt.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Förklaring**  
* Jokertecknet `"*"` talar om för Aspose.Words att behandla *alla* saknade teckensnitt på samma sätt.  
* Du kan också mappa specifika teckensnitt individuellt om du behöver fin‑granulerad kontroll.  
* Efter att ha satt `document.FontSettings` kommer all efterföljande rendering (PDF, bild, HTML) att respektera substitutionen.

---

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapp. Det inkluderar alla nödvändiga `using`‑satser, felhantering och kommentarer för tydlighet.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Förväntad utskrift** (när ett saknat teckensnitt upptäcks):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Om källdokumentet redan innehåller alla nödvändiga teckensnitt kommer varningsraden helt enkelt inte att visas – inget att oroa sig för.

---

## Vanliga frågor & edge‑cases

| Fråga | Svar |
|----------|--------|
| **Vad händer om jag bara vill logga, inte ersätta teckensnitt?** | Hoppa över `FontSettings`‑blocket helt; varningssamlaren ensam räcker. |
| **Kan jag omdirigera varningar till en fil?** | Ja – ersätt `Console.WriteLine` med `File.AppendAllText("font-warnings.log", …)`. |
| **Fungerar detta för DOC, DOCX och ODT?** | Absolut. `LoadOptions` gäller för alla format som stöds av Aspose.Words. |
| **Vad händer med anpassade teckensnitt som är inbäddade i dokumentet?** | Inbäddade teckensnitt kringgår substitueringsmekanismen; de används som de är. |
| **Finns det någon prestandapåverkan?** | Överheaden är minimal – endast ett callback per saknat teckensnitt. För stora batcher, överväg att samla varningar istället för att skriva per händelse. |

---

## Slutsats

Vi har visat **hur man hanterar saknade teckensnitt** i Aspose.Words genom att koppla en `DocumentWarnings`‑samling till `LoadOptions`, eventuellt byta in ett reservteckensnitt, och spara resultatet. Detta mönster ger dig full insyn i teckensnittssubstitutions‑händelser, vilket hjälper dig att behålla visuell integritet över PDF-, bild- eller HTML‑konverteringar.

Nästa steg du kan utforska:

* Integrera varningssamlaren med ett centraliserat loggningsramverk.  
* Bygg en UI‑instrumentpanel som listar dokument med saknade teckensnitt för batch‑behandling.  
* Kombinera detta tillvägagångssätt med Aspose.PDF för att verifiera att de genererade PDF‑erna verkligen använder reservteckensnittet.  

Känn dig fri att experimentera – byt `"Arial"` mot `"Tahoma"` eller ladda ett annat dokumentset. Kärnidén förblir densamma: fånga varningen, agera på den och låt dina dokument se exakt ut som avsett.

Lycka till med kodningen! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}