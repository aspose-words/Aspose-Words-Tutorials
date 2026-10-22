---
category: general
date: 2026-09-21
description: Leer hoe u een ActiveX‑opdrachtknop in een Word‑document maakt met Aspose.Words
  en C#. Een stapsgewijze gids behandelt het invoegen, positioneren en opslaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: nl
lastmod: 2026-09-21
og_description: Maak een ActiveX-opdrachtknop in een Word‑document met C# en Aspose.Words.
  Volg deze volledige tutorial om de knop programmatisch in te voegen, te positioneren
  en op te slaan.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Maak een ActiveX‑opdrachtknop in Word met C# – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Hoe maak je een ActiveX‑opdrachtknop in Word met C#
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een ActiveX command button in Word te maken met C#

Als je een **ActiveX command button** in een Word‑bestand moet **maken**, laat deze gids je de exacte stappen zien. Met Aspose.Words for .NET kun je de knop volledig vanuit C#‑code toevoegen, positioneren en configureren.

Programma‑matig invoegen van een ActiveX‑knop elimineert handmatig UI‑werk en maakt geautomatiseerde documentgeneratie mogelijk voor formulieren, rapporten of interactieve sjablonen. In deze tutorial leer je hoe je **DocumentBuilder**, de **InsertForms2OleControl**‑methode en gerelateerde eigenschappen gebruikt om een volledig functionele knop te realiseren.

## Wat je nodig hebt

* .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.7+)
* Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)
* Een IDE zoals Visual Studio 2022 of VS Code
* Basiskennis van C# en Word‑documentconcepten

Er is geen extra Office‑installatie vereist omdat Aspose.Words onafhankelijk van Microsoft Word werkt.

## Stap 1: Het C#‑project opzetten

Maak een nieuw console‑project aan en voeg het Aspose.Words‑pakket toe.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

De `Aspose.Words`‑bibliotheek levert de **DocumentBuilder**‑klasse die we zullen gebruiken om het document te manipuleren.

## Stap 2: Het document en de builder initialiseren

Het eerste code‑blok maakt een leeg document en een `DocumentBuilder`‑instantie aan. Dit object is het toegangspunt voor alle Word‑verwerkingsbewerkingen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:** `DocumentBuilder` houdt de huidige cursorpositie bij, zodat elke daaropvolgende invoeging precies verschijnt op de plaats waar je de cursor zet.

## Stap 3: De ActiveX command button invoegen

De **InsertForms2OleControl**‑methode maakt een ActiveX‑besturingselement van het opgegeven type. Hier vragen we een `CommandButton` aan en geven we de grootte op in punten (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Uitleg:**  
* `OleControlType.CommandButton` vertelt Aspose.Words om een knop te maken in plaats van een ander besturingselementtype.  
* De methode retourneert een `Forms2OleControl`‑object, dat positionerings‑ en eigenschapsvelden blootlegt.

## Stap 4: De knop positioneren en zijn eigenschappen instellen

Na het invoegen kun je de knop naar elke locatie op de pagina verplaatsen en een programmatische naam en zichtbare bijschrift geven.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Pro‑tip:** Het coördinatensysteem begint in de linkerbovenhoek van de pagina. Pas `Left` en `Top` aan om de knop uit te lijnen met andere formuliervelden.

## Stap 5: Het document opslaan

Schrijf tenslotte het document naar schijf. Het bestand zal de ActiveX‑knop bevatten, klaar om te worden geopend in Microsoft Word waar de knop interactief wordt.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Wanneer je `ActiveXCommandButton.docx` in Word opent, zie je een knop met het label **Submit** op de opgegeven locatie. Klikken erop in Word zal het standaardgedrag van de command‑button activeren (dat je later kunt aanpassen met VBA of Word‑add‑ins).

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samenvoegen levert een zelfstandige applicatie op die je kunt kopiëren, plakken en uitvoeren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Verwachte output:** De console print *“Document created successfully.”* en de map bevat nu `ActiveXCommandButton.docx`. Het openen van het bestand in Microsoft Word toont een klikbare **Submit**‑knop, geplaatst 100 pt vanaf de linkermarge en 150 pt vanaf de bovenkant van de pagina.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| De knop verschijnt buiten de pagina | `Left`/`Top`‑waarden overschrijden de paginadimensies | Gebruik `doc.FirstSection.PageSetup.PageWidth` en `PageHeight` om veilige coördinaten te berekenen |
| Knop is niet zichtbaar in Word | Het document is opgeslagen in een formaat dat ActiveX‑besturingselementen verwijdert (bijv. `.txt`) | Altijd opslaan als `.docx` of `.doc` |
| Runtime‑fout `ArgumentOutOfRangeException` | Breedte of hoogte is ingesteld op nul of een negatieve waarde | Zorg ervoor dat de grootte‑argumenten die aan `InsertForms2OleControl` worden doorgegeven positieve getallen zijn |

## De oplossing uitbreiden

Je kunt de knop verder aanpassen door extra eigenschappen in te stellen, zoals `Enabled`, `Visible`, of door een macro via VBA toe te voegen. De **Forms2OleControl**‑klasse stelt je ook in staat om andere ActiveX‑besturingselementen in te voegen, zoals selectievakjes (`OleControlType.CheckBox`) of keuzelijsten (`OleControlType.ComboBox`).

Als je meerdere knoppen in een lus moet genereren, kapsel je de invoeglogica in een hulpmethode:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusie

Je weet nu hoe je een **ActiveX command button** in een Word‑document kunt **maken** met C# en Aspose.Words. De tutorial behandelde het opzetten van het project, het invoegen van de knop met `InsertForms2OleControl`, het positioneren ervan en het opslaan van het uiteindelijke bestand. Met deze basis kun je complexe formulieren automatiseren, interactieve besturingselementen insluiten en Word‑documenten integreren in grotere .NET‑oplossingen.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **Aspose.Words ActiveX**‑formuliervelden, **C# DocumentBuilder**‑geavanceerde opmaak, of het programmeermatig toevoegen van **ActiveX control in Word** voor selectievakjes en vervolgkeuzelijsten. Experimenteer met verschillende coördinaten en afmetingen om aan je specifieke lay-outvereisten te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een Word‑document met Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Maak een rechthoekige vorm in Word met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Maak een Word‑document met tabel met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}