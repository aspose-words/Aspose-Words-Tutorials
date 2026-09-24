---
category: general
date: 2026-09-24
description: Naučte se, jak v Javě vytvořit prázdný dokument Word a seskupit tvary,
  jako jsou obdélníky a čáry, pomocí Aspose.Words. Obsahuje kód krok za krokem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: cs
lastmod: 2026-09-24
og_description: Vytvořte prázdný dokument Word v Javě a naučte se seskupovat tvary,
  přidávat obdélníkový tvar a nastavovat velikost tvaru pomocí Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Vytvořte prázdný dokument Word a seskupte tvary v Javě – průvodce krok za
  krokem
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak vytvořit prázdný dokument Word a seskupit tvary v Javě
url: /cs/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a seskupit tvary v Javě

Pokud potřebujete **vytvořit prázdný dokument Word** a poté uspořádat více kreslicích objektů, tento návod vám přesně ukáže, jak na to. Pomocí Aspose.Words pro Java můžete vložit skupinový tvar, přidat obdélníkový tvar, nakreslit čáru a ovládat velikost a umístění každého tvaru – vše v jednom spustitelném programu.

Provedeme vás každým krokem, od inicializace dokumentu až po uložení finálního `.docx`. Na konci pochopíte **jak seskupit tvary**, **přidat obdélníkový tvar** a **nastavit velikost tvaru**, aby vaše soubory Word vypadaly přesně podle představ.

## Požadavky

- Java 17 nebo novější (kód se kompiluje s libovolným aktuálním JDK)
- Knihovna Aspose.Words pro Java (stáhněte z [Aspose website](https://products.aspose.com/words/java))
- IDE nebo nástroj pro sestavení (Maven/Gradle), který dokáže přidat Aspose.Words JAR do classpath
- Základní znalost syntaxe Javy

> **Tip:** Použijte Maven pro správu závislostí; přidejte `com.aspose:aspose-words:23.12` (nebo nejnovější verzi) do vašeho `pom.xml`.

## Krok 1: Vytvořit prázdný dokument Word

Prvním úkolem je **vytvořit prázdný dokument Word**. To vám poskytne čisté plátno, na které můžete později vkládat tvary.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité:* Objekt `Document` představuje celý soubor `.docx`. Začátek s prázdným dokumentem zajišťuje, že žádné skryté formátování nezasahuje do tvarů, které přidáte.

## Krok 2: Vložit skupinový tvar – kontejner pro více objektů

**Skupinový tvar** funguje jako kontejner, který vám umožní přesouvat, měnit velikost nebo otáčet několik tvarů najednou. To je podstata **jak seskupit tvary** ve Wordu.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Vysvětlení:* Metoda `insertGroupShape` vytvoří objekt `GroupShape` a umístí jej na aktuální pozici kurzoru. Všechny následné tvary, které pomocí `appendChild` přidáte do této skupiny, budou považovány za jedinou jednotku.

## Krok 3: Přidat obdélníkový tvar a nastavit jeho velikost

Nyní **přidáme obdélníkový tvar** do skupiny a **přesně nastavíme velikost tvaru**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Proč je potřeba nastavit velikost tvaru:* Šířka a výška určují, jak se obdélník zobrazí na stránce. Metody `setLeft` a `setTop` umisťují obdélník relativně k počátku skupiny, což vám poskytuje pixel‑přesnou kontrolu rozvržení.

## Krok 4: Přidat čárový tvar a nakonfigurovat jeho rozměry

Čára je dalším běžným kreslicím objektem. Použijeme logiku podobnou **přidání obdélníkového tvaru** i pro čáru, což ukazuje, že stejné principy velikosti platí.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Klíčový bod:* I když čára nemá výšku, stále používáte `setWidth` k definování její délky. Umístění (`setLeft`, `setTop`) se řídí stejným souřadnicovým systémem jako ostatní tvary.

## Krok 5: Uložit dokument se seskupenými tvary

Nakonec uložte změny tím, že dokument uložíte. Vytvoří se soubor `.docx`, který můžete otevřít v Microsoft Word a ověřit výsledek.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Očekávaný výstup:** Otevření `GroupShapeDemo.docx` zobrazí prázdnou stránku obsahující seskupený obdélník a čáru. Výběrem libovolného tvaru se vybere celá skupina, což vám umožní je přesouvat společně.

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| *Mohu do skupiny přidat více než dva tvary?* | Ano. Pro každý další tvar zavolejte `group.appendChild(yourShape)`. |
| *Co když potřebuji jinou jednotku (např. centimetry) pro velikost?* | Aspose.Words používá body (1 bod = 1/72 palce). Převod provádějte pomocí `Points = centimeters * 28.3465`. |
| *Zachová skupina své rozvržení při otevření dokumentu na jiném počítači?* | Rozhodně. Všechna data o velikosti a pozici jsou uložena v souboru `.docx`, takže rozvržení je přenosné. |
| *Jak mohu později rozdělit tvary ze skupiny?* | Získejte objekt `GroupShape`, poté iterujte přes `group.getChildNodes(NodeType.SHAPE, true)` a každý podřízený prvek přesuňte mimo skupinu. |
| *Co když potřebuji otočit celou skupinu?* | Použijte `group.setRotationAngle(double angleInDegrees)` před uložením. |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do svého IDE. Obsahuje všechny potřebné importy a komentáře.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Spusťte program, otevřete `GroupShapeDemo.docx` v Microsoft Word a uvidíte seskupené tvary přesně tak, jak je popsáno.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **seskupit tvary ve Wordu**, **přidat obdélníkový tvar** a **nastavit velikost tvaru** pomocí Aspose.Words pro Java. Umístěním tvarů do `GroupShape` získáte plnou kontrolu nad společným umístěním, měřítkem a rotací – ideální pro diagramy, vývojové diagramy nebo vlastní grafiku vloženou do automatizovaných reportů.

**Další kroky:**  
- Prozkoumejte **jak seskupit tvary** s komplexnějšími objekty, jako jsou obrázky nebo textová pole.  
- Experimentujte s `setRotationAngle` pro otočení celé skupiny.  
- Kombinujte tuto techniku s hromadnou korespondencí (mail‑merge) pro generování personalizovaných dokumentů, které obsahují značkovou grafiku.

Neváhejte upravit kód pro své vlastní projekty a sdílet své výsledky v komentářích!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar ve Wordu s Java – Kompletní průvodce](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}