---
category: general
date: 2026-09-21
description: Vytvořte Word dokument programově pomocí Javy. Naučte se, jak seskupovat
  tvary ve Wordu, vložit obdélníkový tvar, nastavit velikost tvaru a přidat tvary
  do Word dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: cs
lastmod: 2026-09-21
og_description: 'Vytvořte Word dokument programově v Javě: tento návod ukazuje, jak
  seskupovat tvary ve Wordu, vkládat obdélníkové tvary, nastavit velikost tvaru a
  přidávat tvary do Word dokumentu.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Vytvořte Word dokument programově, seskupte tvary v Javě
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Vytvořit Word dokument programově, seskupit tvary v Javě
url: /cs/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu programově, seskupení tvarů v Javě

Pokud potřebujete **vytvořit Word dokument programově**, tento průvodce vás provede kompletním řešením. Uvidíte, jak **seskupit tvary ve Wordu**, vložit obdélník, nastavit jeho velikost a přidat další tvary — vše pomocí Javy a knihovny Aspose.Words for Java.

Tutoriál pokrývá každý krok od nastavení projektu až po uložení finálního souboru .docx. Na konci budete schopni vygenerovat Word dokument, který obsahuje obdélník a obrázek zabalený do jedné skupiny, což usnadňuje jejich společný přesun nebo změnu velikosti. Předchozí zkušenost s Aspose.Words API není vyžadována, ale měli byste mít základní prostředí pro vývoj v Javě.

## Požadavky

* Java Development Kit (JDK) 8 nebo novější  
* Maven nebo Gradle pro správu závislostí  
* Aspose.Words for Java 23.9 (nebo nejnovější verze) — knihovna je zdarma pro evaluaci  
* Soubor s obrázkem (např. `sample.jpg`) umístěný v známém adresáři  

Mít tyto položky připravené zajišťuje, že kód poběží bez dalších konfigurací.

## Krok 1: Nastavení projektu a import Aspose.Words

Vytvořte Maven projekt (nebo přidejte závislost do existujícího `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Pokud dáváte přednost Gradlu, přidejte následující do `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Po vyřešení závislosti importujte požadované třídy ve vašem Java souboru:

```java
import com.aspose.words.*;
import java.io.File;
```

## Krok 2: Vytvoření Word dokumentu programově

První operací v jakémkoli automatizačním scénáři je vytvořit objekt `Document` a `DocumentBuilder`. Builder zjednodušuje vkládání textu, obrázků a tvarů.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto okamžiku existuje dokument pouze v paměti. Nyní můžete začít přidávat tvary.

## Krok 3: Vložení obdélníkového tvaru – jak vložit obdélníkový tvar

Obdélník je základní `Shape` s typem `ShapeType.RECTANGLE`. Jeho rozměry ovládáte pomocí `setWidth`, `setHeight` a pozici pomocí `setTop` a `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Proč je to důležité:** Explicitní nastavení velikosti a pozice (`set shape size word`) zaručuje, že se obdélník objeví přesně tam, kde očekáváte, bez ohledu na výchozí rozvržení dokumentu.

## Krok 4: Vložení obrázku – přidání tvarů do Word dokumentu

`DocumentBuilder` může vložit obrázek přímo ze souborové cesty. Po vložení můžete obrázek přemístit stejně jako jakýkoli jiný tvar.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Obdélník i obrázek jsou nyní nezávislé tvary uvnitř dokumentu.

## Krok 5: Seskupení tvarů – jak seskupit tvary ve Wordu

Seskupení tvarů je užitečné, když je chcete přesouvat nebo měnit jejich velikost jako jeden celek. Aspose.Words poskytuje kontejner `GroupShape` pro tento účel.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Když je skupina uložena, Word zachází s oběma podřízenými objekty jako s jedním logickým objektem. Později můžete skupinu vybrat a táhnout, a oba, obdélník i obrázek, se budou pohybovat společně.

## Krok 6: Uložení dokumentu

Nakonec zapište dokument na disk. Cesta musí být zapisovatelná procesem Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Spuštěním metody `main` vznikne soubor pojmenovaný **GroupShapeExample.docx**. Otevřete jej v Microsoft Word a uvidíte obdélník a obrázek uzamčené dohromady ve skupině. Výběrem skupiny můžete oba objekty přesunout najednou, což potvrzuje úspěšné seskupení.

## Očekávaný výstup

* Word soubor (`GroupShapeExample.docx`) umístěný v adresáři, který jste zadali.  
* V souboru se v levém horním rohu objeví obdélník (světle šedé výplně) a obrázek leží přímo pod ním.  
* Oba objekty jsou součástí jedné skupiny, takže tažení jednoho přesune i druhý.

## Běžné varianty a okrajové případy

| Situace | Doporučení |
|-----------|----------------|
| **Různé formáty obrázků** | Aspose.Words podporuje PNG, BMP, GIF a TIFF. Použijte odpovídající příponu souboru v `insertImage`. |
| **Negativní rozměry** | API vyhodí `ArgumentException`. Vždy ověřte šířku a výšku před voláním `setWidth` / `setHeight`. |
| **Velké dokumenty** | Seskupení mnoha tvarů může zvýšit velikost souboru. Zvažte sloučení tvarů do jednoho obrázku, pokud záleží na výkonu. |
| **Kompatibilita verzí Wordu** | GroupShape funguje s Word 2007 (`.docx`) a novějšími. U starších `.doc` souborů bude skupina zploštěna. |
| **Dynamické umístění** | Použijte výpočty založené na velikosti stránky (`doc.getFirstSection().getPageSetup().getPageWidth()`), pokud potřebujete adaptivní umístění. |

**Pro tip:** Po vytvoření skupiny můžete změnit

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Vytvoření Word dokumentu v Javě – Přidání obdélníkového tvaru s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vytvoření obdélníkového tvaru ve Wordu s Javou – Kompletní průvodce](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Vytvoření skupinového tvaru ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}