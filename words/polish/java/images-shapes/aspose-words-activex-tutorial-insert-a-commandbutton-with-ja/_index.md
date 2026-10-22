---
category: general
date: 2026-08-07
description: Samouczek Aspose.Words ActiveX pokazuje, jak dodać kontrolkę CommandButton
  do dokumentu Word przy użyciu języka Java. Poznaj pełny kod, konfigurację i kroki
  zapisywania.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: pl
lastmod: 2026-08-07
og_description: Samouczek Aspose.Words ActiveX wyjaśnia, jak osadzić kontrolkę ActiveX
  CommandButton w dokumencie Word przy użyciu języka Java. Postępuj zgodnie z pełnym
  przykładem, aby utworzyć, skonfigurować i zapisać dokument.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Samouczek Aspose.Words ActiveX – przewodnik krok po kroku w Javie
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Samouczek Aspose.Words ActiveX – wstaw przycisk CommandButton przy użyciu Javy
url: /pl/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Samouczek Aspose.Words ActiveX – wstawienie CommandButton w Javie

Jeśli potrzebujesz osadzić kontrolkę ActiveX w pliku Word, ten **samouczek Aspose.Words ActiveX** przeprowadzi Cię przez cały proces. Zobaczysz, jak utworzyć pusty dokument, wstawić CommandButton, ustawić jego właściwości i zapisać wynik — wszystko przy użyciu czystego kodu Java.

Przykład wykorzystuje API Aspose.Words for Java, które eliminuje potrzebę posiadania Microsoft Office na serwerze budowania. Po zakończeniu tego przewodnika będziesz mógł generować pliki .docx zawierające w pełni funkcjonalne kontrolki CommandButton gotowe do użycia w środowiskach Windows.

## Wymagania wstępne

- Zainstalowany Java Development Kit (JDK) 8 lub nowszy.
- Maven lub inne narzędzie budujące do zarządzania zależnościami.
- Licencja Aspose.Words for Java (lub tymczasowy klucz ewaluacyjny), aby uniknąć znaków wodnych wersji próbnej.
- Podstawowa znajomość składni Java i programowania obiektowego.

> **Pro tip:** Dodaj zależność Aspose.Words Maven do swojego `pom.xml`, aby IDE automatycznie rozwiązywało klasy:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Krok 1: Utwórz nowy pusty dokument i `DocumentBuilder`

`Document` reprezentuje plik Word w pamięci, natomiast `DocumentBuilder` udostępnia płynne API do edycji dokumentu. Inicjalizacja obu obiektów przygotowuje dokument do dalszych modyfikacji.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Dlaczego to ważne:**  
`DocumentBuilder` śledzi bieżącą pozycję kursora, więc każda kolejna operacja wstawiania — np. dodanie kontrolki — pojawia się dokładnie tam, gdzie zamierzasz.

## Krok 2: Wstaw kontrolkę ActiveX CommandButton

Aspose.Words udostępnia `Forms2OleControl` dla obiektów ActiveX. Metoda `insertForms2OleControl` wymaga określenia typu kontrolki, który podajesz przy użyciu wyliczenia `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Wyjaśnienie:**  
Wstawiona kontrolka jest obiektem opartym na COM, który Word wyświetli jako przycisk, który można kliknąć, gdy dokument zostanie otwarty w środowisku Windows.

## Krok 3: Skonfiguruj właściwości przycisku

Po wstawieniu możesz dostosować nazwę, etykietę, rozmiar i pozycję przycisku. Te właściwości wpływają na wygląd i zachowanie kontrolki w Wordzie.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Dlaczego te ustawienia są ważne:**  

- **Name** – Umożliwia makróm VBA odwoływanie się do kontrolki (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Określa widoczną etykietę, na którą użytkownicy klikają.
- **Left / Top** – Kontroluje położenie względem marginesów strony.
- **Width / Height** – Zapewnia spójny rozmiar wizualny na różnych rozdzielczościach ekranu.

## Krok 4: Zapisz dokument

Wywołanie `save` zapisuje reprezentację w pamięci do pliku fizycznego. Możesz wybrać dowolny obsługiwany format (`.docx`, `.doc`, `.pdf` itp.). W tym samouczku pozostajemy przy natywnym formacie Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Wynik:**  
Otwarcie `ActiveXDemo.docx` w Microsoft Word wyświetla przycisk CommandButton z etykietą **Submit** umieszczony w określonych współrzędnych. Kliknięcie przycisku wywołuje domyślne zachowanie (domyślnie nie ma dołączonego kodu VBA).

## Pełny kod źródłowy

Łącząc wszystkie elementy, kompletny, działający program wygląda następująco:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Oczekiwany wynik

- Plik o nazwie **ActiveXDemo.docx** znajdujący się w folderze `output`.
- Po otwarciu w Microsoft Word (Windows) dokument wyświetla klikalny przycisk **Submit** w określonej pozycji.
- Przycisk można zaznaczyć, przenieść lub połączyć z kodem VBA za pomocą interfejsu Word (Developer → Properties).

## Obsługa typowych wariantów

| Scenariusz | Dostosowanie |
|----------|------------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word nie udostępnia zdarzeń ActiveX przez Aspose.Words. Musisz dodać kod VBA ręcznie po wygenerowaniu dokumentu. |
| **Multiple controls** | Powtórz blok wstawiania/konfiguracji z różnymi wartościami `setName` i `setCaption`. |
| **Different control type (e.g., CheckBox)** | Użyj `Forms2OleControlType.CHECKBOX` w wywołaniu `insertForms2OleControl`. |
| **Non‑Windows platforms** | Kontrolki ActiveX renderują się tylko w Wordzie na Windows. Dla rozwiązań wieloplatformowych rozważ kontrolki treści (`StructuredDocumentTag`). |

## Najlepsze praktyki i pułapki

- **License early** – Zarejestruj licencję Aspose.Words przed utworzeniem `Document`, aby uniknąć komunikatów wersji próbnej.
- **Coordinate system** – Pozycje mierzone są w punktach (1 pt = 1/72 in). Konwertuj z pikseli lub centymetrów, jeśli Twój projekt UI używa tych jednostek.
- **File paths** – Używaj ścieżek bezwzględnych lub API `Paths` Javy, aby uniknąć `FileNotFoundException`, gdy katalog wyjściowy nie istnieje.
- **Thread safety** – `Document` i `DocumentBuilder` nie są bezpieczne wątkowo. Twórz oddzielne instancje na wątek, jeśli generujesz dokumenty równolegle.
- **Testing** – Zweryfikuj wygenerowany dokument w docelowej wersji Word (np. Word 2016, Word 365), ponieważ starsze wersje mogą wyświetlać kontrolki ActiveX inaczej.

## Zakończenie

Ten **samouczek Aspose.Words ActiveX** pokazuje, jak programowo dodać kontrolkę CommandButton do dokumentu Word przy użyciu Javy. Nauczyłeś się:

1. Zainicjować `Document` i `DocumentBuilder`.
2. Wstawić `Forms2OleControl` typu `COMMAND_BUTTON`.
3. Ustawić nazwę, etykietę, rozmiar i pozycję przycisku.
4. Zapisać dokument jako plik .docx zawierający kontrolkę ActiveX.

Od tego momentu możesz badać dodatkowe typy kontrolek, automatyzować wstawianie makr VBA lub łączyć kontrolki ActiveX z innymi funkcjami Aspose.Words, takimi jak scalanie korespondencji (mail‑merge) i kontrolki treści. Eksperymentuj z różnymi układami i integruj generowane dokumenty w większym, opartym na Javie pipeline raportowania.

---

## Co powinieneś nauczyć się dalej?

Następne tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Używanie obiektów OLE i kontrolek ActiveX w Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Jak tworzyć pola formularzy i dodawać treść przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Konwersja Word do RTF z samouczkiem Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}