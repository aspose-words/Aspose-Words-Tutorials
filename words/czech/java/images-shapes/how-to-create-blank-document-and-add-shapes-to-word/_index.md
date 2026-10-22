---
category: general
date: 2026-09-18
description: Vytvořte prázdný dokument a vložte tvary do Wordu pomocí Aspose.Words
  – naučte se, jak přidat trojúhelníkový tvar a další.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: cs
lastmod: 2026-09-18
og_description: Vytvořte prázdný dokument ve Wordu pomocí Aspose.Words a naučte se,
  jak vložit trojúhelníkový tvar, seskupovat tvary a další grafiku. Postupujte podle
  tohoto kompletního návodu.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Vytvořte prázdný dokument a přidejte tvary do Wordu – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Jak vytvořit prázdný dokument a přidat tvary do Wordu
url: /cs/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument a přidat tvary do Wordu

Pokud potřebujete **vytvořit prázdný dokument** a poté jej obohatit o grafiku, tento návod vám ukáže přesně jak. Provedeme vás vytvořením souboru Word od nuly a **přidáním tvarů do Wordu**, včetně **vložení trojúhelníkového** tvaru, pomocí Aspose.Words pro Java.

Na konci tutoriálu budete mít připravený *.docx* soubor, který obsahuje seskupený tvar s trojúhelníkem. Kroky pokrývají vše od nastavení projektu až po uložení finálního **create word document**. Kromě Aspose.Words nejsou vyžadovány žádné externí nástroje.

## Požadavky

Než začnete, ujistěte se, že máte:

* Java 17 nebo novější nainstalovanou  
* Maven nebo Gradle pro správu závislostí  
* Licenci Aspose.Words pro Java (bezplatná zkušební verze stačí pro tento ukázkový projekt)  

Pokud dáváte přednost jinému build systému, upravte syntaxi závislostí podle potřeby. Kód funguje na jakékoli platformě, která podporuje Javu.

## Vytvoření prázdného dokumentu pomocí Aspose.Words

Prvním krokem je **vytvořit prázdný dokument** v paměti. Aspose.Words poskytuje třídu `Document`, která představuje soubor Word bez jakéhokoli obsahu.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Konstruktor `new Document()` vytvoří prázdnou strukturu *.docx*, kterou můžete později naplnit odstavci, tabulkami nebo grafikou. Protože je dokument prázdný, máte plnou kontrolu nad každým prvkem, který přidáte.

## Přidání tvarů do Wordu – vložení skupinového tvaru

Skupinový tvar vám umožní zacházet s několika grafikami jako s jednou jednotkou. To je užitečné, když chcete přesunout nebo změnit velikost více tvarů najednou.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` je hlavní API pro přidávání obsahu. Volání `insertGroupShape` vytvoří kontejner o rozměrech 300 × 300 bodů (přibližně 4 × 4 palce). Po tomto volání je kurzor umístěn *uvnitř* skupiny, připravený na další tvary.

### Proč použít skupinový tvar?

Seskupování udržuje související grafiku zarovnanou a usnadňuje aplikaci jednotného formátování. Pokud později rozhodnete přesunout trojúhelník, celá skupina se přesune společně a zachová rozložení.

## Jak vložit trojúhelníkový tvar do skupiny

Nyní se zaměříme na **vložení trojúhelníkového** tvaru. Trojúhelník je jednou ze zabudovaných hodnot `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Volání `moveTo` zajistí, že vkládací bod builderu je první odstavec ve skupině. `insertShape` pak přidá trojúhelník o rozměrech 60 × 60 bodů. Protože je kurzor uvnitř skupiny, trojúhelník se stane podřízeným tvarem skupiny.

**Tipy pro přidání trojúhelníkového tvaru**:

* Velikost se měří v bodech; 72 bodů odpovídá jednomu palci. Přizpůsobte rozměry podle svého rozvržení.  
* Pokud potřebujete jinou orientaci, použijte `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` k zarovnání tvaru ve skupině.  
* Trojúhelník dědí výplň a čárové styly skupiny, pokud je nepřepíšete pomocí `shape.getFillColor()` nebo `shape.getStrokeColor()`.

## Uložení dokumentu – create word document

Po vytvoření grafiky soubor uložíte. Tento krok dokončuje operaci **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` zapíše paměťovou reprezentaci na disk jako standardní Word dokument. Soubor `ExtendedGroup.docx` můžete otevřít v Microsoft Word, LibreOffice nebo v libovolném prohlížeči podporujícím formát OOXML. Soubor zobrazí seskupený tvar obsahující trojúhelník, přesně tak, jak byl vytvořen kódem.

## Kompletní spustitelný příklad

Spojením všech částí získáte kompletní program, který můžete zkopírovat, zkompilovat a spustit:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Očekávaný výsledek

Po otevření `ExtendedGroup.docx` uvidíte jediný skupinový tvar uprostřed stránky. Uvnitř této skupiny se na výchozí pozici objeví malý trojúhelník. Trojúhelník lze vybrat a přesunout jako součást skupiny, což potvrzuje, že **add shapes to word** fungovalo podle očekávání.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| *Mohu do skupiny přidat více než jeden tvar?* | Ano. Po vložení trojúhelníku nechte kurzor uvnitř skupiny a znovu zavolejte `builder.insertShape` s jiným `ShapeType`. |
| *Co když potřebuji, aby byl trojúhelník červený?* | Získejte objekt `Shape` vrácený metodou `insertShape` a zavolejte `shape.getFillColor().setColor(Color.RED)`. |
| *Funguje to i se staršími .doc soubory?* | Aspose.Words ukládá ve formátu, který určíte. Použijte `doc.save("file.doc", SaveFormat.DOC)` pro vytvoření staršího Word dokumentu. |
| *Jak změním okraj skupiny?* | Použijte `group.getStrokeColor().setColor(Color.BLUE)` a `group.setLineWeight(2.0)` pro úpravu obrysu. |
| *Existuje způsob, jak otočit trojúhelník?* | Zavolejte `shape.getRotation()` a nastavte úhel ve stupních. |

## Profesionální tipy

* **Znovupoužívejte builder** – vytváření nového `DocumentBuilder` pro každý tvar přináší režii. Používejte jediný builder na celý dokument.  
* **Převod jednotek** – pokud pracujete s milimetry, převeďte je na body (`points = mm * 2.83465`).  
* **Výkon** – u velkých dokumentů volejte `doc.updatePageLayout()` jen jednou po přidání všech tvarů.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument**, **přidat tvary do Wordu** a konkrétně **vložit trojúhelníkový** tvar pomocí Aspose.Words pro Java. Kompletní příklad demonstruje celý workflow od prázdného souboru po uložený **create word document**, který obsahuje seskupený trojúhelník.

Odtud můžete zkoumat další hodnoty `ShapeType`, aplikovat vlastní stylování nebo kombinovat více skupin pro tvorbu složitých diagramů. Experimentujte s různými velikostmi, barvami a pozicemi a ovládněte automatizaci Wordu v Javě.

--- 

*Připraven(a) automatizovat další zprávu? Naklonujte příklad, upravte rozměry a integrujte kód do své vlastní aplikace ještě dnes.*


## Co byste se měli naučit dál?


Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}