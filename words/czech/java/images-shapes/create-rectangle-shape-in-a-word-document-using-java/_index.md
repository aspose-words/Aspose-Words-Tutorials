---
category: general
date: 2026-11-15
description: Vytvořte obdélníkový tvar ve Wordu pomocí Javy a naučte se, jak přidávat
  tvary do Wordu, nastavit rozměry tvaru a efektivně uložit dokument Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: cs
lastmod: 2026-11-15
og_description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí Javy. Naučte se
  přidávat tvary do Wordu, nastavit rozměry tvaru a během několika minut uložit Word
  dokument.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Vytvořte obdélníkový tvar ve Wordu pomocí Javy – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Vytvořte obdélníkový tvar v dokumentu Word pomocí Javy
url: /cs/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Word dokumentu pomocí Javy

Pokud potřebujete **vytvořit obdélníkový tvar** uvnitř souboru Word, tento návod vám ukáže přesně, jak to provést v Javě. Uvidíte, jak **přidávat tvary do Wordu**, jak **nastavit rozměry tvaru**, a nakonec **uložit Word dokument** přímo z IDE.

V následujících sekcích získáte kompletní, spustitelný příklad, vysvětlení každého řádku a tipy na běžné úskalí, jako jsou problémy s velikostí a kompatibilitou dokumentu. Žádné externí odkazy nejsou potřeba — pouze knihovna Aspose.Words for Java.

## Co se naučíte

* Jak inicializovat `Document` a `DocumentBuilder`.
* Jak vložit **skupinový tvar** a umístit do něj obdélník.
* Jak **definovat velikost tvaru** pomocí `setWidth` a `setHeight`.
* Jak **uložit Word dokument** ve formátu `.docx`.
* Řešení okrajových případů pro různé velikosti stránek a nastavení DPI.

### Předpoklady

* Java 17 nebo novější (kód se také kompiluje s Java 8).
* Aspose.Words for Java 23.10 nebo novější — knihovnu můžete získat z Maven Central.
* Základní znalost syntaxe Javy a objektově orientovaných konceptů.

> **Pro tip:** Pokud plánujete později přidávat další tvary (např. kruhy nebo textová pole), udržujte je uvnitř stejného `GroupShape`. To usnadní přesouvání, otáčení nebo formátování celé kolekce.

## Krok 1: Inicializace dokumentu a builderu

Prvním krokem je vytvořit prázdný Word soubor a `DocumentBuilder`, který vám umožní zapisovat obsah.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité:* `Document` představuje celý soubor, zatímco `DocumentBuilder` poskytuje vysoce‑úrovňové metody pro vkládání textu, tabulek a **tvarů**. Bez builderu byste museli manipulovat s nízko‑úrovňovými uzly ručně.

## Krok 2: Vložení skupinového tvaru pro více tvarů

**Skupinový tvar** funguje jako kontejner; můžete do něj přidat několik tvarů a později s nimi zacházet jako s jedním objektem (např. přesunout nebo otočit najednou).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Proč použít skupinový tvar?* Pokud později přidáte šipky, kruhy nebo popisky kolem obdélníku, skupina udrží vše zarovnané. Také zjednodušuje workflow **add shapes to Word**, protože pro každý nový tvar stačí jediný volání `appendChild`.

## Krok 3: Vytvoření obdélníkového tvaru

Nyní vytvoříme skutečný obdélník, který bude uvnitř skupiny. Konstruktor `Shape` potřebuje vlastnický `Document` a typ požadovaného tvaru.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Proč obdélník?* `ShapeType.RECTANGLE` je nejčastější primitivum pro zvýraznění sekcí, vytváření zástupných objektů nebo kreslení jednoduchých UI mock‑upů přímo ve Wordu.

## Krok 4: Definování velikosti obdélníku

Nastavení rozměrů je místo, kde se **set shape dimensions** stává klíčovým. Můžete použít libovolnou jednotku podporovanou Aspose.Words; výchozí jsou body (1 pt = 1/72 palce).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Poznámka:** Pokud dáváte přednost milimetrům, zavolejte `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`, kde `1.39 in ≈ 35 mm`. Tím se demonstruje flexibilita **define shape size**.

## Krok 5: Přidání obdélníku do skupinového tvaru

Připojením obdélníku k dříve vytvořené skupině se zobrazí v dokumentu.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

V tomto okamžiku je obdélník umístěn v levém horním rohu skupiny. Později jej můžete přesunout pomocí `rectangle.setLeft(...)` a `rectangle.setTop(...)`, pokud potřebujete přesné umístění.

## Krok 6: (Volitelné) Uložení dokumentu pro zobrazení výsledku

Nakonec zapíšeme dokument na disk. Toto je krok **save Word document**, který vytvoří soubor `.docx`, který můžete otevřít v Microsoft Word, LibreOffice nebo Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Spuštěním programu vznikne `RectangleShapeDemo.docx` obsahující jediný obdélník uvnitř skupinového tvaru. Otevřením souboru uvidíte čistý bílý obdélník — přesně ve velikosti, kterou jste definovali.

### Očekávaný výstup

* Word soubor pojmenovaný `RectangleShapeDemo.docx`.
* V prvním odstavci skupinový tvar obsahující obdélník 100 pt × 50 pt.
* Žádný text není přidán, takže se obdélník objeví na prázdné stránce.

## Běžné varianty a okrajové případy

| Situace | Jak upravit kód |
|-----------|-----------------------|
| **Jiná velikost stránky** (např. A4) | Zavolejte `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` před vložením tvaru. |
| **Vyšší DPI pro tisk** | Vynásobte šířku/výšku požadovaným DPI faktorem, např. `rectangle.setWidth(200 * 2);` pro dvojnásobné rozlišení. |
| **Přidání textové popisky uvnitř obdélníku** | Vytvořte `Shape` typu `TEXT_BOX`, nastavte jeho `setWidth`/`setHeight` tak, aby odpovídaly obdélníku, a přidejte jej do stejného `GroupShape`. |
| **Otočení obdélníku** | Použijte `rectangle.setRotationAngle(45);` pro otočení o 45 stupňů ve směru hodinových ručiček. |
| **Uložení jako PDF místo DOCX** | Nahraďte `document.save("output.docx");` řádkem `document.save("output.pdf");` — stejná API funguje i pro PDF, zachovává obdélník. |

## Pro tipy pro robustní implementaci

1. **Znovu použijte builder** — po vložení skupinového tvaru můžete pokračovat v přidávání odstavců nebo tabulek bez vytvoření nové instance builderu.
2. **Uvolněte zdroje** — i když garbage collector v Javě zvládá většinu objektů, explicitní volání `document.close();` (při práci se streamy) zabraňuje únikům souborových handle.
3. **Ověřte rozměry** — před voláním `setWidth`/`setHeight` se ujistěte, že hodnoty jsou kladné; záporné hodnoty vyvolají `IllegalArgumentException`.
4. **Kompatibilita verzí** — kód funguje s Aspose.Words 23.x a novějšími. Starší verze mohou vyžadovat `Shape.setSize(width, height)` místo samostatných setterů.

## Kompletní, spustitelný příklad

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Ověření výsledku:** Otevřete `output/RectangleShapeDemo.docx` v Microsoft Word. Měli byste vidět obdélník požadované velikosti, umístěný uprostřed horní části první stránky. Pokud se obdélník jeví příliš malý, upravte hodnoty předávané do `setWidth` a `setHeight`.

## Závěr

Nyní víte, jak **create rectangle shape** v souboru Word pomocí Javy, jak **add shapes to Word** prostřednictvím `GroupShape`, jak **set shape dimensions** a **define shape size**, a nakonec jak **save Word document** pro další distribuci. Stejný vzor funguje i pro jiné typy tvarů, což vám umožní programově vytvářet složité diagramy.

### Co dál?

* Prozkoumejte **add shapes to Word** vložením kruhů, šipek nebo textových polí.
* Spojte více tvarů do jednoho `GroupShape` a aplikujte transformace (otočení, převrácení).
* Generujte reporty, které vkládají grafy jako tvary, a pak **save Word document** jako PDF pro sdílení.

Neváhejte experimentovat s rozměry, barvami a umístěním, aby vyhovovaly vašemu konkrétnímu scénáři. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}