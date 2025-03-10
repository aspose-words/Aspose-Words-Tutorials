---
title: Praca z modelem Google AI
linktitle: Praca z modelem Google AI
second_title: Aspose.Words API przetwarzania dokumentów
description: Ulepsz przetwarzanie dokumentów dzięki Aspose.Words for .NET i Google AI, aby bez wysiłku tworzyć zwięzłe podsumowania.
weight: 10
url: /pl/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Praca z modelem Google AI

## Wstęp

tym artykule krok po kroku omówimy, jak podsumowywać dokumenty za pomocą Aspose.Words i modeli AI Google. Niezależnie od tego, czy chcesz skrócić długi raport, czy wyodrębnić informacje z wielu źródeł, mamy dla Ciebie rozwiązanie.

## Wymagania wstępne

Zanim przejdziemy do części praktycznej, upewnijmy się, że jesteś przygotowany na sukces. Oto, czego będziesz potrzebować:

1. Podstawowa znajomość języka C# i .NET: Znajomość koncepcji programowania pomoże Ci lepiej zrozumieć przykłady.
   
2.  Biblioteka Aspose.Words dla .NET: Ta potężna biblioteka umożliwia bezproblemowe tworzenie i manipulowanie dokumentami Word. Możesz[pobierz tutaj](https://releases.aspose.com/words/net/).

3. Klucz API dla modelu Google AI: Aby wykorzystać modele AI, potrzebujesz klucza API do uwierzytelniania. Przechowuj go bezpiecznie w zmiennych środowiskowych.

4. Środowisko programistyczne: Upewnij się, że masz skonfigurowane, działające środowisko .NET (Visual Studio lub inne IDE).

5. Przykładowy dokument: Będziesz potrzebować przykładowych dokumentów Word (np. „Duży dokument.docx”, „Dokument.docx”), aby przetestować podsumowanie.

Teraz, gdy omówiliśmy podstawy, możemy zagłębić się w kod!

## Importuj pakiety

Aby pracować z Aspose.Words i integrować modele Google AI, musisz zaimportować niezbędne przestrzenie nazw. Oto, jak możesz to zrobić:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Teraz, gdy zaimportowałeś już niezbędne pakiety, przeanalizujmy krok po kroku proces podsumowywania dokumentów.

## Krok 1: Konfigurowanie katalogu dokumentów

Zanim będziemy mogli przetworzyć dokumenty, musimy określić, gdzie znajdują się nasze pliki. Ten krok jest kluczowy dla zapewnienia, że Aspose.Words może uzyskać dostęp do dokumentów.

```csharp
// Twój katalog dokumentów
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Twój katalog ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Zastępować`"YOUR_DOCUMENT_DIRECTORY"` I`"YOUR_ARTIFACTS_DIRECTORY"` z rzeczywistymi ścieżkami w systemie, w których przechowywane są Twoje dokumenty. Będzie to stanowić podstawę do odczytywania i zapisywania dokumentów.

## Krok 2: Ładowanie dokumentów

Następnie musimy załadować dokumenty, które chcemy podsumować. W tym przypadku załadujesz dwa dokumenty, które określiliśmy wcześniej.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 Ten`Document` Klasa z Aspose.Words pozwala na załadowanie plików Word do pamięci. Upewnij się, że nazwy plików odpowiadają rzeczywistym dokumentom w Twoim katalogu, w przeciwnym razie wystąpią błędy file not found!

## Krok 3: Pobieranie klucza API

Aby wykorzystać model AI, musisz pobrać swój klucz API. Służy on jako przepustka dostępu do usług Google AI.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Ta linia kodu pobiera klucz API, który zapisałeś w zmiennych środowiskowych. Dobrą praktyką jest trzymanie poufnych informacji, takich jak klucze API, poza kodem ze względów bezpieczeństwa.

## Krok 4: Tworzenie instancji modelu AI

Teraz czas na utworzenie instancji modelu AI. Tutaj możesz wybrać, którego modelu użyć — w tym przykładzie wybieramy model GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 Ten wiersz ustawia model AI, którego będziesz używać do podsumowania dokumentów. Pamiętaj, aby skonsultować się[dokumentacja](https://reference.aspose.com/words/net/) aby uzyskać szczegółowe informacje na temat różnych modeli i ich możliwości.

## Krok 5: Podsumowanie pojedynczego dokumentu

Skupmy się na podsumowaniu pierwszego dokumentu. Możemy wybrać tutaj krótkie podsumowanie.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 W tym kroku używamy`Summarize`metoda z instancji modelu AI, aby uzyskać kondensację pierwszego dokumentu. Długość podsumowania jest ustawiona na krótką, ale możesz ją dostosować w zależności od potrzeb. Na koniec podsumowany dokument jest zapisywany w katalogu artefaktów.

## Krok 6: Podsumowanie wielu dokumentów

Chcesz podsumować wiele dokumentów na raz? Aspose.Words ułatwia to również!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 Tutaj nazywamy`Summarize` ponownie, ale tym razem z tablicą dokumentów. To da ci długie podsumowanie, które obejmuje istotę obu plików. Tak jak poprzednio, wynik jest zapisywany w określonym katalogu artefaktów.

## Wniosek

I masz to! Udało Ci się skonfigurować środowisko do podsumowywania dokumentów przy użyciu Aspose.Words dla .NET i modeli AI Google. Od ładowania dokumentów po tworzenie zwięzłych podsumowań, te kroki zapewniają usprawnione podejście do efektywnego zarządzania dużymi wolumenami tekstu.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words?
Aspose.Words to zaawansowana biblioteka umożliwiająca tworzenie, modyfikowanie i konwertowanie dokumentów Word przy użyciu platformy .NET.

### Jak uzyskać klucz API dla Google AI?
Klucz API zazwyczaj można uzyskać rejestrując się w Google Cloud i włączając niezbędne usługi API.

### Czy mogę podsumować kilka dokumentów jednocześnie?
Tak! Jak pokazano, możesz przekazać tablicę dokumentów do metody podsumowania.

### Jakie rodzaje podsumowań mogę tworzyć?
Możesz wybierać pomiędzy krótkimi, średnimi i długimi podsumowaniami, zależnie od swoich potrzeb.

### Gdzie mogę znaleźć więcej materiałów na temat Aspose.Words?
 Sprawdź[dokumentacja](https://reference.aspose.com/words/net/) aby uzyskać więcej przykładów i wskazówek.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
