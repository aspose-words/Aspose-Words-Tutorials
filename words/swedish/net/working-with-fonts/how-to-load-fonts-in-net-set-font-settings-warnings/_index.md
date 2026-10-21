---
category: general
date: 2026-06-30
description: Lär dig hur du laddar teckensnitt i .NET med LoadOptions, ställer in
  teckensnittsinställningar, aktiverar anpassade teckensnitt och upptäcker saknade
  teckensnitt med varningsåteranrop.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: sv
og_description: Hur laddar man teckensnitt i .NET? Den här guiden visar hur du ställer
  in teckensnittsinställningar, aktiverar anpassade teckensnitt och upptäcker saknade
  teckensnitt med varningsåteranrop.
og_title: Hur man laddar teckensnitt i .NET – Ställ in teckensnittinställningar och
  varningar
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Hur man laddar teckensnitt i .NET – Ställ in teckensnittsinställningar och
  varningar
url: /sv/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så laddar du teckensnitt i .NET – Ställ in teckensnittinställningar & varningar

Har du någonsin undrat **hur man laddar teckensnitt** i ett .NET-dokument utan att dra i håret? Du är inte ensam. Saknade glyfer, tysta reservteckensnitt och kryptiska varningar kan förvandla en enkel rapportgenerator till en mardröm.  

I den här handledningen går vi igenom ett komplett, färdigt‑att‑köra‑exempel som visar **hur man laddar teckensnitt**, konfigurerar **teckensnittinställningar**, **aktiverar anpassade teckensnitt**, och **upptäcker saknade teckensnitt** genom att hantera varningar. I slutet har du ett robust mönster som du kan använda i vilket Aspose.Words‑ eller liknande bibliotekprojekt som helst.

> **Snabb översikt:** vi kommer att skapa ett `LoadOptions`‑objekt, bifoga en varnings‑callback och ladda en DOCX som medvetet refererar till ett saknat teckensnitt. Konsolen kommer att skriva ut ett tydligt meddelande varje gång motorn ersätter ett teckensnitt.

## Vad du behöver

- .NET 6.0 eller senare (koden fungerar även på .NET Framework 4.6+)  
- Aspose.Words för .NET (gratis prov‑NuGet‑paket fungerar)  
- En DOCX‑fil som refererar till ett teckensnitt du *inte* har installerat (t.ex. `MissingFont.docx`)  

Det är allt—inga extra tjänster, inga kryptiska konfigurationsfiler. Om du har dessa tre saker är du redo att följa med.

![exempel på hur man laddar teckensnitt](https://example.com/how-to-load-fonts-diagram.png)

*Image alt text: exempel på hur man laddar teckensnitt*

## Steg 1: Skapa Load‑alternativ och aktivera anpassade teckensnittinställningar  

Det första du gör när du vill **ställa in teckensnittinställningar** är att instansiera ett `LoadOptions`‑objekt. Inuti placerar du en `FontSettings`‑instans som pekar på en mapp som innehåller eventuella anpassade .ttf‑ eller .otf‑filer du kan behöva.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**Varför detta är viktigt:** Som standard letar Aspose.Words bara på system‑installerade teckensnitt. Om ditt dokument använder ett företags‑varumärkes‑teckensnitt som ligger på en nätverksdelning, måste du berätta för biblioteket var det finns. Det är essensen av **enable custom fonts**.

## Steg 2: Bifoga en varningshanterare för att upptäcka saknade teckensnitt  

Om du hoppar över varningshantering byts saknade glyfer tyst ut mot ett reservteckensnitt—ofta Times New Roman. Det kan förstöra varumärket eller till och med orsaka layoutförändringar. För att **how to handle warnings**, bifoga en callback som inspekterar `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**Proffstips:** `WarningCallback` avfyras för *alla* varningar, inte bara saknade teckensnitt. Genom att filtrera på `WarningType.FontSubstitution` hålls utdata rena och svarar direkt på frågan **detect missing fonts**.

## Steg 3: Ladda dokumentet med de konfigurerade alternativen  

Nu när vi har förberett alternativen kan vi äntligen **how to load fonts** i dokumentet. `Document`‑konstruktorn accepterar sökvägen till filen plus de `LoadOptions` vi just byggde.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

Om källfilen refererar till ett teckensnitt som inte finns i systemmappen *eller* den anpassade mappen vi satte tidigare, kommer varnings‑callbacken från Steg 2 att skriva ut en hjälpsam rad i konsolen.

## Steg 4: Verifiera den laddade teckensnittssamlingen (valfritt men insiktsfullt)  

Ibland vill du dubbelkolla vilka teckensnitt som faktiskt löstes upp. Aspose.Words exponerar de `FontSettings` du skickade in, så du kan lista de lösta teckensnittskällorna.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

Att köra detta kodstycke efter laddning kommer att skriva ut något i stil med:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

Varningsraden bekräftar att vi framgångsrikt **detect missing fonts**, medan listan visar att både system‑ och anpassade mappar har konsulterats.

## Steg 5: Spara eller rendera dokumentet  

När dokumentet är laddat och du har verifierat teckensnitten kan du fortsätta med någon bearbetning—spara som PDF, rendera till bilder eller manipulera DOM‑en. För fullständighetens skull, här är en enradare som sparar resultatet som en PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

När PDF‑filen öppnas har alla saknade glyfer ersatts av reservteckensnittet du såg i konsolutdata. Om du lade till det saknade teckensnittet i `C:\MyCustomFonts`, kör programmet igen så försvinner varningen—bevis på att **enable custom fonts** verkligen fungerar.

---

## Fullständigt fungerande exempel

Kopiera hela blocket nedan till ett nytt konsolprojekt, lägg till Aspose.Words‑NuGet‑paketet och tryck på **Run**. Anpassa filsökvägarna så att de matchar din miljö.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### Förväntad utdata

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

Om du placerar den saknade `Papyrus.ttf`‑filen i `C:\MyCustomFonts` och kör programmet igen, försvinner varningsraden, vilket bekräftar att den anpassade mappen har konsulterats korrekt.

---

## Vanliga frågor & fallgropar

| Fråga | Svar |
|----------|--------|
| **Vad händer om jag inte har en varnings‑callback?** | Dokumentet laddas fortfarande, men du får ingen information om när en ersättning skedde. Att lägga till callbacken är det enklaste sättet att **how to handle warnings**. |
| **Kan jag ladda teckensnitt från en zip‑fil?** | Ja—använd `new FolderFontSource(zipPath, true)` eller implementera en anpassad `IFontSource`. Detta faller fortfarande under **enable custom fonts**. |
| **Behöver jag bädda in teckensnitt i PDF‑filen?** | Ställ in `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` innan du sparar. Inbäddning garanterar att PDF‑filen ser likadan ut på alla maskiner. |
| **Vad händer om dokumentet använder ett teckensnitt som är licensierat och inte får distribueras?** | Du kan fortfarande *upptäcka* det saknade teckensnittet via varningar, men du bör inte bädda in det om du inte har rättigheterna. Överväg att ersätta det med ett liknande öppna källkods‑teckensnitt. |

## Sammanfattning

Vi har gått igenom **how to load fonts** i .NET genom att:

1. Skapa `LoadOptions` och konfigurera **set font settings**.  
2. **Enable custom fonts** genom att peka på en mapp med extra teckensnitt.  
3. **How to handle warnings** med en `WarningCallback` som skriver ut meddelanden om teckensnittsersättningar.  
4. **Detect missing fonts** genom att filtrera `WarningType.FontSubstitution`.  
5. Spara dokumentet, vilket bekräftar att reservteckensnittet

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ställ in teckensnittsmappsystem och anpassad mapp](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hur man fångar teckensnitt i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}