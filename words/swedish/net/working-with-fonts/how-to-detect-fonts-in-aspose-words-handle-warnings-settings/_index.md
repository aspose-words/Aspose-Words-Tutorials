---
category: general
date: 2026-01-03
description: Hur man upptäcker teckensnitt i Aspose.Words och hanterar varningar med
  Aspose‑teckensnittsinställningar – en steg‑för‑steg‑guide för utvecklare.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: sv
og_description: Hur man upptäcker teckensnitt i Aspose.Words och konfigurerar varningar
  med Aspose‑teckensnittsinställningar. Lär dig hela arbetsflödet på några minuter.
og_title: Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar och inställningar
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar

Har du någonsin funderat **hur man upptäcker teckensnitt** i ett Word‑dokument innan det går i produktion? Du är inte ensam. Saknade teckensnitt kan orsaka layout‑mardrömmar, och utan rätt varningar kan du leverera en trasig PDF eller DOCX utan att ens märka det.  

I den här handledningen går vi igenom **hur man upptäcker teckensnitt** med Aspose.Words, visar **hur man hanterar varningar**, och justerar **Aspose‑teckensnittinställningar** så att du kan **konfigurera varningar** exakt som du vill. I slutet har du ett färdigt kodexempel som skriver ut varje ersättning som Aspose utför, och du vet hur du anpassar det för dina egna projekt.

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.6+).  
- Aspose.Words för .NET installerat via NuGet (`Install-Package Aspose.Words`).  
- En Word‑fil som medvetet refererar ett saknat teckensnitt (t.ex. *DocumentWithMissingFonts.docx*).  

Om du redan har detta, bra—låt oss dyka ner.

![how to detect fonts screenshot](https://example.com/detect-fonts.png "exempel på utdata för hur man upptäcker teckensnitt")

## Hur man upptäcker teckensnitt med Aspose.Words

Det första steget är att tala om för Aspose.Words att du bryr dig om händelser för teckensnittsersättning. Detta görs genom att tillhandahålla en anpassad varnings‑callback via **Aspose‑teckensnittinställningar**. Callback‑en får ett `WarningInfo`‑objekt för varje ersättning, vilket låter dig **upptäcka teckensnitt** vid körning.

### Steg 1: Skapa en varnings‑callback‑klass

Implementera `IWarningCallback`‑gränssnittet. Inuti `Warning`‑metoden filtrerar du på `WarningType.FontSubstitution` och loggar detaljerna.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Proffstips:** Strängen `info.Description` innehåller både det saknade teckensnittets namn och det ersättande teckensnitt som Aspose valde. Du kan parsas om du behöver en strukturerad rapport.

### Steg 2: Konfigurera LoadOptions med Aspose‑teckensnittinställningar

Skapa en `LoadOptions`‑instans, fäst ett nytt `FontSettings`‑objekt, och peka `WarningCallback` mot den handler du just byggt. Detta talar om för Aspose **hur man konfigurerar varningar**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Om du har en privat teckensnittsmapp kan du lägga till den så här:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Den raden visar en annan vinkel av **Aspose‑teckensnittinställningar**—du styr exakt var Aspose letar efter teckensnitt innan det bestämmer sig för att ersätta.

### Steg 3: Läs in dokumentet och utlösa callback‑en

Läs nu in mål‑dokumentet med `loadOptions`. När Aspose analyserar filen triggas varnings‑handlern för varje saknat teckensnitt, vilket effektivt **upptäcker teckensnitt** i realtid.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

När du kör programmet får du en utskrift som liknar:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Steg 4: (Valfritt) Samla varningar för senare bruk

Om du behöver lagra ersättningsdata för en rapport, ändra handlern så att den samlar meddelanden i en lista.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Senare kan du skriva `handler.Substitutions` till en JSON‑fil, skicka den till en loggtjänst, eller visa den i ett UI.

### Steg 5: Verifiera resultatet programatiskt

Ibland vill du försäkra dig om att *ingen* ersättning skedde (t.ex. i en CI‑byggnad). Här är en snabb kontroll:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Detta kodexempel demonstrerar **hur man hanterar varningar** på ett deterministiskt sätt, vilket ger dig full kontroll över byggpipelines.

## Vanliga frågor (och kantfall)

**Vad händer om jag vill ignorera vissa ersättningar?**  
Du kan lägga till villkorlig logik i `Warning` och helt enkelt returnera utan att logga för teckensnitt du anser acceptabla.

**Kan jag undertrycka alla varningar och bara få ett booleskt resultat?**  
Ja—sätt `loadOptions.WarningCallback = null` och inspektera sedan `doc.FontInfo` efter inläsning (även om du förlorar den detaljerade loggen).

**Fungerar detta med PDF‑konvertering?**  
Absolut. Samma varningsmekanism aktiveras när du anropar `doc.Save("out.pdf")`. Callback‑en fångar alla teckensnittsswapp som sker under konverteringssteget.

**Finns det någon prestandapåverkan?**  
Överheaden är minimal—endast några extra metodanrop per saknat teckensnitt. För stora batcher kan du vilja cachea resultaten.

## Sammanfattning: Vad vi gick igenom

- **Hur man upptäcker teckensnitt** genom att implementera en anpassad `IWarningCallback`.  
- **Hur man hanterar varningar** via `LoadOptions.WarningCallback`.  
- Justering av **Aspose‑teckensnittinställningar** (lägga till egna teckensnittsmappar, slå på/av varningar).  
- **Hur man konfigurerar varningar** för både omedelbar konsolutskrift och senare analys.  

Med dessa delar på plats kan du tryggt bearbeta Word‑dokument, garantera att saknade teckensnitt flaggas, och hålla din output konsekvent över miljöer.

## Nästa steg

- Utforska `FontSettings.SubstitutionSettings` för mer finfördelad kontroll (t.ex. mappa specifika saknade teckensnitt till valda ersättningar).  
- Kombinera detta tillvägagångssätt med Aspose.PDF för att generera PDF‑filer som behåller exakt typografi.  
- Automatisera varningskontrollen i en CI/CD‑pipeline för att blockera releaser som innehåller teckensnittsproblem—perfekt för team som **hanterar varningar** som en del av kvalitetsgrindar.

Har du fler frågor om **Aspose‑teckensnittinställningar** eller behöver hjälp med att integrera detta i en större tjänst? Lämna en kommentar nedan, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}