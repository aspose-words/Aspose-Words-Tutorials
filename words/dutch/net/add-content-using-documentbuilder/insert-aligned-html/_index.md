---
title: Uitgelijnde HTML invoegen in Word-document met Aspose.Words voor .NET
weight: 210
limit:
description: Leer hoe je HTML met een specifieke uitlijning in een Word-document kunt invoegen met Aspose.Words voor .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uitgelijnde HTML invoegen in Word-document met Aspose.Words voor .NET
Deze tutorial laat zien hoe je Aspose.Words voor .NET's DocumentBuilder gebruikt om HTML-markup in een Word-document in te sluiten en de uitlijning ervan te regelen. Je ziet hoe je de HTML invoegt, de alinea‑uitlijning instelt (links, gecentreerd of rechts) en vervolgens het resulterende document opslaat. Het voorbeeld is ideaal voor ontwikkelaars die web‑achtige opmaak willen behouden bij het programmatisch genereren van Word‑bestanden.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Kan InsertHtml worden gebruikt om HTML toe te voegen aan een bestaand Word-document in plaats van een nieuw document?**
A: Ja. Maak een Document aan van het bestaande bestand, positioneer de DocumentBuilder‑cursor op de plek waar je de HTML wilt invoegen (bijv. met builder.MoveToDocumentEnd()), en roep vervolgens builder.InsertHtml aan met je markup.

**Q: Welke HTML‑attributen worden door InsertHtml gerespecteerd voor uitlijning?**
A: InsertHtml respecteert het "align"‑attribuut op blok‑niveau elementen zoals <p>, <div> en kop‑tags, en past de overeenkomstige alinea‑uitlijning toe in het resulterende Word-document.

**Q: Wat gebeurt er als de HTML‑string niet‑ondersteunde tags of CSS bevat?**
A: Niet‑ondersteunde tags worden genegeerd en hun binnenste tekst wordt als platte tekst ingevoegd; inline CSS‑stijlen die Aspose.Words niet herkent, worden eveneens genegeerd, zodat alleen de ondersteunde subset van HTML wordt gerenderd.

**Q: Moet ik de DocumentBuilder sluiten voordat ik het document opsla?**
A: Er is geen expliciete sluiting nodig; na het invoegen van de HTML kun je direct doc.Save aanroepen met de gewenste bestandsnaam en -formaat, en worden de resources van de builder automatisch vrijgegeven.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}