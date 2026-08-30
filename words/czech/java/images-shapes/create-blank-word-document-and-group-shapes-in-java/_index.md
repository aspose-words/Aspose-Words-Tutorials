---
category: general
date: 2026-08-23
description: Vytvořte prázdný dokument Word pomocí Aspose.Words pro Javu, naučte se
  seskupovat tvary, barvit obdélníkový tvar a během několika minut dokument uložit
  jako docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: cs
lastmod: 2026-08-23
og_description: Vytvořte prázdný dokument Word pomocí Aspose.Words pro Javu, poté
  se podívejte, jak seskupit tvary, obarvit obdélníkový tvar a efektivně uložit dokument
  jako docx.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Vytvořte prázdný dokument Word a seskupte tvary v Javě – krok za krokem
  průvodce
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Vytvořte prázdný dokument Word a seskupte tvary v Javě
url: /cs/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření prázdného dokumentu Word a seskupení tvarů v Javě

Pokud potřebujete **vytvořit prázdný dokument Word** programově, Aspose.Words pro Javu to usnadňuje. Tento tutoriál vám přesně ukáže, jak **vytvořit prázdný dokument Word**, vložit **skupinu tvarů ve Wordu**, použít **barevný obdélníkový tvar** a nakonec **uložit dokument jako docx**. Na konci budete mít znovupoužitelný úryvek kódu, který můžete vložit do jakéhokoli Java projektu.

Naučíte se:

* Požadovaná závislost Maven/Gradle pro Aspose.Words.
* Jak vytvořit prázdný dokument a `DocumentBuilder`.
* Přesné kroky, jak **seskupit tvary** uvnitř `GroupShape`.
* Jak nastavit barvy výplně u obdélníkových tvarů.
* Nejlepší postup pro **uložení dokumentu jako docx** a kde najít výstupní soubor.

Předchozí zkušenost s Aspose.Words se nepředpokládá, ale měli byste být obeznámeni se základním vývojem v Javě a mít nainstalovaný JDK 8 nebo novější.

---

## Předpoklady

| Požadavek | Verze / Detail |
|-------------|-------------------|
| Java Development Kit | 8 nebo vyšší |
| Nástroj pro sestavení | Maven 3+ nebo Gradle 6+ |
| Aspose.Words for Java | 23.12 nebo novější (nejnovější verze v době psaní) |
| IDE (volitelné) | IntelliJ IDEA, Eclipse, VS Code, nebo jakýkoli Java‑kompatibilní editor |

---

## Krok 1: Přidat Aspose.Words do vašeho projektu

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Tip:** Pokud používáte firemní proxy, nakonfigurujte Maven/Gradle tak, aby stahoval balíček z repozitáře Aspose, jak je popsáno v oficiální dokumentaci.

---

## Krok 2: **Vytvořit prázdný dokument Word** pomocí builderu

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` konstruktor vytvoří v paměti prázdný kontejner `.docx`. `DocumentBuilder` vám poskytuje plynulé API pro přidávání obsahu, včetně tvarů.

---

## Krok 3: Vložit kontejner **skupiny tvarů ve Wordu**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` funguje jako mini‑plátno. Všechny tvary do něj přidané se pohybují společně, což je přesně **jak seskupit tvary** pro konzistenci rozvržení.

---

## Krok 4: Přidat první **barevný obdélníkový tvar** (červený)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

Konstanta `ShapeType.RECTANGLE` vytvoří jednoduchý obdélník. Voláním `getFill().setForeColor(...)` řídíte **barevný obdélníkový tvar**. Můžete nahradit `java.awt.Color.RED` libovolnou konstantou `java.awt.Color` nebo vlastním RGB hodnotou.

---

## Krok 5: Přidat druhý **barevný obdélníkový tvar** (zelený) a umístit jej

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Nastavení `setLeft` (nebo `setTop`) posouvá tvar relativně k levému hornímu rohu kontejneru **skupiny tvarů ve Wordu**. Toto ukazuje **jak seskupit tvary** s přesným umístěním.

---

## Krok 6: **Uložit dokument jako docx** a ověřit výsledek

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Metoda `save` automaticky zapíše soubor `.docx`, protože přípona souboru je `.docx`. Pokud potřebujete jiný formát (např. PDF), předáte odpovídající výčtový typ `SaveFormat`.

> **Tip:** Ujistěte se, že cílový adresář (`output/` v tomto příkladu) existuje, nebo jej vytvořte programově pomocí `new File("output").mkdirs();`.

## Kompletní zdrojový kód pro rychlé zkopírování

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Očekávaný výstup:** Otevření `GroupShapeDemo.docx` v Microsoft Word zobrazí jednu stránku obsahující dva barevné obdélníky (červený vlevo, zelený vpravo), které se pohybují společně, když vyberete skupinu.

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| *Mohu přidat více než dva tvary do stejné skupiny?* | Ano. Zavolejte `groupShape.appendChild(yourShape)` pro každý další tvar. Skupina se automaticky přizpůsobí tak, aby zahrnovala nejvzdálenější části, nebo můžete ručně upravit její šířku/výšku. |
| *Co když potřebuji jiný typ tvaru (např. elipsu)?* | Nahraďte `ShapeType.RECTANGLE` za `ShapeType.ELLIPSE`. Stejná logika výplně barvou se použije. |
| *Potřebuji uvolnit objekt `Document`?* | Aspose.Words spravuje nativní zdroje interně. Když JVM skončí, zdroje jsou uvolněny. Pro dlouho běžící aplikace zavolejte `doc.dispose();`, pokud používáte **Aspose.Words for Java (Native)** verzi. |
| *Jak změním Z‑pořadí, aby se jeden obdélník zobrazil nahoře?* | Použijte `groupShape.insertAfter(shape, referenceShape);` nebo `groupShape.insertBefore(shape, referenceShape);` pro změnu pořadí dětí ve skupině. |
| *Mohu seskupovat tvary napříč různými sekcemi?* | Ne. `GroupShape` musí být umístěn v jednom odstavci nebo kontejneru tvaru. Pro seskupení napříč sekcemi vytvořte samostatné skupiny v každé sekci. |

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word** pomocí Aspose.Words pro Javu, **seskupit tvary ve Wordu**, aplikovat styl **barevného obdélníkového tvaru** a **uložit dokument jako docx**. Tento vzor lze rozšířit na složitější rozvržení – stačí přidat další tvary, upravit offsety a případně nastavit text, obrázky nebo hypertextové odkazy uvnitř skupiny.

**Další kroky**, které můžete prozkoumat:

* Použít **skupinu tvarů ve Wordu** k vytvoření vývojových diagramů nebo UI mock‑upů.
* Experimentovat s **uložením dokumentu jako docx** v kombinaci s konverzí do PDF (`doc.save("out.pdf")`).
* Použít gradienty nebo vzory na **barevný obdélníkový tvar** pro bohatší vizuální design.
* Kombinovat seskupené tvary s tabulkami nebo grafy pro pokročilé reportovací dokumenty.

Neváhejte upravit rozměry, barvy nebo typy tvarů tak, aby odpovídaly brandingu vašeho projektu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak uložit dokument jako pdf pomocí Aspose.Words pro Javu](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Používání tvarů dokumentu v Aspose.Words pro Javu](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}