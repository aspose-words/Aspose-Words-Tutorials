---
date: 2025-12-22
description: „Dowiedz się, jak eksportować markdown, konwertując dokumenty Word na
  Markdown przy użyciu Aspose.Words dla Javy. Ten przewodnik krok po kroku obejmuje
  wyrównywanie tabel, obsługę obrazów i wiele więcej.”
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Jak wyeksportować Markdown przy użyciu Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak wyeksportować Markdown przy użyciu Aspose.Words dla Javy

## Wprowadzenie do eksportu Markdown w Aspose.Words dla Javy

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do zapisywania jako Markdown?** `MarkdownSaveOptions`
- **Czy obrazy mogą być wstawiane automatycznie?** Tak – ustaw folder obrazów za pomocą `setImagesFolder`.
- **Jak kontrolować wyrównanie tabeli?** Użyj `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Jakie są minimalne wymagania?** JDK 8+ oraz biblioteka Aspose.Words dla Javy.
- **Czy dostępna jest wersja próbna?** Tak, pobierz ją ze strony Aspose.

## Co to jest „jak wyeksportować markdown”?
Eksportowanie markdown oznacza wzięcie dokumentu Word w formacie rich‑text (`.docx`) i wygenerowanie pliku tekstowego `.md`, który zachowuje nagłówki, tabele i obrazy w składni Markdown.

## Dlaczego używać Aspose.Words dla Javy do konwersji docx z obrazami?
Aspose.Words obsługuje złożone układy, osadzone obrazy i struktury tabel bez utraty jakości. Daje także precyzyjną kontrolę nad wyjściem Markdown, taką jak wyrównanie tabel i zarządzanie folderem obrazów.

## Wymagania wstępne

- Zainstalowany Java Development Kit (JDK) na twoim systemie.
- Biblioteka Aspose.Words dla Javy. Możesz ją pobrać [tutaj](https://releases.aspose.com/words/java/).

## Krok 1: Utwórz prosty dokument Word

Najpierw stworzymy mały dokument zawierający tabelę. Pozwoli nam to później zademonstrować **dostosowanie wyrównania tabeli**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

W powyższym fragmencie:

1. Tworzymy nowy `Document`.
2. Używamy `DocumentBuilder` do wstawienia tabeli dwuczęściowej.
3. Stosujemy wyrównanie akapitu **right** i **center** w każdej komórce.
4. Zapisujemy plik jako Markdown przy użyciu `MarkdownSaveOptions`.

## Krok 2: Dostosuj wyrównanie zawartości tabeli

Aspose.Words pozwala określić, jak komórki tabeli są renderowane w końcowym Markdown. Możesz wymusić wyrównanie left, right, center lub pozwolić bibliotece zdecydować automatycznie na podstawie pierwszego akapitu w każdej kolumnie.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Zmieniając właściwość `TableContentAlignment`, kontrolujesz **dostosowanie wyrównania tabeli** w wyjściu Markdown.

## Krok 3: Obsługa obrazów przy eksporcie do markdown

Gdy dokument zawiera obrazy, chcesz, aby te obrazy pojawiały się poprawnie w wygenerowanym pliku `.md`. Ustaw folder, w którym Aspose.Words ma zapisać wyodrębnione obrazy.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Zastąp `"document_with_images.docx"` ścieżką do swojego pliku źródłowego oraz `"images_folder/"` lokalizacją, w której chcesz przechowywać obrazy. Wynikowy Markdown będzie zawierał linki do obrazów wskazujące na ten folder, co umożliwi **obsługę obrazów w markdown** bezproblemowo.

## Pełny kod źródłowy do zapisywania dokumentów jako Markdown w Aspose.Words dla Javy

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Typowe problemy i rozwiązania

| Problem | Rozwiązanie |
|-------|----------|
| Obrazy nie pojawiają się w pliku `.md` | Sprawdź, czy `setImagesFolder` wskazuje na zapisywalny katalog oraz czy folder jest poprawnie odwoływany w wygenerowanym Markdown. |
| Wyrównanie tabeli wygląda niepoprawnie | Użyj `TableContentAlignment.AUTO`, aby Aspose.Words określił najlepsze wyrównanie na podstawie pierwszego akapitu w każdej kolumnie. |
| Plik wyjściowy jest pusty | Upewnij się, że obiekt `Document` rzeczywiście zawiera treść przed wywołaniem `save`. |

## Najczęściej zadawane pytania

**Q: Jak zainstalować Aspose.Words dla Javy?**  
A: Aspose.Words dla Javy można zainstalować, dołączając bibliotekę do swojego projektu Java. Możesz pobrać bibliotekę [tutaj](https://releases.aspose.com/words/java/) i postępować zgodnie z instrukcjami instalacji zamieszczonymi w dokumentacji.

**Q: Czy mogę konwertować złożone dokumenty Word z tabelami i obrazami do Markdown?**  
A: Tak, Aspose.Words dla Javy obsługuje konwersję złożonych dokumentów Word zawierających tabele, obrazy i różne elementy formatowania do Markdown. Możesz dostosować wyjście Markdown do złożoności swojego dokumentu.

**Q: Jak mogę obsługiwać obrazy w plikach Markdown?**  
A: Ustaw ścieżkę folderu obrazów za pomocą metody `setImagesFolder` w `MarkdownSaveOptions`. Upewnij się, że pliki obrazów są przechowywane w określonym folderze; Aspose.Words wygeneruje odpowiednie linki do obrazów w Markdown.

**Q: Czy dostępna jest wersja próbna Aspose.Words dla Javy?**  
A: Tak, wersję próbną Aspose.Words dla Javy można uzyskać na stronie Aspose. Wersja próbna pozwala ocenić możliwości biblioteki przed zakupem licencji.

**Q: Gdzie mogę znaleźć więcej przykładów i dokumentację?**  
A: Aby uzyskać więcej przykładów, dokumentację i szczegółowe informacje o Aspose.Words dla Javy, odwiedź [dokumentację](https://reference.aspose.com/words/java/).

---

**Ostatnia aktualizacja:** 2025-12-22  
**Testowano z:** Aspose.Words for Java 24.12 (najnowsza w momencie pisania)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}