---
category: general
date: 2026-11-22
description: Utwórz przycisk makra w dokumencie Word przy użyciu Javy. Dowiedz się,
  jak wstawić przycisk polecenia, ustawić tekst przycisku i połączyć makro z przyciskiem
  w celu tworzenia interaktywnych dokumentów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: pl
lastmod: 2026-11-22
og_description: Utwórz przycisk makra w dokumencie Word przy użyciu Javy. Ten samouczek
  pokazuje, jak wstawić przycisk polecenia, ustawić tekst przycisku oraz połączyć
  makro z przyciskiem, aby uzyskać pełną interaktywność.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Utwórz przycisk makra w dokumencie Word przy użyciu Javy – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Jak utworzyć przycisk makra w dokumencie Word przy użyciu Aspose.Words dla
  Javy
url: /pl/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć przycisk makra w dokumencie Word przy użyciu Aspose.Words dla Javy

Jeśli potrzebujesz **utworzyć przycisk makra** w pliku Word, ten przewodnik przeprowadzi Cię przez dokładne wymagane kroki. Nauczysz się **wstawiać przycisk polecenia**, **ustawiać tekst przycisku** oraz **powiązać makro z przyciskiem**, aby dokument stał się w pełni interaktywny.

Programiści często osadzają kontrolki OLE, aby wywoływać makra VBA z poziomu dokumentu. Ten tutorial obejmuje kompletny przepływ pracy, od konfiguracji projektu po działający przykład w Javie, który dodaje **interaktywny przycisk** do pliku .docx. Nie są potrzebne zewnętrzne skrypty — wszystko działa wewnątrz procesu Java.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* JDK 17 lub nowszy zainstalowany.
* Maven 3.8+ (lub Gradle) do zarządzania zależnościami.
* Aspose.Words for Java 23.9 lub nowszy — biblioteka udostępnia `DocumentBuilder` i API kontroli OLE.
* Podstawowa znajomość Javy i makr VBA.

Jeśli którykolwiek z tych elementów jest brakujący, najpierw go zainstaluj; reszta tutorialu zakłada, że są dostępne.

## Jak utworzyć przycisk makra przy użyciu Aspose.Words dla Javy

Rdzeń rozwiązania składa się z czterech działań:

1. **Wstaw przycisk polecenia** kontrolkę OLE do dokumentu.
2. **Ustaw tekst przycisku** (caption), który widzi użytkownik.
3. **Powiąż makro z przyciskiem**, aby kliknięcie uruchamiało żądaną procedurę VBA.
4. **Zapisz dokument** z osadzonym makrem.

Każde działanie jest wyjaśnione w osobnej sekcji poniżej.

### Krok 1: Wstaw przycisk polecenia do dokumentu

`DocumentBuilder.insertForms2OleControl` tworzy kontrolkę OLE określonego typu. Stała `Forms2OleControlType.COMMAND_BUTTON` informuje Aspose.Words, aby wygenerował przycisk polecenia, który może hostować makro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Dlaczego to jest ważne:** Kontrolka OLE działa jako kontener dla makra. Bez jej wstawienia nie ma elementu wizualnego, który użytkownik mógłby kliknąć.

### Krok 2: Ustaw tekst przycisku (caption)

Caption to widoczna etykieta przycisku. Użyj `setCaption`, aby określić, co widzi użytkownik.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Dlaczego to jest ważne:** Czytelny tekst przycisku zwiększa użyteczność. Metoda `setCaption` aktualizuje właściwość `Caption` kontrolki OLE, którą Word wyświetla jako etykietę przycisku.

### Krok 3: Powiąż makro z przyciskiem

Makro jest identyfikowane po nazwie, np. `MyMacro`. Metoda `setOnClick` zapisuje tę nazwę w obsłudze zdarzenia `OnClick` przycisku.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Dlaczego to jest ważne:** Powiązanie makra tworzy interaktywne zachowanie. Gdy użytkownik kliknie przycisk w Wordzie, uruchamiana jest powiązana procedura VBA.

### Krok 4: Dodaj interaktywny przycisk do dokumentu Word

Po skonfigurowaniu kontrolki OLE możesz chcieć ją pozycjonować, zmienić rozmiar lub dodać otaczający tekst. `DocumentBuilder` nadal działa na dokumencie, więc możesz wstawiać akapity przed lub po przycisku.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Dlaczego to jest ważne:** Zapisanie jako `.docm` zachowuje kod makra. Jeśli zapiszesz jako `.docx`, odwołanie do makra zostanie utracone.

## Pełny działający przykład

Poniżej znajduje się kompletny program w Javie, wraz z importami, obsługą wyjątków i komentarzami wyjaśniającymi każdy krok. Skopiuj kod do projektu Maven z zależnością Aspose.Words i uruchom go.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Oczekiwany wynik

Uruchomienie programu generuje `MacroButtonDemo.docm`. Otwarcie pliku w Microsoft Word pokazuje:

* Akapit, który zawiera tekst *„Press the button to execute the macro:”*.
* Przycisk oznaczony **Run Report** bezpośrednio pod akapitem.
* Po kliknięciu przycisku Word próbuje uruchomić makro `MyMacro`. (Musisz dodać rzeczywisty kod VBA do dokumentu ręcznie lub za pomocą innego kroku automatyzacji.)

Jeśli makro nie istnieje, Word wyświetli ostrzeżenie bezpieczeństwa, co jest standardowym zachowaniem dla dokumentów z włączonymi makrami.

## Typowe warianty i przypadki brzegowe

| Scenariusz | Jak dostosować kod |
|------------|--------------------|
| **Different button caption** | Zmień łańcuch przekazywany do `setCaption`. |
| **Multiple buttons** | Wywołaj `insertForms2OleControl` wielokrotnie, każdy z własnym `setCaption` i `setOnClick`. |
| **Custom macro names** | Zamień `"MyMacro"` na dowolną prawidłową nazwę procedury VBA, np. `"ExportToExcel"`. |
| **Button size constraints** | Dostosuj wartości `setWidth` i `setHeight`; Word respektuje podane punkty. |
| **Embedding the macro programmatically** | Użyj `Document.getBuiltInDocumentProperties().add("Macros", …)` lub oddzielnego kroku wstrzykiwania VBA; Aspose.Words nie zapisuje kodu VBA samodzielnie. |

**Wskazówka:** Zawsze testuj wygenerowany `.docm` na maszynie z ustawieniem zabezpieczeń makr na *Włącz wszystkie makra* podczas rozwoju. W produkcji podpisz makro zaufanym certyfikatem, aby uniknąć komunikatów bezpieczeństwa.

## Lista kontrolna rozwiązywania problemów

* **Button does not appear** – Sprawdź, czy dokument jest zapisany jako `.docm` i otwarty w wersji Worda obsługującej kontrolki OLE.
* **Macro does not run** – Upewnij się, że nazwa makra jest dokładnie taka sama, łącznie z wielkością liter, oraz że makro istnieje w projekcie VBA dokumentu.
* **Button caption is truncated** – Zwiększ szerokość przycisku używając `setWidth`, aby pomieścić dłuższy tekst.
* **Unexpected layout shift** – Użyj `builder.moveTo`, aby precyzyjnie ustawić kursor przed wstawieniem kontrolki.

## Zakończenie

Teraz wiesz, jak **utworzyć przycisk makra** w dokumencie Word przy użyciu Javy, **wstawić przycisk polecenia**, **ustawić tekst przycisku** oraz **powiązać makro z przyciskiem** dla pełnej interaktywności. Pełny przykład demonstruje każde wymagane wywołanie API, wyjaśnia, dlaczego każdy krok jest istotny, i dostarcza wskazówek dotyczących typowych wariantów.

Następnie możesz zbadać:

* **Dodaj interaktywny przycisk** do istniejących szablonów zamiast nowego dokumentu.
* **Programowo wstrzyknij kod VBA** używając Open XML SDK lub dodatkowego narzędzia automatyzacji.
* **Połącz wiele kontrolek OLE** (checkboxes, list boxes), aby zbudować rozbudowane formularze.

Eksperymentuj z różnymi etykietami, nazwami makr i rozmiarami przycisków, aby dopasować je do swojego konkretnego przypadku użycia. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}