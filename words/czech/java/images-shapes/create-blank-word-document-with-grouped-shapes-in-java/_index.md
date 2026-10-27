---
category: general
date: 2026-08-07
description: Vytvořte prázdný dokument Word se seskupenými tvary v Javě pomocí Aspose.Words.
  Naučte se, jak seskupit tvar, nastavit velikost tvaru a přidat tvary do Wordu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: cs
lastmod: 2026-08-07
og_description: Vytvořte prázdný dokument Word se seskupenými tvary v Javě. Postupujte
  podle tohoto návodu, jak nastavit velikost tvaru, přidat tvary do Wordu a osvojit
  si, jak tvary seskupovat.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Vytvořte prázdný dokument Word se seskupenými tvary – Java tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Vytvořte prázdný dokument Word s seskupenými tvary v Javě
url: /cs/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word se seskupenými tvary v Javě

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje několik tvarů uspořádaných jako jedna jednotka, tento tutoriál vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který demonstruje **jak seskupit tvar** objekty, upravit jejich rozměry a **přidat tvary do Wordu** pomocí Aspose.Words for Java.

Průvodce vás provede každým krokem — od nastavení projektu až po uložení finálního souboru .docx — takže můžete kód přímo zkopírovat do své aplikace. Žádné externí odkazy nejsou vyžadovány a řešení funguje s Aspose.Words 23.9 nebo novějším.

## Požadavky

* Java 17 (nebo jakýkoli podporovaný JDK)
* Maven nebo Gradle pro správu závislostí
* Licence Aspose.Words pro Java (nebo dočasný evaluační klíč)
* Ukázkový soubor obrázku (např. `sample.jpg`) umístěný v známém adresáři

Pokud některá z těchto položek chybí, nejprve ji nainstalujte; zbytek tutoriálu předpokládá, že prostředí je připravené.

## Krok 1: Přidejte Aspose.Words do svého projektu

Přidejte závislost Aspose.Words do svého `pom.xml` (Maven) nebo `build.gradle` (Gradle). Tato knihovna poskytuje třídy `Document`, `DocumentBuilder`, `GroupShape` a `Shape`, které budou později použity.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Proč je to důležité:** Bez knihovny nejsou k dispozici žádná API pro zpracování Wordu a nemůžete **vytvořit prázdný dokument Word** programově.

## Krok 2: Vytvořte prázdný dokument Word

Prvním konkrétním krokem je vytvořit instanci objektu `Document`, který představuje **prázdný dokument Word** v paměti.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* vytvoří **prázdný dokument Word** s výchozími nastaveními (formát A4, výchozí okraje). Přidružený `DocumentBuilder` vám umožní vkládat obsah na aktuální pozici kurzoru.

## Krok 3: Vložte skupinový tvar (jak seskupit tvar)

*Skupinový tvar* funguje jako kontejner pro ostatní tvary. V tomto kroku se naučíte **jak seskupit tvar** objekty, aby se pohybovaly společně.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Metoda `insertGroupShape` umístí kontejner na pozici kurzoru builderu. Seskupování je nezbytné, když chcete zacházet s několika kresbami jako s jedním celkem — to je jádro funkčnosti **group shapes word**.

## Krok 4: Vytvořte obdélník a nastavte jeho velikost

Nyní přidejte obdélník do skupiny. Toto ukazuje **nastavení velikosti tvaru**, což je nutné pro přesné rozvržení.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Proč nastavit rozměry?* Výslovné volání `setWidth` a `setHeight` zaručuje, že se obdélník zobrazí přesně tak, jak je zamýšlen, bez ohledu na výchozí styly tvarů v dokumentu.

## Krok 5: Vložte obrázek a přidejte jej do skupiny

Přidání obrázku ukazuje další běžný případ použití pro **přidat tvary do word**. Obrázek se stane součástí stejné skupiny a bude se pohybovat společně s obdélníkem.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Pokud soubor obrázku chybí, Aspose.Words vyhodí výjimku. Praktický tip: ověřte cestu předem:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Krok 6: Uložte dokument obsahující seskupené tvary

Nakonec uložte **prázdný dokument Word** (nyní naplněný seskupeným tvarem) na disk.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Když otevřete `GroupShapeDemo.docx` v Microsoft Wordu, uvidíte jediný seskupený objekt, který obsahuje obdélník a obrázek. Výběrem jakékoli části skupiny se přesune celý kontejner, což potvrzuje, že tvary byly správně **seskupeny**.

### Očekávaný výstup

* Soubor pojmenovaný `GroupShapeDemo.docx` ve specifikovaném adresáři.
* Otevřením souboru se zobrazí kontejner o rozměrech 300 × 200 bodů s:
  * Obdélníkem 100 × 50 bodů umístěným na (20, 20).
  * Obrázkem umístěným na (150, 30) ve stejném kontejneru.

## Okrajové případy a varianty

| Situace | Jak to řešit |
|-----------|-----------------|
| **Různá velikost stránky** | Zavolejte `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` před vložením skupiny. |
| **Více skupin** | Opakujte kroky 3‑5 s novou instancí `GroupShape`; každá skupina může být umístěna nezávisle. |
| **Otáčení tvarů** | Použijte `shape.setRotationAngle(45.0);` pro otočení obdélníku nebo obrázku před jeho přidáním do skupiny. |
| **Tvarové objekty, které nejsou obrázky** | Vytvořte objekty `Shape` typu `ShapeType.ELLIPSE`, `ShapeType.LINE` atd. a přidejte je stejně jako obdélník. |
| **Velké obrázky** | Změřte velikost obrázku pomocí `picture.setWidth(80.0); picture.setHeight(60.0);` aby skupina zůstala v původních mezích. |

## Praktické tipy z praxe

* **Pro tip:** Nastavte `RelativeHorizontalPosition` a `RelativeVerticalPosition` skupiny na `RelativeHorizontalPosition.PAGE` a `RelativeVerticalPosition.PAGE`, pokud chcete, aby skupina zůstala ukotvena k stránce místo kurzoru.
* **Pozor na:** Přidání tvaru, který přesahuje rozměry skupiny; tvar bude ve Wordu oříznut. Podle toho upravte velikost skupiny pomocí `group.setWidth()` a `group.setHeight()`.
* **Poznámka o výkonu:** Pokud generujete mnoho dokumentů ve smyčce, znovu použijte jedinou instanci `DocumentBuilder` a zavolejte `doc.clone()`, abyste snížili režii vytváření objektů.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, který obsahuje seskupenou kolekci tvarů pomocí Aspose.Words pro Java. Tutoriál pokryl kompletní postup: nastavení knihovny, vytvoření dokumentu, vložení skupiny, **nastavení velikosti tvaru**, **přidat tvary do word**, a uložení výsledku.

Odtud můžete zkoumat pokročilejší funkce, jako je seskupování grafů, aplikace stylů na jednotlivé tvary nebo export dokumentu do PDF. Každé z těchto témat staví na stejných principech předvedených v tomto průvodci.

---


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vlastních projektech.

- [Vytvořit skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit dokument Word v Javě – Přidat obdélníkový tvar se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vložit tvary do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}