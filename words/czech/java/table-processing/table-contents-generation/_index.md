---
title: Generování obsahu
linktitle: Generování obsahu
second_title: Aspose.Words Java Document Processing API
description: Naučte se vytvářet dynamický obsah pomocí Aspose.Words for Java. Ovládněte generování TOC s podrobnými pokyny a příklady zdrojového kódu.
weight: 14
url: /cs/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generování obsahu

## Zavedení

Měli jste někdy problémy s vytvořením dynamického a profesionálně vypadajícího obsahu (TOC) ve vašich dokumentech aplikace Word? Už nehledejte! S Aspose.Words for Java můžete automatizovat celý proces, čímž ušetříte čas a zajistíte přesnost. Ať už vytváříte komplexní zprávu nebo akademickou práci, tento tutoriál vás provede programovým generováním TOC pomocí Javy. Jste připraveni se ponořit? Začněme!

## Předpoklady

Než začneme kódovat, ujistěte se, že máte následující:

1.  Java Development Kit (JDK): Nainstalovaný ve vašem systému. Můžete si jej stáhnout z[Web společnosti Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words for Java Library: Stáhněte si nejnovější verzi z[stránka vydání](https://releases.aspose.com/words/java/).
3. Integrované vývojové prostředí (IDE): Například IntelliJ IDEA, Eclipse nebo NetBeans.
4.  Aspose Temporary License: Abyste se vyhnuli omezením hodnocení, získejte a[dočasná licence](https://purchase.aspose.com/temporary-license/).

## Importujte balíčky

Chcete-li používat Aspose.Words pro Java efektivně, ujistěte se, že importujete požadované třídy. Zde jsou dovozy:

```java
import com.aspose.words.*;
```

Chcete-li ve svém dokumentu aplikace Word vygenerovat dynamický obsah, postupujte podle těchto kroků.

## Krok 1: Inicializujte Document a DocumentBuilder

 Prvním krokem je vytvoření nového dokumentu a použití`DocumentBuilder` třídy s ním manipulovat.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Představuje dokument aplikace Word.
- `DocumentBuilder`: Pomocná třída, která umožňuje snadnou manipulaci s dokumentem.

## Krok 2: Vložte obsah

Nyní vložíme TOC na začátek dokumentu.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Vloží pole TOC. Parametry specifikují:
  - `\o "1-3"`: Zahrňte nadpisy úrovní 1 až 3.
  - `\h`: Vytvořte položky jako hypertextové odkazy.
  - `\z`: Potlačit čísla stránek pro webové dokumenty.
  - `\u`: Zachovat styly pro hypertextové odkazy.
- `insertBreak`: Přidá konec stránky za obsah.

## Krok 3: Přidejte nadpisy k vyplnění obsahu

Abyste naplnili obsah, musíte přidat odstavce se styly nadpisů.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Nastaví styl odstavce na konkrétní úroveň nadpisu (např.`HEADING_1`, `HEADING_2`).
- `writeln`: Přidá text do dokumentu se zadaným stylem.

## Krok 4: Přidejte vnořené nadpisy

Chcete-li předvést úrovně obsahu, zahrňte vnořené nadpisy.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Přidejte nadpisy hlubších úrovní, abyste zobrazili hierarchii v obsahu.

## Krok 5: Aktualizujte pole obsahu

Pole TOC musí být aktualizováno, aby se zobrazily nejnovější nadpisy.


```java
doc.updateFields();
```

- `updateFields`: Obnoví všechna pole v dokumentu a zajistí, že TOC odráží přidané nadpisy.

## Krok 6: Uložte dokument

Nakonec uložte dokument do požadovaného formátu.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exportuje dokument do a`.docx` soubor. Můžete zadat jiné formáty jako např`.pdf` nebo`.txt` v případě potřeby.

## Závěr

Gratuluji! Úspěšně jste vytvořili dynamický obsah v dokumentu aplikace Word pomocí Aspose.Words for Java. Pomocí několika řádků kódu jste zautomatizovali úkol, který by jinak mohl trvat hodiny. Takže, co bude dál? Zkuste experimentovat s různými styly a formáty nadpisů, abyste přizpůsobili svůj obsah konkrétním potřebám.

## FAQ

### Mohu si formát TOC dále přizpůsobit?
Absolutně! Můžete upravit parametry obsahu, jako je zahrnutí čísel stránek, zarovnání textu nebo použití vlastních stylů nadpisů.

### Je licence pro Aspose.Words pro Java povinná?
 Ano, pro plnou funkčnost je nutná licence. Můžete začít s a[dočasná licence](https://purchase.aspose.com/temporary-license/).

### Mohu vygenerovat TOC pro existující dokument?
 Ano! Vložte dokument do a`Document` objekt a postupujte podle stejných kroků pro vložení a aktualizaci obsahu.

### Funguje to pro exporty PDF?
 Ano, obsah se zobrazí v PDF, pokud dokument uložíte`.pdf` formát.

### Kde najdu další dokumentaci?
 Podívejte se na[Aspose.Words pro dokumentaci Java](https://reference.aspose.com/words/java/) pro více příkladů a podrobností.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
