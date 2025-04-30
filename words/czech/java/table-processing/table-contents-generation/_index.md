---
"description": "Naučte se, jak vytvořit dynamický obsah pomocí Aspose.Words pro Javu. Zvládněte generování obsahu s podrobnými pokyny a příklady zdrojového kódu."
"linktitle": "Generování obsahu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Generování obsahu"
"url": "/cs/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generování obsahu

## Zavedení

Už jste někdy měli problém s vytvořením dynamického a profesionálně vypadajícího obsahu (TOC) ve vašich dokumentech Word? Už nehledejte! S Aspose.Words pro Javu můžete celý proces automatizovat, ušetřit čas a zajistit přesnost. Ať už vytváříte komplexní zprávu nebo akademickou práci, tento tutoriál vás provede programově generovaným obsahem v Javě. Jste připraveni se do toho pustit? Pojďme na to!

## Předpoklady

Než začneme s kódováním, ujistěte se, že máte následující:

1. Vývojářská sada Java (JDK): Nainstalovaná ve vašem systému. Můžete si ji stáhnout z [Webové stránky společnosti Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Knihovna Aspose.Words pro Javu: Stáhněte si nejnovější verzi z [stránka s vydáním](https://releases.aspose.com/words/java/).
3. Integrované vývojové prostředí (IDE): Například IntelliJ IDEA, Eclipse nebo NetBeans.
4. Dočasná licence Aspose: Abyste se vyhnuli omezením hodnocení, pořiďte si [dočasná licence](https://purchase.aspose.com/temporary-license/).

## Importovat balíčky

Abyste mohli Aspose.Words pro Javu efektivně používat, ujistěte se, že jste importovali požadované třídy. Zde jsou importy:

```java
import com.aspose.words.*;
```

Chcete-li v dokumentu Word vygenerovat dynamický obsah, postupujte podle těchto kroků.

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Prvním krokem je vytvoření nového dokumentu a jeho použití. `DocumentBuilder` třídu s ní manipulovat.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Představuje dokument aplikace Word.
- `DocumentBuilder`Pomocná třída, která umožňuje snadnou manipulaci s dokumentem.

## Krok 2: Vložení obsahu

Nyní vložme obsah na začátek dokumentu.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`Vloží pole obsahu. Parametry určují:
  - `\o "1-3"`Zahrňte nadpisy úrovní 1 až 3.
  - `\h`Vytvořte z položek hypertextové odkazy.
  - `\z`: Potlačit čísla stránek pro webové dokumenty.
  - `\u`Zachovat styly pro hypertextové odkazy.
- `insertBreak`: Přidá zalomení stránky za obsah.

## Krok 3: Přidání nadpisů k naplnění obsahu

PRO naplnění obsahu je třeba přidat odstavce se styly nadpisů.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: Nastaví styl odstavce na určitou úroveň nadpisu (např. `HEADING_1`, `HEADING_2`).
- `writeln`Přidá do dokumentu text se zadaným stylem.

## Krok 4: Přidání vnořených nadpisů

Pro demonstraci úrovní obsahu zahrňte vnořené nadpisy.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Pro zobrazení hierarchie v obsahu přidejte nadpisy hlubších úrovní.

## Krok 5: Aktualizace polí obsahu

Pole Obsah musí být aktualizováno, aby se zobrazovaly nejnovější nadpisy.


```java
doc.updateFields();
```

- `updateFields`: Obnoví všechna pole v dokumentu a zajistí, aby obsah odrážel přidané nadpisy.

## Krok 6: Uložte dokument

Nakonec dokument uložte v požadovaném formátu.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: Exportuje dokument do `.docx` soubor. Můžete zadat i jiné formáty, například `.pdf` nebo `.txt` v případě potřeby.

## Závěr

Gratulujeme! Úspěšně jste vytvořili dynamický obsah v dokumentu Word pomocí Aspose.Words pro Javu. S pouhými několika řádky kódu jste automatizovali úkol, který by jinak mohl trvat hodiny. Tak co dál? Zkuste experimentovat s různými styly a formáty nadpisů, abyste si obsah přizpůsobili specifickým potřebám.

## Často kladené otázky

### Mohu si formát obsahu dále přizpůsobit?
Rozhodně! Můžete upravit parametry obsahu, jako je zahrnutí čísel stránek, zarovnání textu nebo použití vlastních stylů nadpisů.

### Je pro Aspose.Words pro Javu nutná licence?
Ano, pro plnou funkčnost je vyžadována licence. Můžete začít s [dočasná licence](https://purchase.aspose.com/temporary-license/).

### Mohu vygenerovat obsah pro existující dokument?
Ano! Vložte dokument do `Document` objekt a postupujte podle stejných kroků pro vložení a aktualizaci obsahu.

### Funguje to i pro export PDF?
Ano, obsah se zobrazí v PDF, pokud dokument uložíte v `.pdf` formát.

### Kde najdu další dokumentaci?
Podívejte se na [Dokumentace k Aspose.Words pro Javu](https://reference.aspose.com/words/java/) pro více příkladů a podrobností.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}