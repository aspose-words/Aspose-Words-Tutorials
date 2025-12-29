---
date: 2025-12-29
description: „Dowiedz się, jak szyfrować pliki docx hasłem przy użyciu opcji zapisu
  Aspose.Words dla języka Java. Zabezpiecz, optymalizuj i dostosowuj swoje pliki OOXML
  bez wysiłku.”
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Jak zaszyfrować plik DOCX hasłem przy użyciu Aspose.Words dla Javy
url: /pl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak zaszyfrować DOCX hasłem przy użyciu Aspose.Words for Java

W tym przewodniku dowiesz się **jak zaszyfrować docx hasłem** podczas zapisywania dokumentów w formacie OOXML przy użyciu Aspose.Words for Java. Niezależnie od tego, czy chronisz poufne raporty, czy zabezpieczasz projekty umów, poniższe kroki pokażą dokładnie, jak zastosować ochronę hasłem i precyzyjnie dostroić inne opcje zapisu OOXML.

## Szybkie odpowiedzi
- **Czy mogę zaszyfrować plik DOCX hasłem?** Tak, użyj `OoxmlSaveOptions.setPassword()` przed zapisem.  
- **Która klasa kontroluje ustawienia zapisu OOXML?** `OoxmlSaveOptions` (część Aspose.Words).  
- **Czy potrzebna jest licencja do ochrony hasłem?** Wymagana jest ważna licencja Aspose.Words do użytku produkcyjnego.  
- **Czy mogę połączyć szyfrowanie z ustawieniami zgodności?** Oczywiście – ustaw zarówno `setPassword`, jak i `setCompliance` na tej samej instancji `OoxmlSaveOptions`.  
- **Jakie poziomy kompresji są dostępne?** `NORMAL`, `SUPER_FAST` i `MAXIMUM` za pośrednictwem `CompressionLevel`.

## Co to jest „zaszyfrować docx hasłem”?
Szyfrowanie pliku DOCX oznacza, że zawartość pliku jest przechowywana w postaci zaszyfrowanej i może być otwarta tylko po podaniu prawidłowego hasła. Chroni to wrażliwe informacje przed nieautoryzowanym dostępem, jednocześnie umożliwiając standardowym narzędziom Word otwarcie pliku po wprowadzeniu hasła.

## Dlaczego warto używać opcji zapisu Aspose.Words do szyfrowania?
Aspose.Words udostępnia bogaty zestaw **aspose words save options**, które pozwalają kontrolować nie tylko szyfrowanie, ale także poziomy zgodności, kompresję i obsługę starszych znaków — wszystko z poziomu kodu Java. Eliminuje to potrzebę ręcznego przetwarzania po zapisie lub używania narzędzi firm trzecich.

## Prerequisites
- Java Development Kit (JDK 8 lub nowszy)  
- Biblioteka Aspose.Words for Java dodana do projektu (Maven/Gradle lub JAR)  
- Ważna licencja Aspose.Words do użytku produkcyjnego (opcjonalnie do oceny)

## Zapisywanie dokumentu z szyfrowaniem hasłem

Możesz zaszyfrować dokument hasłem podczas zapisywania go w formacie OOXML. Oto jak to zrobić:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## Ustawianie zgodności OOXML

Możesz określić poziom zgodności OOXML przy zapisywaniu dokumentu. Na przykład, możesz ustawić go na ISO 29500:2008 (Strict). Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualizacja właściwości „Ostatni zapis”

Możesz wybrać aktualizację właściwości „Last Saved Time” dokumentu przy zapisie. Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Zachowanie starszych znaków kontrolnych

Jeśli dokument zawiera starsze znaki kontrolne, możesz zdecydować się na ich zachowanie przy zapisie. Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Ustawianie poziomu kompresji

Możesz dostosować poziom kompresji przy zapisywaniu dokumentu. Na przykład, możesz ustawić **SUPER_FAST** dla minimalnej kompresji. Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

To niektóre z kluczowych opcji i ustawień, które możesz używać przy zapisywaniu dokumentów w formacie OOXML przy użyciu Aspose.Words for Java. Śmiało eksploruj więcej opcji i dostosowuj proces zapisu dokumentu według potrzeb.

## Pełny kod źródłowy do zapisywania dokumentów w formacie OOXML w Aspose.Words for Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Conclusion

W tym kompleksowym przewodniku omówiliśmy, jak **zaszyfrować docx hasłem** i precyzyjnie dostroić szereg opcji zapisu OOXML przy użyciu Aspose.Words for Java. Niezależnie od tego, czy musisz chronić poufne treści, spełnić rygorystyczne wymogi ISO, zachować starsze znaki, czy kontrolować kompresję, biblioteka zapewnia szczegółową kontrolę poprzez ten sam interfejs API `OoxmlSaveOptions`.

## Najczęściej zadawane pytania

**Q: Jak usunąć ochronę hasłem z dokumentu zabezpieczonego hasłem?**  
A: Otwórz dokument przy użyciu prawidłowego hasła, a następnie zapisz go ponownie bez wywoływania `setPassword`. Nowy plik będzie niechroniony.

**Q: Czy mogę ustawić własne właściwości przy zapisywaniu dokumentu w formacie OOXML?**  
A: Tak. Użyj `BuiltInDocumentProperties` lub `CustomDocumentProperties` na obiekcie `Document` przed wywołaniem `save`.

**Q: Jaki jest domyślny poziom kompresji przy zapisywaniu dokumentu w formacie OOXML?**  
A: Domyślnie jest to `NORMAL`. Możesz przełączyć na `SUPER_FAST` dla szybkości lub `MAXIMUM` dla mniejszego rozmiaru pliku.

**Q: Czy opcje zapisu aspose words działają ze starszymi wersjami Word?**  
A: Tak. Poprzez dostosowanie `MsWordVersion` i ustawień zgodności możesz celować w Word 2007‑2019 i zapewnić kompatybilność.

**Q: Czy można połączyć wiele opcji zapisu w jednej operacji?**  
A: Absolutnie. Utwórz jedną instancję `OoxmlSaveOptions`, ustaw wszystkie pożądane właściwości (hasło, zgodność, kompresję itp.) i przekaż ją do `doc.save()`.

**Ostatnia aktualizacja:** 2025-12-29  
**Testowano z:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}