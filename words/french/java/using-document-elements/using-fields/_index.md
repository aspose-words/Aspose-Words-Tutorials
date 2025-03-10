---
title: Utilisation des champs dans Aspose.Words pour Java
linktitle: Utilisation des champs
second_title: API de traitement de documents Java Aspose.Words
description: Apprenez à utiliser efficacement Aspose.Words pour les champs Java dans ce didacticiel étape par étape. Créez facilement des documents Word dynamiques.
weight: 11
url: /fr/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des champs dans Aspose.Words pour Java


Dans ce didacticiel étape par étape, nous vous expliquerons comment utiliser les champs dans Aspose.Words pour Java pour manipuler facilement des documents. Aspose.Words pour Java est une API puissante qui vous permet de travailler avec des documents Word par programmation, vous donnant un contrôle total sur leur contenu et leur formatage.

## 1. Introduction

Aspose.Words pour Java est un outil essentiel pour quiconque manipule des documents Word dans des applications Java. Les champs sont des espaces réservés qui peuvent stocker des données dynamiques dans votre document. Ce didacticiel vous montrera comment travailler efficacement avec les champs.

## 2. Configuration de votre environnement

 Avant de commencer, assurez-vous d'avoir installé Aspose.Words for Java. Vous pouvez le télécharger à partir de[ici](https://releases.aspose.com/words/java/)Assurez-vous également que Java et un environnement de développement intégré (IDE) comme Eclipse ou IntelliJ IDEA sont installés sur votre système.

## 3. Chargement d'un document Word

Dans votre application Java, vous devez charger le document Word avec lequel vous souhaitez travailler. Voici un extrait de code pour vous aider à démarrer :

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Remplacer`"Your Document Directory"` et`"Your Output Directory"` avec les chemins appropriés.

## 4. Personnalisation du publipostage

Aspose.Words pour Java offre un excellent support pour les opérations de publipostage. Vous pouvez personnaliser le processus de publipostage en configurant un gestionnaire d'événements de publipostage. Voici comment procéder :

```java
// Configurer le gestionnaire d’événements de fusion et de publipostage pour effectuer le travail personnalisé.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Coupez les espaces de fin et de début des valeurs de publipostage.
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

## 5. Sauvegarde du document

Après avoir personnalisé votre document, vous pouvez le sauvegarder en utilisant le code suivant :

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Remplacer`"Your Output Directory"` avec le chemin de sortie souhaité.

## Code source complet
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Configurer le gestionnaire d’événements de fusion et de publipostage pour effectuer le travail personnalisé.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Coupez les espaces de fin et de début des valeurs de publipostage.
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
Code source de la classe HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <résumé>
        /// Ce gestionnaire est appelé pour chaque champ de publipostage trouvé dans le document,
        /// pour chaque enregistrement trouvé dans la source de données.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Nous avons décidé que nous voulions que toutes les valeurs booléennes soient générées sous forme de champs de formulaire de case à cocher.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Déplacez le « curseur » vers le champ de fusion actuel.
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
            // La mise en œuvre n’est pas requise.
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
        // Insérer un MERGEFIELD imbriqué dans un champ IF.
        // Étant donné que l'instruction du champ IF est fausse, le résultat du MERGEFIELD interne ne sera pas affiché,
        //et le MERGEFIELD ne recevra aucune donnée lors d'un publipostage.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Nous pouvons toujours compter les MERGEFIELDs dans les champs IF contenant des fausses déclarations si nous définissons cet indicateur sur true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Le résultat ne sera pas visible dans le document car le champ SI est faux,
        // mais le MERGEFIELD interne a effectivement reçu des données.
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
            // Ne fais rien.
        }
        /// <résumé>
        /// Ceci est appelé lorsque le moteur de publipostage rencontre le champ de fusion Image:XXX dans le document.
        /// Vous avez la possibilité de renvoyer un objet Image, un nom de fichier ou un flux contenant l'image.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // La valeur du champ est un tableau d'octets, il suffit de le convertir et de créer un flux dessus.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Le moteur de publipostage va maintenant récupérer l'image à partir du flux.
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
        /// <résumé>
        /// Appelé pour chaque champ de fusion rencontré dans le document.
        /// Nous pouvons soit renvoyer certaines données au moteur de publipostage, soit faire autre chose avec le document.
        /// Dans ce cas, nous modifions le formatage des cellules.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Sélectionnez la couleur en fonction du nombre de lignes, pair ou impair.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //Il n'existe actuellement aucun moyen de définir les propriétés des cellules pour toute la ligne. Nous devons donc parcourir toutes les cellules de la ligne.
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
            // Ne fais rien.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <résumé>
    /// Renvoie vrai si la valeur est impaire ; faux si la valeur est paire.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <résumé>
    /// Créez un DataTable et remplissez-le de données.
    /// Dans la vie réelle, ce DataTable doit être rempli à partir d'une base de données.
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

## 6. Conclusion

Félicitations ! Vous avez appris à utiliser les champs dans Aspose.Words pour Java pour manipuler des documents Word de manière dynamique. Cette puissante API vous donne un contrôle total sur vos documents, ce qui en fait un atout précieux pour les développeurs Java.

## 7. FAQ

### Q1 : Où puis-je télécharger Aspose.Words pour Java ?
 Vous pouvez télécharger Aspose.Words pour Java à partir de[ici](https://releases.aspose.com/words/java/).

### Q2 : Comment puis-je obtenir une licence temporaire pour Aspose.Words pour Java ?
 Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.aspose.com/temporary-license/).

### Q3 : Où puis-je obtenir de l’aide pour Aspose.Words pour Java ?
 Pour obtenir de l'aide, vous pouvez visiter le forum Aspose.Words[ici](https://forum.aspose.com/).

### Q4 : Aspose.Words pour Java est-il adapté à la gestion du contenu HTML dans les documents Word ?
Oui, Aspose.Words pour Java fournit un excellent support pour la gestion du contenu HTML dans les documents Word.

### Q5 : Puis-je utiliser Aspose.Words pour Java gratuitement ?
 Aspose.Words for Java est un produit commercial, mais vous pouvez explorer ses fonctionnalités avec un essai gratuit disponible[ici](https://releases.aspose.com/).

Commencez dès aujourd’hui avec Aspose.Words pour Java et prenez le contrôle de vos documents Word comme jamais auparavant !


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
