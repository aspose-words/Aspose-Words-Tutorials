---
category: general
date: 2026-02-12
description: Skapa en teckensnittsvarningshanterare för att upptäcka saknade teckensnitt
  och spåra saknade teckensnitt i Aspose.Words. Lär dig hur du loggar varningar effektivt.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: sv
og_description: Skapa en fontvarningshanterare i C# för att upptäcka saknade teckensnitt
  och lär dig hur du loggar varningar när Aspose.Words ersätter teckensnitt.
og_title: Skapa teckensnittsvarningshanterare – Upptäck saknade teckensnitt
tags:
- Aspose.Words
- C#
- Document Processing
title: Skapa teckensnittsvarningshanterare – Detektera saknade teckensnitt i C#
url: /sv/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa teckensnittsvarningshanterare – Upptäck saknade teckensnitt i C#

Har du någonsin behövt **create font warning handler** eftersom ett Word‑dokument tyst bytte ut ett teckensnitt du inte förväntade dig? Du är inte ensam. När Aspose.Words läser in en DOCX som refererar till ett teckensnitt som saknas på servern, faller den tyst tillbaka till ett standardteckensnitt—vilket lämnar din layout subtilt trasig.  

I den här handledningen visar vi exakt hur du **detect missing fonts**, **track missing fonts**, och **how to log warnings** så att du kan upptäcka dessa ersättningar innan de blir ett problem. I slutet har du en återanvändbar varningshanterare som skriver ut varje teckensnitts‑ersättningshändelse till konsolen (eller någon logger du föredrar). Ingen gåta, bara klar, handlingsbar kod.

## Förutsättningar

- .NET 6.0 eller senare (API‑et är detsamma för .NET Framework 4.6+)
- Aspose.Words för .NET installerat (`dotnet add package Aspose.Words`)
- En Word‑fil som refererar till ett teckensnitt som inte är installerat på din maskin (t.ex. `MissingFont.docx`)

Om du redan har dem, toppen—låt oss hoppa in.

## Steg 1: Ställ in LoadOptions med en varnings‑callback  

Det första du gör när du vill **create font warning handler** är att tala om för Aspose.Words att utlösa en callback när den stöter på ett problem. `LoadOptions` är behållaren för den konfigurationen.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Varför detta är viktigt:**  
`LoadOptions` är det enda stället där du kan ansluta ett `IWarningCallback`. Utan det loggar Aspose.Words varningar internt men du ser dem aldrig. Genom att tilldela `FontWarningHandler` får vi full kontroll över vad som händer när ett saknat teckensnitt ersätts.

## Steg 2: Implementera FontWarningHandler‑klassen  

Nu skapar vi faktiskt **create font warning handler**‑kod. Klassen implementerar `IWarningCallback` och tar emot ett `WarningInfo`‑objekt för varje varning som Aspose.Words ger.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Förklaring:**  
- `info.Type` berättar för oss vilken kategori varningen har. Vi är intresserade av `WarningType.FontSubstitution` eftersom den indikerar ett saknat teckensnitt.  
- `info.Description` innehåller ett mänskligt läsbart meddelande som t.ex. *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Genom att skriva till `Console.WriteLine` **log warnings** omedelbart. I en verklig applikation kan du ersätta det med `ILogger`, en filskrivare eller en telemetritjänst.

> **Pro tip:** Om du behöver samla alla saknade teckensnitt för senare rapportering, lagra `info.Description` i en `List<string>` istället för att skriva ut dem.

## Steg 3: Läs in dokumentet med de konfigurerade LoadOptions  

Med callbacken på plats kommer inläsning av ett dokument automatiskt att utlösa vår hanterare när ett teckensnitt saknas.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Vad du kommer att se:**  
När programmet körs skrivs något liknande ut:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Den raden bekräftar att du framgångsrikt **detected missing fonts** och nu **track missing fonts** i realtid.

## Steg 4: Verifiera att hanteraren fungerar med olika scenarier  

Det är lätt att anta att hanteraren bara fungerar för DOCX‑filer, men Aspose.Words stödjer många format. Försök läsa in en PDF som refererar till ett inbäddat teckensnitt, eller en äldre `.doc`‑fil. Samma callback utlöses för alla format som går igenom teckensnittslösnings‑pipeline:n.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Om PDF‑filen refererar till ett teckensnitt som inte är installerat får du samma konsolutskrift. Detta visar att din **create font warning handler**‑lösning är format‑agnostisk.

## Steg 5: Utöka hanteraren – Logga till en fil  

Konsolutskrift är praktisk för demonstrationer, men produktionskod skriver vanligtvis till en loggfil. Här är en snabb justering.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Nu, varje gång ett teckensnitt ersätts, läggs meddelandet till i `font-warnings.log`. Detta uppfyller delen **how to log warnings** i uppdraget och ger dig ett bestående revisionsspår.

## Steg 6: Sätt ihop allt – Fullt, körbart exempel  

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapp. Inga delar saknas; ersätt bara filsökvägen med ditt eget dokument.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Förväntat resultat:**  

- Konsolen skriver ut varje ersättningsrad.  
- `font-warnings.log` innehåller nu en tidsstämplad post för varje saknat‑teckensnitt‑händelse.  
- `output.pdf`‑filen skapas med de ersatta teckensnitten, vilket säkerställer att konverteringen lyckas även när de ursprungliga teckensnitten inte finns tillgängliga.

## Vanliga frågor & kantfall  

| Question | Answer |
|----------|--------|
| *Vad händer om jag vill ignorera vissa teckensnitt?* | Inuti `Warning`, kontrollera `info.Description` för teckensnittsnamnet och `return;` tidigt för teckensnitt du anser vara acceptabla. |
| *Kommer hanteraren att utlösas för inbäddade teckensnitt?* | Nej—inbäddade teckensnitt är alltid tillgängliga för dokumentet, så ingen ersättningsvarning sker. |
| *Kan jag fånga andra varningstyper (t.ex. bild‑upplösningsproblem)?* | Absolut. Ta bort `if (info.Type == WarningType.FontSubstitution)`‑skyddet eller lägg till ytterligare `if`‑block för `WarningType.ImageResolution`. |
| *Är hanteraren trådsäker?* | Standardimplementeringen som visas skriver till en fil utan synkronisering. För flerdelade scenarier, omslut filskrivningar i en låsning eller använd en samtidig logger. |

## Nästa steg  

Nu när du vet **how to log warnings** för saknade teckensnitt, kanske du vill:

- **Detect missing fonts** under en batch‑importprocess och generera en sammanfattningsrapport.  
- **Track missing fonts** över flera dokument och skicka ett e‑postlarm när ett visst teckensnitt förekommer ofta.  
- **Integrate with a monitoring system** (t.ex. Azure Application Insights) för att visa trender i teckensnittsersättningar över tid.  

Alla dessa utökningar bygger på samma `IWarningCallback`‑grund som vi skapade.

---

*Lycklig kodning! Om du stöter på konstigheter—kanske en anpassad teckensnittsmapp eller en nätverksdelning—lämna en kommentar nedan. Gemenskapen (och jag) är alltid glada att hjälpa dig finjustera din font‑warning‑strategi.* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}