---
date: 2026-01-01
description: Naucz się tworzyć pola formularza oraz dodawać tekst, tabele, obrazy,
  hiperłącza i wiele więcej przy użyciu Aspose.Words for Java DocumentBuilder. Przewodnik
  krok po kroku dla programistów.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Jak tworzyć pola formularza i dodawać treść przy użyciu DocumentBuilder w Aspose.Words
  dla Javy
url: /pl/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodawanie treści przy użyciu DocumentBuilder w Aspose.Words dla Javy

## Wprowadzenie do dodawania treści przy użyciu DocumentBuilder w Aspose.Words dla Javy

W tym przewodniku krok po kroku **utworzysz pola formularza** oraz dodasz różnorodne treści — tekst, tabele, poziome linie, HTML, hiperłącza, obrazy i wiele innych — do dokumentu Word przy użyciu Aspose.Words dla Javy. Niezależnie od tego, czy tworzysz raport, szablon umowy, czy interaktywny formularz, klasa `DocumentBuilder` daje precyzyjną kontrolę nad każdym elementem. Zanurzmy się!

## Szybkie odpowiedzi
- **Jak utworzyć pola formularza?** Użyj `insertTextInput`, `insertCheckBox` lub `insertComboBox` na obiekcie `DocumentBuilder`.
- **Która metoda dodaje zwykły tekst?** Wywołaj `builder.write("Your text")` lub `builder.writeln("Your text")`.
- **Czy mogę wstawić poziomą linię?** Tak — `builder.insertHorizontalRule()` dodaje separator w postaci linii.
- **Jak osadzić HTML?** Użyj `builder.insertHtml("<p>HTML content</p>")`.
- **Jak dodać obraz w linii tekstu?** `builder.insertImage("path/to/image.png")` umieszcza obraz w przepływie tekstu.

## Co to jest DocumentBuilder i dlaczego używać go do tworzenia pól formularza?

`DocumentBuilder` to płynne API Aspose.Words do programowego konstruowania i edytowania dokumentów Word. Abstrahuje niskopoziomową strukturę OpenXML, pozwalając skupić się na *tym*, co chcesz dodać — na przykład **pola formularza** — zamiast na *tym*, jak wygląda XML. Dzięki temu jest idealny do generowania dynamicznych formularzy, umów lub dowolnych dokumentów wymagających interakcji użytkownika.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że biblioteka Aspose.Words dla Javy jest zainstalowana w Twoim projekcie. Możesz ją pobrać [tutaj](https://releases.aspose.com/words/java/).

## Dodawanie tekstu (jak dodać tekst)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Dodawanie tabel

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

## Dodawanie poziomej linii (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Dodawanie pól formularza (create form fields)

### Pole formularza typu tekstowego

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Pole formularza typu pole wyboru

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Pole formularza typu lista rozwijana

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

## Dodawanie HTML (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Dodawanie hiperłączy (how to add hyperlink)

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

## Dodawanie spisu treści

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

## Dodawanie obrazów

### Obraz w linii (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Obraz pływający

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Dodawanie akapitów

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

## Przemieszczanie kursora (Step 10)

Możesz kontrolować pozycję kursora w dokumencie za pomocą metod takich jak `moveToParagraph`, `moveToCell` itp.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

To niektóre z typowych operacji, które możesz wykonać przy użyciu `DocumentBuilder` w Aspose.Words dla Javy. Zapoznaj się z dokumentacją biblioteki, aby poznać bardziej zaawansowane funkcje i możliwości dostosowywania. Powodzenia w tworzeniu dokumentów!

## Zakończenie

W tym obszernej przewodniku pokazaliśmy, jak **tworzyć pola formularza** oraz dodawać różne typy treści — tekst, tabele, poziome linie, HTML, hiperłącza, spis treści, obrazy, formatowane akapity i nawigację kursora — przy użyciu `DocumentBuilder` w Aspose.Words dla Javy. Masz teraz solidne podstawy do programowego generowania dynamicznych, interaktywnych dokumentów Word.

## FAQ

### P: Co to jest Aspose.Words dla Javy?

O: Aspose.Words dla Javy to biblioteka Java umożliwiająca programistom tworzenie, modyfikowanie i manipulowanie dokumentami Microsoft Word w sposób programowy. Oferuje szeroki zakres funkcji związanych z generowaniem dokumentów, formatowaniem i wstawianiem treści.

### P: Jak dodać spis treści do mojego dokumentu?

O: Aby dodać spis treści, użyj `DocumentBuilder` do wstawienia pola TOC, a następnie wywołaj `doc.updateFields()` po dodaniu zawartości.

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

### P: Jak wstawić obrazy do dokumentu przy użyciu Aspose.Words dla Javy?

O: Obrazy, zarówno w linii, jak i pływające, możesz wstawiać przy pomocy `DocumentBuilder`.

#### Obraz w linii:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Obraz pływający:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### P: Czy mogę formatować tekst i akapity przy dodawaniu treści?

O: Tak, możesz formatować tekst i akapity używając `DocumentBuilder`. Ustaw właściwości czcionki, wyrównanie akapitu, wcięcia i inne przed zapisaniem treści.

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

### P: Jak przenieść kursor do określonego miejsca w dokumencie?

O: Użyj metod takich jak `moveToParagraph`, `moveToCell` itp., aby ustawić kursor przed wstawieniem nowej treści.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Te odpowiedzi obejmują najczęstsze scenariusze pracy z `DocumentBuilder` w Aspose.Words dla Javy. Po więcej szczegółów odwołaj się do [dokumentacji biblioteki](https://reference.aspose.com/words/java/) lub dołącz do społeczności Aspose.Words, aby uzyskać wsparcie.

---

**Ostatnia aktualizacja:** 2026-01-01  
**Testowane z:** Aspose.Words dla Javy 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}