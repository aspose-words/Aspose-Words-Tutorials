---
title: Infoga TC‑fält i Word-dokument med Aspose.Words for .NET
weight: 110
limit:
description: Lär dig hur du infogar ett TC‑fält med anpassad text i ett Word‑dokument med Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga TC‑fält i Word-dokument med Aspose.Words
Denna handledning visar hur du använder Aspose.Words for .NET för att infoga ett TC‑fält (Table of Contents) i ett ny‑skapat Word‑dokument. Genom att använda DocumentBuilder kan du lägga till ett TC‑fält med anpassad posttext, vilket är användbart för att bygga ett sökbart index för en innehållsförteckning. Exemplet demonstrerar också hur man sparar dokumentet till disk.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Vad betyder växeln \"\\f t\" i TC‑fältkoden?**
A: Växeln \"\\f t\" talar om för Word att behandla posten som en tabellpost, vilket gör att den visas i en innehållsförteckning som genereras med \\f‑växeln.

**Q: Hur kan jag ändra texten som visas i TC‑fältet?**
A: Byt ut \"Entry Text\" i InsertField‑anropet mot vilken sträng du vill, t.ex. builder.InsertField(\"TC \\"Chapter 1\" \\f t\");

**Q: Kan jag infoga flera TC‑fält i samma dokument?**
A: Ja; anropa bara builder.InsertField med olika posttexter på önskade platser innan du sparar dokumentet.

**Q: Fungerar den här koden för andra format än .docx, till exempel .pdf?**
A: Dokumentet sparas som .docx i exemplet, men Aspose.Words kan spara till andra format (t.ex. .pdf) genom att ändra filändelsen i doc.Save och säkerställa att det önskade utdataformatet stöds.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}