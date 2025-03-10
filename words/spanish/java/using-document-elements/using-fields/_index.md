---
title: Uso de campos en Aspose.Words para Java
linktitle: Uso de campos
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a utilizar Aspose.Words para campos Java de forma eficaz en este tutorial paso a paso. Cree documentos dinámicos de Word con facilidad.
weight: 11
url: /es/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de campos en Aspose.Words para Java


En este tutorial paso a paso, le mostraremos cómo usar campos en Aspose.Words para Java para manipular documentos con facilidad. Aspose.Words para Java es una API potente que le permite trabajar con documentos de Word de manera programática, lo que le brinda control total sobre su contenido y formato.

## 1. Introducción

Aspose.Words para Java es una herramienta esencial para cualquier persona que trabaje con documentos de Word en aplicaciones Java. Los campos son marcadores de posición que pueden almacenar datos dinámicos en su documento. Este tutorial le mostrará cómo trabajar con campos de manera eficaz.

## 2. Configuración del entorno

 Antes de comenzar, asegúrese de tener instalado Aspose.Words para Java. Puede descargarlo desde[aquí](https://releases.aspose.com/words/java/)Además, asegúrese de tener Java y un entorno de desarrollo integrado (IDE) como Eclipse o IntelliJ IDEA instalado en su sistema.

## 3. Cargar un documento de Word

En su aplicación Java, debe cargar el documento de Word con el que desea trabajar. A continuación, se incluye un fragmento de código para comenzar:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Reemplazar`"Your Document Directory"` y`"Your Output Directory"` con los caminos adecuados.

## 4. Personalización de la combinación de correspondencia

Aspose.Words para Java ofrece un excelente soporte para operaciones de combinación de correspondencia. Puede personalizar el proceso de combinación de correspondencia configurando un controlador de eventos de combinación de correspondencia. A continuación, le indicamos cómo hacerlo:

```java
// Configure el controlador de eventos de combinación de correspondencia para realizar el trabajo personalizado.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Recortar los espacios iniciales y finales de los valores de combinación de correspondencia.
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

## 5. Guardar el documento

Después de personalizar su documento, puede guardarlo usando el siguiente código:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Reemplazar`"Your Output Directory"` con la ruta de salida deseada.

## Código fuente completo
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Configure el controlador de eventos de combinación de correspondencia para realizar el trabajo personalizado.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Recortar los espacios iniciales y finales de los valores de combinación de correspondencia.
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
Código fuente de la clase HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <resumen>
        /// Este controlador se llama para cada campo de combinación de correspondencia que se encuentre en el documento.
        /// para cada registro encontrado en la fuente de datos.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Decidimos que queremos que todos los valores booleanos se exporten como campos de formulario de casilla de verificación.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Mueva el "cursor" al campo de combinación actual.
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
            // No se requiere implementación.
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
        // Insertar un MERGEFIELD anidado dentro de un campo IF.
        // Dado que la declaración del campo IF es falsa, el resultado del MERGEFIELD interno no se mostrará.
        // el MERGEFIELD no recibirá ningún dato durante una combinación de correspondencia.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Todavía podemos contar MERGEFIELDs dentro de campos IF con declaraciones falsas si establecemos este indicador como verdadero.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // El resultado no será visible en el documento porque el campo SI es falso.
        // pero el MERGEFIELD interno efectivamente recibió datos.
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
            // No hacer nada
        }
        /// <resumen>
        ///Esto se llama cuando el motor de combinación de correspondencia encuentra el campo de combinación Image:XXX en el documento.
        //Tienes la posibilidad de devolver un objeto de imagen, un nombre de archivo o una secuencia que contenga la imagen.
        /// </summary>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // El valor del campo es una matriz de bytes, simplemente conviértalo y cree una secuencia en él.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Ahora el motor de combinación de correspondencia recuperará la imagen del flujo.
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
        /// <resumen>
        /// Se llama para cada campo de combinación encontrado en el documento.
        //Podemos devolver algunos datos al motor de combinación de correspondencia o hacer otra cosa con el documento.
        /// En este caso modificamos el formato de la celda.
        /// </summary>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Seleccione el color dependiendo de si el número de fila es par o impar.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //No hay forma de establecer propiedades de celda para toda la fila en este momento, por lo que tenemos que iterar sobre todas las celdas de la fila.
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
            // No hacer nada
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <resumen>
    /// Devuelve verdadero si el valor es impar; falso si el valor es par.
    /// </summary>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <resumen>
    ///Crea una DataTable y rellénala con datos.
    //En la vida real, esta DataTable debe completarse desde una base de datos.
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

## 6. Conclusión

¡Felicitaciones! Aprendió a usar campos en Aspose.Words para Java para manipular documentos de Word de manera dinámica. Esta poderosa API le brinda control total sobre sus documentos, lo que la convierte en un recurso valioso para los desarrolladores de Java.

## 7. Preguntas frecuentes

### P1: ¿Dónde puedo descargar Aspose.Words para Java?
 Puede descargar Aspose.Words para Java desde[aquí](https://releases.aspose.com/words/java/).

### P2: ¿Cómo puedo obtener una licencia temporal de Aspose.Words para Java?
 Puede obtener una licencia temporal en[aquí](https://purchase.aspose.com/temporary-license/).

### P3: ¿Dónde puedo obtener soporte para Aspose.Words para Java?
 Para obtener ayuda, puede visitar el foro de Aspose.Words[aquí](https://forum.aspose.com/).

### P4: ¿Aspose.Words para Java es adecuado para gestionar contenido HTML en documentos de Word?
Sí, Aspose.Words para Java proporciona un excelente soporte para manejar contenido HTML en documentos de Word.

### Q5: ¿Puedo usar Aspose.Words para Java de forma gratuita?
 Aspose.Words para Java es un producto comercial, pero puedes explorar sus características con una prueba gratuita disponible[aquí](https://releases.aspose.com/).

¡Empiece hoy mismo a utilizar Aspose.Words para Java y tome el control de sus documentos de Word como nunca antes!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
