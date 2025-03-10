---
title: Použití poznámek pod čarou a vysvětlivky v Aspose.Words pro Java
linktitle: Používání poznámek pod čarou a vysvětlivky
second_title: Aspose.Words Java Document Processing API
description: Naučte se efektivně používat poznámky pod čarou a vysvětlivky v Aspose.Words for Java. Vylepšete své dovednosti v oblasti formátování dokumentů ještě dnes!
weight: 13
url: /cs/java/using-document-elements/using-footnotes-and-endnotes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití poznámek pod čarou a vysvětlivky v Aspose.Words pro Java


V tomto tutoriálu vás provedeme procesem používání poznámek pod čarou a vysvětlivek v Aspose.Words pro Java. Poznámky pod čarou a vysvětlivky jsou základními prvky formátování dokumentu, často se používají pro citace, odkazy a další informace. Aspose.Words for Java poskytuje robustní funkce pro bezproblémovou práci s poznámkami pod čarou a vysvětlivkami.

## 1. Úvod do poznámek pod čarou a vysvětlivky

Poznámky pod čarou a vysvětlivky jsou anotace, které poskytují doplňující informace nebo citace v dokumentu. Poznámky pod čarou se zobrazují ve spodní části stránky, zatímco vysvětlivky se shromažďují na konci oddílu nebo dokumentu. Běžně se používají v akademických pracích, zprávách a právních dokumentech k odkazování na zdroje nebo objasnění obsahu.

## 2. Nastavení vašeho prostředí

Než se pustíme do práce s poznámkami pod čarou a vysvětlivkami, musíte nastavit vývojové prostředí. Ujistěte se, že máte ve svém projektu nainstalované a nakonfigurované rozhraní Aspose.Words for Java API.

## 3. Přidání poznámek pod čarou do vašeho dokumentu

Chcete-li do dokumentu přidat poznámky pod čarou, postupujte takto:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Zadejte počet sloupců, se kterými je oblast poznámek pod čarou formátována.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Úprava možností poznámky pod čarou

Můžete upravit možnosti poznámek pod čarou a přizpůsobit jejich vzhled a chování. Zde je postup:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Přidání vysvětlivek do vašeho dokumentu

Přidání vysvětlivky do dokumentu je jednoduché. Zde je příklad:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Přizpůsobení nastavení Endnote

Nastavení koncových poznámek můžete dále upravit tak, aby vyhovovalo vašim požadavkům na dokument.

## Kompletní zdrojový kód
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Zadejte počet sloupců, se kterými je oblast poznámek pod čarou formátována.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. Závěr

V tomto tutoriálu jsme prozkoumali, jak pracovat s poznámkami pod čarou a vysvětlivkami v Aspose.Words for Java. Tyto funkce jsou neocenitelné pro vytváření dobře strukturovaných dokumentů se správnými citacemi a odkazy.

Nyní, když jste se naučili používat poznámky pod čarou a vysvětlivky, můžete vylepšit formátování dokumentu a učinit svůj obsah profesionálnějším.

### Často kladené otázky

### 1. Jaký je rozdíl mezi poznámkami pod čarou a vysvětlivkami?
Poznámky pod čarou se zobrazují ve spodní části stránky, zatímco vysvětlivky se shromažďují na konci oddílu nebo dokumentu.

### 2. Jak mohu změnit pozici poznámek pod čarou nebo vysvětlivky?
 Můžete použít`setPosition` metoda pro změnu pozice poznámek pod čarou nebo vysvětlivky.

### 3. Mohu přizpůsobit formátování poznámek pod čarou a vysvětlivky?
Ano, můžete upravit formátování poznámek pod čarou a vysvětlivky pomocí Aspose.Words for Java.

### 4. Jsou poznámky pod čarou a vysvětlivky důležité při formátování dokumentu?
Ano, poznámky pod čarou a vysvětlivky jsou nezbytné pro poskytování odkazů a dalších informací v dokumentech.

Neváhejte a prozkoumejte další funkce Aspose.Words for Java a vylepšete své možnosti vytváření dokumentů. Šťastné kódování!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
