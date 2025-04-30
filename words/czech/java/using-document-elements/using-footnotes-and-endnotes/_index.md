---
"description": "Naučte se efektivně používat poznámky pod čarou a vysvětlivky v Aspose.Words pro Javu. Zlepšete si své dovednosti formátování dokumentů ještě dnes!"
"linktitle": "Používání poznámek pod čarou a poznámek na konci"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání poznámek pod čarou a koncových poznámek v Aspose.Words pro Javu"
"url": "/cs/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání poznámek pod čarou a koncových poznámek v Aspose.Words pro Javu


tomto tutoriálu vás provedeme procesem používání poznámek pod čarou a koncových poznámek v Aspose.Words pro Javu. Poznámky pod čarou a koncové poznámky jsou základními prvky formátování dokumentů a často se používají pro citace, odkazy a další informace. Aspose.Words pro Javu poskytuje robustní funkce pro bezproblémovou práci s poznámkami pod čarou a koncovými poznámkami.

## 1. Úvod do poznámek pod čarou a poznámek na konci textu

Poznámky pod čarou a koncové poznámky jsou anotace, které poskytují doplňující informace nebo citace v dokumentu. Poznámky pod čarou se zobrazují ve spodní části stránky, zatímco koncové poznámky se shromažďují na konci části nebo dokumentu. Běžně se používají v akademických pracích, zprávách a právních dokumentech k odkazování na zdroje nebo k objasnění obsahu.

## 2. Nastavení prostředí

Než se pustíme do práce s poznámkami pod čarou a vysvětlivkami, je třeba si nastavit vývojové prostředí. Ujistěte se, že máte ve svém projektu nainstalované a nakonfigurované rozhraní Aspose.Words pro Java API.

## 3. Přidání poznámek pod čarou do dokumentu

Chcete-li do dokumentu přidat poznámky pod čarou, postupujte takto:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Zadejte počet sloupců, s nimiž bude formátována oblast poznámek pod čarou.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Úprava možností poznámky pod čarou

Vzhled a chování poznámek pod čarou můžete upravit úpravou možností. Postupujte takto:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Přidání poznámek na konci dokumentu

Přidání poznámek na konci dokumentu je jednoduché. Zde je příklad:
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

## 6. Úprava nastavení poznámky na konci

Nastavení poznámky na konci textu si můžete dále přizpůsobit tak, aby splňovala požadavky vašeho dokumentu.

## Kompletní zdrojový kód
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Zadejte počet sloupců, s nimiž bude formátována oblast poznámek pod čarou.
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

V tomto tutoriálu jsme prozkoumali, jak pracovat s poznámkami pod čarou a vysvětlivkami v Aspose.Words pro Javu. Tyto funkce jsou neocenitelné pro vytváření dobře strukturovaných dokumentů se správnými citacemi a odkazy.

Nyní, když jste se naučili používat poznámky pod čarou a vysvětlivky, můžete vylepšit formátování dokumentu a zkvalitnit jeho obsah.

### Často kladené otázky

### 1. Jaký je rozdíl mezi poznámkami pod čarou a poznámkami na konci?
Poznámky pod čarou se zobrazují ve spodní části stránky, zatímco poznámky na konci sekce nebo dokumentu se shromažďují na konci.

### 2. Jak mohu změnit umístění poznámek pod čarou nebo koncových poznámek?
Můžete použít `setPosition` metoda pro změnu umístění poznámek pod čarou nebo koncových poznámek.

### 3. Mohu si přizpůsobit formátování poznámek pod čarou a vysvětlivek?
Ano, formátování poznámek pod čarou a vysvětlivek si můžete přizpůsobit pomocí Aspose.Words pro Javu.

### 4. Jsou poznámky pod čarou a vysvětlivky důležité pro formátování dokumentu?
Ano, poznámky pod čarou a koncové poznámky jsou nezbytné pro uvádění odkazů a dalších informací v dokumentech.

Neváhejte a prozkoumejte další funkce Aspose.Words pro Javu a vylepšete si své možnosti tvorby dokumentů. Přejeme vám příjemné programování!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}