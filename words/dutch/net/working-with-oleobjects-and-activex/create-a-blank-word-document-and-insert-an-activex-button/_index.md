---
category: general
date: 2026-11-18
description: Maak een leeg Word‑document en voeg een ActiveX‑knop toe met C#. Leer
  hoe je een besturingselement toevoegt, de knopbijschrift instelt en het bestand
  opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: nl
lastmod: 2026-11-18
og_description: Maak een leeg Word‑document en voeg een ActiveX‑knop toe met C#. Volg
  deze volledige tutorial om de controle toe te voegen, de knoptekst in te stellen
  en het resultaat op te slaan.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Maak een leeg Word‑document en voeg een ActiveX‑knop toe – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Maak een leeg Word‑document en voeg een ActiveX‑knop toe
url: /nl/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een ActiveX‑knop in

Als je een **create a blank Word document** moet maken en een interactieve ActiveX‑knop erin wilt plaatsen, laat deze gids je precies zien hoe je dat doet met Aspose.Words for .NET. Je ziet de volledige code, begrijpt waarom elke regel belangrijk is, en leert hoe je **set button caption** kunt **instellen** zodat de besturing er klaar uitziet voor gebruikersinteractie.

Naast het primaire doel behandelen we **how to insert ActiveX**, de stappen **how to add control** aan een Word‑bestand, en de nuances van **insert ActiveX button** met een aangepast bijschrift. Aan het einde heb je een herbruikbaar patroon voor elk document‑automatiseringsscenario dat ingebedde UI‑elementen vereist.

## Wat je zult leren

* Hoe je **create a blank Word document** programmatically maakt.  
* De exacte API‑aanroepen die nodig zijn om **insert ActiveX button** te doen en de eigenschappen te configureren.  
* Hoe je **set button caption** instelt zodat de besturing het gewenste tekst toont.  
* Tips om het bestand op een locatie naar keuze op te slaan en veelvoorkomende valkuilen af te handelen.

### Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).  
* Aspose.Words for .NET geïnstalleerd (`Install-Package Aspose.Words`).  
* Basiskennis van C# en Visual Studio of een andere .NET‑compatibele IDE.

---

## Maak een leeg Word‑document met Aspose.Words

De eerste stap is het instantieren van een leeg `Document`‑object. Dit object vertegenwoordigt een Word‑bestand dat geen inhoud bevat totdat we iets toevoegen.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Waarom dit belangrijk is*: Een leeg `Document` geeft je een schoon canvas. Je kunt later alinea's, tabellen of besturingselementen toevoegen zonder je zorgen te maken over bestaande opmaak.

---

## Initialise een DocumentBuilder om met het document te werken

`DocumentBuilder` is een hulklasse die je in staat stelt inhoud in te voegen op de huidige cursorpositie. Het houdt automatisch bij waar je je in het document bevindt.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is*: Zonder een `DocumentBuilder` zou je de low‑level knooppuntboom handmatig moeten manipuleren. De builder vereenvoudigt het invoegen van tekst, afbeeldingen en ActiveX‑besturingselementen.

---

## Hoe een ActiveX‑knop in te voegen (insert activex button)

Nu gebruiken we `InsertForms2OleControl` om een ActiveX‑besturingselement in te sluiten. De methode vereist drie argumenten:

1. Het type besturingselement (`OleControlType.CommandButton`).  
2. Een interne naam voor het besturingselement (gebruikt door VBA of macro‑code).  
3. Een `RectangleF` die de positie en grootte op de pagina definieert.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Waarom dit belangrijk is*: Dit is de kern van **how to insert activex** in een Word‑document. De coördinaten van het rechthoekige gebied worden uitgedrukt in punten (1 punt = 1/72 inch). Pas ze aan om de knop te positioneren waar je deze nodig hebt.

### Tip

Als je wilt dat de knop op een specifieke pagina verschijnt, verplaats dan eerst de cursor van de builder:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Hoe het knopbijschrift in te stellen (set button caption)

Nadat het besturingselement is geplaatst, kun je de eigenschappen aanpassen. De meest zichtbare eigenschap is `Caption`, die bepaalt welke tekst op de knop wordt weergegeven.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Waarom dit belangrijk is*: Gebruikers zien het bijschrift, niet de interne naam. Het wijzigen maakt de knop betekenisvol in het uiteindelijke document.

---

## Sla het document met de knop op

Tot slot schrijf je het document naar schijf. Je kunt elk ondersteund formaat kiezen (`.docx`, `.pdf`, enz.). Hier slaan we op als een Word‑document.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Waarom dit belangrijk is*: Het bewaren van het bestand stelt je in staat het te openen in Microsoft Word en de knop te testen. Wanneer het document wordt geopend, verschijnt de knop met het bijschrift “Press”.

### Verwacht resultaat

Het openen van `with_button.docx` in Word toont een lege pagina met een rechthoekige knop gelabeld **Press**. Klikken op de knop doet standaard niets omdat er geen VBA‑macro is gekoppeld, maar het besturingselement is volledig functioneel en kan later aan code worden gekoppeld.

---

## Hoe een besturingselement aan een specifieke alinea toe te voegen (how to add control)

Soms wil je de knop in een specifieke alinea plaatsen, bijvoorbeeld na wat instructietekst. Gebruik `MoveTo` om de builder te positioneren voordat je het besturingselement invoegt.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Waarom dit belangrijk is*: Dit patroon laat **how to add control** in context zien, waardoor de documentlay-out logisch blijft.

---

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| Knop verschijnt buiten de pagina | Rechthoekcoördinaten liggen buiten de paginamarges | Gebruik `builder.PageSetup` om paginagrootte op te halen en een veilige `RectangleF` te berekenen. |
| Bijschrift wordt niet weergegeven | `Caption` ingesteld voordat het besturingselement volledig is geïnitialiseerd | Stel `Caption` **na** de `InsertForms2OleControl`‑aanroep in, zoals getoond in Stap 4. |
| Document wordt opgeslagen zonder de knop | De cursor van de builder werd verplaatst na invoegen zonder wijzigingen vast te leggen | Houd de builder op dezelfde pagina of roep `builder.Document.UpdatePageLayout()` aan vóór het opslaan. |

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het maakt een leeg Word‑bestand, voegt een ActiveX‑knop in, stelt het bijschrift in en slaat het resultaat op.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Uitvoer**: Na het uitvoeren van het programma, open `C:\Temp\with_button.docx` in Microsoft Word. Je ziet een enkele pagina met de tekst “Below is an ActiveX button created programmatically:” gevolgd door een knop gelabeld **Press**.

---

## Conclusie

Je weet nu hoe je **create a blank Word document**, **insert an ActiveX button**, **set button caption**, en **save** het resultaat kunt gebruiken met Aspose.Words for .NET. Hetzelfde patroon kan worden uitgebreid naar andere ActiveX‑besturingselementen (checkboxes, list boxes, enz.) door `OleControlType` te wijzigen.  

Vervolgens kun je **how to insert ActiveX button**‑gebeurtenissen verkennen met VBA, of **how to add control** aan bestaande documenten die al inhoud bevatten. Beide onderwerpen bouwen direct voort op de hier behandelde concepten.

Veel plezier met coderen, en voel je vrij om te experimenteren met verschillende groottes, posities en bijschriften om te voldoen aan de UI‑vereisten van je applicatie!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}