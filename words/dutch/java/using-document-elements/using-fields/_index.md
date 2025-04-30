---
"description": "Leer hoe u Aspose.Words effectief kunt gebruiken voor Java-velden in deze stapsgewijze tutorial. Maak eenvoudig dynamische Word-documenten."
"linktitle": "Velden gebruiken"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Velden gebruiken in Aspose.Words voor Java"
"url": "/nl/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Velden gebruiken in Aspose.Words voor Java


In deze stapsgewijze tutorial laten we je zien hoe je velden in Aspose.Words voor Java kunt gebruiken om documenten eenvoudig te bewerken. Aspose.Words voor Java is een krachtige API waarmee je programmatisch met Word-documenten kunt werken, waarbij je volledige controle hebt over de inhoud en opmaak.

## 1. Inleiding

Aspose.Words voor Java is een essentiële tool voor iedereen die met Word-documenten in Java-applicaties werkt. Velden zijn tijdelijke aanduidingen die dynamische gegevens in uw document kunnen opslaan. Deze tutorial laat u zien hoe u effectief met velden kunt werken.

## 2. Uw omgeving instellen

Voordat u begint, moet u ervoor zorgen dat Aspose.Words voor Java geïnstalleerd is. U kunt het downloaden van [hier](https://releases.aspose.com/words/java/)Zorg er ook voor dat u Java en een Integrated Development Environment (IDE) zoals Eclipse of IntelliJ IDEA op uw systeem hebt geïnstalleerd.

## 3. Een Word-document laden

In je Java-applicatie moet je het Word-document laden waarmee je wilt werken. Hier is een codefragment om je op weg te helpen:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Vervangen `"Your Document Directory"` En `"Your Output Directory"` met de juiste paden.

## 4. Mail Merge aanpassen

Aspose.Words voor Java biedt uitstekende ondersteuning voor samenvoegbewerkingen. U kunt het samenvoegproces aanpassen door een samenvoeggebeurtenishandler in te stellen. Zo doet u dat:

```java
// Stel een gebeurtenisafhandeling voor samenvoegingen in om het aangepaste werk uit te voeren.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Verwijder spaties aan het begin en einde van samenvoegingsregels.
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

## 5. Het document opslaan

Nadat u uw document heeft aangepast, kunt u het opslaan met de volgende code:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Vervangen `"Your Output Directory"` met het gewenste uitvoerpad.

## Volledige broncode
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Stel een gebeurtenisafhandeling voor samenvoegingen in om het aangepaste werk uit te voeren.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Verwijder spaties aan het begin en einde van samenvoegingsregels.
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
Broncode van klasse HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <samenvatting>
        /// Deze handler wordt aangeroepen voor elk samenvoegveld in het document,
        /// voor elk record dat in de gegevensbron wordt gevonden.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // We hebben besloten dat we alle Booleaanse waarden als selectievakjesformuliervelden willen uitvoeren.
            if (e.getFieldValue() instanceof /*Booleaanse*/Boolean)
            {
                // Verplaats de "cursor" naar het huidige samenvoegveld.
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
            //  Implementatie is niet vereist.
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
        // Voeg een MERGEFIELD in, genest in een IF-veld.
        // Omdat de IF-veldinstructie onwaar is, wordt het resultaat van het interne MERGEFIELD niet weergegeven,
        // en het MERGEFIELD ontvangt geen gegevens tijdens een samenvoeging.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // We kunnen MERGEFIELDs nog steeds tellen binnen false-statement IF-velden als we deze vlag op true zetten.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Het resultaat zal niet zichtbaar zijn in het document omdat het ALS-veld onwaar is,
        // maar het innerlijke MERGEFIELD ontving wel degelijk gegevens.
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Noordenwind.mdb";
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
            // Niets doen.
        }
        /// <samenvatting>
        /// Dit wordt aangeroepen wanneer de mail merge-engine een samenvoegveld Image:XXX in het document tegenkomt.
        /// U hebt de mogelijkheid om een Image-object, een bestandsnaam of een stream te retourneren die de afbeelding bevat.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // De veldwaarde is een byte-array. U kunt deze casten en er een stream op aanmaken.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Nu zal de samenvoegengine de afbeelding uit de stream ophalen.
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
        /// <samenvatting>
        /// Wordt aangeroepen voor elk samenvoegveld dat in het document wordt aangetroffen.
        /// We kunnen een aantal gegevens terugsturen naar de samenvoegmachine, of iets anders met het document doen.
        /// In dit geval passen we de celopmaak aan.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Selecteer de kleur afhankelijk van of het rijnummer even of oneven is.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Er is op dit moment geen mogelijkheid om celeigenschappen voor de hele rij in te stellen. We moeten dus over alle cellen in de rij itereren.
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
            // Niets doen.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <samenvatting>
    /// Retourneert true als de waarde oneven is; false als de waarde even is.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <samenvatting>
    /// Maak een DataTable en vul deze met gegevens.
    /// In de praktijk zou deze DataTable gevuld moeten worden vanuit een database.
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

## 6. Conclusie

Gefeliciteerd! Je hebt geleerd hoe je velden in Aspose.Words voor Java kunt gebruiken om Word-documenten dynamisch te bewerken. Deze krachtige API geeft je volledige controle over je documenten, wat het een waardevolle aanwinst maakt voor Java-ontwikkelaars.

## 7. Veelgestelde vragen

### V1: Waar kan ik Aspose.Words voor Java downloaden?
U kunt Aspose.Words voor Java downloaden van [hier](https://releases.aspose.com/words/java/).

### V2: Hoe kan ik een tijdelijke licentie voor Aspose.Words voor Java krijgen?
U kunt een tijdelijke vergunning verkrijgen bij [hier](https://purchase.aspose.com/temporary-license/).

### V3: Waar kan ik ondersteuning krijgen voor Aspose.Words voor Java?
Voor ondersteuning kunt u terecht op het Aspose.Words forum [hier](https://forum.aspose.com/).

### V4: Is Aspose.Words voor Java geschikt voor het verwerken van HTML-inhoud in Word-documenten?
Ja, Aspose.Words voor Java biedt uitstekende ondersteuning voor het verwerken van HTML-inhoud in Word-documenten.

### V5: Kan ik Aspose.Words voor Java gratis gebruiken?
Aspose.Words voor Java is een commercieel product, maar u kunt de functies ervan verkennen met een gratis proefversie die beschikbaar is [hier](https://releases.aspose.com/).

Ga vandaag nog aan de slag met Aspose.Words voor Java en krijg meer controle over uw Word-documenten dan ooit tevoren!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}