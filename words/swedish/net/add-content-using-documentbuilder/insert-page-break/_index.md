---
title: Infoga sidbrytning i ett Word-dokument med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig att lägga till sidbrytningar i en Word‑fil med Aspose.Words för .NET med hjälp av Document och DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga sidbrytning i ett Word-dokument med Aspose.Words för .NET
I den här interaktiva handledningen kommer du att lära dig hur du programatiskt lägger till sidbrytningar i ett Word-dokument med Aspose.Words för .NET. Genom att skapa ett Document-objekt och använda DocumentBuilder kan du styra var nya sidor börjar, vilket är avgörande för formatering av rapporter, fakturor eller vilket som helst flersektionsdokument. Följ steg‑för‑steg‑exemplet för att se koden i aktion och förhandsgranska den resulterande filen.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Kan jag använda InsertBreak för att lägga till ett radbrytning eller ett avsnittsbrytning istället för en sidbrytning?**
A: Ja, InsertBreak accepterar vilket BreakType‑enum‑värde som helst, till exempel BreakType.LineBreak eller BreakType.SectionBreakContinuous, för att infoga motsvarande brytning.

**Q: Behöver jag anropa InsertBreak före eller efter att ha skrivit texten för den nya sidan?**
A: InsertBreak bör anropas efter det innehåll du vill ha på den aktuella sidan; nästa Writeln kommer då att börja på den nya sidan som skapats av brytningen.

**Q: Vad händer om sökvägen dataDir inte avslutas med ett katalogseparator?**
A: Om dataDir saknar ett avslutande snedstreck kommer filnamnet att konkateneras direkt (t.ex. "C:\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), vilket kan leda till en ogiltig sökväg; se till att sökvägen avslutas med "\\" eller använd Path.Combine.

**Q: Kan jag återanvända samma DocumentBuilder‑instans för att infoga flera brytningar i hela dokumentet?**
A: Ja, samma DocumentBuilder kan användas upprepade gånger; varje anrop till InsertBreak infogar en brytning vid builderns aktuella markörposition.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}