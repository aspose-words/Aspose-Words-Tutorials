---
category: general
date: 2026-07-20
description: Jak vložit koláčový graf do Wordu pomocí Aspose.Words. Naučte se přidat
  procenta datových popisků a zobrazit procenta v grafu pro profesionální dokumenty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: cs
lastmod: 2026-07-20
og_description: jak vložit koláčový graf do Wordu pomocí Aspose.Words. Tento průvodce
  ukazuje, jak přidat procenta datových popisků a zobrazit procenta v grafu během
  několika řádků.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: jak vložit koláčový graf do Wordu – rychlý průvodce
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Jak vložit koláčový graf ve Wordu – přidat procenta do datových popisků
url: /cs/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit koláčový graf do Wordu – přidat procenta do popisků dat

Už jste se někdy zamýšleli **jak vložit koláčový graf** do dokumentu Word, aniž byste se museli potýkat s uživatelským rozhraním? Nejste v tom sami. V mnoha scénářích reportování potřebujete *přidat koláčový graf do Wordu* a, co je ještě důležitější, **zobrazit procenta na koláčovém grafu**, aby čtenáři okamžitě pochopili rozložení dat.

V tomto tutoriálu projdeme kompletním procesem pomocí Aspose.Words pro Java. Na konci budete přesně vědět, jak **přidat procenta do popisků dat**, **zobrazit procenta na grafu**, a získat vylepšený koláčový graf, který vypadá správně hned na první pokus. Žádné extra pluginy, žádné ruční úpravy – jen čistý kód, který můžete vložit do libovolného projektu.

---

## Požadavky

- Java 17 (nebo novější) – aktuální LTS verze, kterou Aspose.Words podporuje.
- Aspose.Words for Java 24.x (nejnovější v době psaní, červenec 2026).
- Základní nastavení Maven nebo Gradle pro stažení knihovny.
- IDE podle vašeho výběru (IntelliJ IDEA, Eclipse, VS Code… libovolné).

Pokud už máte vše připravené, skvěle – pojďme na to.

---

## Krok 1: Nastavení projektu a import knihovny

Nejprve přidejte závislost Aspose.Words do svého `pom.xml` (Maven) nebo `build.gradle` (Gradle). Tím získáte přístup ke třídám `Document`, `DocumentBuilder` a grafům.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Udržujte číslo verze aktuální; novější vydání často přidávají opravy související s grafy, které činí **display percentages on chart** spolehlivějším.

---

## Krok 2: Vytvoření nového Word dokumentu a builderu

Builder je vaše švýcarské armádní nůž pro vkládání obsahu. Zde vytvoříme nový dokument a připojíme k němu `DocumentBuilder`.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Proč potřebujeme builder? Abstrahuje nízkoúrovňové struktury OpenXML a umožňuje nám soustředit se na *co* chceme – například **add pie chart to word** – místo na *jak* vypadá XML.

---

## Krok 3: Vložení koláčového grafu

Nyní přichází jádro **how to insert pie chart**. Požádáme builder, aby umístil koláčový graf o konkrétní velikosti. Rozměry jsou v bodech (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

V tomto okamžiku je graf prázdný, ale zástupný objekt už je v dokumentu. Právě jste **add pie chart to word** programově.

---

## Krok 4: Naplnění grafu daty

Koláčový graf potřebuje alespoň jednu sérii hodnot. Pojďme mu dodat ukázková data představující podíl na trhu.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Pokud budete potřebovat více sérií (vrstvené koláče, donut grafy atd.), můžete zavolat `pieChart.getSeries().add()` a opakovat kroky. Stejná logika platí, když chcete **display percentages on chart** pro každou výseč.

---

## Krok 5: **add data label percent** – zobrazit procenta na výsečích

To je část, kterou většina vývojářů zapomene: nastavení popisků dat tak, aby ukazovaly procenta. Bez toho graf zobrazuje jen surová čísla, což může být nejasné.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Volání `setShowPercent(true)` říká Aspose.Words, aby vykreslil popisek jako “30 %”, “45 %” atd. To je přesně způsob, jak **show percent on pie chart** bez dalšího formátování.

---

## Krok 6: Uložení dokumentu

Nakonec zapíšeme dokument na disk. Můžete zvolit `.docx`, `.pdf` nebo dokonce `.html`. Pro tento návod zůstáváme u moderního formátu `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Spusťte program, otevřete `PieChartDemo.docx` a uvidíte pěkně vykreslený koláčový graf s procentními popisky na každé výseči.

---

## Očekávaný výstup

Níže je snímek obrazovky vygenerovaného souboru Word. Všimněte si, že každá výseč zobrazuje svůj podíl v procentech – přesně to, co jsme chtěli, když jsme nastavili **add data label percent**.

![Snímek obrazovky dokumentu Word obsahujícího koláčový graf s popisky procent](/images/pie-chart-percent.png){.center width=600px alt="Snímek obrazovky ukazující, jak vložit koláčový graf do Wordu s popisky procent"}

*Alt text obsahuje primární klíčové slovo, což splňuje jak SEO, tak přístupnost.*

---

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| **Mohu změnit font popisků procent?** | Ano. Po povolení `setShowPercent(true)` získáte objekt `DataLabel` a upravíte jeho vlastnost `Font` (`dataLabel.getFont().setSize(10);`). |
| **Co když potřebuji místo koláčového grafu donut graf?** | Nahraďte `ChartType.PIE` za `ChartType.DOUGHNUT` v volání `insertChart`. Stejná logika **add data label percent** funguje. |
| **Zobrazí starší verze Wordu (2007‑2010) procenta správně?** | Aspose.Words zapisuje podkladové XML nezávisle na verzi, takže procenta se zobrazí v jakémkoli Wordu, který podporuje grafy (2007+). |
| **Jak přidat název do grafu?** | Použijte `pieChart.getTitle().setText("Market Share");` před uložením. |
| **Mohu vložit graf do konkrétního odstavce nebo buňky tabulky?** | Ano. Přesuňte `DocumentBuilder` na požadované místo (`builder.moveToParagraph(index, true);` nebo `builder.moveToCell(table, row, column, true);`) před voláním `insertChart`. |

---

## Tipy a triky z praxe

- **Pro tip:** Pokud plánujete generovat mnoho grafů ve smyčce, znovu použijte jedinou instanci `DocumentBuilder`; snížíte tak zátěž paměti.
- **Dejte si pozor na:** Velmi malé výseče (< 2 %). Aspose.Words může popisek vynechat, aby se předešlo nepořádku; můžete jej vynutit pomocí `dataLabel.setShowLabel(true);`.
- **Poznámka k výkonu:** Vykreslování grafů je náročné na CPU. Pro hromadnou tvorbu reportů zvažte multithreading, ale ujistěte se, že každý vláken pracuje s vlastní instancí `Document`.
- **Kontrola verze:** Metoda `setShowPercent` byla zavedena v Aspose.Words 22.8. Pokud používáte starší verzi, aktualizujte ji nebo ručně vypočítejte procenta a nastavte je jako vlastní popisky.

---

## Shrnutí

Probrali jsme **how to insert pie chart** do Word dokumentu pomocí Aspose.Words, ukázali vám, jak **add data label percent**, a demonstrovali nejjednodušší způsob, jak **display percentages on chart**. Pouze několika řádky Java kódu můžete **add pie chart to word** a **show percent on pie chart**, čímž proměníte surová čísla na okamžitě čitelné vizuály.

---

## Co dál?

- Vyzkoušejte další typy grafů (`BAR`, `LINE`, `AREA`) a zjistěte, jak se stejná logika **add data label percent** uplatní.
- Kombinujte grafy s tabulkami pro bohatší reporty – Aspose.Words umožňuje snadno umístit graf vedle datové tabulky.
- Prozkoumejte export téhož dokumentu do PDF nebo HTML a podívejte se, jak se procenta vykreslují v různých formátech.

Klidně upravte rozměry, barvy nebo zdroj dat (např. dotaz do databáze) a sledujte, jak vaše Word reporty ožívají. Pokud narazíte na problém, zanechte komentář níže – šťastné grafování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vložit plošný graf do Word dokumentu | Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Vložit bublinový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}