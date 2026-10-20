---
date: '2026-01-14'
description: Dowiedz się, jak zresetować numerację stron w Aspose.Words Java oraz
  używać LayoutCollector do wyodrębniania danych paginacji, aktualizacji układu strony
  i renderowania stron jako obrazów.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Ponowne numerowanie stron w Aspose.Words Java – LayoutCollector i LayoutEnumerator
url: /pl/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ponowne numerowanie stron w Aspose.Words Java – LayoutCollector i LayoutEnumerator

## Wprowadzenie

Czy masz problem z **ponownym numerowaniem stron** w dużych dokumentach opartych na Javie, jednocześnie potrzebując analizować paginację lub renderować strony jako obrazy? Dzięki **Aspose.Words for Java** możesz wykorzystać `LayoutCollector` i `LayoutEnumerator`, aby nie tylko ponownie numerować strony, ale także **wyodrębnić dane paginacji**, **zaktualizować układ strony** i **renderować strony jako obrazy** do podglądów lub PDF‑ów. Ten przewodnik przeprowadzi Cię przez każdy krok, od konfiguracji biblioteki po implementację callbacków, które dają pełną kontrolę nad renderowaniem dokumentu.

**Czego się nauczysz**
- Jak używać `LayoutCollector` do wyodrębniania danych paginacji i określania zakresów stron.
- Przeglądanie układu dokumentu przy użyciu `LayoutEnumerator`.
- Implementacja callbacków układu strony, aby **renderować strony jako obrazy**.
- **Ponowne numerowanie stron** w sekcjach ciągłych przy użyciu opcji układu.
- Wskazówki dotyczące efektywnego **aktualizowania układu strony**.

## Szybkie odpowiedzi
- **Jak ponownie numerować strony w dokumencie Java?** Użyj `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` i wywołaj `doc.updatePageLayout()`.
- **Która klasa wyodrębnia dane paginacji?** `LayoutCollector` dostarcza indeksy pierwszej i ostatniej strony dla dowolnego węzła.
- **Czy mogę renderować każdą stronę jako obraz?** Tak — zaimplementuj `IPageLayoutCallback` i użyj `ImageSaveOptions`.
- **Czy muszę ręcznie wywołać aktualizację układu strony?** Po zmianie opcji układu zawsze wywołaj `doc.updatePageLayout()`.
- **Jakiej wersji Aspose.Words potrzebuję?** Przykłady działają z Aspose.Words for Java 25.3 (lub nowszą).

## Czym jest ponowne numerowanie stron?

Ponowne numerowanie stron pozwala rozpocząć nową sekwencję numeracji w określonej sekcji dokumentu, co jest niezbędne w raportach, książkach czy umowach, które wymagają oddzielnego numerowania rozdziałów lub załączników. Aspose.Words udostępnia opcję układu, która umożliwia kontrolowanie tego zachowania bez ręcznych sztuczek z podziałami stron.

## Dlaczego używać LayoutCollector i LayoutEnumerator?

- **LayoutCollector** zapewnia programowy dostęp do szczegółów paginacji, umożliwiając **wyodrębnianie danych paginacji**, takich jak pierwsza i ostatnia strona dowolnego węzła.
- **LayoutEnumerator** pozwala przemieszczać się po drzewie wizualnego układu, ułatwiając znajdowanie stron, akapitów lub linii do własnego renderowania lub analizy.
- Razem upraszczają złożone zadania układu, które w przeciwnym razie wymagałyby kosztownych konwersji do PDF lub ręcznych obliczeń.

## Wymagania wstępne

### Wymagane biblioteki i wersje
Upewnij się, że masz zainstalowaną wersję Aspose.Words for Java 25.3 (lub nowszą).

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Wymagania dotyczące konfiguracji środowiska
- Zainstalowany Java Development Kit (JDK).
- IntelliJ IDEA, Eclipse lub dowolne inne IDE Java według wyboru.
- Ważna licencja Aspose.Words (bezpłatna wersja próbna działa w celach oceny).

### Wymagania wiedzy
Podstawowa znajomość programowania w Javie jest wystarczająca.

## Konfiguracja Aspose.Words
Najpierw zintegrować bibliotekę Aspose.Words z projektem. Bezpłatną licencję próbną można uzyskać [tutaj](https://releases.aspose.com/words/java/) lub użyć tymczasowej licencji do testów.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Po przygotowaniu biblioteki możemy przejść do kluczowych funkcji.

## Przewodnik implementacji

### Funkcja 1: Użycie LayoutCollector do analizy zakresu stron
Funkcja `LayoutCollector` pozwala określić, jak węzły rozciągają się na stronach, co jest podstawą **wyodrębniania danych paginacji**.

#### Przegląd
Korzystając z `LayoutCollector`, możesz pobrać indeksy pierwszej i ostatniej strony dowolnego węzła oraz obliczyć łączną liczbę stron, które zajmuje.

#### Kroki implementacji

**1. Initialize Document and LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Populate the Document**
Tutaj dodamy treść, która rozciąga się na wiele stron:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Update Layout and Retrieve Metrics**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Wyjaśnienie
- **`DocumentBuilder`** wstawia tekst oraz podziały stron/sekcji.
- **`updatePageLayout()`** przelicza informacje o układzie, aby dane paginacji były dokładne.

### Funkcja 2: Przeglądanie przy użyciu LayoutEnumerator
`LayoutEnumerator` umożliwia efektywne nawigowanie po drzewie wizualnego układu.

#### Przegląd
Możesz przechodzić przez strony, akapity, linie i inne jednostki układu, co jest przydatne przy własnym renderowaniu lub diagnostyce.

#### Kroki implementacji

**1. Initialize Document and LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Traversing Forward and Backward**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Wyjaśnienie
- **`moveParent()`** przenosi enumerator do encji nadrzędnej (w tym przypadku poziomu strony).
- Rekurencyjne metody przeglądania pozwalają zbadać całą hierarchię układu.

### Funkcja 3: Callbacki układu strony
Zaimplementuj callbacki, aby monitorować zdarzenia układu i **renderować strony jako obrazy** w razie potrzeby.

#### Przegląd
Interfejs `IPageLayoutCallback` powiadamia, gdy część dokumentu zakończy przetwarzanie układu lub gdy konwersja zostanie zakończona.

#### Kroki implementacji

**1. Set Callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implement Callback Methods**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Wyjaśnienie
- **`notify()`** reaguje na zdarzenia układu.
- **`ImageSaveOptions`** w połączeniu z `PageSet` umożliwia **renderowanie stron jako obrazy** (PNG w tym przykładzie).

### Funkcja 4: Ponowne numerowanie stron w sekcjach ciągłych
Kontroluj numerację stron, gdy masz wiele sekcji płynących ciągle.

#### Przegląd
Ustawiając opcję `ContinuousSectionRestart`, możesz zdecydować, czy numery stron mają się restartować na nowej stronie, czy kontynuować płynnie.

#### Kroki implementacji

**1. Load Document**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Configure Page Numbering Options**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Wyjaśnienie
- **`setContinuousSectionPageNumberingRestart()`** określa, jak Aspose.Words ma obsługiwać numerację w sekcjach ciągłych.
- Po zmianie opcji, **zaktualizuj układ strony**, aby zastosować zmiany.

## Praktyczne zastosowania
1. **Analiza paginacji dokumentu** – użyj `LayoutCollector`, aby audytować, jak treść rozkłada się na stronach i odpowiednio dostosować marginesy lub podziały.
2. **Renderowanie PDF** – połącz `LayoutEnumerator` z callbackiem, aby wygenerować wysokiej jakości obrazy stron przed konwersją do PDF.
3. **Dynamiczne aktualizacje dokumentu** – reaguj na zdarzenia układu (np. po rozszerzeniu tabeli) i automatycznie renderuj ponownie dotknięte strony.
4. **Raporty wielosekcyjne** – zastosuj **ponowne numerowanie stron**, aby każdy rozdział miał własny schemat numeracji, zachowując ciągły przepływ.

## Rozważania dotyczące wydajności
- Usuń nieużywane sekcje lub ukryte treści przed wywołaniem `updatePageLayout()`, aby przyspieszyć przetwarzanie.
- Używaj API strumieniowych dla dużych dokumentów, aby uniknąć ładowania całego pliku do pamięci.
- Ogranicz głębokość rekurencyjnego przeglądania w `LayoutEnumerator`, jeśli potrzebujesz tylko informacji na poziomie strony.

## Typowe problemy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|-------|-------|-----|
| `layoutCollector.getNumPagesSpanned()` zwraca 0 | Układ nie został zaktualizowany | Wywołaj `doc.updatePageLayout()` przed zapytaniem |
| Obrazy nie są generowane w callbacku | Brak konfiguracji `ImageSaveOptions` | Upewnij się, że ustawiono `saveOptions.setPageSet(new PageSet(pageIndex))` |
| Numery stron nie restartują się | Nieprawidłowa wartość `ContinuousSectionRestart` | Użyj `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` dla prawdziwego restartu |

## Najczęściej zadawane pytania

**Q: Czy mogę wyodrębnić dokładny numer strony konkretnego akapitu?**  
A: Tak — użyj `LayoutCollector`, aby uzyskać stronę początkową węzła akapitu, a następnie wywołaj `doc.updatePageLayout()`, aby zapewnić aktualność danych.

**Q: Czy `update page layout` wpływa na zawartość dokumentu?**  
A: Nie. Tylko przelicza informacje o układzie; rzeczywisty tekst i formatowanie pozostają niezmienione.

**Q: Jak efektywnie renderować wszystkie strony dużego dokumentu jako obrazy?**  
A: Zaimplementuj `IPageLayoutCallback` i przetwarzaj każdą stronę kolejno, opcjonalnie używając wielowątkowości do zapisu I/O‑zależnego.

**Q: Czy można restartować numerację tylko dla niektórych sekcji?**  
A: Tak — zastosuj `setContinuousSectionPageNumberingRestart` do opcji układu konkretnej sekcji przed wywołaniem `updatePageLayout()`.

**Q: Która wersja Aspose.Words wprowadziła `LayoutCollector`?**  
A: `LayoutCollector` jest dostępny od wczesnych wydań 2020; przykłady używają wersji 25.3.

## Podsumowanie
Opanowując **ponowne numerowanie stron**, `LayoutCollector` i `LayoutEnumerator`, zyskujesz potężny zestaw narzędzi do zaawansowanego przetwarzania tekstu w Aspose.Words for Java. Niezależnie od tego, czy potrzebujesz **wyodrębnić dane paginacji**, **renderować strony jako obrazy**, czy po prostu kontrolować numerację stron w sekcjach, te API zapewniają precyzyjną, programową kontrolę przy zachowaniu wysokiej wydajności.

---

**Ostatnia aktualizacja:** 2026-01-14  
**Testowano z:** Aspose.Words for Java 25.3  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}