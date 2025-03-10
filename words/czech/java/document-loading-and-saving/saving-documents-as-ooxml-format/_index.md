---
title: Ukládání dokumentů ve formátu OOXML v Aspose.Words pro Java
linktitle: Ukládání dokumentů ve formátu OOXML
second_title: Aspose.Words Java Document Processing API
description: Naučte se ukládat dokumenty ve formátu OOXML pomocí Aspose.Words for Java. Zabezpečte, optimalizujte a přizpůsobte své soubory bez námahy.
weight: 20
url: /cs/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů ve formátu OOXML v Aspose.Words pro Java


## Úvod do ukládání dokumentů ve formátu OOXML v Aspose.Words pro Javu

V této příručce prozkoumáme, jak ukládat dokumenty ve formátu OOXML pomocí Aspose.Words for Java. OOXML (Office Open XML) je formát souboru používaný aplikací Microsoft Word a dalšími kancelářskými aplikacemi. Probereme různé možnosti a nastavení pro ukládání dokumentů ve formátu OOXML.

## Předpoklady

Než začneme, ujistěte se, že máte v projektu nastavenou knihovnu Aspose.Words for Java.

## Uložení dokumentu pomocí šifrování heslem

Dokument můžete zašifrovat heslem a uložit jej ve formátu OOXML. Můžete to udělat takto:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Vložte dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a nastavte heslo
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Uložte dokument se šifrováním
doc.save("EncryptedDoc.docx", saveOptions);
```

## Nastavení souladu s OOXML

Při ukládání dokumentu můžete určit úroveň souladu s OOXML. Můžete jej například nastavit na ISO 29500:2008 (Přísné). Zde je postup:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Vložte dokument
Document doc = new Document("Document.docx");

// Optimalizace pro Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Vytvořte OoxmlSaveOptions a nastavte úroveň souladu
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Uložte dokument s nastavením souladu
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualizace vlastnosti posledního uloženého času

Můžete se rozhodnout aktualizovat vlastnost "Čas posledního uložení" dokumentu při jeho ukládání. Zde je postup:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Vložte dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a povolte aktualizaci vlastnosti Last Saved Time
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Uložte dokument s aktualizovanou vlastností
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Zachování starších ovládacích znaků

Pokud váš dokument obsahuje starší řídicí znaky, můžete si je ponechat při ukládání. Zde je postup:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Načtěte dokument se staršími řídicími znaky
Document doc = new Document("LegacyControlChars.doc");

// Vytvořte OoxmlSaveOptions s formátem FLAT_OPC a povolte zachování starších řídicích znaků
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Uložte dokument se staršími řídicími znaky
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Nastavení úrovně komprese

Při ukládání dokumentu můžete upravit úroveň komprese. Můžete jej například nastavit na SUPER_FAST pro minimální kompresi. Zde je postup:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Vložte dokument
Document doc = new Document("Document.docx");

// Vytvořte OoxmlSaveOptions a nastavte úroveň komprese
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Uložte dokument se zadanou úrovní komprese
doc.save("FastCompressionDoc.docx", saveOptions);
```

Toto jsou některé z klíčových možností a nastavení, které můžete použít při ukládání dokumentů ve formátu OOXML pomocí Aspose.Words for Java. Neváhejte a prozkoumejte další možnosti a přizpůsobte si proces ukládání dokumentů podle potřeby.

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

tomto komplexním průvodci jsme prozkoumali, jak ukládat dokumenty ve formátu OOXML pomocí Aspose.Words for Java. Ať už potřebujete zašifrovat své dokumenty hesly, zajistit shodu se specifickými standardy OOXML, aktualizovat vlastnosti dokumentu, zachovat starší řídicí znaky nebo upravit úrovně komprese, Aspose.Words poskytuje všestrannou sadu nástrojů pro splnění vašich požadavků.

## FAQ

### Jak odstraním ochranu heslem z dokumentu chráněného heslem?

Chcete-li odstranit ochranu heslem z dokumentu chráněného heslem, můžete dokument otevřít se správným heslem a poté jej uložit bez zadání hesla v možnostech uložení. Tím se dokument uloží bez ochrany heslem.

### Mohu nastavit uživatelské vlastnosti při ukládání dokumentu ve formátu OOXML?

 Ano, můžete nastavit uživatelské vlastnosti dokumentu před jeho uložením ve formátu OOXML. Použijte`BuiltInDocumentProperties` a`CustomDocumentProperties` třídy pro nastavení různých vlastností, jako je autor, název, klíčová slova a uživatelské vlastnosti.

### Jaká je výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML?

 Výchozí úroveň komprese při ukládání dokumentu ve formátu OOXML pomocí Aspose.Words for Java je`NORMAL` . Úroveň komprese můžete změnit na`SUPER_FAST` nebo`MAXIMUM` podle potřeby.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
