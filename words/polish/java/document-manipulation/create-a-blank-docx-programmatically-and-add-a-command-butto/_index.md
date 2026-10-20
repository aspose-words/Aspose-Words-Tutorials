---
category: general
date: 2026-10-20
description: Utwórz pusty plik DOCX programowo i osadź przycisk polecenia przy użyciu
  Javy. Poznaj kompletny kod tworzenia dokumentu Word, aby zapisać plik z przyciskiem
  i ustawić jego etykietę.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: pl
lastmod: 2026-10-20
og_description: Utwórz pusty dokument DOCX programowo i osadź przycisk polecenia.
  Postępuj zgodnie z tym szczegółowym przewodnikiem w Javie, aby zapisać dokument
  Word z przyciskiem i ustawić podpis przycisku polecenia.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Utwórz pusty plik DOCX programowo – dodaj przycisk polecenia
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Utwórz pusty plik DOCX programowo i dodaj przycisk polecenia
url: /pl/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty plik DOCX programowo i dodaj przycisk poleceń

Jeśli potrzebujesz **utworzyć pusty plik DOCX programowo**, ten samouczek pokaże Ci, jak osadzić przycisk poleceń bezpośrednio w pliku. Otrzymasz kompletny *create word document code*, który zapisuje dokument Word z przyciskiem, pozwala **ustawić podpis przycisku poleceń** i działa z najnowszą biblioteką Aspose.Words for Java.

Osadzanie interaktywnych kontrolek w pliku DOCX jest przydatne, gdy chcesz dystrybuować szablony, które wywołują makra, uruchamiają zewnętrzne programy lub po prostu prowadzą użytkowników przyciskiem „Click Me”. Poniższe kroki obejmują wszystko, od inicjalizacji pustego dokumentu po zapisanie ostatecznego pliku na dysku.

## Wymagania wstępne

* Java 17 lub nowszy zainstalowany.  
* Maven (lub preferowane narzędzie budowania) do zarządzania zależnościami.  
* Aspose.Words for Java 23.9 lub nowszy. Dodaj zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* IDE, np. IntelliJ IDEA lub VS Code (dowolny edytor obsługujący Javę).

## Utwórz pusty plik DOCX programowo – krok po kroku

Poniższe sekcje dzielą proces na przejrzyste, numerowane kroki. Każdy krok wyjaśnia **dlaczego** jest potrzebny, a nie tylko **co** wpisać.

### Krok 1: Zainicjuj nowy pusty dokument

Pusty dokument jest płótnem, na którym umieścisz przycisk poleceń. Aspose.Words udostępnia klasę `Document` w tym celu.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Dlaczego to ważne*: Rozpoczęcie od pustego `Document` zapewnia, że żadne ukryte formatowanie ani istniejące kontrolki nie będą kolidować z przyciskiem, który dodasz później.

### Krok 2: Skonfiguruj `DocumentBuilder`

`DocumentBuilder` jest pomocnikiem, który pozwala wstawiać treść, w tym kontrolki OLE, bez konieczności manipulacji niskopoziomowymi węzłami.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne*: Builder utrzymuje bieżącą pozycję kursora, więc przycisk zostanie umieszczony dokładnie tam, gdzie określisz.

### Krok 3: Wstaw przycisk poleceń OLE

Word traktuje interaktywne kontrolki jako obiekty OLE (Object Linking and Embedding). Aspose.Words udostępnia `Forms2OleControl` w tym celu.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Dlaczego to ważne*: Wstawienie kontrolki tworzy miejsce, które możesz później skonfigurować (typ, podpis, pozycję).

### Krok 4: Skonfiguruj przycisk – typ, podpis i położenie

Musisz określić typ kontrolki (`COMMANDBUTTON`), ustawić widoczny dla użytkownika podpis i umieścić ją na stronie.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Dlaczego to ważne*:  
* **Type** informuje Word, że kontrolka zachowuje się jak przycisk, który można kliknąć.  
* **Caption** to tekst widoczny dla użytkownika; zmiana go to sposób, w jaki **set command button caption**.  
* **Left** i **Top** kontrolują dokładne położenie, co jest kluczowe, gdy **add command button word** dokumenty wymagają precyzyjnego układu.

### Krok 5: Zapisz dokument z osadzonym przyciskiem

Na koniec zapisz plik na dysku. Powstały plik można otworzyć w Microsoft Word, gdzie przycisk będzie w pełni funkcjonalny.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Dlaczego to ważne*: Ten krok **saves Word with button**, więc kontrolka zachowuje się na różnych maszynach. Plik może być dystrybuowany jako szablon lub używany w zautomatyzowanych pipeline'ach generowania raportów.

## Pełny działający przykład

Skopiuj całą klasę poniżej do pliku o nazwie `CommandButtonDemo.java`, dostosuj `YOUR_DIRECTORY` do rzeczywistej ścieżki i uruchom ją poleceniem `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Oczekiwany wynik

Po otwarciu `CommandButton.docx` w Microsoft Word:

* Dokument jest całkowicie pusty, oprócz przycisku oznaczonego **Click Me**.  
* Kliknięcie przycisku wyświetli domyślne zachowanie Worda (nie robi nic, chyba że dołączono makro), potwierdzając, że kontrolka OLE została poprawnie osadzona.

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| **Czy mogę zmienić rozmiar przycisku?** | Tak. Użyj `commandButton.setWidth(double)` i `commandButton.setHeight(double)`, aby dostosować wymiary w punktach. |
| **Co zrobić, jeśli potrzebuję makra dołączonego do przycisku?** | Sam przycisk jest jedynie kontrolką OLE. Musisz dodać makro VBA do dokumentu ręcznie lub przy użyciu narzędzi `addMacro` API `Document` Aspose.Words. |
| **Czy przycisk będzie działał w LibreOffice?** | LibreOffice obsługuje ograniczone kontrolki OLE. Przycisk jest widoczny, ale jego zachowanie po kliknięciu może się różnić. |
| **Jak dodać wiele przycisków?** | Powtórz kroki 3‑4 z nową instancją `Forms2OleControl`. Dostosuj `setLeft`/`setTop` dla każdego przycisku, aby uniknąć nakładania się. |
| **Czy kod jest kompatybilny z .NET?** | Ta sama logika ma zastosowanie, ale użyjesz klas `Aspose.Words` dla .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Porady z praktyki

* **Pro tip:** Użyj `builder.moveToDocumentEnd()` przed wstawieniem przycisku, jeśli chcesz, aby znajdował się na samym końcu dokumentu, niezależnie od wcześniejszej zawartości.  
* **Watch out for:** Bardzo małe wartości `Left`/`Top` mogą umieścić przycisk poza obszarem drukowania, czyniąc go niewidocznym w widoku układu Worda.  
* **Performance note:** Wstawianie wielu kontrolek OLE może zwiększyć rozmiar pliku. Jeśli potrzebujesz jedynie wskazówki wizualnej, rozważ użycie zwykłego `Shape` z hiperłączem.

## Zakończenie

Teraz wiesz, jak **create a blank DOCX programmatically** i osadzić w pełni funkcjonalny przycisk poleceń przy użyciu Javy. Samouczek omówił cały przepływ pracy *create word document code*, pokazał, jak **save Word with button**, przedstawił prawidłowy sposób **add command button word** elementów oraz wyjaśnił, jak **set command button caption**.

Od teraz możesz:

* Dodaj więcej kontrolek OLE (checkboxy, combo boxy) dla bardziej rozbudowanych formularzy.  
* Dołącz makra VBA, aby przycisk wykonywał niestandardowe akcje.  
* Połącz tę technikę z scalaniem korespondencji w dokumencie, aby uzyskać dynamiczne, interaktywne szablony.

Śmiało eksperymentuj ze stylami przycisków, pozycjami i dodatkowymi kontrolkami, aby dopasować je do swoich konkretnych wymagań biznesowych. Szczęśliwego kodowania

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz pusty dokument Word z przyciskiem poleceń – przewodnik krok po kroku](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Jak wstawić przycisk ActiveX w Word – Ustaw podpis przycisku](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Utwórz pusty dokument Word w Javie – pełny przewodnik Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}