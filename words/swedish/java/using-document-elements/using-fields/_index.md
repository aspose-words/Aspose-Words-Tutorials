---
"description": "Lär dig att använda Aspose.Words för Java-fält effektivt i den här steg-för-steg-handledningen. Skapa dynamiska Word-dokument med lätthet."
"linktitle": "Använda fält"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda fält i Aspose.Words för Java"
"url": "/sv/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda fält i Aspose.Words för Java


I den här steg-för-steg-handledningen vägleder vi dig i hur du använder fält i Aspose.Words för Java för att enkelt manipulera dokument. Aspose.Words för Java är ett kraftfullt API som låter dig arbeta med Word-dokument programmatiskt, vilket ger dig full kontroll över deras innehåll och formatering.

## 1. Introduktion

Aspose.Words för Java är ett viktigt verktyg för alla som arbetar med Word-dokument i Java-applikationer. Fält är platshållare som kan lagra dynamisk data i ditt dokument. Den här handledningen visar dig hur du arbetar med fält effektivt.

## 2. Konfigurera din miljö

Innan du börjar, se till att du har Aspose.Words för Java installerat. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/)Se också till att du har Java och en integrerad utvecklingsmiljö (IDE) som Eclipse eller IntelliJ IDEA installerade på ditt system.

## 3. Ladda ett Word-dokument

I ditt Java-program behöver du ladda Word-dokumentet du vill arbeta med. Här är ett kodavsnitt för att komma igång:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Ersätta `"Your Document Directory"` och `"Your Output Directory"` med lämpliga vägar.

## 4. Anpassa dokumentkoppling

Aspose.Words för Java ger utmärkt stöd för dokumentkopplingsåtgärder. Du kan anpassa dokumentkopplingsprocessen genom att konfigurera en händelsehanterare för dokumentkoppling. Så här gör du:

```java
// Konfigurera händelsehanteraren för dokumentkoppling för att utföra det anpassade arbetet.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Trimma efterföljande och inledande blanksteg i dokumentkopplingar.
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

## 5. Spara dokumentet

När du har anpassat ditt dokument kan du spara det med följande kod:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Ersätta `"Your Output Directory"` med önskad utmatningsväg.

## Komplett källkod
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Konfigurera händelsehanteraren för dokumentkoppling för att utföra det anpassade arbetet.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Trimma efterföljande och inledande blanksteg i dokumentkopplingar.
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
Källkod för klassen HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <sammanfattning>
        /// Denna hanterare anropas för varje fält för koppling av dokument som finns i dokumentet,
        /// för varje post som hittas i datakällan.
        /// </sammanfattning>
        public void /*iFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Vi bestämde oss för att alla booleska värden ska visas som kryssrutefält i formuläret.
            if (e.getFieldValue() instanceof /*boolesk*/Boolean)
            {
                // Flytta "markören" till det aktuella kopplingsfältet.
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
        builder.writeln("
{{#foreach example}}");
        builder.writeln("
{{Image(126pt;126pt):stempel}}");
        builder.writeln("
{{/foreach example}}");
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
            //  Implementering krävs inte.
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
        // Infoga ett MERGEFIELD kapslat inuti ett OM-fält.
        // Eftersom IF-fältsatsen är falsk kommer resultatet av det inre MERGEFIELD inte att visas,
        // och MERGEFIELD kommer inte att ta emot några data under en dokumentkoppling.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Vi kan fortfarande räkna MERGEFIELDs inuti OM-fält med falskt påstående om vi ställer in den här flaggan till sann.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Resultatet kommer inte att synas i dokumentet eftersom OM-fältet är falskt,
        // men det inre MERGEFIELD tog faktiskt emot data.
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
        public void /*iFieldMergingCallback.*/fieldMerging(FieldMergingArgs args)
        {
            // Gör ingenting.
        }
        /// <sammanfattning>
        //Detta anropas när kopplingsfunktionen stöter på kopplingsfältet Image:XXX i dokumentet.
        /// Du har möjlighet att returnera ett bildobjekt, filnamn eller en ström som innehåller bilden.
        /// </sammanfattning>
        public void /*iFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Fältvärdet är en byte-array, bara casta den och skapa en ström på den.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Nu kommer koppladningsmotorn att hämta bilden från strömmen.
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
        public void /*iFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
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
        public void /*iFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
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
        /// <sammanfattning>
        /// Anropades för varje kopplingsfält som påträffas i dokumentet.
        /// Vi kan antingen returnera data till kopplingssystemet eller göra något annat med dokumentet.
        /// I det här fallet ändrar vi cellformateringen.
        /// </sammanfattning>
        public void /*iFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Välj färg beroende på om radnumret är jämnt eller udda.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Det finns inget sätt att ange cellegenskaper för hela raden för närvarande, så vi måste iterera över alla celler i raden.
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*iFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // Gör ingenting.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <sammanfattning>
    /// Returnerar sant om värdet är udda; falskt om värdet är jämnt.
    /// </sammanfattning>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <sammanfattning>
    /// Skapa en datatabell och fyll den med data.
    /// I verkligheten borde denna datatabell fyllas i från en databas.
    /// </sammanfattning>
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

## 6. Slutsats

Grattis! Du har lärt dig hur du använder fält i Aspose.Words för Java för att dynamiskt manipulera Word-dokument. Detta kraftfulla API ger dig fullständig kontroll över dina dokument, vilket gör det till en värdefull tillgång för Java-utvecklare.

## 7. Vanliga frågor

### F1: Var kan jag ladda ner Aspose.Words för Java?
Du kan ladda ner Aspose.Words för Java från [här](https://releases.aspose.com/words/java/).

### F2: Hur kan jag få en tillfällig licens för Aspose.Words för Java?
Du kan få en tillfällig licens från [här](https://purchase.aspose.com/temporary-license/).

### F3: Var kan jag få support för Aspose.Words för Java?
För support kan du besöka Aspose.Words-forumet. [här](https://forum.aspose.com/).

### F4: Är Aspose.Words för Java lämpligt för att hantera HTML-innehåll i Word-dokument?
Ja, Aspose.Words för Java erbjuder utmärkt stöd för hantering av HTML-innehåll i Word-dokument.

### F5: Kan jag använda Aspose.Words för Java gratis?
Aspose.Words för Java är en kommersiell produkt, men du kan utforska dess funktioner med en gratis provperiod. [här](https://releases.aspose.com/).

Kom igång med Aspose.Words för Java idag och ta kontroll över dina Word-dokument som aldrig förr!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}