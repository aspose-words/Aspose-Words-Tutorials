---
"description": "Dowiedz się, jak wykrywać formaty plików dokumentów za pomocą Aspose.Words dla .NET dzięki temu kompleksowemu przewodnikowi krok po kroku."
"linktitle": "Wykryj format pliku dokumentu"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Wykryj format pliku dokumentu"
"url": "/pl/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wykryj format pliku dokumentu

## Wstęp

W dzisiejszym cyfrowym świecie efektywne zarządzanie różnymi formatami dokumentów jest kluczowe. Niezależnie od tego, czy obsługujesz Word, PDF, HTML czy inne formaty, możliwość prawidłowego wykrywania i przetwarzania tych plików może zaoszczędzić Ci dużo czasu i wysiłku. W tym samouczku przyjrzymy się, jak wykrywać formaty plików dokumentów za pomocą Aspose.Words dla .NET. Ten przewodnik przeprowadzi Cię przez wszystko, co musisz wiedzieć, od wymagań wstępnych po szczegółowy przewodnik krok po kroku.

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz:

- Aspose.Words dla .NET: Można go pobrać ze strony [Tutaj](https://releases.aspose.com/words/net/). Upewnij się, że masz ważne prawo jazdy. Jeśli nie, możesz uzyskać [licencja tymczasowa](https://purchase.aspose.com/temporary-license/).
- Visual Studio: każda nowsza wersja będzie działać dobrze.
- .NET Framework: Upewnij się, że masz zainstalowaną właściwą wersję.

## Importuj przestrzenie nazw

Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Podzielmy przykład na kilka kroków, aby łatwiej było go śledzić.

## Krok 1: Skonfiguruj katalogi

Najpierw musimy utworzyć katalogi, w których pliki będą sortowane według ich formatu.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Utwórz katalogi, jeśli jeszcze nie istnieją.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Krok 2: Pobierz listę plików

Następnie pobierzemy listę plików z katalogu, wykluczając wszelkie uszkodzone dokumenty.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Krok 3: Wykryj formaty plików

Teraz przeglądamy każdy plik i wykrywamy jego format za pomocą Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Wyświetl typ dokumentu
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Wniosek

Wykrywanie formatów plików dokumentów za pomocą Aspose.Words dla .NET to prosty proces. Konfigurując katalogi, pobierając listę plików i wykorzystując Aspose.Words do wykrywania formatów plików, możesz sprawnie organizować i zarządzać dokumentami. Takie podejście nie tylko oszczędza czas, ale także zapewnia, że obsługujesz różne formaty dokumentów poprawnie.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to potężna biblioteka do programowej pracy z dokumentami Word. Umożliwia ona programistom tworzenie, modyfikowanie i konwertowanie dokumentów w różnych formatach.

### Czy Aspose.Words może wykryć zaszyfrowane dokumenty?
Tak, Aspose.Words potrafi wykryć, czy dokument jest zaszyfrowany, dzięki czemu możesz odpowiednio postępować z takimi dokumentami.

### Jakie formaty potrafi wykryć Aspose.Words?
Aspose.Words potrafi wykryć szeroką gamę formatów, w tym DOC, DOCX, RTF, HTML, MHTML, ODT i wiele innych.

### Jak mogę uzyskać tymczasową licencję na Aspose.Words?
Możesz uzyskać tymczasową licencję od [Zakup Aspose](https://purchase.aspose.com/temporary-license/) strona.

### Gdzie mogę znaleźć dokumentację Aspose.Words?
Dokumentację Aspose.Words można znaleźć [Tutaj](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}