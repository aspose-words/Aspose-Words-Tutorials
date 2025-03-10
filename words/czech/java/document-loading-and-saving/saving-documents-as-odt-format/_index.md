---
title: Ukládání dokumentů ve formátu ODT v Aspose.Words pro Java
linktitle: Ukládání dokumentů ve formátu ODT
second_title: Aspose.Words Java Document Processing API
description: Naučte se ukládat dokumenty ve formátu ODT pomocí Aspose.Words for Java. Zajistěte kompatibilitu s open source kancelářskými balíky.
weight: 19
url: /cs/java/document-loading-and-saving/saving-documents-as-odt-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů ve formátu ODT v Aspose.Words pro Java


## Úvod do ukládání dokumentů ve formátu ODT v Aspose.Words pro Javu

tomto článku prozkoumáme, jak ukládat dokumenty ve formátu ODT (Open Document Text) pomocí Aspose.Words for Java. ODT je populární otevřený standardní formát dokumentu používaný různými kancelářskými balíky, včetně OpenOffice a LibreOffice. Uložením dokumentů ve formátu ODT můžete zajistit kompatibilitu s těmito softwarovými balíčky.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Java Development Environment: Ujistěte se, že máte v systému nainstalovanou sadu Java Development Kit (JDK).

2.  Aspose.Words for Java: Stáhněte si a nainstalujte knihovnu Aspose.Words for Java. Odkaz ke stažení najdete[zde](https://releases.aspose.com/words/java/).

3. Ukázkový dokument: Mějte ukázkový dokument aplikace Word (např. "Document.docx"), který chcete převést do formátu ODT.

## Krok 1: Vložte dokument

Nejprve načtěte dokument aplikace Word pomocí Aspose.Words for Java:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

 Zde,`"Your Directory Path"` by měl ukazovat na adresář, kde je umístěn váš dokument.

## Krok 2: Zadejte možnosti uložení ODT

Chcete-li dokument uložit jako ODT, musíme zadat možnosti uložení ODT. Navíc můžeme nastavit měrnou jednotku dokumentu. Open Office používá centimetry, zatímco MS Office používá palce. Nastavíme to na palce:

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## Krok 3: Uložte dokument

Nyní je čas uložit dokument ve formátu ODT:

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

 Zde,`"Your Directory Path"` by měl ukazovat na adresář, kam chcete uložit převedený soubor ODT.

## Kompletní zdrojový kód pro ukládání dokumentů ve formátu ODT v Aspose.Words pro Java

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office používá centimetry při zadávání délek, šířek a dalších měřitelných formátů
// a vlastnosti obsahu v dokumentech, zatímco MS Office používá palce.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## Závěr

V tomto článku jsme se naučili ukládat dokumenty ve formátu ODT pomocí Aspose.Words for Java. To může být zvláště užitečné, když potřebujete zajistit kompatibilitu s open source kancelářskými sadami, jako jsou OpenOffice a LibreOffice.

## FAQ

### Jak si mohu stáhnout Aspose.Words pro Java?

 Aspose.Words for Java si můžete stáhnout z webu Aspose. Návštěva[tento odkaz](https://releases.aspose.com/words/java/) pro přístup na stránku stahování.

### Jaká je výhoda ukládání dokumentů ve formátu ODT?

Ukládání dokumentů ve formátu ODT zajišťuje kompatibilitu s open source kancelářskými sadami, jako jsou OpenOffice a LibreOffice, což uživatelům těchto softwarových balíčků usnadňuje přístup k vašim dokumentům a jejich úpravy.

### Musím při ukládání ve formátu ODT zadat měrnou jednotku?

Ano, je dobrým zvykem specifikovat měrnou jednotku. Open Office standardně používá centimetry, takže nastavením na palce zajistíte konzistentní formátování.

### Mohu převést více dokumentů do formátu ODT v dávkovém procesu?

Ano, převod více dokumentů do formátu ODT můžete automatizovat pomocí Aspose.Words for Java tím, že projdete soubory dokumentů a použijete proces převodu.

### Je Aspose.Words for Java kompatibilní s nejnovějšími verzemi Java?

Aspose.Words for Java je pravidelně aktualizována, aby podporovala nejnovější verze Java, což zajišťuje zlepšení kompatibility a výkonu. Nezapomeňte zkontrolovat systémové požadavky v dokumentaci, kde najdete nejnovější informace.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
