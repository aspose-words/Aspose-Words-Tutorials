---
"description": "Tanuld meg az Aspose.Words hatékony használatát Java mezőkhöz ebben a lépésről lépésre bemutató oktatóanyagban. Hozz létre dinamikus Word dokumentumokat könnyedén."
"linktitle": "Mezők használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Mezők használata az Aspose.Words fájlban Java-ban"
"url": "/hu/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mezők használata az Aspose.Words fájlban Java-ban


Ebben a lépésről lépésre bemutatóban bemutatjuk, hogyan használhatod az Aspose.Words for Java mezőit a dokumentumok egyszerű kezeléséhez. Az Aspose.Words for Java egy hatékony API, amely lehetővé teszi a Word dokumentumok programozott kezelését, teljes kontrollt biztosítva azok tartalmi és formázási szintje felett.

## 1. Bevezetés

Az Aspose.Words for Java egy nélkülözhetetlen eszköz mindazok számára, akik Word dokumentumokkal dolgoznak Java alkalmazásokban. A mezők helyőrzők, amelyek dinamikus adatokat tárolhatnak a dokumentumban. Ez az oktatóanyag bemutatja, hogyan dolgozhat hatékonyan a mezőkkel.

## 2. A környezet beállítása

Mielőtt elkezdenéd, győződj meg róla, hogy telepítve van az Aspose.Words for Java. Letöltheted innen: [itt](https://releases.aspose.com/words/java/)Győződjön meg arról is, hogy a rendszerén telepítve van a Java és egy integrált fejlesztői környezet (IDE), például az Eclipse vagy az IntelliJ IDEA.

## 3. Word dokumentum betöltése

A Java alkalmazásodban be kell töltened a Word dokumentumot, amellyel dolgozni szeretnél. Íme egy kódrészlet a kezdéshez:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Csere `"Your Document Directory"` és `"Your Output Directory"` a megfelelő útvonalakkal.

## 4. Körlevél testreszabása

Az Aspose.Words for Java kiváló támogatást nyújt a körlevelezési műveletekhez. A körlevelezési folyamatot testreszabhatja egy körlevelezési eseménykezelő beállításával. Íme, hogyan teheti meg:

```java
// Körlevél eseménykezelő beállítása az egyéni feladatok elvégzéséhez.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// A körlevelek értékeinek kezdő és záró szóközeinek levágása.
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

Csere `"Your Output Directory"` a kívánt kimeneti útvonallal.

## Teljes forráskód
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Körlevél eseménykezelő beállítása az egyéni feladatok elvégzéséhez.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// A körlevelek értékeinek kezdő és záró szóközeinek levágása.
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
A HandleMergeField osztály forráskódja

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <összefoglaló>
        /// Ez a kezelő a dokumentumban található összes körlevelező mezőhöz meghívódik,
        /// az adatforrásban található minden rekordhoz.
        /// </összefoglaló>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Úgy döntöttünk, hogy minden logikai értéket jelölőnégyzet űrlapmezőként szeretnénk kimenetként megjeleníteni.
            if (e.getFieldValue() instanceof /*logikai érték*/Boolean)
            {
                // Vigye a "kurzort" az aktuális egyesítési mezőre.
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
            //  A megvalósítás nem szükséges.
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
        // Szúrjon be egy HA mezőbe beágyazott MERGEFIELD mezőt.
        // Mivel az IF mező utasítás hamis, a belső MERGEFIELD eredménye nem jelenik meg,
        // és a MERGEFIELD nem fog semmilyen adatot fogadni körlevelezés közben.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Továbbra is számolhatjuk a MERGEFIELD-eket a hamis utasítású IF mezőkön belül, ha ezt a jelzőt igazra állítjuk.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Az eredmény nem lesz látható a dokumentumban, mert az IF mező hamis,
        // de a belső MERGEFIELD valóban fogadott adatokat.
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getAdatbázisDir() + "Northwind.mdb";
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
        /// Ez akkor hívódik meg, amikor a körzetválasztó motor a dokumentumban a „Kép:XXX” mezőre bukkan.
        /// Lehetőséged van egy Image objektum, fájlnév vagy a képet tartalmazó stream visszaadására.
        /// </összefoglaló>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // A mező értéke egy bájt tömb, csak konvertáld, és hozz létre rajta egy streamet.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // A körzetösszetevő-motor mostantól lekéri a képet a streamből.
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
        /// A dokumentumban található összes egyesítési mezőre meghívódik.
        /// Visszaadhatunk néhány adatot a körlevelező motornak, vagy valami mást csinálhatunk a dokumentummal.
        /// Ebben az esetben módosítjuk a cellaformázást.
        /// </összefoglaló>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Válassza ki a színt attól függően, hogy a sor száma páros vagy páratlan.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Jelenleg nincs mód a teljes sor cellatulajdonságainak beállítására, ezért a sor összes celláján végig kell mennünk.
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
    /// Igaz értéket ad vissza, ha az érték páratlan; hamis értéket, ha az érték páros.
    /// </összefoglaló>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <összefoglaló>
    /// Hozz létre egy adattáblát és töltsd fel adatokkal.
    /// A való életben ezt az adattáblát egy adatbázisból kellene kitölteni.
    /// </összefoglaló>
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

Gratulálunk! Megtanultad, hogyan használhatod az Aspose.Words for Java mezőit a Word dokumentumok dinamikus kezeléséhez. Ez a hatékony API teljes kontrollt biztosít a dokumentumaid felett, így értékes eszköz a Java fejlesztők számára.

## 7. GYIK

### 1. kérdés: Hol tudom letölteni az Aspose.Words programot Java-hoz?
Az Aspose.Words Java-hoz letölthető innen: [itt](https://releases.aspose.com/words/java/).

### 2. kérdés: Hogyan szerezhetek ideiglenes licencet az Aspose.Words for Java-hoz?
Ideiglenes jogosítványt igényelhetsz [itt](https://purchase.aspose.com/temporary-license/).

### 3. kérdés: Hol kaphatok támogatást az Aspose.Words for Java-hoz?
Támogatásért látogassa meg az Aspose.Words fórumot [itt](https://forum.aspose.com/).

### 4. kérdés: Alkalmas-e az Aspose.Words for Java HTML-tartalom kezelésére Word-dokumentumokban?
Igen, az Aspose.Words for Java kiváló támogatást nyújt a HTML-tartalom kezeléséhez a Word dokumentumokban.

### 5. kérdés: Ingyenesen használhatom az Aspose.Words-öt Java-ban?
Az Aspose.Words for Java egy kereskedelmi termék, de a funkcióit ingyenes próbaverzióval is felfedezheti. [itt](https://releases.aspose.com/).

Kezdj el az Aspose.Words for Java programmal még ma, és vedd át az irányítást a Word-dokumentumaid felett úgy, mint még soha!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}