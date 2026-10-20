---
title: Skrytí okraje oblasti vykreslování ve sloupcovém grafu pomocí Aspose.Words pro .NET
weight: 410
limit:
description: Naučte se skrýt okraj oblasti vykreslování grafu a zároveň zachovat viditelné osové čáry ve sloupcovém grafu v dokumentu Word pomocí Aspose.Words pro .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se skrýt okraj oblasti vykreslování grafu a zároveň zachovat
    viditelné osové čáry ve sloupcovém grafu v dokumentu Word pomocí Aspose.Words
    pro .NET.
  headline: Skrytí okraje oblasti vykreslování ve sloupcovém grafu pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se skrýt okraj oblasti vykreslování grafu a zároveň zachovat
    viditelné osové čáry ve sloupcovém grafu v dokumentu Word pomocí Aspose.Words
    pro .NET.
  name: Skrytí okraje oblasti vykreslování ve sloupcovém grafu pomocí Aspose.Words
    pro .NET
  steps:
  - name: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte do dokumentu sloupcový graf o rozměrech 432 × 252 a získejte jeho
      objekt Chart.
    text: Vložte do dokumentu sloupcový graf o rozměrech 432 × 252 a získejte jeho
      objekt Chart.
  - name: Vymažte všechny existující řady, definujte tři štítky kategorií a přidejte
      do grafu řadu se vzorovými hodnotami.
    text: Vymažte všechny existující řady, definujte tři štítky kategorií a přidejte
      do grafu řadu se vzorovými hodnotami.
  - name: Nastavte šířku tahu (stroke weight) oblasti vykreslování na nulu, čímž odstraníte
      její okraj a zachováte viditelné osové čáry.
    text: Nastavte šířku tahu (stroke weight) oblasti vykreslování na nulu, čímž odstraníte
      její okraj a zachováte viditelné osové čáry.
  - name: Uložte upravený dokument do souboru .docx.
    text: Uložte upravený dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Vlastnost `Stroke` patří k celkovému formátu objektu `Chart`, který kreslí
      obdélníkový okraj kolem oblasti vykreslování; osové čáry jsou samostatné objekty
      `Axis` a nejsou ovlivněny nastavením `Stroke` grafu.
    question: Proč nastavení `columnChart.Format.Stroke.Weight = 0` odstraní okraj
      oblasti vykreslování, ale ponechá osové čáry viditelné?
  - answer: Ne, vlastnost `Stroke` řídí celý okraj oblasti vykreslování jako jeden
      obdélník, takže částečné okraje nelze skrýt pomocí Aspose.Words; museli byste
      překrýt vlastní tvary nebo graf upravit ručně.
    question: Mohu skrýt jen jednu stranu okraje oblasti vykreslování (např. levý
      okraj) a zachovat ostatní tři strany?
  - answer: Ano, vlastnost `Stroke` je nezávislá na `ChartType`, takže nastavení jejího
      `Weight` na 0 odstraní okraj oblasti vykreslování u čárových, koláčových i jakýchkoli
      jiných podporovaných typů grafů.
    question: Pokud změním typ grafu na čárový nebo koláčový, bude `columnChart.Format.Stroke.Weight
      = 0` stále skrývat okraj oblasti vykreslování?
  - answer: Není potřeba žádné další obnovení; vymazání řad a přidání nové aktualizuje
      graf interně a `wordDoc.Save(...)` zapíše aktuální stav do souboru .docx.
    question: Po zavolání `columnChart.Series.Clear()` musím graf před uložením dokumentu
      obnovit?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Skrytí okraje oblasti vykreslování ve sloupcovém grafu v dokumentu Word
og_description: Odeberte okraj oblasti vykreslování a zachovejte viditelné osové čáry ve sloupcovém grafu v dokumentu Word pomocí Aspose.Words pro .NET.
og_image_alt: Návod ukazující dokument Word se sloupcovým grafem, kde je okraj oblasti vykreslování skrytý, ale osové čáry zůstávají viditelné, pomocí Aspose.Words pro .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skrytí okraje oblasti vykreslování ve sloupcovém grafu pomocí Aspose.Words pro .NET
Cílem tohoto tutoriálu je naučit se, jak vytvořit dokument Word, vložit sloupcový graf, naplnit jej ukázkovými daty a poté skrýt okraj oblasti vykreslování grafu při zachování viditelných osových čar. Kód krok za krokem ukazuje každou operaci a končí uložením dokumentu, takže výsledek můžete vidět okamžitě.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Proč nastavení `columnChart.Format.Stroke.Weight = 0` odstraní okraj oblasti vykreslování, ale ponechá osové čáry viditelné?**  
A: Vlastnost `Stroke` patří k celkovému formátu objektu `Chart`, který kreslí obdélníkový okraj kolem oblasti vykreslování; osové čáry jsou samostatné objekty `Axis` a nejsou ovlivněny nastavením `Stroke` grafu.

**Q: Mohu skrýt jen jednu stranu okraje oblasti vykreslování (např. levý okraj) a zachovat ostatní tři strany?**  
A: Ne, vlastnost `Stroke` řídí celý okraj oblasti vykreslování jako jeden obdélník, takže částečné okraje nelze skrýt pomocí Aspose.Words; museli byste překrýt vlastní tvary nebo graf upravit ručně.

**Q: Pokud změním typ grafu na čárový nebo koláčový, bude `columnChart.Format.Stroke.Weight = 0` stále skrývat okraj oblasti vykreslování?**  
A: Ano, vlastnost `Stroke` je nezávislá na `ChartType`, takže nastavení jejího `Weight` na 0 odstraní okraj oblasti vykreslování u čárových, koláčových i jakýchkoli jiných podporovaných typů grafů.

**Q: Po zavolání `columnChart.Series.Clear()` musím graf před uložením dokumentu obnovit?**  
A: Není potřeba žádné další obnovení; vymazání řad a přidání nové aktualizuje graf interně a `wordDoc.Save(...)` zapíše aktuální stav do souboru .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}