---
title: Lägg till ett kryssruteformulärfält i ett Word-dokument med Aspose.Words for .NET
weight: 210
limit:
description: Lär dig hur du programatiskt lägger till ett kryssruteformulärfält i ett nytt Word-dokument med Aspose.Words for .NET och sparar filen.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till ett kryssruteformulärfält i ett Word-dokument med Aspose.Words
Denna handledning visar hur man skapar ett nytt Word-dokument och använder Aspose.Words for .NET:s DocumentBuilder för att infoga ett kryssruteformulärfält. Genom att följa stegen ser du den exakta koden som behövs för att lägga till det interaktiva elementet och sedan spara dokumentet till en fil. Det är ett snabbt sätt att programatiskt bygga enkla formuläraktiverade Word-filer.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Vad representerar det fjärde argumentet (0) i InsertCheckBox?**
A: Det anger den visuella storleken på kryssrutan i punkter; ett värde på 0 talar om för Aspose.Words att använda standardstorleken.

**Q: Kan jag infoga mer än en kryssruta med samma namn?**
A: Nej – varje formulärfältsnamn måste vara unikt; att försöka infoga en annan kryssruta med namnet "CheckBox" kommer att kasta ett ArgumentException.

**Q: Hur lägger jag till en kryssruta i ett befintligt dokument istället för ett nytt?**
A: Läs in dokumentet först (t.ex. `Document doc = new Document("Existing.docx");`) skapa sedan en DocumentBuilder för det dokumentet och anropa `InsertCheckBox` på önskad markörposition.

**Q: Hur kan jag läsa av tillståndet för den infogade kryssrutan efter att dokumentet har sparats?**
A: Hämta formulärfältet via `doc.Range.FormFields["CheckBox"]` och inspektera dess `Checked`-egenskap för att se om det var ikryssat.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}