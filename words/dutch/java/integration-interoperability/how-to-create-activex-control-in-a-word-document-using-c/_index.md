---
category: general
date: 2026-08-20
description: Leer hoe je een ActiveX‑besturingselement maakt, de knopgrootte instelt
  en een knop toevoegt aan Word met een compleet C#‑voorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: nl
lastmod: 2026-08-20
og_description: Maak een ActiveX‑besturingselement in een Word‑bestand met C#. Deze
  tutorial laat zien hoe je de knopgrootte instelt, een knop toevoegt aan Word en
  een klikbare knop maakt.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Maak een ActiveX‑besturingselement in Word – stapsgewijze C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Hoe maak je een ActiveX‑besturingselement in een Word‑document met C#
url: /nl/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een ActiveX‑besturingselement in een Word‑document met C#

Als je een **ActiveX control** moet maken binnen een Microsoft Word‑bestand, laat deze gids je precies zien hoe je dat doet. Je ziet hoe je **knop toevoegen aan Word**, de afmetingen van de knop instelt en het besturingselement klikbaar maakt — alles met een kort, zelfstandig C#‑programma.

In deze tutorial leer je:

* Begrijpen waarom een ActiveX‑besturingselement nuttig is voor interactieve Word‑documenten.  
* De exacte code leren om **knopgrootte instellen** en een bijschrift toe te wijzen.  
* Zien hoe je een **klikbare knop** maakt die later kan worden gekoppeld aan een macro of externe logica.  

De stappen werken met Aspose.Words .NET 23.12 of later en vereisen alleen een .NET‑ontwikkelomgeving.

> **Prerequisite** – Je beschikt over een geldige Aspose.Words‑licentie (of je gebruikt de evaluatie‑versie) en Visual Studio 2022 of een andere C#‑IDE.

---

## Hoe maak je een ActiveX‑besturingselement in een Word‑document

De eerste stap is het instantieren van een lege `Document` en een `DocumentBuilder`. De builder biedt de high‑level API voor het invoegen van objecten zoals ActiveX‑besturingselementen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

De `InsertActiveXButton`‑methode (hieronder gedefinieerd) bevat de logica voor **hoe je een knop invoegt** en configureert.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Het uitvoeren van het programma maakt **ActiveXButton.docx**. Het openen van het bestand in Word toont een knop met het label **Submit**. Het besturingselement is volledig functioneel — bij klikken wordt het standaard `CommandButton_Click`‑event opgehaald, dat je later kunt koppelen aan een VBA‑macro.

### Waarom dit werkt

* `InsertForms2OleControl` vertelt Word een OLE‑object van het type **CommandButton** in te sluiten, de klassieke ActiveX‑knopklasse.  
* De breedte‑ en hoogte‑argumenten **stellen de knopgrootte in**; Word vertaalt de waarden van punten (1 pt ≈ 1/72 in).  
* Het benoemen van het besturingselement (`Name = "btnSubmit"`) maakt het eenvoudig te vinden vanuit VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Knopgrootte en bijschrift instellen

Als je een andere weergave wilt, pas je de numerieke argumenten in de `InsertForms2OleControl`‑aanroep aan. De methodesignatuur is:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – De programmatic identifier van de ActiveX‑klasse (`"CommandButton"` voor een standaardknop).  
* **width / height** – Grootte in punten. Voor een knop van 2 cm breed, gebruik `width = 56.7` (2 cm ≈ 56.7 pt).  

Je kunt het bijschrift ook na het invoegen aanpassen:

```csharp
commandButton.Caption = "Send Request";
```

Het wijzigen van het bijschrift heeft geen invloed op de grootte, maar wel op de visuele feedback voor de gebruiker.

### Pro tip

Wil je een vierkante knop, stel dan beide afmetingen op dezelfde waarde:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Knop toevoegen aan Word en klikbaar maken

De bovenstaande code **voegt al een knop toe aan Word**. Om de knop een actie te laten uitvoeren, moet je een VBA‑macro schrijven die het `Click`‑event afhandelt. Hier is een minimale macro die je kunt plakken in de Word VBA‑editor (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Omdat het besturingselement `btnSubmit` heet, mappt Word automatisch het `Click`‑event naar `btnSubmit_Click`. Dit is de standaard manier om **klikbare knop**‑functionaliteit te creëren zonder externe bibliotheken.

> **Note:** Macro‑beveiligingsinstellingen in Word kunnen ActiveX‑besturingselementen blokkeren. Zorg ervoor dat “Enable all macros” of “Enable VBA macros” is geselecteerd voor het document, of onderteken de macro digitaal voor productiegebruik.

---

## Veelgestelde vragen: hoe voeg je een knop in en foutoplossing

### 1. Wat als de knop niet verschijnt na het opslaan?

* Controleer of de Aspose.Words‑versie `InsertForms2OleControl` ondersteunt. Versies vóór 22.5 missen deze functionaliteit.  
* Zorg ervoor dat het doelbestandformaat `.docx` of `.doc` is. Oudere formaten zoals `.rtf` kunnen geen ActiveX‑objecten opslaan.

### 2. Kan ik de knop op een specifiek bladwijzer invoegen?

Ja. Verplaats de builder naar de bladwijzer voordat je `InsertForms2OleControl` aanroept:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Hoe **knopgrootte instellen** op basis van de tekstlengte?

Bereken de benodigde breedte met de `Graphics.MeasureString`‑methode (van `System.Drawing`) en converteer pixels naar punten (`points = pixels * 72 / DPI`). Geef vervolgens de berekende breedte door aan `InsertForms2OleControl`.

### 4. Is er een manier om meerdere knoppen in een lus toe te voegen?

Zeker. Plaats de invoeglogica in een `for`‑lus en pas de `Left`‑ en `Top`‑eigenschappen voor elke iteratie aan:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Verwachte output

Wanneer je het programma uitvoert en **ActiveXButton.docx** opent:

* Er verschijnt één **Submit**‑knop links‑boven op de eerste pagina.  
* De knopgrootte komt overeen met de door jou opgegeven afmetingen (`100 pt × 30 pt`).  
* Als je de VBA‑macro hebt toegevoegd, toont een klik op de knop een berichtvenster: “You clicked the Submit button!”.

Je hebt nu succesvol **ActiveX control maken**, **knopgrootte instellen** en **knop toevoegen aan Word** terwijl je ook hebt geleerd **hoe je een knop invoegt** en **een klikbare knop** maakt voor toekomstige automatiseringstaken.

---

## Conclusie

In deze tutorial heb je geleerd hoe je **ActiveX control** maakt binnen een Word‑document met C#. Door de stappen te volgen kun je **knopgrootte instellen**, het besturingselement een betekenisvolle naam geven, en **knop toevoegen aan Word** zodat het een **klikbare knop** wordt die gekoppeld is aan een VBA‑macro.  

Vanaf hier kun je verder gaan met:

* Het koppelen van de knop aan een .NET COM‑add‑in in plaats van VBA.  
* Het gebruiken van andere ActiveX‑klassen zoals `CheckBox` of `ComboBox`.  
* Het automatiseren van het maken van volledige formulieren met meerdere besturingselementen.

Voel je vrij om te experimenteren met verschillende groottes


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}