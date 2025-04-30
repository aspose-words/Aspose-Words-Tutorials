---
"description": "Naučte se, jak ukládat dokumenty ve formátu OOXML pomocí Aspose.Words pro Javu. Zabezpečte, optimalizujte a upravte své soubory bez námahy."
"linktitle": "Ukládání dokumentů ve formátu OOXML"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání dokumentů ve formátu OOXML v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů ve formátu OOXML v Aspose.Words pro Javu


## Úvod do ukládání dokumentů ve formátu OOXML v Aspose.Words pro Javu

této příručce se podíváme na to, jak ukládat dokumenty ve formátu OOXML pomocí Aspose.Words pro Javu. OOXML (Office Open XML) je formát souborů používaný aplikací Microsoft Word a dalšími kancelářskými aplikacemi. Probereme různé možnosti a nastavení pro ukládání dokumentů ve formátu OOXML.

## Předpoklady

Než začneme, ujistěte se, že máte ve svém projektu nastavenou knihovnu Aspose.Words pro Javu.

## Uložení dokumentu se šifrováním heslem

Dokument můžete zašifrovat heslem a zároveň jej uložit ve formátu OOXML. Postupujte takto:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Načíst dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a nastavte heslo
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Uložte dokument se šifrováním
doc.save("EncryptedDoc.docx", saveOptions);
```

## Nastavení kompatibility s OOXML

Úroveň kompatibility s OOXML můžete zadat při ukládání dokumentu. Můžete ji například nastavit na ISO 29500:2008 (Strict). Postupujte takto:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Načíst dokument
Document doc = new Document("Document.docx");

// Optimalizovat pro Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Vytvořte OoxmlSaveOptions a nastavte úroveň shody s předpisy.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Uložit dokument s nastavením shody s předpisy
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualizace vlastnosti posledního uloženého času

Při ukládání dokumentu si můžete zvolit aktualizaci jeho vlastnosti „Čas posledního uložení“. Postupujte takto:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Načíst dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a povolte aktualizaci vlastnosti Čas posledního uloženého souboru.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Uložte dokument s aktualizovanou vlastností
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Zachování starších řídicích znaků

Pokud váš dokument obsahuje starší řídicí znaky, můžete si je při ukládání ponechat. Postupujte takto:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Načtení dokumentu se staršími řídicími znaky
Document doc = new Document("LegacyControlChars.doc");

// Vytvořte OoxmlSaveOptions s formátem FLAT_OPC a povolte zachování starších řídicích znaků.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Uložení dokumentu se staršími řídicími znaky
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Nastavení úrovně komprese

Úroveň komprese můžete upravit při ukládání dokumentu. Můžete ji například nastavit na SUPER_FAST pro minimální kompresi. Zde je postup:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Načíst dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a nastavte úroveň komprese
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Uložit dokument se zadanou úrovní komprese
doc.save("FastCompressionDoc.docx", saveOptions);
```

Zde jsou některé z klíčových možností a nastavení, které můžete použít při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words pro Javu. Neváhejte prozkoumat další možnosti a přizpůsobit si proces ukládání dokumentů podle potřeby.

## Kompletní zdrojový kód pro ukládání dokumentů ve formátu OOXML v Aspose.Words pro Javu

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

V této komplexní příručce jsme prozkoumali, jak ukládat dokumenty ve formátu OOXML pomocí Aspose.Words pro Javu. Ať už potřebujete šifrovat dokumenty pomocí hesel, zajistit soulad se specifickými standardy OOXML, aktualizovat vlastnosti dokumentu, zachovat starší řídicí znaky nebo upravit úrovně komprese, Aspose.Words poskytuje všestrannou sadu nástrojů, které splní vaše požadavky.

## Často kladené otázky

### Jak odstraním ochranu heslem z dokumentu chráněného heslem?

Chcete-li odebrat ochranu heslem z dokumentu chráněného heslem, můžete dokument otevřít se správným heslem a poté jej uložit bez zadání hesla v možnostech uložení. Tím se dokument uloží bez ochrany heslem.

### Mohu nastavit vlastní vlastnosti při ukládání dokumentu ve formátu OOXML?

Ano, před uložením dokumentu ve formátu OOXML můžete nastavit vlastní vlastnosti. Použijte `BuiltInDocumentProperties` a `CustomDocumentProperties` třídy pro nastavení různých vlastností, jako je autor, název, klíčová slova a vlastní vlastnosti.

### Jaká je výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML?

Výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML pomocí Aspose.Words pro Javu je `NORMAL`Úroveň komprese můžete změnit na `SUPER_FAST` nebo `MAXIMUM` podle potřeby.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}