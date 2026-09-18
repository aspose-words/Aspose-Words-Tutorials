---
category: general
date: 2026-09-18
description: Utwórz pusty dokument w Javie i dodaj przycisk ActiveX. Dowiedz się,
  jak wstawić przycisk polecenia, zbudować interaktywny formularz i zapisać dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: pl
lastmod: 2026-09-18
og_description: Utwórz pusty dokument w Javie i osadź przycisk polecenia ActiveX.
  Skorzystaj z tego przewodnika krok po kroku, aby stworzyć interaktywny formularz
  i zapisać plik Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Utwórz pusty dokument z interaktywnym przyciskiem polecenia w Wordzie
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Utwórz pusty dokument z interaktywnym przyciskiem polecenia w Wordzie przy
  użyciu Javy
url: /pl/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument z interaktywnym przyciskiem polecenia w Word przy użyciu Javy

Jeśli potrzebujesz **utworzyć pusty dokument**, który zawiera przycisk klikalny, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words for Java. Nauczysz się budować interaktywny formularz, dodać przycisk ActiveX oraz ostatecznie zapisać plik Word — wszystko w kilku zwięzłych krokach.

Osadzenie przycisku polecenia zamienia statyczny plik .docx w funkcjonalny formularz, z którym użytkownicy mogą wchodzić w interakcję bezpośrednio w Microsoft Word. Ten tutorial obejmuje także **jak wstawić przycisk polecenia**, radzenie sobie z typowymi problemami oraz rozszerzanie rozwiązania o bardziej złożone formularze.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Java 17 lub nowszą (kod kompiluje się z JDK 17+)
* Aspose.Words for Java 23.9 lub nowszą – biblioteka udostępnia `Document`, `DocumentBuilder` oraz `Forms2OleControl`.
* IDE lub narzędzie budujące (Maven/Gradle), które może dodać zależność Aspose.Words.
* Podstawową znajomość składni Javy oraz koncepcji dokumentów Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Krok 1: Utwórz pusty dokument

Pierwszą operacją jest utworzenie nowego obiektu `Document`. Obiekt ten reprezentuje pusty plik Word gotowy do wypełnienia treścią.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Utworzenie pustego dokumentu daje czyste płótno, co jest niezbędne, gdy chcesz **utworzyć dokument Word** programowo, bez żadnego istniejącego szablonu.

## Krok 2: Zainicjalizuj DocumentBuilder

`DocumentBuilder` jest główną klasą służącą do dodawania tekstu, tabel i kontrolek formularzy. Działa na `Document`, który właśnie utworzyłeś.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder utrzymuje bieżący punkt wstawiania, więc kolejne polecenia wpływają na właściwe miejsce w pliku.

## Krok 3: Wstaw kontrolkę przycisku polecenia Forms2Ole

Aspose.Words udostępnia klasę `Forms2OleControl` dla kontrolek ActiveX. Aby **dodać przycisk activex**, żądasz typu `COMMANDBUTTON` od buildera.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Metoda `insertForms2OleControl` wstawia kontrolkę w bieżącej pozycji kursora buildera. Ponieważ kontrolka jest obiektem ActiveX, działa wyłącznie w wersji desktop Microsoft Word, a nie w Word Online.

## Krok 4: Skonfiguruj wygląd i pozycję przycisku

Możesz ustawić podpis przycisku, jego rozmiar i położenie przy użyciu metod ustawiających kontrolkę. Wartości pozycji mierzone są w punktach (1 punkt = 1/72 cala).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Dlaczego konfigurować te właściwości?* Ustawienie `Top` i `Left` zapewnia, że przycisk pojawi się w oczekiwanym miejscu na stronie, natomiast `Caption` definiuje widoczną etykietę dla użytkownika. Jeśli pominiesz szerokość/wysokość, Word przydzieli domyślne wymiary, które mogą nie pasować do Twojego projektu.

### Porada
Jeśli planujesz dodać wiele kontrolek, wywołaj `builder.moveToDocumentEnd()` przed każdym wstawieniem, aby uniknąć nakładania się obiektów.

## Krok 5: Zapisz dokument z osadzonym przyciskiem polecenia

Na koniec zapisz dokument na dysku. Rozszerzenie pliku musi być `.docx` (lub `.doc` dla starszych wersji Word), aby zachować kontrolkę ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Gdy otworzysz `CommandButton.docx` w Microsoft Word, zobaczysz przycisk oznaczony **Click Me**. Kliknięcie go wywoła domyślną akcję ActiveX (domyślnie nic nie robi). Później możesz dołączyć makro lub skrypt VBA, aby zdefiniować własne zachowanie.

## Jak wstawić przycisk polecenia do istniejącego formularza (opcjonalnie)

Jeśli już masz formularz z polami tekstowymi i chcesz **utworzyć interaktywny formularz**, który zawiera przycisk, wykonaj następujące dodatkowe kroki:

1. Załaduj istniejący dokument: `Document doc = new Document("ExistingForm.docx");`
2. Przenieś builder do żądanej lokalizacji: `builder.moveToParagraph(5, 0); // 6‑ty akapit, pierwszy węzeł`
3. Wstaw przycisk tak, jak w Kroku 3.
4. Dostosuj `Top`/`Left` przycisku w zależności od układu akapitu.

To podejście pozwala wzbogacić dowolny gotowy szablon Word o przycisk ActiveX bez konieczności tworzenia pliku od nowa.

## Przypadki brzegowe i rozwiązywanie problemów

| Sytuacja | Co sprawdzić | Zalecane rozwiązanie |
|----------|--------------|----------------------|
| Przycisk nie pojawia się w Word | Upewnij się, że otworzyłeś plik w wersji desktop Microsoft Word (Word Online usuwa ActiveX). | Otwórz plik w Word 2016+ w wersji desktop. |
| Podpis jest obcięty | Sprawdź, czy szerokość przycisku jest wystarczająca, aby pomieścić tekst. | Zwiększ `setWidth`, aż podpis się zmieści. |
| Zapis zgłasza `IOException` | Potwierdź, że katalog wyjściowy istnieje i masz uprawnienia do zapisu. | Utwórz katalog lub uruchom program z podwyższonymi uprawnieniami. |
| Wielokrotne przyciski nakładają się | Kursor buildera mógł nie przemieścić się po poprzednim wstawieniu. | Wywołaj `builder.moveToDocumentEnd()` przed wstawianiem każdej nowej kontrolki. |

## Pełny przykład do uruchomienia

Poniżej znajduje się kompletny, samodzielny program w Javie, który możesz skopiować, skompilować i uruchomić. Demonstracja obejmuje **utworzenie pustego dokumentu**, **dodanie przycisku activex** oraz **zapis dokumentu Word** w jednym przepływie.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document created: CommandButton.docx
```

Otwarcie `CommandButton.docx` pokazuje jedną stronę z przyciskiem oznaczonym **Click Me**, umieszczonym 100 pt od górnej i lewej krawędzi.

## Zakończenie

Teraz wiesz, jak **utworzyć pusty dokument**, osadzić **przycisk ActiveX** i przekształcić zwykły plik Word w **interaktywny formularz**. Opanowując **jak wstawić przycisk polecenia**, możesz rozszerzyć ten wzorzec o pola wyboru, listy rozwijane czy nawet własną logikę sterowaną VBA.

Następnie rozważ zgłębienie poniższych tematów powiązanych:

* **Utwórz interaktywny formularz** z polami tekstowymi (`builder.insertField`)  
* **Dodaj przycisk activex**, który uruchamia makro VBA (`builder.insertOleObject`)  
* **Utwórz dokument Word** z szablonu przy użyciu `Document(docTemplatePath)`  
* Konwersja powstałego .docx do PDF przy zachowaniu przycisku (uwaga: w PDF przycisk zostanie wyrenderowany jako statyczny obraz).

Śmiało eksperymentuj z rozmiarem, pozycją i etykietą przycisku, aby dopasować go do swojego projektu UI. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Jak tworzyć pola formularza i dodawać treść przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Utwórz projekt VBA w dokumencie Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Utwórz nowy dokument Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}