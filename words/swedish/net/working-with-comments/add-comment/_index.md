---
title: Infoga en Comment på ett specifikt stycke i ett Word-dokument med Aspose.Words för .NET
weight: 210
limit:
description: Steg‑för‑steg‑guide för att lägga till en författarkommentar till ett valt stycke i ett Word-dokument och spara det som DOCX med Aspose.Words för .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Steg‑för‑steg‑guide för att lägga till en författarkommentar till ett
    valt stycke i ett Word-dokument och spara det som DOCX med Aspose.Words för .NET.
  headline: Infoga en Comment på ett specifikt stycke i ett Word-dokument med Aspose.Words
    för .NET
  type: TechArticle
- description: Steg‑för‑steg‑guide för att lägga till en författarkommentar till ett
    valt stycke i ett Word-dokument och spara det som DOCX med Aspose.Words för .NET.
  name: Infoga en Comment på ett specifikt stycke i ett Word-dokument med Aspose.Words
    för .NET
  steps:
  - name: Instansiera ett nytt Document och en DocumentBuilder för att börja bygga
      Word-filen.
    text: Instansiera ett nytt Document och en DocumentBuilder för att börja bygga
      Word-filen.
  - name: Använd DocumentBuilder.Writeln för att lägga till tre separata stycken text
      i dokumentet.
    text: Använd DocumentBuilder.Writeln för att lägga till tre separata stycken text
      i dokumentet.
  - name: Hämta det andra stycket på ett säkert sätt, och falla tillbaka på det första
      om dokumentet har färre än två stycken.
    text: Hämta det andra stycket på ett säkert sätt, och falla tillbaka på det första
      om dokumentet har färre än två stycken.
  - name: Skapa en Comment med författardetaljer, ange dess text och bifoga den till
      det valda stycket.
    text: Skapa en Comment med författardetaljer, ange dess text och bifoga den till
      det valda stycket.
  - name: Spara det modifierade dokumentet som en DOCX-fil med namnet 'sample.docx'
      i den aktuella mappen.
    text: Spara det modifierade dokumentet som en DOCX-fil med namnet 'sample.docx'
      i den aktuella mappen.
  type: HowTo
- questions:
  - answer: '`if`‑blocket faller tillbaka på det första stycket (`paraList[0]`) när
      `paraList.Count` är mindre än 2, så kommentaren kommer att bifogas till det
      enda stycket istället för det saknade andra.'
    question: Vad gör koden om dokumentet bara innehåller ett stycke?
  - answer: De skickas till `Comment`‑konstruktorn som det andra och tredje argumentet
      – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – där "Jordan" är författarnamnet
      och "JH" är initialerna.
    question: Hur sätts kommentarförfattarens namn och initialer i detta exempel?
  - answer: I detta kodsnutt är kommentaren kopplad till hela `Paragraph` via `AppendChild`,
      men för att kommentera ett textintervall måste du skapa ett `CommentRangeStart`
      och ett `CommentRangeEnd` runt de önskade `Run`‑noderna och sedan lägga till
      `Comment`‑noden mellan dem.
    question: Kan jag bifoga en kommentar till en specifik textdel snarare än hela
      stycket?
  - answer: '`AppendChild` lägger till `Comment`‑noden i styckets barnsamling, och
      Aspose.Words genererar automatiskt de nödvändiga kommentarstart‑/slutmärkarna
      när dokumentet sparas.'
    question: Behöver jag manuellt infoga kommentarmarkörer, eller hanterar `AppendChild`
      det?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Infoga en kommentar i ett Word-stycke
og_description: Lägg till en författarkommentar till ett specifikt stycke och exportera filen som DOCX med Aspose.Words.
og_image_alt: Guide som visar hur man lägger till en kommentar till ett stycke i ett Word-dokument med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga en Comment på ett specifikt stycke i ett Word-dokument med Aspose.Words för .NET
Med Aspose.Words för .NET kan du programatiskt lägga till kommentarer i Word-filer. Den här handledningen går igenom att skapa ett nytt dokument, infoga tre stycken, hitta det andra stycket och bifoga en kommentar som innehåller författar- och datuminformation. Slutligen sparas dokumentet som en DOCX-fil som bevarar kommentaren.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Vad gör koden om dokumentet bara innehåller ett stycke?**  
A: `if`‑blocket faller tillbaka på det första stycket (`paraList[0]`) när `paraList.Count` är mindre än 2, så kommentaren kommer att bifogas till det enda stycket istället för det saknade andra.

**Q: Hur sätts kommentarförfattarens namn och initialer i detta exempel?**  
A: De skickas till `Comment`‑konstruktorn som det andra och tredje argumentet – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – där "Jordan" är författarnamnet och "JH" är initialerna.

**Q: Kan jag bifoga en kommentar till en specifik textdel snarare än hela stycket?**  
A: I detta kodsnutt är kommentaren kopplad till hela `Paragraph` via `AppendChild`, men för att kommentera ett textintervall måste du skapa ett `CommentRangeStart` och ett `CommentRangeEnd` runt de önskade `Run`‑noderna och sedan lägga till `Comment`‑noden mellan dem.

**Q: Behöver jag manuellt infoga kommentarmarkörer, eller hanterar `AppendChild` det?**  
A: `AppendChild` lägger till `Comment`‑noden i styckets barnsamling, och Aspose.Words genererar automatiskt de nödvändiga kommentarstart‑/slutmärkarna när dokumentet sparas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}