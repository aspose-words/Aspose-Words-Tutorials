---
category: general
date: 2026-01-05
description: Hur man snabbt fångar teckensnitt och hanterar saknade teckensnitt med
  Aspose.Words. Lär dig en steg‑för‑steg‑lösning med fullständig C#‑kod.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: sv
og_description: Hur du fångar teckensnitt i Aspose.Words och hanterar saknade teckensnitt.
  Följ den här detaljerade guiden för en pålitlig C#‑implementation.
og_title: Hur man fångar teckensnitt i Aspose.Words – Fullständig handledning
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man fångar teckensnitt i Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så fångar du teckensnitt i Aspose.Words – Komplett guide

Har du någonsin undrat **hur man fångar teckensnitt** när man laddar ett Word‑dokument med Aspose.Words? Du är inte ensam. Saknade teckensnitt kan orsaka subtila layout‑fel, och utan en korrekt varning kanske du aldrig märker det förrän den slutgiltiga PDF‑filen ser felaktig ut. I den här handledningen visar vi exakt hur du fångar teckensnitt **och** hanterar saknade teckensnitt så att ditt resultat förblir pixel‑perfekt.

Vi går igenom ett verkligt scenario, ställer in en varnings‑callback och ger dig ett färdigt C#‑exempel att köra. I slutet vet du varför detta är viktigt, hur du implementerar det och vad du bör hålla utkik efter när teckensnitt försvinner från din miljö.

## Vad du kommer att lära dig

- Hur du konfigurerar **LoadOptions** för att lyssna på teckensnitt‑relaterade varningar.  
- Rollen för **IWarningCallback** och **WarningInfo** i Aspose.Words.  
- Praktiska tips för felsökning och loggning av saknade teckensnitt.  
- Ett komplett, självständigt kodexempel som du kan klistra in i Visual Studio och köra omedelbart.

**Förutsättningar:** .NET 6+ (eller .NET Framework 4.7.2+), Aspose.Words för .NET installerat via NuGet, och en grundläggande kunskap om C#. Inga andra bibliotek krävs.

---

## Steg 1: Ställ in LoadOptions för att fånga teckensnitt

Det första vi behöver är en **LoadOptions**‑instans. Detta objekt talar om för Aspose.Words hur det ska bete sig när det läser ett dokument. Genom att tilldela en anpassad **IWarningCallback** kan vi avlyssna alla varningar om teckensnittssubstitution som uppstår under inläsningsprocessen.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Varför detta är viktigt:**  
Aspose.Words ersätter tyst saknade teckensnitt med ett standardteckensnitt om du inte ber det att meddela dig. Genom att ansluta en callback **fångar vi teckensnitt**‑information redan vid inläsning, vilket ger oss möjlighet att logga, ersätta eller till och med avbryta operationen.

> **Proffstips:** Behåll `loadOptions` som en återanvändbar variabel om du bearbetar många dokument i en batch. Det undviker att skapa om samma callback om och om igen.

---

## Steg 2: Ladda dokumentet med de konfigurerade alternativen

Nu när callbacken är på plats laddar vi dokumentet. **Document**‑konstruktorn accepterar sökvägen och de **LoadOptions** vi just konfigurerade.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Om något teckensnitt saknas kommer Aspose.Words att avfyra en varning som vår `FontWarningCollector` tar emot. Dokumentet i sig kommer fortfarande att laddas, men du får en tydlig redogörelse för vilka teckensnitt som ersattes.

---

## Steg 3: Implementera FontWarningCollector – Hantera saknade teckensnitt

Kärnan i **hur man fångar teckensnitt** ligger i klassen `FontWarningCollector`. Den implementerar `IWarningCallback` och filtrerar endast händelser av typen `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Förklaring:**  
- `info.Type` berättar för oss vilken kategori varningen tillhör. Genom att kontrollera `FontSubstitution` **hanterar vi saknade teckensnitt** utan att fylla outputen med irrelevanta meddelanden (t.ex. föråldrade funktioner).  
- `info.Description` innehåller ett människoläsbart meddelande, till exempel “Font 'Comic Sans MS' was substituted with 'Arial'.” Detta är exakt den data du behöver för att granska din teckensnittsinventering.

> **Observera:** Om du behöver stoppa bearbetningen när ett kritiskt teckensnitt saknas, kasta ett undantag i `if`‑blocket istället för att bara skriva ut.

---

## Steg 4: Verifiera output – Vad du kan förvänta dig

Kör programmet från en konsol eller din IDE. För varje saknat teckensnitt kommer du att se en rad som:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Om alla teckensnitt finns kvar är callbacken tyst och dokumentet laddas utan incidenter. Du kan nu säkert fortsätta med att spara, konvertera eller skriva ut dokumentet, med förvissningen om att du har **fångat teckensnitt**‑information.

---

## Steg 5: Fullt fungerande exempel (Alla delar tillsammans)

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Det inkluderar using‑direktiven, callback‑implementeringen och en liten demonstration av att spara det inlästa dokumentet som PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Köra koden:**  
1. Skapa ett nytt konsolprojekt (`dotnet new console -n FontCaptureDemo`).  
2. Lägg till Aspose.Words‑paketet (`dotnet add package Aspose.Words`).  
3. Byt ut den genererade `Program.cs` mot kodsnutten ovan.  
4. Placera en DOCX som medvetet refererar till ett teckensnitt du inte har (t.ex. “Papyrus”).  
5. Kör (`dotnet run`). Titta på konsolen för substitutionsmeddelanden och öppna sedan `output.pdf` för att verifiera layouten.

---

## Vanliga frågor & specialfall

### Vad om jag senare behöver listan över saknade teckensnitt?

Spara meddelandena i en `List<string>` i `FontWarningCollector` och exponera den via en egenskap. På så sätt kan du skriva listan till en loggfil efter att ha bearbetat många dokument.

### Fungerar detta med krypterade eller lösenordsskyddade filer?

Ja, men du måste också ange lösenordet via `LoadOptions.Password`. Varnings‑callbacken fungerar på samma sätt när dokumentet har dekrypterats.

### Kan jag ersätta ett saknat teckensnitt med en egen reserv?

Absolut. Inuti `Warning`‑metoden kan du anropa `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Detta säkerställer att substitutionen är deterministisk.

### Påverkar detta prestandan?

Överheaden är minimal—i princip ett metodanrop per varning. I en batch med tusentals dokument är påverkan försumbar jämfört med I/O‑kostnaden för att ladda varje fil.

---

## Slutsats

Vi har gått igenom **hur man fångar teckensnitt** i Aspose.Words, visat dig hur du **hanterar saknade teckensnitt** med en ren varnings‑callback och levererat ett komplett, körbart exempel. Genom att ansluta detta mönster i din dokument‑bearbetningspipeline blir du aldrig förvånad över tysta teckensnittssubstitutioner igen.

Redo för nästa steg? Försök att utöka samlaren så att den skriver JSON‑loggar, integrera med en övervakningsdashboard eller automatiskt bädda in saknade teckensnitt i den resulterande PDF‑filen. Möjligheterna är oändliga, och nu har du en solid grund.

Lycka till med kodandet! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}