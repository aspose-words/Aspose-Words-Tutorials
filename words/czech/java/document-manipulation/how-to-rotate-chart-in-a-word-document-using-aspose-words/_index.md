---
category: general
date: 2026-10-10
description: Naučte se, jak otočit graf v souboru Word a upravit graf ve Wordu tak,
  aby změnil velikost prstencového grafu, s kompletním příkladem v Javě.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: cs
lastmod: 2026-10-10
og_description: Jak otočit graf v souboru Word a upravit graf ve Wordu pro změnu velikosti
  prstencového grafu pomocí Aspose.Words pro Javu.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Jak otočit graf v dokumentu Word – krok za krokem Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak otočit graf v dokumentu Word pomocí Aspose.Words
url: /cs/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak otočit graf v dokumentu Word pomocí Aspose.Words

Pokud potřebujete **otočit graf** uvnitř souboru Microsoft Word, tento návod vám ukáže přesné kroky. Také se naučíte, jak **upravit graf ve Wordu** a **změnit velikost prstencového grafu** aniž byste opustili svůj Java kód.

Automatizace Wordu se často jeví jako řada nesouvislých volání API, ale s Aspose.Words můžete zacházet s grafem jako s libovolným jiným uzlem dokumentu. Na konci tohoto tutoriálu budete mít spustitelný program, který načte existující `.docx`, otočí prstencový graf o 45°, zmenší díru na 50 % poloměru a výsledek uloží jako nový soubor.

## Požadavky

Než začnete, ujistěte se, že máte:

* Java 17 nebo novější nainstalovanou.
* Maven (nebo Gradle) pro správu závislostí.
* Vstupní Word dokument (`input.docx`) již obsahující prstencový graf.
* Platnou licenci Aspose.Words pro Java (nebo použijte režim hodnocení).

## Krok 1: Nastavení Maven projektu

Vytvořte nový Maven projekt nebo přidejte následující závislost do svého existujícího `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Spuštěním `mvn clean install` se knihovna stáhne a třídy budou dostupné ve vašem classpath.

## Krok 2: Načtení Word dokumentu, který obsahuje graf

Prvním krokem je otevřít existující dokument. Třída `Document` představuje celý soubor.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Načtení souboru **nemění** jeho obsah; pouze vytvoří v‑paměti reprezentaci, kterou můžete dotazovat a upravovat.

## Krok 3: Vytvoření DocumentBuilderu pro navigaci

`DocumentBuilder` poskytuje API podobné kurzoru pro procházení stromu dokumentu. Použijeme jej k nalezení první grafické podoby.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder začíná na začátku dokumentu, ale později jej můžete přesunout na libovolný uzel, pokud bude potřeba.

## Krok 4: Získání první grafické podoby

Grafy jsou uloženy jako uzly typu `Shape`. Filtrováním podřízených uzlů typu `NodeType.SHAPE` můžeme získat objekt grafu.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Pokud dokument obsahuje více grafů, můžete iterovat přes `getChildNodes` a u každého `Shape` zkontrolovat `hasChart()` před přetypováním.

## Krok 5: Otočení grafu (jak otočit graf)

Prstencový graf je v podstatě koláčový graf s dírou. Otočením změníte úvodní úhel první výseče.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Metoda `setStartAngle` očekává `double` představující stupně. Kladné hodnoty otáčejí po směru hodinových ručiček, záporné proti směru hodinových ručiček.

## Krok 6: Změna velikosti díry prstence (změna velikosti prstencového grafu)

Velikost díry je vyjádřena jako zlomek poloměru grafu. Hodnota `0.5` znamená, že díra zabírá 50 % celkového poloměru.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** Platný rozsah je `0.0` (žádná díra, tj. běžný koláč) až `0.9` (velmi tenký prsten). Hodnoty mimo tento rozsah vyvolají `IllegalArgumentException`.

## Krok 7: Uložení upraveného dokumentu

Nakonec zapíšete změny zpět na disk.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Když otevřete `DoughnutFormatted.docx` v Microsoft Word, uvidíte prstencový graf otočený o 45° a díru zmenšenou na polovinu původní velikosti.

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte kompletní program, který můžete zkopírovat a vložit do svého IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Očekávaný výstup

Po spuštění programu se vypíše:

```
Chart rotated and doughnut size changed successfully.
```

Otevření `DoughnutFormatted.docx` zobrazí prstencový graf, jehož první výseč začíná v pozici 45° a vnitřní poloměr zabírá polovinu vnějšího poloměru.

## Běžné varianty a okrajové případy

| Situace | Co upravit | Proč je to důležité |
|-----------|----------------|----------------|
| **Více grafů** | Procházet `getChildNodes(NodeType.SHAPE, true)` a u každého kontrolovat `shape.hasChart()` | Zajišťuje, že upravujete požadovaný graf, nikoli první nalezený |
| **Sloupcový nebo čárový graf** | `setStartAngle` se neuplatní; použijte `chart.getSeries().get(0).setFillFormat(...)` pro jiné vizuální úpravy | Ne všechny typy grafů podporují otočení; pouze prstencové/koláčové mají úvodní úhel |
| **Graf bez díry prstence** | Přeskočte `setDoughnutHoleSize` nebo nejprve změňte typ grafu na prstenec pomocí `chart.setChartType(ChartType.DONUT)` | Změna velikosti díry u grafu, který není prstencový, vyvolá výjimku |
| **Velké dokumenty** | Použijte `DocumentBuilder.moveToDocumentStart()` a `builder.moveToNode(chartShape)` pro cílenou navigaci | Zlepšuje výkon tím, že se vyhnete úplnému procházení nesouvisejících uzlů |

## Profesionální tipy pro spolehlivou manipulaci s grafy

* **Uložte odkaz na graf** – Pokud plánujete měnit více vlastností, uchovejte si lokální proměnnou `Chart` místo opakovaného volání `chartShape.getChart()`.
* **Ověřte vstupní hodnoty** – Před voláním `setStartAngle` nebo `setDoughnutHoleSize` zkontrolujte, že jsou v platném rozsahu, abyste předešli chybám za běhu.
* **Použijte licenci** – Režim hodnocení vloží vodoznak na první stránku. Použití licence (`License license = new License(); license.setLicense("Aspose.Words.lic");`) jej odstraní.

## Další kroky

Nyní, když víte, **jak otočit graf** a **změnit velikost prstencového grafu**, můžete prozkoumat další scénáře **úpravy grafu ve Wordu**:

* Změňte barvy výsečí pomocí `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Přidejte popisky dat voláním `chart.getSeries().get(0).setHasDataLabel(true)`.
* Exportujte graf jako obrázek pomocí `chart.toImage(300, 300, ImageType.PNG)`.

Každé z těchto rozšíření následuje stejný vzor: získáte objekt `Chart`, zavoláte příslušný setter a dokument uložíte.

---

**Právě jste zvládli otáčet a měnit velikost prstencových grafů ve Wordu pomocí Javy.** Klidně upravte kód pro jiné typy grafů, integrujte jej do většího pipeline pro generování dokumentů nebo jej kombinujte s Aspose.Slides pro automatizaci PowerPointu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením krok za krokem, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}