---
"description": "Aprenda a usar o Aspose.Words para campos Java de forma eficaz neste tutorial passo a passo. Crie documentos dinâmicos do Word com facilidade."
"linktitle": "Usando campos"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Usando campos em Aspose.Words para Java"
"url": "/pt/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando campos em Aspose.Words para Java


Neste tutorial passo a passo, mostraremos como usar campos no Aspose.Words para Java para manipular documentos com facilidade. O Aspose.Words para Java é uma API poderosa que permite trabalhar com documentos do Word programaticamente, oferecendo controle total sobre seu conteúdo e formatação.

## 1. Introdução

Aspose.Words para Java é uma ferramenta essencial para quem trabalha com documentos do Word em aplicativos Java. Campos são espaços reservados que podem armazenar dados dinâmicos no seu documento. Este tutorial mostrará como trabalhar com campos de forma eficaz.

## 2. Configurando seu ambiente

Antes de começar, certifique-se de ter o Aspose.Words para Java instalado. Você pode baixá-lo em [aqui](https://releases.aspose.com/words/java/). Além disso, certifique-se de ter o Java e um ambiente de desenvolvimento integrado (IDE), como Eclipse ou IntelliJ IDEA, instalado no seu sistema.

## 3. Carregando um documento do Word

No seu aplicativo Java, você precisa carregar o documento do Word com o qual deseja trabalhar. Aqui está um trecho de código para você começar:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Substituir `"Your Document Directory"` e `"Your Output Directory"` com os caminhos apropriados.

## 4. Personalizando a mala direta

O Aspose.Words para Java oferece excelente suporte para operações de mala direta. Você pode personalizar o processo de mala direta configurando um manipulador de eventos de mala direta. Veja como fazer isso:

```java
// Configure o manipulador de eventos de mala direta para fazer o trabalho personalizado.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Elimine espaços em branco à direita e à esquerda nos valores de mala direta.
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

## 5. Salvando o documento

Depois de personalizar seu documento, você pode salvá-lo usando o seguinte código:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Substituir `"Your Output Directory"` com o caminho de saída desejado.

## Código-fonte completo
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Configure o manipulador de eventos de mala direta para fazer o trabalho personalizado.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Elimine espaços em branco à direita e à esquerda nos valores de mala direta.
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
Código-fonte da classe HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <resumo>
        /// Este manipulador é chamado para cada campo de mala direta encontrado no documento,
        /// para cada registro encontrado na fonte de dados.
        /// </sumário>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Decidimos que queríamos que todos os valores booleanos fossem exibidos como campos de formulário de caixa de seleção.
            if (e.getFieldValue() instanceof /*booleano*/Boolean)
            {
                // Mova o "cursor" para o campo de mesclagem atual.
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
            //  A implementação não é necessária.
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
        // Insira um MERGEFIELD aninhado dentro de um campo IF.
        // Como a instrução do campo IF é falsa, o resultado do MERGEFIELD interno não será exibido,
        // e o MERGEFIELD não receberá nenhum dado durante uma mala direta.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Ainda podemos contar MERGEFIELDs dentro de campos IF com declaração falsa se definirmos esse sinalizador como verdadeiro.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // O resultado não será visível no documento porque o campo SE é falso,
        // mas o MERGEFIELD interno de fato recebeu dados.
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
            // Não faça nada.
        }
        /// <resumo>
        /// Isso é chamado quando o mecanismo de mala direta encontra o campo de mesclagem Image:XXX no documento.
        /// Você tem a chance de retornar um objeto Image, nome de arquivo ou um fluxo que contém a imagem.
        /// </sumário>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // O valor do campo é uma matriz de bytes, basta convertê-lo e criar um fluxo nele.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Agora, o mecanismo de mala direta recuperará a imagem do fluxo.
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
        /// <resumo>
        /// Chamado para cada campo de mesclagem encontrado no documento.
        /// Podemos retornar alguns dados ao mecanismo de mala direta ou fazer outra coisa com o documento.
        /// Neste caso, modificamos a formatação da célula.
        /// </sumário>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Selecione a cor dependendo se o número da linha é par ou ímpar.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Não há como definir propriedades de célula para a linha inteira no momento, então temos que iterar sobre todas as células da linha.
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
            // Não faça nada.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <resumo>
    /// Retorna verdadeiro se o valor for ímpar; falso se o valor for par.
    /// </sumário>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <resumo>
    /// Crie uma DataTable e preencha-a com dados.
    /// Na vida real, esta DataTable deve ser preenchida a partir de um banco de dados.
    /// </sumário>
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

## 6. Conclusão

Parabéns! Você aprendeu a usar campos no Aspose.Words para Java para manipular documentos do Word dinamicamente. Esta poderosa API oferece controle total sobre seus documentos, tornando-se um recurso valioso para desenvolvedores Java.

## 7. Perguntas frequentes

### P1: Onde posso baixar o Aspose.Words para Java?
Você pode baixar Aspose.Words para Java em [aqui](https://releases.aspose.com/words/java/).

### P2: Como posso obter uma licença temporária para o Aspose.Words para Java?
Você pode obter uma licença temporária em [aqui](https://purchase.aspose.com/temporary-license/).

### Q3: Onde posso obter suporte para o Aspose.Words para Java?
Para obter suporte, você pode visitar o fórum Aspose.Words [aqui](https://forum.aspose.com/).

### T4: O Aspose.Words para Java é adequado para manipular conteúdo HTML em documentos do Word?
Sim, o Aspose.Words para Java oferece excelente suporte para manipulação de conteúdo HTML em documentos do Word.

### P5: Posso usar o Aspose.Words para Java gratuitamente?
Aspose.Words para Java é um produto comercial, mas você pode explorar seus recursos com um teste gratuito disponível [aqui](https://releases.aspose.com/).

Comece a usar o Aspose.Words para Java hoje mesmo e assuma o controle dos seus documentos do Word como nunca antes!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}