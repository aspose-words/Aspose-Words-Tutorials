---
category: general
date: 2026-10-20
description: Maak een Word‑document programmatisch aan en voeg een opdrachtknop toe
  met Aspose.Words. Leer een ActiveX‑besturingselement in te voegen en de knopbijschrift
  in te stellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: nl
lastmod: 2026-10-20
og_description: Maak een Word‑document programmatisch aan en voeg een ActiveX‑opdrachtknop
  in. Deze tutorial legt uit hoe je het besturingselement invoegt en de bijschrift
  instelt met Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Maak Word-document programmatisch – voeg ActiveX‑knop toe
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Maak Word-document programmatisch met een ActiveX‑knop
url: /nl/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document programmatisch met een ActiveX-knop

Maak een Word-document programmatisch met Aspose.Words en voeg vervolgens een opdrachtknop toe die gebruikers kunnen klikken. Deze gids leidt je door het invoegen van een ActiveX‑besturingselement, het configureren van de eigenschappen en het opslaan van het resultaat als een **.docx**‑bestand.

Je ziet een volledig, uitvoerbaar voorbeeld dat je kunt kopiëren naar een console‑applicatie. Aan het einde van de tutorial kun je een Word‑bestand genereren dat een volledig functionele opdrachtknop bevat, en begrijp je hoe je **add command button**, **add activex control**, **insert activex button**, en **set button caption** kunt uitvoeren zonder je C#‑code te verlaten.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Visual Studio 2022 (of een andere C#‑compatibele IDE)  
* Een Aspose.Words for .NET licentiebestand (de gratis proefversie werkt voor dit voorbeeld)  
* Basiskennis van C# en het .NET‑project‑systeem  

Er zijn geen extra NuGet‑pakketten vereist naast **Aspose.Words**, omdat de ActiveX‑ondersteuning in de bibliotheek is ingebouwd.

## Stap 1: Het project instellen en Aspose.Words toevoegen

1. Open een terminal of Visual Studio en maak een nieuw console‑project aan:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Voeg het Aspose.Words‑pakket toe:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Optioneel) Als je een licentiebestand hebt, plaats het dan in de project‑root en voeg de volgende regel toe aan het begin van `Program.cs` om evaluatiewatermerken te vermijden:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Stap 2: Word-document programmatisch maken – het document initialiseren

De eerste handeling is om **een Word‑document programmatisch te maken**. Dit doe je door een `Document`‑object en een `DocumentBuilder` te instantieren, waarmee je de inhoud van het document kunt bewerken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

Het `Document` vertegenwoordigt het volledige bestand, terwijl de `DocumentBuilder` een cursor bijhoudt die je naar elke locatie in het document kunt verplaatsen. Deze scheiding houdt de API overzichtelijk en stelt je in staat om later **add activex control** uit te voeren zonder handmatig low‑level structuren te beheren.

## Stap 3: Opdrachtknop toevoegen – een ActiveX‑besturingselement invoegen

Nu ga je **add command button** uitvoeren door een ActiveX‑besturingselement van het type `OleControlType.CommandButton` in te voegen. De methode `InsertForms2OleControl` vereist het besturingselementtype, een locatie (`Point`) en een grootte (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

De bovenstaande aanroep **insert activex button** in het document op de exacte coördinaten die je opgeeft. De coördinaten worden gemeten in punten (1 pt ≈ 1/72 in). Als je de knop op een specifieke alinea wilt plaatsen, verplaats dan eerst de cursor van de builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Stap 4: Knopbijschrift instellen – de tekst van de opdrachtknop aanpassen

Een knop zonder label is verwarrend, dus je gaat **set button caption** naar iets betekenisvols instellen. De eigenschap `Caption` bepaalt de tekst die op de knop wordt weergegeven, terwijl `Name` het besturingselement een programmatische identifier geeft.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Als je later het document exporteert naar een macro‑ingeschakelde indeling (`.docm`), moet de `OnClick`‑waarde overeenkomen met een VBA‑macronaam. Voor een gewone `.docx` wordt de eigenschap opgeslagen maar niet uitgevoerd, wat prima is voor de meeste automatiseringsscenario's.

## Stap 5: Het document met de ActiveX‑knop opslaan

Na het configureren van het besturingselement kun je **save the document** uitvoeren. Kies een map waarin je schrijfrechten hebt en gebruik de `.docx`‑extensie voor maximale compatibiliteit.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Wanneer je het gegenereerde bestand opent in Microsoft Word, zie je een knop met het label **Submit** op de door jou opgegeven coördinaten. Klikken op de knop in de desktop‑client zal proberen de `SubmitForm`‑macro uit te voeren (als deze bestaat).

## Stap 6: Het resultaat verifiëren en veelvoorkomende problemen oplossen

1. Open `ActiveXCommandButton.docx` in Microsoft Word.  
2. Schakel over naar **Design Mode** (tabblad Developer → **Design Mode**) om de randen van de knop te zien.  
3. Als de knop niet verschijnt, controleer dan of het **Developer**‑tabblad is ingeschakeld en of jouw versie van Word ActiveX‑besturingselementen ondersteunt.  
4. Voor macro‑ingeschakelde bestanden (`.docm`) moet de macro‑naam in `OnClick` overeenkomen met een VBA‑routine; anders toont Word een beveiligingswaarschuwing.

### Pro tip

ActiveX‑besturingselementen werken alleen op Windows. Als je platform‑onafhankelijke interactiviteit nodig hebt, overweeg dan om **Content Controls** (`RichTextContentControl`) te gebruiken in plaats van een ActiveX‑knop.

## Volledige broncode

Hieronder staat het volledige, kant‑klaar programma. Kopieer het naar `Program.cs` en voer `dotnet run` uit.



## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word-document met ActiveX‑knop – C#‑gids](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Opdrachtknop toevoegen aan Word-document met Aspose.Words – Complete gids](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Word-documentknop maken met Aspose.Words – Volledig code‑voorbeeld](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}