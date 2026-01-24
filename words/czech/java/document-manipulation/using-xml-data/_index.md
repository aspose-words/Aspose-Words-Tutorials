---
date: 2026-01-24
description: Naučte se, jak sloučit XML data s Aspose.Words pro Java, automatizovat
  generování dokumentů v Javě a používat syntaxi Mustache pro dynamické dokumenty.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Jak sloučit XML v Aspose.Words pro Javu
url: /cs/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak sloučit XML v Aspose.Words pro Java

V tomto komplexním průvodci se dozvíte **jak sloučit XML** data pomocí Aspose.Words pro Java. Provedeme vás základními i vnořenými scénáři hromadné korespondence, ukážeme vám **použití syntaxe Mustache** a vysvětlíme, jak **automatizovat generování dokumentů** ve stylech Java‑projektů. Na konci budete schopni generovat personalizované Word dokumenty přímo ze zdrojů XML pomocí několika řádků kódu.

## Rychlé odpovědi
- **Jaká je hlavní třída pro hromadnou korespondenci?** `Document` a její vlastnost `MailMerge`.  
- **Mohu sloučit vnořené XML tabulky?** Ano – použijte `executeWithRegions` pro hierarchická data.  
- **Je syntaxe Mustache podporována?** Aktivujte ji pomocí `setUseNonMergeFields(true)`.  
- **Potřebuji licenci pro produkci?** Pro komerční nasazení je vyžadována licence Aspose.Words.  
- **Která verze Javy je kompatibilní?** Java 8+ a novější jsou plně podporovány.

## Co je XML Mail Merge v Aspose.Words?
XML mail merge vám umožňuje svázat dataset založený na XML s zástupnými symboly ve Word šabloně. Engine nahradí každý zástupný symbol odpovídající hodnotou uzlu XML a vytvoří hotový dokument bez ruční úpravy.

## Proč použít Aspose.Words pro generování dokumentů založených na XML?
- **Automatizujte generování dokumentů Java** projektů bez jakýchkoli závislostí na Microsoft Office.  
- **Podpora složitých hierarchií** – vnořené tabulky, opakující se sekce a podmíněný obsah.  
- **Syntaxe Mustache** poskytuje flexibilní, ne‑merge‑field zástupné symboly pro pokročilé šablonování.  
- **Cross‑platform** – funguje na Windows, Linuxu i macOS.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) nainstalovaný (nejnovější verze).  
- Ukázkové XML soubory pro zákazníky, objednávky a dodavatele (v tutorialu jsou použity `Mail merge data - Customers.xml`, `Orders.xml` a `Vendors.xml`).  
- Word šablony obsahující merge fields (např. `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Jak sloučit XML – Základní hromadná korespondence

Základní hromadná korespondence načte jednu XML tabulku do Word šablony. Postupujte podle těchto kroků:

1. Načtěte XML soubor do `DataSet`.  
2. Otevřete cílový Word dokument.  
3. Proveďte sloučení pomocí názvu tabulky.  
4. Uložte sloučený dokument.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Tip:** Pro jednoduché sloučení udržujte strukturu XML plochou – každá tabulka by měla přímo mapovat na sadu merge fields.

## Jak sloučit XML – Vnořená hromadná korespondence

Když vaše XML obsahuje vztahy rodič‑potomek (např. objednávky s položkami), potřebujete vnořené sloučení. Metoda `executeWithRegions` zpracuje každou oblast rekurzivně.

1. Načtěte hierarchické XML do `DataSet`.  
2. Zakážete ořezávání mezer, pokud potřebujete přesné formátování.  
3. Zavolejte `executeWithRegions` pro zpracování všech vnořených tabulek.  
4. Uložte výsledek.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Častý úskalí:** Zapomenutí nastavit `setTrimWhitespaces(false)` může vést k nechtěným mezerám ve finálním dokumentu, zejména u měn nebo číselných polí.

## Jak použít Mustache syntaxi s DataSet

Syntaxe Mustache vám umožní vložit ne‑merge‑field zástupné symboly (např. `{{CustomerName}}`) do šablony. Aktivujte ji a spusťte sloučení založené na oblastech.

1. Načtěte XML dodavatele.  
2. Zapněte podporu Mustache pomocí `setUseNonMergeFields(true)`.  
3. Proveďte sloučení s oblastmi.  
4. Uložte výstup.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Proč používat Mustache?** Poskytuje čistý, jazykově neutrální způsob odkazování na data, což usnadňuje čitelnost a údržbu šablon, zejména při **generování dokumentů řízených XML** workflow.

## Časté problémy a řešení

| Problém | Řešení |
|-------|----------|
| XML uzly neodpovídají merge fields | Ověřte, že názvy XML elementů přesně odpovídají názvům merge fields (rozlišuje se velikost písmen). |
| Okolo sloučených hodnot se objevují mezery | Použijte `doc.getMailMerge().setTrimWhitespaces(false)` pro zachování původního odsazení. |
| Vnořené tabulky jsou ignorovány | Ujistěte se, že oblast rodičovské tabulky je definována v šabloně (např. `{{#Orders}} … {{/Orders}}`). |
| Mustache zástupné symboly nejsou nahrazeny | Zavolejte `setUseNonMergeFields(true)` před provedením sloučení. |

## Často kladené otázky

### Jak připravit XML data pro hromadnou korespondenci?

Ujistěte se, že vaše XML má tabulkovou strukturu, kde každý element `<TableName>` obsahuje řádky (`<Row>`) a sloupce odpovídající merge fields ve vaší Word šabloně.

### Mohu přizpůsobit chování ořezávání hodnot při hromadné korespondenci?

Ano. Použijte `doc.getMailMerge().setTrimWhitespaces(false)` pro zachování mezer na začátku i na konci přesně tak, jak jsou v XML.

### Co je to Mustache syntaxe a kdy ji mám použít?

Mustache syntax (`{{FieldName}}`) umožňuje flexibilní zástupné symboly, které nejsou omezeny na tradiční merge fields. Aktivujte ji pomocí `setUseNonMergeFields(true)`, když potřebujete čistší šablonu nebo chcete oddělit logiku dat od kódů Word polí.

### Jak automatizovat generování dokumentů Java projektů tímto přístupem?

Začleňte výše uvedené úryvky kódu do servisní vrstvy, načítejte XML z databází nebo API a vyvolejte rutinu sloučení vždy, když je potřeba nový dokument (např. generování faktur, tvorba smluv).

### Je pro produkční použití vyžadována komerční licence?

Ano, Aspose.Words vyžaduje platnou licenci pro produkční nasazení. Pro vyhodnocení je k dispozici bezplatná dočasná licence.

---

**Poslední aktualizace:** 2026-01-24  
**Testováno s:** Aspose.Words for Java (nejnovější vydání)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}