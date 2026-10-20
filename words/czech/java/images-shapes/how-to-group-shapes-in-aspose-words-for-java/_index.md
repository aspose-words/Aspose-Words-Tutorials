---
category: general
date: 2026-10-20
description: Jak seskupit tvary v Aspose.Words pro Javu – naučte se, jak vložit obdélníkový
  tvar, seskupit je a uložit dokument v jednom průvodci.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: cs
lastmod: 2026-10-20
og_description: Jak seskupit tvary v Aspose.Words pro Java. Tento tutoriál ukazuje,
  jak vložit obdélníkový tvar, seskupit je a exportovat výsledek.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Jak seskupit tvary v Aspose.Words pro Java – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Jak seskupit tvary v Aspose.Words pro Javu
url: /cs/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary v Aspose.Words for Java

Pokud potřebujete **jak seskupit tvary** v dokumentu Word pomocí Aspose.Words for Java, tento průvodce vám ukáže kompletní pracovní postup. Naučíte se, jak **vložit obdélníkový tvar**, přidat druhý obdélník, seskupit oba tvary a nakonec soubor uložit – vše s jasným, spustitelným kódem.

Seskupování tvarů je užitečné, když chcete přesunout, otočit nebo stylovat několik kreslených objektů jako jednotku. Ať už vytváříte šablonu zprávy, diagram nebo vlastní leták, zvládnutí seskupování tvarů vám ušetří čas a zajistí konzistentní rozvržení.

V tomto tutoriálu se naučíte:

* Vytvořit nový `Document` a `DocumentBuilder`.
* **Jak vložit obdélník** s přesnými rozměry.
* Seskupit obdélníky do `GroupShape`.
* Uložit dokument a ověřit výsledek.

> **Předpoklad** – Musíte mít v projektu přidáno Aspose.Words for Java (v23.12 nebo novější). Uživatelé Maven mohou zahrnout závislost uvedenou níže.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Co budete potřebovat

| Položka | Důvod |
|------|--------|
| Java 17+ | Moderní jazykové funkce a lepší výkon |
| Aspose.Words for Java | Poskytuje API `DocumentBuilder`, `Shape` a `GroupShape` |
| IDE (IntelliJ IDEA, Eclipse, VS Code, atd.) | Pro kompilaci a spuštění příkladu |
| Oprávnění k zápisu do složky | Dokument bude uložen na disk |

---

## Jak vložit obdélníkový tvar

Prvním krokem je vytvořit `Document` a `DocumentBuilder`. Builder vám poskytuje metody jako `insertShape` pro umístění kreslených objektů.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Proč je to důležité** – Použití `insertShape` je standardní způsob **jak vložit obdélník** v Aspose.Words. Automaticky přidá tvar do aktuálního odstavce dokumentu, takže se nemusíte starat o nízkoúrovňové OpenXML.

---

## Úprava pozic obdélníků (volitelné)

Pokud druhý obdélník potřebuje vlastní umístění vzhledem k prvnímu, můžete upravit jeho vlastnosti `left` a `top`. Tento krok je volitelný, ale často nezbytný pro přesné rozvržení diagramu.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Tip:** Všechny rozměry jsou v bodech (1 pt ≈ 1/72 in). Použijte `convertPointsToPixels`, pokud potřebujete hodnoty v pixelech pro výpočty založené na UI.

---

## Jak seskupit tvary

Nyní, když jsou obdélníky vytvořeny, můžete je umístit do `GroupShape`. Seskupení způsobí, že se oba obdélníky chovají jako jeden objekt – přesun, otáčení nebo formátování skupiny ovlivní oba tvary.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Proč seskupování funguje** – `GroupShape` dědí z `Shape`, takže můžete se skupinou zacházet stejně jako s jakýmkoli jiným kresleným objektem. Když zavoláte `appendChild`, tvary jsou odstraněny ze své původní pozice a stanou se potomky skupiny.

---

## Uložení dokumentu obsahujícího seskupené tvary

Nakonec zapíšete dokument na disk. Soubor bude obsahovat jediný `GroupShape` se dvěma obdélníky uvnitř.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Očekávaný výsledek

Otevřete `GroupShape.docx` v Microsoft Word:

* Uvidíte dva obdélníky (modrý a zelený) umístěné vedle sebe.
* Výběrem kterékoli obdélníku vyberete celou skupinu – přetahování posune oba najednou.
* Skupina má tenký červený okraj, což potvrzuje, že se aplikovaly vlastnosti `GroupShape`.

Pokud kliknete pravým tlačítkem na skupinu a zvolíte **Group → Ungroup**, obdélníky se vrátí na samostatné tvary, což ukazuje, že operace seskupení je reverzibilní.

---

## Běžné varianty a okrajové případy

| Situace | Jak to řešit |
|-----------|------------------|
| **Více než dva tvary** | Vložte každý tvar a poté všechny přidejte do stejného `GroupShape`. |
| **Různé typy tvarů** (např. elipsa, obrázek) | Použijte `builder.insertShape(ShapeType.ELLIPSE, …)` nebo `builder.insertImage(...)` před přidáním. |
| **Změna měřítka skupiny** | Zavolejte `group.setWidth(newWidth)` nebo `group.setHeight(newHeight)`; potomci se měří proporčně. |
| **Rotace skupiny** | `group.setRotationAngle(45);` otočí celou kolekci kolem jejího středu. |
| **Zachování původních pozic** | Uložte hodnoty `left`/`top` každého tvaru před seskupením a po rozskupení je v případě potřeby obnovte. |

---

## Kompletní, spustitelný příklad

Níže je kompletní třída Java, kterou můžete zkopírovat a vložit do svého IDE. Obsahuje všechny importy, ošetření chyb a komentáře pro přehlednost.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Spusťte program, otevřete vzniklý `GroupShape.docx` a uvidíte seskupené obdélníky přesně tak, jak bylo popsáno.

---

## Závěr

Nyní už víte **jak seskupit tvary** v Aspose.Words for Java, od vytvoření dokumentu po vložení obdélníkových tvarů, úpravu jejich pozic a nakonec jejich seskupení pomocí `GroupShape`. Tato technika vám umožní zacházet s více kresbami jako s jednou entitou, což zjednodušuje úpravy rozvržení a zajišťuje vizuální konzistenci.

**Další kroky**

* Prozkoumejte **jak vložit obdélník** s různými vzory výplně nebo okraji.
* Kombinujte **vložit obdélníkový tvar** s textovými poli pro vytvoření popsaných diagramů.
* Experimentujte s otáčením nebo změnou měřítka skupiny pro tvorbu složitějších grafických prvků.

Neváhejte upravit kód pro jiné typy tvarů, větší skupiny nebo dynamické generování dokumentů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit obdélníkový tvar v Javě – seskupení a umístění tvarů](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [jak vložit skupinový tvar v Javě – kompletní průvodce](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Jak nastavit stín na tvar v Aspose.Words – kompletní průvodce](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}