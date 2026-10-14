---
category: general
date: 2026-10-13
description: Utwórz przycisk pola formularza w programie Word przy użyciu Aspose.Words
  for Java. Dowiedz się, jak wstawić przycisk polecenia w formularzu Word oraz ustawić
  jego etykietę w kilku prostych krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: pl
lastmod: 2026-10-13
og_description: Utwórz przycisk pola formularza w programie Word przy użyciu Aspose.Words
  for Java. Ten samouczek pokazuje, jak szybko wstawić pola przycisku polecenia w
  Wordzie i ustawić etykietę przycisku polecenia.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Utwórz przycisk pola formularza w Word – przewodnik Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Utwórz przycisk pola formularza w Wordzie przy użyciu Aspose.Words Java
url: /pl/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz przycisk pola formularza w Wordzie przy użyciu Aspose.Words Java

Jeśli potrzebujesz **create form field button** w dokumencie Word, ten przewodnik przeprowadzi Cię przez cały proces przy użyciu Aspose.Words for Java. Niezależnie od tego, czy tworzysz szablon formularza do wypełnienia, czy dodajesz interaktywne kontrolki do raportu, dowiesz się, jak **insert command button word** pola formularza i **set command button caption** przy minimalnym kodzie.

Samouczek obejmuje wszystko, od konfiguracji Maven po w pełni działający przykład, dzięki czemu możesz skopiować‑wkleić kod, uruchomić go i zobaczyć plik `.docx` zawierający przycisk, który można kliknąć, gotowy do dalszej personalizacji.

## Wymagania wstępne

- Java 17 (lub nowsza) zainstalowana i skonfigurowana na Twoim komputerze.
- Maven 3.6+ do zarządzania zależnościami.
- IDE lub edytor tekstu według własnego wyboru (np. IntelliJ IDEA, VS Code).
- Ważna licencja Aspose.Words for Java (bezpłatna wersja próbna działa w trybie ewaluacji).

## Krok 1: Dodaj Aspose.Words do swojego projektu Maven

Utwórz plik `pom.xml` (lub edytuj istniejący) i dodaj zależność Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Wskazówka:** Utrzymuj numer wersji aktualny. Nowe wydania dodają wsparcie dla najnowszych funkcji Word i poprawiają wydajność.

## Krok 2: Zainicjuj pusty dokument i `DocumentBuilder`

Klasa `DocumentBuilder` udostępnia płynne API do edycji dokumentu Word. W tym kroku tworzymy pusty `Document` i dołączamy do niego builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Utworzenie dokumentu jest podstawą dla obiektów **create form field button**, które pojawią się później w samouczku.

## Krok 3: Wstaw pole formularza przycisku poleceń

Aspose.Words udostępnia klasę `Forms2OleControl` dla kontrolek formularzy OLE. Aby **insert command button word** pola formularza, wywołaj `insertForms2OleControl` z wartością wyliczenia `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoda zwraca instancję `Forms2OleControl`, którą możemy skonfigurować przed zapisem.

## Krok 4: Zdefiniuj rozmiar i pozycję przycisku

Przycisk polecenia wymaga wyraźnych wymiarów i umiejscowienia na stronie. Dostosuj szerokość, wysokość i współrzędne do swojego układu.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Drobne dopasowanie tych wartości zapewnia, że przycisk pojawi się dokładnie tam, gdzie chcesz w ostatecznym dokumencie.

## Krok 5: **Set command button caption**

Widoczny tekst na przycisku jest kontrolowany metodą `setCaption`. To tutaj **set command button caption**, aby poprowadzić użytkownika.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Możesz zamienić `"Click Me"` na dowolną etykietę pasującą do zamierzenia formularza, np. `"Submit"` lub `"Approve"`.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument na dysku. Powstały plik zawiera interaktywny przycisk i może być otwarty w Microsoft Word lub LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Uruchomienie programu generuje `CommandButtonDemo.docx`. Otworzenie go w Wordzie pokazuje przycisk oznaczony **Click Me**, umieszczony 50 pt od lewej i 100 pt od górnej krawędzi strony.

### Oczekiwany wynik

- Plik `.docx` o nazwie `CommandButtonDemo.docx`.
- Dokument zawiera jedną stronę z polem formularza przycisku poleceń.
- Przycisk wyświetla ustawiony przez Ciebie podpis (np. **Click Me**).

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak dostosować |
|-----------|----------------|
| **Multiple buttons** | Wywołaj `insertForms2OleControl` wielokrotnie, dostosowując `setLeft`/`setTop` dla każdego nowego przycisku. |
| **Different caption per button** | Użyj `setCaption` z unikalnym ciągiem po każdym wstawieniu. |
| **Button inside a table cell** | Przesuń kursor do żądanej komórki przy pomocy `builder.moveTo(cell.getFirstParagraph())` przed wstawieniem kontrolki. |
| **Legacy Word formats (.doc)** | Zapisz używając `doc.save("Demo.doc", SaveFormat.DOC);` – przycisk polecenia zostanie zachowany. |
| **Read‑only forms** | Po wstawieniu ustaw `commandButton.setEnabled(false);`, aby uniemożliwić interakcję użytkownika. |

## Wskazówki dla solidnej implementacji

- **Validate dimensions**: Niezwykle duże szerokości mogą spowodować, że przycisk wyjdzie poza margines strony.
- **License enforcement**: Bez ważnej licencji Aspose.Words dodaje znak wodny do wygenerowanego dokumentu. Zastosuj licencję wcześnie przy pomocy `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testing**: Otwórz wygenerowany plik w Wordzie i przełącz **Design Mode** (Developer → Design Mode), aby zobaczyć właściwości przycisku.

## Pełny kod źródłowy podsumowanie

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Skopiuj kod do pliku o nazwie `InsertCommandButtonDemo.java`, skompiluj przy użyciu Maven (`mvn compile`) i uruchom (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Wygenerowany dokument pojawi się w katalogu głównym Twojego projektu.

## Zakończenie

Teraz wiesz, jak **create form field button** w Wordzie przy użyciu Aspose.Words for Java, jak **insert command button word** pola formularza oraz jak programowo **set command button caption**. Ten kompleksowy przykład zapewnia solidną podstawę do tworzenia bardziej rozbudowanych, interaktywnych dokumentów Word — niezależnie od tego, czy potrzebujesz jednego przycisku zatwierdzania, czy pełnego zestawu kontrolek formularza.

### Co dalej?

- Poznaj inne kontrolki formularzy, takie jak pola wyboru (`Forms2OleControlType.CHECKBOX`) i pola tekstowe (`Forms2OleControlType.TEXTBOX`).
- Połącz pola formularzy z funkcją korespondencji seryjnej, aby generować spersonalizowane kwestionariusze.
- Użyj API Aspose.Words `FormField`, aby odczytać dane wprowadzone przez użytkownika po wypełnieniu dokumentu.

Śmiało eksperymentuj z różnymi rozmiarami, podpisami i pozycjami. Gdy opanujesz przyciski poleceń, dodawanie w pełni funkcjonalnych formularzy do Twoich procesów automatyzacji Word stanie się prostym zadaniem. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularzy i dodawać treść przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Dodaj pole formularza Combo Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Dodaj pole formularza Check Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}