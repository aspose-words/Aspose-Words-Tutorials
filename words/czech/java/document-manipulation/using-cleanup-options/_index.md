---
date: 2026-01-11
description: Naučte se, jak vyčistit dokument Word pomocí možností čištění v Aspose.Words
  pro Javu, včetně odstraňování prázdných odstavců, prázdných řádků tabulky a nepoužívaných
  polí.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Vyčistit dokument Word pomocí možností čištění Aspose.Words (Java)
url: /cs/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Čištění dokumentu Word pomocí možností čištění Aspose.Words (Java)

V tomto tutoriálu se dozvíte, jak **vyčistit soubory Word dokumentu** pomocí Aspose.Words pro Java. Ať už generujete faktury, smlouvy nebo hromadné zprávy z mail‑merge, nechtěné prázdné odstavce, nepoužité pole nebo prázdné řádky tabulek mohou výsledný výstup vypadat neprofesionálně. Provedeme vás každou možností čištění krok za krokem, ukážeme vám přesný kód, který potřebujete, a vysvětlíme *proč* je každé nastavení důležité, abyste vždy mohli vytvořit upravené dokumenty.

## Rychlé odpovědi
- **Co znamená „čistit Word dokument“?** Odstranění prázdných odstavců, nepoužitých oblastí merge, prázdných řádků tabulek a dalších nadbytečných prvků po operaci mail‑merge.  
- **Která možnost čištění odstraňuje prázdné odstavce?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Jak mohu smazat prázdné řádky tabulky?** Použijte `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Mohu se zbavit polí, která nikdy nebyla naplněna?** Ano – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` nebo `REMOVE_EMPTY_FIELDS`.  
- **Potřebuji licenci pro spuštění těchto příkladů?** Pro hodnocení stačí bezplatná zkušební verze; pro produkční použití je vyžadována komerční licence.

## Co znamená „čistit Word dokument“ v kontextu mail merge?
Když provádíte mail merge, Aspose.Words vloží data do merge polí a oblastí. Pokud některá pole obdrží `null` nebo prázdné řetězce, dokument může skončit s roztroušenými odstavci, prázdnými tabulkami nebo placeholder oblastmi. **Možnosti čištění** automaticky tyto artefakty odstraní a zanechají čistý, připravený k tisku dokument.

## Proč používat možnosti čištění?
- **Profesionální vzhled:** Žádné prázdné řádky ani osamělé tabulky.  
- **Menší velikost souboru:** Odstraněním nepoužitých prvků se sníží hmotnost dokumentu.  
- **Zjednodušené následné zpracování:** Čisté dokumenty se snadněji převádějí do PDF, HTML nebo jiných formátů.  
- **Úspora času:** Jednořádková nastavení nahrazují ruční post‑processing skripty.

## Požadavky
- Vývojové prostředí Java (JDK 8+).  
- Knihovna Aspose.Words pro Java – stáhněte ji z [here](https://releases.aspose.com/words/java/).  
- Základní povědomí o konceptech mail‑merge.

## Průvodce krok za krokem

### Krok 1: Jak odstranit prázdné odstavce (Java)
Nejprve ukážeme, jak eliminovat odstavce, které neobsahují žádný viditelný text. To je zvláště užitečné, když se merge pole vyhodnotí na `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Co se zde děje?**  
- `REMOVE_EMPTY_PARAGRAPHS` říká Aspose.Words, aby odstranil jakýkoli odstavec, který po sloučení zůstane prázdný.  
- Povolení `cleanupParagraphsWithPunctuationMarks` také odstraňuje odstavce, které se skládají výhradně z interpunkčních znaků (např. “?”).

### Krok 2: Jak odstranit nesloučené oblasti
Pokud má oblast mail‑merge žádná odpovídající data, můžete ji zcela zahodit.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Proč je to důležité:**  
Nevyužité oblasti často zanechávají prázdné sekce nebo osamělé nadpisy. Příznak `REMOVE_UNUSED_REGIONS` je automaticky vyčistí.

### Krok 3: Jak odstranit prázdná pole
Když pole obdrží prázdný řetězec, můžete chtít celé pole odstranit místo toho, aby zůstalo jako prázdný placeholder.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Krok 4: Jak odstranit nepoužitá pole
Pokud některá pole nejsou během sloučení vůbec použita, můžete je zcela odstranit.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Krok 5: Jak odstranit obsahující pole
Někdy se merge pole nachází uvnitř odstavce, který také chcete zahodit.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Krok 6: Jak odstranit prázdné řádky tabulky
Tabulky často končí řádky, které obsahují jen prázdná pole. Tato možnost tyto řádky ořeže.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Časté problémy a řešení
- **Odstavce se neodstraňují:** Ujistěte se, že `setCleanupParagraphsWithPunctuationMarks(true)` je voláno *po* nastavení možnosti čištění.  
- **Prázdné řádky tabulky přetrvávají:** Ověřte, že buňky tabulky skutečně obsahují prázdné řetězce (ne jen mezery).  
- **Zůstávají nepoužitá pole:** Zkontrolujte, že používáte správný enum (`REMOVE_UNUSED_FIELDS`) a že pole nejsou omylem naplněna jinde.

## Často kladené otázky

**Q: Jaký je rozdíl mezi `REMOVE_EMPTY_FIELDS` a `REMOVE_UNUSED_FIELDS`?**  
A: `REMOVE_EMPTY_FIELDS` maže pole, která během sloučení obdrží prázdný řetězec nebo `null`, zatímco `REMOVE_UNUSED_FIELDS` odstraňuje pole, která nebyla během operace sloučení vůbec referencována.

**Q: Mohu kombinovat více možností čištění?**  
A: Ano. Metoda `setCleanupOptions` přijímá bitový OR hodnot enumů, což vám umožní vyčistit odstavce, tabulky i oblasti v jediném volání.

**Q: Ovlivní povolení `cleanupParagraphsWithPunctuationMarks` běžný text?**  
A: Odstraňuje pouze odstavce, které se skládají výhradně z interpunkčních znaků (např. “?” nebo “---”). Normální věty zůstávají nedotčeny.

**Q: Lze přizpůsobit, které interpunkční znaky jsou považovány?**  
A: Aktuální API používá předdefinovanou sadu interpunkčních znaků. Pro vlastní chování byste museli po sloučení dokument dále zpracovat.

**Q: Fungují tyto možnosti čištění i při konverzi do PDF?**  
A: Rozhodně. Jakmile je Word dokument vyčištěn, můžete jej převést do PDF, HTML nebo jakéhokoli jiného podporovaného formátu, aniž by se přenesly nežádoucí prvky.

## Závěr
Nyní máte kompletní sadu nástrojů pro **čištění Word dokumentů** během mail merge s Aspose.Words pro Java. Výběrem vhodných `MailMergeCleanupOptions` můžete automaticky odstranit prázdné odstavce, prázdné řádky tabulek, nepoužitá pole a další – a získat tak elegantní, připravený dokument pro produkční nasazení.

---

**Poslední aktualizace:** 2026-01-11  
**Testováno s:** Aspose.Words pro Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}