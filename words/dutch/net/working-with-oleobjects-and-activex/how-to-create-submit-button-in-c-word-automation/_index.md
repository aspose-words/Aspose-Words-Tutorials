---
category: general
date: 2026-08-23
description: Maak een verzendknop in C# Word‑automatisering. Leer een ActiveX‑knop
  toe te voegen, de knopnaam, het bijschrift en de tekst programmatically in te stellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: nl
lastmod: 2026-08-23
og_description: Maak een verzendknop in C# Word‑automatisering. Deze gids laat zien
  hoe je een ActiveX‑knop toevoegt, de naam, het bijschrift en de tekst instelt met
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Maak een verzendknop in C# Word‑automatisering
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Hoe maak je een verzendknop in C# Word‑automatisering
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een submit‑knop te maken in C# Word‑automatisering

Als je een **submit‑knop** wilt **maken** binnen een Word‑document met C#, leidt deze gids je door het volledige proces. Je ziet hoe je een ActiveX‑knop toevoegt, een programmatische naam toewijst en de knop‑bijschrift instelt zodat het eruitziet als een gewone *Submit*‑besturingselement.

Het automatiseren van formulierbesturingselementen in Word kan handmatig lay‑outwerk vervangen en zorgt voor consistentie over honderden documenten. In de onderstaande stappen leer je ook hoe je **knop‑tekst instelt**, **knop‑naam instelt** en **knop‑bijschrift instelt** — allemaal essentieel wanneer de knop deelneemt aan een macro‑gedreven workflow.

## Voorvereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 (of later) geïnstalleerd.
* Een referentie naar **Aspose.Words for .NET** (de bibliotheek die `DocumentBuilder.InsertForms2OleControl` biedt).
* Basiskennis van C# en de ActiveX‑formulierelementen van Word.

Je kunt Aspose.Words installeren via NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gebruik de nieuwste stabiele versie van Aspose.Words om te profiteren van bug‑fixes en nieuwe functies met betrekking tot ActiveX‑besturingselementen.

## Overzicht van de oplossing

De tutorial is georganiseerd in drie duidelijke stappen:

1. **ActiveX‑knop toevoegen** – gebruik de `InsertForms2OleControl`‑methode om een commandoknop in het document te plaatsen.  
2. **Knop‑naam instellen** – wijs een unieke programmatische identifier toe met de `Name`‑eigenschap.  
3. **Knop‑bijschrift instellen** – definieer de zichtbare tekst op de knop via de `Caption`‑eigenschap (die ook de **set button text** regelt die je in de UI ziet).

Aan het einde van de gids heb je een volledig functionele **create submit button**‑routine die je in elk Word‑automatiseringsproject kunt hergebruiken.

## Stap 1: Een ActiveX‑knop aan het document toevoegen

De eerste taak is om een **activex button** toe te voegen aan het Word‑bestand. Aspose.Words stelt de `Forms2OleControlType.CommandButton`‑enum hiervoor beschikbaar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Waarom deze stap belangrijk is:**  
ActiveX‑besturingselementen zijn de enige Word‑formelementen die VBA‑macro's kunnen uitvoeren of met externe code kunnen communiceren. Het toevoegen van het element creëert een tijdelijke aanduiding die later kan worden geconfigureerd.

> **Edge case:** Als het document al een besturingselement met dezelfde naam bevat, zal Word de nieuwe automatisch een andere naam geven (bijv. `CommandButton1`). De naam expliciet instellen in de volgende stap voorkomt dergelijke conflicten.

## Stap 2: De knop‑naam instellen

Een betrouwbare **set button name** is cruciaal wanneer je het element moet aanspreken vanuit VBA of vanuit andere delen van je C#‑code. De `Name`‑eigenschap geeft de knop een programmatische identifier.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Waarom je een naam moet instellen:**  
Wanneer het document wordt geopend, kan VBA de knop ophalen via `ActiveDocument.InlineShapes("btnSubmit")`. Een betekenisvolle naam zoals `btnSubmit` verduidelijkt bovendien de intentie wanneer je de XML van het document inspecteert.

> **Pro tip:** Houd namen kort, alfanumeriek en begin met een letter om compatibel te blijven met de VBA‑naamgevingsregels.

## Stap 3: Het knop‑bijschrift (zichtbare tekst) instellen

De tekst die gebruikers op de knop zien, wordt geregeld door de **set button caption**‑eigenschap. In de Word‑UI verschijnt dit als het label van de knop, wat ook de **set button text** is die je wilt weergeven.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Waarom het bijschrift belangrijk is:**  
Het bijschrift is het gebruikersgerichte label. Later wijzigen heeft geen invloed op de naam van de knop, zodat je de UI kunt lokaliseren zonder code die afhankelijk is van `btnSubmit` te breken.

> **Veelgestelde vraag:** *Kan ik zowel Caption als Value instellen?*  
> Voor een `CommandButton` regelt `Caption` het label, terwijl `Value` niet wordt gebruikt. Als je een verborgen waarde nodig hebt, sla die dan op in een aangepaste document‑eigenschap.

## Volledig werkend voorbeeld

De drie stappen samenvoegen levert een complete routine op die je in elke console‑ of Windows‑applicatie kunt plaatsen:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Verwachte output

Het uitvoeren van het programma maakt `SubmitButton.docx`. Wanneer je het bestand opent in Microsoft Word:

* Er verschijnt een **Submit**‑knop op de opgegeven locatie.
* De naam van de knop is `btnSubmit` (controleer via *Developer → Design Mode → Properties*).
* Klikken op de knop in ontwerpmode toont het bijschrift *Submit*.

Je hebt nu een herbruikbaar bouwblok voor elke formulier‑gedreven Word‑oplossing.

## Aanvullende overwegingen

### Omgaan met naamconflicten

Als je de routine meerdere keren op hetzelfde document uitvoert, kan Word dubbele besturingselementen automatisch hernoemen. Om uniekheid te garanderen, kun je een GUID voorvoegen:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Het knop‑bijschrift lokaliseren

Voor meertalige documenten kun je bijschriften opslaan in een resource‑bestand en ze tijdens runtime toewijzen:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Reageren op een klik op de knop

De knop zelf bevat geen kliklogica in C#. Meestal koppel je een VBA‑macro:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Omdat je **set button name** hebt ingesteld op `btnSubmit`, volgt de macro‑naam automatisch de `<Name>_Click`‑conventie.

## Veelgestelde vragen (FAQ)

| Vraag | Antwoord |
|-------|----------|
| **Waarom verschijnt de knop leeg?** | Zorg ervoor dat je de `Caption`‑eigenschap instelt; zonder deze toont de knop geen tekst. |
| **Kan ik een ander ActiveX‑element gebruiken?** | Ja. Vervang `Forms2OleControlType.CommandButton` door `CheckBox`, `OptionButton`, enz., maar de eigenschappen verschillen. |
| **Is dit compatibel met .NET Core?** | Aspose.Words for .NET ondersteunt .NET 6+, dus dezelfde code werkt op .NET Core en .NET Framework. |
| **Wat als het document al een knop bevat?** | Gebruik een unieke `Name` (bijv. een GUID toevoegen) om conflicten te vermijden. |

## Conclusie

Je weet nu hoe je **create submit button** programmatically in een Word‑document kunt maken met C#. Door de drie stappen te volgen — **add activex button**, **set button name** en **set button caption** — kun je betrouwbaar **set button text**, **set button name** en **set button caption** toepassen voor elke geautomatiseerde formulieroplossing.

Vanuit hier kun je verder gaan met:

* Het toevoegen van VBA‑macro's die reageren op de **submit button**‑klik.
* Het stijlen van de knop met aangepaste lettertypen of kleuren via de onderliggende XML.
* Het genereren van meerdere knoppen in een lus voor dynamische formulieren.

Voel je vrij om te experimenteren met verschillende bijschriften, namen en posities om aan jouw specifieke workflow te voldoen. Veel plezier met automatiseren!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}