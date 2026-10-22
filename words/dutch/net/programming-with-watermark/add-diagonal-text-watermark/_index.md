---
title: Maak een diagonale tekstwatermark met aangepast lettertype in een Word‑document met Aspose.Words for .NET
weight: 210
limit:
description: Stap‑voor‑stap code om een diagonale tekstwatermark met aangepast lettertype toe te voegen aan een Word‑.docx met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Stap‑voor‑stap code om een diagonale tekstwatermark met aangepast lettertype
    toe te voegen aan een Word‑.docx met Aspose.Words for .NET.
  headline: Maak een diagonale tekstwatermark met aangepast lettertype in een Word‑document
    met Aspose.Words for .NET
  type: TechArticle
- description: Stap‑voor‑stap code om een diagonale tekstwatermark met aangepast lettertype
    toe te voegen aan een Word‑.docx met Aspose.Words for .NET.
  name: Maak een diagonale tekstwatermark met aangepast lettertype in een Word‑document
    met Aspose.Words for .NET
  steps:
  - name: Maak een nieuwe lege Word‑documentinstantie met de naam `document`.
    text: Maak een nieuwe lege Word‑documentinstantie met de naam `document`.
  - name: Configureer `watermarkSettings` met het lettertype Arial 48 pt grijs, een
      diagonale lay-out en ondoorzichtige weergave.
    text: Configureer `watermarkSettings` met het lettertype Arial 48 pt grijs, een
      diagonale lay-out en ondoorzichtige weergave.
  - name: Pas de tekstwatermark "Private" toe op `document` met behulp van de eerder
      gedefinieerde instellingen.
    text: Pas de tekstwatermark "Private" toe op `document` met behulp van de eerder
      gedefinieerde instellingen.
  - name: Definieer het bestandspad waar het watergemarkeerde document wordt opgeslagen.
    text: Definieer het bestandspad waar het watergemarkeerde document wordt opgeslagen.
  - name: Sla het gewijzigde `document` op naar het opgegeven pad als een .docx‑bestand.
    text: Sla het gewijzigde `document` op naar het opgegeven pad als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` bepaalt of de watermark met gedeeltelijke doorzichtigheid
      wordt weergegeven; als je het op `false` zet, wordt de watermark volledig ondoorzichtig,
      terwijl `true` een standaard halfdoorzichtig effect toepast.'
    question: Wat regelt de **IsSemitrasparent**‑vlag in `TextWatermarkOptions`?
  - answer: Ja—stel de eigenschap `Layout` in op `WatermarkLayout.Horizontal` (of
      een andere enum‑waarde) voordat je `document.Watermark.SetText` aanroept.
    question: Kan ik de oriëntatie van de watermark wijzigen naar horizontaal in plaats
      van diagonaal?
  - answer: Word zal terugvallen op het standaardlettertype voor de watermark, zodat
      de tekst nog steeds verschijnt, maar er anders uit kan zien dan de beoogde stijl.
    question: Wat gebeurt er als de opgegeven `FontFamily` (bijv. "Arial") niet is
      geïnstalleerd op de doelmachine?
  - answer: Laad het bestaande bestand met `Document document = new Document("Existing.docx");`
      configureer vervolgens `TextWatermarkOptions` en roep `document.Watermark.SetText`
      aan zoals getoond.
    question: Is het mogelijk om een watermark toe te voegen aan een bestaand `.docx`‑bestand
      in plaats van een nieuw bestand te maken?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Voeg een diagonale tekstwatermark met aangepast lettertype toe
og_description: Leer binnen enkele minuten een scheve tekstwatermark met je eigen lettertype in een Word‑bestand in te voegen.
og_image_alt: Handleiding die laat zien hoe je een diagonale tekstwatermark met aangepast lettertype toevoegt aan een Word‑document met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Maak een diagonale tekstwatermark met aangepast lettertype in een Word‑document met Aspose.Words
Deze tutorial leidt je stap voor stap door het maken van een nieuw Word‑document, het configureren van een diagonale tekstwatermark met de door jou gekozen lettertype‑instellingen, het toepassen ervan via de Document.Watermark.SetText‑API, en het opslaan van het resultaat als een .docx‑bestand. Aan het einde heb je een professioneel watergemarkeerd document dat je merk of eigendom toont. De stap‑voor‑stap code staat klaar om te kopiëren in elk .NET‑project.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Wat regelt de **IsSemitrasparent**‑vlag in `TextWatermarkOptions`?**  
A: `IsSemitrasparent` bepaalt of de watermark met gedeeltelijke doorzichtigheid wordt weergegeven; als je het op `false` zet, wordt de watermark volledig ondoorzichtig, terwijl `true` een standaard halfdoorzichtig effect toepast.

**Q: Kan ik de oriëntatie van de watermark wijzigen naar horizontaal in plaats van diagonaal?**  
A: Ja—stel de eigenschap `Layout` in op `WatermarkLayout.Horizontal` (of een andere enum‑waarde) voordat je `document.Watermark.SetText` aanroept.

**Q: Wat gebeurt er als de opgegeven `FontFamily` (bijv. "Arial") niet is geïnstalleerd op de doelmachine?**  
A: Word zal terugvallen op het standaardlettertype voor de watermark, zodat de tekst nog steeds verschijnt, maar er anders uit kan zien dan de beoogde stijl.

**Q: Is het mogelijk om een watermark toe te voegen aan een bestaand `.docx`‑bestand in plaats van een nieuw bestand te maken?**  
A: Laad het bestaande bestand met `Document document = new Document("Existing.docx");` configureer vervolgens `TextWatermarkOptions` en roep `document.Watermark.SetText` aan zoals getoond.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}