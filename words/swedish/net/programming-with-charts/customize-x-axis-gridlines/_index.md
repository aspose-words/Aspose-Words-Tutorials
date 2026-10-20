---
title: Anpassa X‑axelns rutnätslinjer i ett stapeldiagram med Aspose.Words för .NET
weight: 610
limit:
description: Lär dig att lägga till och färg‑anpassa huvudrutnätslinjerna på X‑axeln i ett Word‑stapeldiagram med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att lägga till och färg‑anpassa huvudrutnätslinjerna på X‑axeln
    i ett Word‑stapeldiagram med Aspose.Words för .NET.
  headline: Anpassa X‑axelns rutnätslinjer i ett stapeldiagram med Aspose.Words för
    .NET
  type: TechArticle
- description: Lär dig att lägga till och färg‑anpassa huvudrutnätslinjerna på X‑axeln
    i ett Word‑stapeldiagram med Aspose.Words för .NET.
  name: Anpassa X‑axelns rutnätslinjer i ett stapeldiagram med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Word‑dokument och en DocumentBuilder för att redigera det.
    text: Skapa ett nytt Word‑dokument och en DocumentBuilder för att redigera det.
  - name: Infoga ett 432×252 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
    text: Infoga ett 432×252 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
  - name: Ta bort standardserien och lägg till en anpassad serie med tre grupper och
      värden.
    text: Ta bort standardserien och lägg till en anpassad serie med tre grupper och
      värden.
  - name: Hämta en referens till diagrammets primära horisontella (X‑)axel.
    text: Hämta en referens till diagrammets primära horisontella (X‑)axel.
  - name: Aktivera visning av huvudrutnätslinjer på den primära X‑axeln.
    text: Aktivera visning av huvudrutnätslinjer på den primära X‑axeln.
  - name: Ställ in rutnätslinjernas färg till blå och deras tjocklek till 2 punkter.
    text: Ställ in rutnätslinjernas färg till blå och deras tjocklek till 2 punkter.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: 'Ställ in samma axel‑egenskap till false: `horizontalAxis.HasMajorGridlines
      = false;` växlar synligheten för X‑axelns huvudrutnätslinjer.'
    question: Hur döljer jag huvudrutnätslinjerna igen efter att ha aktiverat dem?
  - answer: Nej, `Format.Stroke`‑inställningarna gäller endast den axel du ändrar;
      för att formatera Y‑axelns rutnätslinjer måste du justera `chart.AxisY.Format.Stroke`
      separat.
    question: Kommer en ändring av `horizontalAxis.Format.Stroke.Color` också att
      påverka Y‑axelns rutnätslinjer?
  - answer: Använd `horizontalAxis.Format.Stroke.Weight` och tilldela ett dubbelvärde
      (t.ex. `0.5`) för att göra rutnätslinjerna tunnare.
    question: Vilken egenskap styr tjockleken på X‑axelns huvudrutnätslinjer?
  - answer: Ja, sätt `horizontalAxis.Format.Stroke.DashStyle` till ett `DashStyle`‑enum‑värde,
      till exempel `DashStyle.Dash` eller `DashStyle.Dot`.
    question: Kan jag ändra streckmönstret för X‑axelns huvudrutnätslinjer?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Formatera X‑axelns rutnätslinjer i ett Word‑stapeldiagram
og_description: Aktivera och färg‑anpassa den primära X‑axelns rutnätslinjer i ett Word‑diagram med Aspose.Words för .NET.
og_image_alt: Guide som visar ett Word‑dokument med ett stapeldiagram där den primära X‑axelns huvudrutnätslinjer är markerade i en anpassad färg med Aspose.Words för .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Anpassa X‑axelns rutnätslinjer i ett stapeldiagram med Aspose.Words för .NET
I den här handledningen kommer du att lära dig hur du skapar ett Word‑dokument, infogar ett stapeldiagram, ersätter dess standarddata och sedan aktiverar huvudrutnätslinjerna på den primära X‑axeln. Du får också se hur du ändrar rutnätslinjernas färg så att den matchar din design. Följ den steg‑för‑steg‑kod som ger exakt kontroll över X‑axelns rutnätslinjers synlighet och formatering.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Hur döljer jag huvudrutnätslinjerna igen efter att ha aktiverat dem?**  
A: Ställ in samma axel‑egenskap till false: `horizontalAxis.HasMajorGridlines = false;` växlar synligheten för X‑axelns huvudrutnätslinjer.

**Q: Kommer en ändring av `horizontalAxis.Format.Stroke.Color` också att påverka Y‑axelns rutnätslinjer?**  
A: Nej, `Format.Stroke`‑inställningarna gäller endast den axel du ändrar; för att formatera Y‑axelns rutnätslinjer måste du justera `chart.AxisY.Format.Stroke` separat.

**Q: Vilken egenskap styr tjockleken på X‑axelns huvudrutnätslinjer?**  
A: Använd `horizontalAxis.Format.Stroke.Weight` och tilldela ett dubbelvärde (t.ex. `0.5`) för att göra rutnätslinjerna tunnare.

**Q: Kan jag ändra streckmönstret för X‑axelns huvudrutnätslinjer?**  
A: Ja, sätt `horizontalAxis.Format.Stroke.DashStyle` till ett `DashStyle`‑enum‑värde, till exempel `DashStyle.Dash` eller `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}