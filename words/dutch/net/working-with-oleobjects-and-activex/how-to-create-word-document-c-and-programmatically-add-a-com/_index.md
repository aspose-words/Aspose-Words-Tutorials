---
category: general
date: 2026-09-11
description: Leer hoe je een Word‑document maakt in C# en via code een commandoknop
  toevoegt met Aspose.Words in een paar eenvoudige stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: nl
lastmod: 2026-09-11
og_description: Maak een Word‑document in C# en voeg via code een commandoknop toe
  met Aspose.Words. Volg deze volledige gids voor een werkende oplossing.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Word-document maken in C# – een commandoknop programmatically toevoegen
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Hoe een Word‑document te maken in C# en programmatisch een commandoknop toe
  te voegen
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word-document c# maken en programmatisch een commandoknop toevoegen

Als je **create word document c#** moet maken en een interactieve knop wilt insluiten, laat deze gids je precies zien hoe je dat doet. Met Aspose.Words kun je programmatisch een commandoknop toevoegen in slechts een paar regels code, waardoor handmatig UI-werk in Word niet meer nodig is.

In deze tutorial leer je hoe je:

* Een leeg Word-bestand initialiseren met C#.
* Een ActiveX **CommandButton**-besturingselement invoegen.
* De eigenschappen van de knop instellen, zoals naam en bijschrift.
* Het document opslaan zodat de knop verschijnt wanneer het bestand wordt geopend in Microsoft Word.

Er zijn geen externe tools vereist, behalve de Aspose.Words for .NET bibliotheek, en de stappen werken met .NET 6+ of .NET Framework 4.6.2 en later.

## Vereisten

Before you start, make sure you have:

| Vereiste | Reden |
|------------|--------|
| .NET 6 SDK (of .NET Framework 4.6.2+) | Biedt de runtime voor het C#-project. |
| Visual Studio 2022 (of elke C# IDE) | Maakt het eenvoudig om de code te schrijven, te bouwen en uit te voeren. |
| Aspose.Words for .NET NuGet‑pakket | Levert de `Document`, `DocumentBuilder` en `Forms2OleControl` klassen die in het voorbeeld worden gebruikt. |
| Basiskennis van C#-syntaxis | Stelt je in staat de code te volgen zonder extra leercurves. |

Je kunt het Aspose.Words‑pakket toevoegen via de NuGet‑console:

```powershell
Install-Package Aspose.Words
```

## Stap 1: Een nieuw C# console‑project opzetten

Maak een console‑applicatie die het Word‑bestand genereert. Open een terminal en voer uit:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Het gegenereerde `Program.cs`‑bestand zal de code bevatten die in de volgende stappen wordt getoond.

## Stap 2: Een leeg document en een DocumentBuilder maken

De eerste bewerking is het instantieren van een `Document`‑object, dat een leeg `.docx`‑bestand vertegenwoordigt, en een `DocumentBuilder` die je in staat stelt de inhoud van het document te bewerken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:**  
`Document` is de container voor alle Word‑elementen (alinea's, tabellen, besturingselementen). `DocumentBuilder` biedt een vloeiende API om objecten in te voegen op de huidige cursorpositie zonder te werken met low‑level knooppuntcollecties.

## Stap 3: Een ActiveX CommandButton‑besturingselement invoegen

Aspose.Words ondersteunt het invoegen van legacy ActiveX‑besturingselementen via de `InsertForms2OleControl`‑methode. De methode vereist het type besturingselement en de gewenste grootte in points.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Wat er onder de motorkap gebeurt:**  
Word behandelt een ActiveX‑besturingselement als een OLE (Object Linking and Embedding) object. De `Forms2OleControl`‑klasse omsluit de OLE‑data en stelt eigenschappen bloot zoals `Name` en `Caption`.

## Stap 4: De naam en het bijschrift van de knop configureren

Nadat het besturingselement is geplaatst, kun je de runtime‑eigenschappen aanpassen. Het instellen van een betekenisvolle `Name` helpt je de knop later te identificeren, terwijl `Caption` de tekst definieert die op de knop wordt weergegeven.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro tip:**  
Als je van plan bent om de klik‑event van de knop af te handelen met VBA, wordt de `Name` de macro‑naam die je aanroept, bijv. `Sub btnSubmit_Click()`.

## Stap 5: Het document opslaan op schijf

Schrijf tenslotte het document naar een `.docx`‑bestand. Kies een map waar je schrijfrechten voor hebt; het voorbeeld gebruikt een relatief pad, dat wordt opgelost naar de output‑directory van het project.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Het uitvoeren van het programma produceert `CommandButton.docx`. Het openen van het bestand in Microsoft Word toont een klikbare **Submit**‑knop:

![Word-document met een Submit‑knop](/images/command-button.png "Schermafbeelding van een Word-document met een Submit‑knop gemaakt met C#")

*Afbeeldings‑alt‑tekst (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Het resultaat verifiëren

1. Start Word en open `CommandButton.docx`.  
2. Je zou een knop met het label **Submit** in de document‑body moeten zien.  
3. Als je over de knop hovert, wordt de naam `btnSubmit` weergegeven in het **Properties**‑paneel (tabblad Ontwikkelaar → Eigenschappen).  

Als de knop niet verschijnt, zorg er dan voor dat het **Developer**‑tabblad is ingeschakeld in Word (Bestand → Opties → Lint aanpassen → vink *Developer* aan). ActiveX‑besturingselementen worden verborgen wanneer het tabblad is uitgeschakeld.

## Veelvoorkomende variaties en randgevallen afhandelen

| Situatie | Aanbevolen aanpassing |
|-----------|------------------------|
| **Andere knopgrootte** | Wijzig de breedte‑ en hoogte‑argumenten in `InsertForms2OleControl`. Bijvoorbeeld, `150, 40` maakt een grotere knop. |
| **Meerdere knoppen** | Roep `InsertForms2OleControl` herhaaldelijk aan, en verplaats de cursor van de builder tussen de aanroepen (`builder.Writeln();`). |
| **Knop zonder ActiveX** | Gebruik `InsertFormField` om een legacy‑formulierveld toe te voegen (bijv. een selectievakje) als je compatibiliteit nodig hebt met oudere Word‑versies die ActiveX blokkeren. |
| **Cross‑platform gebruik** | ActiveX‑besturingselementen werken alleen in Windows‑versies van Word. Voor Mac of web‑gebaseerde viewers, overweeg in plaats daarvan een hyperlink in te voegen die als knop is gestyled. |
| **Beveiligingswaarschuwingen** | Word kan een beveiligingsprompt weergeven bij het openen van een document met ActiveX‑besturingselementen. Het ondertekenen van het document met een vertrouwd certificaat vermindert deze wrijving. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in `Program.cs`. Het compileert en draait zonder aanpassingen nadat het Aspose.Words NuGet‑pakket is toegevoegd.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwachte uitvoer in de console:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Het openen van het gegenereerde bestand toont de **Submit**‑knop klaar voor interactie.

## Conclusie

Je weet nu hoe je **create word document c#** en **programmatically add command button** besturingselementen kunt maken met Aspose.Words. Het proces bestaat uit het initialiseren van een `Document`, het invoegen van een `Forms2OleControl`, het configureren van de eigenschappen en het opslaan van het bestand. Vanaf hier kun je:

* Meer besturingselementen toevoegen (bijv. selectievakjes, tekstvelden) door `ControlType` te wijzigen.
* VBA‑macro's aan de knop koppelen voor aangepaste logica.
* Deze techniek combineren met andere Aspose.Words‑functies zoals mail‑merge of het vullen van sjablonen.

Experimenteer met verschillende groottes, bijschriften en meerdere knoppen om bij je automatiseringsscenario te passen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word-document met kop‑ en voettekst met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Maak Word-document met Aspose.Words voor .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Maak groepsvorm in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}