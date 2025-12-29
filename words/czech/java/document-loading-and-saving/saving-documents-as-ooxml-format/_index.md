---
date: 2025-12-29
description: Naučte se, jak šifrovat soubory DOCX pomocí hesla s využitím možností
  uložení Aspose.Words pro Java. Zabezpečte, optimalizujte a přizpůsobte své soubory
  OOXML bez námahy.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Jak zašifrovat DOCX heslem pomocí Aspose.Words pro Javu
url: /cs/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak zašifrovat DOCX pomocí hesla pomocí Aspose.Words pro Java

V tomto průvodci se dozvíte **jak zašifrovat docx pomocí hesla** při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words pro Java. Ať už chráníte důvěrné zprávy nebo zabezpečujete návrhy smluv, níže uvedené kroky vám přesně ukážou, jak použít ochranu heslem a doladit další možnosti ukládání OOXML.

## Rychlé odpovědi
- **Mohu zašifrovat soubor DOCX pomocí hesla?** Ano, použijte `OoxmlSaveOptions.setPassword()` před uložením.  
- **Která třída řídí nastavení ukládání OOXML?** `OoxmlSaveOptions` (součást Aspose.Words).  
- **Potřebuji licenci pro ochranu heslem?** Platná licence Aspose.Words je vyžadována pro produkční použití.  
- **Mohu kombinovat šifrování s nastavením souladu?** Ano – nastavte jak `setPassword`, tak `setCompliance` na stejném objektu `OoxmlSaveOptions`.  
- **Jaké úrovně komprese jsou k dispozici?** `NORMAL`, `SUPER_FAST` a `MAXIMUM` prostřednictvím `CompressionLevel`.

## Co znamená „zašifrovat docx pomocí hesla“?
Zašifrování souboru DOCX znamená, že obsah souboru je uložen v šifrované podobě a lze jej otevřít pouze po zadání správného hesla. To chrání citlivé informace před neoprávněným přístupem, přičemž standardní nástroje Wordu mohou soubor otevřít, jakmile je heslo zadáno.

## Proč použít možnosti ukládání Aspose.Words pro šifrování?
Aspose.Words poskytuje bohatou sadu **aspose words save options**, které vám umožňují řídit nejen šifrování, ale také úrovně souladu, kompresi a zacházení se staršími znaky – vše z Java kódu. Tím se eliminuje potřeba ručního post‑processingu nebo nástrojů třetích stran.

## Požadavky
- Java Development Kit (JDK 8 nebo vyšší)  
- Knihovna Aspose.Words pro Java přidaná do vašeho projektu (Maven/Gradle nebo JAR)  
- Platná licence Aspose.Words pro produkci (volitelná pro hodnocení)

## Ukládání dokumentu s šifrováním heslem

Můžete zašifrovat svůj dokument pomocí hesla při jeho ukládání ve formátu OOXML. Zde je postup:

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

## Nastavení souladu OOXML

Můžete při ukládání dokumentu určit úroveň souladu OOXML. Například ji můžete nastavit na ISO 29500:2008 (Strict). Zde je postup:

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

## Aktualizace vlastnosti „Poslední uložení“

Můžete zvolit aktualizaci vlastnosti „Last Saved Time“ dokumentu při jeho ukládání. Zde je postup:

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

## Zachování starších řídicích znaků

Pokud váš dokument obsahuje starší řídicí znaky, můžete se rozhodnout je při ukládání zachovat. Zde je postup:

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

## Nastavení úrovně komprese

Můžete při ukládání dokumentu upravit úroveň komprese. Například ji můžete nastavit na **SUPER_FAST** pro minimální kompresi. Zde je postup:

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

Toto jsou některé z klíčových možností a nastavení, které můžete použít při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words pro Java. Neváhejte prozkoumat další možnosti a přizpůsobit proces ukládání dokumentu podle potřeby.

## Kompletní zdrojový kód pro ukládání dokumentů ve formátu OOXML v Aspose.Words pro Java

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

## Závěr

V tomto komplexním průvodci jsme prozkoumali, jak **zašifrovat docx pomocí hesla** a doladit řadu možností ukládání OOXML pomocí Aspose.Words pro Java. Ať už potřebujete chránit důvěrný obsah, splnit přísné požadavky ISO, zachovat starší znaky nebo řídit kompresi, knihovna vám poskytuje detailní kontrolu prostřednictvím stejného API `OoxmlSaveOptions`.

## Často kladené otázky

**Q: Jak mohu odstranit ochranu heslem z dokumentu chráněného heslem?**  
A: Otevřete dokument se správným heslem a poté jej uložte znovu bez volání `setPassword`. Nový soubor bude nechráněný.

**Q: Mohu nastavit vlastní vlastnosti při ukládání dokumentu ve formátu OOXML?**  
A: Ano. Použijte `BuiltInDocumentProperties` nebo `CustomDocumentProperties` na objektu `Document` před voláním `save`.

**Q: Jaká je výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML?**  
A: Výchozí je `NORMAL`. Můžete přepnout na `SUPER_FAST` pro rychlost nebo `MAXIMUM` pro menší velikost souboru.

**Q: Fungují možnosti ukládání aspose words se staršími verzemi Wordu?**  
A: Ano. Úpravou `MsWordVersion` a nastavení souladu můžete cílit na Word 2007‑2019 a zajistit kompatibilitu.

**Q: Je možné kombinovat více možností ukládání v jedné operaci?**  
A: Rozhodně. Vytvořte jednu instanci `OoxmlSaveOptions`, nastavte všechny požadované vlastnosti (heslo, soulad, kompresi atd.) a předávejte ji metodě `doc.save()`.

---

**Poslední aktualizace:** 2025-12-29  
**Testováno s:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}