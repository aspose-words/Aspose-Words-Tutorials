---
category: general
date: 2026-07-26
description: Vložte obdélníkový tvar v Javě pomocí Aspose.Words. Naučte se, jak nastavit
  velikost tvaru, umístit tvar a jak seskupovat tvary v souboru DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: cs
lastmod: 2026-07-26
og_description: Vložte obdélníkový tvar v Javě pro tvorbu bohaté grafiky DOCX. Postupujte
  podle tohoto krok‑za‑krokem průvodce a snadno nastavte velikost tvaru, jeho umístění
  a seskupování tvarů.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Vložení obdélníkového tvaru v Javě – Ovládněte seskupování a umístění
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Vložení obdélníkového tvaru v Javě – seskupování a umístění tvarů
url: /cs/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení obdélníkového tvaru v Javě – Skupinování a umístění tvarů

Už jste někdy potřebovali **insert rectangle shape** do Word dokumentu při psaní Java kódu? Nejste jediní — vývojáři vytvářející reporty, faktury nebo vlastní šablony na to narazí pořád. Dobrou zprávou je, že s několika řádky Aspose.Words for Java můžete **insert rectangle shape**, **set shape size**, **position shape** a dokonce **how to group shapes**, aby se pohybovaly jako jedna jednotka.

V tomto průvodci projdeme celý proces od vytvoření prázdného dokumentu až po uložení `.docx`, který obsahuje dva obdélníky pěkně seskupené dohromady. Na konci budete vědět **how to add rectangle** objekty, ovládat jejich rozměry, umístit je přesně tam, kde chcete, a spojit je do znovupoužitelné skupiny. Žádné externí knihovny kromě Aspose.Words nejsou potřeba a kód funguje s Java 8 a novějšími.

## Požadavky

- Java 8 nebo novější nainstalována (používám JDK 17, ale vše, co podporuje Maven, funguje)
- Aspose.Words for Java 23.9 nebo novější — přidejte závislost do vašeho `pom.xml` nebo stáhněte JAR
- Základní pochopení syntaxe Java (pokud umíte napsat `main` metodu, jste v pořádku)
- IDE nebo textový editor podle vašeho výběru (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Pokud používáte Maven, závislost vypadá takto:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nyní, když máme připravený základ, pojďme se ponořit do kódu.

## Vložení obdélníkového tvaru a nastavení jeho velikosti

Prvním krokem bude vytvořit nový `Document` a `DocumentBuilder`. Builder je vaše „pero“, které kreslí tvary na stránku. Níže **insert rectangle shape** a okamžitě **set shape size** na 100 × 80 bodů.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Všimněte si, že volání `setWidth`/`setHeight` **set shape size** v bodech (1 pt ≈ 1/72 palce). Můžete také použít `setSize`, pokud dáváte přednost jedné metodě, ale explicitní volání jasně vyjadřují záměr.

## Umístění tvaru na stránce

Po vytvoření prvního obdélníku potřebujeme **position shape** druhý tak, aby nepřekrýval první. Umístění funguje stejným způsobem: nastavíte vlastnosti `Left` a `Top` relativně k počátku skupiny.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Pokud se ptáte, proč používáme `setLeft` místo `setX`, je to proto, že Aspose.Words používá klasický souřadnicový systém Windows GDI — `Left` je horizontální posun, `Top` je vertikální posun. Úpravou těchto hodnot můžete jemně doladit rozvržení bez manipulace s tabulkami nebo odstavci.

## Jak seskupit tvary

Můžete se zeptat: „Proč vůbec používat skupinu?“ Seskupování dává smysl, když chcete, aby se tvary pohybovaly společně, otáčely jako jednotka nebo sdílely společný styl. Ve výše uvedeném úryvku jsme již vytvořili `GroupShape` pomocí `builder.insertGroupShape`. Tento objekt je v podstatě kontejner — představte si ho jako složku, která obsahuje další tvary.

> **Proč je to důležité:** Pokud se později rozhodnete přidat popisek nebo otočit celý diagram, stačí upravit skupinu, ne každý obdélník zvlášť.

## Jak přidat obdélník do skupiny

Akce **how to add rectangle** do skupiny spočívá jednoduše v zavolání `group.appendChild(rectangle)`. Pod kapotou Aspose.Words aktualizuje interní kolekci skupiny a automaticky přepočítá ohraničující rámeček, aby skupina stále odpovídala deklarované šířce a výšce.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Můžete experimentovat s dalšími `ShapeType` — `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` atd. — a stejný vzor `appendChild` funguje.

## Uložení dokumentu

Nakonec dokument uložíme na disk. Cesta může být absolutní nebo relativní; jen se ujistěte, že složka existuje.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Když otevřete `GroupShape.docx` v Microsoft Word, uvidíte dva obdélníky vedle sebe, oba uzamčené uvnitř světle šedého rámečku. Výběrem šedého rámečku zvýrazníte oba obdélníky najednou — důkaz, že **how to group shapes** opravdu funguje.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Příklad vložení obdélníkového tvaru ukazující dva obdélníky seskupené v Java‑generovaném souboru DOCX"}

*Text alt obrázku (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Očekávaný výstup

- Soubor `GroupShape.docx` umístěný ve složce `output`.
- V dokumentu: skupina 400 × 200 pt obsahující dva obdélníky (100 × 80 pt a 120 × 60 pt) umístěné na (20, 30) a (150, 50) respektive.
- Skupina má tenký černý okraj a světle šedé výplň, což vizuálně zdůrazňuje seskupení.

Otevřete soubor a zkuste táhnout šedý rámeček — oba obdélníky by se měly pohybovat společně. Pokud ne, zkontrolujte, že jste pro každý tvar zavolali `group.appendChild`.

## Časté problémy a okrajové případy

| Problém | Proč se to stane | Oprava |
|---------|------------------|--------|
| **Obdélníky se objevují mimo stránku** | `Left`/`Top` hodnoty překračují rozměry skupiny | Zvětšete velikost skupiny (`insertGroupShape(width, height)`) nebo snižte offsety |
| **Skupina zmizí po uložení** | `Width`/`Height` skupiny jsou nastaveny na 0 | Zadejte nenulové rozměry při volání `insertGroupShape` |
| **Barvy tvaru vypadají špatně** | Výchozí výplň je průhledná; Word ji může vykreslit jako bílou | Explicitně nastavte `setFillColor` nebo použijte `ShapeStyle` |
| **Výjimka `ArgumentOutOfRangeException`** | Použití záporných souřadnic | Udržujte `Left` a `Top` nezáporné |

## Shrnutí a další kroky

Probrali jsme celý životní cyklus **insert rectangle shape** v Javě: vytvoření dokumentu, **set shape size**, **position shape**, **how to group shapes** a **how to add rectangle** do této skupiny. Kompletní, spustitelný příklad je v kódu výše a můžete jej vložit přímo do Maven projektu a vidět výsledek.

Co dál? Zvažte experimentování s:

- Přidání textu uvnitř každého obdélníku pomocí

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Vytvoření Word dokumentu v Javě – Přidání obdélníkového tvaru s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vytvoření skupinového tvaru ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvoření prázdného Word dokumentu se stínovaným obdélníkovým tvarem – Průvodce krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}