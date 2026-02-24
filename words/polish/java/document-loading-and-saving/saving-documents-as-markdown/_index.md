---
date: 2026-02-24
description: Dowiedz się, jak konwertować dokumenty Word na markdown przy użyciu Aspose.Words
  for Java. Ten przewodnik obejmuje wyrównywanie tabel, obsługę obrazów oraz sposób
  zapisywania dokumentu jako markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Konwertuj Word na Markdown przy użyciu Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konwertuj Word do Markdown przy użyciu Aspose.Words for Java

## Wprowadzenie do konwersji Word do Markdown przy użyciu Aspose.Words for Java

W tym samouczku krok po kroku nauczysz się **jak konwertować Word do Markdown** przy użyciu potężnego API Aspose.Words for Java. Markdown to lekki język znaczników, na którym opiera się wielu programistów i platformy treści, aby tworzyć czystą, czytelną dokumentację. Po zakończeniu tego przewodnika będziesz w stanie wziąć dowolny plik `.docx`, zachować tabele, obrazy i formatowanie oraz wyeksportować go jako plik `.md` gotowy do generatorów stron statycznych, README‑ów na GitHubie lub dowolnego przepływu pracy przyjaznego markdownowi.

## Szybkie odpowiedzi
- **Jakiej biblioteki potrzebuję?** Aspose.Words for Java (`aspose-words.jar`).
- **Czy mogę dostosować wyrównanie tabel?** Tak – użyj `TableContentAlignment` w `MarkdownSaveOptions`.
- **Jak obsługiwane są obrazy?** Ustaw folder obrazów za pomocą `setImagesFolder()`; biblioteka tworzy linki względne.
- **Czy potrzebna jest licencja do produkcji?** Licencja komercyjna jest wymagana przy użyciu nie‑trial.
- **Czy jest kompatybilny z Java 17?** Tak, biblioteka obsługuje Java 8 i nowsze.

## Co to jest konwersja Word do Markdown?

Konwersja Word do Markdown oznacza przekształcenie bogatego formatowania dokumentu Microsoft Word w prostą składnię markdown. Proces ten zachowuje nagłówki, listy, tabele i odwołania do obrazów, jednocześnie usuwając binarne formatowanie, co czyni treść przenośną i przyjazną systemom kontroli wersji.

## Dlaczego warto używać Aspose.Words for Java do zapisywania dokumentu jako markdown?

* **Pełna wierność** – tabele, obrazy i złożone układy są zachowane.
* **Precyzyjna kontrola** – możesz dostosować wyrównanie tabel, ścieżki obrazów i nie tylko.
* **Brak zewnętrznych zależności** – biblioteka działa od razu, bez konieczności instalacji Office.
* **Wieloplatformowość** – działa na Windows, Linux i macOS z dowolnym środowiskiem uruchomieniowym Javy.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

- Zainstalowany Java Development Kit (JDK) na swoim systemie.
- Bibliotekę Aspose.Words for Java. Możesz ją pobrać [tutaj](https://releases.aspose.com/words/java/).

## Przewodnik krok po kroku

### Krok 1: Utwórz dokument Word, który zostanie skonwertowany

Najpierw budujemy prosty dokument Word zawierający tabelę dwuczęściową. Ten przykład demonstruje, jak wyrównanie akapitu w komórkach tabeli jest zachowywane, gdy później **zapisujemy dokument jako markdown**.

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

### Krok 2: Dostosuj wyrównanie zawartości tabeli

Aspose.Words for Java pozwala kontrolować, jak komórki tabeli są wyrównane w generowanym markdownie. Użyj właściwości `TableContentAlignment`, aby **dostosować wyrównanie tabeli** do lewej, prawej, środka lub pozwolić bibliotece automatycznie zdecydować na podstawie pierwszego akapitu w każdej kolumnie.

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

Przełączając to ustawienie, możesz **eksportować tabele Word do markdown** z dokładnym wyrównaniem potrzebnym dla dalszych silników renderujących.

### Krok 3: Obsługa obrazów podczas konwersji

Gdy źródłowy dokument Word zawiera obrazy, musisz wskazać Aspose.Words, gdzie umieścić wyeksportowane pliki graficzne. Metoda `setImagesFolder` w `MarkdownSaveOptions` definiuje folder, w którym będą przechowywane zasoby obrazów, a markdown będzie zawierał linki względne do tych plików.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Zastąp `"document_with_images.docx"` ścieżką do swojego pliku źródłowego oraz `"images_folder/"` żądanym folderem wyjściowym dla obrazów.

### Pełny kod źródłowy dla wszystkich scenariuszy

Poniżej znajduje się skonsolidowany przykład, który pokazuje, jak **automatycznie wyrównać tabele**, **dostosować wyrównanie** oraz **ustawić folder obrazów** w jednej metodzie. Ten fragment odzwierciedla oryginalny kod samouczka i działa bez zmian.

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

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Obrazy wyświetlają się jako zepsute linki | `setImagesFolder` nie ustawiono lub ścieżka folderu jest niepoprawna | Sprawdź, czy ścieżka folderu jest prawidłowa i czy folder jest zapisywalny |
| Wyrównanie tabeli wygląda niepoprawnie | Nieprawidłowa wartość `TableContentAlignment` | Użyj `TableContentAlignment.AUTO`, aby pozwolić pierwszemu akapitowi zdecydować, lub ustaw explicite LEFT/RIGHT/CENTER |
| Plik wyjściowy jest pusty | Opcje zapisu nie zostały przekazane do `doc.save()` | Upewnij się, że przekazujesz instancję `MarkdownSaveOptions` do metody `save` |
| Nieobsługiwane funkcje Word (np. SmartArt) | Markdown nie może przedstawić niektórych złożonych obiektów | Przekonwertuj te elementy na obrazy przed zapisem lub uprość dokument źródłowy |

## Najczęściej zadawane pytania

**Q: Jak zainstalować Aspose.Words for Java?**  
A: Aspose.Words for Java można zainstalować, dołączając bibliotekę do projektu Java. Bibliotekę możesz pobrać [tutaj](https://releases.aspose.com/words/java/) i postępować zgodnie z instrukcjami instalacji zamieszczonymi w dokumentacji.

**Q: Czy mogę konwertować złożone dokumenty Word z tabelami i obrazami do Markdown?**  
A: Tak, Aspose.Words for Java obsługuje konwersję złożonych dokumentów Word zawierających tabele, obrazy i różne elementy formatowania do Markdown. Możesz dostosować wynikowy markdown zgodnie ze złożonością swojego dokumentu.

**Q: Jak mogę obsługiwać obrazy w plikach Markdown?**  
A: Aby włączyć obrazy w plikach Markdown, ustaw ścieżkę folderu obrazów przy użyciu metody `setImagesFolder` w `MarkdownSaveOptions`. Upewnij się, że pliki graficzne znajdują się w określonym folderze, a Aspose.Words for Java zajmie się odwołaniami do obrazów.

**Q: Czy dostępna jest wersja próbna Aspose.Words for Java?**  
A: Tak, wersję próbną Aspose.Words for Java można uzyskać na stronie Aspose. Wersja próbna pozwala ocenić możliwości biblioteki przed zakupem licencji.

**Q: Gdzie mogę znaleźć więcej przykładów i dokumentacji?**  
A: Aby uzyskać więcej przykładów, dokumentację i szczegółowe informacje o Aspose.Words for Java, odwiedź [dokumentację](https://reference.aspose.com/words/java/).

## Podsumowanie

W tym przewodniku omówiliśmy wszystko, co potrzebne, aby **konwertować Word do Markdown** przy użyciu Aspose.Words for Java: tworzenie dokumentu źródłowego, **dostosowanie wyrównania tabel** oraz obsługę obrazów przy odpowiedniej konfiguracji folderu. Dzięki tym technikom możesz niezawodnie eksportować treść Worda do markdownu dla blogów, witryn dokumentacyjnych lub dowolnej platformy konsumującej markdown.

---

**Ostatnia aktualizacja:** 2026-02-24  
**Testowano z:** Aspose.Words for Java 24.12 (najnowsza w momencie pisania)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}