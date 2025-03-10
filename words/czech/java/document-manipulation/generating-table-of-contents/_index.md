---
title: Generování obsahu v Aspose.Words pro Javu
linktitle: Generování obsahu
second_title: Aspose.Words Java Document Processing API
description: Naučte se generovat a přizpůsobovat obsah (TOC) pomocí Aspose.Words for Java. Vytvářejte bez námahy organizované a profesionální dokumenty.
weight: 21
url: /cs/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generování obsahu v Aspose.Words pro Javu


## Úvod do generování obsahu v Aspose.Words pro Javu

V tomto tutoriálu vás provedeme procesem generování obsahu (TOC) pomocí Aspose.Words for Java. TOC je klíčová funkce pro vytváření organizovaných dokumentů. Probereme, jak přizpůsobit vzhled a rozvržení obsahu.

## Předpoklady

Než začnete, ujistěte se, že máte Aspose.Words for Java nainstalovaný a nastavený v projektu Java.

## Krok 1: Vytvořte nový dokument

Nejprve vytvoříme nový dokument, se kterým budeme pracovat.

```java
Document doc = new Document();
```

## Krok 2: Přizpůsobte styly obsahu

Chcete-li upravit vzhled vašeho obsahu, můžete upravit styly, které jsou s ním spojené. V tomto příkladu označíme položky TOC první úrovně tučně.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Krok 3: Přidejte obsah do svého dokumentu

Do dokumentu můžete přidat svůj obsah. Tento obsah bude použit ke generování TOC.

## Krok 4: Vygenerujte TOC

Chcete-li vygenerovat obsah, vložte pole obsahu na požadované místo v dokumentu. Toto pole se automaticky vyplní na základě nadpisů a stylů v dokumentu.

```java
// Vložte pole TOC na požadované místo v dokumentu.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Krok 5: Uložte dokument

Nakonec uložte dokument s obsahem.

```java
doc.save("your_output_path_here");
```

## Přizpůsobení zarážek tabulátoru v obsahu

Můžete také přizpůsobit zarážky tabulátoru v obsahu a ovládat tak rozložení čísel stránek. Zarážky tabulátoru můžete změnit takto:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Získejte první kartu použitou v tomto odstavci, která zarovnává čísla stránek.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Odstraňte starou kartu.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Vložte novou záložku na upravenou pozici (např. 50 jednotek vlevo).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nyní máte v dokumentu přizpůsobený obsah s upravenými zarážkami tabulátoru pro zarovnání čísel stránek.


## Závěr

V tomto tutoriálu jsme prozkoumali, jak generovat obsah (TOC) pomocí Aspose.Words for Java, výkonné knihovny pro práci s dokumenty Wordu. Dobře strukturovaný obsah je nezbytný pro organizování a procházení dlouhých dokumentů a Aspose.Words poskytuje nástroje pro snadné vytváření a přizpůsobení obsahu.

## FAQ

### Jak změním formátování položek TOC?

 Styly spojené s úrovněmi obsahu můžete upravit pomocí`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, kde X je úroveň TOC.

### Jak mohu přidat další úrovně do svého obsahu?

Chcete-li do obsahu obsahu zahrnout více úrovní, můžete upravit pole TOC a zadat požadovaný počet úrovní.

### Mohu změnit pozice zarážek tabulátoru pro konkrétní položky obsahu?

Ano, jak je ukázáno ve výše uvedeném příkladu kódu, můžete změnit pozice zarážek tabulátoru pro konkrétní položky obsahu procházením odstavců a odpovídajícími úpravami zarážek tabulátoru.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
