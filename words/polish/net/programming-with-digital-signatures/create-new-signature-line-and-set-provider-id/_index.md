---
title: Utwórz nową linię podpisu i ustaw identyfikator dostawcy
linktitle: Utwórz nową linię podpisu i ustaw identyfikator dostawcy
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak utworzyć nową linię podpisu i ustawić identyfikator dostawcy w dokumentach Word przy użyciu Aspose.Words dla .NET. Przewodnik krok po kroku.
weight: 10
url: /pl/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz nową linię podpisu i ustaw identyfikator dostawcy

## Wstęp

Hej, entuzjaści technologii! Czy kiedykolwiek zastanawiałeś się, jak programowo dodać linię podpisu do dokumentów Word? Cóż, dzisiaj zagłębimy się w to, używając Aspose.Words dla .NET. Ten przewodnik przeprowadzi Cię przez każdy krok, dzięki czemu utworzenie nowej linii podpisu i ustawienie identyfikatora dostawcy w dokumentach Word będzie dziecinnie proste. Niezależnie od tego, czy automatyzujesz przetwarzanie dokumentów, czy po prostu chcesz usprawnić swój przepływ pracy, ten samouczek Ci pomoże.

## Wymagania wstępne

Zanim zaczniemy działać, upewnijmy się, że mamy wszystko, czego potrzebujemy:

1.  Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz[Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko programistyczne C#.
3. .NET Framework: Upewnij się, że masz zainstalowany .NET Framework.
4. Certyfikat PFX: Do podpisywania dokumentów potrzebny jest certyfikat PFX. Możesz go uzyskać od zaufanego urzędu certyfikacji.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw do Twojego projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Dobra, przejdźmy do konkretów. Oto szczegółowy opis każdego kroku tworzenia nowej linii podpisu i ustawienia identyfikatora dostawcy.

## Krok 1: Utwórz nowy dokument

Na początek musimy utworzyć nowy dokument Word. Będzie to kanwa dla naszej linii podpisu.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 W tym fragmencie kodu inicjujemy nowy`Document` i`DocumentBuilder` . Ten`DocumentBuilder` pomaga nam dodawać elementy do naszego dokumentu.

## Krok 2: Zdefiniuj opcje wiersza podpisu

Następnie definiujemy opcje dla naszej linii podpisu. Obejmuje to imię i nazwisko sygnatariusza, tytuł, adres e-mail i inne szczegóły.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Opcje te personalizują linię podpisu, czyniąc ją wyraźną i profesjonalną.

## Krok 3: Wstaw linię podpisu

Po ustawieniu opcji możemy wstawić linię podpisu do dokumentu.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Tutaj,`InsertSignatureLine` Metoda dodaje linię podpisu i przypisujemy jej unikalny identyfikator dostawcy.

## Krok 4: Zapisz dokument

Po wstawieniu wiersza podpisu zapiszmy dokument.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Dokument zostanie zapisany z nowo dodaną linią podpisu.

## Krok 5: Skonfiguruj opcje podpisywania

Teraz musimy skonfigurować opcje podpisywania dokumentu. Obejmuje to identyfikator wiersza podpisu, identyfikator dostawcy, komentarze i czas podpisania.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Opcje te zapewniają, że dokument zostanie podpisany przy użyciu właściwych danych.

## Krok 6: Utwórz posiadacza certyfikatu

Aby podpisać dokument, użyjemy certyfikatu PFX. Utwórzmy dla niego posiadacza certyfikatu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Pamiętaj o wymianie`"morzal.pfx"` z Twoim aktualnym plikiem certyfikatu i`"aw"` z hasłem certyfikatu.

## Krok 7: Podpisz dokument

Na koniec podpisujemy dokument za pomocą narzędzia do podpisu cyfrowego.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Dokument zostaje podpisany i zapisany jako nowy plik.

## Wniosek

I masz to! Udało Ci się utworzyć nową linię podpisu i ustawić identyfikator dostawcy w dokumencie Word za pomocą Aspose.Words dla .NET. Ta potężna biblioteka sprawia, że zarządzanie zadaniami przetwarzania dokumentów i ich automatyzacja są niezwykle łatwe. Wypróbuj ją i zobacz, jak może usprawnić Twój przepływ pracy.

## Najczęściej zadawane pytania

### Czy mogę dostosować wygląd linii podpisu?
 Oczywiście! Możesz modyfikować różne opcje w`SignatureLineOptions`aby spełnić Twoje potrzeby.

### Co zrobić, jeśli nie mam certyfikatu PFX?
Będziesz musiał uzyskać jeden od zaufanego urzędu certyfikacji. Jest on niezbędny do cyfrowego podpisywania dokumentów.

### Czy mogę dodać do dokumentu wiele wierszy podpisu?
Tak, możesz dodać dowolną liczbę wierszy podpisu, powtarzając proces wstawiania, korzystając z różnych opcji.

### Czy Aspose.Words dla .NET jest kompatybilny z .NET Core?
Tak, Aspose.Words for .NET obsługuje platformę .NET Core, co czyni go wszechstronnym rozwiązaniem dla różnych środowisk programistycznych.

### Jak bezpieczne są podpisy cyfrowe?
Podpisy cyfrowe tworzone za pomocą Aspose.Words są bardzo bezpieczne, pod warunkiem, że używasz ważnego i zaufanego certyfikatu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
