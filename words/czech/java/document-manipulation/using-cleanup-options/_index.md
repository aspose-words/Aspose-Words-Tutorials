---
title: Použití možností čištění v Aspose.Words pro Java
linktitle: Použití možností čištění
second_title: Aspose.Words Java Document Processing API
description: Vylepšete srozumitelnost dokumentu pomocí možností Aspose.Words for Java Cleanup. Přečtěte si, jak odstranit prázdné odstavce, nepoužívané oblasti a další.
weight: 10
url: /cs/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití možností čištění v Aspose.Words pro Java


## Úvod do používání možností čištění v Aspose.Words pro Javu

tomto tutoriálu prozkoumáme, jak používat možnosti čištění v Aspose.Words pro Java k manipulaci a čištění dokumentů během procesu hromadné korespondence. Volby vyčištění umožňují ovládat různé aspekty čištění dokumentu, jako je odstranění prázdných odstavců, nepoužívaných oblastí a další.

## Předpoklady

 Než začneme, ujistěte se, že máte do projektu integrovanou knihovnu Aspose.Words for Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Krok 1: Odstranění prázdných odstavců

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vložte slučovací pole
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Nastavte možnosti čištění
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Povolit čištění odstavců s interpunkčními znaménky
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Proveďte hromadnou korespondenci
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Uložte dokument
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

V tomto příkladu vytvoříme nový dokument, vložíme slučovací pole a nastavíme možnosti čištění pro odstranění prázdných odstavců. Navíc umožňujeme odstranění odstavců s interpunkčními znaménky. Po provedení hromadné korespondence se dokument uloží se zadaným vyčištěním.

## Krok 2: Odebrání nesloučených oblastí

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Nastavte možnosti čištění k odstranění nepoužívaných oblastí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Proveďte hromadnou korespondenci s oblastmi
doc.getMailMerge().executeWithRegions(data);

// Uložte dokument
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

tomto příkladu otevřeme existující dokument s oblastmi hromadné korespondence, nastavíme možnosti čištění k odstranění nepoužívaných oblastí a poté provedeme hromadnou korespondenci s prázdnými daty. Tento proces automaticky odstraní nepoužívané oblasti z dokumentu.

## Krok 3: Odstranění prázdných polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavte možnosti čištění pro odstranění prázdných polí
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Proveďte hromadnou korespondenci
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložte dokument
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

V tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění pro odstranění prázdných polí a provedeme hromadnou korespondenci s daty. Po sloučení budou z dokumentu odstraněna všechna prázdná pole.

## Krok 4: Odstranění nepoužívaných polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavením možností čištění odstraníte nepoužívaná pole
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Proveďte hromadnou korespondenci
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložte dokument
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

V tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění pro odstranění nepoužívaných polí a provedeme hromadnou korespondenci s daty. Po sloučení budou z dokumentu odstraněna všechna nepoužívaná pole.

## Krok 5: Odebrání obsahujících polí

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavte možnosti čištění, abyste odstranili obsahující pole
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Proveďte hromadnou korespondenci
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložte dokument
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

tomto příkladu otevřeme dokument se slučovacími poli, nastavíme možnosti čištění pro odstranění obsahujících polí a provedeme hromadnou korespondenci s daty. Po sloučení budou z dokumentu odstraněna samotná pole.

## Krok 6: Odstranění prázdných řádků tabulky

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Nastavte možnosti čištění pro odstranění prázdných řádků tabulky
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Proveďte hromadnou korespondenci
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Uložte dokument
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

V tomto příkladu otevřeme dokument s tabulkou a slučovacími poli, nastavíme možnosti čištění pro odstranění prázdných řádků tabulky a provedeme hromadnou korespondenci s daty. Po sloučení budou z dokumentu odstraněny všechny prázdné řádky tabulky.

## Závěr

V tomto kurzu jste se naučili, jak používat možnosti čištění v Aspose.Words pro Java k manipulaci a čištění dokumentů během procesu hromadné korespondence. Tyto možnosti poskytují jemnou kontrolu nad čištěním dokumentů, což vám umožní snadno vytvářet leštěné a přizpůsobené dokumenty.

## FAQ

### Jaké jsou možnosti čištění v Aspose.Words pro Java?

Možnosti čištění v Aspose.Words for Java jsou nastavení, která vám umožňují ovládat různé aspekty čištění dokumentů během procesu hromadné korespondence. Umožňují vám odstranit nepotřebné prvky, jako jsou prázdné odstavce, nepoužívané oblasti a další, a zajistit tak, že váš konečný dokument bude dobře strukturovaný a vyleštěný.

### Jak mohu z dokumentu odstranit prázdné odstavce?

 Chcete-li z dokumentu odstranit prázdné odstavce pomocí Aspose.Words for Java, můžete nastavit`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` možnost na true. Tím se automaticky odstraní odstavce, které nemají žádný obsah, výsledkem bude čistší dokument.

###  Jaký je účel`REMOVE_UNUSED_REGIONS` cleanup option?

 The`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Tato možnost se používá k odstranění oblastí v dokumentu, které nemají žádná odpovídající data během procesu hromadné korespondence. Pomáhá udržovat váš dokument uklizený tím, že se zbavuje nepoužívaných zástupných symbolů.

### Mohu odstranit prázdné řádky tabulky z dokumentu pomocí Aspose.Words for Java?

 Ano, můžete z dokumentu odstranit prázdné řádky tabulky nastavením`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`možnost čištění na true. Tím se automaticky odstraní všechny řádky tabulky, které neobsahují data, a zajistí se tak dobře strukturovaná tabulka v dokumentu.

###  Co se stane, když nastavím`REMOVE_CONTAINING_FIELDS` option?

 Nastavení`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` možnost odebere z dokumentu během procesu hromadné korespondence celé slučovací pole, včetně odstavce, který obsahuje. To je užitečné, když chcete odstranit slučovací pole a související text.

### Jak mohu z dokumentu odstranit nepoužívaná slučovací pole?

 Chcete-li z dokumentu odstranit nepoužívaná slučovací pole, můžete nastavit`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` možnost na true. Tím se automaticky vyloučí slučovací pole, která nejsou vyplněna během hromadné korespondence, výsledkem bude čistší dokument.

###  Jaký je rozdíl mezi`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 The`REMOVE_EMPTY_FIELDS` Odebere slučovací pole, která nemají žádná data nebo jsou během procesu hromadné korespondence prázdná. Na druhou stranu,`REMOVE_UNUSED_FIELDS`Odebere slučovací pole, která nejsou během slučování naplněna daty. Volba mezi nimi závisí na tom, zda chcete odebrat pole bez obsahu nebo ta, která se nepoužívají v konkrétní operaci sloučení.

### Jak mohu povolit odstranění odstavců s interpunkčními znaménky?

 Chcete-li povolit odstranění odstavců s interpunkčními znaménky, můžete nastavit`cleanupParagraphsWithPunctuationMarks` možnost na hodnotu true a zadejte interpunkční znaménka, která mají být zvážena při čištění. To vám umožní vytvořit jemnější dokument odstraněním zbytečných odstavců obsahujících pouze interpunkci.

### Mohu upravit možnosti čištění v Aspose.Words for Java?

Ano, můžete upravit možnosti čištění podle svých konkrétních potřeb. Můžete si vybrat, které možnosti čištění použít, a nakonfigurovat je podle požadavků na čištění dokumentu, čímž zajistíte, že váš konečný dokument bude splňovat požadované standardy.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
