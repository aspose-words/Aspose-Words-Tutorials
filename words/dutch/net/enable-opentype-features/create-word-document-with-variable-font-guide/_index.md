---
category: general
date: 2026-03-19
description: Maak een Word‑document met Aspose.Words en een variabel lettertype. Leer
  hoe je het lettertypegewicht wijzigt, de letterbreedte instelt en de lettervariatie
  definieert in C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: nl
og_description: Maak een Word‑document met een variabel lettertype met Aspose.Words.
  Deze tutorial laat zien hoe u het lettertype laadt, de letterdikte wijzigt, de letterbreedte
  instelt en de lettervariatie definieert.
og_title: Maak Word-document met variabele lettertype – Complete gids
tags:
- Aspose.Words
- C#
- Variable Font
title: Maak Word-document met variabel lettertype – Gids
url: /nl/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document met variabel lettertype – Gids

Heb je ooit een **een Word-document maken** nodig gehad dat een modern variabel lettertype gebruikt, maar wist je niet waar te beginnen? Je bent niet alleen. In veel projecten—denk aan dynamische rapporten of merk‑consistentie brochures—maakt het kunnen **font weight wijzigen** in één keer een enorm verschil.  

In deze tutorial lopen we het volledige proces stap voor stap door: van het laden van een variabel lettertype in Aspose.Words, tot het instellen van de gewicht en breedte, en uiteindelijk het opslaan van een DOCX die er precies uitziet zoals jij hebt ontworpen. Geen vage verwijzingen, alleen concrete code die je direct in je C#-project kunt plakken.

## Wat je zult leren

- Hoe je **variabel lettertype laden** bestanden in Aspose.Words kunt gebruiken met `FontSettings`.
- De syntaxis voor **font variation definiëren** assen zoals `wght` (gewicht) en `wdth` (breedte).
- Manieren om **font width instellen** en **font weight wijzigen** op een enkele `Run`.
- Tips voor het oplossen van veelvoorkomende valkuilen (ontbrekende glyphs, onjuiste mappaden, enz.).
- Een volledig, uitvoerbaar voorbeeld dat je direct kunt kopiëren‑plakken en meteen kunt testen.

> **Prerequisites**: .NET 6+ (of .NET Framework 4.6+), Aspose.Words for .NET geïnstalleerd via NuGet, en een variabel‑lettertype bestand zoals *RobotoFlex.ttf* geplaatst in een lokale *Fonts* map.

---

## Stap 1 – Laad het variabele lettertype in Aspose.Words

Eerst moeten we Aspose.Words vertellen waar het onze aangepaste lettertypen kan vinden. De `FontSettings`‑klasse doet het zware werk.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Waarom dit belangrijk is**: Zonder de map te registreren, valt Aspose.Words terug op systeembrede lettertypen en negeert het alle OpenType-variatiedata die je later probeert toe te passen. Door te wijzen naar een specifieke directory zorg je ervoor dat *RobotoFlex* (of elk ander variabel lettertype) elke keer dat de code wordt uitgevoerd wordt gevonden.

> **Pro tip**: Stel de tweede parameter van `SetFontsFolder` in op `true` als je wilt dat Aspose ook sub‑mappen doorzoekt. Dit helpt wanneer je lettertypen organiseert op stijl of gewicht.

---

## Stap 2 – Maak een nieuw document en voeg voorbeeldtekst toe

Nu de lettertype‑engine weet waar hij moet zoeken, maken we een leeg `Document` aan en voegen we een alinea met een `Run` toe.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Wat gebeurt er**: `Run` vertegenwoordigt een aaneengesloten stuk tekst met uniforme opmaak. Door het eerst te maken, houden we de opmaaklogica geïsoleerd—perfect voor later het toepassen van verschillende variatie‑assen op afzonderlijke runs indien nodig.

---

## Stap 3 – Definieer de gewenste variatie‑assen (Weight & Width)

Variabele lettertypen bieden *assen* die je tijdens runtime kunt aanpassen. De twee meest voorkomende zijn `wght` (font weight) en `wdth` (font width). Aspose.Words modelleert dit met de `OpenTypeFontVariation`‑collectie.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Waarom deze getallen**: In de OpenType-specificatie varieert `wght` van het minimale tot maximale gewicht van het lettertype (vaak 100–900). Een waarde van **700** resulteert in een vette weergave. `wdth` werkt op dezelfde manier; **100** betekent de standaard (normale) breedte, terwijl waarden onder 100 de glyphs comprimeren.

> **Edge case**: Sommige variabele lettertypen ondersteunen een bepaalde as niet. Als je een niet‑ondersteunde tag opgeeft, negeert Aspose dit stilletjes. Controleer altijd de specificatie van het lettertype (meestal te vinden in de metadata van het `.ttf` of `.otf` bestand).

---

## Stap 4 – Pas de variatie toe op de Run met de lettertype‑naam

Nu koppelen we de variatiedata aan de daadwerkelijke tekst. De `FontInfo`‑klasse bevat de lettertype‑familienaam en de collectie van assen.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Uitleg**: Door `FontInfo` in te stellen, omzeilen we de gebruikelijke `Font.Name`‑eigenschap en geven we de engine een volledig gekwalificeerde lettertype‑configuratie. Dit is de enige manier om Aspose.Words te laten weten dat een variabel lettertype met aangepaste assen moet worden gebruikt.

> **Common mistake**: Vergeten de exacte familienaam in het lettertype‑bestand te gebruiken (`RobotoFlex` in dit voorbeeld). Een typefout zorgt ervoor dat Aspose terugvalt op een standaardlettertype, en gaat de variatie verloren.

---

## Stap 5 – Sla het document op en controleer het resultaat

Tot slot schrijf je het document naar schijf. De gegenereerde DOCX zal de variabele‑lettertype‑instructies bevatten, die Microsoft Word (2016+) correct kan weergeven.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Open het resulterende bestand in Word, selecteer de tekst en bekijk het **Font**‑dialoogvenster. Je zou *Roboto Flex* moeten zien staan, en de tekst zal vetter verschijnen dan de omliggende inhoud—precies wat onze `wght = 700` instelling vraagt.

> **Verification tip**: Als de tekst ongewijzigd lijkt, controleer dan nogmaals of het lettertype‑bestand echt de `wght`‑as ondersteunt. Sommige “variabele” lettertypen bieden alleen `ital` (italic) of `opsz` (optical size) aan.

---

## Optioneel: Voeg meer variatie toe – Breedte dynamisch wijzigen

Als je de *font width* anders wilt **instellen** voor een andere alinea, herhaal dan gewoon stappen 3‑4 met een nieuwe `OpenTypeFontVariation`‑collectie.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Nu heb je twee runs—een vet, een iets breder—die zowel **font weight wijzigen** als **font width instellen** in hetzelfde document demonstreren.

---

## Volledig werkend voorbeeld

Kopieer de onderstaande code in een nieuwe console‑app (`Program.cs`) en voer deze uit. Zorg ervoor dat de `Fonts`‑map `RobotoFlex.ttf` bevat (of elk ander variabel lettertype dat je verkiest).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Verwachte output**: Een `VariableFont.docx`‑bestand waarin de zin “Variable‑weight text” vetgedrukt verschijnt, dankzij de `wght = 700`‑as, terwijl de standaardbreedte behouden blijft.

---

## Veelgestelde vragen & randgevallen

| Question | Answer |
|----------|--------|
| *Wat als het lettertype niet wordt gevonden?* | Controleer het mappad, zorg ervoor dat de bestandsnaam overeenkomt, en dat het proces leesrechten heeft. Je kunt ook `fontSettings.GetFonts()` aanroepen om gedetecteerde lettertypen te tonen. |
| *Kan ik meerdere runs combineren met verschillende variaties?* | Zeker. Elke `Run` kan zijn eigen `FontInfo` hebben. Herhaal gewoon stappen 3‑4 voor elke run. |
| *Ondersteunen oudere versies van Word variabele lettertypen?* | Word 2016 (Build 16.0.8001) introduceerde basisondersteuning. Als je oudere versies target, valt het document terug op de dichtstbijzijnde statische versie van het lettertype. |
| *Is er een limiet aan hoeveel assen ik kan instellen?* | Je kunt zoveel assen instellen als het lettertype definieert. Veelvoorkomende tags zijn `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Het opgeven van een niet‑ondersteunde tag heeft simpelweg geen effect. |
| *Hoe debug ik ontbrekende glyphs?* | Gebruik `FontSettings.GetFontSources()` om geladen lettertypen te inspecteren, en `FontInfo.HasGlyph(char)` om individuele tekens te testen. |

---

## Conclusie

In een handvol stappen hebben we laten zien **hoe je Word-document** bestanden kunt maken die de kracht van variabele lettertypen benutten, waardoor je **font weight kunt wijzigen**, **font width kunt instellen**, **variabel lettertype** bestanden kunt **laden**, en **font variation**‑assen kunt **definiëren**—alles met Aspose.Words voor .NET.  

Het kernidee is eenvoudig: registreer de lettertype‑map, beschrijf de gewenste assen, koppel ze aan een `Run`, en sla op. Vanaf hier kun je de techniek uitbreiden naar volledige secties, tabellen, of zelfs programmatisch merk‑specifieke rapporten genereren.

**Volgende stappen**: probeer `RobotoFlex` te vervangen door een ander variabel lettertype, experimenteer met de `ital` (italic) as, of genereer een PDF‑versie van hetzelfde document met Aspose.PDF. Hetzelfde patroon geldt—laden, definiëren, toepassen, opslaan.

Veel plezier met coderen, en geniet van de flexibiliteit die variabele lettertypen bieden voor je Word‑automatiseringsprojecten!  

<img src="variable-font-demo.png" alt="Maak Word-document met variabel lettertype voorbeeld">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}