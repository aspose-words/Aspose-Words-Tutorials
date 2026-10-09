---
category: general
date: 2026-02-24
description: Hoe lettertypen te detecteren in een Word‑document met Aspose.Words.
  Leer hoe je een callback instelt en een Word‑document laadt met een volledig codevoorbeeld.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: nl
og_description: Hoe lettertypen in een Word‑document te detecteren met behulp van
  een waarschuwingscallback. Deze gids laat zien hoe je een callback instelt en een
  Word‑document laadt met Aspose.Words.
og_title: Hoe lettertypen in Word‑documenten te detecteren – Stapsgewijze C#‑handleiding
tags:
- C#
- Aspose.Words
- Document Processing
title: Hoe lettertypen in Word‑documenten te detecteren – Complete C#‑gids
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen te detecteren in Word-documenten – Complete C# gids

Heb je je ooit afgevraagd **hoe je lettertypen** kunt detecteren die ontbreken wanneer je een Word‑bestand laadt? Misschien ben je een document tegengekomen dat er in de editor goed uitziet, maar de PDF die je genereert verwisselt een paar lettertypen achter de schermen. Dat is een klassiek symptoom van lettertype‑substitutie, en het vroegtijdig opsporen kan je behoeden voor vervelende lay‑out verrassingen.

In deze tutorial lopen we een praktische oplossing door: gebruik van **Aspose.Words** om een `.docx` te laden, een waarschuwing‑callback toe te voegen, en **hoe je callback instelt** die elke lettertype‑substitutie rapporteert. Aan het einde weet je niet alleen **hoe je lettertypen** programmatically detecteert, maar begrijp je ook **hoe je callback instelt** correct en **een Word‑document laden** veilig — allemaal in één enkele, uitvoerbare C#‑voorbeeld.

> **Wat je krijgt**
> * Een volledige, kant‑klaar te kopiëren code‑voorbeeld  
> * Stapsgewijze uitleg van elke regel  
> * Tips voor het omgaan met randgevallen zoals meerdere ontbrekende lettertypen of aangepaste lettertype‑mappen  
> * Verwachte console‑output zodat je kunt verifiëren dat alles werkt

---

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Core)  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)  
- Een Word‑bestand dat opzettelijk verwijst naar een lettertype dat je niet geïnstalleerd hebt (bijv. `MissingFont.docx`)  
- Visual Studio, Rider, of elke editor die je wilt

Er zijn geen andere bibliotheken nodig; alles andere maakt deel uit van de standaard .NET‑runtime.

---

## Hoe lettertypen te detecteren in een Word‑document

### Stap 1: Maak Load‑options en koppel een waarschuwing‑callback

Het eerste wat we doen, is Aspose.Words laten weten dat we op de hoogte willen worden gebracht van eventuele problemen die zich voordoen tijdens het laden van het bestand. Hier komt **hoe je callback instelt** om de hoek kijken.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Waarom dit belangrijk is:**  
`LoadOptions` is de poort naar het aanpassen van het laadproces. Door een instantie van `FontWarningCollector` toe te wijzen aan `WarningCallback`, zal Aspose.Words onze `Warning`‑methode aanroepen elke keer dat het een ontbrekend lettertype vervangt door een fallback. Dit is de kern van **hoe je lettertypen** detecteert die niet aanwezig zijn op de machine.

### Stap 2: Bereid de LoadOptions‑instantie voor

Nu maken we een instantie van `LoadOptions` en koppelen we onze callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro‑tip:** Als je wilt bepalen *waar* Aspose zoekt naar vervangende lettertypen, kun je hier ook `loadOptions.FontSettings` instellen. Handig wanneer je een privé‑lettertype‑map op de server hebt.

### Stap 3: Laad het Word‑document

Met de opties klaar, **laden we het Word‑document** eindelijk. Dit is het moment waarop Aspose de DOCX parseert en, als er lettertypen ontbreken, onze callback wordt geactiveerd.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Wat gebeurt er onder de motorkap?**  
Aspose.Words leest de XML‑onderdelen van de DOCX, lost elke `<w:font>`‑referentie op en controleert de systeem‑lettertypecollectie. Telkens wanneer een referentie niet kan worden vervuld, vervangt het het eerste passende fallback‑lettertype en geeft een `FontSubstitution`‑waarschuwing.

### Stap 4: Verifieer de output

Voer het programma uit en bekijk de console. Voor elk ontbrekend lettertype zie je een regel zoals:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Als het document geen ontbrekende lettertypen bevat, blijft de console stil — wat betekent dat **hoe je lettertypen detecteert** geen resultaten opleverde.

### Stap 5: Volledig werkend voorbeeld (Console‑app)

Hieronder staat een zelfstandige `Program.cs` die je in een nieuw console‑project kunt plaatsen. Het bevat alle besproken onderdelen plus een kleine helper om het console‑venster open te houden tijdens het debuggen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Verwachte console‑output** (voorbeeld):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Als je `MissingFont.docx` vervangt door een bestand dat alleen geïnstalleerde lettertypen gebruikt, zie je alleen de regel “Press any key…” — wat bevestigt dat de detectielogica werkt zoals bedoeld.

---

## Veelgestelde vragen & randgevallen

### Wat als ik *alle* waarschuwingen wil vastleggen, niet alleen lettertype‑substitutie?

Verwijder simpelweg de `if (info.Type == WarningType.FontSubstitution)`‑guard. Het `WarningInfo`‑object bevat een `Type`‑enum waarop je kunt schakelen voor andere scenario's (bijv. `DocumentStructure`, `ImageLoading`).

### Kan ik waarschuwingen naar een bestand loggen in plaats van naar de console?

Absoluut. Vervang `Console.WriteLine` door een aanroep van een logging‑framework (`Serilog`, `NLog`, enz.). De callback draait op dezelfde thread die het document laadt, dus zorg ervoor dat je logger thread‑veilig is.

### Hoe gedraagt dit zich in een webapplicatie?

In ASP.NET Core zou je doorgaans een singleton `IWarningCallback`‑implementatie injecteren en deze via `LoadOptions` doorgeven. Vergeet niet om niet rechtstreeks naar de response‑stream te schrijven — log naar een database of een in‑memory‑collectie die je later via een API‑endpoint kunt blootstellen.

### Wat als er aangepaste lettertypen in een niet‑systeemmap staan?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Nu zal Aspose.Words eerst `C:\MyCustomFonts` doorzoeken voordat het terugvalt op de OS‑lettertypen, waardoor het aantal substitutie‑waarschuwingen dat je ziet wordt verminderd.

## Visuele samenvatting

![Lettertype‑waarschuwing‑callback detecteren in Aspose.Words](/images/font-warning-callback.png "Hoe lettertypen te detecteren met een waarschuwing‑callback")

*De screenshot toont de console‑output wanneer een ontbrekend lettertype wordt vervangen. De alt‑tekst bevat het primaire trefwoord voor SEO.*

## Conclusie

Je hebt nu een solide, productie‑klaar patroon voor **hoe je lettertypen** detecteert in elk Word‑bestand dat je laadt met Aspose.Words. Door **hoe je callback instelt** krijg je realtime inzicht in ontbrekende of vervangen lettertypen, en je hebt de juiste manier geleerd om **een Word‑document te laden** terwijl je code schoon en onderhoudbaar blijft.

Volgende stappen? Probeer de callback uit te breiden zodat waarschuwingen in een lijst worden verzameld, en toon ze vervolgens in een UI of een geautomatiseerd rapport. Je kunt ook `FontSettings.SubstitutionSettings` verkennen om te bepalen *welke* lettertypen als fallback worden gekozen.

Voel je vrij om te experimenteren — wissel het document, voeg meer ontbrekende lettertypen toe, of integreer de logica in een grotere document‑verwerkings‑pipeline. Als je tegen problemen aanloopt, laat dan een reactie achter of ping me op GitHub.

Veel plezier met coderen, en moge je documenten altijd weergeven met de lettertypen die je verwacht!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}