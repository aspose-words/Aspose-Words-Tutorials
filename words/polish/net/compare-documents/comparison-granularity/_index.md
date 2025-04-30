---
"description": "Poznaj funkcję Aspose.Words for .NET umożliwiającą porównywanie dokumentów znak po znaku i raportowanie wprowadzonych zmian."
"linktitle": "Porównanie granularności w dokumencie Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Porównanie granularności w dokumencie Word"
"url": "/pl/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Porównanie granularności w dokumencie Word

Poniżej znajduje się przewodnik krok po kroku objaśniający poniższy kod źródłowy w języku C#, który wykorzystuje funkcję porównywania szczegółowości w dokumencie Word programu Aspose.Words dla platformy .NET.

## Krok 1: Wprowadzenie

Funkcja Compare Granularity w Aspose.Words for .NET umożliwia porównywanie dokumentów na poziomie znaków. Oznacza to, że każdy znak zostanie porównany, a zmiany zostaną odpowiednio zgłoszone.

## Krok 2: Konfigurowanie środowiska

Zanim zaczniesz, musisz skonfigurować środowisko programistyczne do pracy z Aspose.Words dla .NET. Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words i odpowiedni projekt C#, w którym możesz osadzić kod.

## Krok 3: Dodaj wymagane zestawy

Aby użyć funkcji Compare Granularity w Aspose.Words dla .NET, musisz dodać niezbędne zestawy do swojego projektu. Upewnij się, że masz właściwe odwołania do Aspose.Words w swoim projekcie.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Krok 4: Tworzenie dokumentów

tym kroku utworzymy dwa dokumenty przy użyciu klasy DocumentBuilder. Dokumenty te zostaną użyte do porównania.

```csharp
// Utwórz dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Utwórz dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Krok 5: Konfigurowanie opcji porównania

W tym kroku skonfigurujemy opcje porównania, aby określić granularność porównania. Tutaj użyjemy granularności na poziomie znaku.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Krok 6: Porównanie dokumentów

Teraz porównajmy dokumenty używając metody Compare klasy Document. Zmiany zostaną zapisane w dokumencie A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

Ten `Compare` Metoda porównuje dokument A z dokumentem B i zapisuje zmiany w dokumencie A. Można określić nazwisko autora i datę porównania w celach informacyjnych.

## Wniosek

W tym artykule przyjrzeliśmy się funkcji Compare Granularity programu Aspose.Words dla .NET. Funkcja ta umożliwia porównywanie dokumentów na poziomie znaków i raportowanie zmian. Możesz wykorzystać tę wiedzę do wykonywania szczegółowych porównań dokumentów w swoich projektach.

### Przykładowy kod źródłowy dla Granularności porównania przy użyciu Aspose.Words dla .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Wniosek

W tym samouczku przyjrzeliśmy się funkcji Comparison Granularity programu Aspose.Words for .NET. Funkcja ta umożliwia określenie poziomu szczegółowości podczas porównywania dokumentów. Wybierając różne poziomy szczegółowości, możesz wykonywać szczegółowe porównania na poziomie znaku, słowa lub bloku, w zależności od konkretnych wymagań. Aspose.Words for .NET zapewnia elastyczną i wydajną możliwość porównywania dokumentów, ułatwiając identyfikację różnic w dokumentach o różnych poziomach szczegółowości.

### Najczęściej zadawane pytania

#### P: Jaki jest cel stosowania granularności porównawczej w Aspose.Words dla .NET?

A: Granularność porównania w Aspose.Words dla .NET pozwala określić poziom szczegółowości podczas porównywania dokumentów. Dzięki tej funkcji możesz porównywać dokumenty na różnych poziomach, takich jak poziom znaku, poziom słowa, a nawet poziom bloku. Każdy poziom szczegółowości zapewnia inny poziom szczegółowości w wynikach porównania.

#### P: Jak korzystać z granularności porównawczej w Aspose.Words dla .NET?

A: Aby użyć granularności porównawczej w Aspose.Words dla platformy .NET, wykonaj następujące kroki:
1. Skonfiguruj środowisko programistyczne za pomocą biblioteki Aspose.Words.
2. Dodaj niezbędne zestawy do swojego projektu, odwołując się do Aspose.Words.
3. Utwórz dokumenty, które chcesz porównać, korzystając z `DocumentBuilder` klasa.
4. Skonfiguruj opcje porównania, tworząc `CompareOptions` obiekt i ustawienie `Granularity` nieruchomość do pożądanego poziomu (np. `Granularity.CharLevel` do porównania na poziomie postaci).
5. Użyj `Compare` metodę na jednym dokumencie, przekazując drugi dokument i `CompareOptions` obiekt jako parametry. Ta metoda porówna dokumenty na podstawie określonej szczegółowości i zapisze zmiany w pierwszym dokumencie.

#### P: Jakie poziomy szczegółowości porównania są dostępne w Aspose.Words dla platformy .NET?

A: Aspose.Words dla platformy .NET zapewnia trzy poziomy szczegółowości porównania:
- `Granularity.CharLevel`:Porównuje dokumenty na poziomie znaków.
- `Granularity.WordLevel`:Porównuje dokumenty na poziomie słów.
- `Granularity.BlockLevel`:Porównuje dokumenty na poziomie bloków.

#### P: Jak mogę interpretować wyniki porównania z uwzględnieniem szczegółowości na poziomie znaków?

A: Przy granularności na poziomie znaku każdy znak w porównywanych dokumentach jest analizowany pod kątem różnic. Wyniki porównania pokażą zmiany na poziomie pojedynczego znaku, w tym dodatki, usunięcia i modyfikacje.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}