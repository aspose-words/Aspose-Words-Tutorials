---
title: Een Comment invoegen op een specifieke alinea in een Word‑document met Aspose.Words voor .NET
weight: 210
limit:
description: Stapsgewijze handleiding om een auteurscommentaar toe te voegen aan een gekozen alinea in een Word‑document en het op te slaan als DOCX met Aspose.Words voor .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Stapsgewijze handleiding om een auteurscommentaar toe te voegen aan
    een gekozen alinea in een Word‑document en het op te slaan als DOCX met Aspose.Words
    voor .NET.
  headline: Een Comment invoegen op een specifieke alinea in een Word‑document met
    Aspose.Words voor .NET
  type: TechArticle
- description: Stapsgewijze handleiding om een auteurscommentaar toe te voegen aan
    een gekozen alinea in een Word‑document en het op te slaan als DOCX met Aspose.Words
    voor .NET.
  name: Een Comment invoegen op een specifieke alinea in een Word‑document met Aspose.Words
    voor .NET
  steps:
  - name: Instantieer een nieuw Document en een DocumentBuilder om te beginnen met
      het bouwen van het Word‑bestand.
    text: Instantieer een nieuw Document en een DocumentBuilder om te beginnen met
      het bouwen van het Word‑bestand.
  - name: Gebruik DocumentBuilder.Writeln om drie afzonderlijke alinea's tekst aan
      het document toe te voegen.
    text: Gebruik DocumentBuilder.Writeln om drie afzonderlijke alinea's tekst aan
      het document toe te voegen.
  - name: Haal de tweede alinea veilig op, en val terug op de eerste als het document
      minder dan twee alinea's bevat.
    text: Haal de tweede alinea veilig op, en val terug op de eerste als het document
      minder dan twee alinea's bevat.
  - name: Maak een Comment met auteursgegevens, stel de tekst in, en koppel deze aan
      de geselecteerde alinea.
    text: Maak een Comment met auteursgegevens, stel de tekst in, en koppel deze aan
      de geselecteerde alinea.
  - name: Sla het gewijzigde document op als een DOCX‑bestand met de naam 'sample.docx'
      in de huidige map.
    text: Sla het gewijzigde document op als een DOCX‑bestand met de naam 'sample.docx'
      in de huidige map.
  type: HowTo
- questions:
  - answer: Het `if`‑blok valt terug op de eerste alinea (`paraList[0]`) wanneer `paraList.Count`
      kleiner is dan 2, zodat het commentaar aan die enkele alinea wordt gekoppeld
      in plaats van aan de ontbrekende tweede.
    question: Wat doet de code als het document slechts één alinea bevat?
  - answer: Ze worden doorgegeven aan de `Comment`‑constructor als het tweede en derde
      argument – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – waarbij
      "Jordan" de auteursnaam is en "JH" de initialen.
    question: Hoe worden de naam en initialen van de commentaarauteur ingesteld in
      dit voorbeeld?
  - answer: In dit fragment is het commentaar gekoppeld aan de volledige `Paragraph`
      via `AppendChild`, maar om commentaar op een tekstreeks te geven, moet je een
      `CommentRangeStart` en `CommentRangeEnd` rond de gewenste `Run`‑nodes maken
      en vervolgens de `Comment`‑node daartussen toevoegen.
    question: Kan ik een commentaar koppelen aan een specifiek stuk tekst in plaats
      van de hele alinea?
  - answer: '`AppendChild` voegt de `Comment`‑node toe aan de kindcollectie van de
      alinea, en Aspose.Words genereert automatisch de benodigde commentaar‑begin/eind‑markers
      wanneer het document wordt opgeslagen.'
    question: Moet ik handmatig commentaarmarkers invoegen, of regelt `AppendChild`
      dat?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Een commentaar invoegen in een Word‑alinea
og_description: Voeg een auteurscommentaar toe aan een specifieke alinea en exporteer het bestand als DOCX met Aspose.Words.
og_image_alt: Handleiding die laat zien hoe je een commentaar toevoegt aan een alinea in een Word‑document met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Een Comment invoegen op een specifieke alinea in een Word‑document met Aspose.Words voor .NET
Met Aspose.Words voor .NET kun je programmatisch commentaar toevoegen aan Word‑bestanden. Deze tutorial leidt je door het maken van een nieuw document, het invoegen van drie alinea's, het vinden van de tweede alinea, en het koppelen van een commentaar dat auteur‑ en datum‑informatie bevat. Uiteindelijk wordt het document opgeslagen als een DOCX‑bestand waarbij het commentaar behouden blijft.

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

**Q: Wat doet de code als het document slechts één alinea bevat?**  
A: Het `if`‑blok valt terug op de eerste alinea (`paraList[0]`) wanneer `paraList.Count` kleiner is dan 2, zodat het commentaar aan die enkele alinea wordt gekoppeld in plaats van aan de ontbrekende tweede.

**Q: Hoe worden de naam en initialen van de commentaarauteur ingesteld in dit voorbeeld?**  
A: Ze worden doorgegeven aan de `Comment`‑constructor als het tweede en derde argument – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – waarbij "Jordan" de auteursnaam is en "JH" de initialen.

**Q: Kan ik een commentaar koppelen aan een specifiek stuk tekst in plaats van de hele alinea?**  
A: In dit fragment is het commentaar gekoppeld aan de volledige `Paragraph` via `AppendChild`, maar om commentaar op een tekstreeks te geven, moet je een `CommentRangeStart` en `CommentRangeEnd` rond de gewenste `Run`‑nodes maken en vervolgens de `Comment`‑node daartussen toevoegen.

**Q: Moet ik handmatig commentaarmarkers invoegen, of regelt `AppendChild` dat?**  
A: `AppendChild` voegt de `Comment`‑node toe aan de kindcollectie van de alinea, en Aspose.Words genereert automatisch de benodigde commentaar‑begin/eind‑markers wanneer het document wordt opgeslagen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}