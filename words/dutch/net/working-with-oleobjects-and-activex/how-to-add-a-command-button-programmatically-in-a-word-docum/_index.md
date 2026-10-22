---
category: general
date: 2026-10-13
description: Leer hoe je een opdrachtknop programmatisch kunt toevoegen met Aspose.Words.
  Deze gids laat ook zien hoe je een Word‑documentknop maakt met volledige C#‑code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: nl
lastmod: 2026-10-13
og_description: Voeg via code een opdrachtknop toe aan een Word‑document met Aspose.Words.
  Volg deze volledige tutorial om een knop in een Word‑document te maken met C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Een commandoknop via code toevoegen aan een Word‑document – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een opdrachtknop programmatisch toevoegen in een Word‑document
url: /nl/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een command button programmatically toevoegen in een Word-document  

Als u een **command button programmatically wilt toevoegen**, biedt Aspose.Words een nette API waarmee u OLE‑formulierelementen direct in een .docx‑bestand kunt insluiten. Deze tutorial leidt u door elke stap die nodig is om een **Word‑documentknop te maken** die zich gedraagt als een gewone formulierelementknop wanneer het document wordt geopend in Microsoft Word.  

U leert hoe u de ontwikkelomgeving instelt, de knop invoegt, de eigenschappen configureert en het resultaat verifieert. Er zijn geen externe hulpprogramma's nodig—alleen een .NET‑project en de Aspose.Words for .NET‑bibliotheek.  

## Vereisten  

Zorg er voordat u begint voor dat u het volgende heeft:  

* .NET 6.0 SDK of later geïnstalleerd.  
* Een recente versie van Aspose.Words for .NET (de voorbeelden gebruiken 23.12, maar elke 22.x+ release werkt).  
* Een IDE zoals Visual Studio 2022 of Visual Studio Code.  

De code draait op Windows, macOS en Linux omdat Aspose.Words platform‑onafhankelijk is.  

## Stap 1: Het project instellen en Aspose.Words refereren  

1. Maak een nieuw console‑project aan:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Voeg het Aspose.Words NuGet‑pakket toe:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Open **Program.cs** en vervang de inhoud door de scaffold die in de volgende stappen wordt getoond.  

Het project op deze manier instellen zorgt ervoor dat de compiler de `Aspose.Words`‑ en `Aspose.Words.Drawing.Forms`‑namespaces kan vinden die nodig zijn voor formulierelementen.  

## Stap 2: Een leeg document en een DocumentBuilder initialiseren  

De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` een vloeiende API biedt voor het toevoegen van inhoud.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Waarom deze stap belangrijk is* – Zonder een `DocumentBuilder` kunt u de knop niet nauwkeurig op de pagina positioneren. De builder houdt ook rekening met de huidige cursorpositie, waardoor het later eenvoudig is om meerdere besturingselementen in te voegen.  

## Stap 3: Het command button OLE‑element invoegen  

Aspose.Words behandelt een command button als een OLE‑element van het type `ControlType.CommandButton`. U definieert de locatie en grootte met een `RectangleF` gemeten in points (1 point = 1/72 inch).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Belangrijke punten**  

* De oorsprong van de rechthoek (X, Y) is relatief ten opzichte van de linkerbovenhoek van de pagina.  
* Het wijzigen van de `Width` of `Height` verandert de visuele grootte van de knop.  
* `InsertForms2OleControl` retourneert een `Forms2OleControl`‑object dat u verder kunt configureren.  

## Stap 4: De naam en bijschrift van de knop configureren  

De **name** wordt door de macro‑engine van Word gebruikt om het element te identificeren, terwijl de **caption** de tekst is die de gebruiker ziet.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Als u later VBA‑macros wilt toevoegen, gebruik dan een beschrijvende naam omdat de macro‑recorder van Word naar deze eigenschap verwijst.  

## Stap 5: (Optioneel) Het document opslaan en het resultaat verifiëren  

Het opslaan van het bestand stelt u in staat het te openen in Microsoft Word om te bevestigen dat de knop verschijnt en werkt.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Wanneer u *CommandButtonDemo.docx* in Word opent, zou u een knop met het label **Submit** moeten zien, ongeveer 1,4 inch vanaf de linkermarge en 2,1 inch vanaf de bovenkant van de pagina gepositioneerd. Klikken op de knop doet standaard niets omdat er geen macro is gekoppeld, maar het visuele element is volledig functioneel.  

## Stap 6: Randgevallen en veelvoorkomende valkuilen  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Knop overlapt bestaande tekst** | De rechthoek kan een alinea kruisen, waardoor lay‑outproblemen ontstaan. | Voeg de knop in na het aanroepen van `builder.Writeln()` om de cursor naar een nieuwe regel te verplaatsen, of pas de `Y`‑coördinaat aan. |
| **Document opent met een waarschuwing** | Sommige Word‑versies markeren OLE‑elementen die geen gekoppeld programma hebben. | Zorg ervoor dat het elementtype `CommandButton` is; Word behandelt het als een standaard formulierelement en vereist geen extern programma. |
| **Uitvoeren op Linux met headless‑omgeving** | Word kan niet worden gestart om de UI te testen, maar het bestand blijft geldig. | Gebruik een unit‑test die de eigenschappen van het element leest (`commandButton.Name`, `commandButton.Caption`) om te verifiëren dat ze correct zijn ingesteld. |
| **Meerdere knoppen nodig** | Het hergebruiken van dezelfde `DocumentBuilder` zonder de cursor te verplaatsen voegt de knop toe bovenop de vorige. | Roep `builder.MoveToDocumentEnd()` aan of pas de `Y`‑waarde van de rechthoek aan vóór elke invoeging. |

Het vroeg aanpakken van deze randgevallen bespaart tijd bij het opschalen van de oplossing naar volledige formulieren met tientallen elementen.  

## Stap 7: Volledig, uitvoerbaar voorbeeld  

Hieronder staat een zelfstandige programma‑code die u kunt kopiëren, plakken en uitvoeren zonder aanpassingen (behalve het NuGet‑herstel).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Verwachte output**  

Het uitvoeren van het programma geeft een pad weer dat ongeveer als volgt is:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Het openen van het gegenereerde *CommandButtonDemo.docx* toont een enkele **Submit**‑knop geplaatst op de coördinaten die in de code zijn gedefinieerd. Er verschijnen geen extra UI‑elementen, wat bevestigt dat de workflow **add command button programmatically** geslaagd is.  

## Conclusie  

U weet nu hoe u een **command button programmatically** aan een Word‑document kunt toevoegen met Aspose.Words, en u begrijpt ook hoe u een **Word‑documentknop** kunt maken die later kan worden gekoppeld aan VBA‑macros of externe automatiseringstools. Het proces bestaat uit het initialiseren van een document, het invoegen van een OLE `CommandButton`‑element, het configureren van de eigenschappen en het opslaan van het bestand.  

Vanaf hier kunt u:  

* Meer besturingselementen toevoegen (checkboxes, tekstvelden) door stap 3 te herhalen met verschillende `ControlType`‑waarden.  
* VBA‑macros aan de knop koppelen om acties uit te voeren zoals het opslaan van een formulier of het verzenden van een e‑mail.  
* Volledige formulieren dynamisch genereren door te itereren over een data‑gedreven collectie van velddefinities.  

Experimenteer met de rechthoekcoördinaten en het bijschrift van de knop om ze aan te passen aan uw UI‑ontwerp. Veel programmeerplezier!  

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Voeg een combobox‑formulierveld toe aan een Word‑document met Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Voeg een checkbox‑formulierveld toe aan een Word‑document met Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Maak een leeg Word‑document met Aspose.Words – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}