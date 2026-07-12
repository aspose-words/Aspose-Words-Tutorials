---
category: general
date: 2026-06-27
description: Lettertype stijl wijzigen in Word‑documenten met C#. Leer hoe je het
  lettertypegewicht, de vette weergave en de letterbreedte kunt aanpassen voor precieze
  typografie.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: nl
og_description: Verander het lettertype in Word‑documenten met C#. Ontdek hoe je het
  lettertypegewicht, het vetgewicht en de letterbreedte in een paar eenvoudige stappen
  kunt aanpassen.
og_title: Lettertype wijzigen in Word‑documenten – Complete C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Lettertype stijl wijzigen in Word-documenten – Complete C#-gids
url: /nl/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertype‑stijl wijzigen in Word‑documenten – Complete C#‑gids

Heb je ooit **lettertype‑stijl** moeten wijzigen in een Word‑bestand, maar wist je niet welke API‑aanroep dat precies doet? Je bent niet de enige—de meeste ontwikkelaars lopen tegen die muur aan wanneer ze voor het eerst typografie programmatisch willen aanpassen.  

Het goede nieuws is dat je met een paar regels C# **lettertype‑gewicht** kunt instellen, zelfs een vet gewicht kunt verhogen, en de breedte van elk glyph kunt afstemmen. In deze tutorial lopen we een volledig, uitvoerbaar voorbeeld door dat een `.docx`‑bestand van begin tot eind wijzigt.

## Wat deze gids behandelt

We beginnen met het laden van een bestaand document, daarna maken we een `FontSettings`‑object dat een `FontVariation` bevat. Vanaf daar **stellen we het lettertype‑gewicht in**, **stellen we het vet‑gewicht in**, en **passen we de lettertype‑breedte aan** voordat we de wijzigingen toepassen en het resultaat opslaan. Geen externe configuratiebestanden, geen magische strings—alleen pure C# en de Aspose.Words‑bibliotheek. Aan het einde kun je **lettertype in Word**‑documenten met vertrouwen wijzigen, of je nu een rapportage‑engine of een bulk‑opmaaktool bouwt.

### Vereisten

- .NET 6.0 of later (de code compileert ook op .NET Core)  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)  
- Een voorbeeld‑`input.docx` geplaatst in een map die je kunt refereren (we noemen het `YOUR_DIRECTORY`)  

Als je deze basis hebt, laten we dan beginnen.

---

## Stap 1: Lettertype‑stijl wijzigen – Laad het Word‑document

Het eerste wat je moet doen is het doelbestand in het geheugen laden. Beschouw dit als het openen van een leeg canvas waarop je later je nieuwe typografie gaat schilderen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Pro tip:** Als je dit op een server zonder UI uitvoert, zorg er dan voor dat de Aspose.Words‑licentie ofwel op proef staat of dat je een juiste licentiebestand hebt toegepast om watermerk‑meldingen te voorkomen.

---

## Stap 2: Lettertype‑gewicht instellen en Vet‑gewicht instellen

Nu het document in het geheugen staat, maken we een `FontSettings`‑container. Dit object is de toegangspoort tot elke lettertype‑aanpassing die je kunt doen.  

De `FontVariation`‑klasse laat je drie kernattributen specificeren:

| Eigenschap | Wat het doet | Typisch bereik |
|------------|--------------|----------------|
| `Weight`   | Regelt hoe zwaar het glyph eruitziet. Een waarde van **700** is de standaard “vet”. | 100‑900 |
| `Width`    | Rekken of vernauwt het glyph horizontaal. **100** betekent normale breedte. | 50‑200 |
| `Slant`    | Voegt een schuine, cursieve helling toe. Positieve getallen hellen naar rechts. | -90‑90 |

Hieronder **stellen we het lettertype‑gewicht** in op 700 (vet) en laten we ook zien hoe je het nog hoger kunt zetten als je lettertype een “extra‑vet” stijl ondersteunt.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Waarom dit belangrijk is:** Het direct instellen van **set bold weight** via `SetWeight` omzeilt de noodzaak van een apart “Bold”‑stijlobject, waardoor je pixel‑perfecte controle krijgt over hoe dik de strepen worden.

---

## Stap 3: Lettertype‑breedte aanpassen

Als je ooit een lettertype strakker wilt laten lijken voor een kop of ruimer voor een alinea, ben je blij dat je bij deze stap bent aangekomen. De eigenschap `Width` doet precies dat.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Veelvoorkomende valkuil:** Niet elk lettertype respecteert breedte‑variaties. Als je geen visuele verandering ziet, controleer dan of de gebruikte lettertype‑familie condensed/expanded glyphs ondersteunt.

---

## Stap 4: De lettertype‑instellingen toepassen – Lettertype in Word wijzigen

Met onze volledig geconfigureerde `FontSettings` is de laatste stap om het document te laten gebruiken. Dit is waar we **lettertype in Word** op documentniveau wijzigen, waardoor elke tekst‑run die de standaardstijl erft, wordt aangepast.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Wil je alleen een specifieke alinea of run targeten, dan kun je dat node ophalen en zijn `FontSettings` afzonderlijk instellen. Het bovenstaande voorbeeld toont de brede aanpak, perfect voor bulk‑opmaakscenario’s.

---

## Stap 5: Opslaan en de wijzigingen verifiëren

Opslaan is het laatste, maar zeker niet het minste, onderdeel van de workflow. Na het persisteren van het bestand kun je het openen in Microsoft Word om de nieuwe styling in actie te zien.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Verwacht resultaat

- Alle body‑tekst die voorheen het standaardlettertype gebruikte, verschijnt nu **vet** (gewicht 700).  
- Als je `SetWidth(80)` hebt uitgeprobeerd, zien de tekens er iets strakker uit; `SetWidth(120)` spreidt ze uit.  
- Geen andere inhoud (afbeeldingen, tabellen, enz.) wordt aangepast—alleen de lettertype‑kenmerken van tekst‑runs.

Open `output.docx` in Word, selecteer een alinea, en controleer het **Lettertype**‑dialoogvenster. Je ziet dat het **Vet**‑vakje aangevinkt is en dat de **Schaal** (breedte) de door jou gekozen waarde weergeeft.

---

## Veelgestelde vragen & randgevallen

### Kan ik tegelijk het lettertype‑familie wijzigen?

Zeker. Nadat je de `FontVariation` hebt ingesteld, kun je ook een nieuwe `FontInfo` toewijzen aan de `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Wat als ik **set bold weight** alleen voor koppen wil instellen?

Haal het node van de kopstijl op en pas een aparte `FontSettings`‑instantie toe:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Werkt dit met .NET Core op Linux?

Ja—Aspose.Words is cross‑platform. Zorg er alleen voor dat je de juiste runtime‑bibliotheken geïnstalleerd hebt (`libgdiplus` op sommige distributies) als je later het document naar PDF wilt renderen.

---

## Conclusie

We hebben zojuist **lettertype‑stijl** in een Word‑document van begin tot eind **gewijzigd**, waarbij we hebben laten zien hoe je **lettertype‑gewicht**, **vet‑gewicht** en **lettertype‑breedte** instelt met C#. Het volledige, uitvoerbare voorbeeld toont elke benodigde import, objectcreatie en methode‑aanroep, zodat je het kunt kopiëren‑plakken in je eigen project en de typografie direct ziet transformeren.

Nu je weet hoe je **lettertype in Word** kunt **wijzigen**, kun je gerelateerde onderwerpen verkennen zoals **aangepaste lettertypen insluiten**, **kleurgradaties toepassen**, of **dynamische tabellen maken**. Elk van die onderwerpen bouwt voort op dezelfde `FontSettings`‑basis die we hier hebben gebruikt, dus je bent al een stap voor.

Heb je een scenario dat hier niet wordt behandeld? Laat een reactie achter, en we duiken er samen in. Veel programmeerplezier—en moge je documenten er altijd precies uitzien zoals jij wilt!  

![voorbeeld van lettertype stijl wijzigen](placeholder.png){alt="voorbeeld van lettertype stijl wijzigen"}

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Lettertype nadruk markering instellen](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Lettertype fallback instellingen instellen](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Lettertype opmaak instellen](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}