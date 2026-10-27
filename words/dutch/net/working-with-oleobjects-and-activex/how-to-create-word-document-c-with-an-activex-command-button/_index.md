---
category: general
date: 2026-10-26
description: Leer hoe je een Word‑document maakt in C# en een ActiveX‑knop via code
  toevoegt. Deze stapsgewijze handleiding behandelt het invoegen van een commandoknop,
  het verbergen ervan tijdens het ontwerpen en het opslaan van het bestand.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: nl
lastmod: 2026-10-26
og_description: Maak een Word‑document in C# en voeg via code een ActiveX‑knop toe.
  Volg deze volledige tutorial om een opdrachtknop in te sluiten die alleen tijdens
  runtime verschijnt.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Maak een Word‑document in C# met een ActiveX‑opdrachtknop – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Hoe maak je een Word‑document in C# met een ActiveX‑opdrachtknop
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document C# te maken met een ActiveX‑opdrachtknop

Als je een **Word‑document C#** moet maken dat een interactieve knop bevat, laat deze gids je precies zien hoe. Aan het einde van de eerste twee zinnen ken je de algemene aanpak, en de volgende stappen lopen elke regel code die je moet schrijven door.

Je leert hoe je een ActiveX‑knop toevoegt, deze tijdens het ontwerpen verbergt, en alleen zichtbaar maakt wanneer de gebruiker het bestand opent. De tutorial behandelt ook veelvoorkomende valkuilen zoals beveiligingswaarschuwingen en versie‑compatibiliteit, zodat je betrouwbare documenten kunt leveren.

## Voorvereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of later geïnstalleerd  
* Een gelicentieerde kopie van **Aspose.Words for .NET** (de gratis proefversie werkt voor experimenten)  
* Basiskennis van C# en Visual Studio (elke IDE die .NET ondersteunt is voldoende)  

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Stap 1: Een Word‑document C# maken en de DocumentBuilder initialiseren

De eerste stap is het instantieren van een `Document`‑object en een `DocumentBuilder`. Het `Document` vertegenwoordigt het volledige .docx‑bestand, terwijl de `DocumentBuilder` vloeiende methoden biedt om inhoud toe te voegen.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:** Zonder een `DocumentBuilder` zou je de OpenXML‑DOM handmatig moeten manipuleren, wat foutgevoelig en moeilijker leesbaar is. De builder abstraheert die details en garandeert een goed gevormd Word‑bestand.

## Stap 2: Hoe een ActiveX‑knop toe te voegen – een CommandButton‑besturingselement invoegen

Nu voegen we een **CommandButton ActiveX‑control** op een specifieke locatie in. Het rechthoek‑object bepaalt de positie (X, Y) en grootte (breedte, hoogte) in punten.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Waarom dit belangrijk is:** `InsertForms2OleControl` is de enige Aspose.Words‑methode die een echt ActiveX‑OLE‑object maakt. De enum‑waarde `Forms2OleControlType.CommandButton` vertelt Word om een klikbare knop in te sluiten in plaats van een generieke OLE‑container.

## Stap 3: Programma‑matig een opdrachtknop toevoegen – verbergen tot runtime

Word behandelt elk ingevoegd shape standaard als zichtbaar. Om de knop onzichtbaar te houden tijdens het ontwerpen van de sjabloon, stel je de eigenschap `Hidden` in op het shape dat de builder zojuist heeft aangemaakt.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Waarom dit belangrijk is:** Het instellen van `Hidden = true` voorkomt dat de knop de ontwerpmodus vervuilt. Wanneer het document in Word wordt geopend, onthult de runtime‑omgeving automatisch de control, waardoor de beoogde gebruikerservaring behouden blijft.

## Stap 4: Het bestand opslaan – een opdrachtknop‑Word‑document maken

Tot slot schrijf je het document naar schijf. Kies een pad waar je applicatie schrijfrechten heeft, en gebruik de extensie `.docx` om moderne compatibiliteit te garanderen.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Waarom dit belangrijk is:** Opslaan als `.docx` garandeert dat de ingebedde ActiveX‑control voldoet aan de Office Open XML‑standaard, die wordt ondersteund door Word 2007 en later. Als je legacy‑ondersteuning voor `.doc` nodig hebt, vervang dan de extensie en gebruik `SaveFormat.Doc`.

## Volledig werkend voorbeeld

Alles samengevoegd, hier is het complete programma dat je kunt kopiëren, plakken en uitvoeren:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Verwacht resultaat:** Na het uitvoeren van het programma, open `C:\Temp\ActiveX.docx` in Microsoft Word. Je ziet een leeg document; de knop is niet zichtbaar in de ontwerpmodus. Druk op **Alt + F9** om veldcodes te togglen, klik vervolgens op het knopgebied — Word zal de ActiveX‑control weergeven, en je kunt ermee interageren (bijv. dubbelklikken om de eigenschappen te bekijken).

## Randgevallen en best‑practice‑tips

| Situatie | Waar op te letten | Aanbevolen oplossing |
|-----------|-------------------|----------------------|
| **Gebruiker schakelt ActiveX uit** | Word kan een beveiligingswaarschuwing tonen of de control blokkeren. | Instructeer eindgebruikers om “ActiveX‑besturingselementen” in het Vertrouwenscentrum in te schakelen, of bied een macro‑ondertekende alternatief. |
| **Document geopend in Word Online** | Word Online ondersteunt geen ActiveX; de knop wordt weggelaten. | Gebruik een fallback‑hyperlink of een content‑control als je cloud‑compatibiliteit nodig hebt. |
| **Verschillende DPI‑instellingen** | De rechthoek‑grootte kan groter of kleiner lijken op hoge‑DPI‑schermen. | Gebruik `GraphicsUnit.Point` (de standaard) en test op gangbare DPI‑instellingen (96 dpi, 120 dpi). |
| **Meerdere knoppen** | De oproep `GetChildNodes(NodeType.Shape, true)[0]` haalt alleen het eerste shape op. | Loop door `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` en stel `Hidden` in voor elk shape dat je toevoegt. |
| **Legacy .doc‑formaat** | Sommige ActiveX‑eigenschappen gaan verloren bij opslaan als `.doc`. | Geef de voorkeur aan `.docx` tenzij je een strikte legacy‑vereiste hebt. |

**Pro tip:** Na het invoegen van de knop kun je via de Word‑UI een macro toewijzen aan de eigenschap `OnAction`. Hiermee kun je aangepast klik‑gedrag definiëren zonder extra C#‑code te schrijven.

## Veelgestelde vragen

* **Werkt dit met .NET Core?**  
  Ja. Aspose.Words for .NET is volledig compatibel met .NET 5, .NET 6 en later. Verwijs gewoon naar hetzelfde NuGet‑pakket.

* **Kan ik de knop‑bijschrift wijzigen nadat het document is gegenereerd?**  
  Het bijschrift dat in `InsertForms2OleControl` wordt ingesteld, wordt de standaard ontwerp‑tekst. Gebruikers kunnen het in Word bewerken, maar je kunt het ook programmatisch bijwerken via de OLE‑object‑eigenschappen met de `Shape.OleFormat`‑API.

* **Wat als ik een andere grootte voor de knop nodig heb?**  
  Pas de waarden van `RectangleF` aan. De eerste twee parameters zijn de X‑ en Y‑coördinaten; de laatste twee zijn breedte en hoogte in punten (1 pt = 1/72 inch).

## Conclusie

Je weet nu hoe je **Word‑document C#** kunt **programmeer­matig een opdrachtknop toevoegen** met Aspose.Words. De tutorial behandelde het initialiseren van het document, het invoegen van een ActiveX‑knop, het verbergen tot runtime, en het opslaan van het uiteindelijke bestand. Met deze bouwblokken kun je interactieve besturingselementen in elke Word‑sjabloon die je genereert, insluiten.

Vervolgens kun je gerelateerde onderwerpen verkennen zoals **hoe een ActiveX‑knop‑event‑handling** toe te voegen, **maak opdrachtknop‑Word‑styling** met VBA, en **programmeer­matig een opdrachtknop** aan bestaande documenten. Het uitbreiden van dit patroon naar selectievakjes, keuzelijsten of aangepaste OLE‑objecten volgt dezelfde stappen — verander alleen de enum‑waarde `Forms2OleControlType`.

Begin met experimenteren: vervang het bijschrift, pas de positie aan, of koppel meerdere controls aan elkaar. Hoe meer je oefent, hoe vloeiender je wordt in het leveren van rijke, interactieve Word‑documenten vanuit C#. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Hoe een opdrachtknop programmatisch toe te voegen in een Word‑document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Hoe een ActiveX‑knop toe te voegen in een Word‑document met Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Maak Word‑document met ActiveX‑knop – C#‑gids](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}