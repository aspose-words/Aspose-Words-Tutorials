---
title: Infoga horisontell regel‑form i Word‑dokument med Aspose.Words för .NET
weight: 110
limit:
description: Steg‑för‑steg‑guide för att infoga en horisontell regel‑form i ett Word‑dokument med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga horisontell regel‑form i Word‑dokument med Aspose.Words för .NET
Lär dig hur du använder Aspose.Words för .NET för att infoga en horisontell regel‑form i ett Word‑dokument. Denna handledning guidar dig genom att skapa ett nytt dokument, lägga till en textrad, placera en horisontell regel‑form med DocumentBuilder och spara filen. Den horisontella regeln fungerar som en enkel visuell avgränsare för ditt innehåll.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Kan jag ändra utseendet (färg, tjocklek) på den horisontella regel som infogas med DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule skapar en inbyggd horisontell linje‑form med standardformatering; för att ändra dess utseende måste du hämta det infogade Shape‑objektet (builder.CurrentParagraph.LastChild) och justera dess LineFormat‑egenskaper.

**Q: Vad händer om jag anropar InsertHorizontalRule() efter ett stycke som redan avslutas med en radbrytning?**
A: Metoden infogar regeln som ett separat stycke, så ett föregående radbrytning skapar helt enkelt ett tomt stycke före regeln; regeln kommer fortfarande att visas på sin egen rad.

**Q: Är det möjligt att infoga mer än en horisontell regel i samma dokument med DocumentBuilder?**
A: Ja, varje anrop till builder.InsertHorizontalRule() lägger till en ny horisontell regel‑form på den aktuella markörpositionen, vilket möjliggör flera regler i hela dokumentet.

**Q: Fungerar InsertHorizontalRule() när dokumentet sparas i andra format än DOCX, till exempel PDF?**
A: Den horisontella regeln lagras som en shape i dokumentmodellen, så när du sparar till PDF, XPS eller andra stödda format renderas regeln korrekt i resultatet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}