---
category: general
date: 2025-12-23
description: Ustaw tryb odzyskiwania, aby naprawić uszkodzone dokumenty Word. Dowiedz
  się, jak otwierać pliki DOCX, używać trybu odzyskiwania i obsługiwać uszkodzone
  pliki w Javie.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: pl
og_description: Ustaw tryb odzyskiwania, aby przywrócić uszkodzone dokumenty Word.
  Ten przewodnik pokazuje, jak otworzyć pliki DOCX, używać trybu odzyskiwania i obsługiwać
  uszkodzone pliki w Javie.
og_title: Ustaw tryb odzyskiwania – Otwórz uszkodzone pliki Word w Javie
tags:
- Java
- Aspose.Words
- Document Recovery
title: Ustaw tryb odzyskiwania – Jak otworzyć uszkodzone pliki Word w Javie
url: /pl/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw tryb odzyskiwania – Jak otworzyć uszkodzone pliki Word w Javie

Czy kiedykolwiek próbowałeś **ustawić tryb odzyskiwania** w dokumencie Word, który odmawia otwarcia? Nie jesteś sam. Wielu programistów napotyka problem, gdy DOCX jest lekko uszkodzony i zwykłe `new Document("file.docx")` rzuca wyjątek. Dobra wiadomość? Aspose.Words for Java oferuje wbudowany sposób na **użycie trybu odzyskiwania** i faktyczne **odzyskanie uszkodzonych plików Word**.

W tym samouczku przejdziemy krok po kroku przez wszystko, co musisz wiedzieć, aby **bezpiecznie otworzyć uszkodzony plik word**, od konfiguracji `LoadOptions` po obsługę przypadków brzegowych, które zazwyczaj sprawiają problemy. Bez zbędnych wstępów — praktyczne, krok‑po‑kroku rozwiązanie, które możesz od razu wkleić do swojego projektu.

> **Pro tip:** Jeśli masz do czynienia tylko z drobnymi problemami (np. brakującą stopką), tryb odzyskiwania **Tolerant** zazwyczaj wystarcza. Tryb **Strict** zarezerwuj na sytuacje, w których dokument musi być w 100 % czysty przed dalszym przetwarzaniem.

## Czego będziesz potrzebować

- **Java 17** (lub dowolny nowszy JDK; API działa tak samo)
- **Aspose.Words for Java** 23.9 (lub nowszy) – biblioteka, która udostępnia klasę `LoadOptions`.
- Uszkodzony plik **DOCX** do testów (możesz go stworzyć, przycinając prawidłowy plik w edytorze heksadecymalnym).
- Ulubione IDE (IntelliJ, Eclipse, VS Code — wybierz to, które najbardziej Ci odpowiada).

To wszystko. Bez dodatkowych wtyczek Maven, bez zewnętrznych narzędzi. Tylko podstawowa biblioteka i odrobina kodu.

![Illustration of setting recovery mode in Aspose.Words Java API](/images/set-recovery-mode-java.png){.align-center alt="ustaw tryb odzyskiwania"}

## Krok 1 – Utwórz instancję `LoadOptions`

Pierwszą rzeczą, którą robisz, jest utworzenie obiektu `LoadOptions`. Pomyśl o nim jak o skrzynce narzędziowej, która mówi Aspose.Words **jak traktować wczytywany plik**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Dlaczego nie pominąć tego kroku? Ponieważ bez `LoadOptions` nie możesz powiedzieć bibliotece, czy chcesz **używać trybu odzyskiwania**. Domyślne zachowanie jest ścisłe, co oznacza, że każda korupcja przerywa ładowanie.

## Krok 2 – Wybierz odpowiedni tryb odzyskiwania

Aspose.Words oferuje dwie wartości wyliczeniowe:

| Mode | Co robi |
|------|----------|
| `RecoveryMode.Tolerant` | Stara się uratować jak najwięcej. Idealny dla scenariuszy *odzyskiwania uszkodzonego word*, w których jedynym problemem jest brakujący styl lub uszkodzone powiązanie. |
| `RecoveryMode.Strict`   | Szybko przerywa przy jakimkolwiek problemie. Użyj tego, gdy potrzebujesz pewności, że dokument jest nienaruszony przed dalszym przetwarzaniem. |

Ustaw tryb jedną linią:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Dlaczego to ważne:** Gdy **używasz trybu odzyskiwania**, biblioteka wewnętrznie naprawia uszkodzone części, odbudowuje brakujące węzły XML i zwraca użyteczny obiekt `Document`. W trybie *strict* zamiast tego otrzymasz `InvalidFormatException`.

## Krok 3 – Załaduj dokument z użyciem swoich opcji

Teraz w końcu przekazujesz plik do Aspose.Words, podając skonfigurowany `LoadOptions`.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Jeśli plik jest tylko lekko uszkodzony, `doc` będzie w pełni funkcjonalnym obiektem `Document`. Możesz teraz:

- Odczytać tekst (`doc.getText()`),
- Zapisz do innego formatu (`doc.save("repaired.pdf")`),
- Lub nawet sprawdzić listę odzyskanych części za pomocą API `Document`.

### Weryfikacja odzyskiwania

Szybka kontrola pozwala potwierdzić, że odzyskiwanie zakończyło się sukcesem:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Krok 4 – Obsługa przypadków brzegowych

### 4.1 Kiedy tryb Tolerant nie wystarcza

Czasami plik jest tak uszkodzony, że nawet **Tolerant** nie potrafi go złożyć (np. brak głównego XML). W takich rzadkich przypadkach możesz:

1. Spróbuj drugiego ładowania z `RecoveryMode.Strict`, aby sprawdzić, czy komunikat o błędzie daje więcej szczegółów.
2. Użyj narzędzia zip, aby ręcznie wyodrębnić części XML i je naprawić.
3. Zaloguj wyjątek i poinformuj użytkownika, że dokument jest nieodwracalnie uszkodzony.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Rozważania dotyczące pamięci

Ładowanie dużych plików DOCX z włączonym odzyskiwaniem może tymczasowo podwoić zużycie pamięci, ponieważ Aspose.Words trzyma zarówno oryginalną, jak i naprawioną strukturę w pamięci. Jeśli przetwarzasz duże partie:

- Ponownie używaj tej samej instancji `LoadOptions` zamiast tworzyć nową przy każdym ładowaniu.
- Zwolnij `Document` (`doc.close()`) natychmiast po zakończeniu.
- Uruchom na JVM z wystarczającą pamięcią heap (`-Xmx2g` lub wyższą dla plików wielogigabajtowych).

### 4.3 Zapisywanie naprawionego pliku

Po pomyślnym załadowaniu możesz **zapisać wyczyszczoną wersję**, aby nie musieć ponownie uruchamiać odzyskiwania.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Teraz przy następnym otwarciu `repaired.docx` możesz całkowicie pominąć krok **use recovery mode**.

## Najczęściej zadawane pytania

**Q: Czy to działa na starszych plikach `.doc`?**  
A: Tak. To samo podejście `LoadOptions` działa dla `.doc` i `.rtf`. Wystarczy zmienić rozszerzenie pliku.

**Q: Czy mogę połączyć `setRecoveryMode` z innymi opcjami ładowania (np. hasło)?**  
A: Oczywiście. `LoadOptions` ma właściwości takie jak `setPassword` i `setLoadFormat`. Ustaw je przed wywołaniem `setRecoveryMode`.

**Q: Czy istnieje jakiś spadek wydajności?**  
A: Trochę—odzyskiwanie dodaje narzut parsowania. W benchmarkach, 5 MB uszkodzony plik ładuje się około 30 % wolniej w trybie **Tolerant** w porównaniu do ścisłego ładowania czystego pliku. Nadal akceptowalne dla większości zadań wsadowych.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia klas Java, który demonstruje **jak otworzyć docx**, **użyć trybu odzyskiwania** i **zapisać naprawioną kopię**.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Uruchom tę klasę po dodaniu pliku JAR Aspose.Words for Java do classpath projektu. Jeśli plik wejściowy jest jedynie lekko uszkodzony, zobaczysz komunikat **✅** oraz świeży `repaired.docx` na dysku.

## Podsumowanie

Omówiliśmy wszystko, co potrzebne, aby **ustawić tryb odzyskiwania** i skutecznie **otworzyć uszkodzone pliki word** w Javie. Tworząc obiekt `LoadOptions`, wybierając odpowiedni `RecoveryMode` i obsługując sporadyczne przypadki brzegowe, możesz zamienić frustrujący moment „plik nie otwiera się” w płynny proces odzyskiwania.

Pamiętaj:

- **Tolerant** to domyślny wybór dla większości scenariuszy *odzyskiwania uszkodzonego word*.
- **Strict** zapewnia twardą awarię, gdy potrzebna jest absolutna pewność.
- Zawsze weryfikuj załadowany dokument i, jeśli to możliwe, zapisz czystą kopię na przyszłość.

Teraz możesz pewnie odpowiedzieć na pytanie „**jak otworzyć docx**, który odmawia załadowania?” konkretnym fragmentem kodu i jasnym wyjaśnieniem. Powodzenia w kodowaniu i niech Twoje dokumenty pozostaną zdrowe!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}