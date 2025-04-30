---
"description": "Vylepšete přehlednost dokumentů pomocí možností čištění v Aspose.Words pro Javu. Naučte se, jak odstranit prázdné odstavce, nepoužívané oblasti a další."
"linktitle": "Použití možností čištění"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Použití možností čištění v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití možností čištění v Aspose.Words pro Javu


## Úvod do používání možností čištění v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na to, jak pomocí možností čištění v Aspose.Words pro Javu manipulovat s dokumenty a čistit je během procesu hromadné korespondence. Možnosti čištění vám umožňují ovládat různé aspekty čištění dokumentů, jako je například odstraňování prázdných odstavců, nepoužívaných oblastí a dalších.

## Předpoklady

Než začneme, ujistěte se, že máte ve svém projektu integrovanou knihovnu Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Krok 1: Odstranění prázdných odstavců

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložit slučovací pole
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Nastavení možností čištění
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Povolit čištění odstavců pomocí interpunkčních znamének
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Spuštění hromadné korespondence
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Uložit dokument
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

V tomto příkladu vytvoříme nový dokument, vložíme slučovací pole a nastavíme možnosti čištění pro odstranění prázdných odstavců. Dále povolíme odstranění odstavců s interpunkčními znaménky. Po provedení hromadné korespondence se dokument uloží s použitým zadaným čištěním.

## Krok 2: Odebrání nesloučených oblastí

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Nastavení možností čištění pro odstranění nepoužívaných oblastí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Spuštění hromadné korespondence s oblastmi
doc.getMailMerge().executeWithRegions(data);

// Uložit dokument
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

V tomto příkladu otevřeme existující dokument se slučovanými oblastmi, nastavíme možnosti čištění tak, aby se odstranily nepoužívané oblasti, a poté spustíme hromadnou korespondenci s prázdnými daty. Tento proces automaticky odstraní nepoužívané oblasti z dokumentu.

## Krok 3: Odstranění prázdných polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavení možností čištění pro odstranění prázdných polí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Spuštění hromadné korespondence
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložit dokument
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění pro odstranění prázdných polí a provedeme hromadnou korespondenci s daty. Po sloučení budou všechna prázdná pole z dokumentu odstraněna.

## Krok 4: Odstranění nepoužívaných polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavení možností čištění pro odstranění nepoužívaných polí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Spuštění hromadné korespondence
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložit dokument
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

V tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění pro odstranění nepoužívaných polí a spustíme hromadnou korespondenci s daty. Po sloučení budou všechna nepoužívaná pole z dokumentu odstraněna.

## Krok 5: Odebrání obsahujících polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavení možností čištění pro odstranění obsahujících polí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Spuštění hromadné korespondence
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložit dokument
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

V tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění tak, aby se odstranila obsahující pole, a provedeme hromadnou korespondenci s daty. Po sloučení budou samotná pole z dokumentu odstraněna.

## Krok 6: Odstranění prázdných řádků tabulky

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavení možností čištění pro odstranění prázdných řádků tabulky
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Spuštění hromadné korespondence
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložit dokument
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

V tomto příkladu otevřeme dokument s tabulkou a slučovacími poli, nastavíme možnosti čištění pro odstranění prázdných řádků tabulky a provedeme hromadnou korespondenci s daty. Po sloučení budou z dokumentu odstraněny všechny prázdné řádky tabulky.

## Závěr

V tomto tutoriálu jste se naučili, jak používat možnosti čištění v Aspose.Words pro Javu k manipulaci a čištění dokumentů během procesu hromadné korespondence. Tyto možnosti poskytují jemnou kontrolu nad čištěním dokumentů, což vám umožňuje snadno vytvářet propracované a přizpůsobené dokumenty.

## Často kladené otázky

### Jaké jsou možnosti čištění v Aspose.Words pro Javu?

Možnosti čištění v Aspose.Words pro Javu jsou nastavení, která vám umožňují ovládat různé aspekty čištění dokumentů během procesu hromadné korespondence. Umožňují odstranit nepotřebné prvky, jako jsou prázdné odstavce, nepoužité oblasti a další, a zajistit tak, aby byl váš výsledný dokument dobře strukturovaný a vyleštěný.

### Jak mohu z dokumentu odstranit prázdné odstavce?

Chcete-li z dokumentu odstranit prázdné odstavce pomocí Aspose.Words pro Javu, můžete nastavit `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` na hodnotu true. Tím se automaticky odstraní odstavce bez obsahu, což povede k čistšímu dokumentu.

### Jaký je účel `REMOVE_UNUSED_REGIONS` možnost čištění?

Ten/Ta/To `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Možnost se používá k odstranění oblastí v dokumentu, které nemají odpovídající data během procesu hromadné korespondence. Pomáhá udržet dokument v pořádku odstraněním nepoužívaných zástupných symbolů.

### Mohu z dokumentu odstranit prázdné řádky tabulky pomocí Aspose.Words pro Javu?

Ano, prázdné řádky tabulky můžete z dokumentu odstranit nastavením `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` Nastavení možnosti čištění na hodnotu true. Tím se automaticky odstraní všechny řádky tabulky, které neobsahují data, a zajistí se tak dobře strukturovaná tabulka v dokumentu.

### Co se stane, když nastavím `REMOVE_CONTAINING_FIELDS` volba?

Nastavení `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Tato možnost odstraní z dokumentu během procesu hromadné korespondence celé slučovací pole včetně odstavce, který jej obsahuje. To je užitečné, pokud chcete odstranit slučovací pole a s nimi související text.

### Jak mohu z dokumentu odstranit nepoužívaná slučovací pole?

Chcete-li z dokumentu odstranit nepoužívaná slučovací pole, můžete nastavit `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` možnost na hodnotu true. Tím se automaticky odstraní slučovací pole, která nebudou během hromadné korespondence vyplněna, což povede k čistšímu dokumentu.

### Jaký je rozdíl mezi `REMOVE_EMPTY_FIELDS` a `REMOVE_UNUSED_FIELDS` možnosti úklidu?

Ten/Ta/To `REMOVE_EMPTY_FIELDS` Možnost odstraní slučovací pole, která neobsahují žádná data nebo jsou prázdná během procesu hromadné korespondence. Na druhou stranu, `REMOVE_UNUSED_FIELDS` Možnost odstraní slučovací pole, která během sloučení nebudou naplněna daty. Volba mezi nimi závisí na tom, zda chcete odstranit pole bez obsahu nebo ta, která se v dané operaci sloučení nepoužívají.

### Jak mohu povolit odstranění odstavců s interpunkčními znaménky?

Chcete-li povolit odstranění odstavců s interpunkčními znaménky, můžete nastavit `cleanupParagraphsWithPunctuationMarks` na hodnotu true a určete interpunkční znaménka, která se mají brát v úvahu při čištění. To vám umožní vytvořit propracovanější dokument odstraněním nepotřebných odstavců obsahujících pouze interpunkci.

### Mohu si přizpůsobit možnosti čištění v Aspose.Words pro Javu?

Ano, možnosti čištění si můžete přizpůsobit podle svých specifických potřeb. Můžete si vybrat, které možnosti čištění chcete použít, a nakonfigurovat je podle požadavků na čištění dokumentu, čímž zajistíte, že váš výsledný dokument splňuje požadované standardy.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}