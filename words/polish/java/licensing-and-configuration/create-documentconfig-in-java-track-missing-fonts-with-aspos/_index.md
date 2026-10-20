---
category: general
date: 2026-07-06
description: Utwórz DocumentConfig w Javie, aby śledzić brakujące czcionki przy użyciu
  Aspose.Words – kompletny, krok po kroku przewodnik dla programistów.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: pl
og_description: Utwórz DocumentConfig w Javie, aby śledzić brakujące czcionki przy
  użyciu Aspose.Words. Poznaj pełny przepływ pracy, od konfiguracji po obsługę ostrzeżeń.
og_title: Utwórz DocumentConfig w Javie – Śledź brakujące czcionki
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Utwórz DocumentConfig w Javie – Śledź brakujące czcionki za pomocą Aspose.Words
url: /pl/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz DocumentConfig w Javie – Śledź brakujące czcionki w Aspose.Words

**Utwórz DocumentConfig w Javie**, aby monitorować ostrzeżenia o podstawianiu czcionek podczas ładowania dokumentu Word. Zastanawiałeś się kiedyś, dlaczego niektóre znaki wyglądają dziwnie po otwarciu pliku DOCX? Najprawdopodobniej oryginalna czcionka nie jest zainstalowana na komputerze i Aspose.Words cicho ją zamienia. W tym samouczku pokażemy dokładnie, jak **śledzić brakujące czcionki**, aby nigdy nie zostać zaskoczonym nieoczekiwanym glifem.

Przejdziemy przez wszystko, czego potrzebujesz: konfigurację Maven/Gradle, kod tworzący `DocumentConfig`, własny `IWarningCallback`, który filtruje tylko alerty o podstawianiu czcionek, oraz szybki sposób logowania tych komunikatów. Po zakończeniu będziesz mieć działający przykład, który wypisuje każde ostrzeżenie o brakującej czcionce na konsolę (lub do pliku, jeśli wolisz).

---

## Czego się nauczysz

- Dlaczego `DocumentConfig` jest właściwym miejscem do przechwytywania zdarzeń podstawiania czcionek.  
- Jak **śledzić brakujące czcionki** bez zanieczyszczania logów niepowiązanymi ostrzeżeniami.  
- Pełny, gotowy do skopiowania program w Javie, który demonstruje tę technikę.  
- Wskazówki dotyczące rozszerzania rozwiązania — np. zapisywanie ostrzeżeń do bazy danych lub wysyłanie powiadomień e‑mail.

### Wymagania wstępne

| Wymaganie | Powód |
|-------------|--------|
| Java 8 lub nowsza | Aspose.Words for Java obsługuje JDK 8+. |
| Biblioteka Aspose.Words for Java (najnowsza wersja) | Udostępnia `DocumentConfig`, `IWarningCallback` itp. |
| IDE lub narzędzie budowania (IntelliJ, Eclipse, Maven/Gradle) | Do kompilacji i uruchomienia przykładu. |
| Plik DOCX odwołujący się do czcionek, których nie masz zainstalowanych | Aby zobaczyć ostrzeżenie w działaniu. |

Jeśli już masz projekt, po prostu dodaj zależność Aspose i możesz zaczynać.

---

## Krok 1: Dodaj Aspose.Words do swojego projektu

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Wskazówka:** Wersja próbna działa doskonale do testów, ale pamiętaj, aby zastosować licencję w środowisku produkcyjnym, aby usunąć znak wodny oceny.

---

## Krok 2: Utwórz DocumentConfig i zarejestruj Callback ostrzeżeń

Sedno rozwiązania znajduje się w tym fragmencie kodu. **Tworzymy DocumentConfig**, dołączamy własny `IWarningCallback` i instruujemy go, aby **śledził tylko brakujące czcionki**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Dlaczego to działa:** Gdy Aspose.Words analizuje dokument, generuje obiekty `WarningInfo` dla wszelkich nieprawidłowości. Dostarczając callback, przechwytujesz te ostrzeżenia *zanim* znikną w próżni. Warunek `if` zapewnia, że **śledzimy tylko brakujące czcionki**, ignorując inne ostrzeżenia, takie jak przestarzałe tagi czy nieobsługiwane funkcje.

---

## Krok 3: Uruchom przykład i obserwuj wynik

Umieść plik DOCX, który odwołuje się do czcionki, której nie masz (np. „Comic Sans MS” na systemie Linux). Uruchom program:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Powinieneś zobaczyć coś podobnego do:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Każda linia odpowiada brakującej czcionce, którą Aspose automatycznie zastąpił. Jeśli brak brakujących czcionek, program pozostaje cichy — dokładnie to, czego potrzebujesz dla czystego logu.

---

## Krok 4: Zachowaj listę brakujących czcionek (opcjonalnie)

Wypisywanie na konsolę jest przydatne w demonstracjach, ale w rzeczywistym serwisie prawdopodobnie będziesz przechowywać dane. Oto szybki sposób na zapisanie ostrzeżeń do pliku tekstowego.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Teraz każde zdarzenie brakującej czcionki dopisuje linię do `missing-fonts.log`. Możesz później przetworzyć ten plik, wprowadzić go do panelu monitoringu lub nawet wywołać alert, jeśli krytyczna czcionka zniknie z Twojego serwera.

---

## Krok 5: Typowe pułapki i jak ich unikać

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Brak ostrzeżeń, mimo że DOCX używa nieznanych czcionek | Callback nie został zarejestrowany lub `setWarningCallback` wywołano po załadowaniu dokumentu | Upewnij się, że `config.setWarningCallback(...)` jest wywoływane **przed** utworzeniem instancji `Document`. |
| Aplikacja wyłącza się z `NullPointerException` | `info.getDescription()` zwraca `null` dla niektórych rzadkich typów ostrzeżeń | Zabezpiecz się przed null: `String desc = info.getDescription(); if (desc != null) …` |
| Zbyt wiele niepowiązanych ostrzeżeń zalewa konsolę | Callback filtruje tylko `FONT_SUBSTITUTION`? | Sprawdź ponownie warunek `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Spowolnienie wydajności przy dużych partiach | Zapisywanie do pliku synchronicznie dla każdego ostrzeżenia | Zapisuj partiami lub użyj `BufferedWriter`, aby zmniejszyć obciążenie I/O. |

---

## Krok 6: Rozszerzanie rozwiązania – od konsoli do przedsiębiorstwa

- **Logowanie do bazy danych:** Zastąp `FileWriter` wstawianiem JDBC; przechowuj `documentName`, `missingFont` i `timestamp`.  
- **Alerty e‑mail:** Podłącz się do JavaMail; wyślij podsumowanie po przetworzeniu partii dokumentów.  
- **Własna logika podstawiania:** Zamiast pozwalać Aspose wybrać domyślną czcionkę, możesz załadować lokalną kolekcję czcionek za pomocą `FontSettings.setFontsFolder()` i ponownie uruchomić ładowanie, jeśli nastąpi podstawienie.

Te rozszerzenia zachowują podstawową ideę — **utworzyć DocumentConfig** i **śledzić brakujące czcionki** — niezmienioną, jednocześnie skalując rozwiązanie do potrzeb produkcyjnych.

---

## Zakończenie

Masz teraz solidny, gotowy do skopiowania wzorzec do **tworzenia DocumentConfig** w Javie i używania go do **śledzenia brakujących czcionek** w Aspose.Words. Podejście jest lekkie, wymaga tylko kilku linii kodu i daje pełną kontrolę nad tym, jak obsługiwane są ostrzeżenia o podstawianiu czcionek. Niezależnie od tego, czy tworzysz usługę konwersji dokumentów, automatyczny generator raportów, czy narzędzie audytu zgodności, dokładna znajomość brakujących czcionek może zaoszczędzić godziny debugowania.

Kolejne kroki? Spróbuj zamienić wyjście konsoli na ustrukturyzowany log JSON lub zintegrować callback z mikrousługą Spring Boot, która przetwarza przesyłane pliki w czasie rzeczywistym. Jeśli napotkasz jakiekolwiek przypadki brzegowe — np. własną czcionkę OpenType, której Aspose nie potrafi sparsować — zostaw komentarz poniżej; wspólnie znajdziemy rozwiązanie.

Miłego kodowania i niech Twoje PDF‑y zawsze renderują się z oczekiwanymi czcionkami!

## Co powinieneś nauczyć się dalej?

Następujące samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Używanie czcionek w Aspose.Words dla Java](/words/english/java/using-document-elements/using-fonts/)
- [Dostosowywanie kolorów motywu i czcionek w Aspose.Words Java: Kompletny przewodnik](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Jak tworzyć dokumenty PDF za pomocą Aspose.Words dla Java | API przetwarzania dokumentów](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}