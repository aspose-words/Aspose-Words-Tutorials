---
category: general
date: 2026-09-11
description: Leer hoe je forms2olecontrol in code maakt met Aspose.Words DocumentBuilder.
  Deze stapsgewijze gids behandelt het invoegen van een ActiveX‑opdrachtknop, het
  gebruik van setOleClassName en het aanpassen van de grootte.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: nl
lastmod: 2026-09-11
og_description: Maak forms2olecontrol in code met Aspose.Words. Volg deze gids om
  een ActiveX‑opdrachtknop in te voegen, de klassenaam in te stellen en de grootte
  aan te passen.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Maak forms2olecontrol in code – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Hoe maak je forms2olecontrol in code met Aspose.Words
url: /nl/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe forms2olecontrol in code te maken met Aspose.Words

Als je **forms2olecontrol in code** moet **maken**, laat deze gids je precies zien hoe je dat doet met de Aspose.Words .NET API. Of je nu een sjabloon automatiseert dat een ActiveX‑opdrachtknop vereist of je gewoon een Word‑document programmatisch wilt verrijken, de onderstaande stappen behandelen alles van het invoegen van de controle tot het configureren van het uiterlijk.

In deze tutorial leer je hoe je de **Aspose.Words DocumentBuilder** gebruikt om een **ActiveX command button** in te voegen, de klasse in te stellen met de **setOleClassName‑methode**, en de **Forms2OleControl‑grootte** aan te passen. Er zijn geen externe tools nodig—alleen een .NET‑ontwikkelomgeving en de Aspose.Words‑bibliotheek.

## Vereisten

* .NET 6.0 of later geïnstalleerd (de code werkt ook met .NET Framework 4.7+)
* Een recente versie van het Aspose.Words for .NET NuGet‑pakket
* Basiskennis van C# en het concept van ActiveX‑besturingselementen in Word‑documenten

Als een van deze ontbreekt, installeer het NuGet‑pakket met:

```bash
dotnet add package Aspose.Words
```

## Waar deze tutorial over gaat

* Een `DocumentBuilder`‑instantie maken
* Een `Forms2OleControl` invoegen (het onderliggende object voor een ActiveX‑opdrachtknop)
* De juiste klassenaam toewijzen met `setOleClassName`
* De visuele breedte en hoogte instellen met de **Forms2OleControl size**‑eigenschappen
* Het document opslaan en het resultaat verifiëren

Aan het einde van de gids heb je een volledig functioneel Word‑bestand met een klikbare knop die je verder kunt aanpassen of koppelen aan VBA‑macro's.

---

## Hoe forms2olecontrol in code te maken – stap‑voor‑stap

### Stap 1: Initialiseer de DocumentBuilder

De `DocumentBuilder`‑klasse is het startpunt voor de meeste document‑generatietaken in Aspose.Words. Het biedt methoden om tekst, afbeeldingen, tabellen en, belangrijk voor deze tutorial, OLE‑besturingselementen toe te voegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:**  
`DocumentBuilder` houdt de huidige cursorpositie in het document bij. Door het vroeg te maken, zorg je ervoor dat elke volgende invoeging—zoals de **ActiveX command button**—precies verschijnt waar je wilt.

### Stap 2: Invoegen van de Forms2OleControl

De `insertForms2OleControl`‑methode retourneert een `Forms2OleControl`‑object. Dit object vertegenwoordigt de OLE‑controle‑placeholder die Word zal weergeven als een ActiveX‑knop.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Waarom dit belangrijk is:**  
Zonder deze aanroep kun je de eigenschappen van de controle niet manipuleren. Het geretourneerde `Forms2OleControl` geeft volledige toegang tot de **setOleClassName‑methode**, grootte‑attributen en andere OLE‑specifieke instellingen.

### Stap 3: Specificeer de ActiveX‑klasse met setOleClassName

Word moet weten welk type ActiveX‑controle het moet weergeven. De klassenaam voor een standaard opdrachtknop is "Forms.CommandButton.1".

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Waarom dit belangrijk is:**  
De `setOleClassName`‑methode is de brug tussen de generieke OLE‑placeholder en de concrete **ActiveX command button**. Het gebruik van een verkeerde klassenaam resulteert in een leeg object of een runtime‑fout wanneer het document wordt geopend.

### Stap 4: Pas de Forms2OleControl‑grootte aan

Een knop die te klein of te groot is, oogt onprofessioneel. Je kunt de afmetingen regelen met `setWidth` en `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Waarom dit belangrijk is:**  
Deze eigenschappen vormen de **Forms2OleControl size**. Ze beïnvloeden hoe de knop verschijnt in de Word‑UI en zorgen ervoor dat elke gekoppelde macro voldoende klikbare oppervlakte heeft.

### Stap 5: Sla het document op en test

Na het configureren van de controle, sla je het document op op een locatie naar keuze.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Open `ActiveXButton.docx` in Microsoft Word. Je zou een knop moeten zien met het label “CommandButton1” (de standaardbijschrift). Klikken doet niets tenzij je een VBA‑macro toevoegt, maar de controle zelf is volledig functioneel.

**Verwachte output:**  

![Word-document met een ingevoegde ActiveX-opdrachtknop](/images/activeX-button.png "Schermafbeelding van een Word-document waarop een nieuw gemaakte ActiveX-opdrachtknop via code is ingevoegd")

*De alt‑tekst van de afbeelding bevat het primaire zoekwoord voor toegankelijkheid en SEO.*

---

## Inzicht in de ActiveX Forms2OleControl‑klasse

De `Forms2OleControl`‑klasse omsluit de low‑level OLE‑infrastructuur die Word gebruikt voor ActiveX‑elementen. Het erft van `Shape`, wat betekent dat je ook typische vormopmaak (bijv. randen, rotatie) kunt toepassen indien nodig.

* **ActiveX command button** – Het meest voorkomende gebruik; je kunt het koppelen aan een macro via de ontwikkelaarstools van Word.
* **setOleClassName method** – Bepaalt welke COM‑klasse Word laadt; andere geldige waarden zijn onder andere "Forms.TextBox.1" en "Forms.ComboBox.1".
* **Forms2OleControl size** – Wordt geregeld via `SetWidth`/`SetHeight`. Deze methoden accepteren punten (1 pt = 1/72 in).

### Wanneer Forms2OleControl te gebruiken versus Content Controls

Als je alleen eenvoudige gegevensinvoer nodig hebt (bijv. een gewoon tekstveld), zijn de ingebouwde content controls van Word lichter. Gebruik `Forms2OleControl` wanneer je volledige ActiveX‑functionaliteit nodig hebt, zoals event‑handling of aangepaste VBA‑interactie.

---

## Extra eigenschappen instellen (optioneel)

Hoewel de kernstappen voldoende zijn om **forms2olecontrol in code** te **maken**, wil je vaak het uiterlijk of gedrag van de knop fijn afstemmen.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Waarom dit belangrijk is:**  
`SetOleData` stelt je in staat willekeurige eigenschapswaarden rechtstreeks in de OLE‑stroom te schrijven. Dit is de meest flexibele manier om een **ActiveX command button** aan te passen zonder VBA te gebruiken.

---

## Veelvoorkomende valkuilen en probleemoplossing

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Knop verschijnt als een grijze doos | Onjuiste klassenaam doorgegeven aan `setOleClassName` | Controleer of de string exact `"Forms.CommandButton.1"` is (hoofdlettergevoelig) |
| Grootte verandert niet | Width/Height ingesteld vóór het invoegen van de controle | Roep altijd `SetWidth`/`SetHeight` **na** `InsertForms2OleControl` aan |
| Document geeft “OLE object not found” bij openen | Ontbrekende Aspose.Words‑licentie (evaluatieversie kan OLE beperken) | Pas een geldige licentie toe of gebruik de gratis proefversie met volledige OLE‑ondersteuning |
| Knopbijschrift blijft “CommandButton1” | `SetOleData` niet gebruikt of macro leest de eigenschap niet | Gebruik een VBA‑macro om de `"Caption"`‑eigenschap te lezen of stel het bijschrift in via de Word‑UI |

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat een volledige console‑applicatie die je kunt kopiëren, plakken en uitvoeren. Het demonstreert alles wat in deze tutorial behandeld is.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Uitleg van elke sectie**

* **Using directives** – Haalt de Aspose.Words‑namespace op die nodig is voor `Document`, `DocumentBuilder` en `Forms2OleControl`.
* **Document creation** – Maakt een leeg Word‑bestand aan.
* **InsertForms2OleControl** – Plaatst de OLE‑controle op de huidige cursor van de builder.
* **SetOleClassName** – Vertelt Word dat de controle een **ActiveX command button** is.
* **SetWidth / SetHeight** – Past de **Forms2OleControl size** aan voor een professionele uitstraling.
* **SetOleData (optional)** – Demonstreert hoe extra eigenschappen zoals een bijschrift kunnen worden geschreven.
* **Save** – Schrijft het uiteindelijke `.docx`‑bestand naar schijf.

Voer het programma uit (`dotnet run`) en open `ActiveXButton.docx`. Je zou een knop moeten zien die je later kunt koppelen aan een macro.

---

## Conclusie

Je weet nu hoe je **forms2olecontrol in code** kunt **maken** met Aspose.Words, van het initialiseren van de `DocumentBuilder` tot het configureren van de **ActiveX command button** met `setOleClassName` en het regelen van de **Forms2OleControl size**. Deze aanpak stelt je in staat complexe Word‑documenten te automatiseren, interactieve UI‑elementen in te sluiten, en alle logica binnen te houden

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Groep‑vorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechthoek‑vorm maken in Word met Aspose.Words – Stap‑voor‑stap‑gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}