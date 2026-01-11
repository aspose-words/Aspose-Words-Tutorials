---
date: 2026-01-11
description: Dowiedz się, jak oczyścić dokument Word przy użyciu opcji czyszczenia
  Aspose.Words dla Javy, w tym usuwania pustych akapitów, pustych wierszy tabeli i
  nieużywanych pól.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Czyszczenie dokumentu Word przy użyciu opcji czyszczenia Aspose.Words (Java)
url: /pl/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Czyszczenie dokumentu Word przy użyciu opcji czyszczenia Aspose.Words (Java)

W tym samouczku dowiesz się, jak **czyścić dokumenty Word** przy użyciu Aspose.Words dla Javy. Niezależnie od tego, czy generujesz faktury, umowy, czy masowe raporty ze scalaniem korespondencji, niechciane puste akapity, nieużywane pola lub puste wiersze tabel mogą sprawić, że końcowy wynik będzie wyglądał nieprofesjonalnie. Przejdziemy krok po kroku przez każdą opcję czyszczenia, pokażemy dokładny kod, którego potrzebujesz, i wyjaśnimy *dlaczego* każde ustawienie ma znaczenie, abyś mógł tworzyć dopracowane dokumenty za każdym razem.

## Szybkie odpowiedzi
- **Co oznacza „czyszczenie dokumentu Word”?** Usuwanie pustych akapitów, nieużywanych regionów scalania, pustych wierszy tabel i innych zbędnych elementów po operacji scalania korespondencji.  
- **Która opcja czyszczenia usuwa puste akapity?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Jak mogę usunąć puste wiersze tabel?** Użyj `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Czy mogę pozbyć się pól, które nigdy nie zostały wypełnione?** Tak – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` lub `REMOVE_EMPTY_FIELDS`.  
- **Czy potrzebna jest licencja do uruchomienia tych przykładów?** Darmowa wersja próbna wystarczy do oceny; licencja komercyjna jest wymagana w środowisku produkcyjnym.

## Co to jest „czyszczenie dokumentu Word” w kontekście scalania korespondencji?
Podczas scalania korespondencji Aspose.Words wstawia dane do pól i regionów scalania. Jeśli niektóre pola otrzymają `null` lub pusty ciąg znaków, dokument może zawierać niechciane akapity, puste tabele lub regiony zastępcze. **Opcje czyszczenia** automatycznie usuwają te artefakty, pozostawiając czysty, gotowy do druku dokument.

## Dlaczego warto używać opcji czyszczenia?
- **Profesjonalny wygląd:** Brak pustych linii i osieroconych tabel.  
- **Mniejszy rozmiar pliku:** Usuwanie nieużywanych elementów zmniejsza wagę dokumentu.  
- **Uproszczone przetwarzanie dalsze:** Czyste dokumenty łatwiej konwertować do PDF, HTML i innych formatów.  
- **Oszczędność czasu:** Jednolinijkowe ustawienia zastępują ręczne skrypty post‑procesowe.

## Wymagania wstępne
- Środowisko programistyczne Java (JDK 8+).  
- Biblioteka Aspose.Words dla Javy – pobierz ją [tutaj](https://releases.aspose.com/words/java/).  
- Podstawowa znajomość koncepcji scalania korespondencji.

## Przewodnik krok po kroku

### Krok 1: Jak usunąć puste akapity (Java)
Najpierw pokażemy, jak wyeliminować akapity, które nie zawierają widocznego tekstu. Jest to szczególnie przydatne, gdy pole scalania rozwiązuje się do `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Co się tutaj dzieje?**  
- `REMOVE_EMPTY_PARAGRAPHS` nakazuje Aspose.Words usunąć każdy akapit, który po scaleniu pozostaje pusty.  
- Włączenie `cleanupParagraphsWithPunctuationMarks` usuwa również akapity składające się wyłącznie z znaków interpunkcyjnych (np. „?”).

### Krok 2: Jak usunąć niepołączone regiony
Jeśli region scalania nie ma odpowiadających danych, możesz go całkowicie odrzucić.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Dlaczego to ważne:**  
Nieużywane regiony często pozostawiają puste sekcje lub niepotrzebne nagłówki. Flaga `REMOVE_UNUSED_REGIONS` usuwa je automatycznie.

### Krok 3: Jak usunąć puste pola

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Krok 4: Jak usunąć nieużywane pola

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Krok 5: Jak usunąć pola zawierające

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Krok 6: Jak usunąć puste wiersze tabel

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Typowe problemy i rozwiązywanie
- **Akapity nie są usuwane:** Upewnij się, że `setCleanupParagraphsWithPunctuationMarks(true)` jest wywoływane *po* ustawieniu opcji czyszczenia.  
- **Puste wiersze tabel pozostają:** Sprawdź, czy komórki tabel naprawdę zawierają puste ciągi (a nie białe znaki).  
- **Nieużywane pola pozostają:** Zweryfikuj, czy używasz właściwej wartości wyliczeniowej (`REMOVE_UNUSED_FIELDS`) i czy pola scalania nie są przypadkowo wypełniane w innym miejscu.

## Najczęściej zadawane pytania

**P: Jaka jest różnica między `REMOVE_EMPTY_FIELDS` a `REMOVE_UNUSED_FIELDS`?**  
O: `REMOVE_EMPTY_FIELDS` usuwa pola, które podczas scalania otrzymały pusty ciąg znaków lub `null`, natomiast `REMOVE_UNUSED_FIELDS` usuwa pola, które nigdy nie zostały odwołane w operacji scalania.

**P: Czy mogę połączyć wiele opcji czyszczenia?**  
O: Tak. Metoda `setCleanupOptions` przyjmuje bitowy OR wartości wyliczeniowych, co pozwala wyczyścić akapity, tabele i regiony w jednym wywołaniu.

**P: Czy włączenie `cleanupParagraphsWithPunctuationMarks` wpływa na normalny tekst?**  
O: Usuwa wyłącznie akapity składające się wyłącznie ze znaków interpunkcyjnych (np. „?” lub „---”). Zwykłe zdania pozostają nienaruszone.

**P: Czy można dostosować, które znaki interpunkcyjne są brane pod uwagę?**  
O: Obecne API używa zdefiniowanego zestawu znaków interpunkcyjnych. Aby uzyskać zachowanie niestandardowe, trzeba będzie przeprowadzić post‑procesowanie dokumentu po scaleniu.

**P: Czy te opcje czyszczenia działają przy konwersji do PDF?**  
O: Zdecydowanie. Po wyczyszczeniu dokumentu Word możesz go konwertować do PDF, HTML lub dowolnego innego obsługiwanego formatu bez przenoszenia niechcianych elementów.

## Podsumowanie
Masz teraz kompletny zestaw narzędzi do **czyszczenia dokumentów Word** podczas scalania korespondencji przy użyciu Aspose.Words dla Javy. Wybierając odpowiednie `MailMergeCleanupOptions`, możesz automatycznie usuwać puste akapity, puste wiersze tabel, nieużywane pola i wiele więcej — pozostawiając elegancki, gotowy do produkcji dokument za każdym razem.

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}