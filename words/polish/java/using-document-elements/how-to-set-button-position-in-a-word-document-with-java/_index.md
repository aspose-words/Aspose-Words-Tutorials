---
category: general
date: 2026-09-24
description: Ustaw pozycję przycisku w dokumencie Word przy użyciu Javy i Aspose.Words.
  Dowiedz się, jak wstawić przycisk, dodać kontrolkę ActiveX i utworzyć dokument Word
  w stylu Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: pl
lastmod: 2026-09-24
og_description: Ustaw pozycję przycisku w dokumencie Word przy użyciu Javy. Ten przewodnik
  pokazuje, jak wstawić przycisk, dodać kontrolkę ActiveX oraz utworzyć dokument Word
  w Javie przy użyciu Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Ustaw pozycję przycisku w dokumencie Word przy użyciu Javy – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Jak ustawić pozycję przycisku w dokumencie Word w Javie
url: /pl/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić pozycję przycisku w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz **ustawić pozycję przycisku** w pliku Word, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Niezależnie od tego, czy tworzysz szablon wymagający interakcji użytkownika, czy automatyzujesz formularz, dowiesz się dokładnie **jak wstawić przycisk** przy użyciu Aspose.Words for Java i kontrolować jego położenie.

Tutorial obejmuje wszystko, co potrzebne do **dodania kontrolki ActiveX** do dokumentu Word, wyjaśnia, jak **dodać przycisk do Worda**, oraz demonstruje pełny proces **tworzenia dokumentu Word w Javie**. Nie są wymagane żadne zewnętrzne odwołania – po prostu skopiuj, uruchom i zweryfikuj wynik.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Java 17 (lub dowolny runtime Java 8+).
* Maven lub Gradle do zarządzania zależnościami.
* Licencję Aspose.Words for Java (darmowa wersja próbna wystarczy do oceny).
* Podstawową znajomość składni Javy.

> **Pro tip:** Trzymaj pliki JAR Aspose.Words w folderze `libs/` i dodaj je do classpathu projektu, aby uniknąć konfliktów wersji.

## Krok 1: Konfiguracja projektu Maven

Utwórz prosty projekt Maven (lub użyj Gradle) i dodaj zależność Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Uruchomienie `mvn clean compile` pobierze bibliotekę i przygotuje ścieżkę kompilacji.

## Krok 2: Utworzenie nowego dokumentu Word

Pierwszym działaniem jest **utworzenie dokumentu Word w stylu Java**. Inicjalizujesz obiekt `Document` oraz `DocumentBuilder`, które umożliwiają edycję pliku.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Klasa `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` zapewnia płynne API do wstawiania treści.

## Krok 3: Jak wstawić przycisk – dodanie kontrolki ActiveX

Aspose.Words udostępnia klasę `Forms2OleControl` do wstawiania starszych kontrolek ActiveX, takich jak `CommandButton`. Ten krok pokazuje dokładny sposób **jak wstawić przycisk** do dokumentu.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Metoda `insertForms2OleControl` zwraca instancję `Forms2OleControl`, którą możesz skonfigurować. To jest serce procesu **dodawania kontrolki ActiveX**.

## Krok 4: Ustawienie pozycji przycisku

Teraz faktycznie **ustawiamy pozycję przycisku**. Metody `setLeft` i `setTop` przyjmują wartości w punktach (1 pt = 1/72 in). Aby dopasować przycisk do typowych współrzędnych ekranu, możesz przeliczyć piksele na punkty (1 px ≈ 0,75 pt). W przykładzie umieszczamy przycisk 100 px od lewej krawędzi i 150 px od górnej krawędzi.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Ponieważ logika **ustawiania pozycji przycisku** jest tutaj zamknięta, możesz ponownie używać tych linii, kiedy potrzebujesz przesunąć kontrolkę. Dostosuj liczby do własnych wymagań układu.

## Krok 5: Definiowanie rozmiaru i podpisu

Przycisk bez etykiety jest mylący. Użyj `setWidth`, `setHeight` i `setCaption`, aby nadać mu widoczny wygląd.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Rozmiar również wyrażany jest w punktach, więc konwertujemy go z pikseli dla spójności.

## Krok 6: Zapisz dokument – zakończenie przepływu **tworzenia dokumentu Word w Javie**

Na koniec zapisz plik na dysku. Ścieżka może być bezwzględna lub względna względem katalogu głównego projektu.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Uruchomienie programu tworzy `CommandButtonDemo.docx` w folderze `output`. Otworzenie pliku w Microsoft Word pokazuje klikalny przycisk umieszczony dokładnie tam, gdzie go ustawiono.

### Oczekiwany wynik

* Plik `.docx` o nazwie **CommandButtonDemo.docx**.
* W dokumencie pojawia się **CommandButton** z etykietą „Click Me”, umieszczony 100 px od lewego marginesu i 150 px od górnego marginesu.
* Przycisk reaguje na kliknięcia po otwarciu dokumentu w Wordzie (wyświetli domyślną wiadomość ActiveX, chyba że podłączysz własny kod VBA).

## Krok 7: Typowe warianty i przypadki brzegowe

### Dodawanie wielu przycisków

Jeśli potrzebujesz **dodać przycisk do Worda** więcej niż raz, powtórz kroki 3‑5 z nową instancją `Forms2OleControl` za każdym razem. Pamiętaj, aby dostosować wartość `setTop`, aby przyciski się nie nakładały.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Praca bez licencji

Aspose.Words dodaje znak wodny, gdy jest używany bez licencji. W kodzie produkcyjnym zakup licencję i zastosuj ją na początku `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatybilność ze starszymi wersjami Office

Kontrolki ActiveX są obsługiwane w formacie `.doc` (Word 97‑2003). Aby utworzyć starszy plik, zmień format zapisu:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Pełny kod źródłowy (do uruchomienia)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Zapisz plik jako `src/main/java/CommandButtonDemo.java`, uruchom `mvn exec:java -Dexec.mainClass=CommandButtonDemo` i otwórz wygenerowany dokument, aby zobaczyć rezultat.

## Najczęściej zadawane pytania

**P: Czy to działa z OpenJDK?**  
O: Tak. Aspose.Words jest czystą Javą i działa na każdej implementacji JDK 8+, w tym OpenJDK.

**P: Czy mogę zmienić czcionkę lub kolor przycisku?**  
O: Wygląd przycisku ActiveX kontrolowany jest przez aplikację hosta (Word). Możesz podłączyć kod VBA, aby modyfikować właściwości w czasie wykonywania, ale statyczny wygląd jest ograniczony do domyślnego stylu.

**P: Co zrobić, jeśli muszę umieścić przycisk wewnątrz komórki tabeli?**  
O: Przesuń kursor `DocumentBuilder` do komórki przed wywołaniem `insertForms2OleControl`. Kontrolka odziedziczy układ komórki, a nadal możesz używać `setLeft`/`setTop` do drobnego dostrojenia.

## Podsumowanie

Teraz wiesz, jak **ustawić pozycję przycisku** w dokumencie Word przy użyciu Javy, jak **jak wstawić przycisk**, jak **dodać kontrolkę ActiveX** oraz jak **dodać przycisk do Worda**, stosując najlepsze praktyki przy **tworzeniu dokumentu Word w Javie**. Kompletny przykład demonstruje cały przepływ – od konfiguracji projektu po zapisany plik `.docx` zawierający działający CommandButton.

### Kolejne kroki

* Zbadaj inne wartości `Forms2OleControl.ControlType` (np. `CHECKBOX`, `TEXTBOX`), aby budować bardziej rozbudowane formularze.
* Połącz przycisk z makrami VBA, aby obsłużyć własne zdarzenia kliknięcia.
* Skorzystaj z funkcji scalania korespondencji Aspose.Words, aby generować spersonalizowane dokumenty już zawierające interaktywne kontrolki.

Miłego kodowania i udanej automatyzacji dokumentów Word przy użyciu Javy!


## Co powinieneś nauczyć się dalej?


Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}