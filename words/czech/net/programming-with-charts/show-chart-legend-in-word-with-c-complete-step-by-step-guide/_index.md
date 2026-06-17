---
category: general
date: 2026-06-02
description: Zobrazte legendu grafu ve Word dokumentu pomocí C#. Naučte se, jak přidat
  legendu, použít přednastavený styl grafu a během několika minut přizpůsobit vizuální
  podobu grafu ve Wordu.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: cs
og_description: Zobrazte legendu grafu v dokumentu Word okamžitě. Tento průvodce vás
  provede přidáním legendy, aplikací přednastaveného stylu grafu a řešením okrajových
  případů.
og_title: Zobrazte legendu grafu ve Wordu – kompletní C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Zobrazte legendu grafu ve Wordu pomocí C# – Kompletní průvodce krok za krokem
url: /cs/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazit legendu grafu ve Wordu pomocí C# – Kompletní průvodce krok za krokem

Už jste se někdy zamysleli **jak přidat legendu** do grafu, který je součástí dokumentu Word? Nejste v tom sami. V mnoha zprávách chybějící legenda způsobuje, že data vypadají tajemně, a opravit to by nemělo být obtížné.  

V tomto tutoriálu **zobrazíme legendu grafu** v souboru Word pomocí Aspose.Words pro .NET, použijeme předdefinovaný styl grafu a zajistíme, aby se legenda objevila přesně tam, kde ji potřebujete. Na konci budete mít připravený ukázkový kód, který můžete vložit do libovolného C# projektu.

## Co tento průvodce pokrývá

Provedeme celý pracovní postup:

1. Načíst existující *.docx*, který již obsahuje graf.  
2. Získat první graf (nebo jakýkoli graf, který chcete cílit).  
3. **Použít předdefinovaný styl grafu** pro profesionální vzhled.  
4. **Zobrazit legendu grafu**, umístit ji vpravo a ošetřit speciální případy, jako jsou vodopádové grafy.  
5. Uložit upravený dokument.

Žádné externí nástroje, žádné ruční manipulace s UI – jen čistý kód. Jedinou podmínkou je odkaz na NuGet balíček Aspose.Words (verze 23.10 nebo novější) a základní znalost C#.

---

## Požadavky

- .NET 6.0 nebo novější (ukázka funguje také s .NET Framework 4.7.2).  
- Knihovna Aspose.Words pro .NET nainstalována (`Install-Package Aspose.Words`).  
- Soubor Word (`input.docx`), který již obsahuje alespoň jeden graf.  
- Visual Studio, Rider nebo jakékoli IDE, které preferujete.

---

## Krok 1: Nastavení projektu a načtení dokumentu

Nejprve vytvořte konzolovou aplikaci (nebo integrujte kód do existujícího projektu). Přidejte `using` direktivy a načtěte soubor `.docx`.



```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Proč je to důležité:** Načtení dokumentu je základem. Bez instance `Document` nemůžete získat přístup k objektům grafu, které Aspose.Words poskytuje.

---

## Krok 2: Získání cílového grafu

Grafy jsou uloženy jako uzly ve stromu dokumentu. Metoda `GetChild` provádí hluboké vyhledávání, což nám umožňuje získat první graf bez ohledu na to, kde se nachází (hlavička, tělo, zápatí atd.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tip:** Pokud máte více grafů, změňte index `0` na `1`, `2`, … nebo iterujte přes `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Krok 3: Použití předdefinovaného vizuálního stylu

Atraktivní graf často začíná stylem. Aspose.Words obsahuje desítky vestavěných stylů; `ChartStyle.Style12` je čistá, moderní volba.



```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Jak to funguje:** Vlastnost `Style` odpovídá vestavěným stylům grafu ve Wordu, které vidíte v uživatelském rozhraní. Výběrem předvolby se vyhnete ručnímu nastavování barev, fontů a značek.

---

## Krok 4: Povolení legendy a její umístění

Nyní hvězda představení—**zobrazit legendu grafu**. Legendu zapneme a poté ji přichytíme na pravou stranu grafu.



```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Proč vpravo?** Umístění legendy vpravo zachovává širokou oblast dat, což je zvláště užitečné u sloupcových nebo pruhových grafů.

---

## Krok 5: Ošetření vodopádových grafů (speciální případ)

Vodopádové grafy se chovají trochu jinak; legenda může být ve výchozím nastavení skrytá. Následující podmínka zajistí, že legenda bude viditelná, když je typ grafu Waterfall.



```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Poznámka k okrajovému případu:** Některé starší verze Wordu ignorují `HasLegend` u vodopádových grafů, takže explicitní nastavení `Legend.Show` zaručuje viditelnost.

---

## Krok 6: Uložení upraveného dokumentu

Nakonec zapište změny zpět na disk. Můžete přepsat původní soubor nebo vytvořit nový.



```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Spuštěním programu vznikne `output.docx` s viditelnou legendou vpravo, stylizovanou pomocí `Style12`. Otevřete soubor ve Wordu a ověřte výsledek.

---

## Kompletní funkční příklad (všechny kroky dohromady)

Níže je kompletní, připravený k spuštění kód. Zkopírujte jej do `Program.cs` (nebo libovolného C# souboru) a upravte cesty k souborům.



```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Očekávaný výstup:** Otevřením `output.docx` uvidíte původní graf s pravě zarovnanou legendou, stylizovanou moderním `Style12`. Všechny datové řady jsou jasně označeny, což činí graf okamžitě srozumitelným.

---

## Často kladené otázky (FAQ)

### Jak přidat legendu ke konkrétnímu grafu (ne k prvnímu)?

Nahraďte index `0` v `GetChild(NodeType.Chart, 0, true)` nulovým (zero‑based) pořadím vašeho cílového grafu, nebo projděte všechny uzly grafu:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Můžu legendu umístit na spodní část místo vpravo?

Ano. Stačí změnit výčtový typ `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Co když graf už má legendu, ale chci ji skrýt?

Nastavte `HasLegend` na `false`:

```csharp
chart.HasLegend = false;
```

### Funguje to s Word 2010, 2016 a novějšími verzemi?

Ano. Aspose.Words abstrahuje podkladovou verzi Wordu, takže stejný kód funguje ve všech moderních .docx souborech.

---

## Profesionální tipy a běžné úskalí

- **Pro tip:** Po aplikaci stylu můžete stále upravovat jednotlivé prvky (barvy, popisky dat) pomocí kolekce `Chart.Series`. Styl vám poskytuje pevný základ.  
- **Watch out for:** Pokud je graf uvnitř buňky tabulky, může být legenda stísněná. Zvažte zvětšení velikosti grafu (`chart.Width`, `chart.Height`) před umístěním legendy.  
- **Performance note:** Načítání velkých dokumentů (stovky MB) může být náročné na paměť. Použijte `LoadOptions` s `LoadFormat.Docx` ke snížení režie, pokud potřebujete manipulovat jen s grafy.

---

## Další kroky

Nyní, když víte **jak přidat legendu** a **aplikovat předdefinovaný styl grafu** ve Wordu, můžete zkoumat:

- **Custom chart colors** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Data label formatting** (`chart.Series[i].HasDataLabel = true`).  
- **Exporting the chart as an image** (`chart.ToImage()`), useful for embedding elsewhere.  

Každé z těchto témat staví na stejném objektovém modelu, takže se naučíte snadno.

---

## Závěr

Právě jsme předvedli čisté, kompletní řešení pro **zobrazení legendy grafu** v dokumentu Word pomocí C#. Načtením dokumentu, získáním grafu, aplikací předdefinovaného stylu, povolením legendy a ošetřením specifik vodopádových grafů získáte vyladěný graf připravený pro jakoukoliv obchodní zprávu.  

Neváhejte experimentovat s dalšími hodnotami `ChartStyle` nebo pozicemi legendy – vaše datové vizualizace si zaslouží nejlepší prezentaci. Pokud narazíte na problémy, zanechte komentář níže; šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit sloupcový graf do dokumentu Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Skrýt osu grafu v dokumentu Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Používání Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}