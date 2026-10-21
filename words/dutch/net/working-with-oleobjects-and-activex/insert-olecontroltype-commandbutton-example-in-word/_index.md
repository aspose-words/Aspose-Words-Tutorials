---
category: general
date: 2026-08-17
description: Invoegen van een OleControlType.CommandButton‑voorbeeld in Word met Aspose.Words.
  Leer hoe je formulierbesturingselementen via code aan een Word‑document kunt toevoegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: nl
lastmod: 2026-08-17
og_description: Voeg een voorbeeld van OleControlType.CommandButton toe in Word met
  Aspose.Words. Volg deze gids om formulierbesturingselementen toe te voegen aan een
  Word-document.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Voorbeeld van OleControlType.CommandButton invoegen in Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Voorbeeld van OleControlType.CommandButton invoegen in Word
url: /nl/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OleControlType.CommandButton‑voorbeeld invoegen in Word

Als je een **OleControlType.CommandButton‑voorbeeld** in een Word‑bestand wilt **invoegen**, laat deze gids je zien hoe. Je leert **hoe je formulierelementen aan een Word‑document kunt toevoegen** met Aspose.Words, met een volledig, uitvoerbaar C#‑programma.

Formulierelementen zoals ActiveX‑knoppen stellen je in staat interactieve Word‑sjablonen te bouwen — handig voor contracten, vragenlijsten of interne tools. De onderstaande stappen behandelen alles, van projectopzet tot het verifiëren dat de knop correct verschijnt in het opgeslagen `.docx`‑bestand.

## Vereisten

Zorg ervoor dat je het volgende hebt:

- .NET 6.0 SDK of later geïnstalleerd  
- Visual Studio 2022 (of een andere C#‑IDE)  
- Een Aspose.Words for .NET‑licentie of een gratis tijdelijke licentie  
- Basiskennis van C# en Word‑bestandconcepten  

> **Pro tip:** Als je de gratis proefversie gebruikt, plaats dan het licentiebestand in dezelfde map als het uitvoerbare bestand en laad het aan het begin van `Main`.

## Stap 1: Maak een nieuw console‑project en voeg Aspose.Words toe

Open een terminal en voer uit:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Dit maakt een schoon project aan en haalt het nieuwste Aspose.Words‑pakket op, dat de `Document`, `DocumentBuilder` en `InsertForms2OleControl`‑API’s levert die nodig zijn voor het **OleControlType.CommandButton‑voorbeeld**.

## Stap 2: Schrijf het volledige programma

Maak of vervang `Program.cs` door de volgende code. Het bevat alle benodigde `using`‑directieven, licentie‑laden en de vier‑stappen‑workflow die in het oorspronkelijke fragment wordt getoond.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Waarom elke regel belangrijk is

* **Licentie‑laden** – zorgt ervoor dat je niet beperkt wordt door evaluatie‑beperkingen.  
* **`Document doc = new Document();`** – maakt de container voor alle Word‑inhoud; dit is de basis van het **OleControlType.CommandButton‑voorbeeld**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – biedt een fluente API om tekst, afbeeldingen en besturingselementen toe te voegen.  
* **`InsertForms2OleControl`** – de kernmethode die implementeert **hoe je formulierelementen aan een Word‑document kunt toevoegen**. De enum‑waarde `OleControlType.CommandButton` vertelt Aspose.Words een ActiveX‑knop te maken.  
* **`new Rectangle(100, 100, 80, 30)`** – positioneert de knop 100 pt vanaf de linker‑ en bovenmarge, met een breedte van 80 pt en een hoogte van 30 pt. Pas deze getallen aan om ze in je lay‑out te laten passen.  
* **`doc.Save`** – schrijft het .docx‑bestand naar schijf; het bestand bevat nu de ingesloten knop.

## Stap 3: Bouw en voer het programma uit

Voer vanuit de projectmap uit:

```bash
dotnet run
```

Je zou het volgende console‑bericht moeten zien:

```
Document saved to ActiveXButton.docx
```

Open `ActiveXButton.docx` in Microsoft Word. Je ziet een knop met het label **ClickMe** ongeveer in het midden van de pagina. Als je op de knop klikt, wordt het standaard ActiveX‑gedrag geactiveerd (wat meestal een nop‑op is tenzij je een macro koppelt).

![insert olecontroltype.commandbutton example](/images/activex-button.png "ActiveX CommandButton inserted into a Word document")

*Afbeeldings‑alt‑tekst:* insert olecontroltype.commandbutton example – een ActiveX CommandButton weergegeven in een Word‑document.

## Stap 4: De knop aanpassen (optioneel)

Het eenvoudige **OleControlType.CommandButton‑voorbeeld** maakt een standaardknop. Je kunt de bijschrift, het lettertype of zelfs een macro koppelen door het onderliggende OLE‑object te bewerken. Hieronder staat een beknopte manier om het bijschrift van de knop na invoeging te wijzigen:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Opmerking:** Directe manipulatie van OLE‑eigenschappen vereist kennis van de onderliggende COM‑interface. Voor de meeste scenario's is het standaardbijschrift voldoende.

## Stap 5: Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|-------------------|-----------|
| De knop verschijnt niet in Word | Het document is opgeslagen als `.docx` maar geopend in een viewer die OLE‑besturingselementen verwijdert (bijv. Google Docs). | Open het bestand in Microsoft Word of Word Online met bewerkingsrechten. |
| Runtime‑fout `ArgumentOutOfRangeException` | De `Rectangle`‑coördinaten liggen buiten de paginamarges. | Gebruik waarden binnen de paginagrootte (bijv. 0‑500 voor A4). |
| Licentie‑exception | Een proeflicentie verloopt na 30 dagen. | Laad een geldige licentiebestand of vraag een verlengde proefperiode aan bij Aspose. |

## Stap 6: Hoe dit voorbeeld past in grotere automatiseringsprojecten

Wanneer je **hoe je formulierelementen aan een Word‑document kunt toevoegen** op grote schaal moet toepassen — bijvoorbeeld bij het genereren van honderden contract‑sjablonen — verpak je de invoeglogica in een herbruikbare methode:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Je kunt vervolgens `AddCommandButton` aanroepen binnen lussen die rijen met gegevens verwerken, zodat elk gegenereerd document een uniek benoemde knop bevat (bijv. `Approve_001`, `Approve_002`).

## Conclusie

Je hebt nu een compleet **OleControlType.CommandButton‑voorbeeld** dat laat zien **hoe je formulierelementen aan een Word‑document kunt toevoegen** met Aspose.Words voor .NET. De tutorial behandelde projectopzet, volledige broncode, aanpassingstips en veelvoorkomende probleemoplossing.

Vanaf hier kun je verder verkennen:

- Andere besturingselementtypen toevoegen, zoals **CheckBox** of **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- De knop koppelen aan een VBA‑macro voor rijkere interactiviteit.  
- PDF‑bestanden genereren vanuit hetzelfde document terwijl de formuliervelden behouden blijven.

Experimenteer met verschillende groottes, posities en besturingselement‑namen om ze aan jouw specifieke gebruikssituatie aan te passen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}