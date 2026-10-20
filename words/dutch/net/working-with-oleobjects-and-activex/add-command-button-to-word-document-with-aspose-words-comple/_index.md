---
category: general
date: 2026-07-29
description: Voeg een opdrachtknop toe aan een Word‑document met Aspose.Words. Leer
  hoe u de eigenschappen van een ActiveX‑besturingselement instelt en de bijschrift
  van de opdrachtknop instelt in een paar eenvoudige stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: nl
lastmod: 2026-07-29
og_description: Voeg een opdrachtknop toe aan een Word‑document met Aspose.Words.
  Deze tutorial laat zien hoe je de eigenschappen van een ActiveX‑besturingselement
  instelt en snel de bijschrift van de opdrachtknop instelt.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Voeg opdrachtknop toe aan Word‑document – Aspose.Words stap voor stap
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Voeg een opdrachtknop toe aan een Word‑document met Aspose.Words – Complete
  gids
url: /nl/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Commandknop toevoegen aan Word-document – Complete programmeerhandleiding

Heb je ooit moeten **add command button to word document** maar wist je niet welke API‑aanroepen je moet gebruiken? Je bent niet de enige; veel ontwikkelaars lopen tegen die muur aan wanneer ze voor het eerst interactieve besturingselementen in een DOCX‑bestand willen insluiten. Het goede nieuws is dat Aspose.Words het verrassend eenvoudig maakt. In deze gids lopen we door het maken van een CommandButton ActiveX‑control, **set activex control properties**, en **set command button caption**—alles met nette C#‑code die je direct kunt kopiëren en plakken.

Aan het einde van deze tutorial heb je een volledig functioneel Word‑bestand dat een klikbare “Submit”‑knop bevat, klaar om te worden geopend in Microsoft Word. Geen externe VBA‑scripts, geen handmatig UI‑geklungel—alleen pure programmatic control.

## Wat je zult leren

* Hoe je een leeg Word‑document en een `DocumentBuilder` maakt.
* De exacte methode‑aanroep om **add command button to word document** te gebruiken met Aspose.Words.
* Manieren om **set activex control properties** in te stellen, zoals grootte, positie en naam.
* De juiste techniek om **set command button caption** in te stellen zodat de knop precies weergeeft wat je wilt.
* Tips voor het omgaan met randgevallen zoals verschillende knop‑types, DPI‑schaling en compatibiliteit met Word‑versies.

> **Voorvereiste:** Visual Studio (of een andere C#‑IDE) met Aspose.Words voor .NET geïnstalleerd (NuGet‑pakket `Aspose.Words`). Geen eerdere ActiveX‑ervaring vereist.

---

## Stap 1: Het project instellen en namespaces importeren

Voordat we **add command button to word document** kunnen uitvoeren, hebben we een C#‑project nodig dat naar Aspose.Words verwijst. Maak een nieuwe .NET console‑applicatie aan en voeg vervolgens het NuGet‑pakket toe:

```bash
dotnet add package Aspose.Words
```

Breng nu de vereiste namespaces in je bronbestand:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Deze drie `using`‑directieven geven je toegang tot de `Document`, `DocumentBuilder` en de `Forms2OleControl`‑klassen die de ActiveX‑invoeging mogelijk maken.

*Pro tip:* Als je Visual Studio gebruikt, zal de IDE voorstellen deze automatisch toe te voegen wanneer je de klassennamen typt.

## Stap 2: Een leeg document en een builder maken

Een nieuw `Document`‑object vertegenwoordigt een leeg Word‑bestand. De `DocumentBuilder` is ons handige “pen” waarmee we kunnen tekenen, tekst invoegen en — cruciaal — ActiveX‑besturingselementen plaatsen.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Op dit punt is het document slechts een leeg canvas — zie het als een schoon vel papier dat wacht op jouw command button.

## Stap 3: Het CommandButton ActiveX‑control invoegen

Nu voegen we eindelijk **add command button to word document** toe. Aspose.Words biedt de `InsertForms2OleControl`‑methode, die het control‑type en de afmetingen accepteert. We gebruiken `Forms2OleControlType.CommandButton` en geven het een comfortabele breedte van 150 punten en een hoogte van 30 punten.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

De methode retourneert een `Forms2OleControl`‑instantie, die we in de volgende stap zullen gebruiken om **set activex control properties** toe te passen.

## Stap 4: Het control configureren – Naam, bijschrift en positie

### Het bijschrift instellen

Het bijschrift is de tekst die op de knop zelf verschijnt. Om **set command button caption** uit te voeren, wijs je simpelweg een string toe aan de `Caption`‑property:

```csharp
commandButton.Caption = "Submit";
```

Je kunt `"Submit"` naar alles wijzigen — “Save”, “Export”, “Launch”, enz. — en Word zal die exacte tekst weergeven.

### Het control een naam geven

Het geven van een betekenisvolle naam aan het control maakt het later makkelijker om ernaar te verwijzen (bijvoorbeeld bij het automatiseren van Word‑macro's). We stellen de `Name`‑property in:

```csharp
commandButton.Name = "btnSubmit";
```

### Positioneren op de pagina

Word gebruikt punten (1/72 van een inch) voor de lay-out. Pas de `Left`‑ en `Top`‑properties aan om de knop te plaatsen waar je hem nodig hebt:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Als je de knop ten opzichte van een alinea wilt uitlijnen, kun je eerst de cursor van de builder verplaatsen en vervolgens het control invoegen; de coördinaten zijn dan relatief ten opzichte van die locatie.

*Randgeval:* Op monitoren met een hoge DPI kan de visuele grootte in Word iets anders lijken. Om de fysieke grootte van de knop consistent te houden over apparaten, kun je de punten berekenen op basis van de doel‑DPI (normaal 96 DPI voor Word).

## Stap 5: Het document opslaan

Met de knop volledig geconfigureerd, is het opslaan van het bestand een één‑regelige opdracht:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Het resulterende `CommandButton.docx` bevat een volledig functionele ActiveX‑knop. Open het in Microsoft Word, en je ziet een “Submit”‑knop precies op de positie die je hebt opgegeven.

### Verwacht resultaat

1. Het Word‑document opent met één enkele pagina.
2. Een rechthoekige knop met het label **Submit** verschijnt op de opgegeven coördinaten.
3. Als je met de rechtermuisknop op de knop klikt en **Properties** kiest, zie je de naam `btnSubmit` en andere door jou ingestelde eigenschappen.

## Stap 6: Geavanceerde variaties en veelvoorkomende valkuilen

### Andere ActiveX‑types invoegen

De `InsertForms2OleControl`‑methode is niet beperkt tot command buttons. Je kunt selectievakjes, keuzerondjes of zelfs aangepaste ActiveX‑objecten insluiten:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Hetzelfde **set activex control properties**‑patroon is van toepassing — vervang gewoon de type‑enum.

### Omgaan met Word‑versies

Oudere Word‑versies (vóór 2007) gebruiken het binaire `.doc`‑formaat, dat ActiveX‑controls anders opslaat. Aspose.Words converteert het control automatisch wanneer je opslaat als `.doc`, maar sommige eigenschappen (zoals precieze positionering) kunnen verschuiven. Als je legacy‑formaten target, test dan de output in de specifieke Word‑versie die je nodig hebt.

### Beveiligingsinstellingen

Word kan ActiveX‑controls uitschakelen op machines met strikte macro‑beveiliging. Om een “Security Warning”‑dialoog te vermijden, overweeg:

* Het document ondertekenen met een vertrouwd certificaat.
* Gebruikers instrueren om ActiveX‑inhoud in te schakelen voor die bestandslocatie.
* Een macro‑vrije alternatief gebruiken (bijv. gewone content‑controls) als beveiliging een zorg is.

## Stap 7: Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar te‑runnen programma dat elke stap die we hebben besproken bevat. Kopieer het naar je `Program.cs`, pas het uitvoerpad indien nodig aan, en klik op **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Wat deze code doet:**

* Begint met een nieuw document.
* Voegt een command button toe, **sets activex control properties**, en **sets command button caption**.
* Voegt een korte verklarende alinea toe.
* Slaat het bestand op als `CommandButton.docx`.

Voer het programma uit, open het gegenereerde bestand, en je zult de knop onder de verklarende tekst zien staan.

## Conclusie

We hebben zojuist laten zien hoe je **add command button to word document** kunt gebruiken met Aspose.Words, hoe je **set activex control properties** kunt toepassen, en hoe je **set command button caption** kunt instellen — allemaal in een beknopte, productie‑klare C#‑snippet. De aanpak schaalt: verwissel het control‑type, pas de afmetingen aan, of loop over een gegevensbron om tientallen knoppen automatisch in te voegen.

Wil je verder gaan? Probeer:

* De knop koppelen aan een macro die een data‑export triggert.
* Afbeeldingen of aangepaste iconen toevoegen binnen de knop via de `Picture`‑property.
* Een volledig formulier bouwen met meerdere ActiveX‑controls (tekstvakken, keuzelijsten, enz.).

Experimenteren is de beste manier om Word‑automatisering onder de knie te krijgen. Als je tegen een probleem aanloopt, controleer dan je DPI‑berekeningen en Word‑beveiligingsinstellingen nogmaals. Veel plezier met coderen, en moge je documenten steeds interactiever worden!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}