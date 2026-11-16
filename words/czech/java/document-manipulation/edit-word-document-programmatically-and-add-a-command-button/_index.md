---
category: general
date: 2026-11-15
description: Programově upravte dokument Word a vložte příkazové tlačítko. Naučte
  se, jak přidat tlačítko, nastavit název příkazového tlačítka a vytvořit formulářové
  tlačítko ve Wordu během několika minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: cs
lastmod: 2026-11-15
og_description: Programově upravte dokument Word a vložte příkazové tlačítko. Tento
  průvodce ukazuje, jak přidat tlačítko, nastavit název příkazového tlačítka a rychle
  vytvořit formulářové tlačítko ve Wordu.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Upravit dokument Word programově – přidat tlačítko příkazu
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Programově upravit dokument Word a přidat příkazové tlačítko
url: /cs/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Upravit dokument Word programově a přidat příkazové tlačítko

Pokud potřebujete **upravit dokument Word programově**, nejrychlejší cesta je použít API Aspose.Words. Tento tutoriál vám přesně ukáže **jak přidat tlačítko** ovládací prvky, nastavit jejich popisek a **nastavit název příkazového tlačítka**, aby dokument mohl fungovat jako jednoduchý formulář. Na konci budete mít plně editovatelný *.docx*, který obsahuje funkční příkazové tlačítko připravené pro další zpracování.

Naučíte se, jak **vložit text příkazového tlačítka**, **vytvořit text tlačítka formuláře** a spravovat vlastnosti tlačítka, aniž byste museli otevírat Word ručně. Jedinou podmínkou je základní vývojové prostředí Java a knihovna Aspose.Words pro Java.

## Požadavky

- Java 17 nebo novější (kód funguje také s Java 8+)
- Aspose.Words pro Java (stáhněte z [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Existující dokument Word (`input.docx`), který chcete upravit
- Znalost Maven nebo Gradle pro přidání závislosti Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Krok 1: Načtení dokumentu Word

Prvním krokem při **úpravě dokumentu Word programově** je načíst zdrojový soubor do objektu `Document`. Tento objekt představuje celý soubor Word v paměti a umožňuje manipulovat s jeho obsahem.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Proč je to důležité:** Načtení dokumentu vytvoří strukturu podobnou DOM, kterou může Aspose.Words procházet a měnit. Vynechání tohoto kroku by vám nechalo bez cíle pro vložení tlačítka.

## Krok 2: Vytvoření `DocumentBuilder` pro úpravu dokumentu

`DocumentBuilder` funguje jako kurzor uvnitř souboru Word. Umožňuje vkládat text, obrázky a formulářové ovládací prvky na aktuální pozici.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** Pokud potřebujete tlačítko v konkrétním odstavci, nejprve přesuňte builder pomocí `builder.moveToParagraph(index, true);`.

## Krok 3: Vložení Forms2OleControl (příkazové tlačítko)

Nyní odpovídáme na hlavní otázku **jak přidat tlačítko** do souboru Word. Metoda `insertForms2OleControl()` vytvoří starší *Forms2.0* příkazové tlačítko, které je nejkompatibilnější napříč verzemi Wordu.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Hraniční případ:** Ovládací prvek Forms2.0 je viditelný pouze v *Design Mode* ve Wordu. Pokud potřebujete novější ActiveX tlačítko, zvažte místo toho `insertOleControl()`, ale starší ovládací prvek funguje pro většinu automatizačních scénářů.

## Krok 4: Nastavení vlastností tlačítka

Po vložení ovládacího prvku můžete **nastavit název příkazového tlačítka** a **vložit text příkazového tlačítka** (popisek), aby byl uživatelsky přívětivý.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Proč tyto vlastnosti?**  
> - `setName` přiřadí tlačítku identifikátor, na který může odkazovat VBA nebo externí nástroje.  
> - `setCaption` je viditelný štítek, efektivně **vytváří text tlačítka formuláře**, na který uživatelé kliknou.

Můžete také upravit velikost, pozici nebo přidat makro přístupem k podkladovému OLE objektu, ale tyto témata přesahují rozsah tohoto stručného návodu.

## Krok 5: Uložení upraveného dokumentu

Nakonec změny uložíte do nového souboru. Tento krok **vytvoří text tlačítka formuláře** v výstupním dokumentu.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Výsledek:** Po otevření `output.docx` v Microsoft Wordu uvidíte tlačítko s popiskem „Submit“. Když přepnete Word do *Design Mode* (Developer → Design Mode), můžete na tlačítko dvakrát kliknout a přiřadit mu makro, nebo jej použít jako zástupný prvek ve formuláři.

### Očekávaný výstup

Po otevření uloženého souboru:

- Vložený bod kurzoru je nahrazen tlačítkem.
- Tlačítko zobrazuje popisek **Submit**.
- Interní název tlačítka je **cmdSubmit**, který můžete odkazovat ve VBA nebo externích automatizačních skriptech.

## Časté otázky a varianty

### Jak přidat tlačítko do konkrétního odstavce?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Jak vložit tlačítko do buňky tabulky?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Co když potřebuji větší tlačítko?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Jak **vložit text příkazového tlačítka** pomocí jiného jazyka (např. C#)?

Stejná logika platí; nahraďte Java syntaxi ekvivalenty v C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Profesionální tipy a úskalí

- **Pro tip:** Vždy zavolejte `builder.moveToDocumentEnd()` před vložením tlačítka, pokud jej chcete umístit na úplný konec dokumentu.  
- **Dejte si pozor na:** Ukládání do stejného souboru, který jste otevřeli, může dokument poškodit, pokud dojde k výjimce. Použijte samostatnou výstupní cestu, jak je ukázáno.  
- **Kompatibilita:** Legacy tlačítko Forms2.0 funguje ve Wordu 2007‑2021. Pro Word na webu zvažte místo toho obsahové ovládací prvky.  
- **Výkon:** Načítání velmi velkých dokumentů (>100 MB) může spotřebovat značnou paměť. Použijte `Document.load(InputStream, LoadOptions)` s `LoadOptions.setLoadFormat(LoadFormat.DOCX)` pro omezení využití zdrojů.

## Kompletní funkční příklad

Níže je kompletní, připravený ke spuštění Java program. Zkopírujte jej do třídy pojmenované `WordButtonDemo.java`, upravte cesty k souborům a spusťte `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Spusťte program a otevřete `output.docx`, abyste ověřili, že se tlačítko zobrazuje podle očekávání.

## Závěr

Nyní víte, jak **upravit dokument Word programově** k **vloženému textu příkazového tlačítka**, **vytvořit text tlačítka formuláře** a **nastavit název příkazového tlačítka** pomocí Aspose.Words pro Java. Tento přístup eliminuje ruční úpravy, umožňuje hromadné zpracování formulářů a hladce se integruje do automatizovaných pracovních postupů.

Dále můžete zkoumat:

- Přidání VBA makra do tlačítka (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Použití **obsahových ovládacích prvků** pro bohatší formulářové zážitky (`builder.insertCheckBox()` atd.)  
- Automatizaci hromadného vkládání napříč více dokumenty pomocí smyčky  

Neváhejte experimentovat s velikostí, pozicí a obsluhou událostí tlačítka, aby vyhovovaly vašemu konkrétnímu scénáři. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}