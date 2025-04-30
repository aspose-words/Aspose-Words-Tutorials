---
"description": "Odemkněte automatizaci dokumentů s Aspose.Words pro Javu. Naučte se, jak slučovat, formátovat a vkládat obrázky do dokumentů Java. Komplexní průvodce a příklady kódu pro efektivní zpracování dokumentů."
"linktitle": "Používání polí"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání polí v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání polí v Aspose.Words pro Javu

 
## Úvod do používání polí v Aspose.Words pro Javu

V tomto podrobném návodu se podíváme na to, jak používat pole v Aspose.Words pro Javu. Pole jsou výkonné zástupné symboly, které mohou dynamicky vkládat data do vašich dokumentů. Probereme různé scénáře, včetně základního slučování polí, podmíněných polí, práce s obrázky a střídavého formátování řádků. Pro každý scénář poskytneme úryvky kódu Java a vysvětlení.

## Předpoklady

Než začnete, ujistěte se, že máte nainstalovaný Aspose.Words pro Javu. Můžete si ho stáhnout z [zde](https://releases.aspose.com/words/java/).

## Základní slučování polí

Začněme jednoduchým příkladem sloučení polí. Máme šablonu dokumentu s poli hromadné korespondence a chceme je naplnit daty. Zde je kód v Javě, který toho dosáhne:

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

V tomto kódu načteme šablonu dokumentu, nastavíme pole hromadné korespondence a provedeme sloučení. `HandleMergeField` třída zpracovává specifické typy polí, jako jsou zaškrtávací políčka a obsah HTML.

## Podmíněná pole

V dokumentech můžete používat podmíněná pole. Vložme do dokumentu pole KDYŽ a naplňme ho daty:

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

Tento kód vkládá pole IF a do něj MERGEFIELD. I když je příkaz IF nepravdivý, nastavíme `setUnconditionalMergeFieldsAndRegions(true)` spočítat pole MERGEFIELDS uvnitř polí IF s nepravdivým příkazem během hromadné korespondence.

## Práce s obrázky

Obrázky můžete sloučit do dokumentů. Zde je příklad sloučení obrázků z databáze do dokumentu:

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

V tabulce můžete formátovat střídavé řádky. Postupujte takto:

```java
Document doc = new Document("AlternatingRowsTemplate.docx");
doc.getMailMerge().setFieldMergingCallback(new HandleMergeFieldAlternatingRows());
DataTable dataTable = getSuppliersDataTable();
doc.getMailMerge().executeWithRegions(dataTable);
doc.save("FormattedDocument.doc");
```

Tento kód formátuje řádky v tabulce se střídavými barvami na základě `CompanyName` pole.

## Závěr

Aspose.Words pro Javu nabízí výkonné funkce pro práci s poli v dokumentech. Můžete snadno provádět základní slučování polí, pracovat s podmíněnými poli, vkládat obrázky a formátovat tabulky. Začleňte tyto techniky do procesů automatizace dokumentů a vytvářejte dynamické a přizpůsobené dokumenty.

## Často kladené otázky

### Mohu slučovat e-maily pomocí Aspose.Words pro Javu?

Ano, v Aspose.Words pro Javu můžete slučovat poštu. Můžete vytvářet šablony dokumentů s poli hromadné korespondence a poté je naplňovat daty z různých zdrojů. Podrobnosti o tom, jak slučovat poštu, naleznete v uvedených příkladech kódu.

### Jak mohu vkládat obrázky do dokumentu pomocí Aspose.Words pro Javu?

Pro vložení obrázků do dokumentu můžete použít knihovnu Aspose.Words pro Javu. Podrobný návod, jak sloučit obrázky z databáze do dokumentu, naleznete v příkladu kódu v části „Práce s obrázky“.

### Jaký je účel podmíněných polí v Aspose.Words pro Javu?

Podmíněná pole v Aspose.Words pro Javu umožňují vytvářet dynamické dokumenty podmíněným zahrnutím obsahu na základě určitých kritérií. V uvedeném příkladu se pole IF používá k podmíněnému zahrnutí dat do dokumentu během hromadné korespondence na základě výsledku příkazu IF.

### Jak mohu formátovat střídavé řádky v tabulce pomocí Aspose.Words pro Javu?

Chcete-li formátovat střídavé řádky v tabulce, můžete použít Aspose.Words pro Javu k použití specifického formátování na řádky na základě vašich kritérií. V části „Střídavé formátování řádků“ najdete příklad, který ukazuje, jak formátovat řádky se střídavými barvami na základě `CompanyName` pole.

### Kde najdu další dokumentaci a zdroje pro Aspose.Words pro Javu?

Komplexní dokumentaci, ukázky kódu a návody k Aspose.Words pro Javu naleznete na webových stránkách Aspose: [Dokumentace k Aspose.Words pro Javu](https://reference.aspose.com/words/java/)Tento zdroj vám pomůže prozkoumat další funkce a možnosti knihovny.

### Jak mohu získat podporu nebo vyhledat pomoc s Aspose.Words pro Javu?

Pokud potřebujete pomoc, máte dotazy nebo se při používání Aspose.Words pro Javu setkáte s problémy, můžete navštívit fórum Aspose.Words, kde najdete podporu a diskuze komunity: [Fórum Aspose.Words](https://forum.aspose.com/c/words).

### Je Aspose.Words pro Javu kompatibilní s různými Java IDE?

Ano, Aspose.Words pro Javu je kompatibilní s různými integrovanými vývojovými prostředími (IDE) pro Javu, jako jsou Eclipse, IntelliJ IDEA a NetBeans. Můžete jej integrovat do svého preferovaného IDE a zefektivnit tak úlohy zpracování dokumentů.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}