---
category: general
date: 2026-04-01
description: Aktivera teckensnittsvarningar när du laddar Word-dokument med Aspose.Words.
  Lär dig hur du fångar teckensnittssubstitutionshändelser med C# LoadOptions och
  teckensnittsinställningar.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: sv
og_description: Aktivera teckensnittsvarningar när du laddar Word-dokument med Aspose.Words.
  Denna handledning visar hur du fångar händelser för teckensnittsbyte i C#.
og_title: Aktivera teckensnittsvarningar i Aspose.Words – Komplett C#‑guide
tags:
- Aspose.Words
- C#
- Font Management
title: Aktivera teckensnittsvarningar i Aspose.Words – Komplett C#‑guide
url: /sv/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera teckensnittsvarningar i Aspose.Words – Komplett C#-guide

Har du någonsin undrat varför ett Word‑dokument plötsligt ser annorlunda ut efter att du har laddat det programmässigt? **Enable Font Warnings** och du får omedelbart veta när Aspose.Words byter ut ett saknat teckensnitt mot ett reservteckensnitt. I den här handledningen går vi igenom ett praktiskt exempel som inte bara fångar dessa ersättningar utan också förklarar *varför* de sker.

Vi kommer att gå igenom allt du behöver för att komma igång: det nödvändiga NuGet‑paketet, den exakta `LoadOptions`‑konfigurationen och en prydlig konsolutskrift som visar vilka teckensnitt som ersattes. I slutet har du ett robust, återanvändbart mönster för **C# document processing** som fungerar med alla versioner av Aspose.Words.

## Vad du kommer att lära dig

- Hur du skapar en `LoadOptions`‑instans som spårar teckensnittsändringar.  
- Syftet med `SubstitutionWarning`‑händelsen och hur du kopplar den.  
- Ett komplett, körbart kodexempel som skriver tydliga varningar till konsolen.  
- Tips för att hantera edge‑cases såsom dokument som bara innehåller standardteckensnitt.  

Ingen tidigare erfarenhet av Aspose.Words krävs—bara en grundläggande förtrogenhet med C# och .NET.

---

![Aktivera teckensnittsvarningar diagram](placeholder-image.png "Aktivera teckensnittsvarningar diagram")

*Alt text: diagram för aktivera teckensnittsvarningar som visar händelseflödet när ett saknat teckensnitt ersätts.*

## Steg 1: Ställ in LoadOptions och aktivera teckensnittsvarningar

Det första du behöver är ett `LoadOptions`‑objekt. Denna behållare talar om för Aspose.Words hur filen du ska ladda ska behandlas. Genom att tilldela en ny `FontSettings`‑instans öppnar du dörren till teckensnittshändelser.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Varför detta är viktigt:**  
Om du hoppar över `FontSettings`‑tilldelningen kommer Aspose.Words fortfarande att ersätta saknade teckensnitt, men du får ingen notifikation. Varningsmekanismen finns i `FontSettings`, så att initiera den är *avgörande* för vårt mål.

> **Pro tip:** Du kan också peka `FontSettings` på en anpassad teckensnittsmapp med `SetFontsFolder`. Det minskar antalet varningar du ser, eftersom Aspose.Words faktiskt kan hitta de saknade teckensnitten.

## Steg 2: Prenumerera på SubstitutionWarning‑händelsen (teckensnittsersättning)

Nu när `FontSettings`‑objektet finns, kopplar vi in oss på dess `SubstitutionWarning`‑händelse. Denna händelse avfyras **varje gång** Aspose.Words ersätter ett begärt teckensnitt med något annat.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Varför detta är viktigt:**  
Utan denna lyssnare har du ingen insyn i ersättningsprocessen. Konsolraden ger dig ett snabbt revisionsspår, vilket är särskilt praktiskt under automatiserade byggen eller när du genererar PDF‑filer för branscher med strikta efterlevnadskrav.

> **Vanlig fråga:** *Vad händer om jag vill undertrycka varningarna?*  
> Du kan helt enkelt koppla bort hanteraren eller sätta `FontSettings.SubstitutionWarning += null;`. Att behålla varningarna är dock oftast den säkraste vägen eftersom tysta ersättningar kan leda till layoutfel.

## Steg 3: Ladda ditt dokument med konfigurerade alternativ (C# document processing)

När varningssystemet är klart är det enkelt att ladda dokumentet. Skicka `LoadOptions`‑instansen till `Document`‑konstruktorn, så tar Aspose.Words hand om resten.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Varför detta är viktigt:**  
`LoadOptions`‑objektet är bron mellan den råa filen och varningsinfrastrukturen. Om du utelämnar det laddas dokumentet tyst, och alla saknade teckensnitt ersätts utan spår.

> **Edge case:** Vissa dokument bäddar in exakt de teckensnittsfiler de behöver. I det scenariot visas ingen varning eftersom Aspose.Words hittar det inbäddade teckensnittet. Koden ovan fungerar fortfarande; du får bara en tom konsolutskrift.

## Steg 4: Verifiera utskriften och vanliga fallgropar

Kör programmet från en kommandoprompt eller din IDE:s debugger. Om källdokumentet innehåller ett teckensnitt som inte är installerat på maskinen (eller inte finns i den anpassade teckensnittsmappen) kommer du att se rader som:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Om inget skrivs ut, är det antingen:

1. Alla teckensnitt hittades, **eller**  
2. `SubstitutionWarning`‑hanteraren var inte korrekt kopplad (dubbelkolla Steg 2).

### Varför sker teckensnittsersättningar?

- **Missing system font:** Operativsystemet har inte det begärda teckensnittet.  
- **Unsupported font format:** Aspose.Words kan läsa TrueType och OpenType, men inte alla proprietära format.  
- **License restrictions:** Vissa kommersiella teckensnitt blockerar inbäddning, vilket tvingar en reserv.

Att förstå *varför* hjälper dig att avgöra om du ska leverera de saknade teckensnitten med din app eller justera dokumentets stil.

## Bonus: Styrning av reservteckensnittet

Om du vill att varje saknat teckensnitt ska falla tillbaka till en specifik familj (t.ex. “Calibri”), kan du ange en global ersättningsregel:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Nu kommer konsolen fortfarande att varna dig, men det visuella resultatet blir konsekvent för alla saknade teckensnitt.

---

## Sammanfattning

- **Enable Font Warnings** genom att skapa en `LoadOptions` med en ny `FontSettings`.  
- Koppla `SubstitutionWarning`‑händelsen för att få realtidsvarningar när ett teckensnitt ersätts.  
- Ladda ditt dokument med de konfigurerade alternativen, och spara eventuellt till PDF för att se den visuella effekten.  
- Diagnostisera varför en ersättning inträffade och, om behövs, tvinga ett specifikt reservteckensnitt.

Du har just lagt till ett skyddsnät i ditt **Aspose.Words**‑arbetsflöde som förhindrar tysta layoutförändringar. Nästa steg kan vara att utforska **font settings** som `DefaultFontName` eller dyka ner i **document rendering**‑alternativ för att finjustera PDF‑utdata.

---

### Vad du kan prova härnäst?

- **Utforska andra FontSettings‑funktioner**: `SetFontsFolder`, `LoadFontSources` och `DefaultFontName`.  
- **Kombinera varningar med loggningsramverk** (Serilog, NLog) för produktionsklassade diagnostik.  
- **Experimentera med olika dokumentformat** (`.doc`, `.rtf`, `.html`) för att se hur var och en hanterar saknade teckensnitt.  

Har du frågor eller ett udda scenario? Lämna en kommentar nedan, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}