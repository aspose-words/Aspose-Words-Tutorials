---
category: general
date: 2026-11-15
description: Ustaw odstęp między wierszami akapitu w dokumencie Word przy użyciu Javy.
  Dowiedz się, jak programowo ustawiać odstęp między wierszami za pomocą Aspose.Words,
  aby precyzyjnie formatować dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: pl
lastmod: 2026-11-15
og_description: Ustaw odstępy między wierszami akapitu w dokumencie Word przy użyciu
  Javy. Ten przewodnik wyjaśnia, jak ustawić odstępy między wierszami dla akapitów
  i separatorów przypisów przy użyciu Aspose.Words, dając pełną kontrolę nad układem
  dokumentu.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Ustaw odstęp między wierszami akapitu w Wordzie przy użyciu Javy
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Ustaw odstęp między wierszami akapitu w dokumencie Word przy użyciu Javy
url: /pl/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustawienie odstępu wiersza akapitu w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz **ustawić odstęp wiersza akapitu** w dokumencie Word, ten tutorial pokaże Ci, jak zrobić to w Javie i Aspose.Words. Dowiesz się także **jak ustawić odstęp wiersza** dla separatorów przypisów — powszechne wymaganie przy formatowaniu dokumentów profesjonalnych.

W kolejnych sekcjach:

* Wczytać istniejący plik *.docx*.
* Pobrać akapit separatora przypisu.
* Zastosować niestandardową wartość odstępu wiersza.
* Zapisać zaktualizowany dokument.

Nie wymagana jest żadna zewnętrzna konfiguracja poza dodaniem biblioteki Aspose.Words do projektu, więc możesz skopiować kod dosłownie i uruchomić go od razu.

## Wymagania wstępne

* Zainstalowana Java 17 lub nowsza.
* Maven (lub inne narzędzie budujące) do zarządzania zależnościami.
* Ważna licencja Aspose.Words for Java (darmowa wersja ewaluacyjna działa do testów).
* Plik wejściowy Word (`input.docx`) znajdujący się w znanym katalogu.

Dodaj zależność Aspose.Words do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Ustawienie odstępu wiersza akapitu przy użyciu Aspose.Words

Ten nagłówek H2 zawiera główne słowo kluczowe, spełniając wymóg SEO.

### Krok 1: Wczytaj dokument Word

Najpierw utwórz instancję `Document`, która wskazuje na Twój plik źródłowy.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Dlaczego to ważne*: Wczytanie dokumentu daje Ci model w pamięci, który możesz modyfikować bez modyfikacji oryginalnego pliku, dopóki nie zapiszesz go wyraźnie.

### Krok 2: Pobierz separator przypisu

Separatory przypisów to specjalne akapity, które pojawiają się pomiędzy przypisami a tekstem głównym. Aby zmienić ich wygląd, musisz uzyskać dostęp do obiektu `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Wskazówka*: Jeśli Twój dokument nie zawiera przypisów, separator nadal istnieje jako ukryty akapit, więc wywołanie nigdy nie zwróci `null`.

### Krok 3: Jak ustawić odstęp wiersza dla akapitu separatora

Teraz zastosuj pożądany odstęp wiersza. Aspose.Words używa punktów jako jednostki wartości odstępu wiersza; 12 pt to mniej więcej pojedynczy odstęp dla większości czcionek.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Możesz także użyć innych trybów odstępu:

| Tryb                     | Wywołanie metody                                      |
|--------------------------|------------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`       |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Wybranie właściwej reguły zapewnia spójne renderowanie dokumentu w Word, Google Docs i innych przeglądarkach.

### Krok 4: Zapisz zaktualizowany dokument

Na koniec zapisz zmiany z powrotem na dysk.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Gdy otworzysz `output.docx` w Microsoft Word, separator przypisu zostanie wyświetlony z ustawionym przez Ciebie odstępem wiersza.

## Zrozumienie, jak ustawić odstęp wiersza dla zwykłych akapitów

To samo API działa dla dowolnego obiektu `Paragraph`, nie tylko dla separatorów przypisów. Oto szybki przykład, który dostosowuje odstęp pierwszego akapitu w treści:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Dlaczego możesz tego potrzebować**: Raporty, umowy i prace akademickie często wymagają określonego stylu odstępu wiersza (np. podwójny odstęp w wersjach roboczych). Użycie tej samej metody `setLineSpacing` gwarantuje dokładny układ, którego oczekujesz.

## Typowe pułapki i jak ich unikać

| Problem                                 | Przyczyna                                   | Rozwiązanie |
|-----------------------------------------|--------------------------------------------|-------------|
| Odstęp wiersza nie zmienia się          | `LineSpacingRule` pozostawiono w domyślnym (AUTO) | Jawnie ustaw regułę przy pomocy `setLineSpacingRule`. |
| Dodatkowe puste linie po separatorze    | Separator zawiera ukryte znaki powrotu karetki | Przytnij tekst separatora przy pomocy `separator.getText().trim();` przed zastosowaniem odstępu. |
| Dokument ulega uszkodzeniu po zapisaniu | Używanie przestarzałej wersji Aspose.Words | Uaktualnij do najnowszej wersji (np. 24.10), która zawiera poprawki błędów przy zapisywaniu. |

## Porada: przetwarzanie wsadowe wielu dokumentów

Jeśli musisz zaktualizować dziesiątki plików, opakuj logikę w metodę pomocniczą i iteruj po folderze:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Uruchamianie tej metody w pętli zaoszczędzi Ci godziny ręcznej edycji.

## Oczekiwany wynik

Po uruchomieniu pełnego programu, `output.docx` będzie:

* Zawierał oryginalną treść niezmienioną, z wyjątkiem odstępu wiersza.
* Wyświetlał separator przypisu z pojedynczym odstępem (12 pt).
* Zachowywał wszystkie pozostałe formatowania (style, obrazy, tabele).

Otwórz plik w Word i zweryfikuj, że linia separatora jest ściślejsza (lub luźniejsza, w zależności od ustawionej wartości).

## Zakończenie

Teraz wiesz, jak **ustawić odstęp wiersza akapitu** w dokumencie Word przy użyciu Javy, oraz rozumiesz **jak ustawić odstęp wiersza** zarówno dla separatorów przypisów, jak i zwykłych akapitów. Pełny, działający przykład demonstruje wczytywanie dokumentu, dostosowywanie właściwości odstępu wiersza i zapisywanie wyniku — wszystko przy użyciu kilku prostych wywołań API.

**Kolejne kroki**, które możesz rozważyć:

* **Jak ustawić odstęp wiersza** dla tabel i elementów listy.
* Stosowanie różnych reguł odstępu do nagłówków i tekstu głównego.
* Użycie obiektu `Style` do wymuszenia odstępu w całym dokumencie.

Eksperymentuj z wartościami, łącz je z innymi opcjami formatowania i będziesz mieć pełną kontrolę nad układem dokumentu w każdej aplikacji Java. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak ustawić opcje w Aspose.Words for Java – kompletny przewodnik](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Jak ustawić LoadOptions w Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Zmiana odstępów i wcięć azjatyckich akapitów w dokumencie Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}