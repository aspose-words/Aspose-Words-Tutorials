---
title: Zapisywanie dokumentów w formacie OOXML w Aspose.Words dla Java
linktitle: Zapisywanie dokumentów w formacie OOXML
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak zapisywać dokumenty w formacie OOXML za pomocą Aspose.Words dla Java. Bezproblemowo zabezpieczaj, optymalizuj i dostosowuj swoje pliki.
weight: 20
url: /pl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisywanie dokumentów w formacie OOXML w Aspose.Words dla Java


## Wprowadzenie do zapisywania dokumentów w formacie OOXML w Aspose.Words dla Java

W tym przewodniku przyjrzymy się sposobowi zapisywania dokumentów w formacie OOXML przy użyciu Aspose.Words for Java. OOXML (Office Open XML) to format pliku używany przez Microsoft Word i inne aplikacje biurowe. Omówimy różne opcje i ustawienia zapisywania dokumentów w formacie OOXML.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że w Twoim projekcie jest skonfigurowana biblioteka Aspose.Words for Java.

## Zapisywanie dokumentu z szyfrowaniem hasłem

Możesz zaszyfrować swój dokument hasłem podczas zapisywania go w formacie OOXML. Oto jak możesz to zrobić:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Załaduj dokument
Document doc = new Document("Document.docx");

// Utwórz OoxmlSaveOptions i ustaw hasło
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Zapisz dokument z szyfrowaniem
doc.save("EncryptedDoc.docx", saveOptions);
```

## Ustawianie zgodności z OOXML

Możesz określić poziom zgodności OOXML podczas zapisywania dokumentu. Na przykład możesz ustawić go na ISO 29500:2008 (Strict). Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Załaduj dokument
Document doc = new Document("Document.docx");

// Zoptymalizuj dla programu Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Utwórz OoxmlSaveOptions i ustaw poziom zgodności
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Zapisz dokument z ustawieniem zgodności
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualizowanie właściwości czasu ostatniego zapisu

Możesz wybrać aktualizację właściwości „Ostatni czas zapisu” dokumentu podczas jego zapisywania. Oto jak to zrobić:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Załaduj dokument
Document doc = new Document("Document.docx");

// Utwórz OoxmlSaveOptions i włącz aktualizację właściwości Czas ostatniego zapisu
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Zapisz dokument ze zaktualizowaną właściwością
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Zachowanie klasycznych postaci sterujących

Jeśli Twój dokument zawiera starsze znaki kontrolne, możesz wybrać opcję ich zachowania podczas zapisywania. Oto jak to zrobić:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Załaduj dokument ze starszymi znakami kontrolnymi
Document doc = new Document("LegacyControlChars.doc");

// Utwórz OoxmlSaveOptions z formatem FLAT_OPC i włącz zachowywanie starszych znaków kontrolnych
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Zapisz dokument ze starszymi znakami kontrolnymi
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Ustawianie poziomu kompresji

Możesz dostosować poziom kompresji podczas zapisywania dokumentu. Na przykład możesz ustawić go na SUPER_FAST, aby uzyskać minimalną kompresję. Oto jak:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Załaduj dokument
Document doc = new Document("Document.docx");

// Utwórz OoxmlSaveOptions i ustaw poziom kompresji
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Zapisz dokument z określonym poziomem kompresji
doc.save("FastCompressionDoc.docx", saveOptions);
```

Oto niektóre z kluczowych opcji i ustawień, których możesz użyć podczas zapisywania dokumentów w formacie OOXML przy użyciu Aspose.Words for Java. Możesz swobodnie odkrywać więcej opcji i dostosowywać proces zapisywania dokumentów według potrzeb.

## Kompletny kod źródłowy do zapisywania dokumentów w formacie OOXML w Aspose.Words dla Java

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

## Wniosek

tym kompleksowym przewodniku przyjrzeliśmy się sposobom zapisywania dokumentów w formacie OOXML przy użyciu Aspose.Words for Java. Niezależnie od tego, czy musisz zaszyfrować dokumenty hasłami, zapewnić zgodność ze szczególnymi standardami OOXML, zaktualizować właściwości dokumentu, zachować starsze znaki kontrolne lub dostosować poziomy kompresji, Aspose.Words zapewnia wszechstronny zestaw narzędzi, aby spełnić Twoje wymagania.

## Najczęściej zadawane pytania

### Jak usunąć zabezpieczenie hasłem z dokumentu chronionego hasłem?

Aby usunąć ochronę hasłem z dokumentu chronionego hasłem, możesz otworzyć dokument z prawidłowym hasłem, a następnie zapisać go bez określania hasła w opcjach zapisywania. Spowoduje to zapisanie dokumentu bez ochrony hasłem.

### Czy mogę ustawić niestandardowe właściwości podczas zapisywania dokumentu w formacie OOXML?

 Tak, możesz ustawić niestandardowe właściwości dokumentu przed zapisaniem go w formacie OOXML. Użyj`BuiltInDocumentProperties` I`CustomDocumentProperties` klasy umożliwiające ustawienie różnych właściwości, takich jak autor, tytuł, słowa kluczowe i właściwości niestandardowe.

### Jaki jest domyślny poziom kompresji przy zapisywaniu dokumentu w formacie OOXML?

 Domyślny poziom kompresji podczas zapisywania dokumentu w formacie OOXML przy użyciu Aspose.Words dla Java to`NORMAL` . Możesz zmienić poziom kompresji na`SUPER_FAST` Lub`MAXIMUM` w razie potrzeby.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
