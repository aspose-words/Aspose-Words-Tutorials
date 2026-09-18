---
date: 2025-12-27
description: Naucz się, jak ustawiać LoadOptions w Aspose.Words for Java, w tym jak
  określić folder tymczasowy, ustawić wersję Worda, konwertować metafile na PNG oraz
  konwertować kształt na formułę matematyczną, aby zapewnić elastyczną obróbkę dokumentów.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Jak ustawić LoadOptions w Aspose.Words dla Java
url: /pl/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić LoadOptions w Aspose.Words dla Java

W tym samouczku przeprowadzimy Cię przez **jak ustawić LoadOptions** w różnych scenariuszach rzeczywistych przy pracy z Aspose.Words dla Java. LoadOptions dają precyzyjną kontrolę nad sposobem otwierania dokumentu — niezależnie od tego, czy musisz zaktualizować nieodświeżone pola, pracować z zaszyfrowanymi plikami, konwertować kształty do Office Math, czy wskazać bibliotece, gdzie przechowywać dane tymczasowe. Po zakończeniu będziesz mógł dostosować zachowanie ładowania do dokładnych wymagań Twojej aplikacji.

## Szybkie odpowiedzi
- **Czym jest LoadOptions?** Obiekt konfiguracyjny, który wpływa na sposób, w jaki Aspose.Words ładuje dokument.  
- **Czy mogę aktualizować pola podczas ładowania?** Tak — ustaw `setUpdateDirtyFields(true)`.  
- **Jak otworzyć plik chroniony hasłem?** Przekaż hasło do konstruktora `LoadOptions`.  
- **Czy można zmienić folder tymczasowy?** Użyj `setTempFolder("path")`.  
- **Która metoda konwertuje kształty do Office Math?** `setConvertShapeToOfficeMath(true)`.

## Dlaczego używać LoadOptions?
LoadOptions pozwalają uniknąć kroków przetwarzania po załadowaniu, zmniejszyć zużycie pamięci i zapewnić, że dokument jest interpretowany dokładnie tak, jak potrzebujesz. Na przykład konwersja metafili do PNG podczas ładowania zapobiega późniejszym problemom z rasteryzacją, a określenie wersji MS Word pomaga zachować wierność układu przy pracy ze starszymi plikami.

## Wymagania wstępne
- Java 17 lub nowszy  
- Aspose.Words for Java (najnowsza wersja)  
- Ważna licencja Aspose do użytku produkcyjnego  

## Przewodnik krok po kroku

### Aktualizacja nieodświeżonych pól

Gdy dokument zawiera pola, które zostały edytowane, ale nie odświeżone, możesz poinstruować Aspose.Words, aby automatycznie zaktualizował je podczas ładowania.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Wywołanie `setUpdateDirtyFields(true)` zapewnia, że wszystkie nieodświeżone pola zostaną przeliczone natychmiast po otwarciu dokumentu.*

### Ładowanie zaszyfrowanego dokumentu

Jeśli Twój plik źródłowy jest chroniony hasłem, podaj hasło przy tworzeniu instancji `LoadOptions`. Możesz także ustawić nowe hasło przy zapisywaniu do innego formatu.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Konwersja kształtu do Office Math

Niektóre starsze dokumenty przechowują równania jako kształty rysunkowe. Włączenie tej opcji konwertuje te kształty na natywne obiekty Office Math, które później łatwiej edytować.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Ustawienie wersji MS Word

Określenie docelowej wersji Word pomaga bibliotece wybrać odpowiednie zasady renderowania, szczególnie przy pracy ze starszymi formatami plików.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Użycie folderu tymczasowego

Duże dokumenty mogą generować pliki tymczasowe (np. przy wyodrębnianiu obrazów). Możesz skierować te pliki do wybranego folderu, co jest przydatne w środowiskach sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback ostrzeżeń

Podczas ładowania Aspose.Words może generować ostrzeżenia (np. nieobsługiwane funkcje). Implementacja callbacku pozwala logować lub reagować na te zdarzenia.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Konwersja metafili do PNG

Metafile, takie jak WMF, mogą być rasteryzowane do PNG podczas ładowania, zapewniając spójne renderowanie na różnych platformach.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Pełny kod źródłowy do pracy z Load Options w Aspose.Words dla Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Typowe przypadki użycia i wskazówki
- **Potoki konwersji wsadowej** – Połącz `setTempFolder` z zaplanowanym zadaniem, aby przetworzyć setki plików bez zapełniania systemowego katalogu tymczasowego.  
- **Migracja starszych dokumentów** – Użyj `setMswVersion` razem z `setConvertShapeToOfficeMath`, aby przenieść stare dokumenty inżynierskie do nowoczesnego formatu, zachowując równania.  
- **Bezpieczna obsługa dokumentów** – Połącz `loadEncryptedDocument` z `OdtSaveOptions`, aby ponownie zaszyfrować pliki nowym hasłem w innym formacie.  

## Najczęściej zadawane pytania

**P: Jak mogę obsłużyć ostrzeżenia podczas ładowania dokumentu?**  
A: Zaimplementuj własny `IWarningCallback` (jak pokazano w przykładzie *Callback ostrzeżeń*) i zarejestruj go za pomocą `loadOptions.setWarningCallback(...)`. Pozwala to logować, ignorować lub przerywać w zależności od stopnia istotności ostrzeżenia.

**P: Czy mogę konwertować kształty do obiektów Office Math podczas ładowania dokumentu?**  
A: Tak — wywołaj `loadOptions.setConvertShapeToOfficeMath(true)` przed utworzeniem obiektu `Document`. Biblioteka automatycznie zamieni kompatybilne kształty na natywne obiekty Office Math.

**P: Jak określić wersję MS Word przy ładowaniu dokumentu?**  
A: Użyj `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (lub innej wartości enum), aby poinformować Aspose.Words, które zasady renderowania wersji Word mają być zastosowane.

**P: Jaki jest cel metody `setTempFolder` w LoadOptions?**  
A: Kieruje wszystkie pliki tymczasowe generowane podczas ładowania (np. wyodrębnione obrazy) do folderu, którym zarządzasz, co jest niezbędne w środowiskach z ograniczonymi katalogami tymczasowymi systemu.

**P: Czy można konwertować metafile, takie jak WMF, do PNG podczas ładowania?**  
A: Zdecydowanie — włącz to za pomocą `loadOptions.setConvertMetafilesToPng(true)`. Zapewnia to, że obrazy rastrowe są przechowywane jako PNG, zwiększając kompatybilność z nowoczesnymi przeglądarkami.

## Podsumowanie

Omówiliśmy podstawowe techniki **jak ustawić LoadOptions** w Aspose.Words dla Java, od aktualizacji nieodświeżonych pól po obsługę zaszyfrowanych plików, konwersję kształtów, określanie wersji Word, kierowanie przechowywania tymczasowego i inne. Korzystając z tych opcji, możesz tworzyć solidne, wysokowydajne potoki przetwarzania dokumentów, które dostosowują się do szerokiego zakresu scenariuszy wejściowych.

---

**Ostatnia aktualizacja:** 2025-12-27  
**Testowano z:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}