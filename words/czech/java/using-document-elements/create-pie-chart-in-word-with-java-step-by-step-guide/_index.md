---
category: general
date: 2026-08-14
description: Vytvořte koláčový graf ve Wordu pomocí Javy a Aspose.Words. Naučte se,
  jak přidat data řady do grafu a otočit výsek koláčového grafu během několika řádků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: cs
lastmod: 2026-08-14
og_description: Vytvořte koláčový graf ve Wordu pomocí Javy a Aspose.Words. Tento
  návod ukazuje, jak rychle přidat data řady do grafu a otočit výseč koláčového grafu.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Vytvořte koláčový graf ve Wordu pomocí Javy – kompletní průvodce kódováním
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Vytvořte koláčový graf ve Wordu pomocí Javy – krok za krokem
url: /cs/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření koláčového grafu ve Wordu pomocí Javy – krok za krokem

Pokud potřebujete **vytvořit koláčový graf ve Wordu** programově, tento návod vám přesně ukáže, jak to provést pomocí Javy a Aspose.Words. Naučíte se kompletní workflow, od vložení grafu po přidání datových bodů a otočení první výseče.

Generování grafu přímo v souboru `.docx` odstraňuje ruční krok kopírování‑vkládání a umožňuje automatizovat zprávy, faktury nebo dashboardy. Během návodu také pokryjeme **jak přidat data řady do grafu** a jak **otočit výseč koláčového grafu** pro lepší vizuální zdůraznění.

## Vytvoření koláčového grafu ve Wordu – přehled

Aspose.Words for Java poskytuje plynulé API `DocumentBuilder`, které může vložit objekt grafu do dokumentu Word. Typ grafu, který zvolíte, určuje výchozí rozvržení a můžete přizpůsobit řady, barvy, úhly a dokonce přepnout na tvar donutu jedním voláním metody.

### Proč používat Aspose.Words?

* **No Microsoft Office required** – knihovna funguje na jakémkoli serveru nebo v CI prostředí.  
* **Full .docx fidelity** – vygenerovaný graf vypadá identicky jako ten vytvořený ručně ve Wordu.  
* **Single‑file dependency** – stačí přidat JAR a jste připraveni.

## Jak přidat data řady do grafu

Graf bez dat je jen zástupný objekt. Objekt `Chart` poskytuje kolekci `Series`; každá řada obsahuje seznam číselných hodnot, které odpovídají výsečím (pro koláč) nebo bodům (pro čáru). Přidání dat je jednoduché:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Co kód dělá:**  
* `chart.getSeries()` vrací `List<ChartSeries>`.  
* `get(0)` vybírá první řadu, protože koláčový graf obsahuje podle definice pouze jednu řadu.  
* `add(double)` přidá datový bod. Hodnoty jsou automaticky převedeny na procenta, která dohromady dávají 100 % při vykreslení grafu.

> **Tip:** Pokud váš zdroj dat obsahuje více než tři kategorie, pokračujte v přidávání hodnot stejným způsobem. Aspose.Words automaticky vytvoří další výseče.

## Otočení výseče koláčového grafu

Někdy chcete, aby konkrétní výseč začínala pod určitým úhlem, aby nejdůležitější segment směřoval k divákovi. Metoda `setFirstSliceAngle(double)` otáčí celý graf, čímž efektivně posouvá začátek první výseče:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Úhel se měří ve stupních po směru hodinových ručiček od svislé osy. Nastavením na `0` (výchozí) se první výseč umístí nahoře. Upravením hodnoty můžete zvýraznit výseč nebo splnit designové směrnice.

> **Často kladená otázka:** *Ovlivňuje otáčení pořadí dat?*  
> Ne. Pořadí dat zůstává stejné; mění se pouze vizuální výchozí pozice.

## Kompletní Java příklad

Níže je kompletní, připravený k spuštění program, který vytvoří dokument Word s koláčovým grafem, přidá data řady, otočí výseč a uloží soubor. Všechny potřebné importy jsou uvedeny, takže můžete kód zkopírovat do libovolného IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Očekávaný výstup

* Soubor pojmenovaný **PieChart.docx** se objeví ve složce `output`.  
* Otevřením souboru v Microsoft Word se zobrazí barevný koláčový graf se třemi výsečemi (40 %, 30 %, 30 %).  
* Graf je otočen o 45° po směru hodinových ručiček, takže první výseč začíná mírně vpravo od svislé osy.

## Časté problémy a osvědčené postupy

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Graf se zobrazuje prázdně** | Dokument byl uložen před tím, než byl graf plně vykreslen. | Zavolejte `doc.save()` **po** všech úpravách grafu. |
| **Hodnoty výsečí nesčítají na 100 %** | Přidání surových čísel, která nepředstavují procenta, může vést k neočekávanému škálování. | Poskytněte hodnoty, které logicky představují podíly celku, nebo nechte Aspose.Words vypočítat procenta automaticky. |
| **Otáčení nemá žádný efekt** | Použití `ChartType.DOUGHNUT` bez nastavení `holeSize` může skrýt efekt otáčení. | Nechte graf jako `PIE` nebo upravte `holeSize` po nastavení úhlu. |
| **Chyby cesty k souboru** | Relativní cesty se mohou lišit při řešení na Windows vs. Linuxu. | Použijte `Paths.get("output", "PieChart.docx").toString()` nebo absolutní cestu pro produkční kód. |

### Tipy pro produkční použití

* **Reuse the `DocumentBuilder`** – můžete vložit více grafů do stejného dokumentu opakovaným voláním `insertChart`.  
* **Styling** – použijte `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` k zobrazení procent přímo v grafu.  
* **Performance** – vygenerujte graf jednou a klonujte jej (`chart.deepClone()`), pokud potřebujete identické grafy na více místech.

## Otočení výseče koláčového grafu – pokročilé scénáře

- **Dynamic angle** – vypočítejte úhel na základě dat (např. nechte největší výseč začít nahoře).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
- **Multiple series** – i když koláčový graf má obvykle jednu řadu, Aspose.Words vám umožní přidat více pro vrstvené koláče. Otáčení se stále vztahuje pouze na první řadu.

## Závěr

Nyní víte, jak **vytvořit koláčový graf ve Wordu** pomocí Javy, jak **přidat data řady do grafu** a jak **otočit výseč koláčového grafu** pro vizuální zdůraznění. Kompletní příklad demonstruje celý workflow – od inicializace dokumentu po uložení finálního souboru `.docx` – takže můžete integraci generování grafů použít v jakémkoli automatizovaném reportovacím řetězci.

### Co dál?

- Prozkoumejte další typy grafů (`ChartType.BAR`, `ChartType.LINE`) a rozšiřte svůj automatizační nástroj.  
- Kombinujte generování grafů s **mail merge** pro tvorbu personalizovaných zpráv pro každého příjemce.  
- Ponořte se do **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) a přizpůsobte grafy firemnímu brandingu.

Klidně experimentujte s různými datovými sadami, úhly a styly grafů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}