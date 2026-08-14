---
category: general
date: 2026-08-14
description: Utwórz przycisk ActiveX w formacie docx w Javie przy użyciu Aspose.Words.
  Dowiedz się, jak programowo dodać przycisk formularza w Wordzie i zapisać dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: pl
lastmod: 2026-08-14
og_description: Utwórz przycisk ActiveX w pliku docx w Javie przy użyciu Aspose.Words.
  Ten przewodnik pokazuje, jak dodać przycisk formularza w Wordzie, skonfigurować
  go i zapisać plik.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Utwórz przycisk ActiveX docx w Javie – samouczek krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Utwórz przycisk ActiveX w docx w Javie – kompletny przewodnik programistyczny
url: /pl/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz przycisk ActiveX w docx w Javie – kompletny przewodnik programistyczny

Jeśli potrzebujesz **create docx ActiveX button** w Javie, ten przewodnik przeprowadzi Cię przez cały proces. Zobaczysz, jak dodać przycisk formularza w Wordzie, skonfigurować jego właściwości i wygenerować gotowy do użycia .docx file.

Praca z kontrolkami ActiveX jest powszechnym wymogiem przy automatyzacji starszych formularzy Word. W tym samouczku nauczysz się **add form button word** dokumentów przy użyciu biblioteki Aspose.Words for Java, aby móc osadzać interaktywne kontrolki bez ręcznej edycji.

## Czego będziesz potrzebować

* Java 17 lub nowszy (kod kompiluje się także w starszych wersjach, ale zalecany jest Java 17).
* Aspose.Words for Java 23.10 lub nowszy – pobierz plik JAR ze strony Aspose lub dodaj zależność Maven.
* IDE (IntelliJ IDEA, Eclipse lub VS Code) lub prosty edytor tekstu i narzędzia do budowania w wierszu poleceń.
* Podstawowa znajomość składni Java oraz programowania obiektowego.

## Jak utworzyć przycisk ActiveX w docx przy użyciu Aspose.Words

Poniższe kroki pokazują dokładną kolejność niezbędną do **create docx ActiveX button** obiektów i osadzenia ich w dokumencie Word.

### Krok 1: Skonfiguruj projekt i zaimportuj Aspose.Words

Dodaj zależność Aspose.Words do swojego `pom.xml`, jeśli używasz Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Albo, jeśli wolisz Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Po rozwiązaniu zależności, zaimportuj wymagane klasy w swoim pliku źródłowym Java:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Te importy dają dostęp do `Document`, `DocumentBuilder` oraz API `Forms2OleControl` używanego do wstawiania kontrolek ActiveX.

### Krok 2: Utwórz nowy pusty dokument

Zainicjuj obiekt `Document`, który reprezentuje pusty plik Word gotowy do przyjęcia treści.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Utworzenie dokumentu najpierw zapewnia, że kolejny builder działa na czystym płótnie.

### Krok 3: Zainicjalizuj DocumentBuilder

`DocumentBuilder` zapewnia płynny interfejs do wstawiania tekstu, obrazów i kontrolek. Podłącz go do dokumentu, który właśnie utworzyłeś.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder śledzi bieżącą pozycję kursora w dokumencie, więc następne wstawienie odbywa się dokładnie tam, gdzie tego potrzebujesz.

### Krok 4: Wstaw kontrolkę ActiveX CommandButton

Użyj metody `insertForms2OleControl`, aby osadzić ActiveX `CommandButton`. Metoda ta zwraca instancję `Forms2OleControl`, którą możesz dalej konfigurować.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

W tym momencie plik .docx zawiera miejsce na przycisk, ale nie ma jeszcze widocznego napisu ani rozmiaru.

### Krok 5: Skonfiguruj właściwości przycisku

Ustaw nazwę kontrolki, napis oraz atrybuty układu. Te wartości określają, jak przycisk wygląda w Wordzie i jak możesz się do niego odwołać później za pomocą VBA lub skryptów automatyzacji.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** Word mierzy pozycje w punktach (1 pt ≈ 1/72 in). Dostosuj `setTop` i `setLeft`, aby wyrównać przycisk względem otaczającej treści.

### Krok 6: Zapisz dokument

Na koniec zapisz dokument na dysku. Użyj rozszerzenia `.docx`, aby zachować plik w nowoczesnym formacie Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Gdy otworzysz powstały plik w Microsoft Word, zobaczysz przycisk **Submit** umieszczony w określonych współrzędnych. Kliknięcie przycisku w Wordzie nie wywoła żadnej akcji, chyba że dołączysz kod VBA, ale kontrolka jest w pełni funkcjonalna w przepływach pracy opartych na formularzach.

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| **Czy potrzebuję specjalnej wersji Word?** | Kontrolki ActiveX są obsługiwane w wersji desktopowej Microsoft Word na systemie Windows. Nie są dostępne w Wordzie dla Mac ani w Word Online. |
| **Czy mogę używać tego z plikami `.doc`?** | Tak. Zapisz dokument z rozszerzeniem `.doc` (`document.save("ActiveXButton.doc")`). To samo API działa dla starszego formatu binarnego. |
| **Co zrobić, gdy przycisk się nie wyświetla?** | Upewnij się, że **Plik → Opcje → Centrum zaufania → Ustawienia Centrum zaufania → Ustawienia ActiveX** zezwalają na kontrolki ActiveX. Sprawdź także, czy dokument nie jest otwarty w trybie „Chroniony podgląd”. |
| **Czy mogę dodać inne kontrolki ActiveX?** | Oczywiście. Zastąp `Forms2OleControlType.COMMAND_BUTTON` na `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` itp. |
| **Czy istnieje limit rozmiaru?** | Rozmiar kontrolki jest ograniczony jedynie przez układ strony. Bardzo duże wymiary mogą powodować przepełnienie układu. |

## Pełny, działający przykład

Poniżej znajduje się pełna klasa Java, którą możesz skopiować, skompilować i uruchomić. Zawiera wszystkie importy, metodę main oraz komentarze w kodzie dla przejrzystości.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Oczekiwany rezultat:** Po uruchomieniu programu plik `ActiveXButton.docx` pojawi się w katalogu roboczym. Otworzenie go w Microsoft Word pokaże klikalny przycisk **Submit** umieszczony w pobliżu lewego górnego rogu pierwszej strony.

## Zakończenie

Teraz wiesz, jak **create docx ActiveX button** obiekty w Javie przy użyciu Aspose.Words i zobaczyłeś, jak **add form button word** dokumenty programowo. Kroki — konfiguracja projektu, tworzenie dokumentu, wstawianie kontrolki, konfigurowanie jej właściwości i zapisywanie — obejmują cały przepływ pracy od początku do końca.

Następnie możesz zbadać:

* Dodawanie makr VBA, które reagują na kliknięcie przycisku.
* Osadzanie innych kontrolek ActiveX, takich jak pola wyboru czy listy.
* Automatyzację generowania wielostronicowych formularzy z wieloma interaktywnymi elementami.

Śmiało eksperymentuj z rozmiarami, pozycjami i napisami, aby dopasować je do konkretnych wymagań projektowych formularza. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularza i dodawać treść przy użyciu DocumentBuilder w Aspose.Words dla Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak wczytać HTML i zapisać jako DOCX przy użyciu Aspose.Words dla Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Jak tworzyć dokumenty PDF przy użyciu Aspose.Words dla Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}