---
title: Zapisywanie dokumentów jako plików tekstowych w Aspose.Words dla Java
linktitle: Zapisywanie dokumentów jako plików tekstowych
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak zapisywać dokumenty jako pliki tekstowe w Aspose.Words for Java. Postępuj zgodnie z naszym przewodnikiem krok po kroku z przykładami kodu Java.
weight: 24
url: /pl/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisywanie dokumentów jako plików tekstowych w Aspose.Words dla Java


## Wprowadzenie do zapisywania dokumentów jako plików tekstowych w Aspose.Words dla Java

W tym samouczku pokażemy, jak zapisywać dokumenty jako pliki tekstowe przy użyciu biblioteki Aspose.Words for Java. Aspose.Words to potężne API Java do pracy z dokumentami Word, które oferuje różne opcje zapisywania dokumentów w różnych formatach, w tym zwykłego tekstu. Omówimy kroki, aby to osiągnąć i podamy przykładowy kod Java.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

- Java Development Kit (JDK) zainstalowany w Twoim systemie.
-  Biblioteka Aspose.Words for Java zintegrowana z Twoim projektem. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/java/).
- Podstawowa znajomość programowania w Javie.

## Krok 1: Utwórz dokument

Aby zapisać dokument jako plik tekstowy, najpierw musimy utworzyć dokument za pomocą Aspose.Words. Oto prosty fragment kodu Java, aby utworzyć dokument z pewną zawartością:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

tym kodzie tworzymy nowy dokument i dodajemy do niego tekst, w tym tekst w różnych językach.

## Krok 2: Zdefiniuj opcje zapisywania tekstu

Następnie musimy zdefiniować opcje zapisywania tekstu, które określają, jak dokument powinien zostać zapisany jako plik tekstowy. Możemy skonfigurować różne ustawienia, takie jak dodawanie znaczników bidi, wcięcie listy i inne. Przyjrzyjmy się dwóm przykładom:

### Przykład 1: Dodawanie znaczników Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 W tym przykładzie tworzymy`TxtSaveOptions` obiekt i ustaw`AddBidiMarks`nieruchomość do`true` aby uwzględnić znaki bidi w tekście wyjściowym.

### Przykład 2: Używanie znaku tabulacji do wcięcia listy

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Tutaj konfigurujemy opcje zapisu, aby użyć znaku tabulacji do wcięcia listy o liczbie 1.

## Krok 3: Zapisz dokument jako tekst

Teraz, gdy zdefiniowaliśmy opcje zapisywania tekstu, możemy zapisać dokument jako plik tekstowy. Poniższy kod pokazuje, jak to zrobić:

```java
doc.save("output.txt", saveOptions);
```

 Zastępować`"output.txt"` z żądaną ścieżką dostępu, w której chcesz zapisać plik tekstowy.

## Kompletny kod źródłowy do zapisywania dokumentów jako plików tekstowych w Aspose.Words dla Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Utwórz listę z trzema poziomami wcięcia.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Utwórz listę z trzema poziomami wcięcia.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Wniosek

W tym samouczku nauczyliśmy się, jak zapisywać dokumenty jako pliki tekstowe w Aspose.Words dla Java. Omówiliśmy kroki tworzenia dokumentu, definiowania opcji zapisywania tekstu i zapisywania dokumentu w formacie tekstowym. Aspose.Words zapewnia dużą elastyczność, jeśli chodzi o zapisywanie dokumentów, umożliwiając dostosowanie wyników do konkretnych wymagań.

## Najczęściej zadawane pytania

### Jak dodać znaki bidi do tekstu wyjściowego?

 Aby dodać znaki bidi do tekstu wyjściowego, ustaw`AddBidiMarks` własność`TxtSaveOptions` Do`true`. Na przykład:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Czy mogę dostosować znak wcięcia listy?

 Tak, możesz dostosować znak wcięcia listy, konfigurując`ListIndentation` własność`TxtSaveOptions`Na przykład, aby użyć znaku tabulacji do wcięcia listy, możesz wykonać następujące czynności:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Czy Aspose.Words for Java nadaje się do obsługi tekstów wielojęzycznych?

Tak, Aspose.Words for Java nadaje się do obsługi tekstu wielojęzycznego. Obsługuje różne języki i kodowania znaków, co czyni go wszechstronnym wyborem do pracy z dokumentami w różnych językach.

### Jak mogę uzyskać dostęp do dodatkowej dokumentacji i zasobów dla Aspose.Words dla Java?

 Pełną dokumentację i zasoby dotyczące Aspose.Words for Java można znaleźć na stronie internetowej dokumentacji Aspose:[Aspose.Words dla dokumentacji Java](https://reference.aspose.com/words/java/).

### Gdzie mogę pobrać Aspose.Words dla Java?

 Bibliotekę Aspose.Words for Java można pobrać ze strony internetowej Aspose:[Pobierz Aspose.Words dla Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
