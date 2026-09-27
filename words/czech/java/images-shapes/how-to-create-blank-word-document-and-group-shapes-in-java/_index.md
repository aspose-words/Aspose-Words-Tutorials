---
category: general
date: 2026-09-27
description: Vytvořte prázdný dokument Word v Javě a seskupte tvary pomocí Aspose.Words.
  Naučte se nastavit velikost tvaru, nastavit barvu výplně tvaru a přidat podřízený
  prvek do skupiny.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: cs
lastmod: 2026-09-27
og_description: Vytvořte prázdný dokument Word v Javě pomocí Aspose.Words. Tento tutoriál
  ukazuje, jak seskupit tvary ve Wordu, nastavit velikost tvaru, nastavit barvu výplně
  tvaru a přidat podřízený prvek do skupiny.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Vytvořte prázdný dokument Word a seskupte tvary v Javě – průvodce krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak vytvořit prázdný dokument Word a seskupit tvary v Javě
url: /cs/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a seskupit tvary v Javě

Pokud potřebujete **programově vytvořit prázdný dokument Word**, tento průvodce vám ukáže přesně, jak na to s Aspose.Words pro Java. Také se naučíte **seskupit tvary ve Wordu**, nastavit velikost každého tvaru, aplikovat barvu výplně a **přidat podřízený prvek do skupiny**, aby se objekty chovaly jako jeden celek.

Práce se soubory Word z kódu vám ušetří ruční formátování a umožní automaticky generovat zprávy, smlouvy nebo marketingové brožury. Na konci tohoto tutoriálu budete mít spustitelný Java program, který vytvoří soubor `.docx` obsahující modrý obdélník a obrázek, oba seskupené dohromady.

## Požadavky

Než začnete, ujistěte se, že máte:

- Java 17 (nebo jakýkoli novější JDK) nainstalovanou.
- Maven nebo Gradle pro správu závislostí.
- Licenci Aspose.Words pro Java (bezplatná zkušební verze stačí pro testování).
- Ukázkový soubor obrázku (např. `sample.jpg`) umístěný ve složce, na kterou můžete odkazovat z kódu.

> **Tip:** Ukládejte své obrázky do adresáře `resources` a načítejte je pomocí `ClassLoader.getResourceAsStream`, abyste se vyhnuli pevně zakódovaným absolutním cestám.

## Krok 1: Vytvořit prázdný dokument Word a přidat GroupShape

Prvním krokem je vytvořit novou instanci objektu `Document`, který představuje prázdný soubor Word, a poté vložit `GroupShape`. Skupina bude sloužit jako kontejner pro všechny tvary, které později přidáte.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Proč je to důležité:* `GroupShape` vám umožní přesouvat, otáčet nebo formátovat více tvarů najednou, což je nezbytné pro složité rozvržení jako diagramy nebo vodoznaky.

## Krok 2: Vložit obdélník a **nastavit velikost tvaru**

Dále vytvořte obdélník, definujte jeho rozměry a přidejte jej do skupiny. Tím demonstrujeme operaci **nastavit velikost tvaru**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Vysvětlení:* `setWidth` a `setHeight` řídí přesnou velikost tvaru v bodech (1 bod = 1/72 palce). Upravit tyto hodnoty podle požadavků vašeho rozvržení.

## Krok 3: **Nastavit barvu výplně tvaru** pro obdélník

Pozadí obdélníku je nastaveno na modrou pomocí `setFillColor`. Můžete použít libovolnou konstantu `java.awt.Color` nebo vytvořit vlastní RGB barvu.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Proč je to užitečné:* Barvy výplně pomáhají vizuálně odlišit objekty, zejména když později exportujete dokument do PDF nebo jej tisknete.

## Krok 4: Vložit obrázek a **přidat podřízený prvek do skupiny**

Nyní přidejte obrázek do stejného `GroupShape`. Obrázek se vloží pomocí `DocumentBuilder.insertImage` a poté se připojí ke skupině, aby se pohyboval společně s obdélníkem.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Okrajový případ:* Pokud je cesta k obrázku špatná, Aspose.Words vyhodí `FileNotFoundException`. Použijte relativní cestu nebo načtěte obrázek ze zdrojů, abyste tomuto problému předešli.

## Krok 5: **Uložit dokument se seskupenými tvary**

Nakonec zapíšete dokument na disk. Výsledný soubor bude obsahovat obdélník a obrázek seskupené dohromady.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Očekávaný výstup

- V určeném adresáři se objeví soubor s názvem `GroupShape.docx`.
- Po otevření souboru v Microsoft Wordu se zobrazí prázdná stránka s modrým obdélníkem a vybraným obrázkem, oba vybrané jako jeden objekt (můžete je přesouvat nebo měnit jejich velikost společně).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*Výše uvedený snímek obrazovky demonstruje finální seskupené tvary uvnitř nově vytvořeného dokumentu Word.*

## Běžné varianty a doplňující tipy

| Situace | Jak to řešit |
|-----------|-----------------|
| **Více obrázků** | Vložte každý obrázek pomocí `builder.insertImage` a pro každý zavolejte `group.appendChild(picture)`. |
| **Různé typy tvarů** | Použijte `ShapeType.OVAL`, `ShapeType.LINE` atd. při vytváření objektu `Shape`. |
| **Změna pozice skupiny** | Po přidání všech podřízených nastavte `group.setLeft(x)` a `group.setTop(y)`, čímž přesunete celou skupinu. |
| **Export do PDF** | Po seskupení zavolejte `doc.save("output.pdf")`; PDF zachová seskupení. |
| **Vynucení licence** | Pokud používáte zkušební verzi, objeví se vodoznak. Nainstalujte platnou licenci, aby se odstranil. |

## Závěr

Nyní už umíte **vytvořit prázdný dokument Word**, vložit **GroupShape**, **nastavit velikost tvaru**, **nastavit barvu výplně tvaru** a **přidat podřízený prvek do skupiny** pomocí Aspose.Words pro Java. Tento vzor vám umožní vytvářet složité, programově generované rozvržení, které lze později upravovat ve Wordu nebo exportovat do jiných formátů.

Dále prozkoumejte, jak **seskupit tvary ve Wordu** s textovými poli, přidávat hypertextové odkazy k tvarům nebo automatizovat generování více‑stránkových zpráv. Principy jsou stejné – stačí vytvořit další tvary, nastavit jejich vlastnosti a připojit je ke stejné skupině.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}