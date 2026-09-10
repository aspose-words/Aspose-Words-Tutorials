---
date: 2026-01-01
description: Naučte se, jak vytvářet pole formuláře a přidávat text, tabulky, obrázky,
  hypertextové odkazy a další pomocí třídy DocumentBuilder v Aspose.Words pro Javu.
  Krok za krokem průvodce pro vývojáře.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words
  pro Javu
url: /cs/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidávání obsahu pomocí DocumentBuilder v Aspose.Words pro Java

## Úvod do přidávání obsahu pomocí DocumentBuilder v Aspose.Words pro Java

V tomto podrobném průvodci **vytvoříte formulářová pole** a přidáte různorodý obsah — text, tabulky, vodorovné čáry, HTML, hypertextové odkazy, obrázky a další — do dokumentu Word pomocí Aspose.Words pro Java. Ať už vytváříte zprávu, šablonu smlouvy nebo interaktivní formulář, třída `DocumentBuilder` vám poskytuje detailní kontrolu nad každým prvkem. Pojďme na to!

## Rychlé odpovědi
- **Jak vytvořím formulářová pole?** Použijte `insertTextInput`, `insertCheckBox` nebo `insertComboBox` na objektu `DocumentBuilder`.
- **Jaká metoda přidá prostý text?** Zavolejte `builder.write("Váš text")` nebo `builder.writeln("Váš text")`.
- **Mohu vložit vodorovnou čáru?** Ano — `builder.insertHorizontalRule()` vloží oddělovač.
- **Jak vložit HTML?** Použijte `builder.insertHtml("<p>HTML obsah</p>")`.
- **Jak přidat vložený obrázek?** `builder.insertImage("cesta/k/obrazku.png")` umístí obrázek do toku textu.

## Co je DocumentBuilder a proč jej použít k vytvoření formulářových polí?

`DocumentBuilder` je fluent API Aspose.Words pro programové vytváření a úpravu dokumentů Word. Skrývá nízkoúrovňovou strukturu OpenXML, takže se můžete soustředit na *co* chcete přidat — například **formulářová pole** — místo na *jak* vypadá XML. To z něj dělá ideální nástroj pro generování dynamických formulářů, smluv nebo jakýchkoli dokumentů vyžadujících interakci uživatele.

## Předpoklady

Než začnete, ujistěte se, že máte v projektu nainstalovanou knihovnu Aspose.Words pro Java. Stáhnout ji můžete [zde](https://releases.aspose.com/words/java/).

## Přidávání textu (jak přidat text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidávání tabulek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidávání vodorovné čáry (přidat vodorovnou čáru)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidávání formulářových polí (vytvořit formulářová pole)

### Textové vstupní formulářové pole

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Zaškrtávací políčko formulářového pole

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Kombinované políčko formulářového pole

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Vkládání HTML (vložit html do Wordu)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Vkládání hypertextových odkazů (jak přidat hypertextový odkaz)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidání obsahu rejstříku (Table of Contents)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidávání obrázků

### Vložený obrázek (vložit inline obrázek)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Plovoucí obrázek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Přidávání odstavců

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Posouvání kurzoru (Krok 10)

Kurzoru v dokumentu můžete řídit pomocí metod jako `moveToParagraph`, `moveToCell` a dalších.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Jedná se o některé běžné operace, které můžete provádět pomocí `DocumentBuilder` v Aspose.Words pro Java. Prozkoumejte dokumentaci knihovny pro pokročilejší funkce a možnosti přizpůsobení. Šťastné tvoření dokumentů!

## Závěr

V tomto uceleném průvodci jsme ukázali, jak **vytvořit formulářová pole** a přidat různé typy obsahu — text, tabulky, vodorovné čáry, HTML, hypertextové odkazy, rejstřík, obrázky, formátované odstavce a navigaci kurzorem — pomocí `DocumentBuilder` v Aspose.Words pro Java. Nyní máte pevný základ pro programové generování dynamických, interaktivních dokumentů Word.

## Často kladené dotazy

### Otázka: Co je Aspose.Words pro Java?

**Odpověď:** Aspose.Words pro Java je knihovna pro jazyk Java, která umožňuje vývojářům programově vytvářet, upravovat a manipulovat s dokumenty Microsoft Word. Poskytuje širokou škálu funkcí pro generování dokumentů, formátování a vkládání obsahu.

### Otázka: Jak mohu do svého dokumentu přidat rejstřík?

**Odpověď:** Pro přidání rejstříku použijte `DocumentBuilder` k vložení pole TOC a poté po přidání obsahu zavolejte `doc.updateFields()`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Otázka: Jak vložit obrázky do dokumentu pomocí Aspose.Words pro Java?

**Odpověď:** Obrázky, jak vložené, tak plovoucí, můžete vložit pomocí `DocumentBuilder`.

#### Vložený obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Plovoucí obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Otázka: Mohu formátovat text a odstavce při přidávání obsahu?

**Odpověď:** Ano, text a odstavce můžete formátovat pomocí `DocumentBuilder`. Před zápisem obsahu nastavte vlastnosti písma, zarovnání odstavce, odsazení a další.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Otázka: Jak mohu přesunout kurzor na konkrétní místo v dokumentu?

**Odpověď:** Použijte metody jako `moveToParagraph`, `moveToCell` a podobně k umístění kurzoru před vložením nového obsahu.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Tyto odpovědi pokrývají nejčastější scénáře při práci s `DocumentBuilder` v Aspose.Words pro Java. Pro podrobnější informace se podívejte na [dokumentaci knihovny](https://reference.aspose.com/words/java/) nebo se připojte ke komunitě Aspose.Words pro podporu.

---

**Poslední aktualizace:** 2026-01-01  
**Testováno s:** Aspose.Words pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}