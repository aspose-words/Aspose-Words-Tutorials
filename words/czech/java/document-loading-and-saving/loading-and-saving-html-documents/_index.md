---
date: 2025-12-20
description: Naučte se, jak načíst HTML a převést HTML na DOCX pomocí Aspose.Words
  pro Java. Průvodce krok za krokem ukazuje, jak ukládat soubory DOCX a používat strukturované
  značky dokumentu.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Jak načíst HTML a uložit jako DOCX pomocí Aspose.Words pro Java
url: /cs/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak načíst HTML a uložit jako DOCX pomocí Aspose.Words pro Java

## Úvod do načítání a ukládání HTML dokumentů pomocí Aspose.Words pro Java

V tomto článku se podíváme na **jak načíst html** a uložit jej jako soubor DOCX pomocí knihovny Aspose.Words pro Java. Aspose.Words je výkonné API, které vám umožňuje programově manipulovat s dokumenty Word a zahrnuje robustní podporu pro import/export HTML. Provedeme celý proces, od nastavení možností načítání až po uložení výsledku jako dokument Word.

## Rychlé odpovědi
- **Jaká je hlavní třída pro načítání HTML?** `Document` spolu s `HtmlLoadOptions`.
- **Která možnost povoluje Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Mohu převést HTML na DOCX v jednom kroku?** Ano – načtěte HTML a zavolejte `doc.save(...".docx")`.
- **Potřebuji licenci pro vývoj?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována komerční licence.
- **Jaká verze Javy je vyžadována?** Java 8 nebo vyšší je podporována.

## Co znamená „jak načíst html“ v kontextu Aspose.Words?

Načítání HTML znamená čtení HTML řetězce nebo souboru a jeho převod na objekt `Document` z Aspose.Words. Tento objekt pak může být upravován, formátován nebo uložen do libovolného formátu podporovaného API, jako je DOCX, PDF nebo RTF.

## Proč použít Aspose.Words pro konverzi HTML‑na‑DOCX?

- **Zachovává rozvržení** – tabulky, seznamy a obrázky zůstávají nedotčeny.
- **Podporuje Structured Document Tags** – ideální pro vytváření ovládacích prvků obsahu ve Wordu.
- **Není vyžadován Microsoft Office** – funguje na jakémkoli serveru nebo v cloudovém prostředí.
- **Vysoký výkon** – rychle zpracovává velké HTML soubory.

## Požadavky

1. **Knihovna Aspose.Words pro Java** – stáhněte ji z [zde](https://releases.aspose.com/words/java/).
2. **Vývojové prostředí Java** – nainstalovaný a nakonfigurovaný JDK 8+.
3. **Základní znalost Java I/O** – použijeme `ByteArrayInputStream` k předání HTML řetězce.

## Jak načíst HTML dokumenty

Níže je stručný příklad, který ukazuje načtení úryvku HTML při povolení funkce **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Vysvětlení**

- Vytvoříme řetězec `HTML`, který obsahuje jednoduchý ovládací prvek `<select>`.
- `HtmlLoadOptions` nám umožňuje určit, jak má být HTML interpretováno. Nastavením preferovaného typu ovládacího prvku na `STRUCTURED_DOCUMENT_TAG` říkáme Aspose.Words, aby převáděl HTML formulářové ovládací prvky na obsahové ovládací prvky Wordu.
- Konstruktor `Document` načte HTML z `ByteArrayInputStream` s použitím kódování UTF‑8.

## Jak uložit jako DOCX (převod HTML na DOCX)

Jakmile je HTML načteno do objektu `Document`, uložení jako soubor DOCX je jednoduché:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Nahraďte `"Your Directory Path"` skutečnou složkou, kam chcete, aby se výstupní soubor uložil.

## Kompletní zdrojový kód pro načítání a ukládání HTML dokumentů

Níže je kompletní, připravený příklad, který kombinuje kroky načtení a uložení. Klidně jej zkopírujte a vložte do svého IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Časté úskalí a tipy

| Problém | Proč k tomu dochází | Jak opravit |
|-------|----------------|------------|
| **Chybějící fonty** | HTML odkazuje na fonty, které nejsou na serveru nainstalovány. | Vložte fonty do DOCX pomocí `FontSettings` nebo zajistěte, aby požadované fonty byly dostupné. |
| **Obrázky se nezobrazují** | Relativní cesty k obrázkům nelze vyřešit. | Použijte absolutní URL nebo načtěte obrázky do `MemoryStream` a nastavte `HtmlLoadOptions.setImageSavingCallback`. |
| **Typ ovládacího prvku není převeden** | `setPreferredControlType` není nastaven nebo je nastaven na špatný enum. | Ověřte, že používáte `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Problémy s kódováním** | HTML řetězec je kódován jinou znakovou sadou. | Vždy používejte `StandardCharsets.UTF_8` při převodu řetězce na bajty. |

## Často kladené otázky

### Jak nainstalovat Aspose.Words pro Java?

Aspose.Words pro Java lze stáhnout z [zde](https://releases.aspose.com/words/java/). Postupujte podle instalačního průvodce na stránce ke stažení a přidejte soubory JAR do classpath vašeho projektu.

### Mohu načíst složité HTML dokumenty pomocí Aspose.Words?

Ano, Aspose.Words pro Java dokáže zpracovat složité HTML, včetně vnořených tabulek, CSS stylování a interaktivních prvků bez JavaScriptu. Upravit `HtmlLoadOptions` (např. `setLoadImages` nebo `setCssStyleSheetFileName`) pro jemné nastavení importu.

### Jaké další formáty dokumentů Aspose.Words podporuje?

Aspose.Words podporuje DOC, DOCX, RTF, HTML, PDF, EPUB, XPS a mnoho dalších. API umožňuje jednorázové uložení do libovolného z těchto formátů.

### Je Aspose.Words vhodný pro podnikovou automatizaci dokumentů?

Rozhodně. Používá jej velké podniky pro automatizovanou tvorbu reportů, hromadnou konverzi dokumentů a serverové zpracování dokumentů bez závislosti na Microsoft Office.

### Kde najdu další dokumentaci a příklady pro Aspose.Words pro Java?

Úplnou referenci API a další tutoriály můžete prozkoumat na stránce dokumentace Aspose.Words pro Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Poslední aktualizace:** 2025-12-20  
**Testováno s:** Aspose.Words for Java 24.12 (nejnovější v době psaní)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}