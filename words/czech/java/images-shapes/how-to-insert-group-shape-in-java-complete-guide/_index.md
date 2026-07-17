---
category: general
date: 2026-07-16
description: jak vložit skupinový tvar v Javě pomocí Aspose.Words – přidat obdélníkový
  tvar, nastavit rozměry tvaru a vytvořit barevný obdélník a kruh.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: cs
lastmod: 2026-07-16
og_description: 'jak vložit skupinový tvar v Javě: praktický průvodce přidáním obdélníkového
  tvaru, nastavením rozměrů tvaru a vytvořením barevného obdélníku a kruhu pomocí
  Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Vložení skupinového tvaru v Javě – kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Jak vložit skupinový tvar v Javě – kompletní průvodce
url: /cs/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak vložit skupinový tvar v Javě – Kompletní průvodce

Už jste se někdy ptali, **jak vložit skupinový tvar** do dokumentu Word pomocí Javy? Nejste jediní. Ať už vytváříte generátor reportů nebo dynamického tvůrce letáků, seskupování tvarů udržuje rozvržení přehledné a váš kód snadno spravovatelný.

V tomto tutoriálu projdeme přesné kroky k **přidání obdélníkového tvaru**, **nastavení rozměrů tvaru**, a **vytvoření barevného obdélníku** a **vytvoření barevného kruhu** pomocí knihovny Aspose.Words. Na konci budete mít spustitelný program, který vytvoří soubor .docx s modrým obdélníkem a červeným kruhem úhledně zabaleným ve skupině.

## Požadavky

- Java 17 (nebo jakýkoli recentní JDK) nainstalovaný a nakonfigurovaný.
- Maven nebo Gradle pro správu závislostí.
- Aspose.Words for Java 23.9 nebo novější – můžete jej získat z Maven Central.
- Základní pochopení syntaxe Javy – nic složitého není potřeba.

Pokud vám něco z toho chybí, stáhněte JDK z webu Oracle a přidejte závislost Aspose.Words do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nyní, když je základ připraven, pojďme se pustit do práce.

## jak vložit skupinový tvar – Přehled

Základní myšlenka je jednoduchá: vytvořit `Document`, otevřít `DocumentBuilder`, vložit **skupinový tvar**, a poté vložit jednotlivé tvary (obdélník a kruh) do této skupiny. Skupina funguje jako kontejner, takže její pozdější přesunutí posune vše uvnitř – ideální pro složité rozvržení.

Níže je kompletní, připravený k spuštění kód. Klidně jej zkopírujte a vložte do nové Java třídy s názvem `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Tip:** Hodnoty `setLeft` a `setTop` jsou relativní k počátku skupiny, ne k stránce. To usnadňuje pozdější přemístění celé skupiny.

### Co se právě stalo?

1. **Document & Builder** – Vytvoříme prázdný soubor Word a `DocumentBuilder`, který nám umožňuje vkládat obsah.
2. **Group Shape** – `builder.insertGroupShape()` vytvoří kontejner. Představte si ho jako složku pro kreslicí objekty.
3. **Blue Rectangle** – Instancujeme `Shape` typu `RECTANGLE`, nastavíme velikost, pozici a vyplníme ho modrou – to je krok **create colored rectangle**.
4. **Red Circle** – Stejný postup, ale používáme `ELLIPSE` pro dokonalý kruh a vyplníme ho červeně – to je část **create colored circle**.
5. **Saving** – Nakonec vše uložíme do `GroupShapeDemo.docx`.

Spusťte program (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) a otevřete vzniklý soubor. Měli byste vidět modrý obdélník vlevo a červený kruh vpravo, oba uzamčené uvnitř jedné skupinové krabice.

## Přidání obdélníkového tvaru

Pokud potřebujete pouze obdélník bez seskupování, můžete vynechat volání `insertGroupShape()` a přidat obdélník přímo do těla dokumentu. Nicméně seskupování vám poskytuje flexibilitu přesouvat, otáčet nebo mazat více tvarů najednou.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Všimněte si, že zde používáme logiku **add rectangle shape**. Obdélník se objeví na stránce jako samostatný objekt. Ve většině reálných scénářů však budete chtít skupinu, protože zachovává relativní umístění.

## Nastavení rozměrů tvaru

Když vidíte metody jako `setWidth` a `setHeight`, pamatujte, že přijímají **body** (1/72 palce). Pokud dáváte přednost milimetrům, nejprve je převeďte:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Tento úryvek demonstruje **set shape dimensions** s převodem jednotek – užitečné, když vaše návrhové specifikace pocházejí z UI mockupu používajícího metrické jednotky.

## Vytvoření barevného obdélníku

Barvení tvaru je tak jednoduché jako zavolat `getFill().setForeColor()`. Můžete předat libovolnou `java.awt.Color`. Chcete gradient? Použijte `setForeColor` pro počáteční barvu a `setBackColor` pro koncovou.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

To je rychlý způsob, jak **create colored rectangle** s gradientním výplní místo jednobarevné.

## Vytvoření barevného kruhu

Kruhy jsou jen elipsy se stejnou šířkou a výškou. Stejná logika barvení platí:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Pokud potřebujete průhlednou výplň, nastavte alfa kanál:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Nyní ovládáte techniku **create colored circle**.

## Ukládání dokumentu

Aspose.Words vám umožňuje výstup do mnoha formátů: DOCX, PDF, HTML, PNG, jakýkoli. Pro tuto ukázku zůstáváme u DOCX, protože perfektně zachovává vektorové tvary.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Změna `SaveFormat` stačí k vygenerování PDF verze stejného seskupeného díla.

## Časté úskalí a jak se jim vyhnout

- **Zapomněli jste přidat tvar do skupiny?** Tvar se objeví na stránce, ale nebude se pohybovat se skupinou. Vždy zavolejte `group.appendChild(yourShape)`.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Javu](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vytvořit obdélníkový tvar ve Wordu s Aspose.Words – Průvodce krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}