---
title: Hyperlink‑opmerking toevoegen en exporteren als PDF‑annotatie met Aspose.Words for .NET
weight: 110
limit:
description: Leer hoe je een hyperlink‑opmerking toevoegt in een Word‑bestand en deze exporteert als een PDF‑annotatie met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je een hyperlink‑opmerking toevoegt in een Word‑bestand en
    deze exporteert als een PDF‑annotatie met Aspose.Words for .NET.
  headline: Hyperlink‑opmerking toevoegen en exporteren als PDF‑annotatie met Aspose.Words
    for .NET
  type: TechArticle
- description: Leer hoe je een hyperlink‑opmerking toevoegt in een Word‑bestand en
    deze exporteert als een PDF‑annotatie met Aspose.Words for .NET.
  name: Hyperlink‑opmerking toevoegen en exporteren als PDF‑annotatie met Aspose.Words
    for .NET
  steps:
  - name: Doe een nieuw leeg Document‑object aan en een DocumentBuilder om ermee te
      werken.
    text: Doe een nieuw leeg Document‑object aan en een DocumentBuilder om ermee te
      werken.
  - name: Schrijf een regel zichtbare tekst die de komende opmerking zal bevatten.
    text: Schrijf een regel zichtbare tekst die de komende opmerking zal bevatten.
  - name: Maak een Comment aan, geschreven door Jane Doe, en koppel deze aan de eerste
      alinea van het document.
    text: Maak een Comment aan, geschreven door Jane Doe, en koppel deze aan de eerste
      alinea van het document.
  - name: Voeg binnen de opmerking een alinea toe en plaats een blauwe, onderstreepte
      hyperlink naar de Aspose.Words Library‑website.
    text: Voeg binnen de opmerking een alinea toe en plaats een blauwe, onderstreepte
      hyperlink naar de Aspose.Words Library‑website.
  - name: Configureer het document om opmerkingen weer te geven als PDF‑annotaties
      en ververs de lay-out.
    text: Configureer het document om opmerkingen weer te geven als PDF‑annotaties
      en ververs de lay-out.
  - name: Maak een map "Output" aan in de huidige directory om de gegenereerde PDF
      op te slaan.
    text: Maak een map "Output" aan in de huidige directory om de gegenereerde PDF
      op te slaan.
  - name: Sla het voorbereide document op als een PDF‑bestand met behulp van PdfSaveOptions.
    text: Sla het voorbereide document op als een PDF‑bestand met behulp van PdfSaveOptions.
  - name: Controleer of het PDF‑bestand bestaat en gegevens bevat, en geef vervolgens
      het resultaat weer in de console.
    text: Controleer of het PDF‑bestand bestaat en gegevens bevat, en geef vervolgens
      het resultaat weer in de console.
  type: HowTo
- questions:
  - answer: De derde parameter van `InsertHyperlink` geeft aan of de link als een
      veld moet worden behandeld; door deze op `false` te zetten, wordt een gewone
      hyperlink ingevoegd die werkt in de PDF‑annotatie zonder een veldcode nodig
      te hebben.
    question: Wat regelt het derde argument (`false`) in `InsertHyperlink`?
  - answer: Stel `myDocument.LayoutOptions.CommentDisplayMode` in op `CommentDisplayMode.ShowInBalloons`
      vóór het aanroepen van `Save`; de PDF zal dan de opmerking bevatten als een
      reguliere Word‑opmerking in plaats van een annotatie.
    question: Hoe kan ik de opmerking laten verschijnen als een ballon in het Word‑document
      in plaats van als een PDF‑annotatie?
  - answer: Ja—elke `Comment` die je aan een alinea toevoegt kan zijn eigen `InsertHyperlink`‑aanroep
      bevatten, en alle hyperlinks worden bewaard als afzonderlijke PDF‑annotaties
      wanneer het document wordt opgeslagen.
    question: Als ik meer dan één opmerking toevoeg, werkt dan elke hyperlink in de
      geëxporteerde PDF?
  - answer: Open de gegenereerde PDF, zoek de opmerking‑annotatie (meestal weergegeven
      als een notitie‑icoon), klik erop om de opmerkingstekst te tonen, en klik vervolgens
      op de blauwe onderstreepte link; deze zou de doel‑URL in een webbrowser moeten
      openen.
    question: Hoe verifieer ik dat de hyperlink binnen de opmerking daadwerkelijk
      werkt nadat de PDF is gegenereerd?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Hyperlink‑opmerking invoegen & exporteren naar PDF
og_description: Leer hoe je een klikbare link in een Word‑opmerking embedt en deze omzet in een PDF‑annotatie.
og_image_alt: Gids die laat zien hoe je een opmerking met een klikbare hyperlink aan een Word‑document toevoegt en deze exporteert als een PDF‑annotatie met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hyperlink‑opmerking toevoegen en exporteren als PDF‑annotatie met Aspose.Words
In deze tutorial zie je hoe je een Word‑document maakt, een opmerking invoegt die een klikbare hyperlink naar een externe website bevat, die opmerking configureert zodat deze verschijnt als een PDF‑annotatie, het document exporteert naar PDF, en het resulterende PDF‑bestand verifieert. De stapsgewijze code stelt je in staat rijke, link‑geactiveerde opmerkingen toe te voegen en te behouden bij het converteren naar PDF, waardoor het eenvoudig is interactieve notities met lezers te delen.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wat regelt het derde argument (`false`) in `InsertHyperlink`?**  
A: De derde parameter van `InsertHyperlink` geeft aan of de link als een veld moet worden behandeld; door deze op `false` te zetten, wordt een gewone hyperlink ingevoegd die werkt in de PDF‑annotatie zonder een veldcode nodig te hebben.

**Q: Hoe kan ik de opmerking laten verschijnen als een ballon in het Word‑document in plaats van als een PDF‑annotatie?**  
A: Stel `myDocument.LayoutOptions.CommentDisplayMode` in op `CommentDisplayMode.ShowInBalloons` vóór het aanroepen van `Save`; de PDF zal dan de opmerking bevatten als een reguliere Word‑opmerking in plaats van een annotatie.

**Q: Als ik meer dan één opmerking toevoeg, werkt dan elke hyperlink in de geëxporteerde PDF?**  
A: Ja—elke `Comment` die je aan een alinea toevoegt kan zijn eigen `InsertHyperlink`‑aanroep bevatten, en alle hyperlinks worden bewaard als afzonderlijke PDF‑annotaties wanneer het document wordt opgeslagen.

**Q: Hoe verifieer ik dat de hyperlink binnen de opmerking daadwerkelijk werkt nadat de PDF is gegenereerd?**  
A: Open de gegenereerde PDF, zoek de opmerking‑annotatie (meestal weergegeven als een notitie‑icoon), klik erop om de opmerkingstekst te tonen, en klik vervolgens op de blauwe onderstreepte link; deze zou de doel‑URL in een webbrowser moeten openen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}