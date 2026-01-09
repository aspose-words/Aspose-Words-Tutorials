---
date: 2026-01-09
description: Dowiedz się, jak zaszyfrować plik docx hasłem i zmienić poziom kompresji
  podczas zapisywania dokumentów w formacie OOXML przy użyciu Aspose.Words for Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Zaszyfruj docx hasłem – zapis OOXML przy użyciu Aspose.Words Java
url: /pl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Szyfrowanie docx hasłem – zapis OOXML przy użyciu Aspose.Words Java

## Wprowadzenie do zapisywania dokumentów w formacie OOXML w Aspose.Words dla Javy

W tym przewodniku dowiesz się, jak **szyfrować docx hasłem** oraz zapisywać dokumenty w formacie OOXML przy użyciu Aspose.Words dla Javy. OOXML (Office Open XML) to nowoczesny format plików używany przez Microsoft Word i wiele innych aplikacji biurowych. Przejdziemy przez najczęstsze opcje — ochronę hasłem, poziomy zgodności, aktualizację właściwości, obsługę starszych znaków kontrolnych oraz **sposób zmiany poziomu kompresji** — abyś mógł dostosować wynik do swoich dokładnych potrzeb.

## Szybkie odpowiedzi
- **Jak mogę zabezpieczyć plik Word?** Użyj `OoxmlSaveOptions.setPassword("yourPassword")` przed zapisem.  
- **Jaki poziom zgodności OOXML wybrać?** ISO 29500 2008 Strict dla maksymalnej kompatybilności z nowoczesnymi wersjami Office.  
- **Czy mogę zachować starsze znaki kontrolne?** Tak, włącz `setKeepLegacyControlChars(true)`.  
- **Jak zmienić poziom kompresji?** Ustaw `setCompressionLevel(CompressionLevel.SUPER_FAST)` lub `MAXIMUM` w zależności od potrzeb.  
- **Czy te opcje wpływają na rozmiar pliku?** Poziom kompresji i obsługa starszych znaków kontrolnych mogą zauważalnie zmienić ostateczny rozmiar .docx.

## Co to jest „encrypt docx with password”?
Szyfrowanie pliku DOCX oznacza, że dokument jest zapisywany z szyfrowaniem AES‑256, wymagającym podania hasła przy otwieraniu w Wordzie lub innym kompatybilnym podglądzie. Jest to niezbędne do ochrony poufnych informacji, gdy pliki są udostępniane przez e‑mail, chmurę lub portale intranetowe.

## Dlaczego warto używać opcji zapisu OOXML?
- **Bezpieczeństwo:** Ochrona hasłem zapobiega nieautoryzowanemu dostępowi.  
- **Kompatybilność:** Ustawienia zgodności zapewniają działanie pliku w różnych wersjach Worda.  
- **Wydajność:** Dostosowanie kompresji może przyspieszyć zapisywanie lub zmniejszyć rozmiar pliku.  
- **Zachowanie:** Zachowanie starszych znaków kontrolnych utrzymuje wierność przy konwersji starszych dokumentów.

## Wymagania wstępne
- Biblioteka Aspose.Words dla Javy dodana do projektu (Maven/Gradle lub ręczny JAR).  
- Java 8 lub nowsza.  
- Dokument źródłowy (`.docx` lub `.doc`), który chcesz przetworzyć.

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

> **Porada:** Wybierz silne hasło i przechowuj je w bezpiecznym miejscu; hasła nie da się odzyskać z zaszyfrowanego pliku.

## Ustawianie zgodności OOXML

Możesz określić poziom zgodności OOXML przy zapisywaniu dokumentu. Na przykład możesz ustawić go na ISO 29500:2008 (Strict). Oto jak:

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

## Aktualizacja właściwości „Last Saved Time”

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

Jeśli Twój dokument zawiera starsze znaki kontrolne, możesz zdecydować się na ich zachowanie przy zapisie. Oto jak:

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

## Jak zmienić poziom kompresji przy zapisie OOXML

Możesz dostosować poziom kompresji przy zapisywaniu dokumentu. Na przykład możesz ustawić `SUPER_FAST` dla minimalnej kompresji lub `MAXIMUM` dla najmniejszego rozmiaru pliku. Oto jak:

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

Są to niektóre z kluczowych opcji i ustawień, które możesz wykorzystać przy zapisywaniu dokumentów w formacie OOXML przy użyciu Aspose.Words dla Javy. Zachęcamy do dalszego eksplorowania opcji i dostosowywania procesu zapisu dokumentu według własnych potrzeb.

## Pełny kod źródłowy dla zapisywania dokumentów w formacie OOXML w Aspose.Words dla Javy

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

## Zakończenie

W tym obszernej przewodniku omówiliśmy, jak **szyfrować docx hasłem** oraz zapisywać dokumenty w formacie OOXML przy użyciu Aspose.Words dla Javy. Niezależnie od tego, czy potrzebujesz chronić pliki, zapewnić ścisłą zgodność OOXML, zaktualizować właściwości dokumentu, zachować starsze znaki kontrolne, czy **zmienić poziom kompresji**, Aspose.Words oferuje wszechstronny zestaw narzędzi spełniających Twoje wymagania.

## Najczęściej zadawane pytania

**P: Jak usunąć ochronę hasłem z dokumentu zabezpieczonego hasłem?**  
O: Otwórz dokument przy użyciu prawidłowego hasła, a następnie zapisz go bez podawania hasła w `OoxmlSaveOptions`. To utworzy niechronioną kopię.

**P: Czy mogę ustawić własne właściwości przy zapisywaniu dokumentu w formacie OOXML?**  
O: Tak. Użyj `BuiltInDocumentProperties` i `CustomDocumentProperties` na obiekcie `Document` przed wywołaniem `save()`.

**P: Jaki jest domyślny poziom kompresji przy zapisywaniu dokumentu w formacie OOXML?**  
O: Domyślnie jest to `CompressionLevel.NORMAL`. Możesz przełączyć na `SUPER_FAST` dla szybkości lub `MAXIMUM` dla najmniejszego rozmiaru pliku.

**P: Czy włączenie `keepLegacyControlChars` wpłynie na kompatybilność z nowoczesnymi wersjami Worda?**  
O: Nowoczesny Word może otwierać pliki ze starszymi znakami kontrolnymi, ale niektóre starsze funkcje mogą wyświetlać się inaczej. Używaj tej opcji tylko wtedy, gdy musisz zachować dokładną oryginalną zawartość.

**P: Czy można połączyć wiele opcji zapisu (np. hasło + kompresja) w jednym wywołaniu?**  
O: Oczywiście. Skonfiguruj wszystkie pożądane właściwości w jednej instancji `OoxmlSaveOptions` przed przekazaniem jej do `doc.save()`.

---

**Ostatnia aktualizacja:** 2026-01-09  
**Testowane z:** Aspose.Words dla Javy 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}