---
date: 2025-12-24
description: Dowiedz się, jak utworzyć plik tekstowy z dokumentów Word przy użyciu
  Aspose.Words for Java. Ten przewodnik pokazuje, jak konwertować Word na txt, używać
  wcięć tabulacji i zapisywać dokument Word jako txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Jak utworzyć plik tekstowy za pomocą Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć plik tekstowy za pomocą Aspose.Words for Java

## Wprowadzenie do zapisywania dokumentów jako plików tekstowych w Aspose.Words for Java

W tym samouczku dowiesz się, **jak utworzyć plik tekstowy** z dokumentu Word przy użyciu biblioteki Aspose.Words for Java. Niezależnie od tego, czy potrzebujesz **konwertować word na txt**, zautomatyzować generowanie raportów, czy po prostu wyodrębnić surowy tekst do dalszego przetwarzania, ten przewodnik poprowadzi Cię przez cały proces — od tworzenia dokumentu po precyzyjne dostosowanie opcji zapisu, takich jak **użycie wcięć tabulacji** lub dodanie znaków bidi. Zaczynajmy!

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do tworzenia dokumentu?** `Document` z Aspose.Words.  
- **Która opcja dodaje znaki bidi dla języków od prawej do lewej?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Jak wciąć elementy listy za pomocą tabulacji?** Ustaw `ListIndentation.Character` na `'\t'`.  
- **Czy potrzebna jest licencja do rozwoju?** Darmowa wersja próbna działa do testów; licencja jest wymagana w produkcji.  
- **Czy mogę zapisać plik pod własną nazwą i ścieżką?** Tak — przekaż pełną ścieżkę do `doc.save()`.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz spełnione następujące wymagania:

- Zainstalowany Java Development Kit (JDK).  
- Biblioteka Aspose.Words for Java zintegrowana z projektem. Możesz ją pobrać [tutaj](https://releases.aspose.com/words/java/).  
- Podstawowa znajomość programowania w Javie.

## Krok 1: Utworzenie dokumentu

Aby **zapisać word jako txt**, najpierw potrzebujemy instancji `Document`. Poniżej prosty fragment Java, który tworzy dokument i zapisuje kilka linii tekstu wielojęzycznego:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

W tym kodzie tworzymy nowy dokument, dodajemy tekst po angielsku, hebrajsku i arabsku oraz włączamy formatowanie od prawej do lewej dla akapitu hebrajskiego.

## Krok 2: Definiowanie opcji zapisu tekstu

Następnie konfigurujemy, w jaki sposób dokument zostanie zapisany jako plik tekstowy. Aspose.Words udostępnia klasę `TxtSaveOptions`, która pozwala kontrolować wszystko, od znaków bidi po wcięcia list.

### Przykład 1: Dodawanie znaków bidi (jak zapisać txt z prawidłowym wsparciem RTL)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Ustawienie `AddBidiMarks` na `true` zapewnia, że znaki od prawej do lewej są prawidłowo reprezentowane w wynikowym **pliku tekstowym**.

### Przykład 2: Użycie znaku tabulacji do wcięć list (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Tutaj instruujemy Aspose.Words, aby przed każdym poziomem listy dodał znak tabulacji (`'\t'`), co ułatwia czytelność wyjściowego tekstu.

## Krok 3: Zapis dokumentu jako tekst

Gdy opcje zapisu są gotowe, możesz zapisać dokument jako **plik tekstowy**:

```java
doc.save("output.txt", saveOptions);
```

Zastąp `"output.txt"` pełną ścieżką, w której chcesz przechowywać plik.

## Pełny kod źródłowy do zapisywania dokumentów jako plików tekstowych w Aspose.Words for Java

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Typowe problemy i rozwiązania

| Problem | Rozwiązanie |
|-------|----------|
| **Znaki bidi wyświetlają się jako nieczytelny tekst** | Upewnij się, że `setAddBidiMarks(true)` jest włączone i plik wyjściowy otwierany jest z kodowaniem UTF‑8. |
| **Wcięcia listy wyglądają niepoprawnie** | Sprawdź, czy `ListIndentation.Count` i `Character` są ustawione na pożądane wartości (tab `'\t'` lub spacja `' '` ). |
| **Plik nie został utworzony** | Zweryfikuj, czy ścieżka katalogu istnieje oraz czy aplikacja ma uprawnienia do zapisu. |

## Najczęściej zadawane pytania

### Jak dodać znaki bidi do wyjściowego tekstu?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Czy mogę dostosować znak wcięcia listy?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Czy Aspose.Words for Java nadaje się do obsługi tekstu wielojęzycznego?

Tak, Aspose.Words for Java obsługuje szeroką gamę języków i kodowań znaków, co czyni go idealnym do wyodrębniania i zapisywania treści wielojęzycznych jako plików tekstowych.

### Gdzie mogę znaleźć więcej dokumentacji i zasobów dla Aspose.Words for Java?

Kompletną dokumentację i zasoby znajdziesz na stronie dokumentacji Aspose.Words for Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Skąd mogę pobrać Aspose.Words for Java?

Bibliotekę możesz pobrać z oficjalnej strony: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Co zrobić, gdy potrzebuję **konwertować word na txt** w procesie wsadowym?

Umieść powyższy kod w pętli, która wczytuje każdy plik `.docx`, stosuje te same `TxtSaveOptions` i zapisuje go jako `.txt`. Pamiętaj o zwalnianiu zasobów poprzez usuwanie obiektów `Document` po każdej iteracji.

### Czy API obsługuje zapisywanie bezpośrednio do strumienia zamiast do pliku?

Tak, możesz przekazać `OutputStream` do `doc.save(outputStream, saveOptions)` w celu przetwarzania w pamięci lub integracji z usługami sieciowymi.

---

**Ostatnia aktualizacja:** 2025-12-24  
**Testowane z:** Aspose.Words for Java 24.12 (najnowsza)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}