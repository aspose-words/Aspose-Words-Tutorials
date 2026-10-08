---
category: general
date: 2026-03-13
description: Hur du fångar varningar när du laddar dokument med Aspose.Words, samt
  tips för att hantera saknade teckensnitt och ställa in anpassade teckensnittsinställningar.
  Lär dig en komplett C#‑lösning.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: sv
og_description: Hur man fångar varningar vid inläsning av Word‑filer med Aspose.Words,
  samt praktiska sätt att hantera saknade teckensnitt och ställa in anpassade teckensnittsinställningar.
og_title: Så fångar du varningar i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man fångar varningar i Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man fångar varningar i Aspose.Words – Komplett guide

Har du någonsin funderat **hur man fångar varningar** som dyker upp när Aspose.Words laddar ett dokument? I många verkliga projekt ser du varningar om teckensnittssubstitution, föråldrade funktioner eller till och med säkerhetsrelaterade meddelanden. Att ignorera dem är som att köra med sprucket vindruta – du kan komma fram, men du vet aldrig när något är på väg att gå sönder.

Det goda nyheten är att Aspose.Words ger dig ett rent, callback‑baserat sätt att avlyssna dessa meddelanden. I den här tutorialen går vi igenom ett **komplett C#‑exempel** som inte bara fångar varningar utan också visar hur du **hanterar saknade teckensnitt** och **ställer in egna teckensnittsinställningar** så att dina dokument renderas exakt som du förväntar dig.

---

## Vad du kommer att lära dig

- Konfigurera `LoadOptions` för att ansluta ett eget `FontSettings`‑objekt.  
- Registrera en varnings‑callback som filtrerar på `FontSubstitution`‑händelser.  
- Skriva ut varningsdetaljer till konsolen (eller någon logger du föredrar).  
- Utöka lösningen för att elegant hantera saknade teckensnitt på olika plattformar.  

När du är klar med den här guiden har du ett färdigt kodsnutt som du kan klistra in i vilket .NET‑projekt som helst, plus ett antal praktiska tips för att undvika vanliga fallgropar.

---

## Förutsättningar

| Krav | Varför det är viktigt |
|------|-----------------------|
| **Aspose.Words for .NET** (v23.12 eller senare) | API‑et vi använder (`LoadOptions`, `IWarningCallback`) finns här. |
| **.NET 6+** (eller .NET Framework 4.7.2+) | Moderna språkfunktioner gör koden renare. |
| **Ett exempel‑DOCX** (namngivet `input.docx`) placerat i en känd mapp | Vi behöver något att ladda och trigga en varning med. |
| **En konsol‑ eller loggningsramverk** (valfritt) | För att se de fångade varningarna i aktion. |

Inga extra NuGet‑paket krävs utöver själva Aspose.Words.

---

## Steg 1: Ställ in egna teckensnittsinställningar  

Innan du laddar ett dokument kan du tala om för Aspose.Words var den ska leta efter teckensnitt. Detta är delen **set custom font settings** i pusslet.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Varför detta är viktigt:**  
Om ett DOCX refererar till ett teckensnitt som inte är installerat på maskinen, kommer Aspose.Words tyst att ersätta det med ett reservteckensnitt *om* du inte har konfigurerat en mapp med de nödvändiga teckensnitten. Genom att ange en egen mapp minskar du risken för “font‑substitution”-varningar redan från början.

> **Pro tip:** På Linux kan du behöva lägga till paketet `fonts-dejavu-core` eller någon annan TrueType‑samling som dina dokument är beroende av.

---

## Steg 2: Registrera en varnings‑callback  

Aspose.Words implementerar `IWarningCallback`. Vi skapar en liten hanterare som bara skriver ut de varningar vi bryr oss om: saknade eller ersatta teckensnitt.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Varför detta är viktigt:**  
Scenariot **handle missing fonts** blir nu synligt för dig. Istället för att gissa vilket teckensnitt som byttes ut får du en tydlig beskrivning som “Font 'Calibri' was substituted with 'Arial'”. Detta är ovärderligt när du felsöker layoutproblem i genererade PDF‑filer eller utskrivna rapporter.

---

## Steg 3: Ladda dokumentet med de konfigurerade alternativen  

Nu laddar vi äntligen dokumentet i minnet, med hjälp av `LoadOptions` som vi just förberedde.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Om källfilen använder ett teckensnitt som inte finns i `C:\MyFonts` kommer du att se en utskrift som liknar:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Den raden är resultatet av **how to capture warnings** som du letade efter.

---

## Steg 4: Fullt fungerande exempel (Kopiera‑klistra‑klart)

Nedan är hela programmet, redo att kompileras. Klistra in det i ett nytt konsolprojekt och kör – se bara till att sökvägarna pekar på faktiska platser på din maskin.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Förväntad utskrift:**  

- Om alla teckensnitt finns tillgängliga:  
  `Document processed. Check console for any warning messages.`  

- Om ett teckensnitt saknas:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Steg 5: Vanliga variationer & kantfall  

| Situation | Vad som måste justeras |
|-----------|------------------------|
| **Flera teckensnittsmappar** | Anropa `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` för varje extra plats. |
| **Undertryck alla varningar** | Implementera `Warn` men lämna kroppen tom, eller sätt `loadOptions.WarningCallback = null;`. |
| **Fånga andra varningstyper** | Jämför `info.WarningType` med `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` osv. |
| **Kör på Linux/macOS** | Säkerställ att teckensnittsmappen innehåller Linux‑kompatibla `.ttf`/`.otf`‑filer; du kan behöva installera `libfontconfig`. |
| **Stora dokument** | Överväg att strömma dokumentet (`LoadOptions.LoadFormat = LoadFormat.Docx;`) för att minska minnesbelastningen. |

Genom att förutse dessa scenarier undviker du överraskningar när du flyttar från en utvecklingsmaskin till en CI‑pipeline eller en moln‑VM.

---

## Steg 6: Visuell bekräftelse (valfritt)

Om du föredrar en snabb visuell indikator kan du dumpa de fångade varningarna till en liten HTML‑rapport. Här är ett litet kodstycke som skriver meddelandena till `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Efter att ha laddat dokumentet, anropa `handler.WriteReport(@"C:\Docs\warnings.html");` och öppna filen i en webbläsare. Bilden nedan visar hur rapporten kan se ut:

![Hur man fångar varningar skärmdump](/images/capture-warnings.png)

*Alt‑text:* **hur man fångar varningar** – skärmdump av konsolutskrift och HTML‑rapport.

---

## Slutsats  

Vi har gått igenom **hur man fångar varningar** i Aspose.Words, demonstrerat ett pålitligt sätt att **hantera saknade teckensnitt**, och visat hur du **ställer in egna teckensnittsinställningar** för deterministisk rendering. Det fullständiga exemplet är redo att klistras in i vilken .NET‑lösning som helst, och den modulära `FontWarningHandler` kan utökas för att passa din loggnings‑ eller telemetri‑strategi.

Nästa steg? Prova att ersätta `Console.WriteLine`‑anropen med en strukturerad logger som Serilog, eller skicka varningarna till Application Insights för real‑tidsövervakning. Du kan också utforska `DocumentVisitor`‑mönstret om du behöver inspektera dokumentets innehåll efter laddning.

Har du frågor om andra varningstyper eller strategier för teckensnitts‑inbäddning? Lämna en kommentar nedan – happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}