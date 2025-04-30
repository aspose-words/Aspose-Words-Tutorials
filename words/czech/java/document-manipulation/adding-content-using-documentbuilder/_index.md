---
"description": "Zvládněte tvorbu dokumentů s Aspose.Words pro Javu. Podrobný návod k přidávání textu, tabulek, obrázků a dalších prvků. Vytvářejte úžasné dokumenty Word bez námahy."
"linktitle": "Přidávání obsahu pomocí nástroje DocumentBuilder"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Přidávání obsahu pomocí DocumentBuilderu v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidávání obsahu pomocí DocumentBuilderu v Aspose.Words pro Javu


## Úvod do přidávání obsahu pomocí DocumentBuilderu v Aspose.Words pro Javu

V tomto podrobném návodu se podíváme na to, jak pomocí nástroje DocumentBuilder v jazyce Java od Aspose.Words přidat různé typy obsahu do dokumentu Word. Probereme vkládání textu, tabulek, vodorovných linek, polí formulářů, HTML, hypertextových odkazů, obsahu, vložených a plovoucích obrázků, odstavců a dalších věcí. Začněme!

## Předpoklady

Než začnete, ujistěte se, že máte ve svém projektu nastavenou knihovnu Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Přidávání textu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložení jednoduchého odstavce textu
builder.write("This is a simple text paragraph.");

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidávání tabulek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Založit tabulku
Table table = builder.startTable();

// Vložit buňky a obsah
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Konec stolu
builder.endTable();

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidání vodorovné pravítka

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit vodorovnou linii
builder.insertHorizontalRule();

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidávání polí formuláře

### Pole formuláře pro zadávání textu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložení textového pole formuláře
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Uložit dokument
doc.save("path/to/your/document.docx");
```

### Zaškrtávací políčko formuláře

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložení pole formuláře se zaškrtávacím políčkem
builder.insertCheckBox("CheckBox", true, true, 0);

// Uložit dokument
doc.save("path/to/your/document.docx");
```

### Pole formuláře se seznamem

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definování položek pro pole se seznamem
String[] items = { "Option 1", "Option 2", "Option 3" };

// Vložení pole formuláře se seznamem
builder.insertComboBox("DropDown", items, 0);

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidání HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit HTML obsah
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidávání hypertextových odkazů

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit hypertextový odkaz
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", nepravdivé);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidání obsahu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit obsah
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Přidat obsah dokumentu
// ...

// Aktualizovat obsah
doc.updateFields();

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidávání obrázků

### Vložený obrázek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit vložený obrázek
builder.insertImage("path/to/your/image.png");

// Uložit dokument
doc.save("path/to/your/document.docx");
```

### Plovoucí obrázek

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit plovoucí obrázek
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Přidávání odstavců

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Nastavení formátování odstavce
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

// Vložit odstavec
builder.writeln("This is a formatted paragraph.");

// Uložit dokument
doc.save("path/to/your/document.docx");
```

## Krok 10: Pohyb kurzoru

Polohu kurzoru v dokumentu můžete ovládat různými způsoby, jako například `moveToParagraph`, `moveToCell`a další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Přesunutí kurzoru na konkrétní odstavec
builder.moveToParagraph(2, 0);

// Přidat obsah na novou pozici kurzoru
builder.writeln("This is the 3rd paragraph.");
```

Toto jsou některé běžné operace, které můžete provádět pomocí nástroje Aspose.Words pro tvorbu dokumentů v Javě. Prostudujte si dokumentaci ke knihovně, kde najdete další pokročilé funkce a možnosti přizpůsobení. Přejeme vám šťastné vytváření dokumentů!


## Závěr

V této komplexní příručce jsme prozkoumali možnosti nástroje DocumentBuilder v jazyce Java, který umožňuje přidávat různé typy obsahu do dokumentů Wordu. Probrali jsme text, tabulky, vodorovné linky, pole formulářů, HTML, hypertextové odkazy, obsah, obrázky, odstavce a pohyb kurzoru.

## Často kladené otázky

### Otázka: Co je Aspose.Words pro Javu?

A: Aspose.Words pro Javu je knihovna v Javě, která umožňuje vývojářům programově vytvářet, upravovat a manipulovat s dokumenty aplikace Microsoft Word. Nabízí širokou škálu funkcí pro generování dokumentů, formátování a vkládání obsahu.

### Otázka: Jak mohu do dokumentu přidat obsah?

A: Chcete-li přidat obsah, použijte `DocumentBuilder` vložit do dokumentu pole s obsahem. Po přidání obsahu nezapomeňte aktualizovat pole v dokumentu, aby se obsah naplnil. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit pole s obsahem
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Přidat obsah dokumentu
// ...

// Aktualizovat obsah
doc.updateFields();
```

### Otázka: Jak vložím obrázky do dokumentu pomocí Aspose.Words pro Javu?

A: Obrázky můžete vkládat, a to jak přímo v textu, tak i plovoucí, pomocí `DocumentBuilder`Zde jsou příklady obou:

#### Vložený obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit vložený obrázek
builder.insertImage("path/to/your/image.png");
```

#### Plovoucí obrázek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit plovoucí obrázek
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Otázka: Mohu formátovat text a odstavce při přidávání obsahu?

A: Ano, text a odstavce můžete formátovat pomocí `DocumentBuilder`Můžete nastavit vlastnosti písma, zarovnání odstavce, odsazení a další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Nastavení formátování písma a odstavce
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

// Vložení formátovaného odstavce
builder.writeln("This is a formatted paragraph.");
```

### Otázka: Jak mohu přesunout kurzor na určité místo v dokumentu?

A: Polohu kurzoru můžete ovládat pomocí metod, jako je `moveToParagraph`, `moveToCell`a další. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Přesunutí kurzoru na konkrétní odstavec
builder.moveToParagraph(2, 0);

// Přidat obsah na novou pozici kurzoru
builder.writeln("This is the 3rd paragraph.");
```

Zde jsou některé běžné otázky a odpovědi, které vám pomohou začít s Aspose.Words pro Java DocumentBuilder. Pokud máte další otázky nebo potřebujete další pomoc, podívejte se na [dokumentace knihovny](https://reference.aspose.com/words/java/) nebo vyhledejte pomoc od komunity a podpůrných zdrojů Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}