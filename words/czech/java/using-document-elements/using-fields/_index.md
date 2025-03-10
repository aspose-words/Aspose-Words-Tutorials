---
title: Použití polí v Aspose.Words pro Java
linktitle: Použití polí
second_title: Aspose.Words Java Document Processing API
description: Naučte se efektivně používat pole Aspose.Words pro Java v tomto podrobném tutoriálu. Snadno vytvářejte dynamické dokumenty aplikace Word.
weight: 11
url: /cs/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití polí v Aspose.Words pro Java


tomto tutoriálu krok za krokem vás provedeme tím, jak používat pole v Aspose.Words pro Java k snadné manipulaci s dokumenty. Aspose.Words for Java je výkonné rozhraní API, které vám umožňuje pracovat s dokumenty Wordu programově a poskytuje vám plnou kontrolu nad jejich obsahem a formátováním.

## 1. Úvod

Aspose.Words for Java je základním nástrojem pro každého, kdo pracuje s dokumenty Wordu v aplikacích Java. Pole jsou zástupné symboly, které mohou ve vašem dokumentu ukládat dynamická data. Tento tutoriál vám ukáže, jak efektivně pracovat s poli.

## 2. Nastavení vašeho prostředí

 Než začnete, ujistěte se, že máte nainstalovaný Aspose.Words for Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/). Také se ujistěte, že máte v systému nainstalovanou Javu a integrované vývojové prostředí (IDE), jako je Eclipse nebo IntelliJ IDEA.

## 3. Načtení dokumentu aplikace Word

Do vaší Java aplikace musíte načíst dokument Word, se kterým chcete pracovat. Zde je úryvek kódu, který vám pomůže začít:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Nahradit`"Your Document Directory"` a`"Your Output Directory"` s příslušnými cestami.

## 4. Přizpůsobení hromadné korespondence

Aspose.Words for Java poskytuje vynikající podporu pro operace hromadné korespondence. Proces hromadné korespondence můžete přizpůsobit nastavením obslužné rutiny události hromadné korespondence. Jak na to:

```java
// Nastavit obslužnou rutinu události hromadné korespondence k provedení vlastní práce.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Ořízněte koncové a úvodní prázdné hodnoty hromadné korespondence.
doc.getMailMerge().setTrimWhitespaces(false);

String[] fieldNames = {
    "RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
    "Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};

Object[] fieldValues = {
    "Josh", "Jenny", "123456789", "", "Hello",
    "<b>HTML Body Test message 1</b>", true, false, true
};

doc.getMailMerge().execute(fieldNames, fieldValues);
```

## 5. Uložení dokumentu

Po přizpůsobení dokumentu jej můžete uložit pomocí následujícího kódu:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Nahradit`"Your Output Directory"` s požadovanou výstupní cestou.

## Kompletní zdrojový kód
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Nastavit obslužnou rutinu události hromadné korespondence k provedení vlastní práce.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Ořízněte koncové a úvodní prázdné hodnoty hromadné korespondence.
doc.getMailMerge().setTrimWhitespaces(false);
String[] fieldNames = {
	"RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
	"Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};
Object[] fieldValues = {
	"Josh", "Jenny", "123456789", "", "Hello",
	"<b>HTML Body Test message 1</b>", true, false, true
};
doc.getMailMerge().execute(fieldNames, fieldValues);
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```
Zdrojový kód třídy HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <souhrn>
        /// Tento obslužný program je volán pro každé pole hromadné korespondence nalezené v dokumentu,
        /// pro každý záznam nalezený ve zdroji dat.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Rozhodli jsme se, že chceme, aby všechny booleovské hodnoty byly na výstupu jako zaškrtávací pole formuláře.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Přesuňte "kurzor" na aktuální slučovací pole.
                mBuilder.moveToMergeField(e.getFieldName());
                String checkBoxName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                mBuilder.insertCheckBox(checkBoxName, (Boolean) e.getFieldValue(), 0);
                return;
            }
            switch (e.getFieldName())
            {
                case "Body":
                    mBuilder.moveToMergeField(e.getFieldName());
                    mBuilder.insertHtml((String) e.getFieldValue());
                    break;
                case "Subject":
                {
                    mBuilder.moveToMergeField(e.getFieldName());
                    String textInputName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                    mBuilder.insertTextInput(textInputName, TextFormFieldType.REGULAR, "", (String) e.getFieldValue(), 0);
                    break;
                }
            }
        }
        public void imageFieldMerging(ImageFieldMergingArgs args)
        {
            args.setImageFileName("Image.png");
            args.getImageWidth().setValue(200.0);
            args.setImageHeight(new MergeFieldImageDimension(200.0, MergeFieldImageDimensionUnit.PERCENT));
        }
        private DocumentBuilder mBuilder;
    }
    @Test
    public void mailMergeImageField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("{{#foreach example}}");
        builder.writeln("{{Image(126pt;126pt):stempel}}");
        builder.writeln("{{/foreach example}}");
        doc.getMailMerge().setUseNonMergeFields(true);
        doc.getMailMerge().setTrimWhitespaces(true);
        doc.getMailMerge().setUseWholeParagraphAsRegion(false);
        doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS
                | MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS
                | MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS
                | MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);
        doc.getMailMerge().setFieldMergingCallback(new ImageFieldMergingHandler());
        doc.getMailMerge().executeWithRegions(new DataSourceRoot());
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageField.docx");
    }
    private static class ImageFieldMergingHandler implements IFieldMergingCallback
    {
        public void fieldMerging(FieldMergingArgs args)
        {
            // Implementace není nutná.
        }
        public void imageFieldMerging(ImageFieldMergingArgs args) throws Exception
        {
            Shape shape = new Shape(args.getDocument(), ShapeType.IMAGE);
            {
                shape.setWidth(126.0); shape.setHeight(126.0); shape.setWrapType(WrapType.SQUARE);
            }
            shape.getImageData().setImage("Your Directory Path" + "Mail merge image.png");
            args.setShape(shape);
        }
    }
    public static class DataSourceRoot implements IMailMergeDataSourceRoot
    {
        public IMailMergeDataSource getDataSource(String s)
        {
            return new DataSource();
        }
        private static class DataSource implements IMailMergeDataSource
        {
            private boolean next = true;
            private String tableName()
            {
                return "example";
            }
            @Override
            public String getTableName() {
                return tableName();
            }
            public boolean moveNext()
            {
                boolean result = next;
                next = false;
                return result;
            }
            public IMailMergeDataSource getChildDataSource(String s)
            {
                return null;
            }
            public boolean getValue(String fieldName, Ref<Object> fieldValue)
            {
                fieldValue.set(null);
                return false;
            }
        }
    }
    @Test
    public void mailMergeAndConditionalField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vložte MERGEFIELD vnořené do pole IF.
        // Protože příkaz pole IF je nepravdivý, výsledek vnitřního MERGEFIELD se nezobrazí,
        // MERGEFIELD neobdrží žádná data během hromadné korespondence.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Pokud nastavíme tento příznak na hodnotu true, můžeme stále počítat MERGEFIELD v polích IF s nepravdivým příkazem.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Výsledek nebude v dokumentu viditelný, protože pole IF je nepravdivé,
        // ale vnitřní MERGEFIELD skutečně přijímalo data.
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Northwind.mdb";
        Connection connection = DriverManager.getConnection(connString, "Admin", "");
        Statement statement = connection.createStatement();
        ResultSet resultSet = statement.executeQuery("SELECT * FROM Employees");
        DataTable dataTable = new DataTable(resultSet, "Employees");
        IDataReader dataReader = new DataTableReader(dataTable);
        doc.getMailMerge().executeWithRegions(dataReader, "Employees");
        connection.close();
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageFromBlob.docx");
    }
    public static class HandleMergeImageFieldFromBlob implements IFieldMergingCallback
    {
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs args)
        {
            // Nedělejte nic.
        }
        /// <souhrn>
        /// Volá se, když stroj hromadné korespondence narazí v dokumentu na slučovací pole Obrázek:XXX.
        /// Máte možnost vrátit objekt Image, název souboru nebo proud, který obrázek obsahuje.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Hodnota pole je bajtové pole, stačí jej přetypovat a vytvořit na něm stream.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Nyní modul hromadné korespondence načte obrázek ze streamu.
            e.setImageStream(imageStream);
        }
    }
    @Test
    public void handleMailMergeSwitches() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Field sample - MERGEFIELD.docx");
        doc.getMailMerge().setFieldMergingCallback(new MailMergeSwitches());
        final String HTML = "<html>\r\n                    <h1>Hello world!</h1>\r\n            </html>";
        doc.getMailMerge().execute(new String[] { "htmlField1" }, new Object[] { HTML });
        doc.save("Your Directory Path" + "WorkingWithFields.HandleMailMergeSwitches.docx");
    }
    public static class MailMergeSwitches implements IFieldMergingCallback
    {
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (e.getFieldName().startsWith("HTML"))
            {
                if (e.getField().getFieldCode().contains("\\b"))
                {
                    FieldMergeField field = e.getField();
                    DocumentBuilder builder = new DocumentBuilder(e.getDocument());
                    builder.moveToMergeField(e.getDocumentFieldName(), true, false);
                    builder.write(field.getTextBefore());
                    builder.insertHtml(e.getFieldValue().toString());
                    e.setText("");
                }
            }
        }
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
        }
    }
    @Test
    public void alternatingRows() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeFieldAlternatingRows());
        DataTable dataTable = getSuppliersDataTable();
        doc.getMailMerge().executeWithRegions(dataTable);
        doc.save("Your Directory Path" + "WorkingWithFields.AlternatingRows.doc");
    }
    private static class HandleMergeFieldAlternatingRows implements IFieldMergingCallback
    {
        /// <souhrn>
        /// Volá se pro každé slučovací pole nalezené v dokumentu.
        /// Můžeme buď vrátit některá data do modulu hromadné korespondence, nebo s dokumentem udělat něco jiného.
        /// V tomto případě upravíme formátování buněk.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Vyberte barvu podle toho, zda je číslo řádku sudé nebo liché.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // tuto chvíli neexistuje způsob, jak nastavit vlastnosti buňky pro celý řádek, takže musíme iterovat přes všechny buňky v řádku.
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // Nedělejte nic.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <souhrn>
    /// Vrátí true, pokud je hodnota lichá; false, pokud je hodnota sudá.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <souhrn>
    /// Vytvořte DataTable a naplňte ji daty.
    /// V reálném životě by tato DataTable měla být vyplněna z databáze.
    /// </summary>
    private DataTable getSuppliersDataTable()
    {
        DataTable dataTable = new DataTable("Suppliers");
        dataTable.getColumns().add("CompanyName");
        dataTable.getColumns().add("ContactName");
        for (int i = 0; i < 10; i++)
        {
            DataRow datarow = dataTable.newRow();
            dataTable.getRows().add(datarow);
            datarow.set(0, "Company " + i);
            datarow.set(1, "Contact " + i);
        }
        return dataTable;
	}
}
```

## 6. Závěr

Gratuluji! Naučili jste se používat pole v Aspose.Words pro Java k dynamické manipulaci s dokumenty Wordu. Toto výkonné rozhraní API vám poskytuje úplnou kontrolu nad vašimi dokumenty, což z něj činí cenný přínos pro vývojáře v jazyce Java.

## 7. Nejčastější dotazy

### Q1: Kde si mohu stáhnout Aspose.Words for Java?
 Aspose.Words for Java si můžete stáhnout z[zde](https://releases.aspose.com/words/java/).

### Q2: Jak mohu získat dočasnou licenci pro Aspose.Words for Java?
 Dočasnou licenci můžete získat od[zde](https://purchase.aspose.com/temporary-license/).

### Q3: Kde mohu získat podporu pro Aspose.Words pro Java?
 Pro podporu můžete navštívit fórum Aspose.Words[zde](https://forum.aspose.com/).

### Q4: Je Aspose.Words for Java vhodný pro zpracování obsahu HTML v dokumentech aplikace Word?
Ano, Aspose.Words for Java poskytuje vynikající podporu pro práci s obsahem HTML v dokumentech aplikace Word.

### Q5: Mohu používat Aspose.Words for Java zdarma?
 Aspose.Words for Java je komerční produkt, ale jeho funkce můžete prozkoumat pomocí bezplatné zkušební verze[zde](https://releases.aspose.com/).

Začněte s Aspose.Words pro Java ještě dnes a převezměte kontrolu nad svými dokumenty Wordu jako nikdy předtím!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
