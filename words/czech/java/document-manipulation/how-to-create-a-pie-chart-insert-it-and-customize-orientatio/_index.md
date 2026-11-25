---
category: general
date: 2026-11-25
description: Naučte se, jak vytvořit koláčový graf v Javě, vložit koláčový graf do
  dokumentu Word, rozdělit výseč a změnit orientaci grafu pomocí přehledných ukázek
  kódu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: cs
lastmod: 2026-11-25
og_description: Vytvořte koláčový graf v Javě, vložte koláčový graf do dokumentu,
  oddělte výsek koláče a změňte orientaci grafu pomocí kódu krok za krokem.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Vytvořte koláčový graf v Javě – vložte, vytáhněte výsek a otočte
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Jak vytvořit koláčový graf, vložit jej a přizpůsobit orientaci v Javě
url: /cs/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit koláčový graf, vložit jej a přizpůsobit orientaci v Javě

Pokud potřebujete **vytvořit koláčový graf** uvnitř dokumentu Word, tento návod vám přesně ukáže, jak na to. Uvidíte, jak **vložit koláčový graf**, rozšířit výseč pro zdůraznění a **změnit orientaci grafu** pomocí jednoduché rotace.

Návod pokrývá vše, co potřebujete—od nastavení knihovny Aspose.Words for Java po vytvoření finálního souboru `.docx`, který zobrazuje otočený, rozšířený koláčový graf. Není potřeba žádná externí dokumentace; stačí postupovat podle kroků a spustit kód.

## Požadavky

* Nainstalovaný Java 17 nebo novější.
* Maven nebo Gradle pro správu závislostí.
* Platná licence Aspose.Words for Java (nebo použijte režim bezplatného hodnocení).

Přidejte závislost Aspose.Words do svého `pom.xml` (Maven) nebo `build.gradle` (Gradle). Příklad pro Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Tip:** Udržujte verzi knihovny aktuální; nejnovější vydání (24.10 v době psaní) obsahuje opravy chyb při vykreslování grafů.

## Krok 1: Vytvořit koláčový graf a vložit jej do dokumentu

Prvním krokem je **vytvořit objekty koláčového grafu** a vložit je do souboru Word. Níže uvedený kód vytvoří jednoduchý dokument, přidá zástupný prvek grafu a vloží koláčový graf o rozměrech 400 × 300 pixelů.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Proč je to důležité:** `builder.insertChart` vytvoří zástupný prvek grafu, který Aspose.Words automaticky při uložení dokumentu převede na OOXML graf. Argument `ChartType.PIE` říká knihovně, aby vykreslila koláčový graf, čímž splňuje požadavek **vložit koláčový graf**.

## Krok 2: Rozšířit výseč koláčového grafu pro zvýraznění segmentu

Rozšíření výseče přitahuje pozornost k určitému datovému bodu. Následující řádek rozšíří první výseč (index 0) o 10 bodů:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Můžete změnit index, aby cílil na jinou výseč, nebo upravit vzdálenost rozšíření pro jemnější efekt. Rozšíření výseče je standardní způsob, jak **rozšířit výseč koláčového grafu** v Aspose.Words.

## Krok 3: Změnit orientaci grafu otáčením

Otočení grafu poskytuje nový vizuální úhel pohledu. Použijte `setRotationAngle` k otáčení celého grafu ve směru hodinových ručiček (úhel se měří ve stupních).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Výše uvedené volání splňuje požadavky **otočit koláčový graf** a **změnit orientaci grafu**. Přijímá se libovolný úhel mezi 0 a 360 stupni.

## Kompletní spustitelný příklad

Spojením všech částí zde máte kompletní, samostatný program, který vytváří koláčový graf, rozšiřuje výseč a otáčí graf. Spusťte jej z vašého IDE nebo z příkazové řádky pomocí `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Očekávaný výstup

* Soubor pojmenovaný **CreatePieChartDemo.docx** se objeví v pracovním adresáři.
* Otevřením souboru v Microsoft Word se zobrazí koláčový graf o rozměrech 400 × 300 pixelů.
* První výseč (Q1) je posunuta ven o 10 bodů, čímž vzniká efekt **rozšířit výseč koláčového grafu**.
* Celý graf je nakloněn o 45 stupňů, což demonstruje **změnu orientace grafu** a **otočení koláčového grafu**.

## Běžné varianty a okrajové případy

| Situace | Jak upravit kód |
|-----------|-----------------------|
| **Jiná velikost grafu** | Změňte argumenty `400, 300` v `insertChart`. |
| **Více sérií** | Přidejte další objekty `ChartSeries` do `chart.getSeries()`. |
| **Rozšířit jinou výseč** | Použijte `setExplode(sliceIndex, distance)` s požadovaným `sliceIndex`. |
| **Rotace není potřeba** | Vynechte volání `setRotationAngle` nebo nastavte úhel na `0`. |
| **Export do PDF místo DOCX** | Po vytvoření dokumentu zavolejte `doc.save("output.pdf")` s formátem PDF. |

> **Pozor:** Použití záporné vzdálenosti rozšíření vyvolá `IllegalArgumentException`. Vždy zadejte nezápornou hodnotu.

## Tip pro výkon

Pokud generujete mnoho grafů ve smyčce, znovu použijte jediný `DocumentBuilder` a pro každou iteraci zavolejte pouze `insertChart`. Tím se sníží zatížení paměti a zrychlí zpracování.

## Závěr

Nyní víte, jak **vytvořit koláčový graf**, **vložit koláčový graf**, **rozšířit výseč koláčového grafu** a **otočit koláčový graf** pomocí Aspose.Words for Java. Kompletní příklad ukazuje celý pracovní postup—od inicializace dokumentu po uložení souboru, který vizualizuje otočený, rozšířený koláčový graf.

Dále můžete prozkoumat **změnu orientace grafu** pomocí 3‑D efektů, nebo experimentovat s jinými typy grafů, jako jsou **Bar** nebo **Line**. Stejné vzory API platí, takže rozšíření tohoto návodu je jednoduché.

Neváhejte upravit data, index výseče nebo úhel rotace tak, aby odpovídaly vašim potřebám reportování, a sdílejte své výsledky s komunitou!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vložit koláčový graf do dokumentu Word pomocí Javy](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Jak rozšířit výseč koláčového grafu v Javě – tutoriál grafu Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}