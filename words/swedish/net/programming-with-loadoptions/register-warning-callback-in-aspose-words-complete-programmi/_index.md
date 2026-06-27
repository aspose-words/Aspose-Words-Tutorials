---
category: general
date: 2026-06-27
description: Registrera varningsåteruppringning i Aspose.Words för att fånga teckensnittsbyten
  och laddningsproblem. Lär dig steg‑för‑steg‑användning av LoadOptions med Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: sv
og_description: Registrera varningscallback i Aspose.Words för att övervaka teckensnittssubstitutioner
  och andra laddningsvarningar. Följ den här fullständiga handledningen för en robust
  implementering.
og_title: Registrera varningsåteruppringning i Aspose.Words – Komplett guide
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Registrera varningsåteruppringning i Aspose.Words – Komplett programmeringsguide
url: /sv/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrera varnings‑callback i Aspose.Words – Komplett programmeringsguide

Har du någonsin funderat på hur du **registrerar varnings‑callback i Aspose.Words** så att du exakt kan se vilka teckensnitt som byts ut när ett dokument laddas? Du är inte ensam. Många utvecklare fastnar när en tyst teckensnittssubstitution förstör layouten i en genererad PDF‑ eller Word‑fil.  

I den här handledningen går vi igenom en praktisk lösning som inte bara registrerar en varnings‑callback i Aspose.Words utan också förklarar *varför* du vill göra det, hur callbacken fungerar under huven och vilka kantfall du kan stöta på. I slutet kan du logga varje teckensnittssubstitution, fånga andra laddningsvarningar och hålla din dokument‑bearbetningspipeline transparent.

## Vad du kommer att lära dig

- Ställa in **LoadOptions** för att kontrollera dokumentladdningens beteende.  
- Registrera en **varnings‑callback** som triggas för teckensnittssubstitution och andra varningstyper.  
- Ladda en DOCX med de konfigurerade alternativen och tolka callback‑utdata.  
- Vanliga fallgropar (saknade teckensnitt, anpassade teckensnittsmappar och prestanda‑aspekter).  

**Förkunskaper:** Visual Studio 2022 (eller någon C#‑IDE), .NET 6+‑runtime och en aktiv Aspose.Words‑licens (gratis provversion fungerar för experiment). Inga extra NuGet‑paket utöver `Aspose.Words` behövs.

---

![Diagram som visar flödet för att registrera en varnings‑callback i Aspose.Words och hantera teckensnittssubstitutionsvarningar](register-warning-callback-aspose-words.png "register warning callback aspose.words diagram")

## Steg 1: Skapa LoadOptions – Ingångspunkten för varningshantering  

Innan callbacken kan triggas måste du ha en instans av **LoadOptions**. Tänk på den som kontrollpanelen du ger till Aspose.Words när du säger “ladda den här filen, men meddela mig om något ser felaktigt ut.”  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Varför detta är viktigt:** `LoadOptions` låter dig finjustera allt från krypteringslösenord till teckensnittskataloger. Genom att fästa en varnings‑callback på detta objekt förvandlar du en tyst process till en observerbar.

## Steg 2: Registrera varnings‑callbacken – Fånga teckensnittssubstitutioner  

Nu kommer stjärnan i föreställningen: **varnings‑callbacken**. Vi registrerar en anonym metod (en lambda) som Aspose.Words anropar för varje laddningsvarning. Inuti callbacken filtrerar vi på `WarningType.FontSubstitution` och skriver ut ett vänligt meddelande.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Proffstips:** Om du också vill logga saknade bilder eller icke‑stödda funktioner, lägg till ytterligare `if`‑grenar som kontrollerar `args.WarningType`. Detta gör din **register warning callback in Aspose.Words**‑implementation till en allt‑i‑ett‑lösning för alla laddningsdiagnostiker.

## Steg 3: Ladda dokumentet med de konfigurerade LoadOptions  

När callbacken är ansluten är nästa steg helt enkelt att ladda dokumentet. Skicka `loadOptions`‑instansen till `Document`‑konstruktorn. Varje gång Aspose.Words stöter på ett teckensnitt som den inte kan hitta, triggas din callback och skriver till konsolen.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Kör programmet, så får du en utskrift som liknar:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Det är kärnan i **register warning callback aspose.words**—ett tre‑stegs‑mönster du kan återanvända i alla projekt.

## Steg 4: Utöka callbacken för verkliga scenarier  

### 4.1 Logga till en fil istället för konsolen  

I produktion vill du sällan ha konsolspam. Byt ut `Console.WriteLine` mot en logger (t.ex. `Serilog`, `NLog`) eller skriv till en textfil:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Tillhandahålla en anpassad teckensnittsmapp  

Om din miljö använder företags‑teckensnitt, tala om för Aspose.Words var den ska leta innan den faller tillbaka på substitution:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Nu kan callbacken triggas *mindre* ofta, eftersom motorn hittar rätt teckensnitt.

### 4.3 Hantera icke‑teckensnittsvarningar  

Du kan bredda omfattningen för att fånga alla laddningsvarningar:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Steg 5: Testa din implementation – Vad du kan förvänta dig  

### 5.1 Verifiera med ett dokument som har saknade teckensnitt  

Skapa en liten DOCX som refererar till ett teckensnitt som inte är installerat på din maskin (t.ex. “Comic Sans MS” på en Linux‑server). Kör laddaren; du bör se ett substitutionsmeddelande.  

### 5.2 Benchmarka overhead  

Callbacken lägger till försumbar overhead—ungefär några mikrosekunder per varning. Om du laddar tusentals dokument kan du batch‑logga poster eller inaktivera callbacken för icke‑kritiska körningar.

### 5.3 Kantfall  

- **Flera substitutioner för samma teckensnitt:** Aspose.Words kan trigga callbacken flera gånger om samma saknade teckensnitt förekommer på olika sidor. Deduplikera i din logger om så behövs.  
- **Krypterade dokument:** Om DOCX‑filen är lösenordsskyddad måste du också sätta `loadOptions.Password`. Callbacken triggas fortfarande efter avkryptering.  
- **Asynkron laddning:** API‑et är synkront, men du kan omsluta laddningsanropet i `Task.Run` för bakgrundsbehandling; callbacken förblir trådsäker.

## Vanliga fallgropar & hur du undviker dem  

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|---------|
| **Ingen utskrift alls** | Callbacken är inte tilldelad *eller* `WarningCallback` skrivs över senare. | Se till att du tilldelar callbacken **en gång** innan laddning och att du inte åter‑tilldelar `loadOptions` efter tilldelningen. |
| **Felaktigt cast‑undantag** | Försöker kasta en varning som inte är `FontSubstitutionWarningInfo`. | Kontrollera alltid `args.WarningType` innan du castar. |
| **Prestandaförsämring** | Loggar synkront till en långsam I/O‑mål. | Använd asynkrona loggningsramverk eller buffra skrivningar. |
| **Saknade anpassade teckensnitt** | Teckensnittsmapp har inte lagts till i `FontSettings`. | Lägg till `SetFontsFolder` som visas i Steg 4.2. |

## Fullt fungerande exempel – Kopiera‑och‑kör  

Nedan är ett självständigt program du kan klistra in i ett nytt Console‑App‑projekt. Det demonstrerar hela flödet från början till slut.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Förväntad konsolutskrift** (förutsatt saknade teckensnitt):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Kör programmet, så ser du exakt vilka teckensnitt Aspose.Words bytte ut, vilket ger dig full insyn i laddningsprocessen.

---

## Slutsats  

Vi har precis gått igenom **hur du registrerar varnings‑callback i Aspose.Words**, varför det är en bästa praxis för alla dokument‑bearbetningsarbetsflöden, och hur du kan utöka mönstret för loggning, anpassade teckensnitt och bredare varningshantering. Med bara tre kodrader förvandlar du en svart‑låda‑laddning till ett auditerbart, felsökbart steg—inga fler mystiska layoutförändringar.

Vad blir nästa steg? Prova att kombinera denna callback med **Aspose.Words SaveOptions** för att logga varningar både vid laddning *och* sparning, eller knyt callbacken till ett web‑API som bearbetar uppladdningar i realtid. Du kan också utforska de andra sekundära nyckelorden vi introducerade—som *loadoptions font substitution warning*—för att finjustera prestanda eller integrera med en övervakningsdashboard.

Har du frågor eller ett knepigt scenario? Lämna en kommentar så felsöker vi tillsammans. Lycka till med kodandet, och må dina PDF‑filer alltid renderas med rätt teckensnitt!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}