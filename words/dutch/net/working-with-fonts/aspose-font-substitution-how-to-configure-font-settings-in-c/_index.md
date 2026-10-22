---
category: general
date: 2026-03-27
description: 'Aspose Lettertypevervanging eenvoudig gemaakt: leer hoe u lettertype‑instellingen
  configureert, waarschuwingen vastlegt en ontbrekende lettertypen afhandelt in uw
  .NET‑applicaties.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: nl
og_description: Beheers Aspose-lettertypevervanging door het configureren van lettertype‑instellingen
  en het afhandelen van ontbrekende lettertypen met een waarschuwingscallback. Complete
  C#‑gids.
og_title: Aspose Lettertypevervanging – Configureer lettertype-instellingen in C#
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose Lettertypevervanging – Hoe lettertype‑instellingen in C# te configureren
url: /nl/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Complete Gids voor het Configureren van Font-instellingen

Kom je ooit een document tegen dat plotseling je aangepaste lettertype vervangt door iets generieks? Dat is **aspose font substitution** die zijn werk doet—ontbrekende lettertypen vervangt door de dichtstbijzijnde match die het kan vinden. Het is handig, maar als je *exact* wilt weten welk lettertype is vervangen, moet je gebruikmaken van het waarschuwingssysteem van de bibliotheek en de font‑instellingen zelf configureren.

In deze tutorial lopen we door een real‑world scenario: het laden van een DOCX die een lettertype referereert dat je niet hebt, het vastleggen van het substitutie‑event, en het afdrukken van een vriendelijke boodschap naar de console. Aan het einde ben je vertrouwd met **configure font settings**, het opzetten van een **Aspose.Words warning callback**, en het uitbreiden van het voorbeeld om in elke workflow te passen.

> **Wat je nodig hebt**  
> • .NET 6+ (of .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • Een DOCX die een ontbrekend lettertype referereert (we noemen het `MissingFont.docx`)  

Laten we beginnen.

---

## Stap 1: Installeer Aspose.Words en bereid het project voor

Voordat we code schrijven, zorg ervoor dat het Aspose.Words‑pakket is gerefereerd:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gebruik de nieuwste stabiele versie; vanaf maart 2026 is dat 23.11.0. Nieuwere releases verbeteren de algoritmen voor font‑matching en voegen extra waarschuwings‑types toe.

Maak een nieuwe console‑app (of plaats de code in een bestaand project) en voeg de gebruikelijke `using`‑directieven toe:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Deze namespaces geven ons toegang tot de `Document`, `LoadOptions` en de font‑gerelateerde klassen die we nodig hebben.

## Stap 2: Configureer Font‑instellingen met LoadOptions

Het hart van de **aspose font substitution**‑controle zit in `LoadOptions.FontSettings`. Door een leeg `FontSettings`‑object te leveren, vertellen we Aspose om zijn standaard zoekpaden te gebruiken *en* om elke substitutie te rapporteren via een waarschuwings‑callback.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Waarom niet gewoon op de standaardinstellingen vertrouwen? Omdat het koppelen van een waarschuwings‑callback (volgende stap) alleen werkt wanneer de `FontSettings`‑eigenschap niet null is. Deze kleine regel geeft ons een haak in het substitutieproces zonder het daadwerkelijke font‑zoekgedrag te wijzigen.

## Stap 3: Koppel een Waarschuwings‑callback om Substituties Vast te Leggen

Aspose.Words implementeert de `IWarningCallback`‑interface. Telkens wanneer er iets noemenswaardigs gebeurt—zoals een ontbrekend lettertype—roept het onze `Warning`‑methode aan. We implementeren een kleine handler die filtert op `WarningType.FontSubstitution` en de beschrijving afdrukt.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

En hier is de handler zelf:

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

> **Waarom dit belangrijk is** – Zonder de callback verwisselt Aspose stilletjes lettertypen, en je weet nooit welk lettertype is gebruikt. De callback maakt het proces transparant, wat essentieel is voor compliance‑rapportage of voor het debuggen van lay‑outproblemen.

## Stap 4: Laad het Document met de Geconfigureerde Opties

Nu laden we eindelijk het document, waarbij we de `loadOptions` doorgeven die we zojuist hebben voorbereid. Als het bronbestand een lettertype referereert dat niet geïnstalleerd is, wordt onze handler geactiveerd.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Vervang `YOUR_DIRECTORY` door het daadwerkelijke pad waar `MissingFont.docx` zich bevindt. Wanneer je het programma uitvoert, zou je output moeten zien die lijkt op:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Die regel vertelt je precies welk lettertype ontbrak en welke fallback Aspose heeft gekozen.

## Stap 5: (Optioneel) Fijn‑afstellen van Font‑Zoekpaden

Als je een privémap met bedrijfs‑fonts hebt, kun je Aspose vertellen waar te zoeken voordat het terugvalt op systeem‑fonts. Dit is een geavanceerd gebruik van **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Het instellen van `recursive: true` zorgt ervoor dat Aspose ook submappen scant. Nu zal de bibliotheek eerst je privé‑fonts proberen, waardoor de kans op ongewenste substitutie wordt verkleind.

## Volledig Werkend Voorbeeld

Alles samenvoegend, hier is het volledige, kant‑klaar programma:

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

**Verwachte output** (wanneer een ontbrekend lettertype wordt aangetroffen):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Als alle lettertypen aanwezig zijn, draait het programma stil (geen waarschuwingen) en produceert nog steeds de PDF.

## Veelgestelde Vragen & Randgevallen

### Wat als ik substitutie volledig wil *voorkomen*?

Set the `FontSettings.SubstitutionSettings` to `null` or use `FontSettings.FontSubstitutionSettings` to control the behavior. For example:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Nu zal Aspose een uitzondering gooien in plaats van stilletjes te substitueren, die kan worden opgevangen en afgehandeld.

### Werkt dit met andere bestandsformaten (bijv. .doc, .rtf)?

Absoluut. Hetzelfde `LoadOptions`‑object kan worden doorgegeven aan elke `Document`‑constructor die een bestandspad accepteert. De waarschuwings‑callback wordt geactiveerd voor alle formaten die afhankelijk zijn van fonts.

### Kan ik de *exacte* fallback‑fontnaam vastleggen?

Ja. De `info.Description`‑string bevat zowel het ontbrekende lettertype als de vervanging. Als je de naam programmatically nodig hebt, kun je deze parseren of het `FontInfo`‑object gebruiken (beschikbaar in nieuwere versies).

### Hoe gedraagt dit zich in een multi‑threaded omgeving?

`FontSettings` is **niet** thread‑veilig. Maak per thread een aparte `LoadOptions` (met zijn eigen `FontSettings`) aan, of bescherm de toegang met een lock.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **aspose font substitution** en **configure font settings** onder de knie te krijgen in een C#‑applicatie:

1. Installeer Aspose.Words en voeg de benodigde `using`‑statements toe.  
2. Maak een `LoadOptions`‑object met een nieuwe `FontSettings`.  
3. Koppel een aangepaste `IWarningCallback` om substitutie‑events zichtbaar te maken.  
4. Laad het document, waarbij de callback eventuele ontbrekende fonts rapporteert.  
5. (Optioneel) Breid het zoekpad uit of schakel substitutie volledig uit.

Gewapend met dit patroon kun je ontbrekende lettertypen loggen voor compliance, gebruikers waarschuwen in een UI, of automatisch fallback‑fonts insluiten vóór publicatie. Vervolgens kun je **Aspose.Words font substitution policies** verkennen of de workflow integreren in een grotere document‑verwerkings‑pipeline.

Veel programmeerplezier, en moge je documenten altijd weergeven met het juiste lettertype!  

---  

![Diagram dat Aspose.Words een document laadt, FontSettings aanroept, een waarschuwings‑callback triggert en substitutie‑informatie output geeft](image-placeholder.png "aspose font substitutie workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}