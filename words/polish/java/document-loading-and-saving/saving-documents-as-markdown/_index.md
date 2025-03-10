---
title: Zapisywanie dokumentów jako Markdown w Aspose.Words dla Java
linktitle: Zapisywanie dokumentów jako Markdown
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak konwertować dokumenty Word do Markdown za pomocą Aspose.Words for Java. Ten przewodnik krok po kroku obejmuje wyrównywanie tabeli, obsługę obrazów i wiele więcej.
weight: 18
url: /pl/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisywanie dokumentów jako Markdown w Aspose.Words dla Java


## Wprowadzenie do zapisywania dokumentów jako Markdown w Aspose.Words dla Java

W tym przewodniku krok po kroku pokażemy, jak zapisywać dokumenty jako Markdown przy użyciu Aspose.Words for Java. Markdown to lekki język znaczników, który jest powszechnie używany do formatowania dokumentów tekstowych. Dzięki Aspose.Words for Java możesz łatwo przekonwertować dokumenty Word na format Markdown. Omówimy różne aspekty zapisywania plików Markdown, w tym wyrównanie zawartości tabeli i obsługę obrazów.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że spełniasz następujące wymagania wstępne:

- Java Development Kit (JDK) zainstalowany w Twoim systemie.
-  Biblioteka Aspose.Words dla Java. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/java/).

## Krok 1: Tworzenie dokumentu Word

Zacznijmy od utworzenia dokumentu Word, który później przekonwertujemy do formatu Markdown. Możesz dostosować ten dokument zgodnie ze swoimi wymaganiami.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Wstaw tabelę z dwiema komórkami
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Zapisz dokument jako Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 W tym przykładzie tworzymy prostą tabelę z dwiema komórkami i ustawiamy wyrównanie akapitów w tych komórkach. Następnie zapisujemy dokument jako Markdown za pomocą`MarkdownSaveOptions`.

## Krok 2: Dostosuj wyrównanie zawartości tabeli

Aspose.Words for Java pozwala dostosować wyrównanie zawartości tabeli podczas zapisywania jako Markdown. Zawartość tabeli można wyrównać do lewej, prawej, środka lub ustawić ją automatycznie na podstawie pierwszego akapitu w każdej kolumnie tabeli.

Oto jak dostosować wyrównanie zawartości tabeli:

```java
// Ustaw wyrównanie zawartości tabeli do lewej
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Ustaw wyrównanie zawartości tabeli do prawej
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Ustaw wyrównanie zawartości tabeli do środka
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Ustaw wyrównanie zawartości tabeli na automatyczne (określone w pierwszym akapicie)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Zmieniając`TableContentAlignment` Właściwość ta umożliwia kontrolowanie sposobu wyrównywania zawartości tabel podczas konwersji do formatu Markdown.

## Krok 3: Obsługa obrazów

 Aby uwzględnić obrazy w dokumencie Markdown, musisz określić folder, w którym znajdują się obrazy. Aspose.Words for Java pozwala ustawić folder obrazów w`MarkdownSaveOptions`.

Oto jak ustawić folder z obrazami i zapisać dokument z obrazami:

```java
// Załaduj dokument zawierający obrazy
Document doc = new Document("document_with_images.docx");

// Ustaw ścieżkę do folderu ze zdjęciami
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Zapisz dokument ze zdjęciami
doc.save("document_with_images.md", saveOptions);
```

 Pamiętaj o wymianie`"document_with_images.docx"` ze ścieżką do dokumentu Word zawierającego obrazy i`"images_folder/"` z rzeczywistą ścieżką do folderu, w którym przechowywane są Twoje obrazy.

## Kompletny kod źródłowy do zapisywania dokumentów jako Markdown w Aspose.Words dla Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Sprawia, że wszystkie akapity wewnątrz tabeli będą wyrównane.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// W tym przypadku wyrównanie zostanie pobrane z pierwszego akapitu w odpowiedniej kolumnie tabeli.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Wniosek

tym przewodniku przyjrzeliśmy się sposobowi zapisywania dokumentów w formacie Markdown przy użyciu Aspose.Words for Java. Omówiliśmy tworzenie dokumentu Word, dostosowywanie wyrównania zawartości tabeli i obsługę obrazów w plikach Markdown. Teraz możesz wydajnie konwertować dokumenty Word do formatu Markdown, dzięki czemu będą one odpowiednie dla różnych platform wydawniczych i potrzeb dokumentacyjnych.

## Najczęściej zadawane pytania

### Jak zainstalować Aspose.Words dla Java?

 Aspose.Words for Java można zainstalować, włączając bibliotekę do swojego projektu Java. Możesz pobrać bibliotekę z[Tutaj](https://releases.aspose.com/words/java/) i postępuj zgodnie z instrukcjami instalacji podanymi w dokumentacji.

### Czy mogę przekonwertować złożone dokumenty Word zawierające tabele i obrazy do formatu Markdown?

Tak, Aspose.Words for Java obsługuje konwersję złożonych dokumentów Word z tabelami, obrazami i różnymi elementami formatowania do Markdown. Możesz dostosować dane wyjściowe Markdown do złożoności dokumentu.

### Jak radzić sobie z obrazami w plikach Markdown?

 Aby uwzględnić obrazy w plikach Markdown, ustaw ścieżkę folderu obrazów za pomocą`setImagesFolder`metoda w`MarkdownSaveOptions`. Upewnij się, że pliki obrazów są przechowywane w określonym folderze, a Aspose.Words for Java odpowiednio obsłuży odwołania do obrazów.

### Czy jest dostępna wersja próbna Aspose.Words dla Java?

Tak, możesz uzyskać wersję próbną Aspose.Words for Java ze strony internetowej Aspose. Wersja próbna pozwala ocenić możliwości biblioteki przed zakupem licencji.

### Gdzie mogę znaleźć więcej przykładów i dokumentacji?

 Więcej przykładów, dokumentacji i szczegółowych informacji na temat Aspose.Words dla języka Java można znaleźć na stronie[dokumentacja](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
