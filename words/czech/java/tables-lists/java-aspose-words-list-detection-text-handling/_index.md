---
"date": "2025-03-28"
"description": "Naučte se, jak zvládnout detekci seznamů, práci s textem a další pomocí Aspose.Words pro Javu. Tato příručka se zabývá detekcí seznamů oddělených mezerami, ořezáváním mezer, určováním směru dokumentu, zakázáním automatické detekce číslování a správou hypertextových odkazů."
"title": "Detekce hlavních seznamů a zpracování textu v Javě s Aspose.Words – kompletní průvodce"
"url": "/cs/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Detekce hlavních seznamů a zpracování textu v Javě s Aspose.Words: Kompletní průvodce

## Zavedení

Práce s dokumenty v prostém textu často představuje problémy s identifikací strukturovaných dat, jako jsou seznamy, kvůli nekonzistentním oddělovačům a problémům s formátováním. Knihovna Aspose.Words pro Javu poskytuje robustní funkce pro řešení těchto problémů, včetně detekce číslování s mezerami, ořezávání mezer, určování směru dokumentu, deaktivace automatické detekce číslování a správy hypertextových odkazů v textových dokumentech. Tento tutoriál vám umožní efektivně manipulovat s textovými daty pomocí Aspose.Words.

**Co se naučíte:**
- Techniky pro detekci seznamů oddělených mezerami
- Metody pro ořezávání nežádoucích mezer z obsahu dokumentu
- Přístupy k určení směru čtení textového souboru
- Způsoby, jak zakázat automatickou detekci číslování
- Strategie pro detekci a správu hypertextových odkazů v dokumentech s prostým textem

Pojďme si projít předpoklady potřebné před implementací těchto funkcí.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

### Požadované knihovny:
- **Aspose.Words pro Javu**Verze 25.3 nebo novější.

### Nastavení prostředí:
- Ujistěte se, že vaše vývojové prostředí podporuje Maven nebo Gradle, protože jsou nezbytné pro správu závislostí.

### Předpoklady znalostí:
- Základní znalost programování v Javě
- Znalost sestavovacích systémů Maven nebo Gradle

## Nastavení Aspose.Words

Chcete-li začít používat Aspose.Words pro Javu ve svém projektu, musíte zahrnout potřebnou závislost. Zde je návod:

**Znalec:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Získání licence

Abyste mohli plně využívat Aspose.Words, zvažte získání licence:
- **Bezplatná zkušební verze**: K dispozici pro testování funkcí.
- **Dočasná licence**Pro účely hodnocení bez omezení.
- **Nákup**Plná licence pro trvalé užívání.

Jakmile máte licenci, inicializujte ji ve své aplikaci, abyste odemkli všechny funkce knihovny.

## Průvodce implementací

Pojďme si jednotlivé funkce rozebrat a podívat se, jak je implementovat pomocí Aspose.Words pro Javu.

### Detekce číslování s bílými znaky

**Přehled:** Tato funkce umožňuje identifikovat seznamy v dokumentech v prostém textu, které používají jako oddělovače mezery.

#### Krok 1: Vložení dokumentu
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Krok 2: Ověření detekce seznamu
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Parametry a metody:*
- `setDetectNumberingWithWhitespaces(true)`: Konfiguruje analyzátor tak, aby rozpoznával seznamy s oddělovači bílými znaky.
- `doc.getLists().getCount()`: Načte počet nalezených seznamů v dokumentu.

### Oříznout úvodní a koncové mezery

**Přehled:** Tato funkce ořezává nepotřebné mezery na začátku nebo konci řádků v dokumentech s prostým textem, čímž zajišťuje čisté formátování textu.

#### Krok 1: Konfigurace možností načítání
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Krok 2: Ověření ořezu
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Klíčové konfigurace:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Ořezává mezery od začátku řádků.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Odstraní mezery na koncích řádků.

### Rozpoznat směr dokumentu

**Přehled:** Určete, zda se má dokument číst zprava doleva (RTL), například hebrejský nebo arabský text.

#### Krok 1: Nastavení automatické detekce
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Zakázat automatickou detekci číslování

**Přehled:** Zabraňte knihovně v automatické detekci a formátování položek seznamu.

#### Krok 1: Konfigurace možností načítání
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Detekce hypertextových odkazů v textu

**Přehled:** Identifikovat a spravovat hypertextové odkazy v dokumentech s prostými texty.

#### Krok 1: Nastavení možností detekce
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Praktické aplikace

1. **Systémy pro správu obsahu (CMS):** Automaticky formátovat uživatelsky generovaný obsah do strukturovaných seznamů.
2. **Nástroje pro extrakci dat:** Použijte detekci seznamů k uspořádání nestrukturovaných dat pro analýzu.
3. **Potrubí pro zpracování textu:** Vylepšete předzpracování dokumentů ořezáváním mezer a detekcí směru textu.

## Úvahy o výkonu

Optimalizace výkonu:
- Načítání dokumentů s minimálními operacemi se zaměřením na nezbytné funkce.
- Spravujte využití paměti zpracováním velkých dokumentů v blocích, kdekoli je to proveditelné.

## Závěr

Využitím Aspose.Words pro Javu můžete efektivně spravovat textová data v dokumentech v prostém textu. Od detekce seznamů oddělených mezerami až po práci se směrem textu a hypertextovými odkazy, tyto výkonné nástroje umožňují robustní manipulaci s dokumenty. Další informace naleznete v [Dokumentace k Aspose.Words](https://reference.aspose.com/words/java/) nebo si vyzkoušejte bezplatnou zkušební verzi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}