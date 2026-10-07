---
category: general
date: 2026-09-27
description: Vytvořte nový dokument Word a vložte obrázkový tvar, který zůstane skrytý.
  Naučte se, jak skrýt tvar a přidat skrytý obrázek pomocí Aspose.Words pro Javu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: cs
lastmod: 2026-09-27
og_description: Vytvořte nový dokument Word a vložte obrázkový tvar, který zůstane
  skrytý. Naučte se, jak skrýt tvar a přidat skrytý obrázek pomocí Aspose.Words pro
  Javu.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: Vytvořte nový dokument Word s ukrytým obrázkem – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: Vytvořte nový dokument Word s ukrytým obrázkem – krok za krokem
url: /cs/java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření nového dokumentu Word s skrytým obrázkem – krok za krokem

Pokud potřebujete **create new Word document**, který obsahuje logo, ale nechcete, aby logo ovlivnilo rozvržení stránky, tento průvodce vám přesně ukáže, jak to provést. Naučíte se, jak **insert image shape**, pochopíte **how to hide shape** a nakonec **add hidden picture** do souboru bez jakéhokoli vizuálního dopadu.

Tutoriál pokrývá vše od nastavení projektu až po poslední ověřovací krok. Na konci budete mít plně funkční Java program, který vytváří soubor Word, vkládá tvar obrázku, skryje jej a uloží výsledek. Kromě knihovny Aspose.Words pro Java není potřeba žádný další nástroj.

## Požadavky

* Java 17 (nebo novější) nainstalována.
* Projekt Maven nebo Gradle, do kterého můžete přidat závislosti.
* Aspose.Words pro Java 23.9 (nebo nejnovější verze) – viz oficiální Maven repozitář pro správné souřadnice.
* Soubor obrázku (např. `logo.png`) umístěný ve složce, na kterou můžete odkazovat z kódu.

> **Tip:** Uchovávejte obrázek ve stejném adresáři jako váš zdrojový soubor během vývoje; zjednodušuje to práci s cestami.

## Krok 1: Nastavení projektu a import Aspose.Words

Přidejte závislost Aspose.Words do vašeho `pom.xml` (Maven) nebo `build.gradle` (Gradle). Níže je ukázka Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nyní vytvořte třídu Java s názvem `HiddenPictureDemo`. První řádky importují požadované třídy a **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* `Document` představuje celý soubor `.docx`, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání obsahu, jako jsou odstavce, tabulky a tvary.

## Krok 2: Vložení tvaru obrázku do dokumentu Word

Další operace ukazuje **how to insert image** jako tvar. Použití `DocumentBuilder.insertImage` vrací objekt `Shape`, který můžete dále upravovat.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*Proč použít tvar:* Obrázek vložený jako tvar vám poskytuje přístup k vlastnostem rozvržení, jako jsou viditelnost, obtékání a umístění, což je nezbytné pro pozdější skrytí obrázku.

## Krok 3: Skrytí tvaru, aby se neobjevil v rozvržení

Nyní odpovídáme na **how to hide shape**. Nastavení vlastnosti `Hidden` na `true` odstraní tvar z vizuálního rozvržení, přičemž jej ponechá v struktuře dokumentu.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*Vysvětlení:* `setHidden(true)` říká Wordu, aby tvar považoval za neviditelný. Dodatečné `setWrapType(WrapType.NONE)` zajišťuje, že skrytý obrázek nevyhrazuje žádný prostor, čímž zachovává původní tok dokumentu.

## Krok 4: Uložení dokumentu a ověření skrytého obrázku

Nakonec soubor uložíte na disk. Skrytý obrázek zůstává součástí dokumentu, ale není zobrazen při otevření souboru v Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

Když otevřete `HiddenShape.docx` ve Wordu, uvidíte normální, čistou stránku bez viditelného loga, přesto je obrázek uložen uvnitř souboru. Jeho přítomnost můžete ověřit otevřením `.docx` jako zip archivu a prohlídkou složky `word/media`.

### Očekávaný výstup

Running the program prints:

```
Document created successfully with a hidden picture.
```

Otevření vygenerovaného `HiddenShape.docx` ukazuje prázdnou stránku (nebo jakýkoli jiný obsah, který jste přidali jinde) a žádný viditelný obrázek. Pokud rozbalíte `.docx`, najdete `logo.png` ve složce `word/media`, což potvrzuje, že obrázek byl **add hidden picture** správně.

## Jak vložit obrázek v jiných kontextech

Pokud potřebujete **insert image shape** do konkrétního odstavce místo aktuální pozice kurzoru, můžete nejprve přesunout builder:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

Tento vzor funguje pro záhlaví, zápatí nebo tabulky – stačí přesunout builder na cílový uzel před voláním `insertImage`.

## Běžné varianty a okrajové případy

| Scénář | Co upravit |
|----------|----------------|
| **Více skrytých obrázků** | Opakujte kroky 2‑3 pro každý obrázek. Každý `Shape` může být skryt nezávisle. |
| **Různé formáty obrázků** | Aspose.Words podporuje PNG, JPEG, BMP, GIF a TIFF. Použijte vhodnou příponu souboru v cestě. |
| **Velké dokumenty** | Vytvořte dokument jednou a poté znovu použijte stejný `DocumentBuilder` k vložení skrytých obrázků na různá místa. |
| **Podmíněná viditelnost** | Použijte `shape.setVisible(false)` spolu s `shape.setHidden(true)`, pokud později potřebujete přepínat viditelnost pomocí makra Word. |
| **Kompatibilita se staršími verzemi Wordu** | Uložte jako `doc.save("file.doc", SaveFormat.DOC)`, pokud musíte podporovat Word 2003‑2007. Skryté tvary se chovají stejným způsobem. |

## Praktické tipy z praxe

* **Path handling:** Použijte `Paths.get("...").toAbsolutePath().toString()`, abyste se vyhnuli neočekávaným relativním cestám při spuštění z IDE oproti zabalenému JAR.
* **Performance:** Vkládání mnoha velkých obrázků může zvýšit spotřebu paměti. Zvažte změnu velikosti obrázku (`setWidth`/`setHeight`) před jeho skrytím.
* **Testing:** Automatizujte rychlou kontrolu načtením uloženého dokumentu a voláním `doc.getChildNodes(NodeType.SHAPE, true).getCount()`, abyste ověřili, že očekávaný počet tvarů existuje, i když jsou skryté.

## Závěr

Nyní víte, jak **create new Word document**, **insert image shape** a **how to hide shape**, aby obrázek zůstal neviditelný – efektivně **add hidden picture** do libovolného souboru Word pomocí Aspose.Words pro Java. Tato technika je užitečná pro vkládání vodoznaků, značkových aktiv nebo metadatových obrázků, které by neměly narušovat rozvržení dokumentu.

### Další kroky

* Prozkoumejte další vlastnosti tvaru, jako jsou otočení, okraje a hypertextové odkazy.
* Kombinujte skryté obrázky s vlastními vlastnostmi dokumentu pro uložení dalších metadat.
* Podívejte se na **how to insert image** do záhlaví nebo zápatí pro konzistentní značkování napříč stránkami.

Neváhejte experimentovat s různými velikostmi obrázků, pozicemi a nastavením viditelnosti. Pokud narazíte na problémy, dokumentace Aspose.Words pro Java poskytuje podrobné reference API a ukázkové projekty. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními krok za krokem, aby vám pomohly zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}