---
category: general
date: 2026-03-08
description: Aangepaste lettertype‑instellingen laten u lettertype‑instellingen instellen,
  Word‑documenten veilig laden en ontbrekende lettertypen afhandelen met Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: nl
og_description: Aangepaste lettertype‑instellingen stellen je in staat om lettertype‑instellingen
  te configureren, Word‑documenten veilig te laden en ontbrekende lettertypen af te
  handelen met Aspose.Words.
og_title: Aangepaste lettertype‑instellingen in C# – Word laden & omgaan met ontbrekende
  lettertypen
tags:
- Aspose.Words
- C#
- Font Management
title: Aangepaste lettertype‑instellingen in C# – Laad Word en verwerk ontbrekende
  lettertypen
url: /nl/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aangepaste lettertype‑instellingen in C# – Word laden & ontbrekende lettertypen afhandelen

Heb je je ooit afgevraagd hoe **custom font settings** werken wanneer een Word‑bestand lettertypen verwijst die je niet geïnstalleerd hebt? Het is een veelvoorkomend probleem—je document ziet er op één machine goed uit, maar opeens schakelt elke alinea op een fallback‑lettertype op een andere.

Het goede nieuws? Met Aspose.Words kun je **set font settings**, **load Word document**‑inhoud, en **handle missing fonts** allemaal in één nette workflow. Hieronder vind je een volledig, kant‑klaar voorbeeld dat precies laat zien hoe je het doet, plus de “waarom” achter elke stap.

## Wat je zult leren

* Een `LoadOptions`‑object maken en een `FontSettings`‑instance eraan koppelen.  
* Een waarschuwing‑callback registreren zodat je kunt zien welke lettertypen worden vervangen.  
* Een DOCX‑bestand laden dat mogelijk lettertypen mist, en de substitutie‑details naar de console schrijven.  

Aan het einde kun je je C#‑app met vertrouwen distribueren, wetende dat elk ontbrekend‑lettertype‑scenario wordt gelogd en later kan worden aangepakt.

> **Prerequisite:** Aspose.Words for .NET (v23.12 of nieuwer) geïnstalleerd via NuGet, en een basiskennis van C#‑console‑apps.

---

## Aangepaste lettertype‑instellingen – LoadOptions configureren

Het eerste wat je nodig hebt is een `LoadOptions`‑object. Hiermee vertel je Aspose.Words hoe het inkomende bestand moet behandelen. Door een verse `FontSettings`‑instance toe te wijzen, geven we de bibliotheek een plek om naar aangepaste lettertypen te zoeken.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Why this matters:**  
If you skip `FontSettings`, Aspose.Words falls back to the system’s default font collection. That means any missing font will be silently substituted, and you won’t know which ones were swapped. By creating an explicit `FontSettings` container you gain full control over the lookup process.

**Waarom dit belangrijk is:**  
Als je `FontSettings` overslaat, valt Aspose.Words terug op de standaard lettertype‑collectie van het systeem. Dat betekent dat elk ontbrekend lettertype stilletjes wordt vervangen, en je niet weet welke zijn verwisseld. Door een expliciete `FontSettings`‑container te maken, krijg je volledige controle over het zoekproces.

---

## Lettertype‑instellingen op LoadOptions instellen

Nu we een `FontSettings`‑object hebben, vraag je je misschien af waar je het naartoe moet wijzen. Meestal voeg je een map toe die de lettertypen bevat die je met je applicatie meelevert:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Als je geen private map hebt, kun je dit blok weglaten—Aspose.Words zal nog steeds ontbrekende lettertypen melden via de warning‑callback.*

**Pro tip:** Gebruik de `recursive: true`‑vlag als je lettertypen verspreid staan over sub‑mappen. Het bespaart je het handmatig toevoegen van elk pad.

---

## Word‑document laden met aangepaste lettertype‑instellingen

Met de opties klaar, is het laden van het document een fluitje van een cent. De `Document`‑constructor accepteert het bestandspad en de `LoadOptions` die we zojuist hebben opgebouwd.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**What’s happening under the hood?**  
Aspose.Words parses the DOCX, checks every `<w:font>` reference, and consults the `FontSettings` you supplied. If a font isn’t found, it triggers a warning of type `FontSubstitution`. Our custom handler (shown next) will catch those warnings.

**Wat er onder de motorkap gebeurt:**  
Aspose.Words parseert de DOCX, controleert elke `<w:font>`‑referentie en raadpleegt de `FontSettings` die je hebt opgegeven. Als een lettertype niet wordt gevonden, wordt er een waarschuwing van het type `FontSubstitution` gegenereerd. Onze aangepaste handler (hieronder) vangt die waarschuwingen op.

---

## Ontbrekende lettertypen afhandelen met warning‑callback

De `IWarningCallback`‑interface laat je reageren op eventuele problemen die tijdens het laden optreden. Implementeren is eenvoudig:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Wanneer het document is geladen, zal elk ontbrekend lettertype een regel veroorzaken zoals:

```
Font substituted: Arial -> Liberation Sans
```

**Why you should log this:**  
In production you can redirect these messages to a file or telemetry system, making it easy to spot which fonts you need to bundle or license.

**Waarom je dit moet loggen:**  
In productie kun je deze berichten doorsturen naar een bestand of telemetriesysteem, waardoor het eenvoudig wordt om te zien welke lettertypen je moet bundelen of licentiëren.

---

## Volledig werkend voorbeeld

Hieronder staat een zelf‑containend console‑programma dat alles samenbrengt. Kopieer‑en‑plak het in een nieuw .NET Core‑console‑project en klik op **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Expected output** (assuming `input.docx` uses a font you don’t have):

**Verwachte output** (ervan uitgaande dat `input.docx` een lettertype gebruikt dat je niet hebt):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Als alle lettertypen aanwezig zijn, zie je alleen de laatste bevestigingsregel.

---

## Veelgestelde vragen & randgevallen

| Question | Answer |
|----------|--------|
| **What if I need to embed the missing fonts into the PDF?** | After loading, call `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` and then enable embedding with `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Can I suppress the warnings instead of logging them?** | Yes—set `loadOptions.WarningCallback = null;` or implement the callback to ignore non‑font warnings. |
| **Does this work with `.doc` and `.rtf` files?** | Absolutely. The same `LoadOptions` object applies to any format supported by Aspose.Words. |
| **Is the callback thread‑safe?** | The callback runs on the same thread that loads the document, so you can safely write to the console. For multi‑threaded scenarios, use a concurrent collection or logging framework. |

| Vraag | Antwoord |
|-------|----------|
| **Wat als ik de ontbrekende lettertypen in de PDF moet insluiten?** | Na het laden roep je `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` aan en schakel je insluiten in met `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Kan ik de waarschuwingen onderdrukken in plaats van ze te loggen?** | Ja—stel `loadOptions.WarningCallback = null;` of implementeer de callback om niet‑lettertype‑waarschuwingen te negeren. |
| **Werkt dit met `.doc`‑ en `.rtf`‑bestanden?** | Absoluut. Hetzelfde `LoadOptions`‑object geldt voor elk formaat dat door Aspose.Words wordt ondersteund. |
| **Is de callback thread‑safe?** | De callback wordt uitgevoerd op dezelfde thread die het document laadt, dus je kunt veilig naar de console schrijven. Voor multi‑threaded scenario’s gebruik je een concurrente collectie of een logging‑framework. |

---

## Pro Tips & valkuilen

* **Pro tip:** Als je een lettertype meegeeft dat niet op de doelmachine is geïnstalleerd, voeg het dan toe aan de map die je doorgeeft aan `SetFontsFolder`. Dit garandeert deterministische weergave.  
* **Let op licenties:** Sommige lettertypen vereisen een commerciële licentie voor insluiting. Controleer altijd de EULA van het lettertype voordat je het bundelt.  
* **Performance‑opmerking:** Het laden van grote bibliotheken met lettertypen kan het parseren van documenten vertragen. Houd de map slank—neem alleen de lettertypen op die je daadwerkelijk nodig hebt.  
* **Randgeval:** Wanneer een document een lettertype verwijst via de *PostScript‑naam* in plaats van de familienaam, lost Aspose.Words dit nog steeds op zolang het lettertype‑bestand aanwezig is in het zoekpad.  

---

## Conclusie

Je hebt nu een compleet, productie‑klaar patroon voor het gebruik van **custom font settings** in C#. Door `LoadOptions` te configureren, een warning‑callback te registreren, en eventueel naar een private lettertype‑map te wijzen, kun je **set font settings**, **load Word document**‑inhoud betrouwbaar

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}