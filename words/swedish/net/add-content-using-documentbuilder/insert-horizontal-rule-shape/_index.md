---
title: Infoga horisontell linjeform i Word-dokument med Aspose.Words for .NET
weight: 110
limit:
description: Lär dig att lägga till en horisontell linjeform i ett Word-dokument med Aspose.Words for .NET med hjälp av DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga horisontell linjeform i Word-dokument med Aspose.Words
I den här handledningen kommer du att lära dig hur du programatiskt infogar en horisontell linjeform i ett Word-dokument med Aspose.Words for .NET. Med hjälp av klasserna Document och DocumentBuilder skapar vi ett nytt dokument, lägger till ett textstycke och placerar sedan en horisontell linjeform på önskad plats. Den horisontella linjen fungerar som en visuell avgränsare som kan vara användbar för avsnittsbrytningar eller visuell betoning.

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

**Q: Var exakt placerar `builder.InsertHorizontalRule()` linjen i dokumentet?**
A: `InsertHorizontalRule` infogar en horisontell linjeform på den aktuella markörpositionen i `DocumentBuilder`; om du vill ha den på en egen rad, anropa `builder.Writeln()` innan infogningen.

**Q: Kan jag ändra tjocklek, färg eller bredd på den infogade horisontella linjen?**
A: `InsertHorizontalRule` lägger till en standardformaterad linje och exponerar inte formateringsalternativ; för att anpassa dessa egenskaper måste du infoga en `Shape` manuellt (t.ex. `builder.InsertShape(ShapeType.HorizontalLine)`) och sedan sätta dess `LineFormat`‑egenskaper.

**Q: Är det möjligt att lägga till mer än en horisontell linje i samma dokument?**
A: Ja – anropa helt enkelt `builder.InsertHorizontalRule()` varje gång du behöver en ny linje; varje anrop skapar en separat form på Builder:s aktuella plats.

**Q: Kommer den horisontella linjen att vara synlig när den sparade .docx-filen öppnas i Microsoft Word?**
A: Absolut; linjen sparas som en form i .docx-filen, så Word visar den exakt som den ser ut i det genererade dokumentet.

**Q: Vad händer om `dataDir`-mappen inte finns innan `doc.Save(...)` anropas?**
A: `doc.Save` kommer att kasta ett `DirectoryNotFoundException`; se till att mål katalogen finns eller skapa den programatiskt innan du sparar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}