---
category: general
date: 2026-11-22
description: Leer hoe je een Forms2Ole‑besturingselement in Word invoegt met C#. Deze
  stapsgewijze gids behandelt DocumentBuilder, het plaatsen van een commandoknop en
  het opslaan van de .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: nl
lastmod: 2026-11-22
og_description: Voeg Forms2Ole‑besturingselement in Word toe met C#. Volg deze gids
  om een opdrachtknop toe te voegen met Aspose.Words en DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Forms2Ole‑besturingselement invoegen in Word met C# – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een Forms2Ole‑besturingselement in Word in te voegen met C# en Aspose.Words
url: /nl/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Forms2Ole‑besturingselement in Word in te voegen met C# en Aspose.Words

Als je **Forms2Ole‑besturingselement in Word** moet invoegen, laat deze tutorial precies zien hoe je dat doet met C#. Of je nu een invulbare sjabloon maakt of het maken van formulieren automatiseert, de onderstaande oplossing laat je een commandoknop programmatisch toevoegen.

Je leert hoe je een leeg document maakt, `DocumentBuilder` gebruikt om het element te plaatsen, en het resultaat opslaat als een `.docx`. De gids behandelt ook veelvoorkomende valkuilen, zoals coördinatensystemen en compatibiliteit met oudere Word‑versies.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
* Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)
* Een basisbegrip van C# en het Word‑objectmodel
* Een IDE zoals Visual Studio of VS Code

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuwe console‑applicatie en voeg het Aspose.Words‑pakket toe:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

Importeer in `Program.cs` de benodigde namespaces:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Pro tip:** Gebruik de nieuwste Aspose.Words‑versie voor volledige ondersteuning van de `Forms2OleControl`‑API.

## Stap 2: Een leeg document maken en DocumentBuilder initialiseren

De `Document`‑klasse vertegenwoordigt het Word‑bestand, terwijl `DocumentBuilder` methoden biedt om inhoud in te voegen.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` werkt als een cursor; na deze regel kun je overal in het document elementen gaan plaatsen.

## Stap 3: De positie en grootte van de knop definiëren

Word meet coördinaten in punten (1 pt ≈ 1/72 in). De `Rectangle`‑struct uit `System.Drawing` beschrijft de grenzen van het besturingselement.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` plaatst het element in de linkerbovenhoek van de huidige pagina.
* Pas `x` en `y` aan om de knop elders te positioneren (bijv. `new Rectangle(150, 200, 100, 30)`).

## Stap 4: Het Forms2Ole‑commandoknop invoegen

Gebruik nu `InsertForms2OleControl` om het element toe te voegen. De methode vereist het type besturingselement, een naam en de hierboven gedefinieerde grenzen.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Het geretourneerde `Forms2OleControl`‑object stelt je in staat eigenschappen zoals `Enabled`, `Visible` of later een macro‑naam aan te passen.

### Waarom Forms2Ole gebruiken?

* **Legacy‑compatibiliteit** – Forms2Ole‑besturingselementen werken in Word 97‑2003 (`.doc`) en nieuwere `.docx`‑bestanden.
* **Macro‑ondersteuning** – Ze kunnen VBA‑macros activeren, waardoor ze ideaal zijn voor interactieve sjablonen.
* **Precieze plaatsing** – In tegenstelling tot content‑controls bepaal je exacte coördinaten.

## Stap 5: Het document opslaan

Schrijf tenslotte het bestand naar schijf. Kies een map waarin je schrijfrechten hebt.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Open `output.docx` in Microsoft Word. Je ziet een knop met het label **ClickMe** in de linkerbovenhoek van de eerste pagina. Klikken op de knop in Word doet niets totdat je een macro toewijst, maar het besturingselement is volledig functioneel.

## Veelvoorkomende randgevallen afhandelen

| Situatie | Hoe aan te pakken |
|-----------|-------------------|
| **Knop verschijnt buiten de pagina** | Controleer of de `Rectangle`‑coördinaten binnen de paginamarges liggen. Gebruik `builder.PageSetup.PageWidth` en `PageHeight` om veilige grenzen te berekenen. |
| **Besturingselement niet zichtbaar in oudere Word‑versies** | Sla het document op als `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) om Forms2Ole‑compatibiliteit met Word 97‑2003 te garanderen. |
| **Bijschrift wijzigen** | Na invoegen, stel `commandButton.Caption = "Submit";` in. |
| **Een macro toewijzen** | Stel `commandButton.MacroName = "MyMacro"` in; de macro moet bestaan in het VBA‑project van het document. |
| **Meerdere knoppen** | Herhaal Stap 4 met verschillende `Rectangle`‑waarden en unieke namen. |

## Volledig, uitvoerbaar voorbeeld

Alles samengevoegd, hier is een zelfstandig programma dat je kunt kopiëren, plakken en uitvoeren:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwachte output:** Na het uitvoeren van het programma opent `output.docx` in Word met een klikbare knop gelabeld *Click Me!* gepositioneerd in de linkerbovenhoek van de eerste pagina.

## Conclusie

Je weet nu hoe je **Forms2Ole‑besturingselement in Word** kunt invoegen met C# en Aspose.Words. Het proces omvat het maken van een `Document`, het positioneren van een `Rectangle` en het aanroepen van `InsertForms2OleControl` via `DocumentBuilder`. Met het volledige code‑voorbeeld en de richtlijnen voor randgevallen kun je commandoknoppen integreren in elke geautomatiseerde Word‑workflow.

### Volgende stappen

* Verken andere `ControlType`‑waarden zoals `CheckBox` of `OptionButton`.
* Combineer Forms2Ole‑besturingselementen met VBA‑macros voor interactieve formulieren.
* Gebruik `DocumentBuilder.MoveTo` om knoppen op specifieke alinea’s of tabellen te plaatsen.
* Bekijk de **Forms2Ole**‑documentatie van Aspose.Words voor geavanceerde eigenschapsinstellingen.

Happy coding, en veel plezier met het bouwen van rijkere Word‑documenten met C# en Aspose.Words!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}