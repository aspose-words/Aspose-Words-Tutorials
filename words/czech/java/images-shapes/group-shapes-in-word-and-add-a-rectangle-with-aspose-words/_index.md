---
category: general
date: 2026-09-11
description: Seskupte tvary ve Wordu a přidejte obdélníkový tvar pomocí Aspose.Words
  pro Javu. Naučte se, jak nastavit velikost tvaru, seskupit objekty a uložit dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: cs
lastmod: 2026-09-11
og_description: Seskupte tvary ve Wordu a přidejte obdélníkový tvar pomocí Aspose.Words
  pro Java. Tento tutoriál ukazuje, jak nastavit velikost tvaru, seskupit tvary a
  exportovat dokument.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Seskupování tvarů ve Wordu – přidat obdélník pomocí Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Seskupte tvary ve Wordu a přidejte obdélník pomocí Aspose.Words
url: /cs/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skupinování tvarů ve Wordu a přidání obdélníku pomocí Aspose.Words

Pokud potřebujete **group shapes in Word** a zároveň programově přidat obdélník, tento průvodce vám poskytne kompletní, připravené k okamžitému spuštění řešení. Ukážeme vám přesně, jak vložit skupinový tvar, přidat obdélníkový tvar, nastavit velikost tvaru a nakonec dokument uložit, abyste mohli výsledek okamžitě zobrazit.

Práce s dokumenty Word často zahrnuje uspořádání více objektů — obrázků, grafů nebo jednoduchých geometrických tvarů — do jedné logické jednotky. Skupinování těchto objektů usnadňuje jejich společný přesun, otáčení nebo stylování. V tomto tutoriálu se také podíváme na **how to add rectangle** tvary a **set shape size** pro dokonalou kontrolu rozvržení.

## Co se naučíte

* Jak vytvořit nový dokument Word pomocí Aspose.Words for Java.  
* **How to group shapes** tak, aby se chovaly jako jeden objekt.  
* **Add rectangle shape** do skupiny a vložit obrázek do stejné skupiny.  
* **Set shape size** pro obdélník i obrázek.  
* Uložit dokument a otevřít jej v Microsoft Wordu pro ověření výsledku.

### Požadavky

* Nainstalovaný Java 17 nebo novější.  
* Maven nebo Gradle pro správu závislostí.  
* Platná licence Aspose.Words for Java (nebo bezplatný evaluační klíč).  
* Soubor obrázku (`sample.png`) umístěný v známém adresáři (nahraďte `YOUR_DIRECTORY` skutečnou cestou).

---

## Jak skupinovat tvary ve Wordu pomocí Aspose.Words

Prvním krokem je vytvořit `Document` a `DocumentBuilder`. Builder vám poskytuje pohodlné API pro vkládání tvarů, textu a dalších prvků.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč je to důležité:** `DocumentBuilder` pracuje přímo s podkladovým objektem `Document`, což vám umožňuje vkládat tvary bez ručního zacházení s nízkoúrovňovými kolekcemi uzlů.

### Přidání skupinového tvaru

Skupinový tvar je kontejner, který může obsahovat další tvary. Představte si jej jako složku pro kreslicí objekty.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Metoda `insertGroupShape()` vytvoří uzel `GroupShape` a vrátí jej, takže můžete později přidávat podřízené tvary.

---

## Přidání obdélníkového tvaru do skupiny

Nyní **add rectangle shape** přidáme do dříve vytvořené skupiny. Obdélník bude sloužit jako pozadí nebo ohraničení pro obrázek.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tip:** Nastavení `FillColor` a `StrokeColor` způsobí, že bude obdélník viditelný v konečném dokumentu. Pokud tyto vlastnosti vynecháte, tvar se může zobrazit jako průhledný.

### Jak přidat obdélník

Výše uvedený kód ukazuje **how to add rectangle** vytvořením instance `Shape` s `ShapeType.RECTANGLE` a následným připojením k `GroupShape`. Tento vzor funguje pro jakýkoli jiný typ tvaru (např. `ELLIPSE`, `POLYLINE`).

---

## Nastavení velikosti tvaru pro obdélník a obrázek

Správné nastavení velikosti zajišťuje, že se obdélník a obrázek správně zarovnají. Zde také **set shape size** pro obrázek, který vložíme dále.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Obě, obdélník i obrázek, nyní sdílejí stejné rozměry (100 × 50 bodů). Protože patří do stejné skupiny, přesun nebo otočení skupiny ovlivní oba tvary najednou.

> **Proč sladit velikosti?** Zarovnání rozměrů zaručuje, že obrázek bude čistě umístěn uvnitř obdélníku, čímž vznikne čistý efekt „obrázek v rámečku“.

---

## Uložení dokumentu a zobrazení výsledku

Nakonec zapíšeme dokument na disk. Otevření souboru v Microsoft Wordu zobrazí seskupené tvary jako jeden vybraný objekt.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Když otevřete `output.docx`, uvidíte obdélník s obrázkem uvnitř. Kliknutím na tvar vyberete jak obdélník, tak obrázek, protože jsou **grouped**.

![příklad seskupování tvarů ve Wordu](https://example.com/images/group-shapes-word.png "příklad seskupování tvarů ve Wordu")

*Text alternativy obrázku:* *příklad seskupování tvarů ve Wordu* – dokument Word zobrazující seskupený obdélník a obrázek.

---

## Časté otázky a řešení okrajových případů

| Question | Answer |
|----------|--------|
| **Co když potřebuji jinou velikost obrázku?** | Upravte `picture.setWidth()` a `picture.setHeight()` po vložení. Obdélník může zachovat původní velikost, nebo jej můžete také změnit, aby odpovídal. |
| **Mohu přidat další tvary do stejné skupiny?** | Ano. Zavolejte `group.appendChild(newShape)` pro jakékoli další objekty `Shape`. |
| **Jak otočím celou skupinu?** | Použijte `group.setRotationAngle(double angleInRadians)`. Rotace se aplikuje na každý podřízený tvar. |
| **Co když soubor obrázku chybí?** | `insertImage` vyvolá `FileNotFoundException`. Zabalte volání do bloku try‑catch a poskytněte náhradní placeholder tvar. |
| **Je možné později rozdělit skupinu?** | Zavolejte `group.removeAllChildren()` pro odpojení podřízených, poté je vložte zpět do dokumentu jednotlivě. |

---

## Závěr

Nyní máte kompletní, spustitelný příklad, který ukazuje **how to group shapes in Word**, **add rectangle shape**, **set shape size** a **save** dokument pomocí Aspose.Words for Java. Skupinováním obdélníku a obrázku je můžete přesouvat, měnit jejich velikost nebo otáčet jako jednu jednotku — právě to, co vyžaduje mnoho scénářů automatizace dokumentů.

Odtud můžete zkoumat:

* Přidání textových polí do stejné skupiny (text ve stylu `how to add rectangle`).
* Použití různých výplňových vzorů nebo gradientů (`set shape size` kombinováno se stylováním).
* Použití stejné techniky pro seskupení grafů, tabulek nebo SmartArt (`how to group shapes` napříč dalšími typy objektů).

Neváhejte experimentovat s dalšími typy tvarů, barvami a možnostmi rozvržení. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření Word dokumentu v Javě – Přidání obdélníkového tvaru s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak převést Word do PDF pomocí Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}