---
category: general
date: 2026-10-13
description: Naučte se, jak v aplikaci Word pomocí Javy vytvářet seskupené tvary.
  Tento průvodce vám ukáže, jak vložit skupinu tvarů, přidat čáru do skupiny a seskupit
  více tvarů v celém dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: cs
lastmod: 2026-10-13
og_description: Vytvořte seskupené tvary ve Wordu pomocí Javy. Sledujte tento kompletní
  návod, jak vložit skupinu tvarů, přidat čáru do skupiny a seskupit více tvarů ve
  Wordových dokumentech.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Vytvořte seskupené tvary ve Wordu pomocí Javy – krok za krokem průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak vytvořit seskupené tvary v dokumentu Word pomocí Javy
url: /cs/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit seskupené tvary v dokumentu Word pomocí Javy

Pokud potřebujete **vytvořit seskupené tvary** v souboru Microsoft Word z Javy, tento tutoriál vás provede celým procesem. Uvidíte, jak **vložit skupinový tvar**, umístit obdélník a čáru do stejného kontejneru a nakonec dokument uložit se seskupenou grafikou.

Seskupování tvarů usnadňuje přesouvání, změnu velikosti nebo stylování několika kreslicích objektů jako jedné jednotky – ideální pro diagramy, vývojové diagramy nebo vlastní dekorace stránky. Na konci tohoto průvodce budete umět **add line to group**, **group multiple shapes word** dokumenty a tuto techniku znovu použít pro libovolný počet tvarů.

## Požadavky

- Java 17 nebo novější nainstalovaná na vašem vývojovém počítači.  
- Licence Aspose.Words pro Java (nebo bezplatná zkušební verze).  
- Maven nebo Gradle projekt, do kterého můžete přidat závislost Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Žádné další knihovny nejsou potřeba.

## Krok 1: Vložení kontejneru skupinového tvaru

Prvním krokem je **insert group shape** do dokumentu. Tento kontejner bude obsahovat všechny následné tvary.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` vytvoří prázdný objekt `Shape` typu `GROUPSHAPE`. Představte si ho jako průhledné plátno, které může obsahovat další kreslicí objekty.

## Krok 2: Přidání obdélníku do skupiny

Obdélník často slouží jako vizuální pozadí pro skupinu tvarů.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Nastavením `Left` a `Top` na `0` umístíte obdélník do levého horního rohu skupiny. Tyto hodnoty můžete změnit, abyste posunuli tvar uvnitř skupiny.

## Krok 3: **Add line to group** – vytvoření čárového tvaru

Nyní **add line to group**. Čára se objeví pod obdélníkem.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Vlastnost `Top` posune čáru o 60 bodů pod obdélník, čímž vytvoří jednoduché vrstvené uspořádání. Můžete také nastavit `Left`, pokud potřebujete horizontální posun.

## Krok 4: Uložení dokumentu se seskupenými tvary

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Když otevřete `GroupShapeDemo.docx` v Microsoft Word, uvidíte jedinou skupinu, která obsahuje jak obdélník, tak čáru. Výběrem skupiny můžete přesunout oba tvary najednou, což dokazuje, že jste úspěšně **group multiple shapes word**.

## Kompletní, spustitelný příklad

Níže je kompletní program se všemi importy a ošetřením chyb. Zkopírujte jej do svého IDE, nahraďte `YOUR_DIRECTORY` existující cestou ke složce a spusťte.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Očekávaný výstup

- V cílové složce se objeví soubor `GroupShapeDemo.docx`.  
- Otevřením souboru ve Wordu se zobrazí jediný seskupený objekt obsahující obdélník nahoře a čáru pod ním.  
- Přetahování skupiny přesune oba tvary najednou, což potvrzuje, že jste **created grouped shapes** úspěšně.

## Tipy a časté úskalí

- **Pro tip:** Pokud potřebujete otáčet nebo stylovat jednotlivé tvary uvnitř skupiny, zavolejte příslušné settery (`setRotation`, `getFill().setForeColor` atd.) před jejich přidáním do skupiny. Skupina zachová tyto vizuální vlastnosti.
- **Pozor na:** Zapomenutí nastavit vlastnost `Top` pro čáru může způsobit překrytí s obdélníkem, což skupinu učiní nečistou.
- **Hraniční případ:** Když přidáte více než dva tvary, pamatujte, že souřadnice každého potomka jsou relativní k počátku skupiny (0,0). Plánujte rozvržení podle toho.
- **Poznámka o výkonu:** Seskupení velkého počtu tvarů (stovek) může mírně zvětšit velikost souboru, ale zjednodušuje následnou úpravu ve Wordu.

## Jak **group multiple shapes word** dokumenty programově

Vzor ukázaný výše – vytvořit kontejner skupiny, nakonfigurovat každý podřízený tvar a připojit – funguje pro libovolný počet tvarů: kruhy, obrázky, textová pole atd. Stačí opakovat kroky „vytvořit tvar → nastavit vlastnosti → připojit“ před voláním `doc.save()`.

Pokud potřebujete **add line to group** poté, co skupina již obsahuje jiné tvary, můžete získat existující skupinu pomocí:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Tím se ukazuje, že můžete skupinu upravovat v libovolném bodě životního cyklu dokumentu.

## Závěr

Nyní víte, jak **create grouped shapes** v dokumentu Word pomocí Javy a Aspose.Words. Pomocí **inserting group shape**, **adding line to group** a **group multiple shapes word** můžete vytvářet složité kresby, které se chovají jako jeden objekt – ideální pro diagramy, šablony a automatické generování zpráv.

Další související témata:

- **Applying styles to grouped shapes** – naučte se nastavit barvy výplně, okraje a efekty pro všechny potomky najednou.  
- **Exporting grouped shapes to PDF** – podívejte se, jak se stejná skupina zachová při konverzi dokumentu.  
- **Animating shapes with VBA** – kombinujte skupiny generované v Javě s makry Wordu pro interaktivní dokumenty.

Neváhejte experimentovat s různými typy tvarů, velikostmi a pozicemi. Seskupování vám poskytuje flexibilitu zacházet s mnoha objekty jako s jedním, což zjednodušuje jak kód, tak uživatelskou interakci. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}