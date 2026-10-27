---
category: general
date: 2026-10-26
description: Vytvořte prstencový graf a vložte koláčový graf v Javě pomocí krok‑za‑krokem
  kódu. Naučte se kompletní workflow pro flexibilní vizualizace grafů.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: cs
lastmod: 2026-10-26
og_description: Vytvořte prstencový graf v Javě pomocí tohoto návodu, který také ukazuje,
  jak vložit koláčový graf pro flexibilní vizualizace.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Vytvořte prstencový graf a vložte koláčový graf – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Jak vytvořit prstencový graf a vložit koláčový graf
url: /cs/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit donutový graf a vložit koláčový graf

Pokud potřebujete **vytvořit donutový graf** v Javě, tento tutoriál vás provede přesnými kroky. Také ukážeme, jak **vložit koláčový graf** pomocí stejného builder API, takže můžete snadno přepínat mezi vizuálními styly. Na konci průvodce budete mít kompletní, spustitelný program, který vytváří oba typy grafů a demonstruje běžná přizpůsobení.

Tutoriál pokrývá:

* Inicializaci builderu grafu poskytovaného vybranou knihovnou.  
* Vytvoření donutového grafu a nastavení velikosti díry.  
* Vložení koláčového grafu a „explodování“ výseče pro zdůraznění.  
* Tipy pro řešení okrajových případů, jako jsou chybějící série nebo nepodporované typy grafů.

Stačí vám aktuální JDK (8 nebo novější) a JAR knihovny grafů na classpath. Žádné externí služby nejsou potřeba.

---

## Požadavky

| Položka | Důvod |
|------|--------|
| Java Development Kit (JDK) 8+ | Vyžadováno pro kompilaci a spuštění příkladu. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Poskytuje `ChartBuilder`, `ChartType` a metody pro manipulaci se sériemi použité v kódu. |
| An IDE or a text editor | Pro psaní a spuštění Java souboru. |

Ujistěte se, že je JAR knihovny přidán do cesty sestavení vašeho projektu. Pokud používáte Maven, přidejte odpovídající závislost; jinak umístěte JAR do složky `libs` a odkažte na něj při kompilaci.

---

## Krok 1: Nastavení builderu grafu

Prvním krokem je vytvořit instanci `ChartBuilder` (nebo ekvivalent), která bude generovat objekty grafů. Tento objekt funguje jako továrna a drží list nebo plátno, kam bude graf umístěn.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Proč je to důležité:**  
Builder spojuje graf s konkrétním listem, čímž zajišťuje, že všechny následné objekty grafu sdílejí stejný kreslicí povrch. Vynechání tohoto kroku by vám nechalo bez cílového umístění pro vizuální prvky.

---

## Krok 2: **Vytvořit donutový graf**

Nyní vygenerujeme donutový graf s definovanou velikostí. Velikost díry určuje, kolik prostoru uprostřed grafu zůstane prázdné, čímž se běžný koláčový graf změní na donutový.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Vysvětlení:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` vytvoří objekt grafu a rezervuje místo na listu.  
* `setHoleSize(30)` převádí koláč na donut s 30 % prázdným středem.  
* `add("{10, 20, 30, 40}", true)` poskytuje čtyři datové body; příznak `true` říká knihovně, aby hodnoty považovala za jednu sérii.

**Okrajový případ:** Pokud vybraný typ grafu nepodporuje díru (např. sloupcový graf), volání `getDoughnutChart()` vyvolá výjimku. Vždy před úpravou velikosti díry ověřte typ grafu.

---

## Krok 3: **Vložit koláčový graf**

Po vytvoření donutového grafu ukážeme, jak **vložit koláčový graf** pomocí stejného builderu. Tento krok zdůrazňuje podobnost obou typů grafů a ukazuje, jak zvýraznit výseč.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Vysvětlení:**  

* `ChartType.PIE` říká builderu, aby vytvořil klasický koláčový graf.  
* `setExplode(10)` posune první výseč o 10 % poloměru, což je běžná technika pro zvýraznění klíčového datového bodu.  

**Tip:** Metoda `setExplode` funguje pouze na první sérii koláčového grafu. Pokud máte více sérií, musíte cílit na správný index.

---

## Krok 4: Uložit sešit

Nakonec zapíšeme sešit do souboru, abyste mohli grafy zobrazit v Excelu nebo jakémkoli kompatibilním prohlížeči.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Proč uložit nyní:** Uložení sešitu finalizuje všechny kreslicí operace. Pokus o zobrazení souboru před uložením vede k prázdnému nebo neúplnému dokumentu.

**Výsledek:** Otevření *DoughnutAndPieChart.xlsx* ukazuje donutový graf s 30 % dírou vlevo a koláčový graf s „explodovanou“ první výsečí vpravo.

---

## Krok 5: Běžné varianty a řešení problémů

| Situace | Úprava |
|-----------|------------|
| **Různé rozměry grafu** | Změňte argumenty šířky a výšky v `insertChart`. |
| **Více datových sérií** | Zavolejte `add` vícekrát nebo předávejte řetězec 2‑D pole. |
| **Dynamická velikost díry** | Vypočítejte velikost díry na základě rozsahu dat a poté zavolejte `setHoleSize`. |
| **Explodovat více výsečí** | Pro každou výseč, kterou chcete posunout, použijte `chart.getSeries().get(i).setExplode(percent)`. |
| **Knihovna nepodporuje donut** | Použijte koláčový graf a ručně nakreslete bílý kruh jako překryv, i když je to méně přesné. |

**Pro tip:** Vždy po vložení grafů (pokud je k dispozici) zavolejte `builder.flush()`. Tím se uvolní interní buffery a zabrání se únikům paměti.

---

![Java kód vytvářející donutový graf a vkládající koláčový graf](https://example.com/images/doughnut-pie-java.png "příklad vytvoření donutového grafu v Javě")

*Obrázek ilustruje finální rozložení sešitu s oběma grafy vedle sebe.*

---

## Závěr

Nyní víte, jak **vytvořit donutový graf** a **vložit koláčový graf** v Javě pomocí plynulého builder API. Kompletní příklad zahrnuje inicializaci, konfiguraci velikosti, nastavení díry, „explodování“ výseč a výstup do souboru. Odtud můžete zkoumat další přizpůsobení, jako jsou barvy, legendy a popisky dat, aby vyhovovaly vašim požadavkům na reportování.

**Další kroky**

* Experimentujte s **chart customization Java** funkcemi, jako jsou gradientní výplně a popisky dat.  
* Integrovat generování grafů do webové služby, která vrací sešit na požádání.  
* Porovnejte přístup builderu s jinými knihovnami (např. JFreeChart), abyste vybrali nejlepší řešení pro svůj projekt.

Šťastné vytváření grafů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Jak vytvořit donutový graf ve Word dokumentu pomocí Javy](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Uložit Word dokument po úpravě donutového grafu v Javě](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Vložit koláčový graf v Javě – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}