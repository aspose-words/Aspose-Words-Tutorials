---
category: general
date: 2026-05-23
description: Ställ in varningscallback i Aspose för att fånga varningar om teckensnittssubstitution
  i Aspose.Words. Lär dig LoadOptions, FontSettings och implementering av IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: sv
og_description: Ställ in varningsåteruppringning i Aspose för att övervaka teckensnittsbyte
  i Aspose.Words. Denna handledning visar LoadOptions, FontSettings och implementering
  av varningshanterare.
og_title: Ställ in varningsåteruppringning aspose – Steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Ställ in varningsåteruppringning aspose – Komplett guide för laddning av Word-dokument
url: /sv/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Complete Guide for Word Document Loading

Har du någonsin undrat hur man **set warning callback aspose** så att du aldrig missar en varning om teckensnittsbyte igen? Du är inte ensam. När en DOCX refererar till ett teckensnitt som inte är installerat, byter Aspose.Words tyst ut det, och utan en korrekt återuppringning kanske du aldrig får veta att något har förändrats.

I den här handledningen går vi igenom ett komplett, körbart exempel som visar exakt hur man fångar dessa varningar. I slutet kommer du att förstå **Aspose.Words LoadOptions**, hur man konfigurerar **FontSettings**, och varför implementering av **IWarningCallback** är det renaste sättet att hålla sig uppdaterad. Ingen onödig information—bara koden du kan lägga in i ett .NET‑projekt idag.

## Vad du kommer att lära dig

- Hur man **set warning callback aspose** på en `LoadOptions`‑instans.  
- Rollens av **Aspose.Words LoadOptions** när ett dokument öppnas.  
- Konfigurera hantering av **Aspose fonts substitution** med `FontSettings`.  
- Skriva en anpassad **IWarningCallback‑implementation** för att logga teckensnittproblem.  
- Ladda ett dokument säkert med bästa praxis för **Aspose document loading**.

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar även på .NET Framework 4.5+).  
- En giltig Aspose.Words för .NET‑licens eller en provnyckel.  
- Visual Studio, Rider eller någon C#‑redigerare du föredrar.  
- Ett exempel‑DOCX (`fontTest.docx`) som refererar till ett saknat teckensnitt (valfritt men hjälpsamt).

> **Proffstips:** Om du inte har ett DOCX med saknat teckensnitt, byt bara namn på ett teckensnitt i dokumentets stil och se varningen avfyras.

## Hur man sätter varningsåteruppringning aspose för dokumentladdning

Nedan är det kompletta, självständiga programmet. Spara det som `Program.cs`, återställ NuGet‑paketen och kör. Konsolen kommer att skriva ut varje teckensnittssubstitutionsvarning som Aspose.Words genererar vid inläsning av filen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Förväntad konsolutdata

Om `fontTest.docx` refererar till ett teckensnitt som inte är installerat, kommer du att se något liknande:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Om alla teckensnitt finns, kommer den enda raden som skrivs ut att vara *Document loaded successfully*—inga varningar, inget brus.

![set warning callback aspose example](image.png "set warning callback aspose example")

## Förstå LoadOptions i Aspose.Words

`LoadOptions` är porten till varje justering du kan göra för **aspose document loading**. Den låter dig:

1. **Ange en anpassad `FontSettings`** – användbart när din app levererar egna teckensnitt.  
2. **Bifoga en varningsåteruppringning** – exakt vad vi gjorde för att fånga teckensnittssubstitutioner.  
3. Styr dokumentformatdetektering, lösenordshantering och mer.

Eftersom `LoadOptions` skickas till `Document`‑konstruktorn, tillämpas inställningarna **en gång**, precis när filen parsas. Det är därför vi kan garantera att vår varningshanterare ser varje substitution innan dokumentet ens byggs i minnet.

### När man ska använda anpassade LoadOptions

- **Batch‑bearbetning** av många filer där du vill ha en enhetlig loggningsstrategi.  
- **Molntjänster** som behöver rapportera saknade teckensnitt tillbaka till anroparen.  
- **Test‑pipelines** som verifierar att dokument följer en företags‑teckensnittspolicy.

## Konfigurera FontSettings för Aspose fonts substitution

`FontSettings`‑objektet styr hur Aspose.Words löser teckensnitt. Som standard söker det i systemets teckensnittsmappar och faller sedan tillbaka på inbyggda substitut. Du kan finjustera detta beteende:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Dessa rader är valfria för det grundläggande “set warning callback aspose”‑scenariot, men de visar hur du kan **reducera** antalet substitutionsvarningar genom att tillhandahålla rätt teckensnitt i förväg.

## Implementera IWarningCallback för varningar om teckensnittssubstitution

`IWarningCallback`‑gränssnittet är litet—endast en enda `Warning`‑metod. Ändå ger det dig **full kontroll** över hur varningar hanteras:

- **Logga till en fil** istället för konsolen.  
- **Samla varningar** i en lista för senare analys.  
- **Kasta undantag** för kritiska varningar (t.ex. när ett obligatoriskt teckensnitt saknas).

Här är ett snabbt exempel som lagrar varningar i en `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Du kan sedan inspektera `handler.Messages` efter att ha laddat dokumentet för att avgöra om du ska avbryta bearbetningen.

## Ladda ett dokument med anpassad varningshantering (fullt arbetsflöde)

När vi sätter ihop allt ser det slutgiltiga mönstret du sannolikt kommer att återanvända ut så här:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Detta kodsnutt demonstrerar flödet för **aspose document loading** som du kommer att använda i produktion: konfigurera, ladda, sedan reagera. Mönstret skalar bra oavsett om du bearbetar en enda fil eller loopar över tusentals.

## Vanliga frågor & kantfall

**Vad händer om dokumentet är lösenordsskyddat?**  
Lägg till `Password = "secret"` i `LoadOptions`‑initialiseraren. Varningsåteruppringningen fungerar fortfarande när filen har dekrypterats.

**Kommer återuppringningen att triggas för andra varningstyper?**  
Ja—`WarningInfo.Type` kan vara `DocumentStructure`, `UnsupportedFileFormat` osv. I vårt exempel filtrerar vi på `FontSubstitution`, men du kan logga allt genom att ta bort `if`‑kontrollen.

**Påverkar detta prestanda?**  
Obetydligt. Återuppringningen anropas endast när en varning inträffar, vilket är mycket färre gånger än de normala parsingsstegen.

**Kan jag inaktivera teckensnittssubstitution helt?**  
Du kan sätta `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` men då kommer Aspose.Words att kasta ett undantag för saknade teckensnitt istället för att byta dem.

## Slutsats

Du vet nu exakt hur du **set warning callback aspose** för att övervaka teckensnittssubstitutionshändelser under **Aspose.Words LoadOptions**‑bearbetning. Genom att konfigurera `FontSettings`, implementera en lättviktig `IWarningCallback` och ladda dokumentet med dessa alternativ får du full insyn i alla teckensnittsförändringar som Aspose gör i bakgrunden.

Från här kan du:

- Utöka varningshanteraren för att skriva till en central loggtjänst.  
- Kombinera återuppringningen med en anpassad teckensnittsfallback‑strategi.  
- Använd mönstret när du bygger ett moln‑API som validerar klient‑uppladdade dokument.

Prova det med dina egna DOCX‑filer, justera `FontSettings` och se hur konsolen exakt visar vilka teckensnitt som byttes. Lycka till med kodningen, och må dina dokument alltid renderas som avsett!

## Relaterade handledningar

- [Fånga varningar om teckensnittssubstitution i Java med Aspose.Words – Komplett guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aktivera varningar för teckensnittssubstitution i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Hur man sätter LoadOptions i Aspose.Words för Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}