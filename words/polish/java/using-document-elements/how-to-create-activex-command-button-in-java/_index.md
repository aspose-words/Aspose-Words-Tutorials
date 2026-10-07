---
category: general
date: 2026-10-07
description: Utwórz przycisk ActiveX w Javie i programowo dodaj go do dokumentów Word.
  Dowiedz się, jak ustawić lewą górną pozycję przycisku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: pl
lastmod: 2026-10-07
og_description: Utwórz przycisk polecenia ActiveX w Javie, aby osadzać interaktywne
  kontrolki w dokumentach Word. Dowiedz się, jak programowo dodać przycisk polecenia,
  ustawić jego pozycję i dostosować jego wygląd.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Tworzenie przycisku polecenia ActiveX w Javie – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Jak utworzyć przycisk polecenia ActiveX w Javie
url: /pl/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć przycisk polecenia ActiveX w Javie

Jeśli potrzebujesz **utworzyć przycisk polecenia ActiveX** w dokumencie Word przy użyciu Javy, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, działający przykład, który **programowo dodaje przycisk polecenia**, pozycjonuje go za pomocą `setLeft` i `setTop`, oraz zapisuje wynik jako plik `.docx`.

Osadzenie interaktywnego przycisku pozwala tworzyć formularze, automatyzować przepływy pracy lub zbierać dane od użytkownika bezpośrednio w pliku Word. Poniższe kroki obejmują wszystko, od konfiguracji projektu po ostateczną weryfikację, więc możesz skopiować kod do własnego projektu bez pomijania żadnych szczegółów.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

- JDK 17 lub nowszy zainstalowany  
- Maven 3.8+ (lub wybrane narzędzie budowania)  
- Aspose.Words for Java 23.9 lub nowszy – biblioteka zapewniająca `DocumentBuilder` i obsługę kontrolki OLE  
- Podstawowa znajomość składni Javy i koncepcji programowania obiektowego  

Jeśli używasz Maven, dodaj zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Wskazówka:** Użyj najnowszej wersji Aspose.Words, aby skorzystać z poprawek błędów i nowych funkcji OLE.

## Krok 1: Utwórz nowy pusty dokument i DocumentBuilder

Pierwszy krok do **utworzenia przycisku polecenia ActiveX** polega na zainicjowaniu pustego `Document` oraz `DocumentBuilder`. Builder zapewnia płynne API do wstawiania treści, w tym kontrolek OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje plik Word w pamięci, natomiast `DocumentBuilder` działa jako kursor, który pozwala precyzyjnie umieszczać elementy w wybranym miejscu.

## Krok 2: Wstaw kontrolkę przycisku polecenia OLE

Kontrolki ActiveX są wstawiane jako obiekty OLE. Aspose.Words udostępnia klasę `Forms2OleControl` w tym celu.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Gdy wywołujesz `insertForms2OleControl()`, Aspose automatycznie tworzy kształt‑placeholder, który będzie hostował przycisk ActiveX.

## Krok 3: Skonfiguruj właściwości przycisku

Teraz **programowo dodajesz szczegóły przycisku polecenia**, takie jak jego ProgID, podpis i rozmiar. Najbardziej powszechny ProgID dla przycisku polecenia to `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Jak ustawić lewy górny przycisk

Pozycjonowanie przycisku to miejsce, w którym przydatne staje się drugie słowo kluczowe **how to set button left top**. Metody `setLeft` i `setTop` przyjmują wartości mierzone w punktach (1 punkt = 1/72 cala).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Dostosuj te liczby do swojego układu. Na przykład, aby wyrównać przycisk z komórką tabeli, oblicz współrzędne komórki i przekaż je do `setLeft`/`setTop`.

## Krok 4: Zapisz dokument

Na koniec zapisz dokument na dysku. Plik będzie zawierał przycisk ActiveX gotowy do interakcji po otwarciu w Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Uruchomienie metody `main` tworzy plik `CommandButton.docx`. Otwórz go w Wordzie, w razie potrzeby zezwól na zawartość i zobaczysz klikalny przycisk oznaczony **Click Me** umieszczony w określonych współrzędnych.

![Zrzut ekranu tworzenia przycisku ActiveX w Javie](/images/activex-button-screenshot.png){.center width=600 alt="Zrzut ekranu tworzenia przycisku ActiveX w Javie pokazujący przycisk w dokumencie Word"}

## Typowe warianty i przypadki brzegowe

### Dodawanie wielu przycisków

Jeśli potrzebujesz kilku przycisków, powtórz **Krok 2** i **Krok 3** dla każdej kontrolki. Pamiętaj, aby dostosować `setLeft` i `setTop`, aby przyciski się nie nakładały.

### Zmiana zachowania przycisku

Przyciski ActiveX mogą uruchamiać makra VBA po kliknięciu. Aby podłączyć makro, ustaw właściwość `setOnAction` na nazwę makra:

```java
commandButton.setOnAction("MyMacro");
```

Upewnij się, że docelowy dokument zawiera odpowiedni moduł VBA; w przeciwnym razie Word wyświetli błąd.

### Uwagi dotyczące kompatybilności

- Przycisk działa tylko w wersjach desktopowych Worda, które obsługują ActiveX (np. Word dla Windows). W Wordzie dla Mac lub edytorach online pojawi się jako statyczny obraz.  
- Jeśli celujesz w środowisko mieszane, rozważ użycie **kontrolki treści** (`RichTextContentControl`) zamiast kontrolki ActiveX.

## Pełny kod źródłowy jako odniesienie

Poniżej znajduje się kompletny, samodzielny przykład, który możesz skopiować do nowego projektu Maven i od razu uruchomić.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Oczekiwany wynik:** Po wykonaniu znajdziesz `CommandButton.docx` w katalogu roboczym projektu. Otworzenie pliku w Microsoft Word pokazuje przycisk w określonym miejscu z podpisem „Click Me”.

## Zakończenie

Teraz wiesz, jak **utworzyć przycisk polecenia ActiveX** w Javie, **programowo dodać przycisk polecenia** do dokumentu Word oraz precyzyjnie kontrolować jego układ za pomocą metod **how to set button left top**. Ta technika otwiera drzwi do bogatych, interaktywnych formularzy Word, które mogą wywoływać makra, uruchamiać zewnętrzne aplikacje lub zbierać dane od użytkownika bezpośrednio w dokumencie.

### Kolejne kroki

- Zbadaj inne kontrolki ActiveX, takie jak `Forms.TextBox.1` lub `Forms.CheckBox.1`.  
- Połącz wiele kontrolek z modułem VBA, aby stworzyć w pełni funkcjonalne formularze.  
- Zastąp ActiveX kontrolkami treści, jeśli potrzebna jest kompatybilność wieloplatformowa.  

Śmiało eksperymentuj z rozmiarem, podpisem i pozycjonowaniem, aby dopasować je do projektu UI. Jeśli napotkasz problemy, sprawdź dwukrotnie, czy używana wersja Aspose.Words obsługuje kontrolki OLE oraz czy ustawienia zabezpieczeń Worda zezwalają na wykonywanie ActiveX. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne, działające przykłady kodu wraz z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Osadzanie obiektów OLE i kontrolek ActiveX w dokumentach Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Jak tworzyć pola formularzy i dodawać treść przy użyciu DocumentBuilder w Aspose.Words dla Javy](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tworzenie prostokątnego kształtu w Wordzie przy użyciu Javy – pełny przewodnik](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}