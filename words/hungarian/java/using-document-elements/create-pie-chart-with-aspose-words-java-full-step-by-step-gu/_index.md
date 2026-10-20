---
category: general
date: 2026-07-16
description: Készíts kördiagramot Java-ban az Aspose.Words használatával. Ismerd meg,
  hogyan adhatsz hozzá vezetővonalakat, jelenítheted meg a diagram jelmagyarázatát,
  és hogyan robbantsz szét egy szeletet egyetlen útmutatóban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: hu
lastmod: 2026-07-16
og_description: Készíts kördiagramot Java-ban az Aspose.Words használatával. Ez az
  útmutató megmutatja, hogyan adhat hozzá vezetővonalakat, jelenítheti meg a diagram
  jelmagyarázatát, és szétrobálhat egy szeletet, így percek alatt egy kifinomult vizuális
  megjelenést érhet el.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Kördiagram létrehozása Aspose.Words Java-val – Teljes formázási útmutató
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
title: Kördiagram létrehozása az Aspose.Words Java segítségével – Teljes lépésről‑lépésre
  útmutató
url: /hu/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram létrehozása Aspose.Words Java‑val – Teljes lépésről‑lépésre útmutató

Gondolkodtál már azon, hogyan **hozz létre kördiagramot** programozottan Java‑ban anélkül, hogy alacsony szintű rajzoló API‑kkal kellene küzdened? Nem vagy egyedül. Sok fejlesztőnek gyors vizuális megjelenítésre van szüksége jelentésekhez, műszerfalakhoz vagy automatizált dokumentumokhoz, és az Aspose.Words‑ra támaszkodik, mert elvégzi a nehéz munkát.

Ebben az útmutatóban egy teljes, azonnal futtatható példán keresztül vezetünk végig, amely nem csak **kördiagramot hoz létre**, hanem megmutatja, hogyan **adjunk hozzá vezetővonalakat**, **jelenítsük meg a diagram jelmagyarázatát**, és még **szétrobban egy szeletet** a hangsúlyozáshoz. A végére egy olyan `.docx` fájlt kapsz, amely elég kifinomult ahhoz, hogy lenyűgözze az ügyfelet.

> **Gyors eredmény:** Az alábbi kódrészlet azonnal működik az Aspose.Words for Java 23.9‑el (vagy bármely újabb verzióval). Nincs extra függőség, csak a JAR.

## Mit fogsz megtanulni

- Állíts be egy üres Word dokumentumot a `DocumentBuilder`‑rel.
- Helyezz be egy **kördiagramot** egy egyedi mérettel.
- Használd a **szétrobbanó szelet** funkciót egy adatpont kiemeléséhez.
- Engedélyezd a **vezetővonalakat**, hogy a szétrobbanó szelet kapcsolódjon a címkéhez.
- Kapcsold be a **diagram jelmagyarázatát**, hogy az olvasók azonnal azonosíthassák a szeleteket.
- Mentsd el az eredményt egy `.docx` fájlba, amelyet megnyithatsz a Microsoft Word‑ben vagy a LibreOffice‑ban.

**Előfeltételek** – Szükséged lesz:

1. Java 17 (vagy újabb) telepítve.  
2. Aspose.Words for Java JAR a classpath‑odban.  
3. Alap IDE vagy szövegszerkesztő – IntelliJ IDEA, Eclipse, VS Code, vagy bármelyik, amit kedvelsz.

Most merüljünk el.

## 1. lépés: A dokumentum és a builder inicializálása – Felkészülés a **kördiagram létrehozására**

Először egy tiszta dokumentumvászonra van szükségünk. A `Document` a teljes Word fájlt képviseli, míg a `DocumentBuilder` egy segédeszköz, amely lehetővé teszi a tartalom hozzáadását.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Miért fontos:** Egy friss `Document`‑tel kezdve garantált, hogy nincsenek rejtett stílusok vagy maradvány objektumok, amelyek zavarhatják a diagram megjelenítését.

## 2. lépés: A **kördiagram** beszúrása – A méret számít

Aspose.Words a diagram beszúrását egyetlen sorra egyszerűsíti. Itt egy 400 × 300 pont méretű kördiagramot kérünk – nagyjából 5,5 × 4,2 hüvelyk egy tipikus képernyőn.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tipp:** Ha más méretre van szükséged, egyszerűen módosítsd a két numerikus argumentumot. Az API pontokban dolgozik, ahol 72 pont = 1 hüvelyk.

## 3. lépés: **Hogyan robbantsuk szét a szeletet** – Egy kulcsfontosságú adatpont hangsúlyozása

A szelet szétrobbanása kiemeli azt a kör többi részéből, így a szem a fontos adatpontra irányul. A `setExplosion` metódus egy egész számot vár, amely a távolságot pontokban adja meg.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Mi van, ha több sorozatod van?** A `setExplosion`‑t bármely sorozat indexén (`get(1)`, `get(2)`, …) meghívhatod, hogy különböző szeleteket robbants ki.

## 4. lépés: **Vezetővonalak hozzáadása** és **diagram jelmagyarázat megjelenítése** – A pontok összekapcsolása

Amikor egy szelet ki van robbantva, a címke eltolódhat. A vezetővonalak a címkét rögzítik, megőrizve az olvashatóságot. Eközben a jelmagyarázat gyors kulcsot nyújt az összes szelethez.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Miért engedélyezzük a vezetővonalakat?** Nélkülük a címke lebegőnek tűnhet, és összezavarhatja a felhasználókat, hogy melyik szelethez tartozik.  
> **Szükséged van egy egyedi jelmagyarázat pozícióra?** Használd a `chart.getLegend().setPosition(LegendPosition.TOP)`‑t vagy bármely más enum értéket.

## 5. lépés: A dokumentum mentése – Az utolsó **kördiagram létrehozása** lépés

Végül a dokumentumot lemezre mentjük. Állítsd be az elérési utat egy olyan mappára, amelyhez írási jogosultságod van.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Futtasd a programot, nyisd meg a generált `PieChartDemo.docx` fájlt, és egy szépen formázott kördiagramot kell látnod, amelynek az első szelete ki van robbantva, van vezetővonal és látható jelmagyarázat.

![Kördiagram példa, amely szétrobbanó szeletet és jelmagyarázatot mutat](pie-chart-example.png){: .center-image alt="Kördiagram példa, amely szétrobbanó szeletet és jelmagyarázatot mutat"}

### Várt kimenet

Amikor megnyitod a Word fájlt, a diagram nagyjából így néz ki:

- Egy 400 × 300 pt kördiagram.  
- Az első szelet 10 pt távolságra van eltolva.  
- Egy vékony vezetővonal kapcsolja a szétrobbanó szeletet a címkéhez.  
- A diagram alatti jelmagyarázat felsorolja minden sorozat nevét.

Ha nem látod a vezetővonalat, ellenőrizd, hogy a `setLeaderLines(true)` a robbantás beállítása *után* van-e meghívva – a sorrend számít.

## Gyakori buktatók és hogyan kerüld el őket

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| **Nincs jelmagyarázat** | `setShowLegend(true)` hiányzott vagy a rossz diagram objektumon lett meghívva. | Győződj meg arról, hogy a `chart.setShowLegend(true)` **után** a `Chart` lekérése a shape‑ból van meghívva. |
| **Hiányzó vezetővonal** | A szelet nem lett szétrobbanva, vagy a diagram típusa nem támogatja a vezetővonalakat. | Csak a `ChartType.PIE` (vagy `PIE_3D`) támogatja a vezetővonalakat. Először hívd meg a `setExplosion`‑t, majd a `setLeaderLines(true)`‑t. |
| **A szelet nem mozog** | A robbantás értéke túl alacsony (0‑2 pt). | Növeld az egész számot, például `setExplosion(10)` vagy nagyobbat a drámaibb hatásért. |
| **A diagram torzult** | Nem négyzetes méret (szélesség ≠ magasság) használata összenyomhatja a kört. | Tartsd a szélességet és magasságot egyenlő vagy közel egyenlő értéken; a 400 × 300 működik, de a 400 × 400 tökéletes kört ad. |

## Haladó finomhangolások (opcionális)

Ha szeretnél túllépni az alapokon, fontold meg a következőket:

- **Egyéni színek**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Adatcímkék**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D hatás**: Cseréld le a `ChartType.PIE`‑t `ChartType.PIE_3D`‑re.

Ezek az opciók lehetővé teszik, hogy finomhangold a megjelenést a vállalati arculati irányelveknek megfelelően.

## Összefoglalás – Mit értünk el

Egy üres Word dokumentummal kezdtünk, **létrehoztunk egy kördiagramot**, **szétrobbantuk az első szeletet**, **hozzáadtuk a vezetővonalakat**, és **megjelenítettük a diagram jelmagyarázatát**. Az egész folyamat egy tömör `main` metódusba illeszkedik, így könnyen beágyazható nagyobb jelentéscsővezetékekbe.

## Következő lépések

- **További sorozatok hozzáadása**: Töltsd fel a diagramot valós adatokkal egy adatbázisból vagy CSV‑ből.  
- **Exportálás PDF‑be**: Használd a `doc.save("output.pdf", SaveFormat.PDF);`‑t PDF verzió generálásához.  
- **Kombinálás más alakzatokkal**: Szúrj be táblázatokat, képeket vagy további diagramokat egy teljes jelentéshez.

Ha érdekelnek más diagramtípusok – oszlop, sáv, vonal – egyszerűen cseréld le a `ChartType.PIE`‑t a megfelelő enumra, és kövesd ugyanazokat a formázási lépéseket.

---

*Boldog diagramkészítést!* Nyugodtan hagyj megjegyzést, ha valami nem működött a várttal, vagy oszd meg, hogyan testreszabtad a jelmagyarázat pozícióját. A visszajelzésed segít mindannyiunknak jobb automatizált dokumentumokat építeni.

## Mit érdemes legközelebb megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Hogyan hozzunk létre PDF dokumentumokat az Aspose.Words for Java‑val | Document Processing API](/words/english/java/)
- [Hogyan adjunk hozzá vízjelet a dokumentumokhoz az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}