---
category: general
date: 2026-07-23
description: Knop om een Word‑document te maken met Aspose.Words – stapsgewijze handleiding
  voor het invoegen van een ActiveX CommandButton in een .docx‑bestand.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: nl
lastmod: 2026-07-23
og_description: 'maak een Word-documentknop met Aspose.Words: leer hoe je een ActiveX
  CommandButton in een Word‑bestand kunt insluiten in enkele minuten.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Maak Word-documentknop – Complete gids voor Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Knop om Word‑document te maken met Aspose.Words – Volledig codevoorbeeld
url: /nl/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# maak een Word-documentknop met Aspose.Words – Complete programmeergids

Heb je ooit een **create word document button** nodig gehad, maar wist je niet welke API je moest gebruiken? Je bent niet de enige—de meeste ontwikkelaars lopen tegen een muur aan wanneer ze interactieve besturingselementen in een .docx‑bestand proberen in te sluiten. Het goede nieuws? Met Aspose.Words voor .NET kun je een volledig functionele ActiveX CommandButton in een Word‑document plaatsen met slechts een paar regels code.

In deze tutorial lopen we het volledige proces door: van het opzetten van het project, het initialiseren van een `DocumentBuilder`, het invoegen van de knop met `InsertForms2OleControl`, en uiteindelijk het opslaan van het bestand zodat Word de besturingselement herkent. Aan het einde heb je een kant‑klaar Word‑bestand dat een klikbare knop bevat—geen COM‑interop gymnastiek vereist.

## Wat je nodig hebt

- **.NET 6.0** of later (de code werkt ook met .NET Framework 4.6+).  
- **Aspose.Words for .NET** NuGet‑pakket (versie 23.9 of nieuwer).  
- Een basisbegrip van C# (we houden de syntax beginnersvriendelijk).  
- Visual Studio 2022 of een IDE naar keuze.

Dat is alles—geen extra COM‑referenties, geen Office‑interop, alleen pure managed code.

---

## Stap 1: Stel Aspose.Words in om **create word document button** te maken

Allereerst, voeg het Aspose.Words‑pakket toe aan je project:

```bash
dotnet add package Aspose.Words
```

Of, als je de Visual Studio NuGet‑UI gebruikt, zoek dan naar “Aspose.Words” en klik op **Install**. Deze enkele regel geeft je toegang tot de `Document`, `DocumentBuilder` en de `InsertForms2OleControl`‑methode die we later nodig hebben.

> **Pro tip:** Houd je NuGet‑pakketten up‑to‑date; nieuwere releases bevatten vaak bug‑fixes voor ActiveX‑afhandeling.

## Stap 2: Initialiseert **DocumentBuilder** voor een **ActiveX CommandButton**

Nu maken we een nieuw Word‑document en starten een `DocumentBuilder`. Beschouw `DocumentBuilder` als het penseel waarmee je inhoud op het canvas kunt tekenen.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Let op hoe we `System.Drawing` importeren—de `Rectangle`‑struct definieert de locatie en grootte van de knop. Hier zal de **ActiveX CommandButton** zich bevinden.

## Stap 3: Gebruik **InsertForms2OleControl** om een **CommandButton** toe te voegen

Dit is het hart van de tutorial: het invoegen van de knop zelf. De `InsertForms2OleControl`‑methode neemt drie argumenten—controltype, een `Rectangle` en optioneel een naam. We gebruiken `OleControlType.CommandButton` om het exacte control dat we willen te specificeren.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Die ene aanroep doet veel:

1. **Creëert** een OLE‑object binnen het Word‑bestand.  
2. **Registreert** het als een ActiveX CommandButton, die Word weergeeft als een klikbaar UI‑element.  
3. **Positioneert** het volgens de opgegeven rechthoek.

Als je de bijschrift van de knop of andere eigenschappen moet wijzigen, kun je dat na het invoegen doen door toegang te krijgen tot de onderliggende `OleFormat`. Voor de meeste scenario's is de standaardbijschrift (“CommandButton1”) voldoende.

## Stap 4: Sla het Word‑document op dat de **CommandButton** bevat

Opslaan is eenvoudig—wijs gewoon naar een map waar je schrijfrechten voor hebt. De bestandsextensie moet `.docx` zijn zodat de knop de round‑trip overleeft.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wanneer je `CommandButton.docx` opent in Microsoft Word, zie je een kleine knop in de linkerbovenhoek van de eerste pagina. Erop klikken doet niets zonder extra configuratie (dat zou VBA vereisen), maar het control is volledig functioneel en kan later worden gekoppeld.

> **Waarom dit werkt:** Aspose.Words schrijft de OLE‑stroom direct in het DOCX‑pakket, waardoor de noodzaak voor Word om het control tijdens runtime te genereren wordt omzeild. Dit garandeert dat de knop precies verschijnt waar je hem hebt geplaatst.

## Stap 5: Verifieer de knop in Word

Open het gegenereerde bestand:

1. Start Microsoft Word.  
2. Navigeer naar **Bestand → Openen** en selecteer `CommandButton.docx`.  
3. Je zou een rechthoekige knop met het label “CommandButton1” moeten zien.

Als je de knop niet ziet, zorg er dan voor dat **Ontwerpmodus** is ingeschakeld (Ontwikkelaar → Ontwerpmodus). Dit schakelt de visuele weergave van ActiveX‑besturingselementen.

## Stap 6: Geavanceerde opties – Het aanpassen van de **ActiveX CommandButton**

Hieronder staan een paar snelle aanpassingen die handig kunnen zijn:

| Doel | Codefragment |
|------|--------------|
| Wijzig bijschrift | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Stel macro‑naam in (vereist Word‑macro‑ondersteuning) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Verander grootte na invoegen | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Deze fragmenten demonstreren de flexibiliteit van `InsertForms2OleControl`. Je kunt zelfs andere ActiveX‑besturingselementen zoals `CheckBox` of `ListBox` insluiten door de `OleControlType`‑enum te wijzigen.

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar te kopiëren programma dat **creates a word document button** vanaf nul maakt:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Verwachte output wanneer je het programma uitvoert:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Open het resulterende bestand en je zult de knop precies zien waar de code deze heeft geplaatst.

## Veelvoorkomende valkuilen & hoe ze te vermijden

- **Ontbrekende `System.Drawing`‑referentie** – De `Rectangle`‑struct bevindt zich daar; zonder deze zal de compiler klagen.  
- **Gebruik van een oudere Aspose.Words‑versie** – Vroegere releases ondersteunden `InsertForms2OleControl` niet volledig. Upgrade naar het nieuwste stabiele pakket.  
- **Opslaan als `.doc` in plaats van `.docx`** – De OLE‑stroom wordt verwijderd in het oudere binaire formaat, waardoor de knop verdwijnt.  
- **Uitvoeren op een headless server zonder geïnstalleerde Word** – De knop blijft wel in het bestand, maar je kunt deze niet bekijken zonder Word. Dit is prima voor geautomatiseerde generatie‑pijplijnen.

## Volgende stappen – Het uitbreiden van de **create word document button** workflow

Nu je de basis onder de knie hebt, overweeg deze geavanceerde ideeën:

- **VBA‑macro’s koppelen** aan de knop voor aangepaste bedrijfslogica.  
- **Meerdere knoppen genereren** in een lus voor dynamische formulieren.  
- **Combineren met Aspose.PDF** om hetzelfde document naar PDF te exporteren terwijl de visuele lay-out behouden blijft (de knop wordt een statische afbeelding in PDF).  
- **

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}