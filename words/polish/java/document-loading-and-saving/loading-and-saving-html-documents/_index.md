---
date: 2025-12-20
description: Dowiedz się, jak ładować HTML i konwertować HTML na DOCX przy użyciu
  Aspose.Words for Java. Przewodnik krok po kroku pokazuje, jak zapisywać pliki DOCX
  i używać strukturalnych znaczników dokumentu.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Jak wczytać HTML i zapisać jako DOCX przy użyciu Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak wczytać HTML i zapisać jako DOCX przy użyciu Aspose.Words for Java

## Wprowadzenie do wczytywania i zapisywania dokumentów HTML z Aspose.Words for Java

W tym artykule przyjrzymy się **jak wczytać html** i zapisać go jako plik DOCX przy użyciu biblioteki Aspose.Words for Java. Aspose.Words to potężne API umożliwiające programowe manipulowanie dokumentami Word i zawiera rozbudowane wsparcie dla importu/eksportu HTML. Przeprowadzimy Cię przez cały proces, od ustawienia opcji wczytywania po zapis wyniku jako dokumentu Word.

## Szybkie odpowiedzi
- **Jaka jest główna klasa do wczytywania HTML?** `Document` wraz z `HtmlLoadOptions`.
- **Która opcja włącza Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Czy mogę konwertować HTML do DOCX w jednym kroku?** Tak – wczytaj HTML i wywołaj `doc.save(...".docx")`.
- **Czy potrzebna jest licencja do rozwoju?** Darmowa wersja próbna wystarczy do testów; licencja komercyjna jest wymagana w produkcji.
- **Jakiej wersji Javy wymaga?** Obsługiwana jest Java 8 lub nowsza.

## Co oznacza „jak wczytać html” w kontekście Aspose.Words?
Wczytywanie HTML oznacza odczytanie łańcucha lub pliku HTML i przekształcenie go w obiekt `Document` Aspose.Words. Ten obiekt można następnie edytować, formatować lub zapisać w dowolnym formacie obsługiwanym przez API, takim jak DOCX, PDF czy RTF.

## Dlaczego warto używać Aspose.Words do konwersji HTML‑do‑DOCX?
- **Zachowuje układ** – tabele, listy i obrazy pozostają nienaruszone.
- **Obsługuje Structured Document Tags** – idealne do tworzenia kontrolek treści w Wordzie.
- **Nie wymaga Microsoft Office** – działa na dowolnym serwerze lub w chmurze.
- **Wysoka wydajność** – szybko przetwarza duże pliki HTML.

## Wymagania wstępne

1. **Biblioteka Aspose.Words for Java** – pobierz ją z [here](https://releases.aspose.com/words/java/).
2. **Środowisko programistyczne Java** – zainstalowane i skonfigurowane JDK 8+.
3. **Podstawowa znajomość Java I/O** – użyjemy `ByteArrayInputStream`, aby przekazać łańcuch HTML.

## Jak wczytać dokumenty HTML

Poniżej znajduje się zwięzły przykład demonstrujący wczytywanie fragmentu HTML przy włączonej funkcji **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Wyjaśnienie**

- Tworzymy łańcuch `HTML`, który zawiera prostą kontrolkę `<select>`.
- `HtmlLoadOptions` pozwala określić, jak HTML ma być interpretowany. Ustawienie preferowanego typu kontroli na `STRUCTURED_DOCUMENT_TAG` powoduje, że Aspose.Words konwertuje kontrolki formularza HTML na kontrolki treści w Wordzie.
- Konstruktor `Document` odczytuje HTML z `ByteArrayInputStream` przy użyciu kodowania UTF‑8.

## Jak zapisać jako DOCX (konwersja HTML do DOCX)

Po wczytaniu HTML do obiektu `Document`, zapisanie go jako plik DOCX jest proste:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Zastąp `"Your Directory Path"` rzeczywistą ścieżką folderu, w którym ma się pojawić plik wyjściowy.

## Pełny kod źródłowy do wczytywania i zapisywania dokumentów HTML

Poniżej znajduje się kompletny, gotowy do uruchomienia przykład, który łączy kroki wczytywania i zapisu. Śmiało skopiuj go do swojego IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Typowe pułapki i wskazówki

| Problem | Dlaczego się pojawia | Jak naprawić |
|-------|----------------|------------|
| **Brak czcionek** | HTML odwołuje się do czcionek, które nie są zainstalowane na serwerze. | Osadź czcionki w DOCX przy użyciu `FontSettings` lub upewnij się, że wymagane czcionki są dostępne. |
| **Obrazy nie wyświetlają się** | Ścieżki względne do obrazów nie mogą zostać rozwiązane. | Użyj pełnych adresów URL lub wczytaj obrazy do `MemoryStream` i ustaw `HtmlLoadOptions.setImageSavingCallback`. |
| **Typ kontroli nie został skonwertowany** | `setPreferredControlType` nie został ustawiony lub ustawiono niewłaściwy enum. | Zweryfikuj, że używasz `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Problemy z kodowaniem** | Łańcuch HTML jest zakodowany innym zestawem znaków. | Zawsze używaj `StandardCharsets.UTF_8` przy konwersji łańcucha na bajty. |

## Najczęściej zadawane pytania

### Jak zainstalować Aspose.Words for Java?
Aspose.Words for Java można pobrać z [here](https://releases.aspose.com/words/java/). Postępuj zgodnie z przewodnikiem instalacji na stronie pobierania, aby dodać pliki JAR do ścieżki klas projektu.

### Czy mogę wczytać złożone dokumenty HTML przy użyciu Aspose.Words?
Tak, Aspose.Words for Java radzi sobie ze złożonym HTML, w tym zagnieżdżonymi tabelami, stylami CSS i interaktywnymi elementami bez JavaScriptu. Dostosuj `HtmlLoadOptions` (np. `setLoadImages` lub `setCssStyleSheetFileName`), aby precyzyjnie kontrolować import.

### Jakie inne formaty dokumentów obsługuje Aspose.Words?
Aspose.Words obsługuje DOC, DOCX, RTF, HTML, PDF, EPUB, XPS i wiele innych. API umożliwia jednowierszowy zapis do dowolnego z tych formatów.

### Czy Aspose.Words nadaje się do automatyzacji dokumentów na poziomie przedsiębiorstwa?
Zdecydowanie. Jest wykorzystywany przez duże firmy do automatycznego generowania raportów, masowej konwersji dokumentów oraz przetwarzania dokumentów po stronie serwera bez zależności od Microsoft Office.

### Gdzie mogę znaleźć więcej dokumentacji i przykładów dla Aspose.Words for Java?
Pełną referencję API oraz dodatkowe samouczki znajdziesz na stronie dokumentacji Aspose.Words for Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Ostatnia aktualizacja:** 2025-12-20  
**Testowane z:** Aspose.Words for Java 24.12 (najnowsza w momencie pisania)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}