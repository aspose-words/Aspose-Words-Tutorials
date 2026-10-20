---
category: general
date: 2026-05-04
description: Leer hoe u Aspose-lettertypevervanging kunt gebruiken om ontbrekende
  lettertypen te detecteren wanneer u een Word‑document laadt en de details van ontbrekende
  lettertypen opvraagt — stapsgewijze handleiding.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: nl
og_description: Beheers Aspose-lettertypevervanging om ontbrekende lettertypen te
  detecteren bij het laden van een Word‑document en om ontbrekende lettertype‑informatie
  op te halen met volledige C#‑code.
og_title: Aspose-lettertypevervanging – Detecteer ontbrekende lettertypen in Word-documenten
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose Lettertypevervanging: Ontdek ontbrekende lettertypen in Word‑documenten'
url: /nl/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Ontdek ontbrekende lettertypen in Word‑documenten

Heb je je ooit afgevraagd waarom een Word‑document er anders uitziet op een andere computer? Vaak is de boosdoener een ontbrekend lettertype, en **Aspose font substitution** is de tool die je in staat stelt die leemtes te ontdekken voordat ze een visueel rampzalig resultaat geven. In deze tutorial lopen we stap voor stap door hoe je **ontbrekende lettertypen** kunt **detecteren** op het moment dat je een **Word‑document laadt**, en vervolgens **ontbrekende lettertype**‑details kunt **ophalen** zodat je ze kunt repareren of vervangen.

We behandelen alles, van het instellen van de waarschuwings‑callback tot het ophalen van een schone lijst met ontbrekende lettertypen. Aan het einde heb je een kant‑klaar C#‑fragment dat precies aangeeft welke lettertypen niet zijn gevonden, en begrijp je waarom dit belangrijk is voor de document‑fidelity.

---

## Voorvereisten – Wat je nodig hebt voordat je begint

- **Aspose.Words for .NET** (v23.12 of later aanbevolen).  
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider, of de `dotnet`‑CLI).  
- Een voorbeeld‑DOCX die opzettelijk een lettertype gebruikt dat je niet geïnstalleerd hebt — noem het `DocumentWithMissingFont.docx`.  
- Basiskennis van C# — niets ingewikkelds, alleen de mogelijkheid om een console‑applicatie uit te voeren.

Als een van deze onderdelen je onbekend voorkomt, pauzeer dan en installeer het NuGet‑pakket:

```bash
dotnet add package Aspose.Words
```

Dat is alles. Geen extra lettertypen, geen externe services.

---

## Stap 1: Laad het Word‑document (en activeer lettertypecontroles)

Het allereerste wat je doet is een **Word‑document laden**. Aspose.Words parseert het bestand en, als het een verwijst naar een lettertype dat niet gevonden kan worden, plaatst het een *FontSubstitution*‑waarschuwing in de wachtrij. Hier is de code die het laden uitvoert:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Waarom dit belangrijk is:** Het vroegtijdig laden van het document geeft Aspose de kans om elke tekst‑run, stijl en ingesloten object te scannen. Als een lettertype niet wordt gevonden op het systeem of in de aangepaste lettertype‑map, krijg je later een waarschuwing.

---

## Stap 2: Koppel een waarschuwingscallback om substitutie‑gebeurtenissen vast te leggen

Aspose.Words gebruikt een callback‑mechanisme om je te informeren over problemen zoals ontbrekende lettertypen. Door een implementatie van `IWarningCallback` toe te wijzen aan `doc.WarningCallback`, kun je elke waarschuwing onderscheppen op het moment dat deze optreedt.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro tip:** Je kunt meerdere callbacks koppelen (bijv. logging, UI‑updates) door ze in een composiet‑patroon te wikkelen, maar voor deze tutorial houdt één enkele callback de zaken duidelijk.

---

## Stap 3: Implementeer de Font Substitution Warning Callback

Nu definiëren we de klasse die het werk daadwerkelijk uitvoert. De callback ontvangt een `WarningInfo`‑object; we filteren op `WarningType.FontSubstitution` en slaan de beschrijving op voor later gebruik.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Wat er gebeurt:** Wanneer Aspose een ontbrekend lettertype tegenkomt, maakt het een waarschuwing aan zoals “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Onze callback print die regel en slaat hem op.

---

## Stap 4: Verwerk het document (optioneel) en verzamel ontbrekende lettertypen

Als je alleen **ontbrekende lettertypen wilt detecteren**, is de laadstap voldoende — de waarschuwingen worden automatisch afgegeven. Veel ontwikkelaars moeten echter ook **ontbrekende lettertype**‑informatie ophalen na het uitvoeren van bepaalde bewerkingen (bijv. opslaan, converteren). Hieronder forceren we een kleine bewerking — opslaan naar PDF — om ervoor te zorgen dat alle waarschuwingen worden uitgegeven, waarna we de verzamelde berichten ophalen.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Verwachte console‑output** (voorbeeld):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Let op hoe elke regel duidelijk het oorspronkelijke lettertype en de door Aspose gekozen fallback aangeeft. Dat is de kern van **aspose font substitution**‑rapportage.

---

## Stap 5: Geavanceerd – Aangepaste lettertype‑bronnen gebruiken om substituties te verminderen

Soms *heb* je de ontbrekende lettertypen wel, maar niet in de standaard systeemmap. Aspose.Words laat je een aangepaste directory aanwijzen via `FontSettings`. Het toevoegen van deze stap kan het aantal substitutie‑waarschuwingen drastisch verlagen.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Waarom dit toevoegen?** Als je documenten over verschillende machines distribueert, zorgt het bundelen van de benodigde lettertypen in een bekende map ervoor dat de visuele weergave overal gelijk blijft. Het maakt ook je **detect missing fonts**‑routine nauwkeuriger, omdat Aspose die map controleert voordat het fallbackt.

---

## Volledig werkend voorbeeld

Alles bij elkaar genomen, hier een enkel, copy‑paste‑klaar console‑programma. Sla het op als `Program.cs` en voer het uit met `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Wat je zou moeten zien:** Als de bron‑DOCX lettertypen refereert die je niet hebt, print de console elke substitutie‑regel gevolgd door een beknopte samenvatting. Als alle lettertypen aanwezig zijn, krijg je de boodschap “No missing fonts were detected.” te zien.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **Geen waarschuwingen verschijnen** | Het document gebruikt alleen systeemlettertypen, of je hebt al een aangepaste map toegevoegd die de ontbrekende lettertypen bevat. | Controleer of de DOCX echt een niet‑beschikbaar lettertype aanroept. Je kunt het in Word openen en een alinea wijzigen naar een zeldzaam lettertype (bijv. “Papyrus”). |
| **Dubbele berichten** | Hetzelfde lettertype wordt in meerdere runs gebruikt, waardoor meerdere waarschuwingen ontstaan. | De‑duplicate de lijst met `Distinct()` als je alleen een unieke set nodig hebt. |
| **Prestatieverlies bij grote documenten** | Elke waarschuwing wordt verwerkt op de UI‑thread. | Voer het laden uit in een achtergrondtaak of gebruik `Parallel.ForEach` voor de post‑processing. |
| **Verkeerd fallback‑lettertype** | Aspose’s standaard fallback komt mogelijk niet overeen met je huisstijl. | Stel `FontSettings.SubstitutionSettings.DefaultFontName` in op een voorkeurs‑fallback (bijv. “Calibri”). |

---

## Uitbreiden van de oplossing – Ontbrekende lettertypen exporteren naar JSON

Als je een webservice bouwt die ontbrekende lettertypen moet rapporteren aan een client, is het serialiseren van de lijst triviaal:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Nu kan je API een nette JSON‑payload teruggeven die een ander systeem kan verwerken.

---

## Conclusie

In deze gids hebben we **Aspose font substitution** van begin tot eind gedemonstreerd: een Word‑document laden, een waarschuwingscallback koppelen, elke *detect missing fonts*‑gebeurtenis vastleggen, en uiteindelijk **ontbrekende lettertype**‑informatie ophalen voor rapportage of remediering. Door optioneel aangepaste lettertype‑mappen toe te voegen kun je de lijst met substituties verkleinen, en met een paar extra regels kun je de resultaten zelfs als JSON exporteren.

Onthoud dat de visuele integriteit van je documenten afhankelijk is van de lettertypen die ze gebruiken. Met de hier getoonde techniek word je nooit meer verrast door een onverwachte fallback.  

Klaar voor de volgende stap? Probeer deze logica te integreren in een grotere document‑verwerkings‑pipeline, of verken andere functies van Aspose.Words zoals lettertype‑embedding (`doc.FontSettings.EmbeddedFonts`). De mogelijkheden zijn eindeloos, en je gebruikers zullen je dankbaar zijn voor de gepolijste output.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}