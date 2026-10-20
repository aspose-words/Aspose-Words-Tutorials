---
category: general
date: 2026-07-19
description: Maak een Word-document met Aspose.Words C# en leer hoe je een ActiveX-opdrachtknop
  toevoegt, de knopgrootte instelt en de knop via code invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: nl
lastmod: 2026-07-19
og_description: Maak een Word‑document met Aspose.Words C# en voeg binnen enkele seconden
  een ActiveX‑opdrachtknop in. Volg de stapsgewijze handleiding om de knopgrootte
  in te stellen en de knop eenvoudig in te voegen.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Maak Word-document met ActiveX-knop – C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Maak Word-document met ActiveX-knop – C#-gids
url: /nl/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document met ActiveX-knop – Complete C#-gids

Heb je je ooit afgevraagd hoe je een **create word document** maakt dat een functionele ActiveX-knop bevat? Misschien automatiseer je een rapport en heb je een klikbare “Approve”-besturingselement nodig direct in het bestand. In deze tutorial lopen we precies dat stap voor stap door—met Aspose.Words voor .NET om een ActiveX-opdrachtknop toe te voegen, de grootte in te stellen en deze op de gewenste plaats in te voegen.  

Als je je ooit afvroeg *how to add activex* besturingselementen toe te voegen zonder Word handmatig te openen, ben je op de juiste plek. Aan het einde heb je een uitvoerbaar voorbeeld, een duidelijke uitleg van elke stap, en tips voor het omgaan met veelvoorkomende valkuilen.

## Wat je zult leren

- Hoe Aspose.Words in een C#-project in te stellen  
- De exacte code om een **create word document** te maken en een ActiveX-opdrachtknop in te sluiten  
- Manieren om **set button size** in te stellen en de bijschrift en naam aan te passen  
- De juiste methode om **insert command button** toe te voegen en **how to insert button** op elke locatie in het document  
- Edge‑case overwegingen (Word-versie, platformbeperkingen, beveiligingswaarschuwingen)

### Vereisten

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.7+).  
- Een geldige Aspose.Words for .NET-licentie (of een gratis evaluatiesleutel).  
- Visual Studio 2022 (of elke IDE die je wilt).  
- Basiskennis van C# en objectgeoriënteerd programmeren.

Geen andere externe bibliotheken zijn vereist.

---

## Stap 1: Word-document maken – Projectinstelling

Voordat we een **insert command button** kunnen toevoegen, hebben we een leeg Word‑bestand nodig om mee te werken. Deze stap toont ook het klassieke “create word document”-patroon met Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Waarom dit belangrijk is:** `Document` vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` de huidige cursorpositie bijhoudt. Alle volgende invoegingen (inclusief onze ActiveX‑controle) gebeuren relatief ten opzichte van deze builder.

---

## Stap 2: Hoe ActiveX toe te voegen – Bouw de CommandButton‑controle

Nu het document bestaat, gaan we de **how to add activex**-deel aanpakken. Aspose.Words biedt de `Forms2OleControl`‑klasse voor ActiveX‑objecten. Hier maken we een commandobutton en configureren we zijn eigenschappen, inclusief de **set button size**‑vereiste.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** De grootte wordt gemeten in punten (1 punt = 1/72 inch). Pas de waarden aan om bij je lay-out te passen; voor een typische werkbalkknop werkt 120 × 30 goed.

---

## Stap 3: CommandButton invoegen – De kern van **Insert Command Button**

Met de controle klaar, voegen we nu **insert command button** toe aan het document op de huidige locatie van de builder. Je kunt de builder overal naartoe verplaatsen (bijv. na een alinea) voordat je deze methode aanroept.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Als je **how to insert button** op een specifiek bladwijzer wilt plaatsen, verplaats dan eerst de builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Wat er achter de schermen gebeurt?** Aspose.Words schrijft de benodigde OLE‑objectstreams naar het .docx‑pakket, zodat Word de knop kan weergeven zonder extra macro's.

---

## Stap 4: Document opslaan – Afronden van de **Create Word Document**-cyclus

De laatste stap is eenvoudig: het bestand naar schijf schrijven. Hiermee voltooid je de round‑trip van **create word document**, het embedden van de ActiveX en het opslaan.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Open het resulterende bestand in Microsoft Word (alleen Windows). Je zou een klikbare knop moeten zien met het label “Click Me”. Klikken zal de standaardactie voor een CommandButton activeren—er gebeurt niets tenzij je VBA‑code toevoegt, maar de controle is volledig functioneel.

> **Verwachte output:** Een .docx‑bestand met één pagina, een knop gecentreerd op het invoegpunt, met een grootte van 120 × 30 pt, gelabeld “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Afbeeldings‑alt‑tekst:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## Stap 5: Edge Cases, beveiliging en best practices

### Platformbeperkingen
- ActiveX‑besturingselementen werken alleen in de Windows‑versie van Word. Als je publiek macOS‑ of Word Online‑gebruikers omvat, verschijnt de knop als een statisch beeld.
- Sommige bedrijfsomgevingen schakelen ActiveX uit om veiligheidsredenen; je moet het document mogelijk ondertekenen of gebruikers informeren om inhoud in te schakelen.

### VBA‑interactie (optioneel)
Als je wilt dat de knop een macro uitvoert, moet je na het opslaan een VBA‑project aan het document toevoegen. Aspose.Words genereert geen VBA‑code automatisch, maar je kunt de `Document.VbaProject`‑API gebruiken om deze in te voegen.

### Naamconflicten
Geef elke controle altijd een unieke `Name`. Het hergebruiken van dezelfde naam kan runtime‑fouten veroorzaken wanneer Word de controle probeert te vinden.

### Prestatietip
Bij het invoegen van veel controles, hergebruik één `DocumentBuilder`‑instantie en vermijd het aanroepen van `doc.Save` binnen een lus. Batch de invoegingen en sla één keer op aan het einde.

## Volledig werkend voorbeeld

Alles samenvoegend, hier is een compleet, kant‑klaar programma om te kopiëren en plakken:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Voer het programma uit, open het opgeslagen bestand, en je ziet de knop precies op de positie waar de builder stond.

## Conclusie

We hebben zojuist een **create word document** vanaf nul gemaakt, hebben **how to add activex** geleerd door een `Forms2OleControl` te configureren, de **set button size**‑eigenschappen onder de knie gekregen, en de juiste manier gedemonstreerd om **insert command button** toe te voegen en **how to insert button** op elke plek in het bestand.  

Vanuit één codevoorbeeld heb je nu een solide basis voor uitgebreidere Word‑automatisering—of je nu sjablonen met interactieve formulieren bouwt, contracten genereert die gebruikersbevestiging vereisen, of simpelweg een paar handige besturingselementen door een rapport verspreidt.

### Wat is het volgende?

- **Style the button** – wijzig lettertypen, kleuren, of voeg een afbeelding als achtergrond toe.  
- **Attach VBA macros** – laat de knop berekeningen uitvoeren of externe programma's starten.  
- **Combine with other controls** – selectievakjes, lijstvakken, of zelfs ingebedde Excel‑bladen.  

Voel je vrij om te experimenteren, en als je een probleem tegenkomt, laat dan een reactie achter. Veel plezier met coderen, en geniet van het automatiseren van Word met Aspose.Words!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende codevoorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word-document met Aspose.Words voor .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Maak groepsvorm in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Voeg inline afbeelding in Word-document in met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}