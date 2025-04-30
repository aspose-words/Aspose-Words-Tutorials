---
"description": "Naučte se, jak generovat a upravovat obsah (TOC) pomocí Aspose.Words pro Javu. Vytvářejte bez námahy organizované a profesionální dokumenty."
"linktitle": "Generování obsahu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Generování obsahu v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generování obsahu v Aspose.Words pro Javu


## Úvod do generování obsahu v Aspose.Words pro Javu

tomto tutoriálu vás provedeme procesem generování obsahu (TOC) pomocí Aspose.Words pro Javu. Obsah je klíčová funkce pro vytváření organizovaných dokumentů. Probereme, jak přizpůsobit vzhled a rozvržení obsahu.

## Předpoklady

Než začnete, ujistěte se, že máte ve svém projektu Java nainstalovaný a nastavený Aspose.Words pro Javu.

## Krok 1: Vytvořte nový dokument

Nejprve si vytvořme nový dokument, se kterým budeme pracovat.

```java
Document doc = new Document();
```

## Krok 2: Úprava stylů obsahu

Chcete-li přizpůsobit vzhled obsahu, můžete upravit styly, které jsou s ním spojeny. V tomto příkladu zvýrazníme položky obsahu první úrovně tučně.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Krok 3: Přidání obsahu do dokumentu

Do dokumentu můžete přidat svůj obsah. Tento obsah bude použit k vygenerování obsahu.

## Krok 4: Vygenerování obsahu

Chcete-li vygenerovat obsah, vložte pole s obsahem na požadované místo v dokumentu. Toto pole se automaticky vyplní na základě nadpisů a stylů v dokumentu.

```java
// Vložte pole obsahu na požadované místo v dokumentu.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Krok 5: Uložte dokument

Nakonec dokument uložte s obsahem.

```java
doc.save("your_output_path_here");
```

## Přizpůsobení zarážek tabulace v obsahu

Zarážky tabulátoru v obsahu si také můžete přizpůsobit a ovládat tak rozvržení čísel stránek. Zde je návod, jak je změnit:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Získejte první tabulaci použitou v tomto odstavci, která zarovná čísla stránek.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Odstraňte starou záložku.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Vložte novou záložku na upravenou pozici (např. 50 jednotek vlevo).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nyní máte v dokumentu přizpůsobený obsah s upravenými zarážkami tabulátoru pro zarovnání čísel stránek.


## Závěr

V tomto tutoriálu jsme prozkoumali, jak generovat obsah (TOC) pomocí Aspose.Words pro Javu, výkonné knihovny pro práci s dokumenty Wordu. Dobře strukturovaný obsah je nezbytný pro organizaci a navigaci v dlouhých dokumentech a Aspose.Words poskytuje nástroje pro snadné vytváření a úpravu obsahu.

## Často kladené otázky

### Jak změním formátování položek obsahu?

Styly spojené s úrovněmi obsahu můžete upravit pomocí `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, kde X je úroveň obsahu obsahu organických látek (TOC).

### Jak mohu do obsahu přidat další úrovně?

Chcete-li do obsahu zahrnout více úrovní, můžete upravit pole Obsah a zadat požadovaný počet úrovní.

### Mohu změnit pozice zarážek tabulátoru u konkrétních položek obsahu?

Ano, jak je znázorněno ve výše uvedeném příkladu kódu, můžete změnit pozice zarážek tabulátoru pro konkrétní položky obsahu iterací odstavců a odpovídající úpravou zarážek tabulátoru.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}