---
"description": "Dowiedz się, jak dodawać znaki dwukierunkowe (Bidi) w dokumentach Worda przy użyciu Aspose.Words dla .NET z tego przewodnika. Zapewnij właściwy kierunek tekstu dla treści wielojęzycznych."
"linktitle": "Dodaj znaczniki Bidi w dokumencie Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Dodaj znaczniki Bidi w dokumencie Word"
"url": "/pl/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj znaczniki Bidi w dokumencie Word

## Wstęp

świecie przetwarzania dokumentów tekst dwukierunkowy (Bidi) często może być nieco trudny w zarządzaniu. Dotyczy to zwłaszcza języków, które mają różne kierunki tekstu, takich jak arabski lub hebrajski. Na szczęście Aspose.Words dla .NET ułatwia obsługę takich scenariuszy. W tym samouczku pokażemy, jak dodawać znaczniki Bidi do dokumentu Word za pomocą Aspose.Words dla .NET.

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnij się, że masz następujące elementy:

1. Aspose.Words dla .NET: Musisz mieć zainstalowany Aspose.Words dla .NET. Możesz go pobrać ze strony [Strona pobierania Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework lub .NET Core: Upewnij się, że masz skonfigurowane zgodne środowisko .NET do uruchomienia przykładów.
3. Podstawowa znajomość języka C#: Znajomość języka programowania C# i podstawowych operacji w środowisku .NET.

## Importuj przestrzenie nazw

Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw. Oto, jak możesz je uwzględnić w swoim projekcie:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Podzielmy proces dodawania znaczników Bidi w dokumencie Word na jasne kroki. Każdy krok poprowadzi Cię przez kod i jego cel.

## Krok 1: Skonfiguruj swój dokument

Zacznij od utworzenia nowej instancji `Document` klasa i `DocumentBuilder` aby dodać treść do dokumentu.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Utwórz dokument i dodaj treść
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

W tym kroku zainicjujesz nowy dokument Word i skonfigurujesz `DocumentBuilder` aby ułatwić wstawianie treści.

## Krok 2: Dodaj zawartość do dokumentu

Następnie dodaj trochę tekstu do dokumentu. Tutaj dodamy tekst w różnych językach, aby zilustrować obsługę tekstu Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Tutaj najpierw dodajemy standardową angielską frazę. Następnie włączamy formatowanie tekstu Bidi dla kolejnego tekstu, który jest napisany po hebrajsku i arabsku. To pokazuje, jak włączyć tekst dwukierunkowy.

## Krok 3: Skonfiguruj opcje zapisu dla znaczników Bidi

Aby mieć pewność, że znaki Bidi zostaną poprawnie zapisane w dokumencie, należy skonfigurować `TxtSaveOptions` i włącz `AddBidiMarks` opcja.

```csharp
// Dodaj znaki Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

W tym kroku tworzymy instancję `TxtSaveOptions` i ustaw `AddBidiMarks` nieruchomość do `true`. Dzięki temu znaczniki Bidi zostaną uwzględnione podczas zapisywania dokumentu jako pliku tekstowego.

## Wniosek

Dodawanie znaczników Bidi do dokumentów Word może być kluczowym krokiem w przypadku treści wielojęzycznych, które obejmują języki o różnych kierunkach tekstu. Dzięki Aspose.Words dla .NET proces ten jest prosty i wydajny. Postępując zgodnie z powyższymi krokami, możesz mieć pewność, że Twoje dokumenty poprawnie przedstawiają tekst Bidi, zwiększając czytelność i dokładność.

## Najczęściej zadawane pytania

### Czym są znaki Bidi i dlaczego są ważne?
Znaki Bidi to specjalne znaki używane do kontrolowania kierunku tekstu w dokumentach. Są niezbędne do prawidłowego wyświetlania języków czytanych od prawej do lewej, takich jak arabski i hebrajski.

### Czy mogę użyć Aspose.Words dla .NET do obsługi innych typów problemów z kierunkiem tekstu?
Tak, Aspose.Words for .NET zapewnia wszechstronne wsparcie dla różnych kierunków i formatowania tekstu, w tym dla języków pisanych od prawej do lewej i od lewej do prawej.

### Czy możliwe jest zastosowanie formatowania BiDi tylko do wybranych części dokumentu?
Tak, możesz stosować formatowanie BiDi w określonych akapitach lub sekcjach dokumentu, jeśli zajdzie taka potrzeba.

### W jakich formatach mogę zapisać dokument ze znakami Bidi?
W podanym przykładzie dokument jest zapisany jako plik tekstowy. Jednak Aspose.Words obsługuje również zapisywanie dokumentów w różnych formatach, zachowując jednocześnie znaki Bidi.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words dla .NET?
Więcej informacji na temat Aspose.Words dla .NET można znaleźć w [Dokumentacja Aspose](https://reference.aspose.com/words/net/) i uzyskaj dostęp [Forum wsparcia](https://forum.aspose.com/c/words/8) Aby uzyskać dodatkową pomoc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}