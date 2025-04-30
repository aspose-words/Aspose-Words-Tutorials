---
"description": "Impara a usare Aspose.Words per i campi Java in modo efficace con questo tutorial passo passo. Crea documenti Word dinamici con facilità."
"linktitle": "Utilizzo dei campi"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo dei campi in Aspose.Words per Java"
"url": "/it/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo dei campi in Aspose.Words per Java


In questo tutorial passo passo, ti guideremo nell'utilizzo dei campi in Aspose.Words per Java per manipolare i documenti con facilità. Aspose.Words per Java è una potente API che ti permette di lavorare con i documenti Word a livello di codice, offrendoti il pieno controllo sul loro contenuto e sulla formattazione.

## 1. Introduzione

Aspose.Words per Java è uno strumento essenziale per chiunque gestisca documenti Word in applicazioni Java. I campi sono segnaposto che possono memorizzare dati dinamici nel documento. Questo tutorial ti mostrerà come utilizzare i campi in modo efficace.

## 2. Impostazione dell'ambiente

Prima di iniziare, assicurati di aver installato Aspose.Words per Java. Puoi scaricarlo da [Qui](https://releases.aspose.com/words/java/)Assicurati inoltre di avere Java e un ambiente di sviluppo integrato (IDE) come Eclipse o IntelliJ IDEA installati sul tuo sistema.

## 3. Caricamento di un documento Word

Nella tua applicazione Java, devi caricare il documento Word con cui vuoi lavorare. Ecco un frammento di codice per iniziare:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Sostituire `"Your Document Directory"` E `"Your Output Directory"` con i percorsi appropriati.

## 4. Personalizzazione della stampa unione

Aspose.Words per Java offre un eccellente supporto per le operazioni di stampa unione. È possibile personalizzare il processo di stampa unione impostando un gestore di eventi di stampa unione. Ecco come fare:

```java
// Imposta il gestore degli eventi di stampa unione per svolgere il lavoro personalizzato.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Ritaglia gli spazi vuoti iniziali e finali nei valori di unione della posta.
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

## 5. Salvataggio del documento

Dopo aver personalizzato il documento, puoi salvarlo utilizzando il seguente codice:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Sostituire `"Your Output Directory"` con il percorso di output desiderato.

## Codice sorgente completo
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Imposta il gestore degli eventi di stampa unione per svolgere il lavoro personalizzato.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Ritaglia gli spazi vuoti iniziali e finali nei valori di unione della posta.
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
Codice sorgente della classe HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <sommario>
        /// Questo gestore viene chiamato per ogni campo di unione di posta trovato nel documento,
        /// per ogni record trovato nella sorgente dati.
        /// </sommario>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Abbiamo deciso che tutti i valori booleani devono essere visualizzati come campi modulo di casella di controllo.
            if (e.getFieldValue() instanceof /*booleano*/Boolean)
            {
                // Spostare il "cursore" sul campo di unione corrente.
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
            //  Non è richiesta l'implementazione.
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
        // Inserire un MERGEFIELD annidato all'interno di un campo IF.
        // Poiché l'istruzione del campo IF è falsa, il risultato del MERGEFIELD interno non verrà visualizzato,
        // e MERGEFIELD non riceverà alcun dato durante una stampa unione.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Possiamo ancora contare i MERGEFIELD all'interno dei campi IF con istruzione falsa se impostiamo questo flag su true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Il risultato non sarà visibile nel documento perché il campo SE è falso,
        // ma il MERGEFIELD interno ha effettivamente ricevuto dati.
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
            // Non fare nulla.
        }
        /// <sommario>
        /// Questa funzione viene chiamata quando il motore di stampa unione incontra il campo di unione Immagine:XXX nel documento.
        /// Hai la possibilità di restituire un oggetto Immagine, un nome file o un flusso contenente l'immagine.
        /// </sommario>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Il valore del campo è un array di byte, basta eseguirne il cast e creare un flusso su di esso.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Ora il motore di stampa unione recupererà l'immagine dal flusso.
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
        /// <sommario>
        /// Chiamato per ogni campo di unione riscontrato nel documento.
        /// Possiamo restituire alcuni dati al motore di stampa unione oppure fare qualcos'altro con il documento.
        /// In questo caso modifichiamo la formattazione della cella.
        /// </sommario>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Selezionare il colore a seconda che il numero di riga sia pari o dispari.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Al momento non è possibile impostare le proprietà delle celle per l'intera riga, quindi dobbiamo ripetere l'operazione su tutte le celle della riga.
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
            // Non fare nulla.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <sommario>
    /// Restituisce true se il valore è dispari; false se il valore è pari.
    /// </sommario>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <sommario>
    /// Crea DataTable e riempilo con i dati.
    /// Nella vita reale questa DataTable dovrebbe essere compilata da un database.
    /// </sommario>
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

## 6. Conclusion

Congratulazioni! Hai imparato a utilizzare i campi in Aspose.Words per Java per manipolare dinamicamente i documenti Word. Questa potente API ti offre il controllo completo sui tuoi documenti, rendendola una risorsa preziosa per gli sviluppatori Java.

## 7. Domande frequenti

### D1: Dove posso scaricare Aspose.Words per Java?
Puoi scaricare Aspose.Words per Java da [Qui](https://releases.aspose.com/words/java/).

### D2: Come posso ottenere una licenza temporanea per Aspose.Words per Java?
È possibile ottenere una licenza temporanea da [Qui](https://purchase.aspose.com/temporary-license/).

### D3: Dove posso ottenere supporto per Aspose.Words per Java?
Per supporto, puoi visitare il forum di Aspose.Words [Qui](https://forum.aspose.com/).

### D4: Aspose.Words per Java è adatto alla gestione di contenuti HTML nei documenti Word?
Sì, Aspose.Words per Java fornisce un supporto eccellente per la gestione del contenuto HTML nei documenti Word.

### D5: Posso utilizzare Aspose.Words per Java gratuitamente?
Aspose.Words per Java è un prodotto commerciale, ma puoi esplorare le sue funzionalità con una prova gratuita disponibile [Qui](https://releases.aspose.com/).

Inizia subito a usare Aspose.Words per Java e prendi il controllo dei tuoi documenti Word come mai prima d'ora!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}