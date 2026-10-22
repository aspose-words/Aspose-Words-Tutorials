---
category: general
date: 2026-08-14
description: Skrýt obrázek ve Wordu pomocí Javy. Naučte se, jak skrýt obrázek, skrýt
  grafiku, nastavit skrytou vlastnost a skrýt tvar ve Wordu s Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: cs
lastmod: 2026-08-14
og_description: Skryjte obrázek ve Wordu pomocí Javy a Aspose.Words. Tento tutoriál
  ukazuje, jak nastavit vlastnost skrytí na obrázku, skrýt tvar ve Wordu a uložit
  dokument během několika sekund.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Skrytí obrázku ve Wordu – krok za krokem průvodce v Javě s Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Skrytí obrázku ve Wordu – krok za krokem Java průvodce s Aspose
url: /cs/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skrýt obrázek ve Wordu – krok za krokem průvodce v Javě s Aspose

Pokud potřebujete **skrýt obrázek ve Wordu** programově, tento průvodce ukazuje kompletní řešení. Uvidíte, jak najít obrázek, nastavit příznak skrytí a zapsat aktualizovaný soubor zpět na disk.

Skrytí grafiky je běžný požadavek při generování reportů, tvorbě šablon nebo přípravě dokumentů k revizi souladu. Níže uvedený příklad demonstruje **jak skrýt obrázek** pomocí Aspose.Words pro Javu, ale stejné koncepty platí pro jakoukoli knihovnu pro zpracování Wordu, která poskytuje metodu `setHidden` pro tvar.

## Co dosáhnete

* Načtěte soubor `.docx` pomocí Aspose.Words.
* Najděte první tvar obrázku v dokumentu.
* **Nastavte vlastnost hidden** na tomto tvaru, aby se nezobrazoval při otevření souboru v Microsoft Wordu.
* Uložte upravený dokument bez změny ostatního obsahu.

Jedinou podmínkou je vývojové prostředí Java (JDK 8 nebo novější) a platná licence Aspose.Words pro Javu. Kromě základní knihovny nejsou vyžadovány žádné další Maven pluginy.

## Skrýt obrázek ve Wordu pomocí Aspose.Words

Prvním krokem je vytvořit objekt `Document`, který představuje zdrojový soubor. Aspose.Words načte celý balík Wordu do paměti, což usnadňuje procházení uzlů, jako jsou tvary, odstavce a tabulky.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Vytvoření instance `Document` ověří formát souboru a vytvoří interní strom uzlů. Tento strom je základem pro všechny následné operace, včetně **jak skrýt obrázek** objektů.

## Jak skrýt obrázek pomocí vlastnosti set hidden

Obrázek v souboru Word je uložen jako uzel `Shape` s `ShapeType.IMAGE`. Knihovna poskytuje metodu `setHidden(boolean)`, která řídí viditelnost tvaru. Následující stream filtruje kolekci uzlů, aby našel první tvar obrázku.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

Volání `getChildNodes` prochází celý strom dokumentu (`true` povoluje hluboké vyhledávání). Lambda výraz kontroluje `ShapeType` každého uzlu. Tento vzor je doporučený způsob, **jak skrýt obrázek**, když potřebujete přesnou kontrolu výběru uzlů.

## Jak skrýt obrázek ve Word dokumentu

Jakmile je cílový tvar identifikován, aplikujte příznak skrytí. Nastavení této vlastnosti neodstraní obrázek; pouze instruuje Word, aby tvar během vykreslování považoval za skrytý.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

Volání `setHidden(true)` se přímo mapuje na podkladový XML atribut `w:hidden="true"`. Word tento atribut respektuje jak v desktopové, tak online verzi editoru, což zajišťuje, že obrázek zůstane neviditelný pro všechny čtenáře.

## Skrýt tvar ve Wordu – další úvahy

Zatímco příklad skrývá pouze první obrázek, můžete logiku rozšířit tak, aby zpracovávala více tvarů:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Výkon** – Procházení stromu uzlů je O(n); u velmi velkých dokumentů zvažte omezení vyhledávání na konkrétní sekce.
* **Kompatibilita** – Příznak skrytí funguje s Word 2007+ (`.docx`) a Word 97‑2003 (`.doc`) soubory.
* **Přepínání viditelnosti** – Pro opětovné zobrazení skrytého obrázku zavolejte `shape.setHidden(false)`.

Tyto tipy vám pomohou zvládnout scénáře **skrýt tvar ve Wordu** nad rámec základního použití.

## Uložit upravený dokument

Po aktualizaci příznaku skrytí zapište dokument zpět do úložiště. Aspose.Words automaticky zachovává všechny ostatní části dokumentu, jako jsou styly, záhlaví a zápatí.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

Metoda `save` podporuje širokou škálu formátů (PDF, HTML, ODT). V tomto tutoriálu ponecháváme výstup jako Word soubor, aby byl efekt skrytého obrázku zobrazen přímo.

## Kompletní spustitelný příklad

Spojením všech kroků získáte samostatný program, který můžete okamžitě zkompilovat a spustit.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Očekávaný výsledek:** Otevřete `output.docx` v Microsoft Wordu. Původní obrázek se nezobrazí, ale zbytek dokumentu (text, tabulky, další grafika) zůstane nezměněn. Pokud prozkoumáte XML (`document.xml`), uvidíte atribut `w:hidden="true"` na elementu `<w:pict>`, který odpovídá skrytému obrázku.

## Závěr

Nyní víte, jak **skrýt obrázek ve Wordu** pomocí Javy, Aspose.Words a vlastnosti `setHidden`. Tutoriál pokryl vyhledání tvaru obrázku, aplikaci příznaku skrytí a uložení změn. S těmito základy můžete také **skrýt tvar ve Wordu**, zpracovávat více obrázků nebo přepínat viditelnost na základě obchodních pravidel.

**Další kroky**

* Prozkoumejte **jak skrýt obrázek** podmíněně na základě metadat (např. role uživatele).
* Kombinujte tuto techniku s hromadnou korespondencí (mail‑merge) pro generování personalizovaných dokumentů s ohledem na soukromí.
* Projděte si referenci Aspose.Words API pro pokročilou manipulaci s tvary, jako je změna rotace nebo aplikace vodoznaků.

Neváhejte experimentovat s variantami, jako je skrytí grafů nebo objektů SmartArt, a sdílet své poznatky s vývojářskou komunitou. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Show Hide Bookmarked Content In Word Document](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}