---
date: 2026-01-16
description: Dowiedz się, jak podświetlać błędy ortograficzne w programie Word przy
  użyciu Aspose.Words for Java oraz odkryj, jak ustawiać liczbę znaków na wiersz,
  dostosowywać opcje widoku i usuwać niepotrzebne style.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Podświetlanie błędów ortograficznych w Wordzie przy użyciu Aspose.Words Java
url: /pl/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Używanie opcji i ustawień dokumentu w Aspose.Words dla Javy

## Wprowadzenie do używania opcji i ustawień dokumentu w Aspose.Words dla Javy

W tym kompleksowym przewodniku dowiesz się **jak podświetlić błędy ortograficzne w Wordzie** przy użyciu Aspose.Words dla Javy, a także opanujesz powiązane ustawienia, takie jak opcje wyświetlania, układ strony i czyszczenie stylów. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, poniższe przykłady pomogą Ci stworzyć solidne, świadome błędów dokumenty, które działają we wszystkich wersjach Worda.

## Szybkie odpowiedzi
- **Jak mogę podświetlić błędy ortograficzne w Wordzie?** Użyj `setShowSpellingErrors(true)` na obiekcie `Document`.  
- **Czy mogę również wyświetlać błędy gramatyczne?** Tak — wywołaj `setShowGrammaticalErrors(true)`.  
- **Jaką metodą ustawia się liczbę znaków w linii?** `getPageSetup().setCharactersPerLine(int)`.  
- **Które API optymalizuje pod konkretną wersję Worda?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Czy istnieje sposób na usunięcie nieużywanych stylów?** Użyj `CleanupOptions` z `setUnusedStyles(true)` i wywołaj `doc.cleanup(options)`.

## Jak podświetlić błędy ortograficzne w Wordzie?

Aspose.Words ułatwia włączenie podświetlania błędów ortograficznych. Gdy dokument zostanie otwarty w Microsoft Word, błędnie napisane słowa pojawiają się z charakterystycznym czerwonym podkreśleniem, pomagając użytkownikom natychmiast zauważyć problemy.

## Jak ustawić liczbę znaków w linii

Kontrolowanie liczby znaków w linii jest niezbędne w układach o stałej szerokości (np. listy kodu lub starsze formularze). Klasa `PageSetup` udostępnia metodę `setCharactersPerLine(int)`, która pozwala precyzyjnie określić tę wartość.

## Jak wyświetlać błędy gramatyczne

Poza ortografią możesz także włączyć wyświetlanie błędów gramatycznych. Jest to przydatne przy tworzeniu treści, które muszą spełniać wytyczne stylu lub przy budowaniu narzędzi do korekty.

## Optimizing Documents for Compatibility

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Jednym z kluczowych aspektów zarządzania dokumentami jest zapewnienie kompatybilności z różnymi wersjami Microsoft Word. Aspose.Words dla Javy oferuje prosty sposób optymalizacji dokumentów pod konkretne wersje Worda. W powyższym przykładzie optymalizujemy dokument pod Word 2016, zapewniając płynną kompatybilność.

## Identifying Grammatical and Spelling Errors

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Dokładność jest kluczowa przy pracy z dokumentami. Aspose.Words dla Javy umożliwia podświetlanie błędów gramatycznych i ortograficznych w dokumentach, co sprawia, że korekta i edycja są bardziej efektywne.

## Cleaning Up Unused Styles and Lists

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Efektywne zarządzanie stylami i listami w dokumencie jest niezbędne dla zachowania spójności dokumentu. Aspose.Words dla Javy pozwala usuwać nieużywane style i listy, zapewniając uporządkowaną i zoptymalizowaną strukturę dokumentu.

## Removing Duplicate Styles

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Zduplikowane style mogą prowadzić do zamieszania i niespójności w dokumentach. Dzięki Aspose.Words dla Javy możesz łatwo usuwać zduplikowane style, utrzymując przejrzystość i spójność dokumentu.

## Customizing Document Viewing Options

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Dostosowanie sposobu wyświetlania dokumentów jest kluczowe. Aspose.Words dla Javy umożliwia ustawienie różnych opcji wyświetlania, takich jak układ strony i procent powiększenia, aby zwiększyć czytelność dokumentu.

## Configuring Document Page Setup

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Precyzyjne ustawienia strony są kluczowe dla formatowania dokumentu. Aspose.Words dla Javy umożliwia ustawienie trybów układu, **liczby znaków w linii** oraz liczby linii na stronę, zapewniając atrakcyjny wygląd dokumentów.

## Setting Editing Languages

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Języki edycji odgrywają istotną rolę w przetwarzaniu dokumentów. Dzięki Aspose.Words dla Javy możesz ustawiać i dostosowywać języki edycji, aby odpowiadały potrzebom językowym Twojego dokumentu.

## Conclusion

W tym przewodniku przyjrzeliśmy się różnym opcjom i ustawieniom dokumentu dostępnym w Aspose.Words dla Javy. Od optymalizacji i wyświetlania błędów po czyszczenie stylów i opcje wyświetlania, ta potężna biblioteka oferuje szerokie możliwości zarządzania i dostosowywania Twoich dokumentów.

## FAQ

### Jak zoptymalizować dokument pod konkretną wersję Worda?

Aby zoptymalizować dokument pod konkretną wersję Worda, użyj metody `optimizeFor` i określ żądaną wersję. Na przykład, aby zoptymalizować pod Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Jak mogę podświetlić błędy gramatyczne i ortograficzne w dokumencie?

Możesz włączyć wyświetlanie błędów gramatycznych i ortograficznych w dokumencie, używając poniższego kodu:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Jaki jest cel czyszczenia nieużywanych stylów i list?

Czyszczenie nieużywanych stylów i list pomaga utrzymać czystą i uporządkowaną strukturę dokumentu. Usuwa niepotrzebny bałagan, poprawiając czytelność i spójność dokumentu.

### Jak mogę usunąć zduplikowane style z dokumentu?

Aby usunąć zduplikowane style z dokumentu, użyj metody `cleanup` z opcją `duplicateStyle` ustawioną na `true`. Oto przykład:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Jak dostosować opcje wyświetlania dokumentu?

Możesz dostosować opcje wyświetlania dokumentu, używając klasy `ViewOptions`. Na przykład, aby ustawić typ widoku na układ strony i powiększenie na 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Dodatkowe wskazówki i typowe pułapki

- **Włącz zarówno sprawdzanie ortografii, jak i gramatyki**, gdy potrzebujesz kompleksowej korekty. Zapomnienie jednej z flag (`setShowGrammaticalErrors` lub `setShowSpellingErrors`) może spowodować, że błędy pozostaną niewykryte.
- **Podczas ustawiania liczby znaków w linii** pamiętaj, że wartość współdziała z wybraną czcionką i marginesami strony. Testuj na rzeczywistym układzie dokumentu, aby uniknąć nieoczekiwanych podziałów linii.
- **Operacje czyszczenia są nieodwracalne** w oryginalnym pliku. Zawsze pracuj na kopii lub używaj kontroli wersji, aby zachować oryginalne style.
- **Preferencje języka edycji** wpływają na działanie sprawdzania pisowni. Jeśli tworzysz dokumenty wielojęzyczne, dodaj wszystkie odpowiednie języki do `LanguagePreferences`.

---

**Ostatnia aktualizacja:** 2026-01-16  
**Testowane z:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}