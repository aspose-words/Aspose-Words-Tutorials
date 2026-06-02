---
category: general
date: 2026-06-02
description: Leer hoe je een variabel gewicht‑lettertype gebruikt in C# en het lettertypegewicht
  via code instelt, terwijl je de code voor lettertype‑uitrekking aanpast voor dynamische
  typografie.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: nl
og_description: Gebruik een variabele gewichtlettertype in C# om het lettertypegewicht
  programmatisch in te stellen en de lettertype‑stretchcode te wijzigen, waardoor
  dynamische typografie in uw documenten mogelijk wordt.
og_title: Gebruik variabele gewichtlettertype in C# – Volledige gids
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Gebruik variabele gewichtlettertype in C# – Complete programmeergids
url: /nl/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Variabel gewichtlettertype gebruiken in C# – Complete programmeergids

Heb je ooit **variabel gewichtlettertype** moeten gebruiken in een .NET‑project, maar wist je niet hoe je het gewicht en de stretch kunt laten reageren op gebruikersinvoer? Je bent niet de enige. In veel UI‑ of rapportagescenario's wil je dat de tekst zich aanpast—misschien een lichte kop die vet wordt bij hover, of een alinea die zijn breedte vergroot voor nadruk. Het goede nieuws is dat je met Aspose.Words **font weight programmatically kunt instellen** en zelfs **font stretch code kunt wijzigen** terwijl je werkt.

In deze tutorial lopen we een hands‑on voorbeeld door dat precies laat zien hoe je een variabel‑gewichtlettertype laadt, een aangepast gewicht toepast en de stretch‑instelling bijstelt—alles met duidelijke C#‑code die je kunt copy‑paste. Aan het einde heb je een uitvoerbare console‑app die een PDF genereert waarin het effect wordt getoond.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (v23.12 of later). De bibliotheek wordt geleverd met volledige ondersteuning voor variabele‑gewichtlettertypen.
- Een map die minstens één variabel‑gewichtlettertype‑bestand bevat, bijv. *RobotoFlex‑Variable.ttf*. Je kunt het downloaden van Google Fonts.
- .NET 6 SDK (of een recente .NET‑versie) en een IDE naar keuze.
- Basiskennis van C# — niets ingewikkelds, slechts een paar regels code.

Dat is alles. Geen extra NuGet‑pakketten naast Aspose.Words, en geen obscure configuratiebestanden.

![Voorbeeld van variabel gewichtlettertype](https://example.com/variable-weight-sample.png "Demonstratie van variabel gewichtlettertype")

*Alt‑tekst: screenshot die het gebruik van een variabel gewichtlettertype toont in een gegenereerd PDF‑document.*

---

## Stap 1: FontSettings configureren en naar je lettertype‑map wijzen  

First things first—Aspose.Words moet weten waar je variabele‑gewichtlettertypen zich bevinden. Dit doe je door een `FontSettings`‑object te maken en een `FolderFontSource` eraan toe te voegen. De `true`‑vlag vertelt de engine om ook sub‑mappen te doorzoeken, wat handig is als je meerdere lettertypefamilies samenhoudt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Waarom dit belangrijk is:** Zonder het registreren van de map valt Aspose.Words terug op systeemlettertypen en negeert de variabele‑gewichtdata die in je aangepaste lettertypebestand is ingebed. Deze stap vormt de basis voor alles wat volgt.

---

## Stap 2: FontSettings aan het document koppelen  

Nu maken we een nieuw `Document` (of laden een bestaand) en vertellen we het om de `FontSettings` te gebruiken die we zojuist hebben voorbereid. Deze binding zorgt ervoor dat de variabele‑gewichtdata beschikbaar is voor elke `Run` die later wordt toegevoegd.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Als je al een sjabloon hebt—bijvoorbeeld een Word‑bestand met placeholders—kun je `new Document()` vervangen door `new Document("Template.docx")`. Dezelfde `FontSettings` worden dan toegepast.

---

## Stap 3: Een Run‑tekst toevoegen die het variabele‑gewichtlettertype gebruikt  

Een **Run** is de kleinste eenheid van tekstopmaak in Aspose.Words. We maken er één, voegen die in een nieuwe alinea in, en passen later de lettertype‑attributen aan.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Op dit moment wordt de tekst gerenderd met het standaardlettertype (meestal Times New Roman). De magie gebeurt zodra we de variabele‑gewichtfamilie toewijzen.

---

## Stap 4: Kies de variabele‑gewichtlettertype‑familie  

Hier komt het moment waarop we daadwerkelijk **variabel gewichtlettertype** gebruiken. Stel `Font.Name` in op de exacte familienaam die in het variabele lettertypebestand is gedefinieerd. Voor Roboto Flex is de naam `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Als je niet zeker bent van de familienaam, open dan het `.ttf`‑bestand in een lettertype‑viewer of gebruik de methode `fontSettings.GetFonts()` om de beschikbare families op te sommen.

---

## Stap 5: Fontgewicht en stretch programmatically instellen  

Nu de kern van de tutorial: we **stellen font weight programmatically in** en **wijzigen font stretch code**. Beide eigenschappen accepteren gehele getallen die overeenkomen met de OpenType‑specificatie.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Dun) → 900 (Zwart). Kies een willekeurige waarde die het variabele lettertype ondersteunt.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Standaard is 100 (Normaal).

> **Pro tip:** Niet elk variabel lettertype biedt het volledige bereik. Als je een waarde instelt die niet wordt ondersteund, zal de engine deze afkappen naar het dichtstbijzijnde beschikbare gewicht of stretch.

---

## Stap 6: Het document opslaan en het resultaat verifiëren  

Tot slot schrijven we het document weg naar PDF (of DOCX) en openen we het om het effect te zien. PDF is een uitstekend formaat voor visuele verificatie omdat de weergave consistent is over verschillende platformen.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Wanneer je *VariableWeightDemo.pdf* opent, zou je de zin “Variable‑weight text demo” moeten zien gerenderd in een lichte, licht uitgerekte versie van Roboto Flex. Verander `FontWeight` naar `700` en `FontStretch` naar `80` en voer opnieuw uit—let op hoe de tekst vet en compacter wordt.

---

## Veelgestelde vragen & randgevallen  

### Wat als het lettertype helemaal niet verschijnt?  

- **Missing FontSettings**: Controleer dubbel dat `doc.FontSettings = fontSettings;` wordt uitgevoerd **voordat** er tekst wordt toegevoegd.  
- **Incorrect family name**: Gebruik `fontSettings.GetFonts()` om alle ontdekte families te tonen; kopieer de exacte tekenreeks.  
- **Unsupported weight/stretch**: Sommige variabele lettertypen ondersteunen slechts een deel van het 100‑900‑gewichtbereik. Gebruik `run.Font.FontWeight = 400;` als veilige fallback.

### Kan ik het gewicht wijzigen nadat het document is opgeslagen?  

Ja. Het `Run`‑object is mutabel, dus je kunt `FontWeight` of `FontStretch` op elk moment vóór de definitieve `Save` aanpassen. Als je gewichten dynamisch wilt schakelen (bijv. op basis van gebruikersinteractie), overweeg dan om afzonderlijke runs voor elke staat te genereren.

### Werkt dit met DOCX‑output?  

Absoluut. De variabele‑gewichtmetadata wordt opgeslagen in de onderliggende OpenXML, en moderne versies van Word kunnen deze interpreteren. Oudere Word‑versies kunnen echter de stretch‑instelling negeren.

---

## Volledig werkend voorbeeld  

Hieronder staat een compleet console‑programma dat je direct kunt compileren en uitvoeren. Het bevat alle benodigde `using`‑directieven, foutafhandeling en commentaar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Verwachte output:** De console drukt het opslagpad af, en de gegenereerde PDF toont de tekst in een lichte, uitgerekte stijl—precies zoals we hebben geconfigureerd.

---

## Samenvatting  

We hebben behandeld hoe je **variabel gewichtlettertype** kunt gebruiken in C# met Aspose.Words, laten zien hoe je **font weight programmatically kunt instellen**, en je de exacte **change font stretch code** getoond die nodig is om de glyphs uit te breiden of samen te drukken. De stappen zijn eenvoudig: configureer `FontSettings`, koppel ze aan een `Document`, maak een `Run`, kies de variabele‑gewichtfamilie, en pas tenslotte `FontWeight` en `FontStretch` aan.

---

## Wat is het volgende?  

- **[Lettertype gebruiken van doelmachine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)**  
- **[Lettertype gebruiken van doelmachine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)**  
- **[Lettertype gebruiken van doelmachine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}