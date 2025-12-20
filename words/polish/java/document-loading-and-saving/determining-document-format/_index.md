---
date: 2025-12-20
description: Dowiedz się, jak organizować pliki według typu i wykrywać formaty dokumentów
  w Javie z Aspose.Words. Obsługuje DOC, DOCX, RTF i inne.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organizuj pliki według typu przy użyciu Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organizowanie plików według typu przy użyciu Aspose.Words dla Java

Kiedy potrzebujesz **organizować pliki według typu** w aplikacji Java, pierwszym krokiem jest wiarygodne określenie formatu każdego dokumentu. Aspose.Words dla Java upraszcza to zadanie, umożliwiając wykrywanie formatów DOC, DOCX, RTF, HTML, ODT i wielu innych – nawet zaszyfrowanych lub nieznanych plików. W tym przewodniku przeprowadzimy Cię przez tworzenie folderów, wykrywanie formatów plików i automatyczne sortowanie Twoich plików.

## Szybkie odpowiedzi
- **Co oznacza „organizować pliki według typu”?** Oznacza to automatyczne przenoszenie dokumentów do folderów na podstawie wykrytego formatu (np. DOCX, PDF, RTF).  
- **Która biblioteka pomaga wykrywać format pliku w Javie?** Aspose.Words dla Java udostępnia `FileFormatUtil.detectFileFormat()`.  
- **Czy API potrafi rozpoznać nieznane typy plików?** Tak – zwraca `LoadFormat.UNKNOWN` dla nieobsługiwanych lub nierozpoznanych plików.  
- **Czy obsługa wykrywania zaszyfrowanych dokumentów jest dostępna?** Absolutnie; flaga `FileFormatInfo.isEncrypted()` informuje, czy plik jest chroniony hasłem.  
- **Czy potrzebna jest licencja do użytku produkcyjnego?** Wymagana jest ważna licencja Aspose.Words do wdrożeń komercyjnych.

## Wprowadzenie: Organizowanie plików według typu przy użyciu Aspose.Words dla Java

Podczas pracy z przetwarzaniem dokumentów w Javie kluczowe jest określenie formatu obsługiwanych plików. Aspose.Words dla Java oferuje potężne funkcje do **detect file format java**, i przeprowadzimy Cię przez proces efektywnego organizowania plików.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące elementy:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) zainstalowany w systemie
- Podstawowa znajomość programowania w Javie

## Krok 1: Konfiguracja katalogów

Najpierw musimy skonfigurować niezbędne katalogi, aby skutecznie organizować nasze pliki. Utworzymy katalogi dla różnych typów dokumentów.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Utworzyliśmy katalogi dla obsługiwanych, nieznanych, zaszyfrowanych oraz dokumentów sprzed wersji 97.

## Krok 2: Wykrywanie formatu dokumentu

Teraz wykryjmy format dokumentów w naszych katalogach. Skorzystamy z Aspose.Words dla Java, aby to osiągnąć.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

W tym fragmencie iterujemy po plikach, **detect file format java**, i organizujemy je w odpowiednie foldery.

## Pełny kod źródłowy do określania formatu dokumentu w Aspose.Words dla Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Jak wykrywać format pliku w Javie

Metoda `FileFormatUtil.detectFileFormat()` analizuje nagłówek pliku i zwraca obiekt `FileFormatInfo`. Obiekt ten informuje o **load format**, czy plik jest zaszyfrowany oraz o innych przydatnych metadanych. Korzystając z tych informacji możesz programowo **identify unknown file types** i zdecydować, jak przetworzyć każdy z nich.

## Identyfikowanie nieznanych typów plików

Gdy API zwraca `LoadFormat.UNKNOWN`, plik jest uszkodzony lub używa formatu, którego Aspose.Words nie obsługuje. W naszym przykładowym kodzie przenosimy takie pliki do folderu **Unknown**, abyś mógł je później przejrzeć.

## Częste problemy i rozwiązania

| Problem | Powód | Rozwiązanie |
|---------|-------|-------------|
| Pliki zawsze trafiają do folderu *Supported* | `FileFormatUtil` nie mógł odczytać nagłówka (np. plik jest pusty) | Upewnij się, że podajesz prawidłową ścieżkę do pliku i że plik nie ma zerowej wielkości. |
| Zaszyfrowane pliki generują wyjątek | Próba odczytu bez obsługi szyfrowania | Użyj sprawdzenia `info.isEncrypted()` przed dalszym przetwarzaniem, jak pokazano w kodzie. |
| Dokumenty Word sprzed wersji 97 nie są wykrywane | Starsze formaty wymagają obsługi przypadku `DOC_PRE_WORD_60` | Zachowaj blok `case LoadFormat.DOC_PRE_WORD_60`, aby kierować je do folderu *Pre97*. |

## Najczęściej zadawane pytania

### Jak zainstalować Aspose.Words dla Java?

Możesz pobrać Aspose.Words dla Java ze [tutaj](https://releases.aspose.com/words/java/) i postępować zgodnie z podanymi instrukcjami instalacji.

### Jakie formaty dokumentów są obsługiwane?

Aspose.Words dla Java obsługuje różne formaty dokumentów, w tym DOC, DOCX, RTF, HTML, ODT i inne. Zapoznaj się z oficjalną dokumentacją, aby uzyskać pełną listę.

### Jak mogę wykrywać zaszyfrowane dokumenty przy użyciu Aspose.Words dla Java?

Użyj metody `FileFormatUtil.detectFileFormat()`; zwrócona flaga `FileFormatInfo.isEncrypted()` wskazuje na szyfrowanie, jak pokazano w tym przewodniku.

### Czy istnieją ograniczenia przy pracy ze starszymi formatami dokumentów?

Starsze formaty, takie jak MS Word 6 czy Word 95, mogą nie posiadać nowoczesnych funkcji i mogą mieć problemy z kompatybilnością. Rozważ konwersję ich do nowszych formatów, gdy to możliwe.

### Czy mogę zautomatyzować wykrywanie formatu dokumentu w mojej aplikacji Java?

Tak, wstaw dostarczony kod do potoku przetwarzania w Twojej aplikacji. Umożliwi to automatyczne sortowanie i obsługę w oparciu o wykryte formaty.

**Last Updated:** 2025-12-20  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}