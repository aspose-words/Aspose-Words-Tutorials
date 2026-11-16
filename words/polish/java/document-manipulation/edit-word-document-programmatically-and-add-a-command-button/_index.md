---
category: general
date: 2026-11-15
description: Edytuj dokument Word programowo, aby wstawić przycisk polecenia. Dowiedz
  się, jak dodać przycisk, ustawić nazwę przycisku polecenia i utworzyć przycisk formularza
  w Wordzie w kilka minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: pl
lastmod: 2026-11-15
og_description: Edytuj dokument Word programowo i wstaw przycisk polecenia. Ten przewodnik
  pokazuje, jak dodać przycisk, ustawić nazwę przycisku polecenia i szybko utworzyć
  przycisk formularza w Wordzie.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Edytuj dokument Word programowo – dodaj przycisk polecenia
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Edytuj dokument Word programowo i dodaj przycisk polecenia
url: /pl/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Edytuj dokument Word programowo i dodaj przycisk poleceń

Jeśli potrzebujesz **edytować dokument Word programowo**, najszybszym rozwiązaniem jest użycie API Aspose.Words. Ten samouczek pokazuje dokładnie, **jak dodać przycisk** kontrolny, skonfigurować jego etykietę oraz **ustawić nazwę przycisku poleceń**, aby dokument mógł działać jako prosty formularz. Po zakończeniu będziesz mieć w pełni edytowalny plik *.docx* zawierający funkcjonalny przycisk poleceń gotowy do dalszego przetwarzania.

Nauczysz się, jak **wstawić słowo przycisku poleceń**, **utworzyć słowo przycisku formularza** oraz zarządzać właściwościami przycisku bez ręcznego otwierania Worda. Jedynym wymogiem wstępnym jest podstawowe środowisko programistyczne Java oraz biblioteka Aspose.Words for Java.

## Wymagania wstępne

- Java 17 lub nowsza (kod działa również z Java 8+)
- Aspose.Words for Java (pobierz z [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Istniejący dokument Word (`input.docx`), który chcesz zmodyfikować
- Znajomość Maven lub Gradle w celu dodania zależności Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Krok 1: Załaduj dokument Word

Pierwszą operacją przy **edytowaniu dokumentu Word programowo** jest wczytanie pliku źródłowego do obiektu `Document`. Obiekt ten reprezentuje cały plik Word w pamięci, umożliwiając manipulację jego zawartością.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Dlaczego to ważne:** Ładowanie dokumentu tworzy strukturę podobną do DOM, którą Aspose.Words może przeglądać i modyfikować. Pominięcie tego kroku pozostawiłoby Cię bez celu dla wstawiania przycisku.

## Krok 2: Utwórz `DocumentBuilder` do edycji dokumentu

`DocumentBuilder` działa jak kursor wewnątrz pliku Word. Pozwala wstawiać tekst, obrazy i kontrolki formularzy w bieżącej pozycji.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Wskazówka:** Jeśli potrzebujesz przycisku w określonym akapicie, najpierw przesuń builder za pomocą `builder.moveToParagraph(index, true);`.

## Krok 3: Wstaw Forms2OleControl (przycisk poleceń)

Teraz odpowiadamy na centralne pytanie **jak dodać przycisk** w pliku Word. Metoda `insertForms2OleControl()` tworzy starszy przycisk *Forms2.0*, który jest najbardziej kompatybilną kontrolką we wszystkich wersjach Worda.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Przypadek brzegowy:** Kontrolka Forms2.0 jest widoczna tylko w *Trybie Projektowania* Worda. Jeśli potrzebujesz nowszego przycisku ActiveX, rozważ użycie `insertOleControl()`, ale kontrolka legacy działa w większości scenariuszy automatyzacji.

## Krok 4: Skonfiguruj właściwości przycisku

Po wstawieniu kontrolki możesz **ustawić nazwę przycisku poleceń** oraz **wstawić słowo przycisku poleceń** (etykietę), aby był przyjazny dla użytkownika.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Dlaczego te właściwości?**  
> - `setName` nadaje przyciskowi identyfikator, który może być odwoływany w VBA lub przez zewnętrzne narzędzia.  
> - `setCaption` to widoczna etykieta, efektywnie **tworząc słowo przycisku formularza**, na które klikają użytkownicy.

Możesz także dostosować rozmiar, pozycję lub dodać makro, uzyskując dostęp do obiektu OLE, ale te tematy wykraczają poza zakres tego krótkiego przewodnika.

## Krok 5: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany do nowego pliku. Ten krok **tworzy słowo przycisku formularza** w dokumencie wyjściowym.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Rezultat:** Otwierając `output.docx` w Microsoft Word, zobaczysz przycisk oznaczony „Submit”. Po przełączeniu Worda w *Tryb Projektowania* (Developer → Design Mode) możesz dwukrotnie kliknąć przycisk, aby podłączyć makro lub po prostu używać go jako elementu zastępczego w formularzu.

### Oczekiwany wynik

Po otwarciu zapisanego pliku:

- Punkt wstawiania kursora zostaje zastąpiony przyciskiem.
- Przycisk wyświetla etykietę **Submit**.
- Wewnętrzna nazwa przycisku to **cmdSubmit**, którą możesz odwoływać w VBA lub w zewnętrznych skryptach automatyzacji.

## Częste pytania i warianty

### Jak dodać przycisk do konkretnego akapitu?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Jak wstawić przycisk wewnątrz komórki tabeli?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Co zrobić, jeśli potrzebny jest większy przycisk?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Jak **wstawić słowo przycisku poleceń** używając innego języka (np. C#)?

Ta sama logika obowiązuje; zamień składnię Java na odpowiedniki C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Pro tipy i pułapki

- **Pro tip:** Zawsze wywołuj `builder.moveToDocumentEnd()` przed wstawieniem przycisku, jeśli chcesz go umieścić na samym końcu dokumentu.  
- **Uwaga:** Zapisywanie do tego samego pliku, który został otwarty, może uszkodzić dokument w przypadku wystąpienia wyjątku. Użyj osobnej ścieżki wyjściowej, jak pokazano.  
- **Kompatybilność:** Przyciski legacy Forms2.0 działają w Word 2007‑2021. Dla Worda w przeglądarce rozważ użycie kontrolek zawartości.  
- **Wydajność:** Ładowanie bardzo dużych dokumentów (>100 MB) może zużywać znaczną ilość pamięci. Użyj `Document.load(InputStream, LoadOptions)` z `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, aby ograniczyć zużycie zasobów.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program w Javie. Skopiuj go do klasy o nazwie `WordButtonDemo.java`, dostosuj ścieżki do plików i uruchom `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Uruchom program i otwórz `output.docx`, aby zweryfikować, że przycisk pojawił się zgodnie z oczekiwaniami.

## Podsumowanie

Teraz wiesz, jak **edytować dokument Word programowo**, aby **wstawić słowo przycisku poleceń**, **utworzyć słowo przycisku formularza** oraz **ustawić nazwę przycisku poleceń** przy użyciu Aspose.Words for Java. To podejście eliminuje ręczną edycję, umożliwia przetwarzanie wsadowe formularzy i integruje się płynnie z automatycznymi przepływami pracy.

Następnie możesz zbadać:

- Dodawanie makr VBA do przycisku (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Użycie **kontrolek zawartości** dla bogatszych doświadczeń formularzowych (`builder.insertCheckBox()` itp.)  
- Automatyzację masowego wstawiania w wielu dokumentach przy pomocy pętli  

Śmiało eksperymentuj z rozmiarem, pozycją i obsługą zdarzeń przycisku, aby dopasować go do swojego scenariusza. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}