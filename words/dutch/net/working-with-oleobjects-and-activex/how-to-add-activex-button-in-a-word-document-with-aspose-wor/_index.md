---
category: general
date: 2026-08-14
description: Hoe een ActiveX‑knop toe te voegen in een Word‑document met Aspose.Words
  – leer een leeg Word‑document te maken en een ActiveX‑knop programmatisch in te
  voegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: nl
lastmod: 2026-08-14
og_description: Hoe een ActiveX‑knop toe te voegen in een Word‑document met Aspose.Words.
  Deze tutorial laat zien hoe je een leeg Word‑document maakt, een ActiveX‑knop invoegt
  en het resultaat opslaat.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Hoe een ActiveX‑knop toe te voegen in Word – Aspose.Words‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Hoe een ActiveX-knop toe te voegen aan een Word‑document met Aspose.Words
url: /nl/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een ActiveX‑knop toe te voegen in een Word‑document met Aspose.Words

Als je **hoe ActiveX toe te voegen** controls aan een gegenereerd Word‑bestand nodig hebt, laat deze gids je de exacte stappen zien. Je leert om **ActiveX‑knop invoegen** programmatisch, beginnend met **een leeg Word‑document maken** en eindigend met een opgeslagen bestand dat geopend kan worden in Microsoft Word.

Het toevoegen van een knop die VBA‑code uitvoert of een macro activeert is een veelvoorkomende eis voor geautomatiseerde rapportgeneratoren, formuliertemplates of interactieve contracten. Met Aspose.Words voor .NET kun je het document bouwen zonder Office te starten, waardoor het proces snel en server‑vriendelijk blijft.

## Vereisten

* .NET 6.0 (or later) SDK geïnstalleerd.
* Visual Studio 2022 of een andere C#‑compatibele IDE.
* Aspose.Words for .NET NuGet‑pakket (`Aspose.Words` versie 24.9 of nieuwer).  
  Installeer het met:
  ```bash
  dotnet add package Aspose.Words
  ```
* Een Windows‑omgeving als je de ActiveX‑knop wilt testen, omdat ActiveX‑controls de Windows‑versie van Microsoft Word vereisen.

## Stap 1: Een leeg Word‑document maken

De eerste taak is om **een leeg Word‑document maken** in het geheugen. Aspose.Words biedt de `Document`‑klasse hiervoor.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` vertegenwoordigt het volledige .docx‑bestand. Op dit moment bevat het document nog geen pagina's, maar je kunt meteen beginnen met het toevoegen van inhoud.

## Stap 2: Een DocumentBuilder initialiseren

`DocumentBuilder` is een helper waarmee je tekst, afbeeldingen en andere objecten in het document kunt invoegen. Het werkt op de `Document`‑instantie die je zojuist hebt gemaakt.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder houdt een cursorpositie bij; alles wat je na deze regel invoegt, verschijnt aan het begin van de eerste pagina.

## Stap 3: Een ActiveX CommandButton‑control invoegen

Aspose.Words biedt de `InsertForms2OleControl`‑methode om legacy‑formuliervelden toe te voegen, inclusief ActiveX. De methode vereist het type control en de grootte in points.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Het geretourneerde `Forms2OleControl`‑object stelt je in staat eigenschappen zoals de naam en bijschrift van de control te configureren.

## Stap 4: De eigenschappen van de knop configureren

Het instellen van een betekenisvolle `Name` maakt het later mogelijk de control vanuit VBA‑code te refereren. De `Caption` is de tekst die de gebruiker op de knop ziet.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Houd de naam kort en alfanumeriek; Word zal namen die spaties of speciale tekens bevatten afwijzen.

## Stap 5: Het document opslaan

Schrijf tenslotte het document naar schijf. Gebruik de `.docx`‑extensie voor moderne Word‑bestanden; de ActiveX‑knop werkt op dezelfde manier in `.doc`‑bestanden, maar `.docx` is het voorkeursformaat voor nieuwe projecten.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Wanneer je `ActiveXButton.docx` opent in Microsoft Word, zie je een klikbare **Submit**‑knop. Als je macro's inschakelt, kun je VBA‑code koppelen aan `btnSubmit_Click` en laten uitvoeren wanneer de gebruiker op de knop klikt.

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samenvoegen levert een zelfstandige applicatie op die je kunt kopiëren, plakken en uitvoeren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwachte output** – Na het uitvoeren van het programma drukt de console de opslaglocatie af, en bij het openen van het gegenereerde bestand in Word zie je een knop met het label **Submit** bovenaan de eerste pagina.

## Veelvoorkomende vragen en randgevallen behandelen

### Werkt de knop in alle Word‑versies?

ActiveX‑controls worden ondersteund in de desktop‑versie van Word op Windows. Ze worden niet weergegeven in Word Online, Word voor macOS of mobiele clients. Als je cross‑platform interactiviteit nodig hebt, overweeg dan content‑controls of HTML‑gebaseerde oplossingen.

### Wat als ik een andere grootte of positie nodig heb?

`InsertForms2OleControl` plaatst de control op de huidige cursor van de builder. Om deze te verplaatsen, pas je de cursor aan met `builder.MoveTo` vóór het invoegen, of wijzig je de `Left`‑ en `Top`‑eigenschappen van de control na creatie:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Kan ik andere ActiveX‑typen toevoegen?

Ja. De `Forms2OleControlType`‑enumeratie bevat `CheckBox`, `OptionButton`, `ListBox` en meer. Vervang `CommandButton` door de gewenste enum‑waarde en pas de eigenschappen overeenkomstig aan.

### Is een macro vereist om de knop iets te laten doen?

De knop zelf doet niets totdat je VBA‑code koppelt. In Word druk je op **Alt+F11** om de VBA‑editor te openen, zoek `btnSubmit_Click` en schrijf de gewenste logica. Het gegenereerde document behoudt het VBA‑project als je het **SaveFormat.Doc** (legacy `.doc`) formaat inschakelt, maar `.docx`‑bestanden kunnen geen VBA‑macro's opslaan. Gebruik het `.doc`‑formaat als je ingebedde VBA nodig hebt.

## Conclusie

Je weet nu **hoe je ActiveX**‑controls aan een Word‑bestand kunt toevoegen met Aspose.Words. Door de stappen te volgen om **een leeg Word‑document te maken**, een `DocumentBuilder` te initialiseren, **ActiveX‑knop in te voegen**, de eigenschappen te configureren en het bestand op te slaan, kun je interactieve Word‑templates rechtstreeks vanuit je .NET‑code genereren.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **insert ActiveX button**‑eventhandling, het toevoegen van **create word document aspose** voor tabellen of afbeeldingen, en het beveiligen van macro‑ingeschakelde documenten voor bedrijfsimplementatie. Experimenteer met verschillende control‑typen en lay‑outopties om de gebruikerservaring af te stemmen op de behoeften van je applicatie.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word‑document maken met kop‑ en voettekst met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Word‑document maken met tabel met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}