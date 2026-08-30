---
category: general
date: 2026-07-29
description: 'samouczek Java: ustaw rozmiar przycisku – dowiedz się, jak wstawić przycisk
  polecenia ActiveX w dokumencie Word przy użyciu Java i Aspose.Words, a także jak
  ustawiać rozmiar i tworzyć pusty dokument.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: pl
lastmod: 2026-07-29
og_description: Przewodnik Java dotyczący ustawiania rozmiaru przycisku pokazuje,
  jak wstawić przycisk polecenia ActiveX w pliku Word przy użyciu Javy, dostosować
  jego rozmiar i zapisać dokument programowo.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Ustaw rozmiar przycisku Java – Dodaj przycisk ActiveX Command do Worda w
  Javie
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
title: Ustaw rozmiar przycisku w Javie – Wstaw przycisk ActiveX Command w Wordzie
url: /pl/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Wstaw przycisk ActiveX w Word

Zastanawiałeś się kiedyś **how to set button size java** podczas automatyzacji dokumentów Word? Być może tworzysz narzędzie raportujące, które potrzebuje klikalnego przycisku „Submit” bezpośrednio w pliku .docx. W tym samouczku przeprowadzimy Cię przez cały proces — tworzenie pustego dokumentu Word, wstawianie przycisku ActiveX oraz wyraźne ustawienie jego szerokości i wysokości — wszystko w Javie i Aspose.Words.

Odpowiemy także na nurtujące pytanie „how to insert activex”, które pojawia się u wielu programistów. Po zakończeniu będziesz mieć działający program, który generuje plik Word zawierający idealnie wymiarowany przycisk poleceń, gotowy do dalszej personalizacji.

---

## Czego będziesz potrzebować

- **Java Development Kit (JDK) 8 lub nowszy** – kod kompiluje się na dowolnym aktualnym JDK.
- **Aspose.Words for Java** (najnowsza wersja na lipiec 2026). Pobierz plik JAR ze [strony Aspose](https://products.aspose.com/words/java) lub za pomocą Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- IDE lub prosty edytor tekstu — IntelliJ IDEA, Eclipse lub VS Code będą wystarczające.
- Folder, w którym ma zostać zapisany wygenerowany **CommandButton.docx**.

To wszystko. Bez dodatkowych bibliotek Office interop, bez sztuczek COM, po prostu czysta Java.

## Implementacja krok po kroku

Podzielimy rozwiązanie na pięć logicznych kroków. Każdy krok ma dedykowany nagłówek H2; jeden z nich zawiera nasze **główne słowo kluczowe**, aby spełnić wymagania SEO.

### 1. Konfiguracja projektu i import Aspose.Words

Najpierw utwórz nowy projekt Maven (lub Gradle) i dodaj zależność Aspose.Words, jak pokazano powyżej. Następnie zaimportuj wymagane klasy w swoim pliku źródłowym Java:

```java
import com.aspose.words.*;
```

> **Porada:** Jeśli używasz IDE, pozwól mu automatycznie importować klasy. Oszczędza to wiele pisania i zapobiega literówkom.

### 2. java create blank word Document

Teraz naprawdę **java create blank word** dokument. To podstawa, na której później **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Obiekt `Document` reprezentuje cały plik Word w pamięci. W tym momencie plik nie ma stron, nie ma tekstu — tylko czysta karta.

### 3. Inicjalizacja DocumentBuilder i wstawienie kontrolki ActiveX

Klasa `DocumentBuilder` jest pomocnikiem, który pozwala dodawać treść, akapity, tabele i, tak, kontrolki ActiveX. Tutaj odpowiadamy na pytanie **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` jest opakowaniem Aspose wokół obiektu OLE. Poprzez określenie `COMMANDBUTTON` informujemy Word, aby osadził klasyczny przycisk ActiveX.

### 4. How to Set Button Size Java – Dostosowanie szerokości i wysokości

Teraz przychodzi sedno samouczka: **how to set button size java**. Kontrolka udostępnia kilka właściwości układu — `Left`, `Top`, `Width` i `Height`. Ustawienie ich bezpośrednio kontroluje wygląd przycisku na stronie.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Dlaczego te liczby? W Wordzie jeden punkt to 1/72 cala. Szerokość `120` punktów przekłada się na około 1,67 cala — wystarczająco duża, aby etykieta była czytelna, a jednocześnie nie przytłaczająca. Dostosuj wartości do swojego układu; te same właściwości odpowiadają również na pytanie **how to set button**, które możesz mieć.

> **Uwaga:** Jeśli potrzebujesz innego typu przycisku (np. pola wyboru), zamień `Forms2OleControlType.COMMANDBUTTON` na odpowiednią wartość wyliczeniową.

### 5. Zapisz dokument

Na koniec zapisz dokument na dysku:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Zastąp `YOUR_DIRECTORY` pełną lub względną ścieżką na swoim komputerze. Po uruchomieniu programu otwórz wygenerowany plik w Microsoft Word. Zobaczysz przycisk oznaczony „Click Me”, umieszczony 100 pt od lewej i 200 pt od góry, o dokładnie ustawionych wymiarach.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia kod klasy Java. Skopiuj i wklej go do pliku `CommandButtonActiveX.java`, dostosuj ścieżkę wyjściową i naciśnij **Run**.

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

**Oczekiwany wynik:** Otwierając `CommandButton.docx` w Wordzie zobaczysz jedną stronę z klikalnym przyciskiem „Click Me” umieszczonym mniej więcej w połowie strony. Wymiary przycisku odpowiadają ustawionym wartościom, potwierdzając, że **set button size java** działa zgodnie z zamierzeniami.

---

## Częste pytania i przypadki brzegowe

### Co zrobić, gdy przycisk nie pojawia się w Wordzie?

- **Sprawdź wersję Worda.** Kontrolki ActiveX wymagają wersji desktopowej Worda; Word Online je usuwa.
- **Upewnij się, że licencja Aspose.Words jest zastosowana** (jeśli używasz płatnej edycji). Nielicencjonowana wersja ewaluacyjna może dodać znak wodny, ale nadal wyświetla kontrolkę.

### Czy mogę zmienić czcionkę lub kolor przycisku?

Tak. Po wstawieniu kontrolki możesz uzyskać dostęp do jej podstawowego obiektu OLE i manipulować właściwościami VBA. To bardziej zaawansowany temat — sprawdź `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` aby uzyskać czerwony napis, na przykład.

### Jak obsłużyć zdarzenie kliknięcia przycisku?

Przyciski ActiveX wywołują zdarzenie VBA `Click`. Aby przycisk był funkcjonalny, musisz osadzić makro w tym samym dokumencie. Aspose.Words może dodać moduł makr za pomocą API `Document.getMacros()`, ale sam kod makra musi być napisany w VBA.

### A co z innymi typami przycisków?

Aspose.Words obsługuje wiele wartości `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` itd. Zamień stałą wyliczeniową w wywołaniu `insertForms2OleControl`, aby eksperymentować.

---

## Porady dla kodu gotowego do produkcji

1. **Używaj stałych dla wartości układu** — ułatwia przyszłe zmiany.
2. **Opakuj ścieżkę zapisu w obiekt `Path`** aby uniknąć separatorów specyficznych dla platformy.
3. **Zwolnij zasoby Document** (lub użyj try‑with‑resources), jeśli przetwarzasz wiele plików w pętli.
4. **Sprawdź folder wyjściowy** przed wywołaniem `save`, aby uniknąć `FileNotFoundException`.

---

## Podsumowanie

Właśnie nauczyłeś się **set button size java** poprzez stworzenie pustego pliku Word, wstawienie przycisku ActiveX oraz precyzyjne skonfigurowanie jego wymiarów — wszystko przy użyciu kilku linii kodu Java. To obejmuje rdzeń zagadnień **how to insert activex**, **how to set button**, **java create blank word** i **insert command button word** w jednym, samodzielnym przykładzie.

Co dalej? Spróbuj dostosować etykietę przycisku, dodać makro reagujące na kliknięcia lub osadzić wiele kontrolek na tej samej stronie. Możesz także zbadać konwersję wygenerowanego .docx do PDF przy użyciu Aspose.Words, zachowując przycisk jako statyczny obraz.

Śmiało eksperymentuj, a jeśli napotkasz problem, zostaw komentarz poniżej. Szczęśliwego kodowania!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularzy i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak ładować dokumenty Word przy użyciu Aspose.Words Java: Kompletny przewodnik](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Jak zapisać dokument jako PDF przy użyciu Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}