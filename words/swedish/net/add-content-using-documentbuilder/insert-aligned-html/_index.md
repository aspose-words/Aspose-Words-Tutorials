---
title: Infoga justerad HTML i Word-dokument med Aspose.Words för .NET
weight: 210
limit:
description: Lär dig hur du infogar HTML med specifik justering i ett Word-dokument med Aspose.Words för .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga justerad HTML i Word-dokument med Aspose.Words för .NET
Den här handledningen visar hur du använder Aspose.Words för .NET:s DocumentBuilder för att bädda in HTML-markup i ett Word-dokument och styra dess justering. Du kommer att se hur du infogar HTML, sätter styckejustering (vänster, centrerad eller höger) och sedan sparar det resulterande dokumentet. Exemplet är idealiskt för utvecklare som behöver bevara webbliknande formatering när de genererar Word-filer programmässigt.

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

**Q: Kan InsertHtml användas för att lägga till HTML i ett befintligt Word-dokument istället för ett nytt?**  
A: Ja. Skapa ett Document från den befintliga filen, placera DocumentBuilder‑markören där du vill infoga HTML (t.ex. med builder.MoveToDocumentEnd()), och anropa sedan builder.InsertHtml med din markup.

**Q: Vilka HTML-attribut respekteras av InsertHtml för justering?**  
A: InsertHtml respekterar "align"‑attributet på blocknivå‑element som &lt;p&gt;, &lt;div&gt; och rubriktaggar, och tillämpar motsvarande styckejustering i det resulterande Word-dokumentet.

**Q: Vad händer om HTML-strängen innehåller taggar eller CSS som inte stöds?**  
A: Taggar som inte stöds ignoreras och deras innertext infogas som vanlig text; inline‑CSS‑stilar som Aspose.Words inte känner igen ignoreras också, så endast den stödda delmängden av HTML renderas.

**Q: Behöver jag stänga DocumentBuilder innan jag sparar dokumentet?**  
A: Ingen explicit stängning krävs; efter att ha infogat HTML kan du direkt anropa doc.Save med önskat filnamn och format, och builderns resurser frigörs automatiskt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}