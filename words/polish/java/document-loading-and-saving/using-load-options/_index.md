---
title: Korzystanie z opcji ładowania w Aspose.Words dla Java
linktitle: Korzystanie z opcji ładowania
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Opanowanie opcji ładowania w Aspose.Words dla Java. Dostosuj ładowanie dokumentów, obsługuj szyfrowanie, konwertuj kształty, ustawiaj wersje Worda i wiele więcej, aby wydajnie przetwarzać dokumenty Java.
weight: 11
url: /pl/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z opcji ładowania w Aspose.Words dla Java


## Wprowadzenie do pracy z opcjami ładowania w Aspose.Words dla języka Java

tym samouczku pokażemy, jak pracować z opcjami ładowania w Aspose.Words dla Java. Opcje ładowania pozwalają dostosować sposób ładowania i przetwarzania dokumentów. Omówimy różne scenariusze, w tym aktualizowanie brudnych pól, ładowanie zaszyfrowanych dokumentów, konwertowanie kształtów do Office Math, ustawianie wersji MS Word, określanie tymczasowego folderu, obsługę ostrzeżeń i konwertowanie metaplików do PNG. Przyjrzyjmy się temu krok po kroku.

## Aktualizacja Dirty Fields

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Ten fragment kodu pokazuje, jak aktualizować brudne pola w dokumencie.`setUpdateDirtyFields(true)` Metoda ta zapewnia aktualizację pól brudnych podczas ładowania dokumentu.

## Załaduj zaszyfrowany dokument

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Tutaj ładujemy zaszyfrowany dokument, używając hasła.`LoadOptions` konstruktor akceptuje hasło dokumentu, a także możesz określić nowe hasło podczas zapisywania dokumentu za pomocą`OdtSaveOptions`.

## Konwersja kształtu do Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Ten kod pokazuje, jak konwertować kształty na obiekty Office Math podczas ładowania dokumentu.`setConvertShapeToOfficeMath(true)`Metoda ta umożliwia taką konwersję.

## Ustaw wersję MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Możesz określić wersję MS Word do ładowania dokumentów. W tym przykładzie ustawiliśmy wersję na Microsoft Word 2010 za pomocą`setMswVersion`.

## Użyj folderu tymczasowego

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Ustawiając folder tymczasowy za pomocą`setTempFolder`, możesz kontrolować, gdzie przechowywane są pliki tymczasowe podczas przetwarzania dokumentów.

## Ostrzeżenie o oddzwonieniu

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Obsługuj ostrzeżenia pojawiające się w trakcie ładowania dokumentu.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Ten kod pokazuje, jak skonfigurować wywołanie zwrotne ostrzeżenia, aby obsługiwać ostrzeżenia podczas ładowania dokumentu. Możesz dostosować zachowanie swojej aplikacji, gdy wystąpią ostrzeżenia.

## Konwertuj metapliki do PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Aby przekonwertować metapliki (np. WMF) na obrazy PNG podczas ładowania dokumentu, możesz użyć`setConvertMetafilesToPng(true)` metoda.

## Kompletny kod źródłowy do pracy z opcjami ładowania w Aspose.Words dla Java

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
	// Utwórz nowy obiekt LoadOptions, który domyślnie będzie ładować dokumenty zgodnie ze specyfikacją MS Word 2019
	// i zmień wersję ładowaną na Microsoft Word 2010.
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
		//Drukuje ostrzeżenia i ich szczegóły w miarę ich pojawiania się w trakcie ładowania dokumentu.
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

## Wniosek

W tym samouczku zagłębiliśmy się w różne aspekty pracy z opcjami ładowania w Aspose.Words for Java. Opcje ładowania odgrywają kluczową rolę w dostosowywaniu sposobu ładowania i przetwarzania dokumentów, umożliwiając dostosowanie przetwarzania dokumentów do Twoich konkretnych potrzeb. Podsumujmy kluczowe punkty omówione w tym przewodniku:

## Najczęściej zadawane pytania

### Jak poradzić sobie z ostrzeżeniami podczas ładowania dokumentu?

 Można skonfigurować wywołanie zwrotne ostrzeżenia, jak pokazano na rysunku`warningCallback()` metoda powyżej. Dostosuj`DocumentLoadingWarningCallback` Klasa obsługująca ostrzeżenia zgodnie z wymaganiami aplikacji.

### Czy mogę konwertować kształty na obiekty Office Math podczas ładowania dokumentu?

 Tak, możesz konwertować kształty na obiekty Office Math za pomocą`loadOptions.setConvertShapeToOfficeMath(true)`.

### Jak określić wersję programu MS Word do ładowania dokumentów?

 Używać`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` aby określić wersję programu MS Word do ładowania dokumentów.

###  Jaki jest cel`setTempFolder` method in Load Options?

 Ten`setTempFolder`Metoda ta pozwala na określenie folderu, w którym przechowywane są pliki tymczasowe podczas przetwarzania dokumentów.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
