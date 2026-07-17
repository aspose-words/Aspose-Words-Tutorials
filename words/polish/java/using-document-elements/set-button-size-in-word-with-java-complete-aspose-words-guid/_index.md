---
category: general
date: 2026-07-16
description: Ustaw rozmiar przycisku programowo w dokumencie Word przy użyciu Aspose.Words
  for Java. Dowiedz się, jak wstawić przycisk ActiveX, ustawić jego położenie i więcej.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: pl
lastmod: 2026-07-16
og_description: Ustaw rozmiar przycisku w dokumencie Word przy użyciu Javy. Ten przewodnik
  krok po kroku pokazuje, jak wstawić przycisk ActiveX, ustawić jego położenie i programowo
  dodać przycisk.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Ustaw rozmiar przycisku w Wordzie przy użyciu Javy – pełny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Ustaw rozmiar przycisku w Wordzie przy użyciu Javy – Kompletny przewodnik Aspose.Words
url: /pl/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw rozmiar przycisku w Wordzie przy użyciu Javy – Kompletny przewodnik Aspose.Words

Zastanawiałeś się kiedyś, jak **ustawić rozmiar przycisku** wewnątrz pliku Word bez otwierania interfejsu? Nie jesteś jedyny. Gdy musisz na bieżąco generować dokument wypełniony formularzem — na przykład pakiet powitalny z przyciskiem „Submit” — robienie tego programowo oszczędza godziny ręcznej pracy.

W tym samouczku przeprowadzimy Cię przez dokładne kroki, aby **wstawić przycisk ActiveX**, dostosować jego wymiary, prawidłowo go pozycjonować i ostatecznie zapisać plik. Po zakończeniu będziesz w stanie **programowo dodawać przyciski** do dowolnego dokumentu Word przy użyciu Aspose.Words for Java.

## Wymagania wstępne – Co potrzebujesz przed rozpoczęciem

- **Java Development Kit (JDK) 8+** – kod działa na dowolnym nowoczesnym JDK.
- **Aspose.Words for Java** library (download the latest JAR from the official site).  
- **IDE** według własnego wyboru — IntelliJ IDEA, Eclipse lub nawet prosty edytor tekstu działa.
- Podstawowa znajomość składni Javy; nie wymagana głęboka wiedza o automatyzacji Worda.

> *Wskazówka:* Trzymaj plik JAR Aspose.Words na classpathie swojego projektu, w przeciwnym razie napotkasz `ClassNotFoundException` w momencie, gdy spróbujesz zaimportować `com.aspose.words.*`.

## Krok 1: Utwórz nowy dokument Word

Pierwszą rzeczą, którą robimy, jest utworzenie pustego dokumentu i `DocumentBuilder`. Traktuj builder jak pióro, które pozwala nam rysować cokolwiek wewnątrz pliku.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Dlaczego to ważne:** Obiekt `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` jest siłą napędową, która pozwala nam wstawiać akapity, tabele i — tak — kontrolki ActiveX.

## Krok 2: Wstaw przycisk ActiveX – Moment „Wstaw przycisk ActiveX”

Teraz faktycznie **wstawiamy przycisk activex** do dokumentu. Aspose.Words udostępnia wygodną metodę `insertForms2OleControl`, która zwraca obiekt `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Co się dzieje pod maską?* `Forms2OleControlType.COMMAND_BUTTON` informuje Word, że chcemy klasyczny CommandButton, taki sam, jaki można dodać z zakładki Developer w interfejsie użytkownika.

## Krok 3: Ustaw rozmiar i położenie przycisku – Główna logika „Ustaw rozmiar przycisku”

Tutaj błyszczy główne słowo kluczowe. **Ustawimy rozmiar przycisku** oraz **ustawimy położenie przycisku**, aby kontrolka pojawiła się dokładnie tam, gdzie chcemy na stronie.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Dlaczego to ważne:** Punkty są natywną jednostką miary w Wordzie (1 punkt = 1/72 cala). Modyfikując `setLeft`, `setTop`, `setWidth` i `setHeight` uzyskujesz kontrolę piksel‑perfekcyjną — koniec z „wygląda dobrze na moim ekranie, ale nie na drukarce”.

> *Typowy błąd:* Zapomnienie o ustawieniu szerokości lub wysokości pozostawi przycisk w domyślnym rozmiarze, który może być za mały do kliknięcia. Zawsze podawaj oba parametry.

## Krok 4: Zapisz dokument – „Utworzenie przycisku w dokumencie Word” zakończone

Na koniec zapisujemy plik na dysku. Nazwa sugeruje, że **tworzymy przycisk w dokumencie Word** wewnątrz pliku .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Gdy otworzysz `CommandButtonDemo.docx` w Microsoft Word, zobaczysz przycisk **Submit** umieszczony 100 pt od lewej krawędzi i 150 pt od góry, o rozmiarze 80 × 30 pt. Kliknięcie go w interfejsie uruchomi domyślne zachowanie ActiveX (które możesz później podłączyć przy użyciu VBA, jeśli zajdzie taka potrzeba).

### Oczekiwany zrzut ekranu

![Dokument Word pokazujący wstawiony przycisk z ustawionym rozmiarem przycisku](https://example.com/images/set-button-size.png "Zrzut ekranu pliku Word, w którym rozmiar przycisku został ustawiony przy użyciu Aspose.Words for Java")

*Alt text:* ustaw rozmiar przycisku w dokumencie Word przy użyciu Javy

## Krok 5 (Opcjonalnie): Dodaj więcej kontrolek lub stylizuj przycisk

Jeśli potrzebujesz **programowo dodawać przyciski** poza pojedynczym przyciskiem Submit, po prostu powtórz blok wstawiania z nowymi nazwami i podpisami. Możesz także dostosować czcionkę, kolor tła lub później podłączyć makra VBA.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Wskazówka:* Zachowaj wszystkie wymiary przycisków spójne dla profesjonalnego wyglądu. Szybki sposób to przechowywanie szerokości/wysokości w stałych.

## Częste pytania i przypadki brzegowe

### „Czy mogę ustawić rozmiar przycisku w centymetrach zamiast punktów?”

API Worda akceptuje tylko punkty, ale możesz przeliczyć centymetry na punkty (`points = cm * 28.3465`). Napisz małą metodę pomocniczą, jeśli wolisz jednostki metryczne.

### „Co zrobić, jeśli przycisk ma pojawić się na konkretnej stronie?”

Po wstawieniu przycisku możesz przenieść kursor na określoną stronę używając `builder.moveToPage(pageNumber)`. Wstaw kontrolkę zaraz po przeniesieniu, a następnie ustaw jej położenie jak pokazano powyżej.

### „Czy to działa z plikami .doc (Word 97‑2003)?”

Tak — Aspose.Words automatycznie obsługuje starsze formaty. Wystarczy zmienić rozszerzenie pliku w `doc.save("Demo.doc")`.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się cały program, który możesz skopiować‑wkleić do klasy Java i uruchomić od razu (zakładając, że plik JAR Aspose.Words znajduje się na classpathie).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Uruchom program, otwórz wygenerowany `CommandButtonDemo.docx`, a zobaczysz dwa starannie wymiarowane przyciski gotowe do interakcji.

## Zakończenie – Opanowałeś ustawianie rozmiaru przycisku w Wordzie

Przeszliśmy właśnie przez kompletną, kompleksową rozwiązanie dla **ustawiania rozmiaru przycisku** i **ustawiania położenia przycisku** przy użyciu Aspose.Words for Java. Postępując zgodnie z krokami, możesz **wstawić przycisk activex**, **programowo dodawać przyciski** oraz ostatecznie **tworzyć przyciski w dokumencie Word**, które zachowują się dokładnie tak, jak potrzebujesz.

Co dalej? Spróbuj osadzić przycisk w komórce tabeli lub dołączyć makro VBA, które weryfikuje pola formularza przed wysłaniem. Ten sam wzorzec działa dla innych kontrolek ActiveX, takich jak pola wyboru czy pola kombi — wystarczy zamienić `Forms2OleControlType.COMMAND_BUTTON` na odpowiednią wartość wyliczeniową.

Jeśli napotkasz jakiekolwiek problemy, zostaw komentarz poniżej. Szczęśliwego kodowania i ciesz się mocą automatycznego tworzenia dokumentów Word!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak ustawić LoadOptions w Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak usunąć stopki z dokumentów Word przy użyciu Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Kompletny przewodnik po przetwarzaniu dokumentów Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}