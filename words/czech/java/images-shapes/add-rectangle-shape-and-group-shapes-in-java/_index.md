---
category: general
date: 2026-11-22
description: Přidejte obdélníkový tvar do dokumentu Word pomocí Javy, nastavte velikost
  tvaru, seskupte více tvarů a efektivně připojte tvar ke skupině.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: cs
lastmod: 2026-11-22
og_description: Přidejte obdélníkový tvar do dokumentu Word pomocí Javy, poté nastavte
  velikost tvaru, seskupte více tvarů a připojte tvar ke skupině v jediném pracovním
  postupu.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Přidejte obdélníkový tvar a seskupte tvary v Javě – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Přidat obdélníkový tvar a seskupit tvary v Javě
url: /cs/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání obdélníkového tvaru a seskupení tvarů v Javě

Pokud potřebujete **přidat obdélníkový tvar** do dokumentu Word pomocí Javy, tento návod vás provede přesnými kroky. Také se naučíte, jak **nastavit velikost tvaru**, **seskupit více tvarů** a **připojit tvar ke skupině** bez opuštění IDE.

Práce s vektorovou grafikou uvnitř souboru DOCX se často podobá žonglování různými API. Na konci tohoto tutoriálu budete mít jednorázový, samostatný program, který vytvoří obdélník, elipsu a libovolné další tvary, které potřebujete, a následně je seskupí, aby se pohybovaly jako jeden objekt. Žádné externí nástroje nejsou potřeba kromě Aspose.Words pro Javu.

## Požadavky

Než začnete, ujistěte se, že máte:

* Java 17 nebo novější nainstalovanou.
* Maven 3.8+ (nebo Gradle) pro správu závislostí.
* Platnou licenci Aspose.Words pro Javu (evaluační licence funguje pro testování).
* IDE jako IntelliJ IDEA nebo VS Code, i když stačí libovolný textový editor.

Tyto požadavky umožňují kódu kompilovat a spustit v jakémkoli moderním vývojovém prostředí.

## Krok 1: Nastavení Maven projektu

Vytvořte nový Maven projekt nebo přidejte závislost Aspose.Words do existujícího souboru `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Závislost stáhne všechny třídy potřebné pro manipulaci s dokumentem, včetně `Document`, `DocumentBuilder`, `Shape` a `GroupShape`. Maven automaticky stáhne JAR soubory při spuštění `mvn compile`.

## Krok 2: Načtení dokumentu a vytvoření DocumentBuilderu

`DocumentBuilder` poskytuje plynulé API pro vkládání obsahu. Načtěte existující DOCX nebo začněte s prázdným dokumentem:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Vytvoření builderu na začátku vám poskytne kurzor umístěný na začátku dokumentu, připravený pro vkládání tvarů.

## Přidání obdélníkového tvaru do dokumentu Word

### Krok 3: Vložení obdélníkového tvaru

Obdélník je první vizuální prvek, který chceme umístit do dokumentu. Použitím konstruktoru `Shape` s `ShapeType.RECTANGLE` získáte plně editovatelný objekt.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Přidání obdélníku v tomto okamžiku neovlivní rozvržení, dokud není definována jeho velikost a není připojen ke kontejneru.

### Nastavení velikosti a rozměrů tvaru

#### Krok 4: Definování šířky a výšky

Nastavení rozměrů tvaru určuje, jak se zobrazí na stránce. Hodnoty šířky a výšky jsou měřeny v bodech (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Tyto čísla můžete upravit podle požadavků vašeho designu. Stejné metody platí pro jakýkoli objekt `Shape`, takže je můžete znovu použít pro kruhy, šipky nebo vlastní kresby.

#### Krok 5: Vložení obdélníku do dokumentu

Nyní, když má obdélník velikost, umístěte jej na stránku. Metoda `insertShape` třídy `DocumentBuilder` přidá tvar na aktuální pozici kurzoru.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

V tomto okamžiku se obdélník zobrazuje sám na stránce. Další kroky ukážou, jak jej zkombinovat s dalšími tvary.

## Seskupení více tvarů dohromady

Seskupení tvarů vám umožní přesouvat, otáčet nebo měnit jejich velikost jako jeden celek. To je zvláště užitečné při tvorbě složitých diagramů.

### Krok 6: Vytvoření kontejneru pro skupinu tvarů

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Volání `insertGroupShape` přidá prázdný kontejner do dokumentu. Jakékoli tvary připojené k tomuto kontejneru se stanou součástí skupiny.

### Připojení tvaru ke skupině

#### Krok 7: Přidání obdélníku do skupiny

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Připojení přesune obdélník z těla dokumentu do interní kolekce skupiny. Obdélník nyní respektuje transformace skupiny.

#### Krok 8: Přidání elipsy pro demonstraci

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Elipsa sdílí stejný souřadnicový prostor jako obdélník, takže je můžete vizuálně zarovnat úpravou jejich vlastností `setLeft` a `setTop`, pokud je to potřeba.

### Krok 9: Uložení dokumentu

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Spuštěním programu se vygeneruje soubor `output.docx`. Otevřete jej v Microsoft Word nebo LibreOffice; uvidíte obdélník a elipsu seskupené dohromady. Výběrem libovolného tvaru se zvýrazní celá skupina, což potvrzuje, že **připojení tvaru ke skupině** bylo úspěšné.

![Add rectangle shape example in Java](image.png){alt="Příklad přidání obdélníkového tvaru v Javě"}

*Na snímku je obdélník a elipsa uvnitř jedné skupiny, připravené k společné manipulaci.*

## Proč je tento přístup důležitý

* **Jednotný zdroj pravdy** – Všechny vlastnosti tvaru jsou nastaveny před vytvořením skupiny, což zabraňuje problémům s rozvržením.
* **Znovupoužitelnost** – Metody `setWidth`/`setHeight` fungují pro jakýkoli tvar, takže můžete příklad rozšířit o šipky, hvězdy nebo vlastní SVG.
* **Výkon** – Seskupení snižuje počet kreslicích objektů, které musí Word renderovat, což zrychluje otevírání velkých dokumentů.
* **Údržba** – Držením logiky tvorby tvarů a jejich seskupování pohromadě mohou budoucí vývojáři měnit rozměry nebo přidávat nové tvary bez hledání v nesouvisejícím kódu.

## Běžné varianty a okrajové případy

| Scénář | Úprava |
|----------|------------|
| **Různé jednotky** | Použijte konverzi `PointsToPixels` nebo nastavte `Shape.setWrapType(WrapType.INLINE)` pro inline umístění. |
| **Otáčení skupiny** | Zavolejte `groupShape.setRotation(45);` pro otočení všech podřízených tvarů o 45°. |
| **Přidání textu do tvaru** | Použijte `Shape.setText("Label");` po nastavení velikosti. |
| **Dynamické velikosti** | Získejte rozměry stránky pomocí `doc.getFirstSection().getPageSetup().getPageWidth()` a vypočítejte velikosti tvarů úměrně. |

Tyto varianty ukazují, jak se základní vzor — **přidat obdélníkový tvar**, **nastavit velikost tvaru**, **seskupit více tvarů**, **připojit tvar ke skupině** — přizpůsobuje mnoha reálným požadavkům.

## Závěr

Nyní víte, jak **přidat obdélníkový tvar** do dokumentu Word pomocí Javy, **nastavit velikost tvaru**, **seskupit více tvarů** a **připojit tvar ke skupině** čistým a udržovatelným způsobem. Kompletní příklad se přeloží do jediné spustitelné třídy a výsledný soubor DOCX demonstruje očekávaný výstup.

Od sem můžete dále zkoumat:

* Přidávání textových popisků nebo hypertextových odkazů ke každému tvaru.
* Vnořování skupin pro tvorbu hierarchických diagramů.
* Export dokumentu do PDF při zachování skupin tvarů.

Neváhejte experimentovat s různými rozměry, barvami a dalšími typy tvarů. Ovládnutí manipulace s tvary otevírá dveře k automatizované tvorbě reportů, dynamickým diagramům a bohatým dokumentovým zážitkům – vše přímo z Java kódu.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}