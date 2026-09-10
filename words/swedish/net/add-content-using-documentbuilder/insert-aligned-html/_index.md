---
title: Infoga justerad HTML i Word‑dokument med Aspose.Words för .NET
weight: 210
limit:
description: Lär dig infoga rå HTML med vänster, centrerad eller höger justering i ett Word‑dokument med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga justerad HTML i Word‑dokument med Aspose.Words för .NET
Denna interaktiva handledning visar hur man bäddar in rå HTML i ett Word‑dokument samtidigt som man styr dess justering—vänster, centrerad eller höger—med Aspose.Words för .NET. Genom att utnyttja Document och DocumentBuilder kan du infoga en HTML‑sträng och tillämpa önskad styckejustering med bara några rader kod. Exemplet är idealiskt när du behöver bevara HTML‑formatering och placera innehållet exakt i ditt dokument.

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

**Q: Vad händer om HTML‑strängen som skickas till DocumentBuilder.InsertHtml innehåller taggar som Aspose.Words inte stöder, såsom <script> eller <iframe>?**
A: Ostödda taggar ignoreras; Aspose.Words analyserar endast den del av HTML som den kan rendera, så <script>, <iframe> och liknande element tas bort medan resten av innehållet infogas.

**Q: Kommer inline‑CSS‑stilar (t.ex. <span style="color:red;">) att bevaras när InsertHtml används?**
A: Ja, InsertHtml respekterar många inline‑CSS‑egenskaper som färg, font‑size och bakgrund, och konverterar dem till motsvarande Word‑formatering.

**Q: Skapar InsertHtml automatiskt ett nytt stycke för block‑nivå‑element som <div> eller <h1>?**
A: Block‑nivå‑element mappas till Word‑stycken, så varje <div>, <p>, <h1> osv. blir ett separat stycke i dokumentet.

**Q: Hur kan jag infoga HTML på en specifik plats i ett befintligt dokument istället för i början?**
A: Flytta DocumentBuilder‑markören till önskad nod (t.ex. builder.MoveToDocumentEnd() eller builder.MoveToParagraph(index)) innan du anropar InsertHtml; HTML‑koden kommer att infogas på den aktuella markörpositionen.

**Q: Om dokumentet redan innehåller text, kommer ett anrop till InsertHtml att skriva över befintligt innehåll?**
A: Nej, InsertHtml infogar den analyserade HTML‑koden på builderns nuvarande position utan att radera befintliga noder, såvida du inte uttryckligen flyttar markören in i eller tar bort dessa noder i förväg.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}