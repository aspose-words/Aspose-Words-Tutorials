---
category: general
date: 2026-03-01
description: Skapa FontSettings i C# för att upptäcka saknade teckensnitt, fånga teckensnittmeddelanden
  och hantera saknade teckensnitt med Aspose.Words. Steg‑för‑steg‑guide för utvecklare.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: sv
og_description: Skapa FontSettings i C# för att upptäcka saknade teckensnitt, fånga
  teckensnittmeddelanden och hantera saknade teckensnitt med Aspose.Words. Komplett
  handledning med kod.
og_title: Skapa FontSettings i C# – Detektera saknade teckensnitt och fånga teckensnittmeddelanden
tags:
- Aspose.Words
- C#
- Font Management
title: Skapa FontSettings i C# – Detektera saknade typsnitt och fånga typsnittmeddelanden
url: /sv/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa FontSettings i C# – Upptäck saknade teckensnitt & fånga teckensnittmeddelanden

Har du någonsin behövt **create FontSettings** i ett .NET‑projekt men varit osäker på hur du upptäcker teckensnitt som inte är installerade på målmaskinen? Du är inte ensam. I många verkliga applikationer—tänk automatiska rapportgeneratorer eller dokumentkonverterare—kan saknade teckensnitt tyst förstöra layouten, och du märker det inte förrän PDF‑filen ser konstig ut.  

Tänk om du kunde **detect missing fonts**, **capture font messages** och **handle missing fonts** innan de förstör ditt resultat? Den goda nyheten är att Aspose.Words gör detta till en barnlek. I den här handledningen går vi igenom hela processen, från att konfigurera `FontSettings`‑objektet till att ansluta en varnings‑callback som talar om exakt vilka glyfer som ersattes.

> **TL;DR:** I slutet har du en färdig‑att‑köra C#‑konsolapp som loggar varje teckensnittsersättning, så att du kan avgöra om du ska bädda in ett ersättnings‑teckensnitt eller varna användaren.

---

## Förutsättningar

- .NET 6 SDK (eller någon nyare .NET‑version)  
- Visual Studio 2022 eller VS Code med C#‑tillägg  
- En Aspose.Words för .NET‑licens (gratis provversion fungerar för denna demo)  
- Ett exempel‑DOCX som refererar till ett teckensnitt du inte har installerat (t.ex. *Comic Sans MS* på en Linux‑maskin)  

Inga speciella NuGet‑paket utöver `Aspose.Words` behövs.

---

## Steg 1 – Installera Aspose.Words och sätt upp projektet

Först och främst, skapa ett nytt konsolprojekt och lägg till Aspose.Words‑biblioteket.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Om du redan har en lösning, lägg bara till paketet via NuGet Package Manager‑gränssnittet—det gör versionshantering enklare.

---

## Steg 2 – Skapa FontSettings (Primärt nyckelord visas här)

Steget **create FontSettings** är hörnstenen i alla teckensnitt‑relaterade arbetsflöden. `FontSettings` talar om för Aspose.Words var den ska leta efter teckensnitt, om den ska använda systemmappar och hur den ska falla tillbaka när något saknas.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Varför är detta viktigt? Utan en korrekt konfigurerad `FontSettings` ersätter motorn tyst saknade glyfer med standard‑systemteckensnittet, och du får aldrig någon varning.

---

## Steg 3 – Anslut LoadOptions med FontSettings

`LoadOptions` låter dig skicka `FontSettings` till dokumentladdaren. Detta är bron som låter motorn **detect missing fonts** under `Document`‑konstruktionsfasen.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Nu, varje gång du laddar ett DOCX med `loadOptions`, kommer Aspose.Words att konsultera de `FontSettings` vi konfigurerade tidigare.

---

## Steg 4 – Anslut en varnings‑callback till **Capture Font Messages**

Aspose.Words avger varningar för en rad olika förhållanden—teckensnittsersättning är en vanlig. Genom att tillhandahålla en implementation av `IWarningCallback` kan du **capture font messages** i realtid.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Varningshanterarklassen

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description`‑fältet innehåller ett mänskligt läsbart meddelande som t.ex. *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Detta är exakt den typ av output du behöver för att **handle missing fonts** på ett smidigt sätt.

---

## Steg 5 – Ladda dokumentet och låt callbacken göra sitt jobb

Med allt anslutet är inläsning av dokumentet enkelt. Om källfilen refererar till ett teckensnitt som saknas i systemet, kommer vår varningshanterare att triggas.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

När du kör programmet kommer du att se konsolutdata liknande:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Den utskriften är delen **capture font messages** i vårt arbetsflöde. Du kan utöka hanteraren för att logga till en fil, skicka telemetri, eller till och med avbryta konverteringen om kritiska teckensnitt saknas.

---

## Steg 6 – Fullständigt fungerande exempel (Alla delar tillsammans)

Nedan är ett komplett, kopiera‑och‑klistra‑klart program. Klistra in det i `Program.cs`, justera filsökvägarna och kör `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Förväntad utskrift

Att köra programmet på en maskin som saknar *Comic Sans MS* kommer att skriva ut något i stil med:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Du får också en `Result.pdf` som använder de ersatta teckensnitten, vilket säkerställer att konverteringen aldrig kraschar.

---

## Vanliga frågor & kantfall

| Fråga | Svar |
|----------|--------|
| **Vad händer om jag vill att konverteringen ska misslyckas istället för att ersätta?** | Inuti `FontSubstitutionWarningHandler`, kasta ett undantag när `info.Description` innehåller ett kritiskt teckensnittsnamn. |
| **Kan jag automatiskt bädda in ett ersättnings‑teckensnitt?** | Ja. Efter att ha upptäckt ett saknat teckensnitt kan du ladda en reserv‑`FontInfo` från en känd sökväg och lägga till den i `fontSettings` via `fontSettings.SetFontsFolder`. |
| **Fungerar detta på Linux/macOS?** | Absolut. `FontSettings` fungerar på flera plattformar; se bara till att reservmappen innehåller de korrekta `.ttf`‑ eller `.otf`‑filerna. |
| **Är varnings‑callbacken trådsäker?** | Callbacken körs på samma tråd som laddar dokumentet, så du behöver ingen extra synkronisering för konsolloggning. För flertrådade scenarier, skydda delade resurser. |
| **Hur loggar jag varningar till en fil?** | Byt ut `Console.WriteLine` mot `File.AppendAllText("font_warnings.log", ...)` eller använd någon loggningsramverk (Serilog, NLog). |

---

## Proffstips för produktionsklar teckensnittshantering

1. **Cachea teckensnittssökningar** – att återanvända samma `FontSettings`‑instans över flera dokumentladdningar undviker upprepade filsystemskanningar.  
2. **Vitlista kritiska teckensnitt** – om ditt varumärke kräver ett specifikt teckensnitt, verifiera dess närvaro tidigt och avbryt med ett tydligt felmeddelande.  
3. **Använd `SetFontFolder` rekursivt** – att sätta `recursive: true` säkerställer att undermappar skannas, vilket är praktiskt när du levererar en hel teckensnittssamling.  
4. **Kombinera med `FontSubstitutionSettings`** – du kan finjustera ersättningsregler (t.ex. föredra teckensnitt med samma familjenamn).  

---

## Slutsats

Vi har precis **created FontSettings**, konfigurerat `LoadOptions` för att **detect missing fonts**, anslutit en callback som **captures font messages**, och demonstrerat hur man **handle missing fonts** på ett rent, produktionsklart sätt. Hela flödet ryms i några dussin rader C#, men ger dig full insyn i teckensnittslandskapet för alla DOCX‑filer du bearbetar.

Nästa steg, du kan utforska:

- **Bädda in reservteckensnitt** direkt i utdata‑PDF‑filen (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmerad teckensnittsersättning** baserat på företagets varumärkesregler.  
- **Integrera med en CI‑pipeline** för att automatiskt flagga dokument som använder otillåtna teckensnitt.

Prova det, justera varningshanteraren efter dina behov, och låt dina dokumentpipeline köras med förtroende—inga fler mystiska layoutfel orsakade av osynliga teckensnittssubstitutioner.

Lycka till med kodandet! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}