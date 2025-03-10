---
title: Mezők használata az Aspose.Words for Java-ban
linktitle: Mezők használata
second_title: Aspose.Words Java Document Processing API
description: Tanulja meg az Aspose.Words for Java mezők hatékony használatát ebben a lépésről lépésre mutató oktatóanyagban. Dinamikus Word dokumentumokat hozhat létre könnyedén.
weight: 11
url: /hu/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mezők használata az Aspose.Words for Java-ban


Ebben a lépésenkénti oktatóanyagban bemutatjuk, hogyan használhatja az Aspose.Words for Java mezőit a dokumentumok egyszerű kezeléséhez. Az Aspose.Words for Java egy hatékony API, amely lehetővé teszi a Word-dokumentumok programozott kezelését, így teljes ellenőrzést biztosít a tartalom és a formázás felett.

## 1. Bevezetés

Az Aspose.Words for Java alapvető eszköz azoknak, akik Word dokumentumokkal foglalkoznak Java alkalmazásokban. A mezők olyan helyőrzők, amelyek dinamikus adatokat tárolhatnak a dokumentumban. Ez az oktatóanyag megmutatja, hogyan kell hatékonyan dolgozni a mezőkkel.

## 2. A környezet beállítása

 Mielőtt elkezdené, győződjön meg arról, hogy az Aspose.Words for Java telepítve van. Letöltheti innen[itt](https://releases.aspose.com/words/java/). Győződjön meg arról is, hogy Java és integrált fejlesztői környezet (IDE), például az Eclipse vagy az IntelliJ IDEA telepítve van a rendszerére.

## 3. Word dokumentum betöltése

A Java alkalmazásban be kell töltenie azt a Word dokumentumot, amellyel dolgozni szeretne. Íme egy kódrészlet a kezdéshez:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Cserélje ki`"Your Document Directory"` és`"Your Output Directory"` a megfelelő utakkal.

## 4. A körlevél testreszabása

Az Aspose.Words for Java kiváló támogatást nyújt a körlevél-műveletekhez. A körlevél-eseménykezelő beállításával testreszabhatja a körlevél-összevonási folyamatot. Íme, hogyan kell csinálni:

```java
// Az egyéni munka elvégzéséhez állítsa be a körlevél-eseménykezelőt.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Vágja le a záró és kezdő szóközöket a körlevél-összevont értékeket.
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

## 5. A dokumentum mentése

A dokumentum testreszabása után a következő kóddal mentheti el:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Cserélje ki`"Your Output Directory"` a kívánt kimeneti útvonallal.

## Teljes forráskód
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Az egyéni munka elvégzéséhez állítsa be a körlevél-eseménykezelőt.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Vágja le a záró és kezdő szóközöket a körlevél-összevont értékeket.
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
A Class HandleMergeField forráskódja

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <összefoglaló>
        /// Ez a kezelő minden, a dokumentumban található körlevél mezőhöz meghívásra kerül,
        /// az adatforrásban talált minden rekordra.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Úgy döntöttünk, hogy az összes logikai értéket jelölőnégyzet űrlapmezőként akarjuk kiadni.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Vigye a „kurzort” az aktuális egyesítési mezőre.
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
            // A megvalósítás nem szükséges.
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
        // Szúrjon be egy MERGEFIELD értéket egy IF mezőbe.
        // Mivel az IF mező utasítása hamis, a belső MERGEFIELD eredménye nem jelenik meg,
        //és a MERGEFIELD nem kap semmilyen adatot a körlevél-összevonás során.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // A hamis állítású IF mezőkben továbbra is megszámolhatjuk a MERGEFIELD-eket, ha ezt a jelzőt igazra állítjuk.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Az eredmény nem lesz látható a dokumentumban, mert az IF mező hamis,
        // de a belső MERGEFIELD valóban kapott adatokat.
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
            // Ne csinálj semmit.
        }
        /// <összefoglaló>
        /// Ezt akkor hívják meg, ha a körlevél-motor az Image:XXX egyesítési mezővel találkozik a dokumentumban.
        /// Lehetősége van visszaadni egy Image objektumot, fájlnevet vagy olyan adatfolyamot, amely tartalmazza a képet.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // A mező értéke egy bájttömb, csak öntsd át, és hozz létre egy adatfolyamot rajta.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Most a körlevél-motor lekéri a képet az adatfolyamból.
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
        /// <összefoglaló>
        /// A dokumentumban talált összes egyesítési mező esetén meghívva.
        /// Valamilyen adatot visszaadhatunk a körlevél-motorba, vagy tehetünk mást a dokumentummal.
        /// Ebben az esetben módosítjuk a cella formázását.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Válassza ki a színt attól függően, hogy a sorszám páros vagy páratlan.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //Jelenleg nincs mód az egész sor cellatulajdonságainak megadására, ezért a sor összes celláján át kell iterálni.
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
            // Ne csinálj semmit.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <összefoglaló>
    /// Igazat ad vissza, ha az érték páratlan; false, ha az érték páros.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <összefoglaló>
    /// Hozzon létre DataTable-t és töltse fel adatokkal.
    /// A való életben ezt a DataTable-t adatbázisból kell kitölteni.
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

## 6. Következtetés

Gratulálok! Megtanulta az Aspose.Words for Java mezőinek használatát a Word dokumentumok dinamikus kezeléséhez. Ez a hatékony API teljes ellenőrzést biztosít a dokumentumok felett, így értékes eszköz a Java-fejlesztők számára.

## 7. GYIK

### 1. kérdés: Honnan tölthetem le az Aspose.Words for Java programot?
 Az Aspose.Words for Java letölthető innen:[itt](https://releases.aspose.com/words/java/).

### 2. kérdés: Hogyan szerezhetek ideiglenes licencet az Aspose.Words for Java számára?
 Ideiglenes jogosítványt szerezhet be[itt](https://purchase.aspose.com/temporary-license/).

### 3. kérdés: Hol kaphatok támogatást az Aspose.Words for Java-hoz?
 Támogatásért keresse fel az Aspose.Words fórumot[itt](https://forum.aspose.com/).

### 4. kérdés: Az Aspose.Words for Java alkalmas Word dokumentumok HTML-tartalmának kezelésére?
Igen, az Aspose.Words for Java kiváló támogatást nyújt a Word dokumentumok HTML-tartalmának kezelésére.

### 5. kérdés: Használhatom ingyenesen az Aspose.Words for Java programot?
 Az Aspose.Words for Java kereskedelmi termék, de ingyenes próbaverzióval felfedezheti a funkcióit[itt](https://releases.aspose.com/).

Kezdje el az Aspose.Words for Java alkalmazást még ma, és vegye át az irányítást Word-dokumentumai felett, mint még soha!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
