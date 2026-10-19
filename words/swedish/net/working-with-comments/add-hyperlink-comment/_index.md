---
title: Lägg till Hyperlink‑kommentar och exportera som PDF‑annotation med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig att lägga till en hyperlänk‑kommentar i en Word‑fil och exportera den som en PDF‑annotation med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att lägga till en hyperlänk‑kommentar i en Word‑fil och exportera
    den som en PDF‑annotation med Aspose.Words för .NET.
  headline: Lägg till Hyperlink‑kommentar och exportera som PDF‑annotation med Aspose.Words
    för .NET
  type: TechArticle
- description: Lär dig att lägga till en hyperlänk‑kommentar i en Word‑fil och exportera
    den som en PDF‑annotation med Aspose.Words för .NET.
  name: Lägg till Hyperlink‑kommentar och exportera som PDF‑annotation med Aspose.Words
    för .NET
  steps:
  - name: Skapa ett nytt tomt Document‑objekt och en DocumentBuilder för att arbeta
      med det.
    text: Skapa ett nytt tomt Document‑objekt och en DocumentBuilder för att arbeta
      med det.
  - name: Skriv en rad synlig text som kommer att innehålla den kommande kommentaren.
    text: Skriv en rad synlig text som kommer att innehålla den kommande kommentaren.
  - name: Skapa en Comment skriven av Jane Doe och fäst den på dokumentets första
      stycke.
    text: Skapa en Comment skriven av Jane Doe och fäst den på dokumentets första
      stycke.
  - name: Inuti kommentaren, lägg till ett stycke och infoga en blå, understruken
      hyperlänk till Aspose.Words Library‑webbplatsen.
    text: Inuti kommentaren, lägg till ett stycke och infoga en blå, understruken
      hyperlänk till Aspose.Words Library‑webbplatsen.
  - name: Konfigurera dokumentet så att kommentarer renderas som PDF‑annotationer
      och uppdatera layouten.
    text: Konfigurera dokumentet så att kommentarer renderas som PDF‑annotationer
      och uppdatera layouten.
  - name: Skapa en \"Output\"‑mapp i den aktuella katalogen för att lagra den genererade
      PDF‑filen.
    text: Skapa en \"Output\"‑mapp i den aktuella katalogen för att lagra den genererade
      PDF‑filen.
  - name: Spara det förberedda dokumentet som en PDF‑fil med PdfSaveOptions.
    text: Spara det förberedda dokumentet som en PDF‑fil med PdfSaveOptions.
  - name: Kontrollera att PDF‑filen finns och innehåller data, skriv sedan ut resultatet
      till konsolen.
    text: Kontrollera att PDF‑filen finns och innehåller data, skriv sedan ut resultatet
      till konsolen.
  type: HowTo
- questions:
  - answer: '`InsertHyperlink`s tredje parameter anger om länken ska behandlas som
      ett fält; om den sätts till `false` infogas en vanlig hyperlänk som fungerar
      i PDF‑annotation utan att behöva ett fältkod.'
    question: Vad styr det tredje argumentet (`false`) i `InsertHyperlink`?
  - answer: Ställ in `myDocument.LayoutOptions.CommentDisplayMode` till `CommentDisplayMode.ShowInBalloons`
      innan du anropar `Save`; PDF‑filen kommer då att innehålla kommentaren som en
      vanlig Word‑kommentar snarare än en annotation.
    question: Hur kan jag få kommentaren att visas som en bubbla i Word‑dokumentet
      istället för som en PDF‑annotation?
  - answer: Ja—varje `Comment` du lägger till i ett stycke kan innehålla sitt eget
      `InsertHyperlink`‑anrop, och alla hyperlänkar bevaras som separata PDF‑annotationer
      när dokumentet sparas.
    question: Om jag lägger till mer än en kommentar, kommer varje hyperlänk att fungera
      i den exporterade PDF‑filen?
  - answer: Öppna den genererade PDF‑filen, lokalisera kommentaranotation (vanligtvis
      visas den som en notikon), klicka på den för att visa kommentartexten och klicka
      sedan på den blå understrukna länken; den bör öppna mål‑URL:en i en webbläsare.
    question: Hur verifierar jag att hyperlänken i kommentaren faktiskt fungerar efter
      att PDF‑filen har genererats?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Infoga hyperlänk‑kommentar och exportera till PDF
og_description: Lär dig att bädda in en klickbar länk i en Word‑kommentar och omvandla den till en PDF‑annotation.
og_image_alt: Guide som visar hur man lägger till en kommentar med en klickbar hyperlänk i ett Word‑dokument och exporterar den som en PDF‑annotation med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till Hyperlink‑kommentar och exportera som PDF‑annotation med Aspose.Words för .NET
I den här handledningen får du se hur man skapar ett Word‑dokument, infogar en kommentar som innehåller en klickbar hyperlänk till en extern webbplats, konfigurerar kommentaren så att den visas som en PDF‑annotation, exporterar dokumentet till PDF och verifierar den resulterande PDF‑filen. Den steg‑för‑steg‑koden låter dig lägga till rika, länkintegrerade kommentarer och bevara dem vid konvertering till PDF, vilket gör det enkelt att dela interaktiva anteckningar med läsarna.

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

**Q: Vad styr det tredje argumentet (`false`) i `InsertHyperlink`?**  
A: `InsertHyperlink`s tredje parameter anger om länken ska behandlas som ett fält; om den sätts till `false` infogas en vanlig hyperlänk som fungerar i PDF‑annotation utan att behöva ett fältkod.

**Q: Hur kan jag få kommentaren att visas som en bubbla i Word‑dokumentet istället för som en PDF‑annotation?**  
A: Ställ in `myDocument.LayoutOptions.CommentDisplayMode` till `CommentDisplayMode.ShowInBalloons` innan du anropar `Save`; PDF‑filen kommer då att innehålla kommentaren som en vanlig Word‑kommentar snarare än en annotation.

**Q: Om jag lägger till mer än en kommentar, kommer varje hyperlänk att fungera i den exporterade PDF‑filen?**  
A: Ja—varje `Comment` du lägger till i ett stycke kan innehålla sitt eget `InsertHyperlink`‑anrop, och alla hyperlänkar bevaras som separata PDF‑annotationer när dokumentet sparas.

**Q: Hur verifierar jag att hyperlänken i kommentaren faktiskt fungerar efter att PDF‑filen har genererats?**  
A: Öppna den genererade PDF‑filen, lokalisera kommentaranotation (vanligtvis visas den som en notikon), klicka på den för att visa kommentartexten och klicka sedan på den blå understrukna länken; den bör öppna mål‑URL:en i en webbläsare.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}