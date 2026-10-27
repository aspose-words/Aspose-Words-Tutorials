---
category: general
date: 2026-10-16
description: Utwórz pusty dokument Word w Javie i dowiedz się, jak dodać przycisk
  ActiveX, ustawić jego podpis oraz dostosować jego wymiary przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: pl
lastmod: 2026-10-16
og_description: Utwórz pusty dokument Word w Javie, a następnie dodaj przycisk ActiveX,
  ustaw jego podpis i określ wymiary przy użyciu Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Utwórz pusty dokument Word i osadź przycisk ActiveX – przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Utwórz pusty dokument Word i dodaj przycisk ActiveX (Java)
url: /pl/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word i dodaj przycisk ActiveX (Java)

Jeśli potrzebujesz **utworzyć pusty dokument Word** programowo, ten przewodnik pokaże Ci, jak zrobić to w Javie przy użyciu Aspose.Words. Dowiesz się także, jak **dodać przycisk ActiveX**, **ustawić jego etykietę** oraz **ustawić wymiary przycisku**, aby kontrolka wyglądała dokładnie tak, jak tego oczekujesz.

Ten tutorial obejmuje:

* Inicjalizację pustego pliku Word przy użyciu Aspose.Words for Java.  
* Wstawienie kontrolki ActiveX `CommandButton`.  
* Konfigurację etykiety i rozmiaru przycisku.  
* Zapis końcowego pliku `.docx`.

Powinieneś mieć podstawową znajomość Javy oraz aktualną wersję biblioteki Aspose.Words for Java (kod działa z wersją 23.9 i nowszą). Nie są wymagane dodatkowe zależności.

![Utwórz pusty dokument Word z przyciskiem ActiveX](/images/activex-button-example.png){: .align-center alt="Utwórz pusty dokument Word z przyciskiem ActiveX"}

## Utwórz pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie pustego obiektu `Document`. Obiekt ten reprezentuje cały plik Word w pamięci i udostępnia klasę `DocumentBuilder` do edycji.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Dlaczego to ważne:**  
Utworzenie pustego dokumentu daje czyste płótno, unikając ukrytych stylów lub sekcji, które mogłyby zakłócić późniejsze obliczenia układu.

## Dodaj przycisk ActiveX do dokumentu

Aspose.Words pozwala osadzać starsze kontrolki ActiveX za pomocą klasy `Forms2OleControl`. Poniższy kod wstawia kontrolkę `CommandButton` w bieżącej pozycji kursora.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Wskazówka:** Wartość `setOleClassName` `"Forms.CommandButton.1"` jest ProgID standardowego przycisku Microsoft Forms. Użycie innego ProgID (np. `"Forms.CheckBox.1"`) spowodowałoby wstawienie innego typu kontrolki.

## Ustaw etykietę przycisku

Etykieta to tekst wyświetlany na powierzchni przycisku. Możesz ją zmienić w dowolnym momencie przed zapisaniem dokumentu.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Dlaczego tego potrzebujesz:** Użytkownicy rozumieją kontrolkę tylko wtedy, gdy jej przeznaczenie jest jasne. Ustawienie sensownej etykiety poprawia użyteczność, szczególnie gdy dokument jest otwierany w Wordzie na Windowsie.

## Ustaw wymiary przycisku

Pozycja i rozmiar są określane w punktach (1 punkt = 1/72 cala). Dostosuj wartości, aby pasowały do Twojego układu.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Typowe wariacje:**

| Scenariusz | Dostosowanie |
|------------|--------------|
| Większy przycisk dla ekranów dotykowych | Zwiększ `setWidth` i `setHeight` proporcjonalnie |
| Wyśrodkowany przycisk na stronie | Oblicz `left = (pageWidth - width) / 2` |
| Wiele przycisków w kolumnie | Zwiększ `setTop` dla każdego nowego przycisku |

## Zapisz dokument zawierający przycisk ActiveX

Na koniec zapisz dokument na dysku. Format `.docx` zachowuje kontrolkę ActiveX dla wersji Windows Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Oczekiwany rezultat:** Otwierając `ActiveXCommandButton.docx` w Wordzie (Windows) zobaczysz pustą stronę z klikalnym przyciskiem oznaczonym **Click Me**, umieszczonym 100 pt od lewego marginesu i 200 pt od górnego marginesu.

## Pełny, gotowy do uruchomienia przykład

Skopiuj całą klasę poniżej do swojego IDE, dodaj plik JAR Aspose.Words for Java do ścieżki klas projektu i uruchom ją.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Uruchomienie programu tworzy plik `ActiveXCommandButton.docx` w katalogu roboczym. Otwórz go w Microsoft Word (Windows), aby zweryfikować, że przycisk pojawia się dokładnie tak, jak skonfigurowano.

## Dlaczego to podejście jest zalecane

* **Prostota:** Używany jest wyłącznie podstawowy API Aspose.Words; nie są potrzebne interfejsy COM ani dodatkowe biblioteki.  
* **Przenośność:** Kod działa na każdej platformie obsługującej Javę, choć sama kontrolka ActiveX działa tylko w wersjach Worda na Windowsie.  
* **Łatwość utrzymania:** Wszystkie właściwości (etykieta, wymiary, pozycja) są ustawiane przy użyciu czytelnych, samodokumentujących się metod, co ułatwia przyszłe modyfikacje.

## Typowe pułapki i jak ich uniknąć

| Pułapka | Rozwiązanie |
|---------|-------------|
| Przycisk nie pojawia się w Wordzie na macOS lub Linux | Kontrolki ActiveX działają tylko w Windows. Użyj innej kontrolki (np. kontrolki zawartości) dla dokumentów wieloplatformowych. |
| Etykieta jest obcięta | Upewnij się, że szerokość przycisku jest wystarczająca dla tekstu; zwiększ `setWidth` lub użyj krótszej etykiety. |
| Przycisk nachodzi na inną treść | Dostosuj wartości `setTop` i `setLeft` lub wstaw nowy akapit przed kontrolką, aby uzyskać własną przestrzeń. |

## Kolejne kroki

Teraz, gdy potrafisz **utworzyć pusty dokument Word**, **dodać przycisk ActiveX**, **ustawić etykietę przycisku** i **ustawić wymiary przycisku**, możesz rozważyć:

* Dodanie kodu obsługi zdarzeń za pomocą makr VBA (wymaga osadzenia modułu makr).  
* Wstawianie wielu kontrolek w układzie tabeli dla dokumentów przypominających formularze.  
* Korzystanie z API **FormField** Aspose.Words dla rozwiązań formularzy działających na wielu platformach.

Eksperymentuj z różnymi rozmiarami, pozycjami i etykietami, aby dopasować je do swojego projektu dokumentu. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}