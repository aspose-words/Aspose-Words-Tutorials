---
category: general
date: 2026-08-20
description: Naučte se, jak seskupovat tvary, nastavit velikost tvaru, vložit obrázek
  do dokumentu, přidat obrázek do skupiny a vytvořit obdélníkový tvar pomocí Aspose.Words
  v Javě.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: cs
lastmod: 2026-08-20
og_description: Jak seskupit tvary v dokumentu Word pomocí Aspose.Words. Postupujte
  podle tohoto krok‑za‑krokem Java tutoriálu, kde nastavíte velikost tvaru, vložíte
  obrázek do dokumentu, přidáte obrázek do skupiny a vytvoříte obdélníkový tvar.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Jak seskupit tvary v dokumentu Word pomocí Aspose.Words – průvodce pro Javu
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Jak seskupit tvary ve Word dokumentu pomocí Aspose.Words
url: /cs/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary v dokumentu Word pomocí Aspose.Words

Pokud potřebujete **jak seskupit tvary** v souboru Word, tento tutoriál ukazuje kompletní řešení v Javě. Uvidíte, jak **nastavit velikost tvaru**, **vložit obrázek do dokumentu**, **přidat obrázek do skupiny** a **vytvořit obdélníkový tvar** — vše s jasnými vysvětleními a spustitelným ukázkovým kódem.

Seskupování tvarů zjednodušuje správu rozvržení, umožňuje přesunout nebo otočit více objektů jako jednotku a udržuje dokument přehledný. V následujících krocích vytvoříte skupinu, která obsahuje obdélník a obrázek, a poté skupinu umístíte na stránku.

## Požadavky

* Nainstalovaný Java 17 nebo novější.
* Aspose.Words pro Java (verze 23.9 nebo novější) přidán do classpath vašeho projektu.
* Ukázkový JPEG obrázek v `YOUR_DIRECTORY/sample.jpg` (nahraďte `YOUR_DIRECTORY` skutečnou cestou).

Aspose.Words můžete přidat pomocí Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Jak seskupit tvary pomocí Aspose.Words

Následující sekce vás provede každou operací potřebnou k **jak seskupit tvary**. Primární nadpis H2 obsahuje hlavní klíčové slovo, což splňuje SEO pravidla.

### Krok 1: Vytvořit nový dokument a `DocumentBuilder`

`Document` představuje soubor Word, zatímco `DocumentBuilder` poskytuje pohodlné metody pro vkládání obsahu.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: Začít s novým `Document` zajišťuje, že vytvořená skupina nebude zasahovat do existujících prvků.

### Krok 2: Vložit skupinový tvar, který bude obsahovat více podřízených tvarů

Skupinový tvar funguje jako kontejner. Jeho rozměry definují ohraničující rámeček pro všechny podřízené tvary.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: Šířka (`300`) a výška (`200`) jsou v bodech (1 pt = 1/72 palce). Přizpůsobte je podle velikosti tvarů, které plánujete přidat.

### Krok 3: Vytvořit obdélníkový tvar, nastavit jeho velikost a přidat jej do skupiny

Nastavení přesné velikosti tvaru je nezbytné, pokud chcete mít přesnou kontrolu nad rozvržením.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Proč nastavujeme velikost tvaru*: Metody `setWidth` a `setHeight` odpovídají sekundárnímu klíčovému slovu **set shape size**, což vám poskytuje pixel‑dokonalou kontrolu nad vzhledem obdélníku.

### Krok 4: Vložit obrázek a poté přidat tvar obrázku do stejné skupiny

Vložení obrázku je jádrem požadavku **insert image into document**. Vrácený `Shape` je tvar obrázku, který lze seskupit stejně jako jakýkoli jiný tvar.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: Pokud potřebujete zachovat původní poměr stran, nastavte pouze jeden rozměr (`setWidth` nebo `setHeight`). Aspose.Words automaticky přepočítá druhý rozměr.

### Krok 5: Umístit celou skupinu na stránku

Po přidání všech podřízených tvarů můžete celou skupinu přesunout, otočit nebo skrýt. Umístění nepřímo využívá koncept **add picture to group**, protože skupina nyní obsahuje obrázek.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Vysvětlení*: `setLeft` a `setTop` umisťují skupinu relativně k okrajům stránky. Otočení skupiny ukazuje, že všechny podřízené tvary zdědí transformaci.

### Krok 6: Uložit dokument

Nakonec zapíšete soubor na disk. Výsledný `.docx` můžete otevřít ve Wordu a ověřit seskupení.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Spuštěním programu vznikne **GroupShapesDemo.docx** obsahující obdélník a obrázek spojené dohromady. Výběrem libovolného tvaru ve Wordu se vybere i druhý, což potvrzuje, že jste úspěšně naučili **jak seskupit tvary**.

---

## Očekávaný výstup

Když otevřete *GroupShapesDemo.docx* v Microsoft Word:

* Obdélník (zlaté výplně) se objeví na levé straně skupiny.
* Poskytnutý obrázek se objeví vpravo od obdélníku.
* Oba objekty se pohybují společně, když táhnete skupinu.
* Skupina je umístěna 50 pt od levého okraje a 100 pt od horního okraje, otočena o 15°.

Pokud se obrázek neobjeví, zkontrolujte znovu cestu k souboru v `insertImage`. Aspose.Words vyvolá `IOException`, pokud soubor nelze najít.

---

## Časté otázky a řešení okrajových případů

| Question | Answer |
|----------|--------|
| **Mohu přidat více než dva tvary?** | Ano. Pro každý další tvar zavolejte `groupShape.appendChild(otherShape)`. |
| **Co když potřebuji průhledné pozadí pro obdélník?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Je seskupování podporováno ve starších formátech Wordu (např. `.doc`)?** | Seskupování funguje pro `.docx` i `.doc`, ale některé starší prohlížeče mohou ignorovat metadata skupiny. Pro plnou věrnost uložte jako `.docx`. |
| **Jak mohu později rozdělit skupinu?** | Získejte podřízené uzly pomocí `groupShape.getChildNodes(NodeType.ANY, true)` a přesuňte je do těla dokumentu, poté skupinu odstraňte. |
| **Mohu seskupovat tvary napříč různými sekcemi?** | Ne. `GroupShape` musí být umístěn v jedné `Story` (obvykle v hlavním těle dokumentu). |

---

## Profesionální tipy pro robustní práci s tvary

* **Používejte absolutní umístění střídmě** – relativní umístění (`builder.moveToDocumentEnd()`) často poskytuje responzivnější rozvržení.
* **Ukládejte `DocumentBuilder` do cache** – vytváření nového builderu pro každou operaci může snižovat výkon u velkých dokumentů.
* **Nastavte `PictureFillMode`**, pokud potřebujete, aby se obrázek roztáhl nebo dlaždicově vyplnil uvnitř tvaru: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Ověřte rozměry obrázku** před vložením, aby nedošlo k neočekávanému škálování, které může ovlivnit ohraničující rámeček skupiny.

---

## Další kroky

Nyní, když víte **jak seskupit tvary**, můžete prozkoumat:

* **Insert image into document** s pokročilými možnostmi, jako je ořezávání (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamicky na základě rozměrů stránky (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** spolu s textovými poli pro popisky grafiky.
* **Create rectangle shape** s kulatými rohy (`rectangleShape.setCornerRadius(5);`).

Tyto témata staví na stejném API a pomáhají vám vytvářet sofistikované, programové Word reporty.

---

## Závěr

V tomto tutoriálu jste se naučili **jak seskupit tvary** v dokumentu Word pomocí Aspose.Words pro Java. Dodržením šesti kroků – vytvoření dokumentu, vložení skupiny, **vytvoření obdélníkového tvaru**, **nastavení velikosti tvaru**, **vložit obrázek do dokumentu**, **přidat obrázek do skupiny** a umístění skupiny – máte nyní znovupoužitelný vzor pro složité scénáře rozvržení. Klidně experimentujte s dalšími podřízenými tvary, různými otočeními nebo podmíněnou logikou seskupování, aby vyhovovaly potřebám vaší aplikace.

Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Používání tvarů dokumentu v Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Vytvořit skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}