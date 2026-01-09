---
date: 2026-01-09
description: Naučte se, jak šifrovat soubory DOCX pomocí hesla a změnit úroveň komprese
  při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words pro Javu.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Zašifrovat docx heslem – uložení OOXML pomocí Aspose.Words Java
url: /cs/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Šifrování docx pomocí hesla – uložení OOXML pomocí Aspose.Words Java

## Úvod do ukládání dokumentů ve formátu OOXML v Aspose.Words pro Java

V tomto průvodci se naučíte, jak **encrypt docx with password** a uložit dokumenty ve formátu OOXML pomocí Aspose.Words pro Java. OOXML (Office Open XML) je moderní formát souborů používaný Microsoft Word a mnoha dalšími kancelářskými aplikacemi. Provedeme vás nejčastějšími možnostmi — ochrana heslem, úrovně souladu, aktualizace vlastností, zachování starých řídicích znaků a **jak změnit úroveň komprese** — abyste mohli výstup přizpůsobit přesně svým potřebám.

## Rychlé odpovědi
- **Jak mohu chránit soubor Word?** Použijte `OoxmlSaveOptions.setPassword("yourPassword")` před uložením.  
- **Jakou úroveň souladu s OOXML mám zvolit?** ISO 29500 2008 Strict pro maximální kompatibilitu s moderními verzemi Office.  
- **Mohu zachovat staré řídicí znaky?** Ano, povolte `setKeepLegacyControlChars(true)`.  
- **Jak změním úroveň komprese?** Nastavte `setCompressionLevel(CompressionLevel.SUPER_FAST)` nebo `MAXIMUM` podle potřeby.  
- **Ovlivňují tyto možnosti velikost souboru?** Úroveň komprese a zachování starých řídicích znaků mohou výrazně změnit konečnou velikost .docx.

## Co znamená „encrypt docx with password“?
Šifrování souboru DOCX znamená, že dokument je uložen s šifrou AES‑256, která vyžaduje heslo pro jeho otevření ve Wordu nebo jakémkoli kompatibilním prohlížeči. To je nezbytné pro ochranu důvěrných informací při sdílení souborů e‑mailem, v cloudovém úložišti nebo na intranetových portálech.

## Proč používat možnosti ukládání OOXML?
- **Bezpečnost:** Ochrana heslem zabraňuje neoprávněnému přístupu.  
- **Kompatibilita:** Nastavení souladu zajišťuje, že soubor funguje napříč různými verzemi Wordu.  
- **Výkon:** Úprava komprese může urychlit ukládání nebo snížit velikost souboru.  
- **Zachování:** Uchování starých řídicích znaků zachovává věrnost při konverzi starších dokumentů.

## Požadavky
- Knihovna Aspose.Words pro Java přidaná do projektu (Maven/Gradle nebo ručně JAR).  
- Java 8 nebo vyšší.  
- Zdrojový dokument (`.docx` nebo `.doc`), který chcete zpracovat.

## Ukládání dokumentu s šifrováním heslem

Můžete šifrovat svůj dokument pomocí hesla při ukládání ve formátu OOXML. Zde je postup:

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

> **Tip:** Zvolte silné heslo a uložte jej bezpečně; heslo nelze z šifrovaného souboru obnovit.

## Nastavení souladu s OOXML

Můžete při ukládání dokumentu určit úroveň souladu s OOXML. Například můžete nastavit ISO 29500:2008 (Strict). Zde je postup:

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

Můžete zvolit aktualizaci vlastnosti „Last Saved Time“ dokumentu při ukládání. Zde je postup:

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

## Zachování starých řídicích znaků

Pokud váš dokument obsahuje staré řídicí znaky, můžete je při ukládání zachovat. Zde je postup:

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

## Jak změnit úroveň komprese při ukládání OOXML

Můžete upravit úroveň komprese při ukládání dokumentu. Například můžete nastavit `SUPER_FAST` pro minimální kompresi nebo `MAXIMUM` pro nejmenší velikost souboru. Zde je postup:

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

Toto jsou některé klíčové možnosti a nastavení, které můžete použít při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words pro Java. Neváhejte prozkoumat další možnosti a přizpůsobit proces ukládání dokumentu podle svých potřeb.

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

V tomto komplexním průvodci jsme probrali, jak **encrypt docx with password** a uložit dokumenty ve formátu OOXML pomocí Aspose.Words pro Java. Ať už potřebujete chránit své soubory, zajistit přísný soulad s OOXML, aktualizovat vlastnosti dokumentu, zachovat staré řídicí znaky nebo **změnit úroveň komprese**, Aspose.Words poskytuje všestrannou sadu nástrojů, které splní vaše požadavky.

## Často kladené otázky

**Q: Jak odeberu ochranu heslem z dokumentu chráněného heslem?**  
A: Otevřete dokument s platným heslem a poté jej uložte bez zadání hesla v `OoxmlSaveOptions`. Tím vytvoříte nechráněnou kopii.

**Q: Mohu nastavit vlastní vlastnosti při ukládání dokumentu ve formátu OOXML?**  
A: Ano. Použijte `BuiltInDocumentProperties` a `CustomDocumentProperties` na objektu `Document` před voláním `save()`.

**Q: Jaká je výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML?**  
A: Výchozí je `CompressionLevel.NORMAL`. Pro rychlost můžete přepnout na `SUPER_FAST` nebo pro nejmenší velikost na `MAXIMUM`.

**Q: Ovlivní povolení `keepLegacyControlChars` kompatibilitu s moderními verzemi Wordu?**  
A: Moderní Word může otevřít soubory se starými řídicími znaky, ale některé starší funkce se mohou zobrazit odlišně. Používejte tuto možnost jen tehdy, když potřebujete zachovat přesný původní obsah.

**Q: Je možné kombinovat více možností ukládání (např. heslo + komprese) v jednom volání?**  
A: Rozhodně. Nakonfigurujte všechny požadované vlastnosti na jedné instanci `OoxmlSaveOptions` před jejím předáním do `doc.save()`.

---

**Poslední aktualizace:** 2026-01-09  
**Testováno s:** Aspose.Words pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}