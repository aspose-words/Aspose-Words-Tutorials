---
title: Odeberte řadu grafu z Word Documentu pomocí Aspose.Words pro .NET
weight: 510
limit:
description: Naučte se, jak smazat konkrétní datovou řadu ze sloupcového grafu ve Word dokumentu pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se, jak smazat konkrétní datovou řadu ze sloupcového grafu ve
    Word dokumentu pomocí Aspose.Words pro .NET.
  headline: Odeberte řadu grafu z Word Documentu pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se, jak smazat konkrétní datovou řadu ze sloupcového grafu ve
    Word dokumentu pomocí Aspose.Words pro .NET.
  name: Odeberte řadu grafu z Word Documentu pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový Word Document a DocumentBuilder, který je s ním propojen.
    text: Vytvořte nový Word Document a DocumentBuilder, který je s ním propojen.
  - name: Vložte sloupcový graf o velikosti 432 × 252 bodů a získejte objekt Chart
      pro další úpravy.
    text: Vložte sloupcový graf o velikosti 432 × 252 bodů a získejte objekt Chart
      pro další úpravy.
  - name: Definujte nulově‑založený index řady, která má být odstraněna (druhá řada).
    text: Definujte nulově‑založený index řady, která má být odstraněna (druhá řada).
  - name: Pokud je index platný, zavolejte RemoveAt na kolekci Series grafu, aby se
      řada smazala.
    text: Pokud je index platný, zavolejte RemoveAt na kolekci Series grafu, aby se
      řada smazala.
  - name: Uložte aktualizovaný dokument do souboru .docx.
    text: Uložte aktualizovaný dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Kontrola `if` (`targetSeriesIdx < columnChart.Series.Count`) selže, takže
      `RemoveAt` se nikdy nevyvolá a graf zůstane nezměněn.
    question: Co se stane, když předám index, který je roven počtu řad v grafu?
  - answer: Ano, po `columnChart.Series.RemoveAt` se legenda znovu vygeneruje tak,
      aby odrážela zbývající řady, a tak odstraněná položka zmizí z legendy.
    question: Zda odstranění řady automaticky aktualizuje legendu grafu?
  - answer: Kód funguje pro jakýkoli typ grafu, který podporuje kolekci `Series`;
      stačí při vkládání grafu změnit `ChartType.Column` na požadovaný typ.
    question: Mohu použít stejný kód k odstranění řady z čárového nebo koláčového
      grafu?
  - answer: Graf s nulovým počtem řad je stále platný `Shape` a bude uložen, ale v
      výsledném dokumentu se zobrazí prázdný.
    question: Pokud odstraním jedinou řadu v grafu, bude graf stále správně uložen?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Smazat řadu grafu ve Word dokumentu
og_description: Krok‑za‑krokem průvodce, jak odstranit datovou řadu z grafu ve Wordu pomocí Aspose.Words pro .NET.
og_image_alt: Průvodce ukazující, jak smazat konkrétní datovou řadu ze sloupcového grafu ve Word dokumentu pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Odeberte řadu grafu z Word Documentu pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak vytvořit Word dokument, přidat sloupcový graf pomocí DocumentBuilder a poté smazat konkrétní datovou řadu z tohoto grafu pomocí metody ChartSeriesCollection.RemoveAt. Na konci budete mít uložený dokument s odstraněnou nechtěnou řadou, což vám poskytne přesnou kontrolu nad obsahem grafu přímo z .NET kódu.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Co se stane, když předám index, který je roven počtu řad v grafu?**  
A: Kontrola `if` (`targetSeriesIdx < columnChart.Series.Count`) selže, takže `RemoveAt` se nikdy nevyvolá a graf zůstane nezměněn.

**Q: Zda odstranění řady automaticky aktualizuje legendu grafu?**  
A: Ano, po `columnChart.Series.RemoveAt` se legenda znovu vygeneruje tak, aby odrážela zbývající řady, a tak odstraněná položka zmizí z legendy.

**Q: Mohu použít stejný kód k odstranění řady z čárového nebo koláčového grafu?**  
A: Kód funguje pro jakýkoli typ grafu, který podporuje kolekci `Series`; stačí při vkládání grafu změnit `ChartType.Column` na požadovaný typ.

**Q: Pokud odstraním jedinou řadu v grafu, bude graf stále správně uložen?**  
A: Graf s nulovým počtem řad je stále platný `Shape` a bude uložen, ale v výsledném dokumentu se zobrazí prázdný.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}