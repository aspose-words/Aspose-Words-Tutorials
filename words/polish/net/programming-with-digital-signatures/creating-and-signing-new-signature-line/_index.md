---
"description": "Dowiedz się, jak utworzyć i cyfrowo podpisać linię podpisu w dokumencie Word za pomocą Aspose.Words dla .NET dzięki temu samouczkowi krok po kroku. Idealne do automatyzacji dokumentów."
"linktitle": "Tworzenie i podpisywanie nowej linii podpisu"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Tworzenie i podpisywanie nowej linii podpisu"
"url": "/pl/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie i podpisywanie nowej linii podpisu

## Wstęp

Cześć! Masz więc dokument Word i musisz dodać linię podpisu, a następnie podpisać go cyfrowo. Brzmi skomplikowanie? Wcale nie! Dzięki Aspose.Words dla .NET możesz to osiągnąć bezproblemowo, używając zaledwie kilku linii kodu. W tym samouczku przeprowadzimy Cię przez cały proces, od skonfigurowania środowiska po zapisanie dokumentu z błyszczącym nowym podpisem. Gotowy? Zaczynajmy!

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnijmy się, że masz wszystko, czego potrzebujesz:
1. Aspose.Words dla .NET - Możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
2. Zdecydowanie zalecane jest środowisko programistyczne .NET — Visual Studio.
3. Dokument do podpisania — utwórz prosty dokument Word lub wykorzystaj istniejący.
4. Plik certyfikatu – jest potrzebny do podpisów cyfrowych. Możesz użyć `.pfx` plik.
5. Obrazy do linii podpisu – opcjonalnie plik obrazu podpisu.

## Importuj przestrzenie nazw

Najpierw musimy zaimportować niezbędne przestrzenie nazw. Ten krok jest kluczowy, ponieważ konfiguruje środowisko do korzystania z funkcjonalności Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Krok 1: Konfigurowanie katalogu dokumentów

Każdy projekt potrzebuje dobrego początku. Ustawmy ścieżkę do katalogu dokumentów. To tutaj będą zapisywane i pobierane Twoje dokumenty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Tworzenie nowego dokumentu

Teraz utwórzmy nowy dokument Word za pomocą Aspose.Words. To będzie nasze płótno, w którym dodamy linię podpisu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Wstawianie linii podpisu

Tutaj dzieje się magia. Wstawiamy linię podpisu do naszego dokumentu za pomocą `DocumentBuilder` klasa.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Krok 4: Zapisywanie dokumentu z linią podpisu

Gdy linia podpisu jest już na miejscu, musimy zapisać dokument. Jest to krok pośredni przed przystąpieniem do jego podpisania.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Krok 5: Konfigurowanie opcji podpisywania

Teraz skonfigurujmy opcje podpisywania dokumentu. Obejmuje to określenie identyfikatora wiersza podpisu i obrazu, który ma zostać użyty.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Krok 6: Ładowanie certyfikatu

Podpisy cyfrowe wymagają certyfikatu. Tutaj ładujemy plik certyfikatu, który będzie użyty do podpisania dokumentu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Krok 7: Podpisanie dokumentu

To jest ostatni krok. Używamy `DigitalSignatureUtil` klasa do podpisania dokumentu. Podpisany dokument jest zapisywany pod nową nazwą.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Wniosek

masz to! Dzięki tym krokom udało Ci się utworzyć nowy dokument Word, dodać wiersz podpisu i podpisać go cyfrowo za pomocą Aspose.Words dla .NET. To potężne narzędzie, które sprawia, że automatyzacja dokumentów staje się dziecinnie prosta. Niezależnie od tego, czy masz do czynienia z kontraktami, umowami czy innymi formalnymi dokumentami, ta metoda zapewnia ich bezpieczne podpisanie i uwierzytelnienie.

## Najczęściej zadawane pytania

### Czy mogę użyć innych formatów obrazu w wierszu podpisu?
Tak, możesz używać różnych formatów obrazów, takich jak PNG, JPG, BMP itp.

### Czy konieczne jest użycie `.pfx` złożyć wniosek o certyfikat?
Tak, `.pfx` Plik jest popularnym formatem służącym do przechowywania informacji kryptograficznych, w tym certyfikatów i kluczy prywatnych.

### Czy mogę dodać wiele wierszy podpisu w jednym dokumencie?
Oczywiście! Możesz wstawić wiele wierszy podpisu, powtarzając krok wstawiania dla każdego podpisu.

### A co jeśli nie mam certyfikatu cyfrowego?
Będziesz musiał uzyskać certyfikat cyfrowy od zaufanego urzędu certyfikacji lub wygenerować go przy użyciu narzędzi typu OpenSSL.

### Jak zweryfikować podpis cyfrowy w dokumencie?
Możesz otworzyć podpisany dokument w programie Word i przejść do szczegółów podpisu, aby sprawdzić autentyczność i integralność podpisu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}