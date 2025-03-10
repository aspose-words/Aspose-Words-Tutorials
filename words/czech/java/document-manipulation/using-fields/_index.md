---
title: Použití polí v Aspose.Words pro Java
linktitle: Použití polí
second_title: Aspose.Words Java Document Processing API
description: Odemkněte automatizaci dokumentů pomocí Aspose.Words pro Java. Naučte se slučovat, formátovat a vkládat obrázky do dokumentů Java. Komplexní průvodce a příklady kódu pro efektivní zpracování dokumentů.
weight: 11
url: /cs/java/document-manipulation/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití polí v Aspose.Words pro Java

 
## Úvod do používání polí v Aspose.Words pro Javu

tomto podrobném průvodci prozkoumáme, jak používat pole v Aspose.Words pro Java. Pole jsou výkonné zástupné symboly, které mohou dynamicky vkládat data do vašich dokumentů. Probereme různé scénáře, včetně základního slučování polí, podmíněných polí, práce s obrázky a střídavého formátování řádků. Pro každý scénář poskytneme úryvky kódu Java a vysvětlení.

## Předpoklady

 Než začnete, ujistěte se, že máte nainstalovaný Aspose.Words for Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Základní slučování polí

Začněme jednoduchým příkladem sloučení polí. Máme šablonu dokumentu s poli hromadné korespondence a chceme je naplnit daty. Zde je kód Java, jak toho dosáhnout:

```java
Document doc = new Document("Mail merge template.docx");
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
String[] fieldNames = {
    "RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
    "Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};
Object[] fieldValues = {
    "Josh", "Jenny", "123456789", "", "Hello",
    "<b>HTML Body Test message 1</b>", true, false, true
};
doc.getMailMerge().execute(fieldNames, fieldValues);
doc.save("MergedDocument.docx");
```

 V tomto kódu načteme šablonu dokumentu, nastavíme pole hromadné korespondence a provedeme sloučení. The`HandleMergeField` třída zpracovává specifické typy polí, jako jsou zaškrtávací políčka a obsah těla HTML.

## Podmíněná pole

Ve svých dokumentech můžete použít podmíněná pole. Vložíme pole IF do našeho dokumentu a naplníme jej daty:

```java
Document doc = new Document("ConditionalFieldTemplate.docx");
FieldIf fieldIf = (FieldIf) doc.getBuilder().insertField(" IF 1 = 2 ");
fieldIf.setResultIfFalse(true);
FieldMergeField mergeField = (FieldMergeField) doc.getBuilder().insertField(" MERGEFIELD FullName ");
DataTable dataTable = new DataTable();
dataTable.getColumns().add("FullName");
dataTable.getRows().add("James Bond");
doc.getMailMerge().execute(dataTable);
```

 Tento kód vloží pole IF a MERGEFIELD do něj. I když je příkaz IF nepravdivý, nastavíme`setUnconditionalMergeFieldsAndRegions(true)` k počítání MERGEFIELD uvnitř polí IF s falešným příkazem během hromadné korespondence.

## Práce s obrázky

Obrázky můžete sloučit do svých dokumentů. Zde je příklad sloučení obrázků z databáze do dokumentu:

```java
Document doc = new Document("ImageMergeTemplate.docx");
doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Northwind.mdb";
Connection connection = DriverManager.getConnection(connString, "Admin", "");
Statement statement = connection.createStatement();
ResultSet resultSet = statement.executeQuery("SELECT * FROM Employees");
DataTable dataTable = new DataTable(resultSet, "Employees");
doc.getMailMerge().executeWithRegions(dataTable, "Employees");
connection.close();
doc.save("MergedDocumentWithImages.docx");
```

V tomto kódu načteme šablonu dokumentu s poli pro sloučení obrázků a naplníme je obrázky z databáze.

## Střídavé formátování řádků

V tabulce můžete formátovat střídající se řádky. Jak na to:

```java
Document doc = new Document("AlternatingRowsTemplate.docx");
doc.getMailMerge().setFieldMergingCallback(new HandleMergeFieldAlternatingRows());
DataTable dataTable = getSuppliersDataTable();
doc.getMailMerge().executeWithRegions(dataTable);
doc.save("FormattedDocument.doc");
```

 Tento kód formátuje řádky v tabulce se střídajícími se barvami na základě`CompanyName` pole.

## Závěr

Aspose.Words for Java poskytuje výkonné funkce pro práci s poli ve vašich dokumentech. Snadno můžete provádět základní slučování polí, pracovat s podmíněnými poli, vkládat obrázky a formátovat tabulky. Zahrňte tyto techniky do svých procesů automatizace dokumentů a vytvořte dynamické a přizpůsobené dokumenty.

## FAQ

### Mohu provést sloučení pošty s Aspose.Words pro Java?

Ano, hromadnou korespondenci můžete provádět v Aspose.Words for Java. Můžete vytvořit šablony dokumentů s poli hromadné korespondence a poté je naplnit daty z různých zdrojů. Podrobnosti o provádění hromadné korespondence naleznete v poskytnutých příkladech kódu.

### Jak mohu vložit obrázky do dokumentu pomocí Aspose.Words for Java?

Pro vložení obrázků do dokumentu můžete použít knihovnu Aspose.Words for Java. Podívejte se na příklad kódu v části "Práce s obrázky", kde najdete podrobný návod, jak sloučit obrázky z databáze do dokumentu.

### Jaký je účel podmíněných polí v Aspose.Words pro Java?

Podmíněná pole v Aspose.Words pro Java umožňují vytvářet dynamické dokumenty podmíněným zahrnutím obsahu na základě určitých kritérií. V uvedeném příkladu se pole IF používá k podmíněnému zahrnutí dat do dokumentu během hromadné korespondence na základě výsledku příkazu IF.

### Jak mohu formátovat střídající se řádky v tabulce pomocí Aspose.Words for Java?

 Chcete-li formátovat střídající se řádky v tabulce, můžete použít Aspose.Words for Java k použití specifického formátování na řádky na základě vašich kritérií. V části "Střídavé formátování řádků" najdete příklad, který ukazuje, jak formátovat řádky se střídajícími se barvami na základě`CompanyName` pole.

### Kde najdu další dokumentaci a zdroje pro Aspose.Words for Java?

 Komplexní dokumentaci, ukázky kódu a výukové programy pro Aspose.Words for Java naleznete na webu Aspose:[Aspose.Words pro dokumentaci Java](https://reference.aspose.com/words/java/)Tento zdroj vám pomůže prozkoumat další funkce a funkce knihovny.

### Jak mohu získat podporu nebo vyhledat pomoc s Aspose.Words for Java?

 Pokud potřebujete pomoc, máte otázky nebo se při používání Aspose.Words pro Java setkáte s problémy, můžete navštívit fórum Aspose.Words, kde najdete podporu komunity a diskuse:[Fórum Aspose.Words](https://forum.aspose.com/c/words).

### Je Aspose.Words for Java kompatibilní s různými Java IDE?

Ano, Aspose.Words for Java je kompatibilní s různými Java Integrated Development Environments (IDE), jako jsou Eclipse, IntelliJ IDEA a NetBeans. Můžete jej integrovat do svého preferovaného IDE a zjednodušit tak své úlohy zpracování dokumentů.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
