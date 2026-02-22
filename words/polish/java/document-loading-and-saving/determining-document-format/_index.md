---
date: 2026-02-22
description: Dowiedz się, jak wykrywać format dokumentu w Javie przy użyciu Aspose.Words
  i automatycznie przenosić pliki według formatu. Rozpoznawaj DOC, DOCX i inne.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Wykrywanie formatu dokumentu w Javie przy użyciu Aspose.Words for Java
url: /pl/java/document-loading-and-saving/determining-document-format/
weight: 25
---

. So translate labels.

"**Last Updated:** 2026-02-22" -> "**Ostatnia aktualizacja:** 2026-02-22"

"**Tested With:** Aspose.Words for Java 24.12 (latest)" -> "**Testowano z:** Aspose.Words for Java 24.12 (latest)"

"**Author:** Aspose" -> "**Autor:** Aspose"

Then closing shortcodes.

Now ensure we didn't translate any URLs, code placeholders, shortcodes.

Also ensure we keep markdown formatting.

Now produce final output with all content.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# wykrywanie formatu dokumentu java przy użyciu Aspose.Words for Java

Kiedy potrzebujesz **detect document format java** w partii plików, możliwość automatycznego sortowania ich do odpowiednich folderów może zaoszczędzić godziny ręcznej pracy. W tym samouczku pokażemy, jak Aspose.Words for Java ułatwia identyfikację formatów Word, RTF, HTML, ODT i wielu innych, a następnie **move files by format** do uporządkowanych katalogów.

## Szybkie odpowiedzi
- **What does “detect document format java” mean?** Jest to proces programowego identyfikowania formatu przetwarzania tekstu pliku (DOC, DOCX, RTF itp.) przy użyciu kodu Java.  
- **Which library provides this capability?** Aspose.Words for Java oferuje API `FileFormatUtil.detectFileFormat`.  
- **Can the utility also handle encrypted files?** Tak – flaga `FileFormatInfo.isEncrypted()` informuje, czy dokument jest chroniony hasłem.  
- **Do I need a license for production use?** Wymagana jest komercyjna licencja Aspose.Words dla wdrożeń nie‑ewaluacyjnych.  
- **Is it possible to move files automatically after detection?** Oczywiście – połącz wynik wykrywania z `FileUtils.copyFile`, aby sortować pliki do własnych folderów.

## Co to jest detect document format java?
`detect document format java` odnosi się do użycia kodu Java do sprawdzenia binarnego nagłówka pliku i określenia, do którego formatu przetwarzania tekstu należy (np. DOC, DOCX, ODT). Aspose.Words odczytuje plik bez pełnego ładowania dokumentu, co sprawia, że operacja jest szybka i oszczędna pod względem pamięci.

## Dlaczego przenosić pliki według formatu?
Organizowanie dokumentów według ich natywnego formatu upraszcza dalsze przetwarzanie:

- **Batch conversions** stają się proste, gdy wszystkie pliki DOCX znajdują się w jednym folderze.  
- **Legacy support**: możesz odizolować pliki Word sprzed wersji 97 do specjalnego przetwarzania.  
- **Security**: zaszyfrowane dokumenty mogą być automatycznie kwarantannowane.  

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (pobierz najnowszą wersję)  
- Java Development Kit (JDK) 8 lub nowszy zainstalowany  
- Podstawowa znajomość Java I/O i strumieni  

## Krok 1: Utwórz katalogi dla każdego formatu

Najpierw tworzymy czystą strukturę folderów, do których będą przenoszone wykryte pliki. To utrzymuje przepływ pracy w porządku i ułatwia późniejsze dodawanie nowych kategorii formatów.

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

> **Pro tip:** Używaj ścieżek bezwzględnych lub skonfiguruj katalog bazowy za pomocą pliku właściwości, aby uniknąć twardego kodowania ścieżek w kodzie produkcyjnym.

## Krok 2: Wykryj format dokumentu i przenieś pliki

Rdzeń **detect document format java** znajduje się w pętli poniżej. Skanuje każdy plik, określa jego typ i kopiuje go do odpowiedniego folderu.

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

Blok `switch` można rozszerzyć, aby obsługiwał wszystkie interesujące Cię formaty. Każdy przypadek wypisuje przyjazny komunikat, a następnie przenosi plik do pasującego folderu.

## Pełny kod źródłowy dla wykrywania formatu dokumentu java

Poniżej znajduje się pełny, gotowy do uruchomienia przykład, który łączy konfigurację katalogów i logikę wykrywania. Skopiuj go do klasy Java, dostosuj ścieżkę bazową i uruchom na folderze z mieszanymi dokumentami.

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

## Typowe problemy i rozwiązywanie

| Problem | Dlaczego się pojawia | Jak naprawić |
|---------|----------------------|--------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Plik jest uszkodzony lub używa formatu nie‑Word. | Zweryfikuj rozszerzenie pliku lub dodaj mechanizm awaryjny, aby przenieść go do folderu *Unknown* (już w przykładzie). |
| **Encrypted files throw an exception** | API próbuje odczytać zawartość przed sprawdzeniem szyfrowania. | Zawsze wywołuj `info.isEncrypted()` przed jakąkolwiek inną operacją na dokumencie. |
| **Directory creation fails on Linux** | Brak wystarczających uprawnień lub brak folderu nadrzędnego. | Upewnij się, że proces Java ma dostęp do zapisu i że ścieżka bazowa istnieje. |

## Najczęściej zadawane pytania

**Q: How do I install Aspose.Words for Java?**  
A: Możesz pobrać Aspose.Words for Java z [tutaj](https://releases.aspose.com/words/java/) i postępować zgodnie z dostarczonymi instrukcjami instalacji.

**Q: What document formats are supported for detection?**  
A: Aspose.Words może wykrywać DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML oraz starsze formaty sprzed wersji 97, i inne.

**Q: Can this code handle password‑protected documents?**  
A: Tak. Flaga `FileFormatInfo.isEncrypted()` identyfikuje zaszyfrowane pliki, pozwalając przenieść je do bezpiecznego folderu bez ich otwierania.

**Q: Is there a performance impact when scanning large folders?**  
A: Wykrywanie odczytuje tylko nagłówek pliku, więc nawet tysiące plików są przetwarzane szybko. W przypadku bardzo dużych partii rozważ użycie równoległych strumieni.

**Q: How can I extend the script to convert unsupported formats?**  
A: Po wykryciu możesz wywołać `Document.save` z żądanym formatem wyjściowym dla dowolnego obsługiwanego typu źródłowego.

## Podsumowanie

Korzystając z **detect document format java** wraz z Aspose.Words, zyskujesz niezawodny sposób na automatyczne sortowanie, kwarantannowanie lub konwertowanie plików związanych z Wordem. Przykładowy kod pokazuje, jak stworzyć przejrzystą hierarchię folderów, zidentyfikować format każdego pliku i przenieść go odpowiednio — oszczędzając czas i redukując błędy ręczne.

---

**Ostatnia aktualizacja:** 2026-02-22  
**Testowano z:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}