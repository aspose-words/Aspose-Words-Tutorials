---
title: Aktualizace dat řad grafu v dokumentu Word pomocí Aspose.Words pro .NET
weight: 610
limit:
description: Naučte se upravovat datové body řad grafu v dokumentu Word a obnovit graf pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se upravovat datové body řad grafu v dokumentu Word a obnovit
    graf pomocí Aspose.Words pro .NET.
  headline: Aktualizace dat řad grafu v dokumentu Word pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se upravovat datové body řad grafu v dokumentu Word a obnovit
    graf pomocí Aspose.Words pro .NET.
  name: Aktualizace dat řad grafu v dokumentu Word pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový Document, vložte sloupcový graf pomocí DocumentBuilder a uložte
      jej jako počáteční soubor.
    text: Vytvořte nový Document, vložte sloupcový graf pomocí DocumentBuilder a uložte
      jej jako počáteční soubor.
  - name: Otevřete uložený soubor a najděte tvar grafu, abyste získali existující
      objekt Chart.
    text: Otevřete uložený soubor a najděte tvar grafu, abyste získali existující
      objekt Chart.
  - name: Vymažte hodnoty první řady a přidejte nové body, poté upravte druhou řadu
      odebráním jejího prvního bodu a přidáním nového.
    text: Vymažte hodnoty první řady a přidejte nové body, poté upravte druhou řadu
      odebráním jejího prvního bodu a přidáním nového.
  - name: Uložte upravený dokument do nového souboru obsahujícího aktualizovaný graf.
    text: Uložte upravený dokument do nového souboru obsahujícího aktualizovaný graf.
  type: HowTo
- questions:
  - answer: Použijte `document.GetChildNodes(NodeType.Shape, true)` k získání všech
      tvarů, poté filtrujte pomocí `s.HasChart` a vyberte první (nebo ten, který potřebujete)
      – tím se vyhnete výběru nesouvisejících obrázků nebo textových polí.
    question: Jak mohu spolehlivě najít tvar grafu v dokumentu, který může obsahovat
      i jiné tvary?
  - answer: '`ClearValues()` odstraňuje existující datové body; bez něj jsou nové
      body připojeny k těm starým, což může vést k duplicitním kategoriím nebo nesprávným
      součtům.'
    question: Proč musím zavolat `ClearValues()` před přidáním nových bodů do řady?
  - answer: Použijte `FromString`, když jsou kategorie osy X grafu textové (např.
      „Group A“), a `FromDouble`, když osa očekává číselné hodnoty, jako jsou data
      nebo měření.
    question: Kdy bych měl použít `ChartXValue.FromString` místo `ChartXValue.FromDouble`
      pro hodnoty osy X?
  - answer: Pokus o přístup k neexistující řadě vyvolá `ArgumentOutOfRangeException`;
      vždy před odkazováním na konkrétní index zkontrolujte `existingChart.Series.Count`.
    question: Co se stane, pokud má graf jen jednu řadu a pokusím se přistoupit k
      `existingChart.Series[1]`?
  - answer: Uložení `openedDoc` stačí, protože jde o instanci dokumentu, která obsahuje
      upravený graf; původní `document` byl použit jen k vytvoření počátečního souboru.
    question: Musím po úpravě grafu znovu uložit původní `document`, nebo je uložení
      `openedDoc` dostačující?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Úprava dat řad grafu ve Wordu
og_description: Průvodce krok za krokem, jak změnit hodnoty řad grafu v souboru Word pomocí Aspose.Words pro .NET.
og_image_alt: Průvodce ukazující dokument Word se sloupcovým grafem před a po aktualizaci dat jeho řad pomocí Aspose.Words pro .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizace dat řad grafu v dokumentu Word pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak vytvořit dokument Word obsahující sloupcový graf, poté soubor znovu otevřít, získat existující řady grafu, upravit jejich datové body a dokument uložit tak, aby graf zobrazoval nové hodnoty. Postupujte podle krok‑za‑krokem kódu a uvidíte, jak snadné je programově upravit data grafu pomocí Aspose.Words pro .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Jak mohu spolehlivě najít tvar grafu v dokumentu, který může obsahovat i jiné tvary?**  
A: Použijte `document.GetChildNodes(NodeType.Shape, true)` k získání všech tvarů, poté filtrujte pomocí `s.HasChart` a vyberte první (nebo ten, který potřebujete) – tím se vyhnete výběru nesouvisejících obrázků nebo textových polí.

**Q: Proč musím zavolat `ClearValues()` před přidáním nových bodů do řady?**  
A: `ClearValues()` odstraňuje existující datové body; bez něj jsou nové body připojeny k těm starým, což může vést k duplicitním kategoriím nebo nesprávným součtům.

**Q: Kdy bych měl použít `ChartXValue.FromString` místo `ChartXValue.FromDouble` pro hodnoty osy X?**  
A: Použijte `FromString`, když jsou kategorie osy X grafu textové (např. „Group A“), a `FromDouble`, když osa očekává číselné hodnoty, jako jsou data nebo měření.

**Q: Co se stane, pokud má graf jen jednu řadu a pokusím se přistoupit k `existingChart.Series[1]`?**  
A: Pokus o přístup k neexistující řadě vyvolá `ArgumentOutOfRangeException`; vždy před odkazováním na konkrétní index zkontrolujte `existingChart.Series.Count`.

**Q: Musím po úpravě grafu znovu uložit původní `document`, nebo je uložení `openedDoc` dostačující?**  
A: Uložení `openedDoc` stačí, protože jde o instanci dokumentu, která obsahuje upravený graf; původní `document` byl použit jen k vytvoření počátečního souboru.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}