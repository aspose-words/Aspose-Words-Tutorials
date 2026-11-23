---
category: general
date: 2026-11-22
description: Naučte se, jak přidat tvar do Wordu pomocí Aspose.Words pro Javu – vložte
  obdélník a skryjte jej programově.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: cs
lastmod: 2026-11-22
og_description: Přidejte tvar do Wordu pomocí Aspose.Words pro Javu. Tento tutoriál
  ukazuje, jak vložit obdélník, skrýt tvar a uložit dokument.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Přidejte tvar do Wordu pomocí Aspose.Words – průvodce pro Javu
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Jak přidat tvar do dokumentů Word pomocí Aspose.Words pro Javu
url: /cs/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat tvar do dokumentů Word pomocí Aspose.Words pro Java

Pokud potřebujete **přidat tvar do Word** dokumentů programově, Aspose.Words pro Java to usnadňuje. V tomto průvodci se naučíte **jak vložit tvar**, ovládat jeho viditelnost a **jak tvar skrýt**, aby výsledný soubor vypadal přesně tak, jak očekáváte.

Provedete kompletní, spustitelný příklad, který načte existující `.docx`, vloží obdélník, skryje jej a uloží výsledek. Nepotřebujete žádné externí skripty ani ruční kroky a tutoriál zahrnuje běžné varianty, jako je vytvoření nového dokumentu od nuly nebo skrytí tvaru pouze při tisku.

## Požadavky

* Java 17 (nebo novější) nainstalováno – starší verze fungují, ale nejnovější LTS poskytuje lepší výkon.  
* Maven 3.8+ pro správu závislostí.  
* Platná licence Aspose.Words pro Java (bezplatná zkušební verze stačí pro učení).  
* IDE nebo textový editor dle vašeho výběru (např. IntelliJ IDEA, VS Code).

## Krok 1: Přidat Aspose.Words do vašeho Maven projektu

Přidejte následující závislost do souboru `pom.xml`. Tím získáte nejnovější stabilní verzi (k listopadu 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Tip:** Použijte klauzuli `<scope>provided</scope>`, pokud plánujete distribuovat JAR s vlastní licenční logikou.

## Přidání tvaru do Word – inicializace dokumentu

Prvním funkčním krokem je získat objekt `Document`. Můžete buď načíst existující soubor, nebo vytvořit nový.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Proč je to důležité*: Třída `Document` je vstupním bodem pro všechny manipulace s Wordem. Načtení existujícího souboru zachová styly, záhlaví a zápatí, zatímco nový dokument vám poskytne čistý list.

## Jak vložit tvar do dokumentu Word

Dále vytvořte `DocumentBuilder` pro úpravu obsahu dokumentu. Builder poskytuje metody pro vkládání textu, tabulek a **tvarů**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Volání `insertShape` vrací objekt `Shape`, který můžete dále konfigurovat (barvu, okraj, text atd.). Rozměry jsou vyjádřeny v bodech (1 pt = 1/72 palce).

*Proč můžete použít obdélník*: Obdélníky jsou nejčastějším kontejnerem pro anotace, vodoznaky nebo zástupné objekty. Můžete nahradit `ShapeType.RECTANGLE` za `ShapeType.ELLIPSE`, `ShapeType.LINE` atd., aby vyhovovaly různým vizuálním požadavkům.

## Jak skrýt tvar ve Wordu

Někdy potřebujete, aby tvar existoval pro výpočty rozvržení, ale neobjevil se ve finálním vykreslení. Aspose.Words poskytuje metodu `setHidden(true)`, která to umožňuje.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Příznak skrytí funguje jako formátovací volba **Hidden** v Microsoft Word: tvar je vynechán z vizuálního rozvržení, ale stále je součástí objektového modelu dokumentu. To je užitečné pro:

* Ukládání metadat nebo značek, které vaše aplikace později načte.
* Vytváření zástupných objektů, které jsou odstraněny těsně před publikací.
* Řízení viditelnosti pro různé výstupní formáty (např. skrýt v HTML, ale zachovat v PDF).

> **Poznámka:** Skryté tvary jsou ve výchozím nastavení stále exportovány do PDF. Pokud je chcete také vynechat z PDF, nastavte `rectangle.getWrapType( ) = WrapType.NONE` a odpovídajícím způsobem upravte vlastnost `Hidden`.

## Krok 4: Uložit upravený dokument

Nakonec uložte změny do nového souboru.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Když otevřete `output.docx` v Microsoft Word, obdélník nebude viditelný, ale zůstane součástí stromu dokumentu. Jeho přítomnost můžete programově ověřit opětovným načtením souboru a kontrolou `Shape.isHidden()`.

### Očekávaný výstup

* Soubor `output.docx` se otevře bez viditelných tvarů.  
* Pokud dokument prozkoumáte pomocí Aspose.Words (např. `doc.getChildNodes(NodeType.SHAPE, true).size()`), počet tvarů bude **1**, což potvrzuje, že tvar existuje, ale je skrytý.

## Pokročilé varianty a okrajové případy

### 1. Vytvoření tvaru v novém dokumentu

Pokud začínáte od nuly, nahraďte řádek načítání tímto:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Přesné umístění tvaru

Ve výchozím nastavení `insertShape` umístí tvar na aktuální pozici kurzoru. Pro absolutní umístění:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Řízení viditelnosti podle výstupního formátu

Pokud potřebujete, aby byl tvar viditelný v uživatelském rozhraní Word, ale skrytý při exportu do PDF, použijte `Shape.setWrapType(WrapType.NONE)` spolu s `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Přidání textu uvnitř tvaru

Obdélník může obsahovat textový rámec:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Poté můžete textové pole skrýt stejným voláním `setHidden(true)`.

## Časté problémy a jak se jim vyhnout

| Příznak | Příčina | Řešení |
|---------|---------|--------|
| Tvar se zobrazuje i po `setHidden(true)` | Dokument byl uložen před nastavením příznaku skrytí. | Ujistěte se, že voláte `setHidden(true)` **před** `doc.save()`. |
| Velikost tvaru vypadá deformovaně | Záměna bodů a pixelů na obrazovkách s vysokým DPI. | Používejte body (72 pt = 1 palec) pro konzistentní velikost napříč platformami. |
| Skrytý tvar se stále tiskne | Některé tiskárny ignorují příznak skrytí. | Nastavte `Shape.setWrapType(WrapType.NONE)` a také vymažte `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Závěr

Nyní víte, jak **přidat tvar do Word** dokumentů pomocí Aspose.Words pro Java, **jak vložit tvar** a **jak tvar skrýt**, aby byl neviditelný pro koncové uživatele, ale stále součástí struktury dokumentu. Kompletní příklad výše načte soubor, vloží obdélník, skryje jej a uloží výsledek, přičemž pokrývá jak typické scénáře, tak několik okrajových případů.

Odtud můžete zkoumat související témata, jako je **jak vložit tvar** s vlastními barvami výplně, **jak skrýt tvar ve Wordu** pro podmíněný tisk, nebo automatizace hromadného zpracování dokumentů pomocí Aspose.Words. Experimentujte s různými hodnotami `ShapeType`, možnostmi umístění a příznaky viditelnosti, aby vyhovovaly vašemu konkrétnímu workflow.

Šťastné programování a užijte si flexibilitu, kterou programová manipulace s Wordem přináší vašim Java aplikacím!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit dokument Word programově, přidat a skrýt tvar v Javě pomocí Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Jak skrýt tvar v dokumentu Word pomocí Javy](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Vytvořit prázdný .docx dokument Word a přidat skrytý obdélníkový tvar s Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}