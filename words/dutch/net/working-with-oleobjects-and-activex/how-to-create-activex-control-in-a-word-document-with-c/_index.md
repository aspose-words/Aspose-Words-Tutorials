---
category: general
date: 2026-09-14
description: Maak een ActiveX‑besturingselement in een Word‑document met C#. Leer
  hoe je ActiveX invoegt, een interactieve knop toevoegt en het .docx‑bestand via
  code genereert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: nl
lastmod: 2026-09-14
og_description: Maak een ActiveX‑besturingselement in een Word‑document met C#. Volg
  dit volledige voorbeeld om ActiveX in te voegen, een interactieve knop toe te voegen
  en het bestand op te slaan.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: ActiveX‑besturingselement maken in Word met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Hoe maak je een ActiveX‑besturingselement in een Word‑document met C#
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een ActiveX‑besturingselement te maken in een Word‑document met C#

Als je een **ActiveX‑besturingselement** moet maken in een Microsoft Word‑bestand, laat deze gids je een complete, kant‑klaar oplossing zien. Je ziet precies hoe je een ActiveX CommandButton invoegt, de eigenschappen instelt en het resulterende `.docx`‑bestand opslaat met alleen C#‑code.

Het toevoegen van een interactieve knop aan een Word‑document is een veelvoorkomende eis wanneer je wilt dat eindgebruikers macro's of aangepaste logica rechtstreeks vanuit de document‑UI activeren. Het onderstaande voorbeeld laat zien **hoe ActiveX in te voegen** zonder gebruik te maken van tools van derden, en behandelt ook **hoe een Word‑document te maken** via code.

Aan het einde van deze tutorial kun je **een knop met code maken**, de bijschrift aanpassen en een draagbaar Word‑bestand produceren dat het ActiveX‑besturingselement behoudt.

## Vereisten

- .NET 6.0 of later (de Aspose.Words for .NET‑bibliotheek werkt met .NET Core en .NET Framework)
- Een referentie naar het `Aspose.Words` NuGet‑pakket  
  ```bash
  dotnet add package Aspose.Words
  ```
- Basiskennis van C# en object‑georiënteerd programmeren

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuw console‑project (of integreer de code in een bestaand C#‑programma). Importeer de benodigde namespaces zodat de compiler de Word‑verwerkingsklassen kan vinden.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Waarom deze stap belangrijk is** – De `Aspose.Words`‑API levert de `Document`, `DocumentBuilder` en `Forms2OleControl`‑klassen waarmee je Word‑bestanden op objectniveau kunt manipuleren. Zonder deze referenties zou de rest van de code niet compileren.

## Stap 2: Een nieuw Word‑document en een DocumentBuilder maken

Het `Document`‑object vertegenwoordigt het volledige `.docx`‑pakket, terwijl `DocumentBuilder` een vloeiende API biedt voor het invoegen van inhoud.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Uitleg** – Het instantieren van een nieuw `Document` geeft je een leeg canvas. De cursor van de builder start aan het begin van de eerste sectie, klaar voor de volgende invoeging.

## Stap 3: De ActiveX CommandButton invoegen

Gebruik `InsertForms2OleControl` om een ActiveX‑besturingselement op een specifieke locatie te plaatsen. De methode vereist het type besturingselement en een `RectangleF` die de X/Y‑coördinaten en grootte (in punten) definieert.

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Waarom dit werkt** – `OleControlType.CommandButton` vertelt de API om een standaard Windows CommandButton te maken. Het rechthoekige gebied positioneert de knop ten opzichte van de linkerbovenhoek van de pagina, waardoor je een **interactieve knop** precies kunt toevoegen waar je deze nodig hebt.

## Stap 4: De eigenschappen van de knop configureren

Stel nu de zichtbare tekst van de knop (`Caption`) en de interne naam (`Name`) in. Deze eigenschappen zijn wat gebruikers zien en waar VBA‑code later naar kan verwijzen.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Praktische tip** – De `Name` moet uniek zijn binnen het document; anders kunnen VBA‑macro's naar het verkeerde besturingselement verwijzen.

## Stap 5: Het document opslaan

Schrijf tenslotte het bestand naar schijf. Het ActiveX‑besturingselement wordt opgeslagen binnen het Word‑pakket, zodat het opgeslagen bestand volledige functionaliteit behoudt wanneer het wordt geopend in Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Resultaat** – Het openen van `CommandButton.docx` in Word toont een klikbare CommandButton met het label “Click Me”. Het besturingselement kan via de Word‑UI (`Developer → Design Mode → Properties`) aan een macro worden gekoppeld.

## Volledige broncode

Alle stappen samenvoegen levert een enkel, zelfstandig programma op dat je kunt kopiëren, plakken en uitvoeren.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Verwachte output

Het uitvoeren van het programma geeft een bevestigingsregel weer:

```
Document saved to C:\Temp\CommandButton.docx
```

Wanneer je het gegenereerde bestand opent in Microsoft Word, zie je een **CommandButton** op de opgegeven coördinaten. Klikken op de knop in ontwerpmode markeert deze; in uitvoermodus gedraagt hij zich als elke standaard ActiveX‑knop.

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanpassing |
|----------|------------|
| **Ander besturingselementtype** | Vervang `OleControlType.CommandButton` door `OleControlType.CheckBox`, `OleControlType.OptionButton`, enz. |
| **Meerdere knoppen** | Roep `InsertForms2OleControl` herhaaldelijk aan en werk de `RectangleF`‑coördinaten bij voor elke nieuwe knop. |
| **Dynamische grootte** | Bereken de afmetingen van de rechthoek op basis van de paginagrootte (`builder.PageSetup.PageWidth`). |
| **Opslaan naar een stream** | Gebruik `document.Save(stream, SaveFormat.Docx)` wanneer je het bestand moet retourneren vanuit een web‑API. |
| **Word 97‑2003‑formaat** | Wijzig het opslaan‑formaat naar `SaveFormat.Doc` om een `.doc`‑bestand te produceren dat nog steeds het ActiveX‑besturingselement bevat. |

> **Pro tip:** Test het gegenereerde document altijd op de doel‑versie van Word, omdat oudere versies mogelijk beveiligingsinstellingen afdwingen die ActiveX‑besturingselementen standaard uitschakelen.

## Veelgestelde vragen

**Werkt dit met .NET Core?**  
Ja. De Aspose.Words‑bibliotheek is cross‑platform en volledig compatibel met .NET Core en .NET 5/6+.

**Kan ik een macro aan de knop toewijzen via code?**  
De API embedt geen VBA‑code direct. Nadat het document is gegenereerd, open je het in Word, schakel je het tabblad Developer in en neem je een macro op of schrijf je er een die `btnClick` aanroept.

**Wat als de knop niet verschijnt?**  
Controleer of het `Developer`‑tabblad is ingeschakeld in Word en of het document niet in **Protected View** is geopend. Verifieer ook dat de rechthoek‑coördinaten binnen de paginamarges vallen.

## Conclusie

Je weet nu hoe je een **ActiveX‑besturingselement** in een Word‑bestand kunt maken met C#. De tutorial behandelde **hoe ActiveX in te voegen**, toonde **het toevoegen van een interactieve knop**, liet **een Word‑document maken** vanaf nul zien, en illustreerde **een knop met code maken** die behouden blijft na het opslaan.  

Vanaf hier kun je extra ActiveX‑typen verkennen, de knop verbinden met VBA‑macro's, of de logica in een grotere document‑generatieservice opnemen. Experimenteer met verschillende groottes, posities en besturingseigenschappen om de exacte gebruikerservaring te realiseren die je nodig hebt.

---

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Nieuw Word‑document maken](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [VBA‑project maken in Word‑document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Een Word‑document maken en opmaken in Aspose.Words voor .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}