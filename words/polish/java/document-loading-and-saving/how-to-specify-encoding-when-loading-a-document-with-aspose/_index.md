---
category: general
date: 2026-10-26
description: Dowiedz się, jak określić kodowanie w Javie przy użyciu LoadOptions.
  Ten przewodnik obejmuje kodowanie znaków, metodę setEncoding oraz opcje ładowania
  dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: pl
lastmod: 2026-10-26
og_description: Jak określić kodowanie w Javie przy użyciu Aspose.Words. Przejdź do
  tego pełnego samouczka, aby wczytywać dokumenty z właściwym zestawem znaków.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Jak określić kodowanie w Javie przy użyciu Aspose.Words – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Jak określić kodowanie przy ładowaniu dokumentu przy użyciu Aspose.Words dla
  Javy
url: /pl/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak określić kodowanie przy ładowaniu dokumentu przy użyciu Aspose.Words for Java

Jeśli potrzebujesz **jak określić kodowanie** dla pliku źródłowego w Javie, ten samouczek pokaże Ci dokładne kroki. Niezależnie od tego, czy dokument używa Big5, UTF‑8, czy innego zestawu znaków, możesz kontrolować proces odczytu za pomocą `LoadOptions`. Po zakończeniu przewodnika zrozumiesz, dlaczego kodowanie znaków ma znaczenie, jak zastosować metodę `setEncoding` oraz jak zweryfikować, że dokument został poprawnie załadowany.

Ładowanie dokumentu z odpowiednim kodowaniem znaków zapobiega zniekształconemu tekstowi i zapewnia, że treść wielojęzyczna jest wyświetlana zgodnie z zamierzeniami. Ten samouczek obejmuje:

* Rolę **kodowania znaków w Javie** przy odczytywaniu plików.
* Jak skonfigurować **kodowanie LoadOptions** dla Aspose.Words.
* Praktyczny kod, który możesz skopiować do swojego projektu.
* Typowe pułapki, takie jak niepasujące kodowania i jak je rozwiązywać.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Java Development Kit (JDK) 8 lub nowszy.
* Maven lub Gradle do zarządzania zależnościami.
* Aspose.Words for Java 23.10 lub nowszy (wersja użyta w tym przewodniku).
* Przykładowy dokument tekstowy (`input.doc`) zapisany w żądanym kodowaniu (np. Big5).

Nie potrzebujesz żadnych dodatkowych bibliotek; przykład używa wyłącznie podstawowego API Aspose.Words.

## Krok 1: Dodaj Aspose.Words do swojego projektu

Jeśli używasz Maven, dodaj następującą zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Dla Gradle, umieść tę linię w swoim `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Dołączenie biblioteki udostępnia klasy `LoadOptions`, `Document` i `Encoding`.

## Krok 2: Utwórz instancję `LoadOptions`

`LoadOptions` pozwala dostosować sposób, w jaki Aspose.Words otwiera plik. Utworzenie obiektu jest pierwszą częścią **jak określić kodowanie**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Obiekt `LoadOptions` rozpoczyna z ustawieniami domyślnymi. W następnym kroku dostosujesz jego właściwości.

## Krok 3: Ustaw żądane kodowanie znaków

Metoda `setEncoding` definiuje **kodowanie znaków w Javie**, którego loader powinien używać. W tym przykładzie wybieramy stronę kodową Big5, która jest powszechna dla tradycyjnych chińskich plików tekstowych.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Dlaczego to ważne*: Jeśli bajty pliku zostaną zinterpretowane przy użyciu niewłaściwej strony kodowej, znaki pojawią się jako znaki zapytania lub bełkot. Wywołując jawnie `setEncoding`, informujesz Aspose.Words, aby dekodował strumień bajtów przy użyciu tabeli mapowania Big5.

Możesz zamienić `"Big5"` na dowolną nazwę zestawu znaków rozpoznawaną przez Javę, taką jak `"UTF-8"`, `"ISO-8859-1"` lub `"Windows-1252`. Metoda rzuca `UnsupportedEncodingException`, jeśli nazwa jest nieprawidłowa, więc w kodzie produkcyjnym warto przechwycić ten wyjątek.

## Krok 4: Załaduj dokument z skonfigurowanymi opcjami

Teraz, gdy **kodowanie LoadOptions** jest ustawione, przekaż opcje do konstruktora `Document`. Ten krok kończy podstawowy przepływ **jak określić kodowanie**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Zastąp `YOUR_DIRECTORY` absolutną lub względną ścieżką do swojego pliku. Instancja `Document` zawiera teraz w pełni przetworzoną treść, respektując podane kodowanie.

## Krok 5: Zweryfikuj, że tekst ładuje się poprawnie

Szybka weryfikacja pomaga upewnić się, że kodowanie zostało zastosowane zgodnie z oczekiwaniami. Możesz wyodrębnić tekst dokumentu i wydrukować go w konsoli:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Jeśli konsola wyświetla czytelne chińskie znaki (lub język, którego oczekujesz), kodowanie zakończyło się sukcesem. Jeśli nadal widzisz zniekształcony wynik, dokładnie sprawdź kodowanie oryginalnego pliku i potwierdź, że nazwa zestawu znaków jest dokładnie zgodna.

## Obsługa typowych przypadków brzegowych

### 5.1 Ładowanie z `InputStream`

Czasami otrzymujesz dokument jako strumień (np. z usługi internetowej). Nadal możesz kontrolować kodowanie, przekazując strumień razem z `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Te same **opcje ładowania dokumentu** mają zastosowanie, a wywołanie `setEncoding` pozostaje niezmienione.

### 5.2 Fallback, gdy kodowanie jest nieznane

Jeśli nie możesz określić zestawu znaków pliku źródłowego, możesz spróbować biblioteki wykrywającej (takiej jak ICU4J) przed ustawieniem kodowania. Gdy masz przypuszczenie, wywołaj `setEncoding` z tą wartością. Takie podejście zmniejsza ryzyko nieprawidłowo zdekodowanego tekstu.

### 5.3 Radzenie sobie z nieobsługiwanymi kodowaniami

Java obsługuje szeroki zakres stron kodowych, ale niektóre starsze kodowania mogą być nieobecne. W takim przypadku rozważ konwersję pliku do UTF‑8 zewnętrznie (np. przy użyciu `iconv`) przed jego załadowaniem przy pomocy Aspose.Words. Po konwersji możesz pominąć wywołanie `setEncoding`, ponieważ UTF‑8 jest domyślne dla większości nowoczesnych API.

## Porada: Ponowne użycie `LoadOptions` przy przetwarzaniu wsadowym

Jeśli musisz załadować wiele dokumentów, które używają tego samego zestawu znaków, utwórz jedną instancję `LoadOptions` i używaj jej ponownie:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Ponowne użycie obiektu zmniejsza narzut związany z tworzeniem obiektów i zapewnia spójne kodowanie w całej partii.

## Pełny działający przykład

Poniżej znajduje się kompletny program, który zawiera wszystkie kroki, niezbędne importy i obsługuje potencjalne wyjątki.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Oczekiwany wynik** (zakładając, że plik źródłowy zawiera chiński tekst zakodowany w Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Jeśli wynik wyświetla nieczytelne symbole, sprawdź ponownie nazwę zestawu znaków lub zweryfikuj oryginalne kodowanie pliku.

## Najczęściej zadawane pytania

**Czy to działa z innymi formatami dokumentów (DOCX, RTF, HTML)?**  
Tak. Ten sam obiekt `LoadOptions` ma zastosowanie do każdego formatu obsługiwanego przez Aspose.Words. Jedynym wymogiem jest, aby podstawowy plik faktycznie używał określonego zestawu znaków.

**Co jeśli muszę zmienić kodowanie po załadowaniu dokumentu?**  
Kodowanie wpływa tylko na fazę odczytu. Gdy obiekt `Document` istnieje, jego wewnętrzna reprezentacja Unicode jest niezależna od pierwotnego zestawu znaków. Aby zmienić kodowanie wyjściowe, dostosuj `SaveOptions` podczas zapisywania pliku.

**Czy mogę użyć tego podejścia z innymi bibliotekami (np. Apache POI)?**  
Apache POI samodzielnie obsługuje wykrywanie zestawu znaków dla starszych formatów binarnych, ale koncepcja podawania zestawu znaków loaderowi jest podobna. Dla Aspose.Words, `LoadOptions` jest oficjalnym sposobem kontrolowania **jak określić kodowanie**.

## Zakończenie

Teraz wiesz **jak określić kodowanie** przy ładowaniu dokumentu przy użyciu Aspose.Words for Java. Tworząc obiekt `LoadOptions`, wywołując metodę `setEncoding` i przekazując opcje do konstruktora `Document`, zapewniasz prawidłową interpretację bajtów pliku. Ta praktyka eliminuje zniekształcony tekst, wspiera treść wielojęzyczną i integruje się płynnie z przetwarzaniem wsadowym lub przepływami opartymi na strumieniach.

Zbadaj powiązane tematy, takie jak **opcje ładowania dokumentów**, **zapisywanie z określonymi kodowaniami** oraz **obsługa Unicode w Javie**, aby pogłębić swoją biegłość w przetwarzaniu tekstu. Eksperymentuj z różnymi nazwami zestawów znaków, łącz podejście z konwersją do PDF lub zintegrować je z usługą sieciową przyjmującą pliki w różnych kodowaniach.

Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}