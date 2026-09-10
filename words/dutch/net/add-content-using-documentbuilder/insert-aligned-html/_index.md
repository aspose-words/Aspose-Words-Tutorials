---
title: Voeg uitgelijnde HTML in een Word-document in met Aspose.Words for .NET
weight: 210
limit:
description: Leer hoe je ruwe HTML met links, gecentreerde of rechts uitlijning in een Word-document kunt invoegen met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg uitgelijnde HTML in een Word-document in met Aspose.Words
Deze interactieve tutorial laat zien hoe je ruwe HTML in een Word-document kunt insluiten terwijl je de uitlijning—links, gecentreerd of rechts—beheert met Aspose.Words for .NET. Door gebruik te maken van Document en DocumentBuilder kun je een HTML‑string invoegen en de gewenste alinea‑uitlijning toepassen met slechts een paar regels code. Het voorbeeld is ideaal wanneer je HTML-opmaak wilt behouden en de inhoud nauwkeurig binnen je document wilt plaatsen.

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

**Q: Wat gebeurt er als de HTML‑string die aan DocumentBuilder.InsertHtml wordt doorgegeven tags bevat die Aspose.Words niet ondersteunt, zoals <script> of <iframe>?**
A: Niet‑ondersteunde tags worden genegeerd; Aspose.Words parseert alleen de subset van HTML die het kan weergeven, dus <script>, <iframe> en vergelijkbare elementen worden verwijderd terwijl de rest van de inhoud wordt ingevoegd.

**Q: Worden inline CSS‑stijlen (bijv. <span style="color:red;">) behouden bij het gebruik van InsertHtml?**
A: Ja, InsertHtml respecteert veel inline CSS‑eigenschappen zoals kleur, lettergrootte en achtergrond, en zet ze om naar de overeenkomstige Word-opmaak.

**Q: Maakt InsertHtml automatisch een nieuwe alinea aan voor block‑level elementen zoals <div> of <h1>?**
A: Block‑level elementen worden gemapt naar Word‑alinea's, zodat elk <div>, <p>, <h1>, enz., een aparte alinea in het document wordt.

**Q: Hoe kan ik HTML op een specifieke locatie in een bestaand document invoegen in plaats van aan het begin?**
A: Verplaats de DocumentBuilder‑cursor naar het gewenste knooppunt (bijv. builder.MoveToDocumentEnd() of builder.MoveToParagraph(index)) voordat je InsertHtml aanroept; de HTML wordt ingevoegd op de huidige cursorpositie.

**Q: Als het document al tekst bevat, zal het aanroepen van InsertHtml bestaande inhoud overschrijven?**
A: Nee, InsertHtml voegt de geparseerde HTML in op de huidige positie van de builder zonder bestaande knooppunten te verwijderen, tenzij je de cursor expliciet naar die knooppunten verplaatst of ze vooraf verwijdert.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}