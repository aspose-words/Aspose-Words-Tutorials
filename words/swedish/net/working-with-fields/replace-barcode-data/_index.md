---
title: Byt ut streckkodsdata i Word-dokument med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig hur du infogar ett DISPLAYBARCODE-fält och ersätter dess datasträng med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Lär dig hur du infogar ett DISPLAYBARCODE-fält och ersätter dess datasträng
    med Aspose.Words för .NET.
  headline: Byt ut streckkodsdata i Word-dokument med Aspose.Words för .NET
  type: TechArticle
- description: Lär dig hur du infogar ett DISPLAYBARCODE-fält och ersätter dess datasträng
    med Aspose.Words för .NET.
  name: Byt ut streckkodsdata i Word-dokument med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document‑objekt och en DocumentBuilder för att konstruera
      dess innehåll.
    text: Skapa ett nytt Document‑objekt och en DocumentBuilder för att konstruera
      dess innehåll.
  - name: Infoga ett DISPLAYBARCODE-fält och ange dess typ, initiala värde och start-/stopptecken,
      lägg sedan till ett radbryt.
    text: Infoga ett DISPLAYBARCODE-fält och ange dess typ, initiala värde och start-/stopptecken,
      lägg sedan till ett radbryt.
  - name: Anropa UpdateFields för att rendera det nyinfogade streckkodsfältet.
    text: Anropa UpdateFields för att rendera det nyinfogade streckkodsfältet.
  - name: Använd Find/Replace‑motorn för att ändra streckkodens datasträng från INIT123
      till NEWVAL.
    text: Använd Find/Replace‑motorn för att ändra streckkodens datasträng från INIT123
      till NEWVAL.
  - name: Uppdatera fälten igen så att DISPLAYBARCODE återspeglar den nya datasträngen.
    text: Uppdatera fälten igen så att DISPLAYBARCODE återspeglar den nya datasträngen.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: '`Range.Replace` ändrar bara den underliggande texten; DISPLAYBARCODE-fältets
      visuella resultat genereras om igen endast när `UpdateFields()` anropas, så
      den nya streckkoden visas i det sparade dokumentet.'
    question: Varför måste jag anropa `myDocument.UpdateFields()` efter att ha utfört
      `Range.Replace`?
  - answer: Ja, `Document.Range.Replace` arbetar på hela dokumentets område, så all
      matchande text någon annanstans kommer att ersättas om du inte begränsar sökningen
      med `FindReplaceOptions` (t.ex. genom att ange ett specifikt `Range` eller använda
      `.MatchWholeWord`).
    question: Kommer anropet `Replace(\"INIT123\", \"NEWVAL\", ...)` att påverka andra
      förekomster av \"INIT123\" utanför streckkodsfältet?
  - answer: Du kan tilldela ett nytt värde till `displayBarcode.BarcodeType` när som
      helst, men du måste anropa `myDocument.UpdateFields()` därefter för att förändringen
      ska återspeglas i den renderade streckkoden.
    question: Kan jag ändra streckkodstypen (t.ex. från CODE39 till QR) efter att
      fältet har infogats?
  - answer: När `AddStartStopChar` är true lägger Aspose.Words automatiskt till de
      nödvändiga start-/stopptecknen (`*`) runt streckkodsvärdet, vilket krävs av
      CODE39; sätt den till false om din symbologi inte behöver dem.
    question: Vad gör egenskapen `AddStartStopChar = true` för CODE39-streckkoder?
  - answer: Inga speciella inställningar krävs för en enkel exakt matchning, men du
      kan aktivera `.MatchCase` eller `.MatchWholeWord` i `FindReplaceOptions` för
      att undvika oavsiktliga partiella ersättningar.
    question: Behöver jag konfigurera några speciella alternativ i `FindReplaceOptions`
      för att säkert ersätta streckkodsvärdet?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Uppdatera ett streckkodsfält i Word med Aspose.Words
og_description: Byt ut en streckkods datasträng och uppdatera den omedelbart i en Word‑fil.
og_image_alt: Skärmbild som visar ett Word-dokument med ett DISPLAYBARCODE-fält före och efter databytes med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Byt ut streckkodsdata i Word-dokument med Aspose.Words för .NET
Den här handledningen demonstrerar hur man infogar ett DISPLAYBARCODE-fält i ett Word-dokument och sedan använder Document.Range.Replace‑metoden för att ändra streckkodens datasträng. Efter ersättningen uppdateras fältet så att den uppdaterade streckkoden visas i den sparade filen. Följ stegen för att se streckkodsuppdateringen omedelbart utan att återskapa fältet.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Varför måste jag anropa `myDocument.UpdateFields()` efter att ha utfört `Range.Replace`?**  
A: `Range.Replace` ändrar bara den underliggande texten; DISPLAYBARCODE-fältets visuella resultat genereras om igen endast när `UpdateFields()` anropas, så den nya streckkoden visas i det sparade dokumentet.

**Q: Kommer anropet `Replace(\"INIT123\", \"NEWVAL\", ...)` att påverka andra förekomster av \"INIT123\" utanför streckkodsfältet?**  
A: Ja, `Document.Range.Replace` arbetar på hela dokumentets område, så all matchande text någon annanstans kommer att ersättas om du inte begränsar sökningen med `FindReplaceOptions` (t.ex. genom att ange ett specifikt `Range` eller använda `.MatchWholeWord`).

**Q: Kan jag ändra streckkodstypen (t.ex. från CODE39 till QR) efter att fältet har infogats?**  
A: Du kan tilldela ett nytt värde till `displayBarcode.BarcodeType` när som helst, men du måste anropa `myDocument.UpdateFields()` därefter för att förändringen ska återspeglas i den renderade streckkoden.

**Q: Vad gör egenskapen `AddStartStopChar = true` för CODE39-streckkoder?**  
A: När `AddStartStopChar` är true lägger Aspose.Words automatiskt till de nödvändiga start-/stopptecknen (`*`) runt streckkodsvärdet, vilket krävs av CODE39; sätt den till false om din symbologi inte behöver dem.

**Q: Behöver jag konfigurera några speciella alternativ i `FindReplaceOptions` för att säkert ersätta streckkodsvärdet?**  
A: Inga speciella inställningar krävs för en enkel exakt matchning, men du kan aktivera `.MatchCase` eller `.MatchWholeWord` i `FindReplaceOptions` för att undvika oavsiktliga partiella ersättningar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}