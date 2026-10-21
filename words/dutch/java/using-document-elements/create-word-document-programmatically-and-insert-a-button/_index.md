---
category: general
date: 2026-09-21
description: Maak een Word-document programmatisch aan en leer hoe je de knop ‘Word-document
  opslaan’, de opdrachtknop ‘Word’ invoegt en de bijschrift van de opdrachtknop instelt
  met DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: nl
lastmod: 2026-09-21
og_description: Maak een Word-document programmatically met Aspose.Words. Leer hoe
  je een knop om een Word-document op te slaan, een opdrachtknop in Word invoegt,
  de bijschrift van een opdrachtknop instelt en DocumentBuilder gebruikt voor interactieve
  formulieren.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Maak een Word-document programmatically en voeg een knop toe
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Maak een Word‑document programmatisch aan en voeg een knop toe
url: /nl/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document programmatisch en voeg een knop toe

Als je **een Word-document programmatisch wilt maken**, biedt Aspose.Words een vloeiende API waarmee je interactieve besturingselementen kunt toevoegen, zoals een CommandButton. Deze tutorial legt ook uit **hoe je DocumentBuilder gebruikt**, hoe je **een Word-document met knop opslaat**, en hoe je **de caption van de commandoknop instelt**, zodat de knop er precies uitziet zoals je verwacht in het .docx‑bestand.

U leert hoe u:

* Een leeg document initialiseren met `Document`.
* Werken met `DocumentBuilder` om het document te bewerken.
* Een **CommandButton** invoegen (`insert command button word`).
* De naam en zichtbare caption van de knop instellen (`set command button caption`).
* Het resultaat opslaan op schijf (`save word document button`).

De stappen zijn geschreven voor .NET‑ontwikkelaars die C# gebruiken en de nieuwste Aspose.Words for .NET (v24.10). Er zijn geen extra NuGet‑pakketten nodig naast Aspose.Words.

---

## Wat je nodig hebt voordat je begint

| Voorwaarde | Reden |
|------------|-------|
| Visual Studio 2022 (of een andere C# IDE) | Om de voorbeeldcode te compileren en uit te voeren. |
| .NET 6.0 SDK of later | Biedt de runtime voor het voorbeeld. |
| Aspose.Words for .NET (v24.10 of nieuwer) | De bibliotheek die je **een Word-document programmatisch kunt maken** en formulierbesturingselementen kunt manipuleren. |
| Basiskennis van C# en OOP-concepten | Vereist om de codeflow te begrijpen. |

Je kunt Aspose.Words installeren via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Word-document programmatisch maken

De eerste stap is het instantieren van een leeg `Document`. Dit object vertegenwoordigt het volledige Word‑bestand in het geheugen.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Het programmatisch maken van het document geeft je een schoon canvas waarop je alinea's, tabellen of interactieve besturingselementen kunt toevoegen.  

---

## Hoe DocumentBuilder te gebruiken

`DocumentBuilder` is de primaire klasse voor het bewerken van een `Document`. Het biedt methoden om tekst, afbeeldingen en formuliervelden in te voegen. In deze tutorial gebruiken we het om een CommandButton te plaatsen.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder houdt een interne cursor bij die wijst naar de huidige invoeglocatie. Standaard start deze aan het begin van de eerste sectie, wat ideaal is voor ons voorbeeld.

---

## CommandButton invoegen in Word

Aspose.Words behandelt een CommandButton als een ActiveX‑besturingselement. De methode `InsertForms2OleControl` maakt een generiek OLE‑object dat we vervolgens als knop configureren.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Op dit punt bestaat het besturingselement in het document, maar heeft het geen visuele weergave totdat we het type definiëren.

---

## Caption van de commandoknop instellen

Nu vertellen we het OLE‑object dat het zich moet gedragen als een CommandButton en geven we het een vriendelijke label.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Het instellen van de **command button caption** is essentieel omdat Word deze tekst op het knopoppervlak weergeeft. Als je `SetCaption` weglaten, verschijnt de knop met een generiek label.

---

## Word-document met knop opslaan

Ten slotte sla je het document op schijf op. De methode `Save` schrijft het volledige Word‑pakket, inclusief de nieuw ingevoegde knop, naar een .docx‑bestand.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Het bestand `CommandButton.docx` bevat nu een volledig functionele knop met het label **Submit**. Wanneer de gebruiker het bestand opent in Microsoft Word en op de knop klikt, wordt de standaardactie (die je later via VBA kunt koppelen) geactiveerd.

---

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het demonstreert de volledige workflow van het maken van een document tot het opslaan van de knop.

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

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwacht resultaat**

* Een bestand met de naam `CommandButton.docx` op het door jou opgegeven pad.
* Het openen van het bestand in Microsoft Word toont een enkele **Submit**‑knop op de eerste pagina.
* De knop kan worden geselecteerd, van grootte worden gewijzigd, of gekoppeld aan een macro via het **Developer**‑tabblad van Word.

---

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|-------|----------|
| *Wat als ik meer dan één knop nodig heb?* | Herhaal stappen 3–6 met verschillende namen en captions. Elke knop moet een unieke `SetName`‑waarde hebben. |
| *Kan ik de grootte van de knop instellen?* | Ja. Na het invoegen van het besturingselement kun je de eigenschappen `Width` en `Height` aanpassen via het `OleFormat`‑object. |
| *Werkt de knop in alle Word‑versies?* | ActiveX‑besturingselementen worden ondersteund in de desktopversie van Word (Windows). Ze worden niet weergegeven in Word Online of op macOS. |
| *Hoe voeg ik een klik‑handler toe?* | Je moet VBA‑code schrijven die verwijst naar de naam van de knop (`btnSubmit`). De VBA‑macro kan worden ingebed met `doc.VbaProject`. |
| *Wat als ik de knop in een tabelcel moet invoegen?* | Verplaats de cursor van de builder naar de gewenste cel (`builder.MoveTo(cell.FirstParagraph)`) voordat je `InsertForms2OleControl` aanroept. |

---

## Pro‑tips

* **Pro tip:** Stel altijd een betekenisvolle naam in met `SetName`. Dit vereenvoudigt VBA‑automatisering en maakt debuggen makkelijker.
* **Let op:** Het vergeten aanroepen van `SetControlType`. Zonder deze aanroep verschijnt het OLE‑object als een generieke placeholder in plaats van een klikbare knop.
* **Performance tip:** Als je veel documenten in een lus genereert, hergebruik dan één `DocumentBuilder`‑instantie en roep `builder.MoveToDocumentEnd()` aan vóór elke invoeging om onnodige cursor‑resets te vermijden.

---

## Volgende stappen

Nu je weet hoe je **een Word-document programmatisch kunt maken**, **een commandobutton in Word kunt invoegen**, **de caption van de commandoknop kunt instellen**, en **een Word-document met knop kunt opslaan**, kun je meer geavanceerde scenario's verkennen:

* Voeg **TextFormField**‑besturingselementen toe voor gebruikersinvoer.
* Combineer knoppen met **MacroButton**‑velden om VBA direct uit te voeren.
* Gebruik **DocumentBuilder.InsertImage** om pictogrammen op je knoppen te plaatsen.
* Integreer met ASP.NET om Word‑formulieren te genereren op

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een nieuw Word-document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Maak Word-document met Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Voeg inline afbeelding in Word-document toe met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}