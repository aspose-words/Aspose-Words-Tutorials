---
title: Lägg till ett Combo Box Form Field i ett Word‑dokument med Aspose.Words for .NET
weight: 310
limit:
description: Lär dig hur du lägger till ett kombinationsruta‑formulärfält med fördefinierade objekt i ett Word‑dokument med hjälp av Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till ett Combo Box Form Field i ett Word‑dokument med Aspose.Words
Den här handledningen visar hur man använder Aspose.Words for .NET:s DocumentBuilder för att skapa ett nytt Word‑dokument och infoga ett kombinationsruta‑formulärfält som är fyllt med fördefinierade objekt. Genom att följa den steg‑för‑steg‑kod du får se hur du konfigurerar alternativen för kombinationsrutan och sedan sparar dokumentet för användning i interaktiva formulär.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: Vad representerar `items`‑arrayen som skickas till `InsertComboBox`?**
A: Den definierar listan av strängar som visas som valbara alternativ i kombinationsrutans rullgardinsmeny.

**Q: Hur kan jag ändra vilket objekt som är förvalt markerat när dokumentet öppnas?**
A: Ställ in det tredje argumentet (`selectedIndex`) i `InsertComboBox` till det nollbaserade indexet för det önskade förvalda objektet (t.ex. `2` för "Three").

**Q: Är det möjligt att placera kombinationsrutan på en specifik plats i dokumentet?**
A: Ja—flytta `DocumentBuilder`‑markören till önskad plats med metoder som `MoveToParagraph`, `InsertParagraph` eller `Write` innan du anropar `InsertComboBox`.

**Q: Vilket filformat skapas av den här koden och kan det öppnas i äldre versioner av Word?**
A: Koden sparar en `.docx`‑fil, som kan öppnas av Word 2007 och senare, samt av alla program som stödjer OpenXML‑formatet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}