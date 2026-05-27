---
category: general
date: 2026-05-26
description: Otwórz uszkodzony dokument Word w Javie przy użyciu Aspose.Words. Dowiedz
  się, jak ustawić tryb odzyskiwania i niezawodnie przywrócić uszkodzone pliki Word.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: pl
og_description: Otwórz uszkodzony dokument Word w Javie przy użyciu Aspose.Words.
  Ten przewodnik pokazuje, jak ustawić tryb odzyskiwania i skutecznie przywrócić uszkodzone
  pliki Word.
og_title: Otwórz uszkodzony dokument Word – ustaw tryb odzyskiwania w Javie
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Otwórz uszkodzony dokument Word – ustaw tryb odzyskiwania w Javie
url: /pl/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Otwieranie uszkodzonego dokumentu Word – ustaw tryb odzyskiwania w Javie

Czy kiedykolwiek próbowałeś otworzyć uszkodzony dokument Word i zobaczyłeś, jak program wywala wyjątek? Nie jesteś sam — te zepsute pliki .docx mogą być prawdziwą uciążliwością. Dobrą wiadomością jest to, że Aspose.Words for Java daje Ci precyzyjną kontrolę, dzięki czemu możesz **otworzyć uszkodzony dokument Word** bez awarii aplikacji i samodzielnie zdecydować, czy chcesz otrzymywać ostrzeżenia, ciche odzyskiwanie, czy twarde odrzucenie.

W tym samouczku przeprowadzimy Cię przez cały proces: od stworzenia odpowiedniego `LoadOptions`, przez wybranie właściwej wartości **set recovery mode**, aż po potwierdzenie, że dokument został rzeczywiście załadowany. Po zakończeniu będziesz wiedział, **jak odzyskać uszkodzony plik Word** programowo, bez ręcznego kopiowania‑wklejania.

> **Czego potrzebujesz**  
> * Java 8 lub nowsza (API działa również z Java 11)  
> * Aspose.Words for Java 23.9 (lub najnowsza wersja)  
> * Przykładowy uszkodzony .docx ‑ po prostu zmień nazwę dowolnego prawidłowego pliku, aby zasymulować uszkodzenie, jeśli nie masz takiego pod ręką  

Zanurzmy się.

## Otwieranie uszkodzonego dokumentu Word – przegląd krok po kroku

Poniżej znajduje się wysokopoziomowy przepływ, który zaimplementujemy:

1. **Utwórz `LoadOptions`** – ten obiekt informuje Aspose.Words, jak zachować się w sytuacji problemowej.  
2. **Ustaw tryb odzyskiwania** – wybierz `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS` lub `REJECT_CORRUPTED`.  
3. **Załaduj dokument** używając skonfigurowanych opcji.  
4. **Zweryfikuj**, że ładowanie się powiodło (np. wypisz liczbę stron).  

Każdy krok jest wyjaśniony szczegółowo, wraz z fragmentami kodu, które możesz skopiować i wkleić bezpośrednio do swojego IDE.

## Ustawianie trybu odzyskiwania dla różnych scenariuszy

Aspose.Words definiuje trzy strategie odzyskiwania w `LoadOptions.RecoveryMode`:

| Tryb | Zachowanie | Kiedy używać |
|------|------------|--------------|
| `RECOVER_WITH_WARNINGS` | Próbuje załadować dokument, ale wyświetla wszelkie problemy jako ostrzeżenia w konsoli. | Chcesz zobaczyć *co* poszło nie tak, nie przerywając działania. |
| `RECOVER_WITHOUT_WARNINGS` | Cicho naprawia, co się da, i tłumi ostrzeżenia. | Środowiska produkcyjne, w których logi muszą pozostać czyste. |
| `REJECT_CORRUPTED` | Rzuca wyjątek w momencie wykrycia uszkodzenia. | Ścisłe potoki walidacji, które muszą szybko zakończyć się niepowodzeniem. |

Wybranie właściwego trybu jest istotą **set recovery mode**. W większości sesji debugowania `RECOVER_WITH_WARNINGS` jest optymalnym wyborem, ponieważ dokładnie informuje, które części zostały naprawione.

## Jak odzyskać uszkodzony plik Word przy użyciu Aspose.Words

Poniżej znajduje się **kompletny, gotowy do uruchomienia program w Javie**, który demonstruje cały proces. Wystarczy, że wkleisz go do pliku `RecoveryModeDemo.java`, dostosujesz ścieżkę i uruchomisz.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Dlaczego każdy wiersz ma znaczenie

* **`LoadOptions loadOptions = new LoadOptions();`** – bez tego obiektu Aspose.Words używa domyślnego odzyskiwania, które *odrzuca* uszkodzone pliki. Utworzenie go daje Ci punkt zaczepienia do zmiany tego zachowania.  
* **`setRecoveryMode(...)`** – to wywołanie **set recovery mode**, które decyduje, czy ostrzeżenia będą wyświetlane, ukryte, czy spowodują wyjątek.  
* **`new Document(path, loadOptions);`** – konstruktor przyjmuje właśnie skonfigurowane `LoadOptions`, więc biblioteka od razu wie, jak traktować uszkodzony plik.  
* **`doc.getPageCount()`** – szybka kontrola poprawności. Jeśli dokument się załaduje i zwróci liczbę stron, udało Ci się **jak odzyskać uszkodzony plik Word**.  
* **`doc.save(...)`** – opcjonalne, ale przydatne; możesz zapisać naprawioną wersję na dysku do późniejszego użycia.

## Obsługa typowych przypadków brzegowych

### 1. Plik nie został znaleziony

Jeśli ścieżka jest nieprawidłowa, `Document` rzuca `FileNotFoundException`. Owiń ładowanie w blok try‑catch i zaloguj przyjazny komunikat:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Nieodwracalne uszkodzenie

Nawet przy `RECOVER_WITH_WARNINGS` niektóre struktury mogą być poza naprawą. W takim wypadku Aspose.Words i tak załaduje to, co się da, ale zobaczysz ostrzeżenia typu „Cannot read paragraph properties”. Zwróć uwagę na wyjście konsoli; te ostrzeżenia często wskazują brakujące sekcje, które możesz musieć odtworzyć ręcznie.

### 3. Duże pliki i wydajność

Odzyskiwanie wprowadza niewielki narzut, ponieważ biblioteka parsuje plik dwa razy — raz, aby wykryć problemy, drugi raz, aby je odbudować. Dla dokumentów wielogigabajtowych rozważ strumieniowe przetwarzanie pliku lub zwiększenie pamięci JVM (`-Xmx2g`), aby uniknąć `OutOfMemoryError`.

## Pro Tips – jak uczynić odzyskiwanie odpornym

* **Loguj ostrzeżenia do pliku** – przekieruj `System.err` do loggera, aby mieć ślad audytowy tego, co zostało naprawione.  
* **Waliduj po odzyskaniu** – wywołaj `doc.updatePageLayout();` i ponownie sprawdź liczbę stron; czasami układ zmienia się po naprawie uszkodzonych sekcji.  
* **Automatyzuj wsadowe odzyskiwanie** – otocz demo pętlą, która przetwarza folder z uszkodzonymi plikami, używając tego samego `LoadOptions` przy każdym przebiegu.

## Podsumowanie

Teraz wiesz dokładnie, **jak odzyskać uszkodzony plik Word** przy użyciu Aspose.Words for Java. Tworząc instancję `LoadOptions`, **set recovery mode** na strategię pasującą do Twojego scenariusza i ładując dokument z tymi opcjami, możesz bezpiecznie **otworzyć uszkodzony dokument Word** bez wywoływania awarii aplikacji. Powyższy przykładowy kod to kompletny, gotowy do uruchomienia zestaw, który wypisuje liczbę stron i nawet zapisuje oczyszczoną kopię.

Co dalej? Spróbuj zamienić tryb odzyskiwania na `RECOVER_WITHOUT_WARNINGS` i porównaj wyjście konsoli, albo poeksperymentuj z ładowaniem zaszyfrowanych dokumentów (będziesz musiał podać hasło poprzez

## Powiązane samouczki

- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}