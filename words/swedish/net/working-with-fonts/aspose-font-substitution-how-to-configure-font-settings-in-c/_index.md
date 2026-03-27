---
category: general
date: 2026-03-27
description: 'Aspose teckensnittssubstitution gjort enkelt: lär dig att konfigurera
  teckensnittinställningar, fånga varningar och hantera saknade teckensnitt i dina
  .NET‑appar.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: sv
og_description: Behärska Aspose teckensnittssubstitution genom att konfigurera teckensnittsinställningar
  och hantera saknade teckensnitt med en varningsåteruppringning. Komplett C#‑guide.
og_title: Aspose teckensnittssubstitution – Konfigurera teckensnittsinställningar
  i C#
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose teckensnittssubstitution – Hur man konfigurerar teckensnittsinställningar
  i C#
url: /sv/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Komplett guide för att konfigurera teckensnittsinställningar

Har du någonsin stött på ett dokument som plötsligt byter ditt anpassade typsnitt mot något generiskt? Det är **aspose font substitution** som gör sitt jobb – den ersätter saknade teckensnitt med den närmaste matchning den kan hitta. Det är praktiskt, men om du behöver veta *exakt* vilket teckensnitt som byttes ut, måste du ansluta till bibliotekets varningssystem och konfigurera teckensnittsinställningarna själv.

I den här handledningen går vi igenom ett verkligt scenario: vi laddar en DOCX som refererar till ett teckensnitt du inte har, fångar substitutions‑händelsen och skriver ett vänligt meddelande till konsolen. När du är klar kommer du att känna dig bekväm med **configure font settings**, att koppla en **Aspose.Words warning callback**, och att utöka exemplet för att passa vilket arbetsflöde som helst.

> **What you’ll need**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • A DOCX that references a missing font (we’ll call it `MissingFont.docx`)  

Låt oss dyka ner.

---

## Step 1: Install Aspose.Words and Prepare the Project

Innan vi skriver någon kod, se till att Aspose.Words‑paketet är refererat:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Använd den senaste stabila versionen; i mars 2026 är den 23.11.0. Nyare releaser förbättrar algoritmer för teckensnittsmatchning och lägger till extra varningstyper.

Skapa en ny konsolapp (eller klistra in koden i ett befintligt projekt) och lägg till de vanliga `using`‑direktiven:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Dessa namnrymder ger oss åtkomst till `Document`, `LoadOptions` och de teckensnittsklasser vi kommer att behöva.

## Step 2: Configure Font Settings with LoadOptions

Kärnan i **aspose font substitution**‑kontrollen finns i `LoadOptions.FontSettings`. Genom att tillhandahålla ett tomt `FontSettings`‑objekt säger vi åt Aspose att använda sina standardsökvägar *och* att rapportera eventuell substitution via en varnings‑callback.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Varför inte bara förlita sig på standardinställningarna? För att en varnings‑callback (nästa steg) bara fungerar när egenskapen `FontSettings` är icke‑null. Den här lilla raden ger oss en krok in i substitutionsprocessen utan att ändra det faktiska teckensnittssökbeteendet.

## Step 3: Attach a Warning Callback to Capture Substitutions

Aspose.Words implementerar gränssnittet `IWarningCallback`. När något anmärkningsvärt händer – till exempel ett saknat teckensnitt – anropar det vår `Warning`‑metod. Vi implementerar en liten hanterare som filtrerar på `WarningType.FontSubstitution` och skriver ut beskrivningen.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Och så ser själva hanteraren ut:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this matters** – Utan callback byter Aspose tyst ut teckensnitt, och du får aldrig veta vilket som användes. Callbacken gör processen transparent, vilket är viktigt för efterlevnadsrapportering eller för att felsöka layoutproblem.

## Step 4: Load the Document Using the Configured Options

Nu laddar vi äntligen dokumentet och passerar de `loadOptions` vi just förberett. Om källfilen refererar till ett teckensnitt som inte är installerat, kommer vår hanterare att triggas.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Byt ut `YOUR_DIRECTORY` mot den faktiska sökvägen där `MissingFont.docx` ligger. När du kör programmet bör du se en utskrift liknande:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Den raden talar om exakt vilket teckensnitt som saknades och vilken reserv Aspose valde.

## Step 5: (Optional) Fine‑Tune Font Search Paths

Om du har en privat mapp med företags‑teckensnitt kan du tala om för Aspose var den ska leta innan den faller tillbaka på systemteckensnitt. Detta är en avancerad användning av **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Genom att sätta `recursive: true` får Aspose även att skanna undermappar. Nu kommer biblioteket att försöka med dina privata teckensnitt först, vilket minskar risken för oönskad substitution.

## Full Working Example

Sätter vi ihop allt får vi det kompletta, körklara programmet:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Expected output** (when a missing font is encountered):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Om alla teckensnitt finns installerade körs programmet tyst (inga varningar) och producerar ändå PDF‑filen.

## Common Questions & Edge Cases

### What if I need to *prevent* substitution altogether?

Sätt `FontSettings.SubstitutionSettings` till `null` eller använd `FontSettings.FontSubstitutionSettings` för att styra beteendet. Till exempel:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Nu kommer Aspose att kasta ett undantag istället för att tyst ersätta, vilket kan fångas och hanteras.

### Does this work with other file formats (e.g., .doc, .rtf)?

Absolut. Samma `LoadOptions`‑objekt kan passeras till vilken `Document`‑konstruktor som helst som accepterar en filsökväg. Varnings‑callbacken kommer att triggas för alla format som är beroende av teckensnitt.

### Can I capture the *exact* fallback font name?

Ja. Strängen `info.Description` innehåller både det saknade teckensnittet och ersättningen. Om du behöver namnet programatiskt kan du parsra det eller använda `FontInfo`‑objektet (tillgängligt i nyare versioner).

### How does this behave in a multi‑threaded environment?

`FontSettings` är **inte** trådsäker. Skapa ett separat `LoadOptions` (med sin egen `FontSettings`) per tråd, eller skydda åtkomsten med en låsning.

## Conclusion

Vi har gått igenom allt du behöver för att bemästra **aspose font substitution** och **configure font settings** i en C#‑applikation:

1. Installera Aspose.Words och lägg till de nödvändiga `using`‑satserna.  
2. Skapa ett `LoadOptions`‑objekt med ett nytt `FontSettings`.  
3. Koppla en anpassad `IWarningCallback` för att exponera substitutions‑händelser.  
4. Ladda dokumentet och låt callbacken rapportera eventuella saknade teckensnitt.  
5. (Valfritt) Utöka sökvägen eller inaktivera substitution helt.

Med detta mönster kan du logga saknade teckensnitt för efterlevnad, varna användare i ett UI, eller automatiskt bädda in reservteckensnitt innan publicering. Nästa steg kan vara att utforska **Aspose.Words font substitution policies** eller integrera arbetsflödet i en större dokument‑bearbetningspipeline.

Lycka till med kodningen, och må dina dokument alltid renderas med rätt teckensnitt!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}