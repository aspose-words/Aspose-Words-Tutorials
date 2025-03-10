---
title: Ustaw identyfikator dostawcy podpisu w dokumencie Word
linktitle: Ustaw identyfikator dostawcy podpisu w dokumencie Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Bezpiecznie ustaw Signature Provider ID w dokumentach Word za pomocą Aspose.Words dla .NET. Postępuj zgodnie z naszym szczegółowym, 2000-wyrazowym przewodnikiem, aby cyfrowo podpisywać dokumenty.
weight: 10
url: /pl/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw identyfikator dostawcy podpisu w dokumencie Word

## Wstęp

Hej! Więc masz ten niesamowity dokument Word, który wymaga podpisu cyfrowego, prawda? Ale nie byle jakiego podpisu — musisz ustawić konkretny identyfikator dostawcy podpisu. Niezależnie od tego, czy obsługujesz dokumenty prawne, umowy czy jakąkolwiek inną papierkową robotę, dodanie bezpiecznego podpisu cyfrowego jest kluczowe. W tym samouczku przeprowadzę Cię przez cały proces ustawiania identyfikatora dostawcy podpisu w dokumencie Word przy użyciu Aspose.Words dla .NET. Gotowy? Zaczynajmy!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Biblioteka Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś,[pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub dowolne środowisko IDE zgodne z C#.
3. Dokument Word: Dokument z linią podpisu (`Signature line.docx`).
4.  Certyfikat cyfrowy: A`.pfx` plik certyfikatu (np.`morzal.pfx`).
5. Podstawowa wiedza o języku C#: Tylko podstawy — nie martw się, jesteśmy tutaj, aby pomóc!

A teraz przejdźmy do akcji!

## Importuj przestrzenie nazw

Przede wszystkim upewnij się, że uwzględniłeś niezbędne przestrzenie nazw w swoim projekcie. Jest to niezbędne do uzyskania dostępu do biblioteki Aspose.Words i powiązanych klas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

Dobrze, podzielmy to na proste, łatwe do zrozumienia kroki.

## Krok 1: Załaduj swój dokument Word

Pierwszym krokiem jest załadowanie dokumentu Word zawierającego wiersz podpisu. Ten dokument zostanie zmodyfikowany, aby uwzględnić podpis cyfrowy ze wskazanym identyfikatorem dostawcy podpisu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Tutaj określamy katalog, w którym znajduje się Twój dokument. Zastąp`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do dokumentu.

## Krok 2: Uzyskaj dostęp do linii Signature Line

Następnie musimy uzyskać dostęp do wiersza podpisu w dokumencie. Wiersz podpisu jest osadzony jako obiekt kształtu w dokumencie Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Ten wiersz kodu pobiera pierwszy kształt z treści pierwszej sekcji dokumentu i rzutuje go na`SignatureLine` obiekt.

## Krok 3: Ustaw opcje znaku

Teraz tworzymy opcje podpisu, które obejmują identyfikator dostawcy i identyfikator wiersza podpisu z wiersza podpisu, do którego uzyskano dostęp.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Opcje te zostaną użyte podczas podpisywania dokumentu, aby mieć pewność, że ustawiono prawidłowy identyfikator dostawcy podpisu.

## Krok 4: Załaduj certyfikat

 Aby podpisać dokument cyfrowo, potrzebujesz certyfikatu. Oto, jak załadować swój`.pfx` plik:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Zastępować`"aw"` wraz z hasłem do pliku certyfikatu, jeśli takowe istnieje.

## Krok 5: Podpisz dokument

 Na koniec nadszedł czas na podpisanie dokumentu za pomocą`DigitalSignatureUtil.Sign` metoda.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Podpisuje dokument i zapisuje go jako nowy plik,`Digitally signed.docx`.

## Wniosek

 masz! Udało Ci się ustawić identyfikator dostawcy podpisu w dokumencie Word przy użyciu Aspose.Words dla .NET. Ten proces nie tylko zabezpiecza Twoje dokumenty, ale także zapewnia ich zgodność ze standardami podpisów cyfrowych. Teraz wypróbuj go na swoich dokumentach. Masz jakieś pytania? Sprawdź poniższe FAQ lub kliknij[Forum wsparcia Aspose](https://forum.aspose.com/c/words/8).

## Najczęściej zadawane pytania

### Czym jest identyfikator dostawcy podpisu?

Identyfikator dostawcy podpisu jednoznacznie identyfikuje dostawcę podpisu cyfrowego, gwarantując autentyczność i bezpieczeństwo.

### Czy mogę podpisać się przy użyciu dowolnego pliku .pfx?

Tak, o ile jest to ważny certyfikat cyfrowy. Upewnij się, że masz prawidłowe hasło, jeśli jest chronione.

### Jak mogę uzyskać plik .pfx?

Plik .pfx można uzyskać od Urzędu Certyfikacji (CA) lub wygenerować go za pomocą narzędzi takich jak OpenSSL.

### Czy mogę podpisać kilka dokumentów jednocześnie?

Tak, możesz przeglądać wiele dokumentów i stosować do każdego z nich tę samą procedurę podpisywania.

### Co zrobić, jeśli w moim dokumencie nie ma linii podpisu?

Najpierw musisz wstawić linię podpisu. Aspose.Words udostępnia metody dodawania linii podpisu programowo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
