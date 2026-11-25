---
category: general
date: 2026-11-25
description: Skryjte tvar ve Wordu pomocí Aspose.Words a naučte se vytvářet Word dokumenty
  s Aspose, když vložíte obdélníkový tvar, během několika řádků kódu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: cs
lastmod: 2026-11-25
og_description: Skrytí tvaru ve Wordu pomocí Aspose.Words. Tento tutoriál vám ukáže,
  jak vytvořit Word dokument pomocí Aspose, vložit obdélníkový tvar do Wordu a skrýt
  jej programově.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Skrytí tvaru ve Wordu pomocí Aspose.Words – rychlý krok‑za‑krokem návod
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Jak skrýt tvar ve Wordu pomocí Aspose.Words
url: /cs/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak skrýt tvar ve Wordu pomocí Aspose.Words

Pokud potřebujete **skrýt tvar ve Wordu** při programovém generování dokumentů, Aspose.Words to usnadňuje. V tomto průvodci uvidíte přesně, jak vytvořit Word dokument pomocí aspose, vložit obdélníkový tvar do Wordu a poté tento tvar skrýt, aby se neobjevil v rozvržení. Kompletní, spustitelný příklad je k dispozici, takže jej můžete zkopírovat a vložit do svého IDE a okamžitě vidět výsledek.

Po dokončení tohoto tutoriálu budete mít soubor Word, který obsahuje skrytý obdélník – užitečný pro zástupné symboly, podmíněný obsah nebo metadata, která mají zůstat neviditelná pro čtenáře. Kromě knihovny Aspose.Words pro Java (nebo .NET) nejsou potřeba žádné externí nástroje.

## Co se naučíte

* Jak **vytvořit Word dokument pomocí aspose** od nuly.  
* Jak **vložit obdélníkový tvar do Wordu** pomocí `DocumentBuilder`.  
* Jak nastavit vlastnost `hidden` tvaru, aby se nezobrazoval v konečném rozvržení.  
* Jak ověřit, že je tvar skrytý, a jak jej v případě potřeby znovu zobrazit.  

### Požadavky

* Java 17+ (nebo .NET 6+, pokud dáváte přednost C# — API volání jsou analogická).  
* Aspose.Words pro Java 24.x (nejnovější verze v době psaní).  
* IDE, například IntelliJ IDEA, Eclipse nebo VS Code.  

> **Tip:** Použijte bezplatnou dočasnou licenci od Aspose, pokud ještě nemáte komerční licenci. Knihovna funguje bez licence pro hodnocení, ale licence odstraňuje vodoznaky hodnocení.

## Skrýt tvar ve Wordu pomocí Aspose.Words

Základní kroky jsou:

1. **Vytvořit nový `Document`.**  
2. **Vložit obdélníkový tvar** pomocí `DocumentBuilder`.  
3. **Označit tvar jako skrytý**, aby se neobjevil při otevření souboru.  

### Krok 1: Vytvořit Word dokument pomocí aspose

Nejprve vytvořte prázdný `Document` a `DocumentBuilder`. Builder poskytuje plynulé API pro přidávání obsahu, včetně tvarů.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:**  
Vytvoření nového `Document` vám poskytne čisté plátno. `DocumentBuilder` je doporučený způsob úpravy dokumentu, protože automaticky sleduje aktuální vkládací bod a spravuje sekce/stránky za vás.

### Krok 2: Vložit obdélníkový tvar do Wordu

Nyní přidáme obdélníkový tvar. Metoda `insertShape` vyžaduje typ tvaru a jeho rozměry v bodech (1 bod = 1/72 palce).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Proč je to důležité:**  
`insertShape` vytváří kreslicí objekt, který žije v části *drawing* dokumentu. Zadáním velikosti řídíte, kolik místa by tvar zabíral, pokud by byl viditelný. Volitelné stylování vám pomůže ověřit tvar před jeho skrytím.

### Krok 3: Skrýt tvar, aby se neobjevil v rozvržení

Aspose.Words odráží atribut *Hidden* Microsoft Wordu. Nastavením na `true` řeknete Wordu, aby tvar nevypsal, přičemž objekt zůstane v struktuře dokumentu.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Proč je to důležité:**  
Skrytý tvar lze stále programově přistupovat (např. pro podmíněné zpracování) a lze jej později znovu zobrazit přepnutím vlastnosti. To je ideální pro scénáře, jako jsou **podmíněné zástupné symboly**, které by se měly zobrazit jen pro určité publikum.

### Krok 4: Uložit a ověřit výsledek

Nakonec zapište dokument na disk. Otevřete soubor v Microsoft Wordu a potvrďte, že obdélník není viditelný. Můžete také prozkoumat podkladové XML a vidět příznak skrytí.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Očekávaný výstup:**  
Spuštění programu vypíše:

```
Document saved to HideShapeResult.docx
```

Když otevřete *HideShapeResult.docx* ve Wordu, stránka vypadá prázdně (nebo obsahuje jakýkoli jiný obsah, který jste před tvarem přidali). Obdélník je přítomen v XML souboru (`<w:hidden>` atribut), ale není vykreslen.

### Krok 5: (Volitelné) Znovu zobrazit tvar později

Pokud potřebujete tvar znovu zobrazit, načtěte dokument, najděte tvar a nastavte `hidden` na `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Proč je to důležité:**  
Možnost přepínat příznak skrytí vám dává plnou kontrolu nad dynamickým generováním dokumentů — např. můžete vytvořit hlavní dokument se všemi volitelnými prvky skrytými a poté je selektivně zobrazit podle preferencí uživatele.

## Kompletní, spustitelný příklad (vytvořit Word dokument pomocí aspose, vložit obdélníkový tvar do Wordu, skrýt tvar)

Níže je kompletní program, který můžete přímo zkompilovat a spustit.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Spuštění kódu**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Nahraďte `aspose-words-24.10.jar` skutečnou verzí, kterou jste stáhli.

### Co obsahují výstupní soubory

* **HideShapeResult.docx** – obdélník je skrytý; stránka vypadá prázdně.  
* **UnhiddenShape.docx** – stejný obdélník je viditelný, zobrazuje červený rámeček s černým obrysem.

## Časté otázky a řešení okrajových případů

| Question | Answer |
|----------|--------|
| *Ovlivní skrytý tvar stránkování?* | Ne. Skryté objekty jsou ignorovány layoutovým enginem, takže neposouvají text na novou stránku. |
| *Mohu skrýt i jiné objekty ve Wordu (např. obrázky, tabulky)?* | Ano. Většina podtříd `Node` (včetně `Shape`, `Paragraph`, `Run`) poskytuje metodu `setHidden(boolean)`. |
| *Co když dokument již obsahuje tvary?* | Použijte `doc.getChildNodes(NodeType.SHAPE, true)` k iteraci a skrytí pouze těch tvarů, které chcete. |
| *Zvyšuje skrytí tvaru velikost souboru?* | Mírně, protože XML tvaru zůstává. Dopad je pro typické dokumenty zanedbatelný. |
| *Zůstane příznak skrytí při uložení dokumentu jako PDF?* | Při konverzi do PDF jsou skryté tvary ve výchozím nastavení vynechány. V případě potřeby to můžete řídit pomocí `PdfSaveOptions`. |

## Nejlepší postupy při práci se skrytými objekty

* **Pojmenujte své tvary** pomocí `setName("MyPlaceholder")`. To usnadní jejich pozdější vyhledání.  
* **Seskupte související skryté objekty** uvnitř `GroupShape`, pokud potřebujete najednou přepínat viditelnost několika prvků.  
* **Zdokumentujte účel** skrytých prvků v komentářích nebo samostatném specifikačním souboru — budoucí správci ocení kontext.  
* **Vyhněte se nadměrnému používání skrytých objektů**; zvyšují složitost dokumentu a mohou zmást koncové uživatele, kteří manuálně kontrolují XML.

## Závěr

Nyní víte, jak **skrýt tvar ve Wordu** pomocí Aspose.Words, jak **vytvořit Word dokument pomocí aspose** a jak **vložit obdélníkový tvar do Wordu** před jeho skrytím. Příklad ukazuje celý životní cyklus: vytvoření, vložení, skrytí, uložení a případně opětovné zobrazení. Použijte tyto techniky k tvorbě dynamických reportů, podmíněných šablon nebo jakéhokoli automatizovaného pracovního postupu ve Wordu, kde jsou potřeba neviditelné zástupné symboly.

### Další kroky

* Prozkoumejte **podmíněný obsah** kombinací skrytých tvarů s poli hromadné korespondence.  
* Naučte se, jak **skrýt textové běhy** (`Run.setHidden(true)`) pro podrobnější kontrolu.  
* Podívejte se do dokumentace Aspose.Words na **ochranu dokumentu**, aby uživatelé neodhalili tvary omylem.

Šťastné programování a ať vaše generované soubory Word zůstávají čisté, zatímco nesou skrytá data, která potřebujete!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument programově, přidat a skrýt tvar v Javě pomocí Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Jak skrýt tvar ve Word dokumentu pomocí Javy](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Vytvořit prázdný .docx Word dokument a přidat skrytý obdélníkový tvar pomocí Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}