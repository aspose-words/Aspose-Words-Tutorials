---
category: general
date: 2026-11-25
description: Jak seskupit tvary ve Wordu pomocí Javy a jak nastavit rozměry tvarů
  v souboru DOCX pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: cs
lastmod: 2026-11-25
og_description: Jak seskupit tvary ve Wordu pomocí Aspose.Words Java API a rychle
  nastavit velikost tvaru ve Wordu. Postupujte podle kompletního krok‑za‑krokem řešení.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Jak seskupit tvary ve Wordu a nastavit jejich rozměry – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Jak seskupit tvary ve Wordu a nastavit jejich rozměry programově
url: /cs/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu a programově nastavit jejich rozměry

Pokud potřebujete **jak seskupit tvary ve Wordu** a ovládat jejich přesnou velikost, tento návod vám ukáže kompletní, spustitelné řešení. Pomocí Aspose.Words pro Java můžete vytvořit obdélník, elipsu, přidat je do `GroupShape` a poté **jak nastavit rozměry tvaru**, například šířku a výšku, v jediném souboru DOCX.

Dozvíte se, jak:

* Vytvořit nový Word dokument od nuly.  
* Vložit `GroupShape` (nové API ve verzi 24.9).  
* Přidat do skupiny obdélník a elipsu.  
* **Nastavit velikost tvaru ve Wordu** přesně pomocí `setWidth` a `setHeight`.  
* Uložit dokument na disk.

Není potřeba žádný externí nástroj – stačí Java 17+, Maven a knihovna Aspose.Words pro Java.

## Požadavky

* Java Development Kit 17 nebo novější.  
* Maven (nebo Gradle) pro správu závislostí.  
* Aspose.Words pro Java 24.9 nebo novější (API `GroupShape` bylo zavedeno ve verzi 24.9).  
* Základní znalost syntaxe Javy a objektově orientovaných konceptů.

Pokud jste ještě nepřidali Aspose.Words do svého projektu, zahrňte následující Maven závislost:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Krok 1: Vytvoření nového dokumentu a DocumentBuilderu

Třída `Document` představuje celý Word soubor, zatímco `DocumentBuilder` poskytuje pohodlný způsob, jak přidávat obsah.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč tento krok?*  
Vytvoření nového `Document` vám poskytne čisté plátno. `DocumentBuilder` je vysoce úrovňový pomocník, který vám umožní vkládat odstavce, tabulky a v tomto případě tvary.

## Krok 2: Vložení GroupShape (nové API ve verzi 24.9)

`GroupShape` funguje jako kontejner; jakýkoli tvar, který přidáte, se stane součástí stejné vizuální skupiny.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Proč použít `GroupShape`?*  
Seskupování tvarů zjednodušuje jejich přesouvání, otáčení nebo aplikaci formátování na více objektů najednou. API bylo přidáno ve verzi 24.9, takže starší verze tuto řádku nezkopírují.

## Krok 3: Vytvoření obdélníku, nastavení jeho velikosti a přidání do skupiny

Zde ukazujeme **jak nastavit rozměry tvaru** pro obdélník.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Proč nastavit šířku a výšku explicitně?*  
Word ukládá velikost tvaru v bodech. Voláním `setWidth` a `setHeight` řídíte přesnou vizuální stopu, což je nezbytné, když potřebujete přesné rozvržení nebo při exportu do PDF.

## Krok 4: Vytvoření elipsy, nastavení její velikosti a přidání do stejné skupiny

Stejná technika **nastavení velikosti tvaru ve Wordu** funguje pro jakýkoli typ tvaru.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Proč přidat elipsu do stejného `GroupShape`?*  
Oba tvary se budou pohybovat společně jako jednotka. To je užitečné při tvorbě ikon, log nebo složitých diagramů, které musí zůstat zarovnané.

## Krok 5: Uložení dokumentu se seskupenými tvary

Nakonec uložíme soubor DOCX na disk.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Po spuštění tohoto programu vznikne soubor pojmenovaný **GroupShape.docx**, který obsahuje obdélník a elipsu seskupené dohromady. Když soubor otevřete v Microsoft Word, uvidíte, že oba tvary se chovají jako jeden objekt – můžete je táhnout, měnit jejich velikost nebo otáčet společně.

### Očekávaný výstup

* Word dokument (`GroupShape.docx`) s jednou stránkou.  
* `GroupShape` obsahující obdélník 100 × 50 pt a elipsu 80 × 80 pt.  
* Výběr libovolného tvaru vybere celou skupinu.

## Často kladené otázky a okrajové případy

### Jak změnit pozici seskupených tvarů?

Po vytvoření `GroupShape` můžete nastavit jeho vlastnosti `left` a `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Tyto souřadnice jsou také měřeny v bodech.

### Co když potřebuji přidat více než dva tvary?

`GroupShape` funguje jako jakýkoli jiný kontejnerový uzel. Pro každý další tvar zavolejte `groupShape.appendChild(yourShape)`. API neomezuje počet potomků.

### Můžu aplikovat styl (barvu výplně, tloušťku čáry) na jednotlivé tvary?

Ano. Každý objekt `Shape` expose formátovací vlastnosti:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Funguje kód se staršími verzemi Aspose.Words?

Metoda `insertGroupShape` byla zavedena ve verzi 24.9. Pokud používáte starší verzi, budete muset vytvořit `GroupShape` ručně přes strom uzlů, což je složitější. Doporučujeme aktualizaci.

## Profesionální tipy

* **Používejte body pro konzistenci** – interní jednotkou Wordu je bod (1/72 palce). Převod z pixelů nebo centimetrů může vést k neočekávaným velikostem.  
* **Seskupujte před umístěním** – pozici `GroupShape` nastavte až po přidání všech jeho potomků; jinak budete muset přepočítat offsety.  
* **Znovu použijte DocumentBuilder** – můžete vkládat více skupin do stejného dokumentu přesunutím kurzoru builderu (`builder.moveTo`) před každé volání `insertGroupShape`.

## Závěr

Nyní máte kompletní, end‑to‑end příklad **jak seskupit tvary ve Wordu** a **jak nastavit rozměry tvaru** pomocí Aspose.Words pro Java. Tutoriál pokrýval vytvoření dokumentu, vložení `GroupShape`, přidání obdélníku a elipsy, nastavení jejich přesné velikosti a uložení výsledku.  

Od sem můžete dále zkoumat:

* Přidání textových polí nebo obrázků do stejné skupiny.  
* Animaci seskupených tvarů pomocí funkcí SmartArt ve Wordu (přes API).  
* Export seskupených tvarů do PDF nebo SVG pro webové použití.

Neváhejte experimentovat s různými typy tvarů, velikostmi a pozicemi – seskupování vám poskytuje silnou kontrolu nad složitými rozvrženími ve Word dokumentech.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}