---
category: general
date: 2026-07-26
description: Jak wstawić przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words
  – dowiedz się, jak ustawić napis przycisku, pozycję i rozmiar w kilku linijkach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: pl
lastmod: 2026-07-26
og_description: Jak wstawić przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words.
  Postępuj zgodnie z tym samouczkiem krok po kroku, aby ustawić podpis przycisku,
  pozycję i rozmiar.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Jak wstawić przycisk ActiveX w Word – szybki przewodnik
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Jak wstawić przycisk ActiveX w Word – Ustaw podpis przycisku
url: /pl/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić przycisk ActiveX w Word – Ustaw podpis przycisku

Zastanawiałeś się kiedyś **jak wstawić kontrolki ActiveX** do pliku Word bez otwierania interfejsu użytkownika? Nie jesteś sam. W wielu aplikacjach korporacyjnych potrzebny jest przycisk, który uruchamia makro, a zrobienie tego programowo oszczędza godziny. Ten przewodnik pokazuje dokładnie **jak wstawić ActiveX** CommandButton przy użyciu Aspose.Words for Java oraz — tak — **jak ustawić podpis przycisku**, aby użytkownik wiedział, co ma kliknąć.

Przejdziemy krok po kroku przez cały proces: od skonfigurowania biblioteki, stworzenia nowego dokumentu, wstawienia przycisku, dopasowania jego rozmiaru i położenia, nadania przyjaznego podpisu, aż po zapisanie pliku. Na końcu będziesz mieć gotowy plik `.docx`, który otwiera się w Wordzie z w pełni działającym przyciskiem ActiveX gotowym do wywołania Twojego makra.

---

## Czego się nauczysz

- Zainstalować i odwołać się do Aspose.Words w projekcie Java.  
- Utworzyć nowy `Document` i `DocumentBuilder`.  
- **Wstawić ActiveX** kontrolkę CommandButton jedną linią kodu.  
- **Ustawić podpis przycisku**, dostosować jego pozycję i zdefiniować wymiary.  
- Zapisać dokument i otworzyć go w Wordzie, aby zobaczyć rezultat.

Wcześniejsze doświadczenie z ActiveX nie jest wymagane; wystarczy podstawowa znajomość Javy oraz kopia Aspose.Words.

---

## Wymagania wstępne

- Java 8 lub nowsza zainstalowana na Twoim komputerze.  
- Maven lub Gradle do zarządzania zależnościami (pokażemy fragment Maven).  
- Licencjonowana lub ewaluacyjna kopia **Aspose.Words for Java** (bezpłatna wersja próbna wystarczy do tego demo).  
- Microsoft Word (dowolna nowsza wersja) do przetestowania wygenerowanego pliku.

---

## Krok 1: Dodaj Aspose.Words do projektu

Na początek — dodaj zależność Aspose.Words. Jeśli używasz Maven, wstaw to do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Użytkownicy Gradle mogą dodać:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Po szybkim `mvn clean install` (lub `gradle build`) biblioteka znajdzie się na classpath i możesz przystąpić do kodowania.

---

## Krok 2: Utwórz nowy dokument i builder

`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` pozwala go edytować. Myśl o builderze jak o piórze rysującym na czystym płótnie.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Dlaczego zaczynamy od pustego dokumentu? Gwarantuje to pełną kontrolę nad każdym elementem, który dodajesz, i eliminuje ukryte formatowanie, które mogłoby Cię później zaskoczyć.

---

## Krok 3: Wstaw kontrolkę ActiveX CommandButton

Teraz najważniejszy element. Aspose.Words udostępnia metodę `insertForms2OleControl`, która może umieścić dowolną kontrolkę ActiveX, którą określisz. Tutaj prosimy o **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoda zwraca obiekt `Forms2OleControl`, dając programowy dostęp do właściwości przycisku. To właśnie tutaj **jak wstawić activex** staje się jedną linijką — bez konieczności majstrowania przy niskopoziomowych interfejsach COM.

---

## Krok 4: Pozycja, rozmiar i ustawienie podpisu przycisku

Przycisk unoszący się pośrodku strony nie jest zbyt użyteczny. Trzeba go umieścić tam, gdzie użytkownik się tego spodziewa, nadać mu sensowny rozmiar i — co najważniejsze — **ustawić podpis przycisku**, aby wiedział, co się stanie po kliknięciu.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Dlaczego te liczby?** Word używa punktów (1 pt ≈ 1/72 cala). `100 pt` ≈ 1,4 cala od lewej krawędzi, `150 pt` ≈ 2,1 cala od góry — mniej więcej środek standardowej strony A4. Dostosuj je do własnego układu.

Ustawienie podpisu jest kluczowe; bez niego przycisk wygląda jak pustokształtny prostokąt. Metoda `setCaption` przyjmuje dowolny ciąg znaków, więc możesz go później lokalizować.

---

## Krok 5: Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny folder, pamiętaj tylko, aby ścieżka istniała.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Gdy otworzysz `ActiveXButton.docx` w Wordzie, zobaczysz ładnie umieszczony przycisk oznaczony **„Click Me.”** („Kliknij mnie”). Po dwukrotnym kliknięciu Word poprosi o włączenie makr (ponieważ kontrolki ActiveX są traktowane jako makra). Następnie możesz powiązać procedurę VBA z zdarzeniem `Click` przycisku.

---

## Przypadki brzegowe i wskazówki, które możesz przeoczyć

- **Format makro‑włączony**: Word wyłącza kontrolki ActiveX w zwykłych plikach `.docx`, chyba że użytkownik włączy makra. Jeśli potrzebujesz, aby przycisk działał od razu, rozważ zapis jako `.docm` (makro‑włączony) używając `doc.save(outputPath, SaveFormat.DOCM);`.
- **Kompatybilność**: Starsze wersje Worda (przed 2007) używają binarnego formatu `.doc`. Aspose.Words potrafi zapisywać w tym formacie, ale właściwości kontrolki mogą wyglądać nieco inaczej.
- **Ustawienia bezpieczeństwa**: W niektórych środowiskach korporacyjnych ActiveX jest zablokowane. Jeśli przycisk się nie wyświetla, sprawdź Centrum zaufania Word → Ustawienia ActiveX.
- **Wiele przycisków**: Potrzebujesz więcej niż jednego? Po prostu powtórz wywołanie `insertForms2OleControl` i dostosuj wartości `Left`/`Top` każdego przycisku. Trzymaj referencje do zwróconych obiektów, aby móc ustawiać indywidualne podpisy.
- **Stylizacja podpisu**: Podpis dziedziczy domyślną czcionkę. Aby ją zmienić, trzeba edytować underlying XML lub zastosować styl Word po wstawieniu — wykracza to poza zakres tego krótkiego przewodnika, ale jest możliwe przy użyciu API `ParagraphFormat` Aspose.Words.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia kod klasy Java. Skopiuj‑wklej go do swojego IDE, dostosuj ścieżkę wyjściową i naciśnij **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Oczekiwany wynik**: Po uruchomieniu w konsoli zostanie wypisana lokalizacja zapisu. Otwierając wygenerowany plik w Wordzie zobaczysz przycisk umieszczony mniej więcej w środku strony, oznaczony „Click Me”. Kliknięcie go wywoła standardowe zdarzenie kliknięcia ActiveX (musisz podpiąć makro VBA, aby zareagować).

---

## Podsumowanie

Teraz wiesz **jak wstawić ActiveX** kontrolki CommandButton do dokumentu Word programowo przy użyciu Aspose.Words oraz dokładnie **jak ustawić podpis przycisku**, pozycję i rozmiar kontrolki. To podejście eliminuje ręczną pracę w UI, integruje się czysto z automatycznymi generatorami raportów i daje pełną kontrolę nad

## Co warto nauczyć się dalej?


Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz krok‑po‑kroku wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}