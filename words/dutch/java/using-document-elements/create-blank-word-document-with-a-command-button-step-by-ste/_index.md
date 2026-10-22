---
category: general
date: 2026-08-04
description: Maak een leeg Word‑document en voeg een opdrachtknop toe met Aspose.Words.
  Leer hoe je de knopgrootte instelt en een klikbare knop toevoegt in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: nl
lastmod: 2026-08-04
og_description: Maak een leeg Word‑document met Aspose.Words en voeg een opdrachtknop
  toe. Deze gids laat zien hoe je de knopgrootte instelt, een klikbare knop toevoegt
  en het bestand opslaat.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Maak een leeg Word‑document en voeg een opdrachtknop toe – volledige C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een leeg Word‑document met een opdrachtknop – stapsgewijze handleiding
url: /nl/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met een opdrachtknop – stap‑voor‑stap gids

Als je een **leeg Word‑document maken** moet die een interactieve knop bevat, laat deze tutorial je precies zien hoe je dit doet met Aspose.Words for .NET. Je leert hoe je een **command button invoegen**, het uiterlijk kunt aanpassen en de knop klikbaar kunt maken — alles in een paar regels C#.

De gids behandelt alles van projectinstelling tot het opslaan van het uiteindelijke bestand, zodat je de volledige oplossing kunt kopiëren‑plakken in je eigen applicatie. Onderweg leggen we ook uit hoe je een **klikbare knop toevoegen**, **knopgrootte instellen** en **command button maken** programmatically.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd.
* Visual Studio 2022 (of een IDE die .NET ondersteunt).
* Aspose.Words for .NET NuGet‑pakket (`Aspose.Words` versie 23.12 of nieuwer).
* Basiskennis van C# en objectgeoriënteerd programmeren.

Er zijn geen extra Office‑interop‑assemblies nodig omdat Aspose.Words volledig onafhankelijk van Microsoft Word werkt.

## Stap 1: .NET‑project instellen

Maak een console‑applicatie die de Word‑automatiseringscode host.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Dit commando maakt een nieuwe map `WordButtonDemo` met een kant‑klaar `Program.cs` en voegt de Aspose.Words‑bibliotheek toe.

## Stap 2: Leeg Word‑document maken

De eerste handeling is om een **leeg Word‑document maken**. Aspose.Words biedt een `Document`‑klasse die een leeg Word‑bestand direct beschikbaar maakt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Het maken van een leeg document geeft je een schoon canvas waarop je alinea’s, tabellen of, in dit geval, een OLE‑opdrachtknop kunt toevoegen.

## Stap 3: DocumentBuilder initialiseren

`DocumentBuilder` is de helper waarmee je inhoud in het document kunt invoegen. Je moet het koppelen aan het document dat je zojuist hebt aangemaakt.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder houdt de huidige cursorpositie bij, zodat elke volgende invoeging precies gebeurt waar je wilt.

## Stap 4: Command button invoegen

Nu **command button invoegen** (een OLE `Forms2OleControl`) in het document. De methode `InsertForms2OleControl` vereist drie argumenten:

1. De ProgID van de OLE‑control – `"CommandButton"` voor een standaardknop.
2. Een `Rectangle` die de **knopgrootte instellen** en positie definieert.
3. Het bijschrift dat op de knop verschijnt.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Wanneer het document in Word wordt geopend, gedraagt de knop zich als elke native form‑control — je kunt erop klikken en Word zal de gekoppelde macro uitvoeren (indien aanwezig). Dit voldoet aan de **klikbare knop toevoegen**‑vereiste.

### Waarom Forms2OleControl gebruiken?

`Forms2OleControl` embed een OLE‑object direct in het DOCX‑bestand, waardoor de eigenschappen van de control behouden blijven zonder de Word‑Interop‑assembly nodig te hebben. Het is de meest betrouwbare manier om een **command button maken** die werkt over verschillende Word‑versies.

## Stap 5: De knop aanpassen (optioneel)

Je wilt misschien de **knopgrootte instellen** nauwkeuriger of extra eigenschappen wijzigen, zoals het lettertype of de achtergrondkleur. Aspose.Words maakt het onderliggende OLE‑object toegankelijk, waardoor verdere aanpassingen mogelijk zijn.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Als je een andere grootte nodig hebt, pas dan simpelweg de `Rectangle`‑waarden in Stap 4 aan. De coördinaten worden gemeten in points (1 pt = 1/72 inch), dus `120` komt ongeveer overeen met 1,67 inch breed.

## Stap 6: Document opslaan

Schrijf tenslotte het document naar schijf. Het resulterende bestand bevat een **leeg Word‑document maken** met een volledig functionele command button.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Wanneer je `CommandButtonDemo.docx` opent in Microsoft Word, zie je een knop met de tekst “Click Me”. Het klikken op de knop toont het standaard macro‑dialoogvenster, tenzij je een aangepaste macro koppelt.

## Volledige broncode

Hieronder staat het volledige programma dat je kunt kopiëren naar `Program.cs`. Het bevat alle hierboven beschreven stappen en compileert zonder aanpassingen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Verwacht resultaat

Het uitvoeren van het programma produceert `CommandButtonDemo.docx`. Het openen van het bestand in Word toont:

* Een enkele pagina met een knop gelabeld **Click Me**.
* De knop respecteert de **knopgrootte instellen** (120 × 30 points).
* Het klikken op de knop activeert Word’s standaard command‑button‑gedrag, wat bevestigt dat de **klikbare knop toevoegen**‑operatie geslaagd is.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Werkt dit met .doc‑bestanden?** | Ja. Verander de bestandsextensie in `doc.Save("file.doc")`. De OLE‑control wordt ook opgeslagen in het legacy‑binaire formaat. |
| **Wat als ik meerdere knoppen nodig heb?** | Roep `InsertForms2OleControl` herhaaldelijk aan en pas de `Rectangle` voor elke nieuwe knop aan om overlapping te voorkomen. |
| **Kan ik een macro aan de knop koppelen?** | De knop zelf bevat geen macro‑code. Je moet handmatig of via de `Document`‑object‑`Modules`‑collectie een VBA‑macro aan het document toevoegen. |
| **Is de knop zichtbaar bij PDF‑export?** | Bij het exporteren van de DOCX naar PDF met Aspose.Words wordt de knop gerenderd als een statisch beeld, niet als een interactieve control. |
| **Welke Word‑versies worden ondersteund?** | De OLE‑command button werkt in Word 2007 en later, omdat het de standaard Forms2.0‑specificatie volgt. |

## Conclusie

Je weet nu hoe je een **leeg Word‑document maken**, **command button invoegen**, **klikbare knop toevoegen** en **knopgrootte instellen** kunt doen met Aspose.Words for .NET. Het volledige voorbeeld demonstreert de **command button maken**‑workflow van begin tot eind, en biedt een solide basis voor meer geavanceerde Word‑automatiseringstaken.

## Volgende stappen

* Verken andere OLE‑controls (bijv. `CheckBox`, `ListBox`) door de ProgID in `InsertForms2OleControl` te wijzigen.
* Combineer de knop met een VBA‑macro om aangepaste acties uit te voeren wanneer de gebruiker erop klikt.
* Gebruik Aspose.Words’ `DocumentBuilder` om extra inhoud toe te voegen, zoals tabellen, afbeeldingen of voetnoten, vóór het invoegen van de knop.
* Experimenteer met **knopgrootte instellen**‑waarden om ze af te stemmen op de lay‑outvereisten van je document.

Veel programmeerplezier, en geniet van het bouwen van rijkere Word‑documenten met interactieve controls!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}