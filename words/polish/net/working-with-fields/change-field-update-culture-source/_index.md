---
"description": "Dowiedz się, jak zmienić źródło kultury aktualizacji pola w Aspose.Words dla .NET za pomocą tego przewodnika. Łatwo kontroluj formatowanie daty na podstawie różnych kultur."
"linktitle": "Zmień pole Aktualizacja źródła kultury"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Zmień pole Aktualizacja źródła kultury"
"url": "/pl/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmień pole Aktualizacja źródła kultury

## Wstęp

W tym samouczku zanurzymy się w świat Aspose.Words dla .NET i odkryjemy, jak zmienić źródło kultury aktualizacji pól. Jeśli masz do czynienia z dokumentami Word, które zawierają pola daty i musisz kontrolować, jak te daty są formatowane w oparciu o różne kultury, ten przewodnik jest dla Ciebie. Przeprowadzimy Cię przez proces krok po kroku, upewniając się, że rozumiesz każdą koncepcję i możesz ją skutecznie zastosować w swoich projektach.

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnij się, że masz następujące elementy:

- Aspose.Words dla .NET: Można go pobrać ze strony [Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: dowolne środowisko IDE zgodne z platformą .NET (np. Visual Studio).
- Podstawowa wiedza o języku C#: W tym samouczku zakładamy, że posiadasz podstawową wiedzę na temat programowania w języku C#.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw dla naszego projektu. Dzięki temu będziemy mieć dostęp do wszystkich wymaganych klas i metod dostarczonych przez Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Teraz podzielimy przykład na kilka kroków, aby lepiej zrozumieć, jak zmienić źródło kultury aktualizacji pola w Aspose.Words dla platformy .NET.

## Krok 1: Zainicjuj dokument

Pierwszym krokiem jest utworzenie nowej instancji `Document` klasa i `DocumentBuilder`. Stanowi to podstawę do tworzenia i manipulowania naszym dokumentem Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Wstaw pola z określonymi ustawieniami regionalnymi

Następnie musimy wstawić pola do dokumentu. W tym przykładzie wstawimy dwa pola daty. Ustawimy ustawienia regionalne czcionki na niemieckie (LocaleId = 1031), aby pokazać, jak kultura wpływa na format daty.

```csharp
builder.Font.LocaleId = 1031; // niemiecki
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Krok 3: Ustaw źródło kultury aktualizacji pola

Aby kontrolować kulturę używaną podczas aktualizacji pól, ustawiamy `FieldUpdateCultureSource` własność `FieldOptions` Klasa. Ta właściwość określa, czy kultura jest pobierana z kodu pola czy dokumentu.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Krok 4: Wykonaj korespondencję seryjną

Teraz musimy wykonać korespondencję seryjną, aby wypełnić pola rzeczywistymi danymi. W tym przykładzie ustawimy drugie pole daty (`Date2`) do 1 stycznia 2011 r.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Krok 5: Zapisz dokument

Na koniec zapisujemy dokument do określonego katalogu. Ten krok kończy proces zmiany źródła kultury aktualizacji pola.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Wniosek

masz! Udało Ci się zmienić źródło kultury aktualizacji pola w Aspose.Words dla .NET. Wykonując te kroki, możesz upewnić się, że Twoje dokumenty Word wyświetlają daty i inne wartości pól zgodnie z określonymi ustawieniami kultury. Może to być szczególnie przydatne podczas generowania dokumentów dla odbiorców międzynarodowych.

## Najczęściej zadawane pytania

### Jaki jest cel ustawienia `LocaleId`?
Ten `LocaleId` określa ustawienia kulturowe tekstu, które mają wpływ na sposób formatowania dat i innych danych zależnych od ustawień regionalnych.

### Czy mogę użyć innego ustawienia regionalnego niż niemiecki?
Tak, możesz ustawić `LocaleId` do dowolnego prawidłowego identyfikatora lokalizacji. Na przykład 1033 dla języka angielskiego (Stany Zjednoczone).

### Co się stanie, jeśli nie ustawię `FieldUpdateCultureSource` nieruchomość?
Jeżeli ta właściwość nie jest ustawiona, podczas aktualizacji pól zostaną użyte domyślne ustawienia kulturowe dokumentu.

### Czy można aktualizować pola na podstawie kultury dokumentu, a nie kodu pola?
Tak, możesz ustawić `FieldUpdateCultureSource` Do `FieldUpdateCultureSource.Document` aby użyć ustawień kulturowych dokumentu.

### Jak sformatować daty według innego wzoru?
Możesz zmienić wzorzec formatu daty w `InsertField` metoda poprzez modyfikację `\\@` wartość przełącznika.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}