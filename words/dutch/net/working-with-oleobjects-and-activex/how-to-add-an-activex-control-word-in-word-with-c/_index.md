---
category: general
date: 2026-09-30
description: Voeg een ActiveX‑besturingselement toe aan een Word‑document met C#.
  Leer hoe je een ActiveX‑knop invoegt, een opdrachtknop toevoegt en deze klikbaar
  maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: nl
lastmod: 2026-09-30
og_description: Voeg een ActiveX‑besturingselement toe aan een Word‑document met C#.
  Volg deze volledige gids om een ActiveX‑knop in te voegen, een opdrachtknop toe
  te voegen en deze klikbaar te maken.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Een ActiveX‑besturingselement toevoegen aan Word‑documenten – stapsgewijze
  C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Hoe voeg je een ActiveX‑besturingselement toe in Word met C#
url: /nl/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een ActiveX control word toe te voegen in Word met C#

Als je een **ActiveX control word** in een Microsoft Word‑bestand moet insluiten, laat deze gids je precies zien hoe je dat doet. Je ziet een volledig, uitvoerbaar voorbeeld dat een klikbare knop invoegt, het document opslaat en werkt met de nieuwste Aspose.Words voor .NET.

Het toevoegen van een ActiveX control word stelt je in staat interactieve formulieren, aangepaste dialoogvensters of eenvoudige UI‑elementen te maken die zich gedragen als native Word‑besturingselementen. Of je nu een contracttemplate bouwt die gebruikersinteractie vereist of een rapport dat een “Run”‑knop nodig heeft, de onderstaande stappen behandelen alles wat je nodig hebt.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.8)
* Visual Studio 2022 (of een IDE die C# ondersteunt)
* Aspose.Words voor .NET geïnstalleerd (`dotnet add package Aspose.Words`)
* Een basisbegrip van C# en de structuur van Word‑documenten

> **Pro tip:** De `InsertForms2OleControl`‑methode werkt alleen met de legacy “Forms 2.0”‑besturingselementen, de ActiveX‑controls die Word gebruikt voor formuliervelden. Als je nieuwere Office‑versies target, wordt de control nog steeds correct weergegeven in de desktop‑client.

## Stap 1: Het project instellen en namespaces importeren

Maak een nieuw console‑project aan en voeg de benodigde `using`‑statements toe. Hierdoor kan de compiler de klassen `Document`, `DocumentBuilder` en `OleControlType` vinden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

De `Aspose.Words`‑namespace biedt high‑level API’s voor Word‑verwerking, terwijl `Aspose.Words.Drawing` de `OleControlType`‑enumeratie bevat die nodig is om het type ActiveX‑control op te geven.

## Stap 2: Het bron‑Word‑document laden

Je moet beginnen met een Word‑bestand dat je wilt aanpassen. De volgende code laadt `input.docx` uit een map die je opgeeft.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Als het bestand niet bestaat, gooit Aspose.Words een `FileNotFoundException`. Plaats de oproep in een `try/catch`‑blok als je een nette foutafhandeling wilt.

## Stap 3: Een DocumentBuilder maken om het document te bewerken

`DocumentBuilder` is de werkpaard voor het invoegen van tekst, afbeeldingen en controls. Het houdt een cursor bij die wijst naar de locatie waar het volgende element wordt geplaatst.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Standaard staat de cursor van de builder aan het begin van de eerste sectie. Je kunt deze verplaatsen met methoden zoals `MoveToDocumentEnd()` of `MoveToParagraph(index)` als je de knop ergens anders wilt plaatsen.

## Stap 4: Een ActiveX CommandButton‑control invoegen

Nu volgt de kern van de tutorial: het invoegen van een **ActiveX control word** die verschijnt als een klikbare knop. De `InsertForms2OleControl`‑methode neemt twee argumenten – het type control en een bijschrift (of naam) voor de control.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Waarom `OleControlType.CommandButton` gebruiken?**  
  Het vertelt Word om een klassieke Forms 2.0‑commandobutton te maken, die een bijschrift toont en later kan worden gekoppeld aan een macro of VBA‑script.

* **Wat doet het bijschrift?**  
  De string `"ClickMe"` wordt de zichtbare tekst van de knop. Je kunt dit aanpassen naar elke tekst die bij je UI past.

### De knop op een specifieke locatie invoegen

Als je de knop na een bepaalde alinea wilt plaatsen, verplaats je eerst de builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Stap 5: Het gewijzigde document opslaan

Na het invoegen van de control, sla je de wijzigingen op in een nieuw bestand (of overschrijf je het origineel).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `output.docx` opent in de desktop‑versie van Word, zie je de knop met het label **ClickMe** (of **Submit**, afhankelijk van het bijschrift dat je hebt gebruikt). Klikken op de knop in ontwerpmode doet standaard niets; je kunt later een macro toewijzen via het tabblad **Developer** in Word.

## Volledig, uitvoerbaar voorbeeld

Hieronder vind je een zelfstandige applicatie die de volledige workflow demonstreert. Kopieer deze naar `Program.cs` van een nieuw console‑app en voer uit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Verwachte output

* De console toont een succesbericht met het uitvoerpad.
* Het openen van `output.docx` laat een **ClickMe**‑knop zien op de locatie waar de builder deze heeft ingevoegd.
* De knop kan worden geselecteerd, van grootte worden veranderd of een macro krijgen via **Developer → Design Mode** in Word.

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|-------|----------|
| **Hoe een ActiveX‑knop in de header/footer invoegen?** | Verplaats de builder naar de header/footer met `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` voordat je `InsertForms2OleControl` aanroept. |
| **Wat als ik een checkbox in plaats van een knop nodig heb?** | Gebruik `OleControlType.CheckBox` en geef een bijschrift zoals `"Agree"` op. |
| **Werkt de knop in Word Online?** | Nee. Word Online ondersteunt geen legacy Forms 2.0 ActiveX‑controls. De knop wordt alleen weergegeven in de desktop‑client. |
| **Kan ik de grootte van de knop programmatically instellen?** | Na invoegen kun je het `Shape`‑object ophalen via `builder.CurrentParagraph.Runs[0].GetShape()` en `Width`/`Height` aanpassen. |
| **Is er een manier om via code een macro toe te wijzen?** | Aspose.Words biedt geen macro‑bewerking. Je moet het document in Word openen en handmatig een macro koppelen, of de Office Interop‑API gebruiken. |

## Tips voor productiegebruik

* **Vermijd hard‑coded paden** – gebruik `Path.Combine` en configuratie‑bestanden.
* **Dispose van `Document`** – plaats het in een `using`‑statement bij grote bestanden om het geheugen snel vrij te geven.
* **Valideer de output** – controleer programmatically of het document een shape van type `OleControl` bevat door `doc.GetChildNodes(NodeType.Shape, true)` te itereren.
* **Beveiligingsopmerking** – ActiveX‑controls kunnen code uitvoeren op de clientmachine. Distribueer documenten alleen naar vertrouwde gebruikers en overweeg digitale handtekeningen.

## Conclusie

Je weet nu hoe je een **ActiveX control word** aan een Word‑document kunt toevoegen met C#. Door een document te laden, een `DocumentBuilder` te maken, een commandobutton in te voegen met `InsertForms2OleControl` en het bestand op te slaan, kun je de creatie van interactieve Word‑formulieren automatiseren. Experimenteer met andere `OleControlType`‑waarden, plaats controls in headers of tabellen, en combineer ze met macro’s voor rijkere gebruikerservaringen.

---

*Volgende stappen*: verken **hoe andere soorten ActiveX**‑controls in te voegen, leer **hoe je event‑handlers voor commandobuttons** via VBA toe te voegen, en lees over **beste praktijken voor het invoegen van ActiveX‑knoppen** voor cross‑platform compatibiliteit.


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}