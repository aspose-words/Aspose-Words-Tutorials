---
category: general
date: 2026-08-23
description: Dowiedz się, jak wstawić przycisk polecenia w dokumencie Word przy użyciu
  Javy i Aspose.Words. Ten przewodnik pokazuje, jak dodać kontrolkę formularza, ustawić
  nazwę przycisku i osadzić przycisk ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: pl
lastmod: 2026-08-23
og_description: Wstaw przycisk polecenia w dokumencie Word przy użyciu Javy. Postępuj
  zgodnie z tym przewodnikiem, aby dodać kontrolkę formularza, ustawić nazwę przycisku
  i osadzić przycisk ActiveX za pomocą Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Wstaw przycisk polecenia w Wordzie przy użyciu Javy – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Jak wstawić przycisk polecenia w dokumencie Word przy użyciu Javy
url: /pl/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić przycisk polecenia w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz **wstawić przycisk polecenia** do pliku Word, ten samouczek pokaże Ci kompletną rozwiązanie z Aspose.Words for Java. Zobaczysz, jak dodać kontrolkę formularza, skonfigurować jej etykietę i ustawić nazwę przycisku bez opuszczania IDE.

Poradnik obejmuje wszystko, co potrzebne, aby utworzyć plik `.docx` zawierający przycisk ActiveX gotowy do użycia w Microsoft Word. Nie wymaga dodatkowych narzędzi, a przykład działa na Java 8+.

## Czego się nauczysz

* Jak dodać kontrolkę formularza typu **CommandButton** do dokumentu Word.  
* Dokładne kroki, aby **ustawić nazwę przycisku** i **dodać właściwości przycisku activex**.  
* Jak zapisać dokument, aby przycisk wyświetlał się poprawnie po otwarciu w Wordzie.  

Powinieneś mieć podstawowe środowisko programistyczne Java oraz projekt Maven lub Gradle, który może zaimportować bibliotekę Aspose.Words.

## Wymagania wstępne

| Wymaganie | Powód |
|-------------|--------|
| Java 8 lub nowszy | Aspose.Words for Java działa na Java 8+. |
| Maven lub Gradle | Ułatwia dodanie zależności Aspose.Words. |
| Licencja Aspose.Words for Java (lub wersja próbna) | Wymagana do pełnego zestawu funkcji; API działa w trybie ewaluacyjnym. |
| IDE, takie jak IntelliJ IDEA lub Eclipse | Ułatwia edycję i uruchamianie przykładu. |

## Krok 1: Dodaj Aspose.Words do swojego projektu

Jeśli używasz Maven, dodaj następującą zależność do `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Dla Gradle, umieść tę linię w `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Po rozwiązaniu zależności możesz importować klasy biblioteki w swoim pliku źródłowym Java.

## Krok 2: Wstaw przycisk polecenia – kod podstawowy

Utwórz nową klasę Java o nazwie `InsertCommandButtonDemo`. Poniższy kod wykonuje wszystkie cztery akcje wymagane do **wstawienia przycisku polecenia**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Dlaczego każda linia ma znaczenie

* **Document & DocumentBuilder** – Dostarczają reprezentację pliku Word w pamięci oraz API do modyfikacji jego zawartości.  
* **insertForms2OleControl** – Ta metoda **dodaje kontrolkę formularza** typu `COMMAND_BUTTON`. Zwrócony obiekt `Forms2OleControl` reprezentuje kontrolkę ActiveX.  
* **setName** – Przypisuje programowy identyfikator (`btnSubmit`). Makra Word lub VBA mogą odwoływać się do tej nazwy później.  
* **setCaption** – Definiuje tekst widoczny na przycisku, odpowiadając na pytanie „jak dodać przycisk”.  
* **save** – Zapisuje `.docx` na dysk, zachowując osadzony przycisk ActiveX.  

Uruchomienie programu tworzy `CommandButtonDemo.docx` w katalogu roboczym. Otwarcie pliku w Microsoft Word wyświetla przycisk oznaczony **Submit**, który można kliknąć (wyświetli domyślny dialog ActiveX w trybie ewaluacyjnym).

## Krok 3: Zweryfikuj wstawiony przycisk w Wordzie

1. Otwórz `CommandButtonDemo.docx` w Microsoft Word (2016 lub nowszy).  
2. Przycisk **Submit** pojawia się w miejscu, w którym kursor był ustawiony podczas wstawiania.  
3. Kliknij prawym przyciskiem myszy przycisk i wybierz **Properties**, aby zobaczyć, że pole **Name** zawiera `btnSubmit`.  

Jeśli przycisk się nie pojawia, upewnij się, że **kontrolki ActiveX** są włączone w ustawieniach Trust Center w Wordzie.

## Krok 4: Dostosowywanie przycisku (opcjonalnie)

Możesz dodatkowo dostosować przycisk, zmieniając jego rozmiar, pozycję lub dodając makro VBA. Klasa `Forms2OleControl` udostępnia dodatkowe właściwości, takie jak `setWidth`, `setHeight` i `setLeft`. Poniżej przykład, który powiększa przycisk:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Te linie można umieścić po wywołaniu `setCaption`. Demonstrują one dostosowanie **add activex button** wykraczające poza podstawowe wstawienie.

## Typowe pułapki i jak ich uniknąć

| Objaw | Przyczyna | Rozwiązanie |
|---------|-------|-----|
| Przycisk nie pojawia się w Wordzie | Dokument zapisano przed dodaniem kontrolki | Upewnij się, że `insertForms2OleControl` jest wywoływany przed `doc.save`. |
| Etykieta przycisku jest pusta | `setCaption` nie został wywołany lub wywołany z pustym ciągiem | Podaj niepusty ciąg, np. `"Submit"`. |
| VBA nie może znaleźć przycisku | Niezgodność nazw między kodem VBA a wartością `setName` | Zachowaj spójność nazw; użyj `setName("btnSubmit")` i odwołuj się do `btnSubmit` w VBA. |
| Ostrzeżenie bezpieczeństwa przy otwieraniu pliku | Zabezpieczenia makr w Wordzie blokują kontrolki ActiveX | Dostosuj Trust Center > Macro Settings lub podpisz dokument zaufanym certyfikatem. |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny plik źródłowy, gotowy do skopiowania i wklejenia do IDE. Zawiera instrukcje importu, obsługę wyjątków oraz blok komentarzy wyjaśniający każdy główny krok.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Oczekiwany rezultat:** Po uruchomieniu programu, `CommandButtonDemo.docx` zawiera pojedynczy przycisk **Submit**. Otwarcie pliku w Wordzie pokazuje przycisk dokładnie w miejscu, w którym znajdował się kursor `DocumentBuilder`.

## Kolejne kroki

* **Dodaj więcej kontrolek formularza** – Użyj `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` lub `TEXT_BOX`, aby zbudować pełne formularze Word.  
* **Połącz z korespondencją seryjną** – Wstaw przyciski do dokumentu połączonego w korespondencji seryjnej, aby tworzyć spersonalizowane interaktywne formularze.  
* **Dołącz makra VBA** – Programowo osadź VBA reagujące na zdarzenie `Click` przycisku w celu zaawansowanej automatyzacji.  

Te tematy naturalnie rozszerzają technikę **add form control**, którą właśnie opanowałeś.

### Podsumowanie

Teraz wiesz, jak **wstawić przycisk polecenia** do dokumentu Word przy użyciu Javy, jak **dodać kontrolkę formularza**, jak **ustawić nazwę przycisku** oraz jak **dodać dostosowania przycisku activex**. Pełny przykład działa od razu, a Ty możesz go dostosować do dowolnego przepływu generowania dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularza i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wstaw pole formularza Combo Box w dokumencie Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Wstaw pole formularza Check Box w dokumencie Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}