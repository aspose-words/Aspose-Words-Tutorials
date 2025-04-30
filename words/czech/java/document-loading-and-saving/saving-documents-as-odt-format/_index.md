---
"description": "Naučte se, jak ukládat dokumenty ve formátu ODT pomocí Aspose.Words pro Javu. Zajistěte kompatibilitu s open-source kancelářskými balíky."
"linktitle": "Ukládání dokumentů ve formátu ODT"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání dokumentů ve formátu ODT v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-documents-as-odt-format/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů ve formátu ODT v Aspose.Words pro Javu


## Úvod do ukládání dokumentů ve formátu ODT v Aspose.Words pro Javu

V tomto článku se podíváme na to, jak ukládat dokumenty ve formátu ODT (Open Document Text) pomocí Aspose.Words pro Javu. ODT je oblíbený otevřený standardní formát dokumentů používaný různými kancelářskými balíky, včetně OpenOffice a LibreOffice. Ukládáním dokumentů ve formátu ODT si můžete zajistit kompatibilitu s těmito softwarovými balíčky.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Vývojové prostředí Java: Ujistěte se, že máte v systému nainstalovanou sadu Java Development Kit (JDK).

2. Aspose.Words pro Javu: Stáhněte a nainstalujte knihovnu Aspose.Words pro Javu. Odkaz ke stažení naleznete [zde](https://releases.aspose.com/words/java/).

3. Ukázkový dokument: Mějte ukázkový dokument aplikace Word (např. „Dokument.docx“), který chcete převést do formátu ODT.

## Krok 1: Vložení dokumentu

Nejprve si načtěme dokument Wordu pomocí Aspose.Words pro Javu:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

Zde, `"Your Directory Path"` by měl ukazovat na adresář, kde se nachází váš dokument.

## Krok 2: Zadejte možnosti ukládání ODT

Pro uložení dokumentu ve formátu ODT je nutné zadat možnosti ukládání ODT. Dále můžeme nastavit měrnou jednotku dokumentu. Open Office používá centimetry, zatímco MS Office používá palce. Nastavíme ji na palce:

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## Krok 3: Uložte dokument

Nyní je čas uložit dokument ve formátu ODT:

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Zde, `"Your Directory Path"` by měl ukazovat na adresář, kam chcete uložit převedený soubor ODT.

## Kompletní zdrojový kód pro ukládání dokumentů ve formátu ODT v Aspose.Words pro Javu

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office používá centimetry při určování délek, šířek a dalšího měřitelného formátování
// a vlastnosti obsahu v dokumentech, zatímco MS Office používá palce.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## Závěr

tomto článku jsme se naučili, jak ukládat dokumenty ve formátu ODT pomocí Aspose.Words pro Javu. To může být obzvláště užitečné, když potřebujete zajistit kompatibilitu s open-source kancelářskými balíky, jako jsou OpenOffice a LibreOffice.

## Často kladené otázky

### Jak si mohu stáhnout Aspose.Words pro Javu?

Aspose.Words pro Javu si můžete stáhnout z webových stránek Aspose. Navštivte [tento odkaz](https://releases.aspose.com/words/java/) pro přístup ke stránce stahování.

### Jaká je výhoda ukládání dokumentů ve formátu ODT?

Ukládání dokumentů ve formátu ODT zajišťuje kompatibilitu s kancelářskými balíky s otevřeným zdrojovým kódem, jako jsou OpenOffice a LibreOffice, což uživatelům těchto softwarových balíčků usnadňuje přístup k dokumentům a jejich úpravy.

### Musím při ukládání do formátu ODT zadat měrnou jednotku?

Ano, je dobrým zvykem specifikovat měrnou jednotku. Open Office standardně používá centimetry, takže nastavení na palce zajistí konzistentní formátování.

### Mohu dávkově převést více dokumentů do formátu ODT?

Ano, můžete automatizovat převod více dokumentů do formátu ODT pomocí Aspose.Words pro Javu iterací souborů dokumentů a použitím procesu převodu.

### Je Aspose.Words pro Javu kompatibilní s nejnovějšími verzemi Javy?

Aspose.Words pro Javu je pravidelně aktualizován, aby podporoval nejnovější verze Javy, a tím byl zajištěn vylepšený kompatibilita a výkon. Nejnovější informace naleznete v dokumentaci k systémovým požadavkům.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}