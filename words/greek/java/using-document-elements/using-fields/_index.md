---
title: Χρήση πεδίων στο Aspose.Words για Java
linktitle: Χρήση Πεδίων
second_title: Aspose.Words Java Document Processing API
description: Μάθετε να χρησιμοποιείτε αποτελεσματικά τα πεδία Aspose.Words για Java σε αυτό το βήμα προς βήμα σεμινάριο. Δημιουργήστε δυναμικά έγγραφα Word με ευκολία.
weight: 11
url: /el/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση πεδίων στο Aspose.Words για Java


Σε αυτό το βήμα προς βήμα σεμινάριο, θα σας καθοδηγήσουμε πώς να χρησιμοποιείτε πεδία στο Aspose.Words για Java για να χειρίζεστε έγγραφα με ευκολία. Το Aspose.Words για Java είναι ένα ισχυρό API που σας επιτρέπει να εργάζεστε με έγγραφα του Word μέσω προγραμματισμού, δίνοντάς σας πλήρη έλεγχο του περιεχομένου και της μορφοποίησής τους.

## 1. Εισαγωγή

Το Aspose.Words για Java είναι ένα απαραίτητο εργαλείο για όσους ασχολούνται με έγγραφα του Word σε εφαρμογές Java. Τα πεδία είναι σύμβολα κράτησης θέσης που μπορούν να αποθηκεύσουν δυναμικά δεδομένα στο έγγραφό σας. Αυτό το σεμινάριο θα σας δείξει πώς να εργάζεστε αποτελεσματικά με πεδία.

## 2. Ρύθμιση του περιβάλλοντος σας

 Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε εγκαταστήσει το Aspose.Words για Java. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/). Επίσης, βεβαιωθείτε ότι έχετε εγκαταστήσει στο σύστημά σας Java και ένα ολοκληρωμένο περιβάλλον ανάπτυξης (IDE) όπως το Eclipse ή το IntelliJ IDEA.

## 3. Φόρτωση εγγράφου Word

Στην εφαρμογή Java, πρέπει να φορτώσετε το έγγραφο του Word με το οποίο θέλετε να εργαστείτε. Ακολουθεί ένα απόσπασμα κώδικα για να ξεκινήσετε:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Αντικαθιστώ`"Your Document Directory"` και`"Your Output Directory"` με τα κατάλληλα μονοπάτια.

## 4. Προσαρμογή συγχώνευσης αλληλογραφίας

Το Aspose.Words για Java παρέχει εξαιρετική υποστήριξη για λειτουργίες συγχώνευσης αλληλογραφίας. Μπορείτε να προσαρμόσετε τη διαδικασία συγχώνευσης αλληλογραφίας ρυθμίζοντας έναν χειριστή συμβάντων συγχώνευσης αλληλογραφίας. Δείτε πώς να το κάνετε:

```java
// Ρυθμίστε το πρόγραμμα χειρισμού συμβάντων συγχώνευσης αλληλογραφίας για να κάνετε την προσαρμοσμένη εργασία.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Περικόψτε τις τιμές συγχώνευσης αλληλογραφίας στο τέλος και τα κορυφαία κενά.
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

## 5. Αποθήκευση του εγγράφου

Αφού προσαρμόσετε το έγγραφό σας, μπορείτε να το αποθηκεύσετε χρησιμοποιώντας τον ακόλουθο κώδικα:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Αντικαθιστώ`"Your Output Directory"` με την επιθυμητή διαδρομή εξόδου.

## Πλήρης Πηγαίος Κώδικας
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Ρυθμίστε το πρόγραμμα χειρισμού συμβάντων συγχώνευσης αλληλογραφίας για να κάνετε την προσαρμοσμένη εργασία.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Περικόψτε τις τιμές συγχώνευσης αλληλογραφίας στο τέλος και τα κορυφαία κενά.
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
Πηγαίος κώδικας του Class HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <περίληψη>
        /// Αυτός ο χειριστής καλείται για κάθε πεδίο συγχώνευσης αλληλογραφίας που βρίσκεται στο έγγραφο,
        /// για κάθε εγγραφή που βρίσκεται στην πηγή δεδομένων.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Αποφασίσαμε ότι θέλουμε όλες οι τιμές boolean να εμφανίζονται ως πεδία φόρμας πλαισίου ελέγχου.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Μετακινήστε τον "δρομέα" στο τρέχον πεδίο συγχώνευσης.
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
            // Δεν απαιτείται εφαρμογή.
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
        // Εισαγάγετε ένα MERGEFIELD ένθετο μέσα σε ένα πεδίο IF.
        // Εφόσον η πρόταση πεδίου IF είναι ψευδής, το αποτέλεσμα του εσωτερικού MERGEFIELD δεν θα εμφανιστεί,
        //και το MERGEFIELD δεν θα λάβει δεδομένα κατά τη συγχώνευση αλληλογραφίας.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Μπορούμε ακόμα να μετρήσουμε τα MERGEFIELD μέσα στα πεδία IF με ψευδή δήλωση εάν ορίσουμε αυτήν τη σημαία σε true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Το αποτέλεσμα δεν θα είναι ορατό στο έγγραφο επειδή το πεδίο IF είναι ψευδές,
        // αλλά το εσωτερικό MERGEFIELD έλαβε πράγματι δεδομένα.
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
            // Μην κάνετε τίποτα.
        }
        /// <περίληψη>
        /// Καλείται όταν η μηχανή συγχώνευσης αλληλογραφίας συναντά το πεδίο συγχώνευσης εικόνας:XXX στο έγγραφο.
        /// Έχετε την ευκαιρία να επιστρέψετε ένα αντικείμενο εικόνας, ένα όνομα αρχείου ή μια ροή που περιέχει την εικόνα.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Η τιμή του πεδίου είναι ένας πίνακας byte, απλώς μεταφέρετέ τον και δημιουργήστε μια ροή σε αυτόν.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Τώρα η μηχανή συγχώνευσης αλληλογραφίας θα ανακτήσει την εικόνα από τη ροή.
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
        /// <περίληψη>
        /// Καλείται για κάθε πεδίο συγχώνευσης που συναντάται στο έγγραφο.
        /// Μπορούμε είτε να επιστρέψουμε κάποια δεδομένα στη μηχανή συγχώνευσης αλληλογραφίας είτε να κάνουμε κάτι άλλο με το έγγραφο.
        /// Σε αυτήν την περίπτωση τροποποιούμε τη μορφοποίηση κελιών.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Επιλέξτε το χρώμα ανάλογα με το αν ο αριθμός της σειράς είναι άρτιος ή μονός.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //Δεν υπάρχει τρόπος να ορίσουμε ιδιότητες κελιού για ολόκληρη τη σειρά αυτή τη στιγμή, επομένως πρέπει να κάνουμε επανάληψη σε όλα τα κελιά της σειράς.
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
            // Μην κάνετε τίποτα.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <περίληψη>
    /// Επιστρέφει true εάν η τιμή είναι περιττή. false αν η τιμή είναι άρτια.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <περίληψη>
    /// Δημιουργήστε DataTable και γεμίστε τον με δεδομένα.
    /// Στην πραγματική ζωή, αυτός ο Πίνακας Δεδομένων θα πρέπει να συμπληρώνεται από μια βάση δεδομένων.
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

## 6. Συμπέρασμα

Συγχαρητήρια! Έχετε μάθει πώς να χρησιμοποιείτε πεδία στο Aspose.Words για Java για δυναμικό χειρισμό εγγράφων του Word. Αυτό το ισχυρό API σάς δίνει τον πλήρη έλεγχο των εγγράφων σας, καθιστώντας το πολύτιμο πλεονέκτημα για τους προγραμματιστές Java.

## 7. Συχνές ερωτήσεις

### Ε1: Πού μπορώ να κατεβάσω το Aspose.Words για Java;
 Μπορείτε να κάνετε λήψη του Aspose.Words για Java από[εδώ](https://releases.aspose.com/words/java/).

### Ε2: Πώς μπορώ να αποκτήσω μια προσωρινή άδεια για το Aspose.Words για Java;
 Μπορείτε να αποκτήσετε προσωρινή άδεια από[εδώ](https://purchase.aspose.com/temporary-license/).

### Ε3: Πού μπορώ να λάβω υποστήριξη για το Aspose.Words για Java;
 Για υποστήριξη, μπορείτε να επισκεφτείτε το φόρουμ Aspose.Words[εδώ](https://forum.aspose.com/).

### Ε4: Είναι το Aspose.Words για Java κατάλληλο για χειρισμό περιεχομένου HTML σε έγγραφα του Word;
Ναι, το Aspose.Words για Java παρέχει εξαιρετική υποστήριξη για τη διαχείριση περιεχομένου HTML σε έγγραφα του Word.

### Ε5: Μπορώ να χρησιμοποιήσω το Aspose.Words για Java δωρεάν;
 Το Aspose.Words for Java είναι ένα εμπορικό προϊόν, αλλά μπορείτε να εξερευνήσετε τις δυνατότητές του με μια δωρεάν δοκιμή διαθέσιμη[εδώ](https://releases.aspose.com/).

Ξεκινήστε με το Aspose.Words για Java σήμερα και αποκτήστε τον έλεγχο των εγγράφων του Word όπως ποτέ άλλοτε!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
