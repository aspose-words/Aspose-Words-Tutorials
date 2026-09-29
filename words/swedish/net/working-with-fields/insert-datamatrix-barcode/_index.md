---
title: Infoga DataMatrix‑streckkod i Word‑dokument med Aspose.Words for .NET
weight: 210
limit:
description: Lägg till en DataMatrix‑streckkod i ett Word‑dokument programatiskt med Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Lägg till en DataMatrix‑streckkod i ett Word‑dokument programatiskt
    med Aspose.Words for .NET.
  headline: Infoga DataMatrix‑streckkod i Word‑dokument med Aspose.Words for .NET
  type: TechArticle
- description: Lägg till en DataMatrix‑streckkod i ett Word‑dokument programatiskt
    med Aspose.Words for .NET.
  name: Infoga DataMatrix‑streckkod i Word‑dokument med Aspose.Words for .NET
  steps:
  - name: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
    text: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
  - name: Infoga ett DISPLAYBARCODE‑fält på den aktuella markörpositionen, vilket
      lägger till en fältplatshållare i dokumentet.
    text: Infoga ett DISPLAYBARCODE‑fält på den aktuella markörpositionen, vilket
      lägger till en fältplatshållare i dokumentet.
  - name: Ställ in fältets BarcodeType till DataMatrix och ange datasträngen som ska
      kodas.
    text: Ställ in fältets BarcodeType till DataMatrix och ange datasträngen som ska
      kodas.
  - name: Definiera eventuellt streckkodens bakgrunds- och förgrundsfärger.
    text: Definiera eventuellt streckkodens bakgrunds- och förgrundsfärger.
  - name: Anropa UpdateFields på dokumentet för att rendera streckkodbilden i fältet.
    text: Anropa UpdateFields på dokumentet för att rendera streckkodbilden i fältet.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: Fältet kommer att infogas, men `document.UpdateFields()` lämnar streckkoden
      tom och Aspose.Words kastar ett `FieldException` som indikerar en ogiltig streckkodstyp.
    question: Vad händer om jag tilldelar ett ej‑stödd värde till `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` renderar streckkodsbilderna, så du kan infoga flera
      `FieldDisplayBarcode`‑objekt och anropa `document.UpdateFields()` en enda gång
      i slutet för att rendera dem alla.'
    question: Behöver jag anropa `document.UpdateFields()` efter varje streckkodsinläggning,
      eller kan jag uppdatera en gång efter att alla fält har lagts till?
  - answer: Båda egenskaperna förväntar sig en hexadecimalt RGB‑sträng med prefixet
      `0x` (t.ex. "0xFF0000" för röd); alla andra format ignoreras och standardfärgerna
      används.
    question: Vilket format ska färgsträngarna ha för `BackgroundColor` och `ForegroundColor`?
  - answer: Ja – sätt helt enkelt `displayBarcodeField.BarcodeValue` till en ny sträng
      och anropa `document.UpdateFields()` igen för att uppdatera den renderade bilden.
    question: Kan jag ändra streckkodens data efter att fältet har infogats?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Infoga en DataMatrix‑streckkod med Aspose.Words
og_description: Lär dig hur du lägger till en DataMatrix‑streckkod i en Word‑fil med bara några rader .NET‑kod.
og_image_alt: Guide som visar hur du infogar och renderar en DataMatrix‑streckkod i ett Word‑dokument med Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga DataMatrix‑streckkod i Word‑dokument med Aspose.Words
Med Aspose.Words for .NET kan du programatiskt lägga till en DataMatrix‑streckkod i ett Word‑dokument. Den här handledningen visar hur du skapar ett nytt dokument, infogar ett DISPLAYBARCODE‑fält, ställer in dess typ till DataMatrix och renderar streckkodbilden med klasserna Document och DocumentBuilder. Följ stegen för att generera en utskrivbar streckkod direkt i din .docx‑fil.

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

**Q: Vad händer om jag tilldelar ett ej‑stödd värde till `displayBarcodeField.BarcodeType`?**  
A: Fältet kommer att infogas, men `document.UpdateFields()` lämnar streckkoden tom och Aspose.Words kastar ett `FieldException` som indikerar en ogiltig streckkodstyp.

**Q: Behöver jag anropa `document.UpdateFields()` efter varje streckkodsinläggning, eller kan jag uppdatera en gång efter att alla fält har lagts till?**  
A: `UpdateFields()` renderar streckkodsbilderna, så du kan infoga flera `FieldDisplayBarcode`‑objekt och anropa `document.UpdateFields()` en enda gång i slutet för att rendera dem alla.

**Q: Vilket format ska färgsträngarna ha för `BackgroundColor` och `ForegroundColor`?**  
A: Båda egenskaperna förväntar sig en hexadecimalt RGB‑sträng med prefixet `0x` (t.ex. "0xFF0000" för röd); alla andra format ignoreras och standardfärgerna används.

**Q: Kan jag ändra streckkodens data efter att fältet har infogats?**  
A: Ja – sätt helt enkelt `displayBarcodeField.BarcodeValue` till en ny sträng och anropa `document.UpdateFields()` igen för att uppdatera den renderade bilden.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}