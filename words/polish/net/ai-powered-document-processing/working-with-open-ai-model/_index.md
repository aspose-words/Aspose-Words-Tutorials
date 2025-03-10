---
title: Praca z otwartym modelem AI
linktitle: Praca z otwartym modelem AI
second_title: Aspose.Words API przetwarzania dokumentów
description: Odblokuj wydajne podsumowanie dokumentów za pomocą Aspose.Words dla .NET z potężnymi modelami OpenAI. Zanurz się w tym kompleksowym przewodniku już teraz.
weight: 10
url: /pl/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Praca z otwartym modelem AI

## Wstęp

dzisiejszym cyfrowym świecie treść jest królem. Niezależnie od tego, czy jesteś studentem, profesjonalistą biznesowym czy zapalonym pisarzem, umiejętność wydajnego manipulowania, podsumowywania i generowania dokumentów jest nieoceniona. To właśnie tutaj wkracza biblioteka Aspose.Words for .NET, umożliwiająca zarządzanie dokumentami jak profesjonalista. W tym kompleksowym samouczku zagłębimy się w to, jak wykorzystać Aspose.Words w połączeniu z modelami OpenAI, aby skutecznie podsumowywać dokumenty. Gotowy, aby odblokować swój potencjał zarządzania dokumentami? Zaczynajmy!

## Wymagania wstępne

Zanim zakasamy rękawy i zagłębimy się w kod, jest kilka niezbędnych rzeczy, które musisz mieć na miejscu:

### .NET Framework
Upewnij się, że korzystasz z wersji .NET Framework, która jest zgodna z Aspose.Words. Generalnie .NET 5.0 i nowsze powinny działać idealnie.

### Aspose.Words dla biblioteki .NET
 Musisz pobrać i zainstalować bibliotekę Aspose.Words. Możesz ją pobrać z[ten link](https://releases.aspose.com/words/net/).

### Klucz API OpenAI
Aby zintegrować modele językowe OpenAI do podsumowania dokumentów, potrzebujesz klucza API. Możesz go uzyskać, rejestrując się na platformie OpenAI i pobierając klucz z ustawień konta.

### IDE dla rozwoju
Posiadanie zintegrowanego środowiska programistycznego (IDE), takiego jak Visual Studio, jest idealnym rozwiązaniem do tworzenia aplikacji .NET.

### Podstawowa wiedza programistyczna
Podstawowa znajomość języka C# i programowania obiektowego pomoże Ci łatwiej zrozumieć te koncepcje.

## Importuj pakiety

Teraz, gdy wszystko mamy już ustawione, zaimportujmy nasze pakiety. Otwórz projekt Visual Studio i dodaj niezbędne biblioteki. Oto, jak to zrobić:

### Dodaj pakiet Aspose.Words

Możesz dodać pakiet Aspose.Words za pomocą NuGet Package Manager. Oto jak to zrobić:
- Przejdź do Narzędzia -> Menedżer pakietów NuGet -> Zarządzaj pakietami NuGet dla rozwiązania.
- Wyszukaj „Aspose.Words” i kliknij Zainstaluj.

### Dodaj środowisko systemowe

 Pamiętaj o uwzględnieniu`System`przestrzeń nazw do obsługi zmiennych środowiskowych:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Dodaj Aspose.Words

Następnie uwzględnij przestrzeń nazw Aspose.Words w pliku C#:
```csharp
using Aspose.Words;
```

### Dodaj bibliotekę OpenAI

Jeśli używasz biblioteki do interfejsu z OpenAI (np. klienta REST), upewnij się, że ją również uwzględniasz. Być może będziesz musiał dodać ją przez NuGet w taki sam sposób, w jaki dodaliśmy Aspose.Words.

Teraz, gdy przygotowaliśmy nasze środowisko i zaimportowaliśmy niezbędne pakiety, przeanalizujmy krok po kroku proces podsumowania dokumentów.

## Krok 1: Zdefiniuj katalogi dokumentów

Zanim zaczniesz pracować ze swoimi dokumentami, musisz utworzyć katalogi, w których będą przechowywane Twoje dokumenty i artefakty:

```csharp
// Twój katalog dokumentów
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Twój katalog artefaktów
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Dzięki temu kod staje się bardziej łatwy w zarządzaniu, ponieważ w razie potrzeby można łatwo zmienić ścieżki.`MyDir` to miejsce, w którym przechowywane są Twoje dokumenty wejściowe, podczas gdy`ArtifactsDir` tutaj będziesz zapisywać wygenerowane podsumowania.

## Krok 2: Załaduj swoje dokumenty

Następnie załadujesz dokumenty, które chcesz podsumować. Jest to proste dzięki Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Upewnij się, że nazwy Twoich dokumentów są zgodne z tymi, których zamierzasz użyć, w przeciwnym razie wystąpią błędy!

## Krok 3: Uzyskaj swój klucz API

Teraz, gdy Twoje dokumenty są załadowane, czas pobrać klucz API OpenAI. Pobierzesz go ze zmiennych środowiskowych, aby zachować jego bezpieczeństwo:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Bezpieczne zarządzanie kluczem API jest niezwykle istotne, aby uniemożliwić dostęp nieautoryzowanym użytkownikom.

## Krok 4: Utwórz instancję modelu OpenAI

Mając gotowy klucz API, możesz teraz utworzyć wystąpienie modelu OpenAI. Do podsumowania dokumentu użyjemy modelu Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Ten krok zasadniczo uruchamia zasoby mózgowe niezbędne do podsumowania dokumentów, zapewniając dostęp do podsumowań sterowanych przez sztuczną inteligencję.

## Krok 5: Podsumowanie pojedynczego dokumentu

Podsumujmy najpierw pierwszy dokument. To tutaj dzieje się magia:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Tutaj używamy`Summarize` metoda modelu.`SummaryLength.Short`Parametr określa, że chcemy uzyskać krótkie podsumowanie — idealne do szybkiego przeglądu!

## Krok 6: Podsumowanie wielu dokumentów

Czujesz się ambitny? Możesz podsumować wiele dokumentów na raz. Spójrz tylko, jak to jest proste:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Ta funkcja jest szczególnie przydatna do porównywania wielu plików. Może przygotowujesz się do spotkania i potrzebujesz zwięzłych notatek z kilku długich raportów. To jest twój nowy najlepszy przyjaciel!

## Wniosek

Podsumowywanie dokumentów za pomocą Aspose.Words dla .NET i OpenAI to nie tylko przydatna umiejętność; to całkiem budujące. Postępując zgodnie z tym przewodnikiem, zamieniłeś długi, skomplikowany tekst w zwięzłe podsumowania, oszczędzając sobie czasu i wysiłku. Niezależnie od tego, czy zapewniasz klientom przejrzystość, czy przygotowujesz się do ważnej prezentacji, masz teraz narzędzia, aby zrobić to wydajnie.

Więc na co czekasz? Zanurz się w swoich dokumentach z pewnością siebie i pozwól technologii wykonać ciężką pracę!

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?  
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom programowe tworzenie, modyfikowanie i konwertowanie dokumentów.

### Czy potrzebuję klucza API dla OpenAI?  
Tak, musisz mieć ważny klucz API OpenAI, aby uzyskać dostęp do możliwości podsumowania za pomocą ich modeli.

### Czy mogę podsumować kilka dokumentów jednocześnie?  
Oczywiście! Możesz podsumować wiele dokumentów w jednym połączeniu, co jest idealne w przypadku obszernych raportów.

### Jak zainstalować Aspose.Words?  
Można go zainstalować za pomocą Menedżera pakietów NuGet w programie Visual Studio, wyszukując „Aspose.Words”.

### Czy istnieje bezpłatna wersja próbna Aspose.Words?  
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej Aspose.Words za pośrednictwem ich[strona internetowa](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
