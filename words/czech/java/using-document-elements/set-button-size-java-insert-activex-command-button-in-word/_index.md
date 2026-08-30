---
category: general
date: 2026-07-29
description: 'Nastavení velikosti tlačítka – Java tutoriál: naučte se, jak vložit
  ActiveX příkazové tlačítko do dokumentu Word pomocí Javy a Aspose.Words, včetně
  nastavení velikosti a vytvoření prázdného dokumentu.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: cs
lastmod: 2026-07-29
og_description: Průvodce nastavením velikosti tlačítka v Javě ukazuje, jak pomocí
  Javy vložit ActiveX příkazové tlačítko do souboru Word, upravit jeho velikost a
  programově uložit dokument.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Nastavit velikost tlačítka v Javě – Přidat ActiveX Command Button do Wordu
  pomocí Javy
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Nastavit velikost tlačítka v Javě – Vložit ActiveX Command Button do Wordu
url: /cs/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# nastavit velikost tlačítka java – Vložit ActiveX Command Button ve Wordu

Už jste se někdy zamysleli nad tím, **jak nastavit velikost tlačítka java**, když automatizujete Word dokumenty? Možná vytváříte nástroj pro reportování, který potřebuje klikatelné tlačítko „Submit“ přímo v souboru .docx. V tomto tutoriálu projdeme celý proces – vytvoření prázdného Word dokumentu, vložení ActiveX command button a explicitní nastavení jeho šířky a výšky – vše pomocí Javy a Aspose.Words.

Také odpovíme na dlouholetou otázku „jak vložit activex“, která se objevuje u mnoha vývojářů. Na konci budete mít spustitelný program, který vytvoří Word soubor obsahující perfektně veliké tlačítko, připravené k dalším úpravám.

---

## Co budete potřebovat

- **Java Development Kit (JDK) 8 nebo novější** – kód se kompiluje s libovolným aktuálním JDK.
- **Aspose.Words for Java** (nejnovější verze k červenci 2026). Stáhněte JAR z [Aspose website](https://products.aspose.com/words/java) nebo přes Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- IDE nebo jednoduchý textový editor – IntelliJ IDEA, Eclipse nebo VS Code budou stačit.
- Složka, kam chcete uložit vygenerovaný **CommandButton.docx**.

A to je vše. Žádné další knihovny pro Office interop, žádné COM triky, jen čistá Java.

---

## Implementace krok za krokem

Rozdělíme řešení do pěti logických kroků. Každý krok má vlastní nadpis H2; jeden z nich obsahuje naše **primární klíčové slovo** pro SEO.

### 1. Nastavení projektu a import Aspose.Words

Nejprve vytvořte nový Maven (nebo Gradle) projekt a přidejte závislost Aspose.Words, jak je uvedeno výše. Poté importujte požadované třídy ve vašem Java souboru:

```java
import com.aspose.words.*;
```

> **Tip:** Pokud používáte IDE, nechte ji automaticky importovat třídy. Ušetří to spoustu psaní a zabrání překlepům.

### 2. java create blank word Document

Nyní skutečně **java create blank word** dokument. Toto je základ, na který později **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Objekt `Document` představuje celý Word soubor v paměti. V tomto okamžiku soubor nemá žádné stránky, žádný text – jen čistý list.

### 3. Inicializace DocumentBuilder a vložení ActiveX ovládacího prvku

`DocumentBuilder` je pomocník, který nám umožňuje přidávat obsah, odstavce, tabulky a ano, i ActiveX ovládací prvky. Zde odpovídáme na **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` je obal Aspose kolem OLE objektu. Zadáním `COMMANDBUTTON` říkáme Wordu, aby vložil klasické ActiveX command button.

### 4. How to Set Button Size Java – Úprava šířky a výšky

Nyní přichází jádro tutoriálu: **how to set button size java**. Ovládací prvek poskytuje několik vlastností rozvržení – `Left`, `Top`, `Width` a `Height`. Přímé nastavení těchto hodnot ovlivňuje vzhled tlačítka na stránce.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Proč právě tyto čísla? Ve Wordu jeden bod odpovídá 1/72 palce. Šířka `120` bodů tedy odpovídá přibližně 1,67 palce – dostatečně velká pro čitelný popisek, ale ne příliš. Přizpůsobte hodnoty podle svého rozvržení; stejné vlastnosti také odpovídají na dotaz **how to set button**, který můžete mít.

> **Poznámka:** Pokud potřebujete jiný typ tlačítka (např. zaškrtávací políčko), nahraďte `Forms2OleControlType.COMMANDBUTTON` odpovídající hodnotou enumu.

### 5. Uložení dokumentu

Nakonec uložte dokument na disk:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Nahraďte `YOUR_DIRECTORY` absolutní nebo relativní cestou na vašem počítači. Po spuštění programu otevřete vygenerovaný soubor v Microsoft Wordu. Uvidíte tlačítko s popiskem „Click Me“, umístěné 100 bodů od levého okraje a 200 bodů od horního, přesně ve velikosti, kterou jsme nastavili.

---

## Kompletní funkční příklad

Níže je kompletní, připravená ke spuštění Java třída. Zkopírujte ji do `CommandButtonActiveX.java`, upravte výstupní cestu a stiskněte **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Očekávaný výstup:** Otevřením `CommandButton.docx` ve Wordu se zobrazí jedna stránka s klikacím tlačítkem „Click Me“ umístěným přibližně uprostřed stránky. Rozměry tlačítka odpovídají nastaveným hodnotám, což potvrzuje, že **set button size java** funguje podle očekávání.

---

## Časté otázky a okrajové případy

### Co když se tlačítko ve Wordu nezobrazí?

- **Zkontrolujte verzi Wordu.** ActiveX ovládací prvky vyžadují desktopovou verzi Wordu; Word Online je odstraňuje.
- **Ujistěte se, že je použita licence Aspose.Words** (pokud používáte placenou edici). Nelicencovaná evaluační verze může vložit vodoznak, ale ovládací prvek stále zobrazí.

### Můžu změnit font nebo barvu tlačítka?

Ano. Po vložení ovládacího prvku můžete přistupovat k jeho podkladovému OLE objektu a manipulovat s VBA vlastnostmi. To je pokročilejší téma – podívejte se například na `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` pro červený popisek.

### Jak zvládnout událost kliknutí tlačítka?

ActiveX command button spouští VBA událost `Click`. Aby tlačítko fungovalo, musíte do stejného dokumentu vložit makro. Aspose.Words může přidat modul makra pomocí API `Document.getMacros()`, ale samotný kód makra musí být napsán ve VBA.

### Co s různými typy tlačítek?

Aspose.Words podporuje mnoho hodnot `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` atd. Pro experimentování zaměňte enum konstantu v volání `insertForms2OleControl`.

---

## Tipy pro produkční kód

1. **Používejte konstanty pro hodnoty rozvržení** – usnadní to budoucí úpravy.
2. **Zabalte cestu pro uložení do objektu `Path`** aby se předešlo specifickým oddělovačům platformy.
3. **Uvolněte Document** (nebo použijte try‑with‑resources), pokud zpracováváte mnoho souborů ve smyčce.
4. **Ověřte výstupní složku** před voláním `save`, aby nedošlo k `FileNotFoundException`.

---

## Závěr

Právě jste se naučili **set button size java** vytvořením prázdného Word souboru, vložením ActiveX command button a přesným nastavením jeho rozměrů – vše pomocí několika řádků Java kódu. Toto pokrývá jádro **how to insert activex**, **how to set button**, **java create blank word** a **insert command button word** v jednom samostatném příkladu.

Další kroky? Zkuste přizpůsobit popisek tlačítka, přidat makro reagující na kliknutí nebo vložit více ovládacích prvků na stejnou stránku. Můžete také prozkoumat konverzi výsledného .docx do PDF pomocí Aspose.Words, přičemž tlačítko bude zachováno jako statický obrázek.

Klidně experimentujte a pokud narazíte na problém, zanechte komentář níže. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}