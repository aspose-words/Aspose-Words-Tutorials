---
date: 2026-01-16
description: Naučte se, jak převést palce na body, číst metadata dokumentu v Javě,
  přidávat vlastní vlastnosti v Javě a nastavovat okraje stránky v Javě pomocí Aspose.Words
  pro Javu.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Převod palců na body – Použití vlastností dokumentu v Aspose.Words pro Java
url: /cs/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Převod palců na body – Použití vlastností dokumentu v Aspose.Words pro Java

V tomto tutoriálu se dozvíte, jak **převést palce na body** při nastavování okrajů stránky, číst metadata dokumentu v Javě, přidávat vlastní vlastnosti v Javě a pracovat se zabudovanými vlastnostmi dokumentu pomocí Aspose.Words pro Java. Ať už generujete zprávy, faktury nebo právní dokumenty, zvládnutí těchto technik vám poskytne detailní kontrolu nad vzhledem i metadaty vašich souborů Word.

## Rychlé odpovědi
- **Jak převést palce na body?** Použijte `ConvertUtil.inchToPoint(value)` z Aspose.Words.
- **Mohu číst metadata dokumentu v Javě?** Ano – zavolejte `doc.getBuiltInDocumentProperties()` nebo `doc.getCustomDocumentProperties()`.
- **Jak přidám vlastní vlastnost v Javě?** Použijte `doc.getCustomDocumentProperties().add(name, value)`.
- **Jaká metoda nastavuje okraje stránky v bodech?** `PageSetup.setTopMargin`, `setBottomMargin` atd. přijímají hodnoty v bodech.
- **Je podporováno odkazování na záložku?** Ano – použijte `addLinkToContent` na kolekci vlastností.

## Úvod do vlastností dokumentu

Vlastnosti dokumentu jsou důležitou součástí každého souboru Word. Uchovávají informace jako název, autor, předmět, klíčová slova a libovolná vlastní metadata potřebná pro následné zpracování. V Aspose.Words pro Java můžete manipulovat jak se zabudovanými, tak s vlastními vlastnostmi dokumentu a také řídit detaily rozvržení, jako jsou okraje, převodem měrných jednotek (např. **převod palců na body**).

## Co je „převod palců na body“?

V aplikaci Word jsou rozvrhové měření vyjádřeny v bodech (1 bod = 1/72 palce). Převod palců na body vám umožní definovat okraje, odsazení a mezery pomocí známých imperiálních jednotek, zatímco API interně pracuje s body.

## Proč spravovat metadata dokumentu v Javě?

Vkládání metadat usnadňuje vyhledávání, kategorizaci a automatizaci pracovních postupů. Například můžete označit smlouvu příznakem „Authorized“ nebo uložit číslo revize pro auditní stopy. Čtení a zápis těchto informací programově zajišťuje konzistenci napříč velkými dávkami dokumentů.

## Požadavky
- Java 17+ (nebo kompatibilní JDK)
- Knihovna Aspose.Words pro Java přidaná do projektu (Maven/Gradle)
- Ukázkový soubor `.docx` (např. `Properties.docx`) umístěný v přístupném adresáři

## Průvodce krok za krokem

### Výpis zabudovaných vlastností dokumentu
Níže je jednoduchý test, který otevře dokument a vypíše všechny zabudované vlastnosti, jako je Název, Autor a Klíčová slova.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Tip:** Použijte tento úryvek k ověření, že vaše metadata byla během předchozích kroků správně zapsána.

### Přidání vlastních vlastností dokumentu (add custom properties java)
Vlastní vlastnosti vám umožní uložit libovolný datový typ – boolean, string, datum, číslo atd.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Proč je to důležité:** Přidání příznaku jako **Authorized** může řídit následné schvalovací workflow bez změny obsahu dokumentu.

### Odstranění vlastní vlastnosti
Pokud vlastnost již není potřeba, můžete ji čistě smazat.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Nastavení odkazu na obsah (odkazování na záložku)
Můžete vytvořit záložku a poté přidat vlastní vlastnost, která na tuto záložku odkazuje, což umožní dynamické křížové odkazy.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Převod mezi měrnými jednotkami (set page margins java)
Zde se uplatní hlavní klíčové slovo. Nastavíme okraje v palcích a poté **převodíme palce na body** pomocí `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Poznámka:** `ConvertUtil` také poskytuje `pointToInch`, `mmToPoint` a další metody pro flexibilní práci s rozvržením.

### Použití řídicích znaků (read document metadata java)
Řídicí znaky vám pomáhají čistit textové proudy. Tento příklad nahrazuje návrat vozíku (`\r`) sekvencí Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Časté problémy a řešení
| Problém | Příčina | Řešení |
|---------|----------|--------|
| Okraje vypadají špatně po převodu | Použitá špatná jednotka (např. cm místo palců) | Ověřte, že voláte `ConvertUtil.inchToPoint` pro hodnoty v palcích |
| Vlastní vlastnost se nezobrazuje | Vlastnost přidána po uložení dokumentu | Zavolejte `doc.save(...)` po přidání vlastností |
| Odkaz na záložku nefunguje | Překlep v názvu záložky | Ujistěte se, že název záložky přesně odpovídá v `addLinkToContent` |

## Často kladené otázky

### Jak získat přístup k zabudovaným vlastnostem dokumentu?

Pro získání zabudovaných vlastností dokumentu v Aspose.Words pro Java použijte metodu `getBuiltInDocumentProperties` na objektu `Document`. Tato metoda vrací kolekci zabudovaných vlastností, kterou můžete iterovat.

### Mohu přidat vlastní vlastnosti dokumentu?

Ano, vlastní vlastnosti můžete přidat pomocí kolekce `CustomDocumentProperties`. Lze definovat vlastnosti různých datových typů, včetně řetězců, boolean, datumů a číselných hodnot.

### Jak mohu odstranit konkrétní vlastní vlastnost dokumentu?

Pro odstranění konkrétní vlastní vlastnosti použijte metodu `remove` na kolekci `CustomDocumentProperties` a jako parametr uveďte název vlastnosti, kterou chcete odstranit.

### Jaký je účel odkazování na obsah v dokumentu?

Odkazování na obsah v dokumentu umožňuje vytvářet dynamické reference na konkrétní části dokumentu. To je užitečné při tvorbě interaktivních dokumentů nebo křížových odkazů mezi sekcemi.

### Jak mohu převádět mezi různými měrnými jednotkami v Aspose.Words pro Java?

Měřité jednotky můžete převádět pomocí třídy `ConvertUtil`. Nabízí metody pro převod jednotek, jako jsou palce na body, body na centimetry a další.

## Frequently Asked Questions

**Q: Jak číst metadata dokumentu v Javě, aniž bych načetl celý soubor?**  
A: Použijte `DocumentInfo` k získání základních vlastností bez úplného načtení obsahu dokumentu.

**Q: Mohu programově nastavit okraje stránky v Javě pro existující dokumenty?**  
A: Ano – otevřete dokument, upravte okraje `PageSetup` (převodem palců na body, pokud je potřeba) a uložte.

**Q: Je možné exportovat vlastní vlastnosti do PDF metadat?**  
A: Při ukládání do PDF Aspose.Words automaticky mapuje vlastní vlastnosti dokumentu na vlastní PDF metadata.

**Q: Ovlivňují řídicí znaky konverzi do PDF?**  
A: Během konverze jsou zachovány; přesto můžete chtít normalizovat konce řádků pro konzistenci.

**Q: Jaká verze Aspose.Words je vyžadována pro `ConvertUtil`?**  
A: `ConvertUtil` je k dispozici od Aspose.Words 16.5; jakákoli novější verze jej podporuje.

## Závěr

Ovládnutím **převodu palců na body**, čtením metadat dokumentu v Javě a přidáváním vlastních vlastností v Javě získáte plnou kontrolu jak nad vizuálním rozvržením, tak nad skrytými daty vašich souborů Word. Tyto možnosti vám umožní budovat automatizované pipeline dokumentů, vynucovat soulad s předpisy a vytvářet bohatě formátované zprávy – vše s Aspose.Words pro Java.

---

**Poslední aktualizace:** 2026-01-16  
**Testováno s:** Aspose.Words pro Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}