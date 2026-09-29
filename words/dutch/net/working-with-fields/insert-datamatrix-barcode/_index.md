---
title: Voeg DataMatrix-barcode in Word-document in met Aspose.Words for .NET
weight: 210
limit:
description: Voeg programmatisch een DataMatrix-barcode toe aan een Word-document met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Voeg programmatisch een DataMatrix-barcode toe aan een Word-document
    met Aspose.Words for .NET.
  headline: Voeg DataMatrix-barcode in Word-document in met Aspose.Words for .NET
  type: TechArticle
- description: Voeg programmatisch een DataMatrix-barcode toe aan een Word-document
    met Aspose.Words for .NET.
  name: Voeg DataMatrix-barcode in Word-document in met Aspose.Words for .NET
  steps:
  - name: Doe een nieuw leeg Word-document en een DocumentBuilder om het te bewerken.
    text: Doe een nieuw leeg Word-document en een DocumentBuilder om het te bewerken.
  - name: Voeg een DISPLAYBARCODE-veld in op de huidige cursorpositie, waardoor een
      veldplaceholder aan het document wordt toegevoegd.
    text: Voeg een DISPLAYBARCODE-veld in op de huidige cursorpositie, waardoor een
      veldplaceholder aan het document wordt toegevoegd.
  - name: Stel de BarcodeType van het veld in op DataMatrix en geef de te coderen
      gegevensreeks op.
    text: Stel de BarcodeType van het veld in op DataMatrix en geef de te coderen
      gegevensreeks op.
  - name: Definieer optioneel de achtergrond- en voorgrondkleuren van de barcode.
    text: Definieer optioneel de achtergrond- en voorgrondkleuren van de barcode.
  - name: Roep UpdateFields aan op het document om de barcode-afbeelding binnen het
      veld te renderen.
    text: Roep UpdateFields aan op het document om de barcode-afbeelding binnen het
      veld te renderen.
  - name: Sla het document op als een .docx-bestand.
    text: Sla het document op als een .docx-bestand.
  type: HowTo
- questions:
  - answer: Het veld wordt ingevoegd, maar `document.UpdateFields()` laat de barcode
      leeg en Aspose.Words zal een `FieldException` werpen die een ongeldige barcode‑type
      aangeeft.
    question: Wat gebeurt er als ik een niet-ondersteunde waarde toewijs aan `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` rendert de barcode‑afbeeldingen, dus je kunt meerdere
      `FieldDisplayBarcode`‑objecten invoegen en `document.UpdateFields()` één keer
      aan het einde aanroepen om ze allemaal te renderen.'
    question: Moet ik `document.UpdateFields()` na elke barcode‑invoeging aanroepen,
      of kan ik één keer bijwerken nadat alle velden zijn toegevoegd?
  - answer: Beide eigenschappen verwachten een hexadecimale RGB‑string voorafgegaan
      door `0x` (bijv. "0xFF0000" voor rood); elk ander formaat wordt genegeerd en
      de standaardkleuren worden gebruikt.
    question: In welk formaat moeten de kleur‑strings staan voor `BackgroundColor`
      en `ForegroundColor`?
  - answer: Ja—stel simpelweg `displayBarcodeField.BarcodeValue` in op een nieuwe
      string en roep `document.UpdateFields()` opnieuw aan om de gerenderde afbeelding
      te vernieuwen.
    question: Kan ik de barcode‑payload wijzigen nadat het veld is ingevoegd?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Voeg een DataMatrix-barcode in met Aspose.Words
og_description: Leer hoe je een DataMatrix-barcode aan een Word-bestand toevoegt in slechts een paar regels .NET-code.
og_image_alt: Gids die laat zien hoe je een DataMatrix-barcode invoegt en rendert in een Word-document met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg DataMatrix-barcode in Word-document in met Aspose.Words
Met Aspose.Words for .NET kun je programmatisch een DataMatrix-barcode aan een Word-document toevoegen. Deze tutorial laat zien hoe je een nieuw document maakt, een DISPLAYBARCODE-veld invoegt, het type instelt op DataMatrix, en de barcode-afbeelding rendert met behulp van de Document- en DocumentBuilder-klassen. Volg de stappen om een afdrukbare barcode direct in je .docx-bestand te genereren.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Wat gebeurt er als ik een niet-ondersteunde waarde toewijs aan `displayBarcodeField.BarcodeType`?**  
A: Het veld wordt ingevoegd, maar `document.UpdateFields()` laat de barcode leeg en Aspose.Words zal een `FieldException` werpen die een ongeldige barcode‑type aangeeft.

**Q: Moet ik `document.UpdateFields()` na elke barcode‑invoeging aanroepen, of kan ik één keer bijwerken nadat alle velden zijn toegevoegd?**  
A: `UpdateFields()` rendert de barcode‑afbeeldingen, dus je kunt meerdere `FieldDisplayBarcode`‑objecten invoegen en `document.UpdateFields()` één keer aan het einde aanroepen om ze allemaal te renderen.

**Q: In welk formaat moeten de kleur‑strings staan voor `BackgroundColor` en `ForegroundColor`?**  
A: Beide eigenschappen verwachten een hexadecimale RGB‑string voorafgegaan door `0x` (bijv. "0xFF0000" voor rood); elk ander formaat wordt genegeerd en de standaardkleuren worden gebruikt.

**Q: Kan ik de barcode‑payload wijzigen nadat het veld is ingevoegd?**  
A: Ja—stel simpelweg `displayBarcodeField.BarcodeValue` in op een nieuwe string en roep `document.UpdateFields()` opnieuw aan om de gerenderde afbeelding te vernieuwen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}