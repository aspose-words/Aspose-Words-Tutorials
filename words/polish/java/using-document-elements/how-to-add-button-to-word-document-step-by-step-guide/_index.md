---
category: general
date: 2026-07-20
description: Jak dodać przycisk do dokumentu Word przy użyciu Aspose.Words. Dowiedz
  się, jak w kilka minut wstawić przycisk Forms2OleControl za pomocą DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: pl
lastmod: 2026-07-20
og_description: Jak dodać przycisk do dokumentu Word przy użyciu Aspose.Words. Skorzystaj
  z tego praktycznego przewodnika, aby osadzić przycisk CommandButton Forms2OleControl
  przy użyciu Javy.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Jak dodać przycisk do dokumentu Word – Kompletny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Jak dodać przycisk do dokumentu Word – przewodnik krok po kroku
url: /pl/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać przycisk do dokumentu Word – Kompletny samouczek Aspose.Words

Zastanawiałeś się kiedyś **jak dodać przycisk do dokumentu Word** bez otwierania interfejsu i klikania? Nie jesteś jedyny. Wielu programistów musi programowo osadzać interaktywne kontrolki — pomyśl o przycisku „Submit” w szablonie, który później wypełnia użytkownik końcowy. Dobre wieści? Dzięki Aspose.Words for Java możesz to zrobić w kilku linijkach.

W tym samouczku przeprowadzimy Cię przez dokładne kroki wstawienia `Forms2OleControl` typu **CommandButton** przy użyciu `DocumentBuilder`. Po zakończeniu będziesz mieć gotowy do użycia plik `.docx`, który wyświetla przycisk „Click Me”. Bez tajemnic, tylko przejrzysty kod i wyjaśnienie każdej linii.

## Czego się nauczysz

- Jak utworzyć nowy dokument Word od podstaw.
- Jak używać **DocumentBuilder** do umieszczenia **Forms2OleControl**.
- Dlaczego należy ustawić podpis przycisku i rozmiar w taki sposób, jak to robimy.
- Jak zapisać i zweryfikować wynik.
- Typowe pułapki (np. brakujące biblioteki, nieobsługiwane typy kontrolek) i jak ich uniknąć.

**Wymagania wstępne** – Potrzebujesz Java 8+ (lub nowszej) oraz biblioteki Aspose.Words for Java (wersja 23.12 lub późniejsza). IDE takie jak IntelliJ IDEA lub Eclipse ułatwią pracę, ale każdy edytor tekstu się sprawdzi.

---

## Krok 1: Skonfiguruj projekt i zaimportuj zależności

Zanim jakikolwiek kod zostanie uruchomiony, Maven (lub Gradle) musi wiedzieć, skąd pobrać Aspose.Words. Dodaj ten fragment do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Jeśli wolisz Gradle, odpowiednik wygląda tak:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Wskazówka:** Używaj najnowszej wersji; starsze wersje mogą nie zawierać API `Forms2OleControl`.

Gdy zależność zostanie rozwiązana, możesz przystąpić do pisania kodu Java.

---

## Krok 2: Utwórz nowy dokument i uzyskaj DocumentBuilder

`Document` reprezentuje cały pakiet `.docx`, natomiast `DocumentBuilder` jest pędzlem, którym malujesz zawartość. Traktuj `DocumentBuilder` jako „kursor”, który wie, gdzie ma się znaleźć kolejny element.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:** Inicjalizacja nowego `Document` daje czyste płótno. Builder automatycznie wskazuje pierwszy akapit, więc nie musisz ręcznie zarządzać sekcjami czy stronami.

---

## Krok 3: Wstaw Forms2OleControl typu CommandButton

Teraz pojawia się gwiazda programu: `insertForms2OleControl`. Ta metoda tworzy kontrolkę OLE (Object Linking and Embedding), którą Word traktuje jako element formularza. Przekażemy trzy argumenty:

1. `Forms2OleControlType.COMMANDBUTTON` – informuje Word, że chcemy przycisk.
2. `100` – szerokość w punktach (≈1,39 cala).
3. `30` – wysokość w punktach (≈0,42 cala).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Jak to działa:** W tle Aspose.Words tworzy odpowiedni XML w części `word/document.xml`, odwołując się do obiektu OLE. Podane wymiary są respektowane przez silnik układu Worda, więc przycisk pojawia się dokładnie tam, gdzie znajduje się kursor buildera.

---

## Krok 4: Ustaw podpis (tekst) na przycisku

Przycisk bez etykiety jest mylący — wyobraź sobie cichy przycisk windy. Metoda `setCaption` ustawia widoczny tekst:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Możesz zmienić podpis na dowolny: „Submit”, „Approve” lub nawet na przetłumaczony ciąg. Podpis jest przechowywany w właściwościach obiektu OLE, więc Word wyświetli go natywnie.

---

## Krok 5: Zapisz dokument i zweryfikuj wynik

Na koniec zapisz plik na dysku. Wybierz folder, do którego masz prawo zapisu; w przeciwnym razie napotkasz `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Otwórz `button-demo.docx` w Microsoft Word. Powinieneś zobaczyć przycisk oznaczony **Click Me** umieszczony na górze dokumentu. Kliknięcie go w Wordzie wywoła domyślne zachowanie OLE (zazwyczaj komunikat zastępczy, chyba że powiążesz makro).

---

## Typowe przypadki brzegowe i jak sobie z nimi radzić

| Sytuacja | Dlaczego się dzieje | Rozwiązanie |
|-----------|----------------|-----|
| **Brak typu `Forms2OleControl`** | Starsze wersje Aspose.Words nie udostępniały tego wyliczenia. | Zaktualizuj do wersji 23.12+ lub nowszej. |
| **Przycisk wyświetla się jako obraz** | Ustawienia zabezpieczeń Worda blokują kontrolki OLE. | Włącz „Zaufaj dostępowi do modelu obiektu projektu VBA” w Centrum zaufania lub użyj pliku `.docm` z włączonymi makrami. |
| **Nieprawidłowy rozmiar** | Mieszanie punktów i pikseli. | Pamiętaj, że 1 punkt = 1/72 cala. Dostosuj liczby odpowiednio. |
| **Zapis zgłasza `FileNotFoundException`** | Ścieżka nie istnieje. | Upewnij się, że katalog (`output/`) został utworzony przed `doc.save`. Użyj `new File("output").mkdirs();`. |

---

## Rozszerzanie przykładu: Dodawanie wielu przycisków lub innych kontrolek

Jeśli potrzebujesz więcej niż jednego przycisku, po prostu przesuń kursor buildera za pomocą `builder.moveTo` lub `builder.writeln()` przed ponownym wywołaniem `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Możesz także wstawić **CheckBox**, **ComboBox** lub **ListBox**, zamieniając `Forms2OleControlType.COMMANDBUTTON` na odpowiednią wartość wyliczenia (`CHECKBOX`, `COMBOBOX` itd.). Te same parametry szerokości/wysokości mają zastosowanie.

---

## Jak to pasuje do większych przepływów automatyzacji Worda

- **Generowanie szablonów:** Stwórz szablon umowy zawierający przycisk „Approve” do dalszego zatwierdzania.
- **Raportowanie:** Wygeneruj codzienny raport z przyciskiem „Refresh Data”, który wywołuje makro.
- **Dystrybucja formularzy:** Wyślij kwestionariusz z wstępnie wypełnionymi interaktywnymi kontrolkami.

Wszystkie te scenariusze korzystają z podejścia **automatyzacji Worda**, które przedstawiliśmy. Osadzając kontrolki programowo, eliminujesz ręczną edycję i zmniejszasz liczbę błędów ludzkich.

---

## Pełny kod źródłowy (gotowy do kopiowania i wklejania)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Oczekiwany wynik:** Po otwarciu `output/button-demo.docx` w Microsoft Word zobaczysz dwa przyciski — „Click Me” i „Submit” — ułożone pionowo na górze pliku.

---

## Zakończenie

Odpowiedzieliśmy na pytanie **jak dodać przycisk do dokumentu Word** przy użyciu Aspose.Words for Java, krok po kroku. Zaczynając od pustego `Document`, wykorzystaliśmy **DocumentBuilder** do wstawienia `Forms2OleControl` typu **CommandButton**, ustawiliśmy przyjazny podpis i zapisaliśmy wynik. Podejście skaluje się na wiele kontrolek i płynnie integruje się z szerszymi pipeline’ami **automatyzacji Worda**.

Gotowy na kolejne wyzwanie? Spróbuj zamienić przycisk na **CheckBox** lub podłącz makro, które zareaguje, gdy użytkownik kliknie przycisk w pliku `.docm`. Ten sam schemat się sprawdza — wystarczy zmienić wyliczenie i dostosować podpis.

Jeśli napotkasz jakiekolwiek problemy, sprawdź ponownie wersję biblioteki i uprawnienia do folderu wyjściowego. Śmiało zostaw komentarz poniżej z pytaniami lub podziel się własnym przypadkiem użycia. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularzy i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words dla Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wstawianie obrazu w linii w dokumencie Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Tworzenie grupy kształtów w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}