---
title: Přidání obsahu pomocí DocumentBuilder v Aspose.Words for Java
linktitle: Přidávání obsahu pomocí DocumentBuilder
second_title: Aspose.Words Java Document Processing API
description: Vytvoření hlavního dokumentu pomocí Aspose.Words pro Javu. Podrobný průvodce přidáváním textu, tabulek, obrázků a dalších. Vytvářejte úžasné dokumenty Word bez námahy.
weight: 26
url: /cs/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání obsahu pomocí DocumentBuilder v Aspose.Words for Java


## Úvod do přidávání obsahu pomocí DocumentBuilder v Aspose.Words for Java

V tomto podrobném průvodci prozkoumáme, jak používat Aspose.Words for Java's DocumentBuilder k přidání různých typů obsahu do dokumentu aplikace Word. Budeme se zabývat vkládáním textu, tabulek, vodorovných pravidel, polí formulářů, HTML, hypertextových odkazů, obsahu, vložených a plovoucích obrázků, odstavců a dalších. Začněme!

## Předpoklady

 Než začnete, ujistěte se, že máte v projektu nastavenou knihovnu Aspose.Words for Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Přidání textu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte jednoduchý textový odstavec
builder.write("This is a simple text paragraph.");

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidávání tabulek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Založte stůl
Table table = builder.startTable();

// Vložte buňky a obsah
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Ukončete stůl
builder.endTable();

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidání horizontálního pravidla

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte vodorovné pravítko
builder.insertHorizontalRule();

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidání polí formuláře

### Pole formuláře pro zadávání textu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte pole formuláře pro zadávání textu
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Uložte dokument
doc.save("path/to/your/document.docx");
```

### Zaškrtávací políčko Pole formuláře

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte zaškrtávací pole formuláře
builder.insertCheckBox("CheckBox", true, true, 0);

// Uložte dokument
doc.save("path/to/your/document.docx");
```

### Pole formuláře Combo Box

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definujte položky pro pole se seznamem
String[] items = { "Option 1", "Option 2", "Option 3" };

// Vložte pole formuláře pole se seznamem
builder.insertComboBox("DropDown", items, 0);

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidání HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte obsah HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidávání hypertextových odkazů

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte hypertextový odkaz
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", nepravda);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidání obsahu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte obsah
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Přidejte obsah dokumentu
// ...

// Aktualizujte obsah
doc.updateFields();

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidávání obrázků

### Vložený obrázek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte vložený obrázek
builder.insertImage("path/to/your/image.png");

// Uložte dokument
doc.save("path/to/your/document.docx");
```

### Plovoucí obrázek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte plovoucí obrázek
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Přidávání odstavců

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Nastavte formátování odstavce
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

// Vložte odstavec
builder.writeln("This is a formatted paragraph.");

// Uložte dokument
doc.save("path/to/your/document.docx");
```

## Krok 10: Přesunutí kurzoru

 Pozici kurzoru v dokumentu můžete ovládat různými způsoby, např`moveToParagraph`, `moveToCell`další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Přesuňte kurzor na konkrétní odstavec
builder.moveToParagraph(2, 0);

// Přidejte obsah na novou pozici kurzoru
builder.writeln("This is the 3rd paragraph.");
```

Toto jsou některé běžné operace, které můžete provádět pomocí Aspose.Words pro Java's DocumentBuilder. Prozkoumejte dokumentaci knihovny, kde najdete pokročilejší funkce a možnosti přizpůsobení. Šťastné vytváření dokumentů!


## Závěr

V tomto komplexním průvodci jsme prozkoumali možnosti aplikace Aspose.Words for Java DocumentBuilder pro přidávání různých typů obsahu do dokumentů aplikace Word. Probrali jsme text, tabulky, horizontální pravidla, pole formuláře, HTML, hypertextové odkazy, obsah, obrázky, odstavce a pohyb kurzoru.

## FAQ

### Otázka: Co je Aspose.Words for Java?

A: Aspose.Words for Java je knihovna Java, která umožňuje vývojářům vytvářet, upravovat a manipulovat s dokumenty Microsoft Word programově. Poskytuje širokou škálu funkcí pro generování dokumentů, formátování a vkládání obsahu.

### Otázka: Jak mohu přidat obsah do svého dokumentu?

A: Chcete-li přidat obsah, použijte`DocumentBuilder` pro vložení pole obsahu do dokumentu. Po přidání obsahu nezapomeňte aktualizovat pole v dokumentu, aby se naplnil obsah. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte pole obsahu
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Přidejte obsah dokumentu
// ...

// Aktualizujte obsah
doc.updateFields();
```

### Otázka: Jak vložím obrázky do dokumentu pomocí Aspose.Words for Java?

 Odpověď: Obrázky, vložené i plovoucí, můžete vkládat pomocí`DocumentBuilder`. Zde jsou příklady obou:

#### Vložený obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte vložený obrázek
builder.insertImage("path/to/your/image.png");
```

#### Plovoucí obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte plovoucí obrázek
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Otázka: Mohu při přidávání obsahu formátovat text a odstavce?

 Odpověď: Ano, text a odstavce můžete formátovat pomocí`DocumentBuilder`. Můžete nastavit vlastnosti písma, zarovnání odstavce, odsazení a další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Nastavte písmo a formátování odstavce
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

// Vložte formátovaný odstavec
builder.writeln("This is a formatted paragraph.");
```

### Otázka: Jak mohu přesunout kurzor na určité místo v dokumentu?

 Odpověď: Pozici kurzoru můžete ovládat pomocí metod jako`moveToParagraph`, `moveToCell`další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Přesuňte kurzor na konkrétní odstavec
builder.moveToParagraph(2, 0);

// Přidejte obsah na novou pozici kurzoru
builder.writeln("This is the 3rd paragraph.");
```

Toto jsou některé běžné otázky a odpovědi, které vám pomohou začít s Aspose.Words pro Java's DocumentBuilder. Pokud máte další otázky nebo potřebujete další pomoc, přejděte na stránku[dokumentaci knihovny](https://reference.aspose.com/words/java/) nebo vyhledejte pomoc od komunity Aspose.Words a zdrojů podpory.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
