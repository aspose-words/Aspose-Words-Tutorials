---
"description": "Tworzenie dokumentów głównych z Aspose.Words dla Java. Przewodnik krok po kroku po dodawaniu tekstu, tabel, obrazów i innych. Twórz oszałamiające dokumenty Word bez wysiłku."
"linktitle": "Dodawanie treści za pomocą DocumentBuilder"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Dodawanie zawartości za pomocą DocumentBuilder w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodawanie zawartości za pomocą DocumentBuilder w Aspose.Words dla Java


## Wprowadzenie do dodawania treści za pomocą DocumentBuilder w Aspose.Words dla Java

W tym przewodniku krok po kroku pokażemy, jak używać Aspose.Words for Java's DocumentBuilder do dodawania różnych typów treści do dokumentu Word. Omówimy wstawianie tekstu, tabel, poziomych linii, pól formularzy, HTML, hiperłączy, spisu treści, obrazów inline i float, akapitów i nie tylko. Zaczynajmy!

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że w swoim projekcie masz skonfigurowaną bibliotekę Aspose.Words for Java. Możesz ją pobrać ze strony [Tutaj](https://releases.aspose.com/words/java/).

## Dodawanie tekstu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw prosty akapit tekstowy
builder.write("This is a simple text paragraph.");

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie tabel

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Rozpocznij tabelę
Table table = builder.startTable();

// Wstaw komórki i zawartość
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Zakończ tabelę
builder.endTable();

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie linii poziomej

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw linię poziomą
builder.insertHorizontalRule();

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie pól formularza

### Pole formularza wprowadzania tekstu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw pole formularza wprowadzania tekstu
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

### Pole formularza pola wyboru

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw pole formularza z polem wyboru
builder.insertCheckBox("CheckBox", true, true, 0);

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

### Pole formularza Combo Box

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Zdefiniuj elementy dla pola kombi
String[] items = { "Option 1", "Option 2", "Option 3" };

// Wstaw pole formularza typu combo box
builder.insertComboBox("DropDown", items, 0);

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw zawartość HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie hiperłączy

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw hiperłącze
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", fałsz);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie spisu treści

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw spis treści
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dodaj zawartość dokumentu
// ...

// Zaktualizuj spis treści
doc.updateFields();

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie obrazów

### Obraz w tekście

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw obraz w tekście
builder.insertImage("path/to/your/image.png");

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

### Obraz pływający

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw obraz pływający
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Dodawanie akapitów

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ustaw formatowanie akapitu
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

// Wstaw akapit
builder.writeln("This is a formatted paragraph.");

// Zapisz dokument
doc.save("path/to/your/document.docx");
```

## Krok 10: Przesuwanie kursora

Możesz kontrolować położenie kursora w dokumencie, korzystając z różnych metod, takich jak: `moveToParagraph`, `moveToCell`i więcej. Oto przykład:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Przesuń kursor do określonego akapitu
builder.moveToParagraph(2, 0);

// Dodaj zawartość w nowej pozycji kursora
builder.writeln("This is the 3rd paragraph.");
```

Oto kilka typowych operacji, które możesz wykonać za pomocą Aspose.Words for Java's DocumentBuilder. Zapoznaj się z dokumentacją biblioteki, aby poznać bardziej zaawansowane funkcje i opcje dostosowywania. Miłego tworzenia dokumentów!


## Wniosek

W tym kompleksowym przewodniku zbadaliśmy możliwości Aspose.Words for Java's DocumentBuilder w zakresie dodawania różnych typów treści do dokumentów Word. Omówiliśmy tekst, tabele, linie poziome, pola formularzy, HTML, hiperłącza, spis treści, obrazy, akapity i ruch kursora.

## Najczęściej zadawane pytania

### P: Czym jest Aspose.Words dla języka Java?

A: Aspose.Words for Java to biblioteka Java, która umożliwia programistom programowe tworzenie, modyfikowanie i manipulowanie dokumentami Microsoft Word. Zapewnia szeroki zakres funkcji do generowania dokumentów, formatowania i wstawiania treści.

### P: Jak mogę dodać spis treści do mojego dokumentu?

A: Aby dodać spis treści, użyj `DocumentBuilder` aby wstawić pole spisu treści do dokumentu. Upewnij się, że zaktualizowałeś pola w dokumencie po dodaniu treści, aby wypełnić spis treści. Oto przykład:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw pole spisu treści
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dodaj zawartość dokumentu
// ...

// Zaktualizuj spis treści
doc.updateFields();
```

### P: Jak wstawiać obrazy do dokumentu za pomocą Aspose.Words dla Java?

A: Możesz wstawiać obrazy zarówno osadzone, jak i ruchome, używając `DocumentBuilder`Oto przykłady obu:

#### Obraz w tekście:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw obraz w tekście
builder.insertImage("path/to/your/image.png");
```

#### Obraz pływający:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw obraz pływający
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### P: Czy mogę formatować tekst i akapity podczas dodawania treści?

A: Tak, możesz formatować tekst i akapity za pomocą `DocumentBuilder`. Możesz ustawić właściwości czcionki, wyrównanie akapitu, wcięcie i więcej. Oto przykład:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ustaw czcionkę i formatowanie akapitu
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

// Wstaw sformatowany akapit
builder.writeln("This is a formatted paragraph.");
```

### P: Jak mogę przenieść kursor w określone miejsce w dokumencie?

A: Możesz kontrolować położenie kursora za pomocą takich metod jak `moveToParagraph`, `moveToCell`i więcej. Oto przykład:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Przesuń kursor do określonego akapitu
builder.moveToParagraph(2, 0);

// Dodaj zawartość w nowej pozycji kursora
builder.writeln("This is the 3rd paragraph.");
```

Oto kilka typowych pytań i odpowiedzi, które pomogą Ci rozpocząć pracę z Aspose.Words for Java's DocumentBuilder. Jeśli masz więcej pytań lub potrzebujesz dalszej pomocy, zapoznaj się z [dokumentacja biblioteki](https://reference.aspose.com/words/java/) lub zwróć się o pomoc do społeczności Aspose.Words i innych źródeł wsparcia.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}