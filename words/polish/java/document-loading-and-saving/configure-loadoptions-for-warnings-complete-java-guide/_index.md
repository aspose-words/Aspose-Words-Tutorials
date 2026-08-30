---
category: general
date: 2026-06-30
description: Skonfiguruj LoadOptions dla ostrzeżeń w Aspose.Words Java. Dowiedz się,
  jak ustawić wywołanie zwrotne ostrzeżeń dla podstawiania czcionek i innych ostrzeżeń
  związanych z opcjami ładowania.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: pl
og_description: Skonfiguruj LoadOptions dla ostrzeżeń w Aspose.Words Java. Ten przewodnik
  pokazuje, jak przechwycić alerty o podstawianiu czcionek przy użyciu wywołania zwrotnego
  ostrzeżenia.
og_title: Konfiguracja LoadOptions dla ostrzeżeń – samouczek Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Skonfiguruj LoadOptions dla ostrzeżeń – Kompletny przewodnik po Javie
url: /pl/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konfiguracja LoadOptions dla ostrzeżeń – Kompletny przewodnik Java

Czy kiedykolwiek potrzebowałeś **skonfigurować LoadOptions dla ostrzeżeń** przy otwieraniu dokumentu Word przy użyciu Aspose.Words for Java? Nie jesteś sam. Wielu programistów napotyka problem, gdy brakująca czcionka jest cicho zamieniana, co powoduje, że końcowy PDF wygląda niezgodnie z marką. Dobra wiadomość? Dodając **callback ostrzeżeń w Javie** do swojego `LoadOptions`, możesz przechwycić każde powiadomienie o zamianie czcionki w momencie jego wystąpienia.

W tym samouczku przeprowadzimy Cię przez praktyczny przykład, który nie tylko pokaże, jak ustawić callback, ale także wyjaśni *dlaczego* każdy element ma znaczenie. Po zakończeniu będziesz w stanie **obsługiwać ostrzeżenia o czcionkach**, logować je lub nawet zamieniać czcionki w locie — bez domysłów.

## Co zdobędziesz po przeczytaniu

- W pełni działający program w Javie, który wypisuje każde ostrzeżenie o zamianie czcionki.  
- Zrozumienie mechaniki **zastępowania czcionek w Aspose.Words**.  
- Wskazówki dotyczące dostosowywania obsługi ostrzeżeń w większych projektach.  
- Wgląd w **opcje ładowania dokumentu** i momenty, w których warto je modyfikować.

> **Wymagania wstępne:** Java 8+ oraz biblioteka Aspose.Words for Java (wersja 23.9 lub nowsza). Nie są potrzebne inne zewnętrzne zależności.

---

## Krok 1: Skonfiguruj LoadOptions dla ostrzeżeń

Pierwszą rzeczą, której potrzebujesz, jest instancja `LoadOptions`, która wie, że ma raportować ostrzeżenia. Pomyśl o `LoadOptions` jako o skrzynce narzędziowej, którą przekazujesz Aspose.Words zanim jeszcze otworzy plik.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Dlaczego to ważne:**  
`LoadOptions` kontroluje, w jaki sposób biblioteka odczytuje dokument. Przypisując `IWarningCallback`, informujesz Aspose.Words, aby wywołał Twój kod za każdym razem, gdy napotka coś godnego uwagi — np. brakującą czcionkę. Bez tego biblioteka cicho podmieni czcionkę i nigdy się o tym nie dowiesz.

> **Porada:** Jeśli chcesz przechwycić *wszystkie* ostrzeżenia, usuń warunek `if`. Na razie skupiamy się na problemach z czcionkami, ponieważ są one najczęstszym źródłem niespodziewanych zmian układu.

---

## Krok 2: Załaduj dokument przy użyciu skonfigurowanych opcji

Teraz, gdy callback jest gotowy, załaduj swój plik `.docx` (lub inny obsługiwany format) przy użyciu tego samego `LoadOptions`. To właśnie tutaj **opcje ładowania dokumentu** wchodzą w życie.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Co się dzieje w tle:**  
Podczas parsowania `input.docx` Aspose.Words przeszukuje tabele czcionek. Jeśli czcionka użyta w dokumencie nie jest zainstalowana na maszynie hosta, silnik generuje ostrzeżenie `FONT_SUBSTITUTION`, które natychmiast wywołuje wcześniej zdefiniowany callback.

---

## Krok 3: Zapisz dokument – ostrzeżenia zostały już wypisane

Zapisanie dokumentu jest proste, ale to moment, w którym możesz zweryfikować, czy callback został wywołany poprawnie. Wszystkie ostrzeżenia są wypisywane podczas kroku ładowania, więc operacja zapisu to jedynie sprzątanie.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Oczekiwany wynik w konsoli:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Jeśli nic się nie pojawi, oznacza to, że dokument używał wyłącznie zainstalowanych czcionek lub callback nie został poprawnie podłączony — sprawdź ponownie Krok 1.

---

## Krok 4: Rozszerz callback, aby **elegancko obsługiwać ostrzeżenia o czcionkach**

Wypisywanie do konsoli jest w porządku w demonstracjach, ale w kodzie produkcyjnym często potrzebna jest bardziej rozbudowana obsługa: logowanie do pliku, wysyłanie alertów lub nawet programowa zamiana czcionek.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Dlaczego warto to zrobić:**  
Plik logu daje Ci możliwość retrospektywnej analizy, szczególnie przy przetwarzaniu partii dokumentów. Opcjonalny blok zamiany pokazuje, jak **skonfigurować LoadOptions dla ostrzeżeń** *i* interweniować, aby wymusić politykę czcionek korporacyjnych.

---

## Zaawansowane: Kontrolowanie innych scenariuszy **zastępowania czcionek w Aspose.Words**

Callback ostrzeżeń nie ogranicza się tylko do brakujących czcionek. Możesz także przechwycić:

- **Nieobsługiwane znaki Unicode** (`WarningType.UNSUPPORTED_CHAR`).  
- **Problemy ze skryptami złożonymi** (`WarningType.COMPLEX_SCRIPT`).

Wystarczy rozbudować instrukcję `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Dzięki temu Twoje rozwiązanie będzie odporne na dokumenty wielojęzyczne, co jest częstym przypadkiem w aplikacjach globalnych.

---

## Pełny, działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Wklej go do dowolnego IDE Javy, zamień znaczniki `YOUR_DIRECTORY` na odpowiednie ścieżki i naciśnij *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Oczekiwany rezultat

- Konsola wypisuje wszystkie ostrzeżenia o zamianie czcionek.  
- `font-warnings.log` zawiera listę z sygnaturą czasową (jeśli pozostawiłeś opcjonalne logowanie).  
- `output.docx` zostaje zapisany z zamienionymi czcionkami, zgodnie z określonym fallbackiem.

---

## Typowe pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Brak ostrzeżeń** | Callback nie został podłączony lub dokument używa wyłącznie zainstalowanych czcionek. | Upewnij się, że `loadOptions.setWarningCallback(...)` jest wywoływane *przed* załadowaniem dokumentu. |
| **FileNotFoundException** przy `input.docx` | Ścieżka jest nieprawidłowa lub plik nie znajduje się w projekcie. | Użyj ścieżki bezwzględnej lub umieść plik w folderze zasobów projektu. |
| **Spowolnienie wydajności** przy przetwarzaniu tysięcy dokumentów | Nadmierne logowanie na dysk przy każdym ostrzeżeniu. | Buforuj logi i zapisuj je partiami, albo ogranicz logowanie do krytycznych ostrzeżeń. |
| **Nieoczekiwana zamiana czcionki** mimo ustawionego fallbacku | Tabela zamiany nie została zastosowana wystarczająco wcześnie. | Ustawienia zamiany czcionek **przed** załadowaniem dokumentu lub użyj globalnie `FontSettings.setSubstitutionSettings`. |

---

## Kolejne kroki

Teraz, gdy opanowałeś **konfigurację LoadOptions dla ostrzeżeń**, rozważ następujące tematy:

- **Przetwarzanie wsadowe**: iteracja po katalogu dokumentów i agregowanie wszystkich ostrzeżeń czcionek w jednym raporcie.  
- **Niestandardowi dostawcy czcionek**: ładowanie czcionek z udziału sieciowego lub zasobów osadzonych zamiast lokalnego systemu operacyjnego.  
- **Integracja z frameworkami logowania** takimi jak Log4j, aby uzyskać poziom przedsiębiorczej śledzenia.  
- Eksploracja innych **opcji ładowania dokumentu**, takich jak wykrywanie `LoadFormat` czy obsługa `Password` dla plików zabezpieczonych.

Wszystkie te zagadnienia opierają się na tym samym wzorcu — tworzysz obiekt `LoadOptions`, podłączasz odpowiednie callbacki i pozwalasz Aspose.Words wykonać ciężką pracę.

---

## Podsumowanie

Zagłębiliśmy się w to, jak **skonfigurować LoadOptions dla ostrzeżeń** w Aspose.Words dla Javy, jak ustawić **callback ostrzeżeń w Javie** i jak wykorzystać te informacje do **inteligentnej obsługi ostrzeżeń o czcionkach**. Kod jest zwięzły, koncepcje jasne, a Ty masz solidną bazę do rozszerzenia obsługi ostrzeżeń na inne scenariusze, takie jak nieobsługiwane znaki czy skrypty złożone.

Wypróbuj to, dopasuj tabelę zamiany do czcionek swojej marki i pożegnaj się z cichymi zamianami czcionek. Powodzenia w kodowaniu!

--- 

![Diagram showing the flow of configuring LoadOptions for warnings, loading a document, capturing font substitution events, and saving the output](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## Co powinieneś nauczyć się dalej?


Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}