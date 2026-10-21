---
category: general
date: 2026-07-16
description: Vytvořte koláčový graf v Javě pomocí Aspose.Words. Naučte se, jak přidat
  vodící čáry, zobrazit legendu grafu a oddělit výseč v jednom tutoriálu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: cs
lastmod: 2026-07-16
og_description: Vytvořte koláčový graf v Javě pomocí Aspose.Words. Tento průvodce
  ukazuje, jak přidat vodící čáry, zobrazit legendu grafu a oddělit výsek, což vám
  během několika minut poskytne vylepšený vizuální výstup.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Vytvořte koláčový graf pomocí Aspose.Words Java – Kompletní návod na formátování
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Vytvořte koláčový graf pomocí Aspose.Words Java – Kompletní průvodce krok za
  krokem
url: /cs/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření koláčového grafu pomocí Aspose.Words Java – Kompletní průvodce krok za krokem

Už jste se někdy zamýšleli, jak **vytvořit koláčový graf** programově v Javě, aniž byste se potýkali s nízkoúrovňovými kreslícími API? Nejste v tom sami. Mnoho vývojářů potřebuje rychlou vizualizaci pro zprávy, dashboardy nebo automatizované dokumenty a sáhnou po Aspose.Words, protože zvládá těžkou práci.  

V tomto tutoriálu projdeme kompletním, připraveným příkladem, který nejen **vytvoří koláčový graf**, ale také vám ukáže, jak **přidat vedoucí čáry**, **zobrazit legendu grafu** a dokonce **explodovat výsek** pro zdůraznění. Na konci budete mít soubor `.docx`, který vypadá dostatečně profesionálně, aby zaujal klienta.

> **Rychlý úspěch:** Níže uvedený úryvek kódu funguje ihned s Aspose.Words for Java 23.9 (nebo jakoukoli novější verzí). Žádné další závislosti, jen JAR.

## Co se naučíte

- Nastavit prázdný Word dokument pomocí `DocumentBuilder`.
- Vložit **koláčový graf** vlastní velikosti.
- Použít funkci **explodovat výsek** pro zvýraznění datového bodu.
- Povolit **vedoucí čáry**, aby explodovaný výsek zůstal spojený s popiskem.
- Zapnout **legendu grafu**, aby čtenáři mohli okamžitě identifikovat každý výsek.
- Uložit výsledek do souboru `.docx`, který můžete otevřít v Microsoft Word nebo LibreOffice.

**Prerequisites** – Budete potřebovat:

1. Nainstalovanou Javu 17 (nebo novější).
2. JAR Aspose.Words for Java ve vaší classpath.
3. Základní IDE nebo textový editor – IntelliJ IDEA, Eclipse, VS Code, nebo cokoli, co preferujete.

Teď se ponořme do toho.

## Krok 1: Inicializace dokumentu a builderu – Příprava na **vytvoření koláčového grafu**

Nejprve potřebujeme čisté plátno dokumentu. `Document` představuje celý Word soubor, zatímco `DocumentBuilder` je pomocník, který nám umožňuje přidávat obsah.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Proč je to důležité:** Začátek s čerstvým `Document` zaručuje, že nebudou žádné skryté styly nebo zbylé objekty, které by mohly narušit vykreslování grafu.

## Krok 2: Vložení **koláčového grafu** – Velikost má význam

Aspose.Words umožňuje vložení grafu jedním řádkem kódu. Zde požadujeme koláčový graf o rozměrech 400 × 300 bodů – přibližně 5,5 × 4,2 palce na typické obrazovce.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Tip:** Pokud potřebujete jinou velikost, stačí změnit oba číselné argumenty. API pracuje v bodech, kde 72 bodů = 1 palec.

## Krok 3: **Jak explodovat výsek** – Zvýraznění klíčového datového bodu

Explodování výseku jej vytáhne z ostatních částí koláče a upoutá pozornost čtenáře. Metoda `setExplosion` přijímá celé číslo představující vzdálenost v bodech.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Co když máte více sérií?** Můžete volat `setExplosion` na libovolném indexu série (`get(1)`, `get(2)`, …) a explodovat různé výseky.

## Krok 4: **Přidat vedoucí čáry** a **zobrazit legendu grafu** – Spojení bodů

Když je výsek explodován, popisek může odplout pryč. Vedoucí čáry udržují popisek připevněný, čímž zachovávají čitelnost. Současně legenda poskytuje rychlý klíč ke všem výsekům.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Proč povolit vedoucí čáry?** Bez nich může popisek vypadat, že levituje, a uživatelé nebudou vědět, ke kterému výseku patří.  
> **Potřebujete vlastní pozici legendy?** Použijte `chart.getLegend().setPosition(LegendPosition.TOP)` nebo jakoukoli jinou hodnotu enumu.

## Krok 5: Uložení dokumentu – Poslední krok **vytvoření koláčového grafu**

Nakonec dokument uložíme na disk. Přizpůsobte cestu do složky, do které máte právo zapisovat.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Spusťte program, otevřete vygenerovaný `PieChartDemo.docx` a měli byste vidět pěkně naformátovaný koláčový graf s explodovaným prvním výsekem, vedoucími čarami a viditelnou legendou.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Vytvořit příklad koláčového grafu s explodovaným výsekem, vedoucími čarami a legendou"}

### Očekávaný výstup

Když otevřete Word soubor, graf vypadá zhruba takto:

- Koláčový graf o rozměrech 400 × 300 pt.
- První výsek je posunut o 10 pt.
- Tenčí vedoucí čára spojuje explodovaný výsek s jeho popiskem.
- Legenda pod grafem uvádí název každé řady.

Pokud nevidíte vedoucí čáru, zkontrolujte, že `setLeaderLines(true)` je voláno *po* nastavení exploze – pořadí má význam.

## Časté úskalí a jak se jim vyhnout

| Problém | Proč se to stane | Řešení |
|-------|----------------|-----|
| **Legenda se nezobrazí** | `setShowLegend(true)` byl vynechán nebo volán na nesprávném objektu grafu. | Ujistěte se, že voláte `chart.setShowLegend(true)` **po** získání `Chart` z tvaru. |
| **Vedoucí čára chybí** | Výsek nebyl explodován, nebo typ grafu nepodporuje vedoucí čáry. | Pouze `ChartType.PIE` (nebo `PIE_3D`) podporuje vedoucí čáry. Nejprve zavolejte `setExplosion`, poté `setLeaderLines(true)`. |
| **Výsek se nepohybuje** | Hodnota exploze je příliš nízká (0‑2 pt). | Zvyšte celé číslo, např. `setExplosion(10)` nebo vyšší pro výraznější efekt. |
| **Graf vypadá deformovaně** | Použití nečtvercových rozměrů (šířka ≠ výška) může koláč deformovat. | Udržujte šířku a výšku stejnou nebo blízkou; 400 × 300 funguje, ale 400 × 400 dává dokonalý kruh. |

## Pokročilé úpravy (volitelné)

Pokud chcete jít dál než jen základy, zvažte:

- **Vlastní barvy**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Datové popisky**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D efekt**: Nahraďte `ChartType.PIE` za `ChartType.PIE_3D`.

Tyto možnosti vám umožní doladit vizuál tak, aby odpovídal firemním brandingovým směrnicím.

## Shrnutí – Co jsme dosáhli

Začali jsme s prázdným Word dokumentem, **vytvořili koláčový graf**, **explodovali první výsek**, **přidali vedoucí čáry** a **zobrazili legendu grafu**. Celý tok se vejde do stručné metody `main`, což usnadňuje jeho začlenění do větších reportingových pipeline.

## Další kroky

- **Přidat více řad**: Naplňte graf skutečnými daty z databáze nebo CSV.
- **Export do PDF**: Použijte `doc.save("output.pdf", SaveFormat.PDF);` k vytvoření PDF verze.
- **Kombinovat s dalšími tvary**: Vložte tabulky, obrázky nebo další grafy pro kompletní zprávu.

Pokud vás zajímají jiné typy grafů – sloupcové, pruhové, čárové – stačí nahradit `ChartType.PIE` odpovídajícím enumem a postupovat podle stejných kroků formátování.

*Šťastné grafování!* Neváhejte zanechat komentář, pokud něco nefungovalo podle očekávání, nebo sdílet, jak jste přizpůsobili pozici legendy. Vaše zpětná vazba pomáhá všem vytvářet lepší automatizované dokumenty.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak vytvořit PDF dokumenty pomocí Aspose.Words pro Java | Document Processing API](/words/english/java/)
- [Jak přidat vodoznak do dokumentů pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}